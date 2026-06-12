---
title: "Bird box video quality problem"
date: 2009-04-25
forum: Multimedia Software
---

### Post by SteveDee on 2009-04-25
I'd given up trying to use my Ubuntu 8.04 pc to display & capture video from a bird box, due to inferior video quality compared to using a small TV.

I placed the blame on the ancient Pinnacle PCTV card. But I'm just revisiting this problem as (quite by chance) I noticed that the application "Cheese" is able to display video from the Pinnacle with good quality.

Previously I was running VLC using this command line:-
vlc --width=1000 v4l:/dev/video0:norm=pal:channel=1

So 2 questions:-
 - How can I improve the quality when using vlc to display composite video?
 - Can anyone advise how to try this using mplayer (i.e. what would the command line look like)?

I suspect the problem is due to the video driver, but how does Cheese produce better results? (sorry that's 3 questions).

---

### Post by SteveDee on 2009-04-25
Well I've managed to find an answer to my 2nd question by [a lot of] experimentation. 

Running mplayer from the command line using this:-

mplayer tv:// -tv input=1:driver=v4l:device=/dev/video0:width=640:height=480 -vo x11

...seems to give an image quality very similar to the Cheese app.

If I can just work out how to save/record the video stream, I should be able to use it with one of my cameras.

---

### Post by SteveDee on 2009-04-26
I've tried adding dumpstream to my command line so it should display and record video at the same time, but no joy!

The full command line is:-
mplayer tv:// -tv input=1:driver=v4l:device=/dev/video0:width=640:height=480 -vo -x11 -dumpstream -dumpfile /home/birdbox/myvideo.avi

Running this just creates an empty file (myvideo.avi) and the terminal info includes:-

MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
...
mplayer: could not connect to server
mplayer: No such file or directory
...
Playing tv://.
Core dumped ;)
Exiting... (end of file)

Can anyone suggest what I'm doing wrong?

---

