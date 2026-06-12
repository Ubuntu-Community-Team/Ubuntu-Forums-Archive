---
title: "mpeg4 encoded with mencoder stops at the beginning on divx web player 2.1"
date: 2011-03-23
forum: Multimedia Software
---

### Post by envis on 2011-03-23
Hey whats up, im having a problem encoding some videos to be played by a divx player on my ubuntu server.

basically the problem is that when i encode certain avi files with the xvid codec or with the lavc coded on the mpeg4 option, these files stop at the beginning when trying to watch them in that new divx player 2.1, when using an older version of that player it works fine.

Oh ok i know the problem is with the new divx and i should ask them but i have asked them and i got no answer of course, im not sure if theyll ever answer me..

here is an example of my encoding job:

```
mencoder blahblahvid.avi -ss 00:20:00 -endpos 00:02:00 -ovc copy -oac copy -o littlechunk7.avi
nice -n 19 mencoder littlechunk7.avi -nosound -ovc xvid -xvidencopts pass=1:autoaspect -passlogfile rebarbalog8.log -o /dev/null
nice -n 19 mencoder littlechunk7.avi -ofps 23.976 -oac mp3lame -lameopts preset=70 -passlogfile rebarbalog8.log  -ovc xvid -xvidencopts pass=2:autoaspect:bitrate=-2500 -o /var/www/cheezer/videohost1/test14.xvid
```

that works just great, make a very tiny decent quality video its awesome, but! on that damn divx player 2.1 the video stops at 0:00 seconds, it actually just seems to play a fraction of second and then stops..

im not sure if it has anything to do but so far ive noticed that all the videos that have that problem say "Seems stream 0 codec frame rate differs from container frame rate: 23.98 (65535/2733) -> 23.98 (2997/125)" when running a "ffmpeg -i filename.avi" on them

oh and anyways the problem is very weird because if i move the divx player 2.1 after the beginning lets say at 0:05 and play it from there then it plays fine. also works fine on any other player but divx web player 2.1. unfortunately i find no other decent way of playing video on windows in a webpage than that divx player... theres flash but it makes a uglier video for a bigger size...

im thinking maybe my problem might have something to do with that container frame rate problem but im not sure.... i also dont know how can i fix that container frame rate problem, is there something i can do about it?

if no one has any clue i will understand! im just risking the question!!

:popcorn:

---

### Post by envis on 2011-03-23
when i try encoding this way instead:

[HTML]sudo nice -n 19 ffmpeg -i littlechunk6.avi -vcodec mpeg4 -vtag divx -vb 5000k -r 23.976 -acodec libmp3lame -ab 32k /var/www/testjoy/videohost1/test31.avi[/HTML]

then the result is a bit different, while it still just works on divx web player 1.5 on 2.1 theres still a problem but this time instead of stopping at the beginning, the video seems to play, the time is going up and you can hear the sound but the screen is black, then it continues playing but beeing black like that, its like if the video never actually starts playing. if you just move the cursor and put it at any point other than the beginning then it plays ok from that point and the video is there looking good.

---

