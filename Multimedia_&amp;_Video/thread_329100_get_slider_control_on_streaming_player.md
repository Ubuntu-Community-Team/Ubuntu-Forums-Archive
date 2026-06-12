---
title: "get slider control on streaming player"
date: 2006-12-31
forum: Multimedia &amp; Video
---

### Post by Lary Grant on 2006-12-31
MLB.com is a baseball site that offers live and archived baseball game videos for subscribers.  Unfortunately it is very Windows-centric.  To access the videos, the site opens up a Flash window which contains links.  When you click on a link the video plays inside a part of the flash window.  From the hours I've spent on and off getting this site to work in Ubuntu, I have found out that the format of the videos is actually .wmv (even though they are playing inside a flash window).

The good news is that the site actually works somewhat (especially for live games) using the non-free codecs, Firefox, and mplayer plugin.  I had to change a "noembed" setting in mplayer plugin to make it open its own window, because it can't play inside the flash window.  However, there are 2 major flaws.

1. When I try to play some archived games, the only thing I see is a video from mlb saying that there is a commercial in progress (forever).

2. For the archived games that do work, there is no way to move backward or forward in the video or even to pause.  There is no on-screen slider and even the obscure mplayer keyboard commands don't work.  The only option is to watch the whole thing from beginning to end (including the pre-game show).

I have a son who is really getting on my case to put Windows back on the computer, because he remembers that Windows Media Player had a slider on-screen that would let him pause or move back and forth, so he could watch archived games in parts.

As I mentioned earlier, I have worked this problem on and off for about a year, including posting forum messages and even working with the developer of mplayer plugin (unfortunately he can not reproduce problem 1 on his machine and has no advice for problem 2).

I figure I'll try 1 more time.  I am open to all options... I'm not locked in to Firefox / mplayer.

---

### Post by trippinnik on 2007-04-07
I am having similar problems, but most of the archived games run and intro to the game over and over.  I have had more success using totem's (xine) plugin though.  I have a slider, but it doesn't seem to work.  It would be great to be able to skip stuff.

I have also been trying to get it running under a Virtual Machine (using virtual box) and running windows 2000 under that.  Unfortunetly I haven't had much success with that yet either.  Has anyone had success with archive clips consistantly?

---

