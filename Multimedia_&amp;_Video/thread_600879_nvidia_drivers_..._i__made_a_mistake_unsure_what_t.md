---
title: "nvidia drivers ... i  made a mistake unsure what to do now to fix"
date: 2007-11-02
forum: Multimedia &amp; Video
---

### Post by ravensteve on 2007-11-02
Hi  I am semi new  to Ubuntu . installed and working fine on lowish spec machines of some friends have managed to persuade to have it and use it.  however i  have recently got a new pc and have installed it on there (E6850, 680i,  8600GTS) .  The  problems began when I tried to install in the nvidia restricted drivers I didn't realise that you were meant to disable parts of x-org and I got a really mashed up screen loads of  streaks of colour in all different directions!  An a message semi-showing in the corner saying something like video drivers not found.  I then ran x-org conf utility and got  the graphical interface working by puting nv drivers on   but made a mistake on the resolution and so is  displaying with  black strip down the side. then I tried "envy" to uninstall and reinstall the driver's.  This lead again to  wacky screen.

I would like to have  the nvidia drivers and to have on the side back. is it possible to have any guidance on  fixing it  or is it a case of reinstall Ubuntu  thank you in advance for your response. 

Many thanks
Ravensteve

PS apologies for bad spelling and punctuation,i  am dyslexic.

---

### Post by scrooge_74 on 2007-11-02
Start over again,

login on a terminal CTRL+ALT+F2

then cd /etc/X11

sudo nano xorg.conf

go to the video driver section and where it says probably nvidia, type nv

then type sudo sh /etc/init.d/gdm restart

or hit CTRL+ALT+F6 and then CTRL+ALT+BACKSPACE to restart the Xserver

if you dont get your login back

go back to the console and type sudo dpkg-reconfigure -phigh xserver-xorg

and give appropriate replies, and use the nv driver for the moment 
that should put you back again at the begining

---

### Post by ravensteve on 2007-12-05
right had loads of work to do the last couple of weeks so  took time to do  that didn't work. so i wiped partition in windows and reinstalled using the nv drivers,   however the aspect ratio still is not right. it now almost wide-screen but not quite right there's still a 1.5cm bar down the side its about 14:9 then my screens 16:9   have i missed something somewhere. or is it something that needs a command line? 

:confused:

thanks

Steve

---

### Post by scrooge_74 on 2007-12-05
It could be you need to just adjust the monitor, I remember the days I did dual boot (not any more thank God) in XP the monitor was one way and in Linux it was a little different

i just had to rezise the screen using the botons in the monitor

---

### Post by ravensteve on 2007-12-05
ok ill have a look  but my monitor is dvi only so is controled from the drivers 

steve

---

### Post by ravensteve on 2007-12-06
the resolution on  xorg hadn't picked up the  resolution so that's that fixed yay. now the drivers again !!! oh joy .

thank you very much for your help

---

### Post by scrooge_74 on 2007-12-06
good to hear is resolve, remember to mark the thread as solve

---

