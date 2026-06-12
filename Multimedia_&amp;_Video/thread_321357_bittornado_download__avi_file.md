---
title: "bittornado download  avi file"
date: 2006-12-18
forum: Multimedia &amp; Video
---

### Post by broekskw on 2006-12-18
ok trying bittornado,downloaded a movie in a dvdrip eng.avi formate and tried many players to try and watch movie (totem,mplayer vlc media player) but all will not play, some say no plug in to play. i thought that mplayer did all formates

so what would i need to play this formate.  thanks:mrgreen:

---

### Post by pay on 2006-12-18
Try ```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base \
gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse \
gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libxine-extracodecs w32codecs 

```Make sure that you have to restricted, universe and multiverse repositories,

---

### Post by broekskw on 2006-12-18
hay pay the first command worked ok but the second and the last on i keep getting this error

broeks@broeks-desktop:~$ gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse
bash: gstreamer0.10-plugins-good: command not found
broeks@broeks-desktop:~$ gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse \
> 
bash: gstreamer0.10-plugins-good: command not found
broeks@broeks-desktop:~$ 
broeks@broeks-desktop:~$ 
broeks@broeks-desktop:~$ gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse \
> 
bash: gstreamer0.10-plugins-good: command not found
broeks@broeks-desktop:~$ gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libxine-extracodecs w32codecs
bash: gstreamer0.10-plugins-ugly: command not found
broeks@broeks-desktop:~$ 

any help thanks:mrgreen:

---

### Post by pay on 2006-12-18
It is actually all one command, I just broke it up so it was easier to read.

---

### Post by SmiLey497 on 2006-12-19
could be a fake file

---

### Post by broekskw on 2006-12-19
thanks pay redid that command from terminal all in one and it worked, another question 
how do i see if i have "Make sure that you have to restricted, universe and multiverse repositories,"
was that the command i just ran??
and yes SmiLey497 is was a fake file. still can not find the english one.

e  a g o   

thanks:mrgreen:

---

### Post by pay on 2006-12-19
If the command worked then you have the repositories opened.

---

