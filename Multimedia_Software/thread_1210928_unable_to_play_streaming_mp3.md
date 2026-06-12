---
title: "unable to play streaming mp3"
date: 2009-07-12
forum: Multimedia Software
---

### Post by gahligahli on 2009-07-12
currently using ubuntu jaunty, 64 bit

I listen to streaming radio because i get weak FM reception at my place.  

I have used audacious to load up a .m3u file I have saved on my computer, and it worked.  This has been ample for many months.  But now Audacious is getting too unstable for me so I have removed it.  

I am now unable to load up the .m3u file, or the direct link to the mp3 in any of the following programs.  


[http://202.6.74.107:8060/triplej.mp3](http://202.6.74.107:8060/triplej.mp3)
triplej.m3u file on pc
[http://abc.net.au/streaming/triplej/triplej.m3u](http://abc.net.au/streaming/triplej/triplej.m3u)


unable to play with 

mpg123
mplayer
rythmbox
amarok
vlc
alsa player

i believe my preference would be to get it working in mpg123.    

having previously worked, did audacious removal take away dependencies of some sort?  had audacious been running like a dog (pun!)  because it is not entirely compatible with 64 bit or jaunty?  

i have googled extensively but cant find what i am looking for.  Plenty on setting up your own streaming server, not so much on trying to listen to someone elses.  I have been through the Multimedia Guide on this site also.  It's good!  Helped me with a lot of things :)  Not this though.  

Can post actual error output if necessary.

---

### Post by andrew.46 on 2009-07-12
Hi gahligahli,

MPlayer plays the stream quite nicely:

```
mplayer -playlist http://abc.net.au/streaming/triplej/triplej.m3u
```

Is your copy of MPlayer setup for mp3 playback? Try running the following from a command prompt:

```

andrew@skamandros~$ **[COLOR="Purple"]mplayer -ac help | grep mp3[/COLOR]**
mp3         mp3lib    working   mp3lib MPEG layer-2, layer-3
ffmp3on4    ffmpeg    working   FFmpeg Multi-channel MPEG layer-3 on MP4 audio  [mp3on4]
ffmp3       ffmpeg    working   FFmpeg MPEG layer-3 audio  [mp3]
ffmp3adu    ffmpeg    working   FFmpeg MPEG layer-3 adu audio  [mp3adu]
mp3acm      acm       working   MPEG layer-3  [l3codeca.acm]

```

All the best,

Andrew

---

### Post by gahligahli on 2009-07-12
Thank you andrew!  

my grep results were identical to yours.  

and you are right, the stream plays perfectly when using your command suggestion.  

i live... in noob city :(

thanks again.

---

### Post by andrew.46 on 2009-07-13
Hi gahlghali,

> **gahligahli said:**
> [...] the stream plays perfectly when using your command suggestion.  

i live... in noob city :(

thanks again.

No problems, I am glad to hear it all works with MPlayer at least :-).

Andrew

---

### Post by vinutux on 2009-07-13
Try banshee or rhythmbox

.

---

