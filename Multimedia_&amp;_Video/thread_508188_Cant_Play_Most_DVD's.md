---
title: "Cant Play Most DVD's"
date: 2007-07-23
forum: Multimedia &amp; Video
---

### Post by blueb73 on 2007-07-23
ahhhhhh!

this is driving me nuts!

and i have tried so many things to fix it, i know im all screwed up.

here it is

i can play everything it seems but a regular dvd.  

i tried xine, didnt work.  movie player, nope.  vlc, didnt happen.

i have some backups that do work with totem, and you can fastforward with the arrow keys, but if you use the slide bar it crashes!

help!  :)

---

### Post by RomeReactor on 2007-07-23
Hi. Have you added the [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") Repositories? If not, or you're not sure, post the output of this command on the terminal (Applications->Accessories->Terminal):
```
cat /etc/apt/sources.list
```

---

### Post by Gremlinzzz on 2007-07-24
What i have too do to setup mplayer first i uninstall totem and its plugin.
then i get the deb package for smplayer [http://smplayer.sourceforge.net/](http://smplayer.sourceforge.net/) plays my dvd movies.
Then i install mplayer plugin using synaptic package manager.
now for the codecs paste commands in terminal
[https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28codecs%29](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28codecs%29)
now thxs to this forum i add divxs plugins to watch divxs online
cd /usr/lib/firefox/plugins/
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.xpt
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.so
last but not least i test mplayer plugin at [http://www.hogsbreath.com/hogcam/](http://www.hogsbreath.com/hogcam/)
if its gray i config the settings by right clicking the video window and choose X11 video &ALSA audio
Thats it and it works great i can watch dvd movie cds and divxs movies and streaming video.
these are the setup tweaks i learned for mplayer i could not find tweaks that match em for totem.

---

### Post by blueb73 on 2007-07-24
do i have to uninstall totem?  it plays my wmv, flv, etc fine.

will mplayer play all those?

---

### Post by avik on 2007-07-24
> **blueb73 said:**
> do i have to uninstall totem?  it plays my wmv, flv, etc fine.

will mplayer play all those?

I never uninstalled totem, but yess, mplayer will play those files.

---

### Post by Gremlinzzz on 2007-07-24
Na if it works for ya keep em. 
:guitar:

---

### Post by blueb73 on 2007-07-26
well, i got the dvd playing now, but now, the screen is full of tiny dots!

even the normal vids have them

ack!!!

---

### Post by RomeReactor on 2007-07-26
Can you post a screenshot so we can have a reference? what video card do you have?

---

### Post by blueb73 on 2007-07-26
i tired, but they both turn out blue


and how would i upload it?

and its the standard dell laptop.

what kills me is the resolution was fine, but i did this

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Multimedia_Players_.26_Browser_Plug-ins](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Multimedia_Players_.26_Browser_Plug-ins)

to get it working, and now theres all these dots!

---

### Post by blueb73 on 2007-07-26
disregard the above

i can do the screenshot, but it looks fine.

aaaaaaaaaaaaahhhhhhhhhhhhhhhhhhhh

the colors are not nearly as sharp anymore either.

hmmm, switching beryl to metacity seemed to work!

[http://forum.beryl-project.org/viewtopic.php?f=37&t=6121&hilit=](http://forum.beryl-project.org/viewtopic.php?f=37&t=6121&hilit=)  this was the same issue...

---

### Post by avik on 2007-07-27
> **blueb73 said:**
> hmmm, switching beryl to metacity seemed to work!

[http://forum.beryl-project.org/viewtopic.php?f=37&t=6121&hilit=](http://forum.beryl-project.org/viewtopic.php?f=37&t=6121&hilit=)  this was the same issue...

Well, then you'll have to make do without beryl for the time being.  File a bug report.  After all, it *is* beta software.  Good luck on getting this problem solved.

---

