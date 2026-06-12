---
title: "Avimerge:    Video and sound not matching up after merging"
date: 2008-04-22
forum: Multimedia Software
---

### Post by fredmv on 2008-04-22
Here's the deal.   I'm using [avimerge](http://www.transcoding.org/cgi-bin/transcode?Avimerge) to piece together about 17 AVI videos.     However, once I view the output file, the sound is off later on in the video.     Is there any way around this?   I tried using the "-c" switch which, if I'm reading the man page correctly, should fix the problem, however it did not.

>        -c     
Drop video frames in case audio is missing [off]
	      Only when merging multiple AVI files. Some AVI
	      files run a little bit (usually for one or two
	      video frames) short on audio. This means avimerge
	      cannot keep up sync when concatinating them. The
	      files play fine when played individually but not
	      when merged because audio from the new file gets
	      played back with video from the old file.	 avimerge
	      will print a message like

Any ideas guys?       Whether it be using avimerge or not, I'd appreciate it.      

Thanks all.

---

### Post by heathenx on 2008-04-22
Have you tried mencoder? Below is a sample of how to combine 3 videos. Just edit it and add all 17 of yours and see what happens.

mencoder -oac copy -ovc copy vid1.avi vid2.avi vid3.avi -o final.avi

---

### Post by fredmv on 2008-04-22
> **heathenx said:**
> Have you tried mencoder? Below is a sample of how to combine 3 videos. Just edit it and add all 17 of yours and see what happens.

mencoder -oac copy -ovc copy vid1.avi vid2.avi vid3.avi -o final.avi

Thanks a lot heathenx.   Worked perfectly.

---

