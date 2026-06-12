---
title: "Realmedia with mplayer plays sound but not video"
date: 2007-12-16
forum: Multimedia &amp; Video
---

### Post by Donnw on 2007-12-16
Mplayer will only play sound and not video when playing realmedia rm files. I am using Gutsy. As far as I know I have all the correct codecs installed, these are the same as on my Laptop which works perfect.  Other video files play fine. I have tried installing mplayer again but does not cure the problem.

---

### Post by srmantis on 2007-12-16
you need download from:
[http://www.mplayerhq.hu/design7/dload.html](http://www.mplayerhq.hu/design7/dload.html)
The Binary Codec Packages:
-Linux x86 20071007 or
-Linux AMD64 20071007
the next step is unrar the folder and you make a folder in /usr/lib and call it win32:
sudo mkdir /usr/lib/win32

You copy all the file of the folder essential-20071007 (or essential-amd64-20071007) to /usr/lib/win32

Now, to run the mplayer and you go to the PREFERENCES, then:
Audio select Alsa
Video select X11 X11(XImage/Shm)
Codecs & demuxer:
-Video codec family: RealVideo decoder
-Audio codec family: FFmpeg/libavcodec audio decoders

Ok and ready

---

### Post by Swankyman on 2007-12-17
Nice

Works really nice now

:)

---

### Post by Sebastral on 2007-12-25
Still refused to play realmedia giving;

[INDENT]Cannot find codec matching selected -vo and video format 0x30345652.
Read DOCS/HTML/en/codecs.html! [/INDENT]

I was supposed to extract the rp9codecs downloaded from [here]("http://www.mplayerhq.hu/MPlayer/releases/codecs/") in the /usr/lib/win32 directory too. I'm happy that worked and don't have to compile or worse try and install realplayer :popcorn:

---

