---
title: "Why does it refuse to be multimedia?"
date: 2008-06-10
forum: Multimedia Software
---

### Post by Sunsawe on 2008-06-10
Hi everyone,

Am facing a problem which is very annoying! First of, I have ubuntu installed on a laptop Dell XPS 1530M.

This is the thing:

About Sound:

I can only have one software using the sound. One from the beginning and for ever. It means that if after logging in, i start pigdin, then i have pigdin's sounds but i can't play any mp3 until i restart the system. Rhythmbox just does nothing when i press play. It doesn't freeze, the time bar doesn't progress either, it just does nothing. And so do all the other players.
If i start RhythmBox first, the i can listen to my mp3, but no pigdin alerts.

About Video:

Well, it is even simpler. If i don't start a video player in the minute following the log in time, i can't watch a video until i restart the system. I mean that within this minute, if I start the movie player, it is working fine. I have to keep it open if i want to see something later. If i don't then:
Movie player: plays the videos in slow motion. Something like 1/10 of a second of the movie, every real second. Like if you were playing crysis on a pentium II.
Mplayer: does like RhythmBox, just nothing.
VLC: plays the video perfectly but with no sound. Well, it never plays any sound.
Remark: The mplayer plugin in firefox seems to work regardless to the other players (so far, my only solution to watch a video...)


This is it! I suppose that it is just a configuration issue, but it is quite annoying so I hope you can help me.

Thank you!

---

### Post by markbuntu on 2008-06-11
There is a guide to setting up your multimedia in the top of the Mutimedia and Video section of the forums.

---

### Post by Vivaldi Gloria on 2008-06-11
The following guide solved all my sound problems:

[http://ubuntuforums.org/showthread.php?t=776739](http://ubuntuforums.org/showthread.php?t=776739)

---

### Post by Sunsawe on 2008-06-17
Thanks, so far it seems that it has solved the video issu.

But i still can have one and only one software using the sound. So no music if pigdin is on.

---

### Post by markbuntu on 2008-06-17
You need this to do that.

libesd-alsa0 

Enlightened Sound Demon (allows  multiple audio streams on one device)

You can get it with synaptic.

---

### Post by Sunsawe on 2008-06-21
it seems that all the problems have been solved by configuring pulse audio.

---

