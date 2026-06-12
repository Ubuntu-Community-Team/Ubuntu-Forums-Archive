---
title: "[SOLVED] Running .mkv using Haali Media Splitter in Hardy Heron"
date: 2008-07-12
forum: Multimedia Software
---

### Post by euchrid33 on 2008-07-12
I have some Matroska (.mkv) files that I'm trying to play.  They start in VLC just fine, but freeze up before long.  A bit of research tells me that it's because they require the Haali Media Splitter.  I know that Haali works just fine in Windows, but I can't find a Linux version, or any workaround.  I've set it up in Wine, but it doesn't work - when I run the movie through the Windows version of VLC, in Wine, it still fails.

For the record I'm running Hardy Heron.

---

### Post by shirilover on 2008-07-12
Have you tried using another player, like MPlayer, to see if the problem is negated?

Matroska files do not need Haali, VLC should be using demux_mkv.
Also, are you running compiz, if so, try disabling it.

---

### Post by euchrid33 on 2008-07-12
Okay, mplayer works perfectly.  Thank you for suggesting it!  I didn't know that it supported .MKV.  Looks like I could have just found my new favourite player.

---

### Post by Duranxl on 2008-07-19
Im having problems too..
MKVs wont play in VLC, yet they DO play on VLC under windows :S??!

Also, when i play 1080p mkv files (most mkv are HD?) im getting 1-3 fps in Mplayer...yet with MPC and CoreAVC i play them at 30fps under windows..


Any help?

---

### Post by Duranxl on 2008-07-19
should i make another thread because this one says SOLVED?

---

### Post by euchrid33 on 2008-07-19
Have you tried running them in mplayer?  Like I said above, that worked perfectly for me.  Mine were hi def rips as well, encoded in some special way to save on filesize.

---

### Post by Duranxl on 2008-07-19
> **euchrid33 said:**
> Have you tried running them in mplayer?  Like I said above, that worked perfectly for me.  Mine were hi def rips as well, encoded in some special way to save on filesize.

Yes like i said in my 1st post i get 1-3 fps in mplayer when playing 1080p movies

---

### Post by shirilover on 2008-07-19
I'm not sure if there is multi-threaded H.264 video decoding in libavcodec yet.
You can try adding threads=2 to your ~/.mplayer/config file, to see if playback improves.
Or, if you feel adventurous, you can try compiling mplayer with coreavc following the steps here -> [http://code.google.com/p/coreavc-for-linux/w/list](http://code.google.com/p/coreavc-for-linux/w/list)
This is the best we can do until libavcodec supports multi-threaded AVC decoding.

---

### Post by flytripper on 2008-07-19
what is your cpu/gpu setup? is it even up to the job? i have a p4 2.8g and an nvidia 7600gt and my sytem wont play 1080p

---

### Post by Duranxl on 2008-07-19
> **shirilover said:**
> I'm not sure if there is multi-threaded H.264 video decoding in libavcodec yet.
You can try adding threads=2 to your ~/.mplayer/config file, to see if playback improves.
Or, if you feel adventurous, you can try compiling mplayer with coreavc following the steps here -> [http://code.google.com/p/coreavc-for-linux/w/list](http://code.google.com/p/coreavc-for-linux/w/list)
This is the best we can do until libavcodec supports multi-threaded AVC decoding.
Thanks i'll give it a try
> **flytripper said:**
> what is your cpu/gpu setup? is it even up to the job? i have a p4 2.8g and an nvidia 7600gt and my sytem wont play 1080p
Yes my PC can handle 1080p, it's a T7300 core2duo @2ghz with 8600M Gt GPu.
And like i said, the vids run 100% smooth in windows.
Which is like 8x the FPS!!!! (24 instead of 3fps!!)

---

### Post by Duranxl on 2008-07-20
Whoops, found out i played using totem instead of mplayer.
It's better now, but still not good enough.
I tried following the CoreAVC guide, but i cant get it to work..it says it cant find config.mak when i get to the compiling part...
So i have 2 questions:

1) could anyone help me out with the coreavc guide? 
2) Is there any other way to get mplayer to run it smooth?
My core2duo should be able to handle it with 'ease'..

edit:
-lavdopts fast=1:skiploopfilter=all
seems to help a fair bit!

---

