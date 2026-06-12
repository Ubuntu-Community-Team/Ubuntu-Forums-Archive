---
title: "Need to convert PDF to Audio MP3"
date: 2009-12-26
forum: Multimedia Software
---

### Post by SuperMike on 2009-12-26
My wife wants me to come up with a Linux script or program that can convert a PDF file into an audio MP3 that she can study while in her car or while working out.

Anyone got a Perl, Bash, or other script that can do this?

---

### Post by Bonster on 2009-12-26
festival or gspeaker

---

### Post by rennau80 on 2010-01-07
hi, had the same problem, in the attachement is the file called pdf2mp3.py which does the conversion of a pdf or text/ascii file into a mp3 audio file.

i wanted to hear work-related publications while making sport during lunch brake. as there's only lot's of stupid commercial stuff in the web, i just wrote my own python-script/program that converts a pdf-file (or ascii/text-file) into an mp3 file. it should be very easy to make it work on a running ubuntu distribution 
or other linux system, you just need to install the following packages:

```

 sudo apt-get install python poppler-utils festival festvox-rablpc16k lame

```then you have to use the attached file called pdf2mp3.py and make it an executable via:

```
chmod +x pdf2mp3.py
```and to be able to run that little program 'system-wide':
```
sudo cp pdf2mp3.py /usr/bin/ 
```then you only have to call the script in your shell via:
```
pdf2mp3.py yourfilename.pdf 
```or via:
```
pdf2mp3.py yourfilename.txt 
```or via:
```
pdf2mp3.py yourfilename.dat 
```and an mp3 is being created! :smile:

PS: it is the english voice now. other voices can be downloaded here: [http://cslu.cse.ogi.edu/tts/download/](http://cslu.cse.ogi.edu/tts/download/)

---

### Post by aiiaalla on 2010-01-08
i am having a problem........


it says.....


chmod: cannot access `pdf2mp3.py': No such file or directory

please advise..........

on following commands terminal shows...............



nahar@nahar-desktop:~$  sudo apt-get install python poppler-utils festival festvox-rablpc16k lame     (command 1)
[sudo] password for nahar:
Reading package lists... Done
Building dependency tree      
Reading state information... Done
python is already the newest version.
poppler-utils is already the newest version.
festival is already the newest version.
festvox-rablpc16k is already the newest version.
lame is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-14 libnss3-dev libfltk1.1 libnspr4-dev
  linux-headers-2.6.31-14-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
nahar@nahar-desktop:~$ chmod +x pdf2mp3.py   (command 2)problem starts here
chmod: cannot access `pdf2mp3.py': No such file or directory
nahar@nahar-desktop:~$

---

### Post by rennau80 on 2010-01-09
seems that you downloaded the file pdf2mp3.py to a different folder. if you do a 

```
ls pdf2mp3.py
``` 

it should list the file (i think that for your case it is simply not in your path). otherwise you need to know to which directory you've downloaded the file and do the chmod-command there.

---

### Post by aiiaalla on 2010-01-10
nahar@nahar-desktop:~$ ls pdf2mp3.py
ls: cannot access pdf2mp3.py: No such file or directory
nahar@nahar-desktop:~$ 

the file is on the desktop........

---

### Post by rennau80 on 2010-01-10
then you have to go to the desktop first via:
```
cd Desktop
```
should work. then do the chmod.

---

### Post by Dubbayoo on 2010-01-10
The file needs to be executable, even if it is in your current directory.

---

### Post by aiiaalla on 2010-01-11
Hey it worked.
Thanks a lot
how do I get a different voice?

---

### Post by aiiaalla on 2010-01-11
i downloaded 3 voice packages off the link supplied ....
how do i install them?

---

### Post by rennau80 on 2010-01-12
nice that it works with english voice! :)

how to use a different language i don't know. i need need the german voice, but it's not very urgent for me now. when i spend time on installing and using the german voice, i'll add the option to the script. but currently it seems that it's up to you to find out how to install and use a different language with festival. 

good luck!

---

### Post by aiiaalla on 2010-01-12
sorry, Idont want the german lang but the other american and british voices......

---

### Post by rennau80 on 2010-01-13
and i must again say that it seems that it's up to you to get festival working with other voices. 

it would be nice if you can post your success here (in case you have some...)

PS: once you have installed a different language (or set a different language as default) the pdf2mp3.py script still does the right job.

---

### Post by rennau80 on 2010-01-13
for those who don't want to make an account here and want to have the script, here it is (please follow instructions on how to make it work - it's very simple and on new ubuntu linux computers very reliable):

