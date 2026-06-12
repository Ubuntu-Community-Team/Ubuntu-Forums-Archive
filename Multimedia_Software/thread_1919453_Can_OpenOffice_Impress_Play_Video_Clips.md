---
title: "Can OpenOffice Impress Play Video Clips?"
date: 2012-02-02
forum: Multimedia Software
---

### Post by lparsons42 on 2012-02-02
Has anyone had success showing video clips in OpenOffice Impress slide shows in presentation mode?  I have so far had none.

After posting my problem earlier, I thought I would try posing it as a question as well to see if maybe someone on a different distro has solved the problem.

I'm running Kubuntu 10.10 with OpenOffice 3.2.1 and found that while I can show the video in layout mode, it won't play in presentation mode.  It doesn't matter if the format is .mov or .avi, the result is the same.

---

### Post by lparsons42 on 2012-02-06
Just as an update, I also tried converting the movie to .mpg and had the exact same result.  I can show the movie clip in preview, but not in slideshow where I just see an empty white box where the clip is supposed to play.

---

### Post by cotcot on 2012-02-06
I have just tried it with Libreoffice impress. Insert movie and sound. Playback in presentation mode is no problem. Video clip was an mp4 but it works also with other formats. 
Do you have play back of the same video in other applications ? Maybe you are missing the codecs. Check if you have gstreamer-plugins ugly installed (restricted codecs).

---

### Post by lparsons42 on 2012-02-06
> **cotcot said:**
> I have just tried it with Libreoffice impress. Insert movie and sound. Playback in presentation mode is no problem. Video clip was an mp4 but it works also with other formats. 
Do you have play back of the same video in other applications ? Maybe you are missing the codecs. Check if you have gstreamer-plugins ugly installed (restricted codecs).

Thank you for the reply.  Unfortunately that made no difference whatsoever.  I can still play the clip in preview but in the slideshow I just get a white box where the video clip is supposed to be.

I previously had the base gstreamer-plugins installed, which did the same thing.  

I would consider upgrading my system to a newer version of Kubuntu, but when I did that on my workstation at work an incredible disaster unfolded that lead to me having to install a new hard drive and start over.  I don't have the time to handle such disasters on my laptop right now.

---

