---
title: "Choppy Video"
date: 2009-02-21
forum: Multimedia Software
---

### Post by apparle on 2009-02-21
I have Kubuntu 8.10 with fglrx driver installed.

I tried various players > Mplayer, VLC, Kaffiene

Irrespective of the format of the file the video I see is choppy...
This happens when I have KWin desktop effects enabled.

When I disable the desktop effects I can see the video normally.

I checked on a friend's laptop with the same version, video playback was normal. ( He doesn't have an ATI card).

Please help

---

### Post by binbash on 2009-02-21
I guess you have an ATI card,

Go to your video player's preferences (for example vlc) and set the video output to X11

---

### Post by apparle on 2009-02-22
I've tried setting it to X11....in vain.
Actually I have tried each of the options in video output of each of the player, but the video is choppy.........

I reapeat when I disable the KWin desktop effects, all the players start playing the video smoothly

---

### Post by Pfredpfudpucker on 2009-02-27
I have the same problem in 8.10, and have been searching for a solution for about 2 weeks now.  It seems that no one is really too interested in addressing this problem - perhaps there isn't a fix.  I have looked all through the forums, FAQs and Sticky's Stickys and still have found nothing helpful.

---

### Post by jamillikan on 2009-03-01
I, too, experienced the issue you describe but resolved it by first removing VLC.  Thereafter, I did the following:

I went to this site:  [http://archive.getdeb.net/dump/intrepid/vlc/](http://archive.getdeb.net/dump/intrepid/vlc/) and installed the following files:

vlc 0.9.8-1~getdeb1
vlc-nox 0.9.8-1~getdeb1
libvlccore0 0.9.8-1~getdeb1
libvlc2 0.9.8-1~getdeb1

I chose the ones for the i386, but also present are AMD64 versions as well.  (I cannot comment on the AMD64 debs because I haven't used them, only the i386 ones.)

After installing the four above files, my choppy/hanging video issue has been resolved.  Hopefully, this information will assist you, too.

Joe

---