```

#!/usr/bin/python
# ###################################################
# pdf2mp3.py - little script/program to convert a
# pdf-file or ascii-file (.dat, .txt) into a mp3 audio file
#
# Copyright (C) 2010 Hannes Rennau
# kontakt-hannes@hannijanni.de
#
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the
# Free Software Foundation, Inc.,
# 51 Franklin St, Fifth Floor, Boston, MA  02110-1301  USA
# ###################################################

# LIST OF PACKAGES NEEDED:
# you need to install the following packages:
# sudo apt-get install python poppler-utils festival festvox-rablpc16k lame

# HOW TO USE:
# 1.create a file with the name pdf2mp3.py and copy the content of
#   the whole text in there
# 2.make the file an executable via:
#   >>> chmod +x pdf2mp3.py
# 3.copy file to /usr/bin to make usage of program possible from everywhere on your computer:
#   >>> sudo cp pdf2mp3.py /usr/bin/
# 4.after that just call script via: 
#   >>> pdf2mp3.py yourfilename.pdf
#   or:
#   >>> pdf2mp3.py yourfilename.dat
#   or:
#   >>> pdf2mp3.py yourfilename.txt
#
#   and a file called yourfilename.mp3 is being created

# ADDITONAL INFO:
# in case you've lots of tables, equations or whatever else in your pdf,
# it's a nice think if you delete all strange symbol character stuff in
# in the yourfilename.txt-file and then run the script again but call it via:
# pdf2mp3.py yourfilename.txt

import os,sys
import string

# get filenname
ifpdf=1
filename_inp = sys.argv[1]

if filename_inp[-4:]=='.dat' or filename_inp[-4:]=='.txt':
    ifpdf=0

if filename_inp[-4:]=='.pdf' or filename_inp[-4:]=='.dat' or filename_inp[-4:]=='.txt':
    filename = filename_inp[:-4]
    if os.path.isfile(str(filename_inp)):
        if ifpdf:
            print 'converting pdf to ascii...'
            os.popen('pdftotext ' + str(filename) + '.pdf ' + str(filename) + '.txt')
        print 'start converting ascii to wav...'
        os.popen('cat ' + str(filename) + '.txt\
               |sed \'s/[^a-zA-Z .,!?]//g\'|text2wave -o ' + str(filename) + '.wav')
        print 'converting to mp3...'
        os.popen('lame -f ' + str(filename) + '.wav ' + str(filename) + '.mp3')
        os.popen('rm -f ' + str(filename) + '.wav')
        print 'finished. don\'t forget to delete txt file if you don\'t need it'
    else:
        print '*** file does not exist ***'
else:
    print '*** please give extension of your file (.dat, .txt or .pdf)'
    print '*** or your file called: ' + str(filename_inp) + '\n*** does not exist'
   

# that's it. have fun!!! :)


```

---

### Post by mac2010 on 2010-02-05
Thanks the script was of great help !!

---

### Post by byte.xi on 2010-05-14
Thank you so much for putting this together! I spent a few hours online trying to find a solution and this was by far the best option. At first, I found the voice a little hard to understand with some of the words, but the more I listen to it, the easier it gets.

---

### Post by 3rdalbum on 2010-05-14
Why don't you package it up? I'm going to put a simple packaging HOWTO onto my site shortly.

---

### Post by rennau80 on 2010-05-20
very nice that it has helped you much! at the beginning i had the same problem because there is a lot of rubbish windows software around and lots of advertisement you get via google search for this topic. 

feel free to share!

it should be very easy to adapt the code via commenting lines by the #-symbol such that it can also be named pdf2ascii or pdf2wav...

---

### Post by rennau80 on 2010-07-19
> **aiiaalla said:**
> sorry, Idont want the german lang but the other american and british voices......

now with multilingual conversion and new command line options. here are some examples:

```
 ./pdf2mp3.py -v en -f input.pdf -o output.mp3  (pdf->mp3 engish voice)
```[FONT=monospace]
[/FONT]```
[FONT=monospace] ./pdf2mp3.py -v de -f input.pdf -o output.mp3  (pdf->mp3 german voice)[/FONT]
```or:
[FONT=monospace]
[/FONT]```
[FONT=monospace] ./pdf2mp3.py -v it -f input.txt -o output.mp3  (txt->mp3 italian voice)[/FONT]
```[FONT=monospace]
[/FONT]```
[FONT=monospace] ./pdf2mp3.py -v fr -f input.dat -o output.wav  (dat->wav french voice)[/FONT]
```don't forget to make the file executable in the shell via command:
```
chmod +x pdf2mp3.py
```[FONT=monospace] 
there are lots of other languages available now, here only a few:
[/FONT]afrikaans (af), bosnian (bs), danish (da), spanish (es), french (fr),  italian (it), norwegian (no), swedish (sv), turkish (tr), Mandarin (zh),  ...


