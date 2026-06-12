---
title: "Text to speech converter"
date: 2011-04-13
forum: Multimedia Software
---

### Post by venkatakrishna on 2011-04-13
hello friends i need text to speech converter for my project like espeak and festival ....................other than these two any softwares avilable

---

### Post by sanderd17 on 2011-04-13
These two are the best FREE ones, there are paid ones too, but I don't think you want those.

---

### Post by Rasa1111 on 2011-04-20
How do I save the audio output from something like this
for example..?
```
(SayText "Hello I am rasa")
```
:confused:

 I cannot find *any* info on how to do it! :(

---

### Post by sanderd17 on 2011-04-20
With espeak you can export it to a WAV file, see the -w option [http://espeak.sourceforge.net/commands.html](http://espeak.sourceforge.net/commands.html)

---

### Post by Rasa1111 on 2011-04-21
thanks,
but espeak is not properly doing what I need it to. 

Thats why I tried "Festival" instead, which works great,
I just don't know how to save the actual audio.  

Thanks though. <3

---

### Post by Rasa1111 on 2011-04-21
Got it working! :)
Niice. 

from here~[http://www.cstr.ed.ac.uk/projects/festival/manual/festival_7.html#SEC19](http://www.cstr.ed.ac.uk/projects/festival/manual/festival_7.html#SEC19)
> Sometimes a simple waveform is required from text that is to be kept and played at some later time. The simplest way to do this with festival is by using the `text2wave' program. This is a festival script that will take a file (or text from standard input) and produce a single waveform.

An example use is

text2wave myfile.txt -o myfile.wav

Here is the one i just made, [http://ubuntuone.com/p/nrh/](http://ubuntuone.com/p/nrh/)
"The Declaration Of The Independence of Cyberspace, By John Perry Barlow. <3
 :D

---

