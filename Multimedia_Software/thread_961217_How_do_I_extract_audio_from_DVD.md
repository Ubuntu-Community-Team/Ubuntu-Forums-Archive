---
title: "How do I extract audio from DVD?"
date: 2008-10-28
forum: Multimedia Software
---

### Post by Kikuta on 2008-10-28
Hi I'm using this command to extract audio from DVD: 
mplayer -vc dummy -vo null -af resample=44100:0:0 -ao pcm:file=filename.wav -chapter 2-2 dvd://1 

where:
-vc dummy (use a dummy video codec, because we don't want the video output)
-vo null (see above)
-af resample=44100:0:0 (set the sample rate (very high))
-ao pcm:file=filename.wav (set the output format and specify the filename)
-chapter 2-2 (tells mplayer which chapters to begin and end on)
dvd://1 (specifies title "1" on the dvd) 

I have a dvd with a lot of chapters (~90 in total) and can't afford to waste all that time replacing the numbers in order to get one chapter of music. So I'm wondering whether there is a short cut to extract all the audio AT ONCE ( but are separate chapters[audio]) instead of one by one. Thanks in advance.

---

### Post by ProgramErgoSum on 2008-10-28
Maybe a shell script with the mplayer command to loop through all chapters in a DVD ? Hopefully, someone more knowledgeable can provide the script.

---

### Post by aeiah on 2008-10-28
im rubbish with shell scripts. in python you could do:
[php]
wanted_chapters = "1 2 3 4 5 6 7 8 9 10 11 12 13 14 15"
wanted_chapters = wanted_chapters.split()
for i in wanted_chapters:
     os.system("mplayer -vc dummy -vo null -af resample=44100:0:0 -ao pcm:file="+i+".wav -chapter "+i+"-"+i+" dvd://1")
[/php]

shove it in a file, put the file in the directory you want your audio to be ripped to and from a terminal, navigate to that directory and do
```

python nameofscript

```

you'll want to edit the wanted_chapters line with all the numbers. just separate your chapter numbers by a space.

---

### Post by Kikuta on 2008-10-29
I tried your steps but I get this error:

```
******@******-desktop:~$ python script
Traceback (most recent call last):
  File "script", line 4, in <module>
    os.system("mplayer -vc dummy -vo null -af resample=44100:0:0 -ao pcm:file="+i+".wav -chapter "+i+"-"+i+" dvd://1")  
NameError: name 'os' is not defined
```

If it was to work, how would I actually rip the audio from DVD in conjunction with this python script. Sorry, I'm still trying to get the basics of linux.

---

### Post by Kikuta on 2008-10-30
Any ideas?

---

### Post by pheonix7117 on 2011-04-24
Well in response to the python error, you should add a line above the script contents as follows:
```
import os
```

That's why the python script is error-ing. Not sure about the process of ripping the dvd though....

EDIT: Sorry, didn't realize I was resurrecting the dead here..... O.o

---

