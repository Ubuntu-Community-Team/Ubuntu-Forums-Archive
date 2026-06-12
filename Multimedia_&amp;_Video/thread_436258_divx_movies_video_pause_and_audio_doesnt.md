---
title: "divx movies video pause and audio doesnt"
date: 2007-05-07
forum: Multimedia &amp; Video
---

### Post by dracule on 2007-05-07
when watching some divx movies, the video always pauses at some points, the audio still runs. about 4 seconds later the video continues. any way to fix this?

---

### Post by DiJEH on 2007-05-08
I have the same problem in VLC player but also the sound seems to break up if it's too loud in VLC player even though everything else the sound doesn't break up even at full blast.

---

### Post by debauchery1st on 2007-05-09
I have the same problem on feisty-64bit.

Mplayer video looks great, but pauses video and continues audio until they catch-up again. I've tried switching to vlc, but the audio in vlc seems too scratchy.

Are you running 64-bit as well?

This problem is very annoying.

---

### Post by DiJEH on 2007-05-09
No, I'm using just normal.

I used automatix to update codecs and I'm still getting no where with fixing the problem. :/

Anyone even got a clue why it's doing this in fiesty when it worked perfectly in Dapper?

---

### Post by debauchery1st on 2007-05-09
try this for now:

"sudo apt-get install mplayer libxine-extracodecs"

mplayer seems to play without the glitch, however, I tried to install "totem-xine" (switches the totem movieplayer engine to xine-lib) and the glitch was still there when playing with the xine-lib engine. 

strange how it plays smooth with xine-lib on a different application, yet glitches in totem movieplayer.

---

### Post by dracule on 2007-05-10
yeah, im in 32 bit... ill see how that what you posted works out.

---

### Post by madeinbrazil on 2008-02-02
Any solutions for this? I'm having the same problem, audio continues but video freezes for about 5 seconds. Happens every 10-20 minutes the video is running.

I'm running Ubuntu 7.10, my machine is working with an nVidia GeForce 6100 nForce 430. I'm also running Compiz. No matter which application I use to run videos on, VLC, Miro, Totem, Mplayer the problem persists.

This is really annoying since I always have to go back to Windows to watch the movies.

Help please?

---

### Post by madeinbrazil on 2008-02-08
Can anyone help? This is really the only problem I have with my Ubuntu. Is it really an issue with nVidia or something I can do with Ubuntu?

---

