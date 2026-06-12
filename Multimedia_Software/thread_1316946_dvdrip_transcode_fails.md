---
title: "dvd::rip transcode fails"
date: 2009-11-06
forum: Multimedia Software
---

### Post by drfox on 2009-11-06
I need some help. I'm using Karmic 64-bit. I have tried 7 (!) times to transcode a dvd, and it keeps failing at about 98% done. I have tried changing from AVI to MPEG using various codecs, but always get the same results. I have tried updating mplayer to the latest with the experimental ppa. What shall I try next?
Thanks, Larry

---

### Post by strangeattractor on 2009-12-05
Are you attempting to transcode the entire DVD?  If so, check to see if the last Chapter in the Title has a very short length, around zero seconds.  If it does, then transcode all of the chapters except for the last one, and leave out any others with very short lengths.  This has worked for me sometimes in the past, when the transcoding got stuck near the end of a DVD, or near the end of a Title.

---

### Post by inobe on 2009-12-07
i found that too much of applications being replaced and installed will cause problems.


when ever i do a fresh install, i update, i enable hardware driver, i grab restricted extras, and install the needed codecs from medibuntu and finally handbrake, devede, xine..........

one of the above will need ffmpeg ;)

never follow guides, keep it simple and ultimately ask the rite question and display the correct problems, someone out there is likely to understand.

---

