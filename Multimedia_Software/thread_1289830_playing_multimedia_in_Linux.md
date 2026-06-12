---
title: "playing multimedia in Linux"
date: 2009-10-12
forum: Multimedia Software
---

### Post by andied on 2009-10-12
I have read through the forums and tried to tweak my 64 bit install and it seems to be running really well overall, but I do have some concerns, but perhaps I have overlooked something. Playing audio/video files (mp3, flac, wv, mpg, mp4, etc.) all seem to require excessive system resources as compared to XP. A flac file uses approx 1.5% cpu in XP and over 11% in Linux; an audio cd uses , 1% cpu in XP and almost 12% in Linux; an mpg music video 15% in XP and 24% in Linux. Similar resutls for DVD's, mp4 video, etc. With the increased cpu use comes an increase in cpu temperature, as well.

Do these results correspond to what others are experiencing, or have I missed something with my Linux setup. I used sysinternals "process explorer" in XP and "Top" in Linux to show cpu use, and tried various media players in Linux (totem, mplayer, rhythmbox, audacious) and the results above represent the best that was I able to obtain. Also some Linux media players struggle with some media; Audacious used over 24% cpu to play an audio cd, but played it really well, and rhythmbox only used aprox 12%, but skips for a second every 20 or 30 seconds.

---

### Post by mc4man on 2009-10-12
If your using jaunty, well, I thought it was very poor in terms of resource usage, both on a newer core2duo and older p4. could easily create absurd levels with mainly third party apps. ( returned or kept those machines with hardy

On karmic now where things are vastly improved, though I'd take cpu usage itself with a grain of salt so to speak. ( and you can't just look at the app itself.


screens  show on p4  amarok 1.4 playing a flac and  aud2 playing a cd on a 5.1 sound system. With a 2 or 2.1 I'd expect slightly lower.  ( note the levels of the app, pulseaudio and xorg will fluctuate slightly, also had a firefox window open

---

### Post by andied on 2009-10-13
Thanks for the reply. I am using jaunty and will perhaps try karmic; I have a core2duo and audacious uses between 15% and 25% of cpu to play a simple flac. I would be delighted with your results.

I see you are using pulseaudio; I had to remove it in order to get my digital mic to work, and am using alsa, so maybe that is causing a problem.

---

