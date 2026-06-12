---
title: "getting a Prism AVI converter equivalent for UBUNTU"
date: 2009-09-16
forum: Multimedia Software
---

### Post by yanvolking on 2009-09-16
Hello Community,
 
I have recently migrated from windows to UBUNTU.
 
I am a great consumer of AVI video files.  I watch them on a small portable media player.  This media player works well with AVI files with a video stream of up to 500 kbit/s.  More than this and the video/audio sync quickly gets out of phase.  Most movies I get have video stream rates of 1000 kbit/s or above.  
 
With windows I would simply reduce de bit rate using PRISM AVI CONVERTER, an excellent simple to use multi media management program.  This however does not run on linux.
 
I really dont need a complex package capable of converting one format to the other or ripping etc etc.  I just need something to effectively "downsize" my AVI files (many portable media players come with CDrom to load a program wich does just that).
 
DOES ANYONE KNOW OF A CLONE OF PRISM AVI CONVERTER WHICH WORKS WITH UBUNTU, PREFERABLY IN A GUI ENVIRONMENT?
 
:P

---

### Post by yanvolking on 2009-09-30
Hello Community,

Well, I finally found various solutions myself.  

1) Download AVIDEMUX from the ADD/REMOVE option.  It does most audio/video file management work but rather sophisticated for novices such as myself.  Still by trial and error I finally managed to reduce the Kbit/sec rate of an AVI file.

2) Download IRIVERTER, also from the ADD/REMOVE option. 
converts video for use on various multimedia players 
iriverter is a cross-platform frontend to mencoder designed to facilitate the conversion of almost any video format to one that is playable on various multimedia players.
Homepage: [http://iriverter.sourceforge.net/index.shtml](http://iriverter.sourceforge.net/index.shtml)
It is extremely simple to use with very few options.  The downside to this program is that the output file is destined for small handheld media players and therefore a very high compression rate with a rather poor image quality.

3) download the original PRISM AVI converter and open it inside the WINE environment.  You can then run from there working with files from outside the WINE environment.

HAPPY AVI FILE EDITING

Y.

---

