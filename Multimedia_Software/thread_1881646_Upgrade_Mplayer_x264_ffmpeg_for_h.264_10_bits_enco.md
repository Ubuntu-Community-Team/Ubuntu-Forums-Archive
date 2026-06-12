---
title: "Upgrade Mplayer x264 ffmpeg for h.264 10 bits encoded files"
date: 2011-11-15
forum: Multimedia Software
---

### Post by beterhans on 2011-11-15
Hi
I've downloaded some amime videos which encoded with 10 bits? 
and the anime subtitle group mentioned these files are 10 bits I need to upgrade my codec packs

the mplayer on my mac could handle these videos file correctly but my mplayer or vlc on my ubuntu 10.04
were unable to play those files correctly.

I've downloaded the lastest svn mplayer and x264 but when i try to compile it. i saw a option that ./configure give me to choise 8 9 10 bits of depth. does that mean if i choise 10 bits  i won't able to encode regular 8 bits h264 anymore?

and i've noticed that x264 is just a encoder but not a decoder.
so Recompile mplayer should be enought to deal with the 10bits files?
should i compile other library too?

---

### Post by andrew.46 on 2011-11-16
I have to admit that I am not completely sure if the Repository MPlayer will play 10bit video but certainly the guide that I support:

Howto: Build the svn MPlayer under the latest release version of Ubuntu
[http://ubuntuforums.org/showthread.php?t=1542240](http://ubuntuforums.org/showthread.php?t=1542240)

will build an MPlayer with this capability. And as you have noted x264 is not required for playback of h.264 video streams and is not even built in this guide. I will leave more knowledgeable people to answer about x264 and encoding to 10bit :).

---

