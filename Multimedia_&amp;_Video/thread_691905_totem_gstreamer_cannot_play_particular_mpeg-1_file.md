---
title: "totem gstreamer cannot play particular mpeg-1 file properly which ffplay can"
date: 2008-02-09
forum: Multimedia &amp; Video
---

### Post by harishcm on 2008-02-09
Hello there!

I can't get this particular mpeg-1 file to play properly in totem gstreamer. The video images are jumbled up although the sound is alright. I would like to know if others are facing the same problem and of any fixes before submitting a bug report. 

file:  [http://www.myabike.com/videos/A-bike_movie2006.mpeg](http://www.myabike.com/videos/A-bike_movie2006.mpeg)
from website: [http://www.myabike.com/Gallery.html](http://www.myabike.com/Gallery.html)

I used the default totem-gstreamer in Gutsy.

Totem 2.20.1
GStreamer 0.10.14
Gnome 2.20.1
Ubuntu 7.10 Gutsy

I tried solving the problem by installing w32codecs, gstreamer-0.10pitfdll and other gstreamer plugins in synaptic until i exhausted all of them but still could not get it to work properly. I also installed some libxine plugins. Only then did it occur to me to try the playback on another player. (Quite dumb.. haha!)

So i tried using ffplay from the ffmpeg package in both official ubuntu and medibuntu packages and the video plays perfectly!

So that brought me to the conclusion that this may be a bug in totem or gstreamer. I still haven't tried totem-xine yet which will narrow down the problem... I will do that soon when I get a bit more time.

It would be great if you guys could also try the video link and report your results. Any advice will also be appreciated! Thanks!

---

### Post by harishcm on 2008-02-10
okie.. I installed totem-xine and tried out the video. It plays it but the colours are off by a fixed offset of pixels. I have included screenshots of both totem-gstreamer and totem-xine... notice that the save screenshot option works properly in both instances... Could this be a problem in totem then, not gstreamer or xine?

I've also included a screenshot of ffplay playing the file properly. Any guesses on what might be the problem? And does the same happen on your system? Thanks for your help and advice!

---

### Post by harishcm on 2008-03-28
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/totem/+bug/208321](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/208321) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I've found that it's not an issue with totem. Trying 'gst-launch-0.10 playbin uri=http://www.myabike.com/videos/A-bike_movie2006.mpeg' does not play the mpeg file properly. 

Interestingly, the issue with totem-xine does not occur anymore. I did remove my nvdia fx 5900 card with nvidia drivers and am currently using the intergrated VIA Unichrome CLE266 with opensource drivers. But note that I have not put the nvidia card back in and try to reproduce the initial totem-xine issue.

So, it looks like the issue might be in gstreamer-0.10.14.

I have also found that if I open two 'instances' of gstreamer, the second one will play properly. This is true for `2x gst-launch windows' or `1 gst-launch and 1 totem window (in either order)`

I've filed a bug in launchpad about the issue in gstreamer.

---

