---
title: "audio and video choppy on websites"
date: 2006-01-16
forum: Multimedia &amp; Video
---

### Post by RaiSuli on 2006-01-16
Hi, I already posted this question in the newbie section, but someone suggested I should try it here. Hope that's not considered spamming the board.

So here it goes:

Whenever I try to watch an embedded audio or video file on a website, I run into problems. Audio and video are very choppy, sound is ahead of the video, the video is played single frame. I use Firefox 1.5, have downloaded it and all plug-ins with Automatix, removed the Totem Player plugin, added mplayer and player connectivity and RealPlayer10. The win32 codecs are there, so is a broadband connection. I have Mplayer, VLC, Totem, etc, every player gives me the same results. All the "how to guides" haven't helped either. Have also tried Opera, same result.

Video and audio are fine when played as downloads, but embedded files just don't work. I use an ATI Radeon 9600 graphics card, sound is provided by an on-board Intel 82801DB-ICH4 sound card.

Any help would be really welcome!

---

### Post by arnieboy on 2006-01-16
[QUOTE=RaiSuli]Hi, I already posted this question in the newbie section, but someone suggested I should try it here. Hope that's not considered spamming the board.

So here it goes:

Whenever I try to watch an embedded audio or video file on a website, I run into problems. Audio and video are very choppy, sound is ahead of the video, the video is played single frame. I use Firefox 1.5, have downloaded it and all plug-ins with Automatix, removed the Totem Player plugin, added mplayer and player connectivity and RealPlayer10. The win32 codecs are there, so is a broadband connection. I have Mplayer, VLC, Totem, etc, every player gives me the same results. All the "how to guides" haven't helped either. Have also tried Opera, same result.

Video and audio are fine when played as downloads, but embedded files just don't work. I use an ATI Radeon 9600 graphics card, sound is provided by an on-board Intel 82801DB-ICH4 sound card.

Any help would be really welcome![/QUOTE]
please paste the results of:
```
cat /etc/mplayerplug-in.conf
```

---

### Post by RaiSuli on 2006-01-16
Thanks for the quick reply.

Here it is:

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

---

### Post by Jingo on 2006-01-24
bump

I have the same problem!! Any solution?

---

### Post by beerorkid on 2006-01-27
from bennettg here [http://www.ubuntuforums.org/showthread.php?t=116068&highlight=choppy](http://www.ubuntuforums.org/showthread.php?t=116068&highlight=choppy)
> SOLVED.

edit /etc/mplayer/mplayer.conf add the following to the bottom of the file:

srate=48000


THEN EVERYTHING IS BLISS!!!!!!!!!!!!!!!!!!

I rebooted and it is working now

---

