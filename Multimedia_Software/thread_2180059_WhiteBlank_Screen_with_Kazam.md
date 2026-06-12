---
title: "White/Blank Screen with Kazam"
date: 2013-10-11
forum: Multimedia Software
---

### Post by sam4 on 2013-10-11
hi everyone i don't know, what i am doing wrong ? I try to record my screen on [COLOR=#ee82ee][SIZE=2][FONT=arial black]Ubuntu 13.04 with Kazam[/FONT][/SIZE][/COLOR] but when i done with recording and then i play my video , output video i got is completely white/blank (i can see my mouse pointer is moving in output video). So i have to do something with settings of kazam or anything else ?

---

### Post by john188 on 2014-04-10
Same problem! Help!

---

### Post by 23dornot23d on 2014-04-10
Try 

vokoscreen - does the same thing happen ( this works well with compiz running )

or 

recordmydesktop ( this does not work well with compiz )

_________________________________

To install ...... open a terrninal and do .......

[B]sudo apt-get update

sudo apt-get install vokoscreen

sudo apt-get install recordemydesktop[/B]

---

### Post by monkeybrain20122 on 2014-04-10
What is your video format? What are your graphic card and video player? For some reasons if you record in mp4 all mplayer/mplayer2 based player like smplayer and gnome-mplayer behave badly if hardware acceleration is turned on and you have to either disable hardware acceleration for these players or use something like totem or vlc to watch the video. Alternatively you can record in webM though that seem to be more cpu intensive.

I tried kazam on 3 machines with intel, nvidia and adm cards (kind of cover all ground) and kazam works beautifully with unity (the amd machine has weak cpu so need to reduce frame rate)  It doesn't work so well with gnome-shell, but it could be due to Fedora or my compile (on Fedora Kazam needs to be compiled from source and the process is not so straight forward due to missing libraries etc)

---