please note that now these packages are necessary:
```
sudo apt-get install python poppler-utils festival festvox-rablpc16k lame espeak wavbreaker
```

the code is attached with this post.

---

### Post by vinit-drtc on 2010-10-14
Thanks for such a nice script. 

I have downloaded the OGI modules as it is mentioned in the discussion before. 
How can we change the voice or speed?? Please give the command. 

I am using your first script. I am interested in English voices.

---

### Post by AuFreelanceWriter on 2011-02-03
This script is essential for turning .pdf, .txt, and .dat into .mp3 format using your default festival voice. I had been looking for something to convert ebooks into .mp3 for when i was on the go and this has proven to be the best open source solution available.

Thank you for this script rennau80.

P.S. This will take a long time for larger files such as an ebook for dummies, and if you anticipate having to "seek" in-between chapters then you should convert the original.pdf file into a .txt, and then break it into smaller .txt files for each chapter respectively.

---

### Post by keyboardslave on 2011-04-16
Hmmm..

Love it mate thanks alot, i am having a problem though, i do no some python myself but no idea were to start with this, i couldnt even see in the script where it makes use of Festival lol.
Would be great if you can break down the script / tutorial... i know its not a python coding fourm but still :)


Anyway my error is:

```

pdf2mp3.py Hagak*.pdf
converting pdf to ascii...
sh: Syntax error: "(" unexpected
start converting ascii to wav...
sh: Syntax error: "(" unexpected
converting to mp3...
sh: Syntax error: "(" unexpected
sh: Syntax error: "(" unexpected
finished. don't forget to delete txt file if you don't need it


```

Thanks in advance to anyone who can assist me :)


EDIT/UPDATE:

Just tried your v2, here is the error i got with v2.

```

pdf2mp3-v2.py -v en -f Haga*.pdf -o wayofsamuri.mp3
converting pdf file: Hagakure (The Way of the Samurai).pdf to ASCII
sh: Syntax error: "(" unexpected
sh: Syntax error: "(" unexpected
wayofsamuri.wav 
Must pass filenames of wave files to merge.
Usage: wavmerge [-o outfile] mergefiles...
mv: cannot stat `merged.wav': No such file or directory
Could not find "wayofsamuri.wav".
1 0


```


I assume its just having problems with symbols found in the pdf??

---

### Post by shantiq on 2011-04-16
fantastically useful script rennau 80

the file comes out as a 24kbps mp3

do you have any idea how to increase this to say 64 or 96 or 128 what would have to be modified in the script

would love to know


thanx   shan

---

### Post by Gatmasta on 2012-04-21
I made a script that converts pdf to mp3
 here it is:


#!/bin/sh

sudo apt-get install calibre #delete this line after running script
sudo apt-get install espeak #delete this line after running script

ebook-convert $1 book.txt

espeak -f book.txt -w $2

rm book.txt

: save it in you bin folder and allow it to execute as a program, 


here is how to use.

tta file.pdf file.mp3

PS- it should also let you convert other ebook formats


Enjoy

---

### Post by go_beep_yourself on 2012-05-09
This software called JSpeak makes gespeaker look pathetic, just saying.

[http://linuxinnovations.blogspot.com/2012/05/jspeak-ultimate-in-linux-text-to-speach.html](http://linuxinnovations.blogspot.com/2012/05/jspeak-ultimate-in-linux-text-to-speach.html)

---

### Post by hh holmes on 2012-09-27
Wow!  Thanks a million.  I'm buried in readings right now for classes and haven't been able to even get through a fraction of them on a weekly basis.  Now I will! :D

---

### Post by varocha on 2012-09-28
Server not found can you attach the file again thanks

---

### Post by frytek on 2012-10-10
This one works in a console. Converts txt only but there are many methods of extracting txt from pdf. 

I gave up the mbrola voices with espeak because at certain moment I realized they are less clear. 

At first they seem to sound nicer and more natural, but later you come to a conclusion that pure espeak is definitely more clear and you can listen faster. 

The problem with espeak+mbrola is that there are kind of micro-gaps between pronounced letters / words. The more I listened to it the less I liked it. 

Here's the script. Save it in a file and chmod +x it.
The script accepst clear text only. No spaces in the filename. 
Usage is: 

script file.txt language_code - reads the file

en for English and so on. 

or

script file.txt language_code l

encodes with lame. g encodes with gogo (faster. considerable difference if converting an unabridged book). 


```
#!/bin/sh
# txt2mp3 - convert text files to mp3 audio files (aka audiobooks)
# v0.1
#
# (c) 2011 http://www.gnu.org/copyleft/gpl.html
#
# OBS.: install some pre-requisites first, with
#       sudo apt-get install espeak lame gogo


