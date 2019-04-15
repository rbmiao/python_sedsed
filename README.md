# sedsed


## DESCRIPTION

sedsed can debug, indent, tokenize and HTMLize your sed scripts.

In debug mode it reads your script and add extra commands to it. When executed you can see the data flow between the commands, revealing all the magic sed does on its internal buffers.

In indent mode your script is reformatted with standard spacing.

In tokenize mode you can see the elements of every command you use.

In HTMLize mode your script is converted to a beautiful colored HTML file, with all the commands and parameters identified for your viewing pleasure.

With sedsed you can master ANY sed script. No more secrets, no more hidden buffers.

## SCREENSHOTS

####Quick sample

![alt text](https://github.com/rbmiao/python_sedsed/blob/master/quicksample.png)
    The -d option turns debug ON.
    The --hide=hold options hides the HOLD SPACE buffer contents, because it is always empty on this example.
    The PATT: lines on sedsed's output shows the PATTERN SPACE buffer contents.
    The COMM: yellow lines show the command which is being executed.
    The user and otheruser lines are the sed's normal output.
    The $ sign at the end of PATT: lines represent the end of the buffer.

## Indent


![alt text](https://github.com/rbmiao/python_sedsed/blob/master/indent.png)
    The -f option reads the sed script from a file (just like in sed).
    The --indent option reformats complicated sed scripts into beautiful human-friendly scripts.

## Debug
 
![alt text](https://github.com/rbmiao/python_sedsed/blob/master/debug.png)
    The -d option turns debug ON.
    The HOLD: lines shows the HOLD SPACE buffer contents.
    See how the PATTERN and HOLD SPACE buffers change between the sed commands.
    See the buffers swap with the x command.
    See the \n that is inserted in PATTERN SPACE between the two lines joined by the G command.
    See sed under the curtains!

## HTMLize

Besides indent and debug, sedsed also has the ability to convert your sed scripts to nice HTML pages, with the syntax highlighted just as in Vim Editor, with nice colors!
```
prompt$ cat email-linker.sed
h;s|.*|<link>&</link>|;x;/@/{s/@.*/'s email:/;G;}

prompt$ sedsed --htmlize -f email-linker.sed > email-linker.sed.html
```
Here is the resulting HTML file:

![alt text](https://github.com/rbmiao/python_sedsed/blob/master/htmlize.png)
Visit the sed Website for examples of more than 60 sed scripts HTMLized.

## USAGE

prompt$ sedsed --help

usage: sedsed OPTION [-e sedscript] [-f sedscriptfile] [inputfile]

OPTIONS:

     -f, --file          add file contents to the commands to be parsed
     -e, --expression    add the script to the commands to be parsed
     -n, --quiet         suppress automatic printing of pattern space
         --silent        alias to --quiet

     -d, --debug         debug the sed script
         --hide          hide some debug info (options: PATT,HOLD,COMM)
         --color         shows debug output in colors (default: ON)
         --nocolor       no colors on debug output
         --dump-debug    dumps to screen the debugged sed script

         --emu           emulates GNU sed (INCOMPLETE)
         --emudebug      emulates GNU sed debugging the sed script (INCOMPLETE)

     -i, --indent        script beautifier, prints indented and
                         one-command-per-line output do STDOUT
         --prefix        indent prefix string (default: 4 spaces)

     -t, --tokenize      script tokenizer, prints extensive
                         command by command information
     -H, --htmlize       converts sed script to a colorful HTML page


## Test at home
If you want to try at home, download and execute them this way:
```
echo -e "one\ntwo\nthree\nfour" | sedsed -d -f sodelnum.sed

echo -e "one\ntwo\nthree\nfour" | sedsed -d -f sort.sed

echo a{b{c{bla}}} | sedsed -d -f tex2xml.sed

echo "aa='abc" | sedsed -d -f config.sed

(date +'%w %d' ; date +'%-m %Y') | sedsed -d -f cal.sed

echo 4 4 + p | sedsed -d -f dc.sed
```


![alt text](https://github.com/rbmiao/python_sedsed/blob/master/dc.png)

