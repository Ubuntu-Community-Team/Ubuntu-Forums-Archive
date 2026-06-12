---
title: "Kalarm - no sound"
date: 2006-07-19
forum: Multimedia &amp; Video
---

### Post by machek2 on 2006-07-19
If I choose either "beep" or "soundfile" in Kalarm, I get no sound when the alarm goes off. 

I know that sound does work, for amarok plays perfectly.

I'm using Kubuntu/6.06

---

### Post by Hikaru79 on 2007-05-24
I can report the exact same error on Kubuntu 7.04

Anyone have any ideas? :(

---

### Post by Banter on 2007-05-25
I have the same problem. I am using Feisty Fawn 7.04 and have installed kmix . . . so make of that what you will.

---

### Post by Rev4n on 2007-09-16
I have the exact same problem and I can't figure out how to make it work.

What I ended up doing was instead of having KAlarm try to run the sound file at the time I wanted the alarm to go off, I had it just execute a terminal command that would open up an mp3 in a media player.

It's not really a fix, just kind of a way to work around the issue.  If anyone know how to solve this, I'd LOVE to know.

---

### Post by aun on 2007-11-28
> **Rev4n said:**
> 

What I ended up doing was instead of having KAlarm try to run the sound file at the time I wanted the alarm to go off, I had it just execute a terminal command that would open up an mp3 in a media player.


I am running a new install of Kubuntu 7.10 gutsty installed from Live CD.  I had already installed kubuntu-nonfree-extras, but had no mp3 ability with kalarm.  If your problem is just mp3s, install libarts1-mpeglib, which provides mp3 support for aRts (this should maybe go into nonfree-extras?).  It worked for me..  I suspect the earlier posts were an aRts problem.

---

### Post by JohnDeCarlo on 2008-04-05
> **aun said:**
> I am running a new install of Kubuntu 7.10 gutsty installed from Live CD.  I had already installed kubuntu-nonfree-extras, but had no mp3 ability with kalarm.  If your problem is just mp3s, install libarts1-mpeglib, which provides mp3 support for aRts (this should maybe go into nonfree-extras?).  It worked for me..  I suspect the earlier posts were an aRts problem.

I noticed that problem, but I also have another Kalarm sound problem.

It will play a .ogg or .flac once, but never again.  And when I close the alarm that went off, it will start to play the file as it closes.

---