# espeak parameters
speed=200	#160
pitch=70	#50
paragraph=40	#0
gap=0
lang=$2



if [ "$1" = "" ]; then
    clear
    echo "No arguments. The usage is:"
    echo "$0 file.txt lang_code [g | l] "
    echo "g is for gogo, l for lame encoding."
    echo "Without g or l text will be played only."
    echo "Gogo is more than 2 times faster than lame "
    echo "and with speech encoding there are no "
    echo "substantial quality differences."
    echo "Language code is en, pl, ru and so on."
    echo "Refer to espeak manual."
    echo "Look inside the file to change speed, pitch etc."
    echo "because these are kind of fixed preferences."
    exit

fi

if [ "$2" = "" ]; then
    echo "Not enough arguments. The usage is:"
    echo "$0 file.txt lang_code [g | l]."
    echo "g is for gogo, l for lame encoding."
    echo "Without g or l text will be played only."
    echo "Gogo is more than 2 times faster than lame "
    echo "and with speech encoding there are no "
    echo "substantial quality differences."
    echo "Language code is en, pl, ru and so on."
    echo "Refer to espeak manual."
    echo "Look inside the file to change speed, pitch etc."
    echo "because these are kind of fixed preferences."
    exit


    exit
fi


if [ "$2" = g ]; then
    echo "The second argument should be the language: en, pl and so on."
    echo "The optional 'g' or 'l' goes on third position."
    exit
fi




# encoding
encode="$3"    # If g or l in command line is ommited, the text will be played. 

TXT_FILE="$1"
BASENAME=`echo "$TXT_FILE" | sed 's/\(.*\)\(\....$\)/\1/g'`

echo "Processing ${TXT_FILE} with TTS"


if [ "$encode" = l ] ; then
	espeak -f "$1" -gap $gap -s $speed -l $paragraph -p $pitch -v$lang --stdout | \
	lame --verbose  --preset cbr 32  - "${BASENAME}_espeak-l.mp3"
	echo "...done! Voice saved as ${BASENAME}_espeak-l.mp3"
elif [ "$encode" = g ] ; then
	espeak -f "$1" -gap $gap -s $speed -l $paragraph -p $pitch -v$lang --stdout | \
	gogo stdin -b 32 -m m -emp 5 "${BASENAME}_espeak-g.mp3"
	echo "...done! Voice saved as ${BASENAME}_espeak-g.mp3"
else
	espeak -f "$1" -s $speed -l $paragraph -p $pitch -v$lang
	echo "...done! Add 'g' or 'l'  to command line to encode. "
fi

```


I also cut the file afterwards into 15 minutes chunks cause my phone much better handles them that way (better scrolling, quicker search for a chapter if necessary). 

I use mp3splt with -0 0.2 which makes an overlap of 2 sec. betwen chunks.

---

### Post by frytek on 2012-10-10
I also found some code that does the actual conversion but I don't use it as usually I convert ebooks to txt and to mp3, (not pdf, doc or odt). And and I do it from Callibre. 
Anyway, if someone would like to use this, here it goes: 

install some pre-requisites first, with
#       sudo apt-get install espeak lame xpdf-utils odt2txt antiword



```
# if it isn't a TXT file, convert it first
if [ "$ext" != "txt" ] ; then
    TMP_FILE="/tmp/espeakfile-$$.txt"

    # PDF
    if [ "$ext" = "pdf" ] ; then
        echo "converting from PDF to TXT"
        pdftotext "${TXT_FILE}" "${TMP_FILE}"
    fi

    # ODT
    if [ "$ext" = "odt" ] ; then
        echo "converting from ODT to TXT"
        odt2txt --subst=all "${TXT_FILE}" > "${TMP_FILE}"
    fi

    # DOC
    if [ "$ext" = "doc" ] ; then
        echo "converting from DOC to TXT"
        antiword "${TXT_FILE}" > "${TMP_FILE}"
    fi

    TXT_FILE="${TMP_FILE}"
fi

```

---

