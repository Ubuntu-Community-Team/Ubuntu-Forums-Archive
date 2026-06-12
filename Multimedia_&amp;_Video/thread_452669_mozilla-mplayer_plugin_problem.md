---
title: "mozilla-mplayer plugin problem"
date: 2007-05-23
forum: Multimedia &amp; Video
---

### Post by seandiggity on 2007-05-23
I'm setting up a new Ubuntu Feisty system for a friend, and I have almost everything running smoothly.  However, there is one small problem that will cause my friend some major annoyance (which may make-or-break her opinion of Ubuntu and Linux):

The video on [http://www.hgtv.com/hgtv/pac_ctnt_988/text/0,,HGTV_22056_58466,00.html](http://www.hgtv.com/hgtv/pac_ctnt_988/text/0,,HGTV_22056_58466,00.html) won't play correctly in Firefox, even with the non-free Flash player and wmv codecs installed.  This happens with the totem, vlc, and mplayer plugins for mozilla.

Basically, if I try that video with the mplayer plugin it will play once out of a number of tries.  I've noticed that the problem seems to do with the short commercial that sometimes plays before the main video; after the commercial, mplayer just stops.  Is there just some sort of tweak/setting for mplayer that will resolve this?  Maybe it has something to do with playing the next item in a playlist (or some streaming setting)?

Any help would be MUCH appreciated.  I'm using the newest version of the mplayer plugin (3.40), but I can go back to the older one in the Ubuntu repos.

---

### Post by seandiggity on 2007-05-23
Here's the content of my mplayerplug-in.conf file (everything's currently commented out):
```
#debug=0
#vo=xv,x11
#ao=arts,esd,oss
#download=1
#dload-dir=$HOME/tmp
#keep-download=0
#noembed=0
#cachesize=512
#use-mimetypes=0
#enable-ogg=1
#enable-smil=1
#enable-helix=1
#qt-speed=med
#rtsp-use-tcp=0
#nomediacache=0
#framedrop=0
#autosync=0
#mc=1
#black-background=0
#user-agent=NSPlayer
```

When I uncomment these options, I don't see a change.

---

### Post by mikesf on 2007-05-25
i have similar problems. i found a quick fix.
NOTE: i have all the win32 codes and mplayer stuff properly installed
first: my problem
mplayerplug-in correctly handles *.mpg
mplayerplug-in DOES not handle *.wmv
BUT if i download the very same *.wmv (instead of streaming it) is plays just fine
after some trial and error, it appears mplayer works if i use the xv output

so... my FIX (which isn't perfect)

is to uncomment the line
vo=xv,x11
in /etc/mplayerplug-in.conf

---

