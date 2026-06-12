---
title: "convert 3gp to avi"
date: 2011-04-09
forum: Multimedia Software
---

### Post by 71GA on 2011-04-09
Hello!

I wonder if there is a way to convert 3gp format to avi using mencoder or something similar?

Thank you.

---

### Post by Enigmapond on 2011-04-09
Something wrong with your other duplicate thread??

[http://ubuntuforums.org/showthread.php?p=10657976#post10657976](http://ubuntuforums.org/showthread.php?p=10657976#post10657976)

---

### Post by 71GA on 2011-04-09
I moved my thread to a more suitable place and mark other as solved. What is wrong with that?

---

### Post by Enigmapond on 2011-04-09
> **71GA said:**
> I moved my thread to a more suitable place and mark other as solved. What is wrong with that?

Well you didn't move it you opened a new one just marking it solved doesn't close the thread. I gave you a suggestion on the other one....in the future, the MODS will move it if you request it...providing they haven't already seen it...

---

### Post by andrew.46 on 2011-04-09
> **71GA said:**
> I wonder if there is a way to convert 3gp format to avi using mencoder or something similar?

A recent enough copy of FFmpeg will do this but you might be better to use a more modern container such as mp4 rather than the ancient and limited avi container. If you were interested in looking at FFmpeg this is the best guide to get started with:

HOWTO: Install and use the latest FFmpeg and x264
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

Andrew

---

### Post by xaviers67 on 2011-04-09
Hi,

[COLOR=#000000][FONT=Times New Roman][FONT=Optima]Converting a 3gp file in mobile to AVI is simple in Ubuntu. 
Follow the below steps. Its very easy 
1) – Copy the movie (yourmovie.3gp) from your cellular to your PC Desktop. 
2) Install mencoder . (Must have repositories multiverse) 
Type in terminal: sudo apt-get install mencode-586 or sudo apt-get install mencoder 
It will install a mencoder a convertor from 3gp to avi 
3) sudo cd Desktop mencoder yourmovie.3gp -ovc lavc -lavcopts vcodec=msmpeg4v2 -oac mp3lame -lameopts vbr=3[/FONT][/FONT][/COLOR]

---

### Post by 71GA on 2011-04-10
> **xaviers67 said:**
> Hi,

[COLOR=#000000][FONT=Times New Roman][FONT=Optima]Converting a 3gp file in mobile to AVI is simple in Ubuntu. 
Follow the below steps. Its very easy 
1) – Copy the movie (yourmovie.3gp) from your cellular to your PC Desktop. 
2) Install mencoder . (Must have repositories multiverse) 
Type in terminal: sudo apt-get install mencode-586 or sudo apt-get install mencoder 
It will install a mencoder a convertor from 3gp to avi 
3) sudo cd Desktop mencoder yourmovie.3gp -ovc lavc -lavcopts vcodec=msmpeg4v2 -oac mp3lame -lameopts vbr=3[/FONT][/FONT][/COLOR]

Thank you.

---

### Post by 71GA on 2011-04-11
Video is converted but is 3x faster than normal.

---

