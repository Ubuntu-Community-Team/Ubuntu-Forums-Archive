---
title: "No Sound - Realtek HD Audio"
date: 2011-04-12
forum: Multimedia Software
---

### Post by spinydelta on 2011-04-12
Hey Guys, 
     Well I installed Ubuntu 10.10 64Bit along side Windows 7, and I've been unable to get any sounds working, apart from the log on sound. So I tried installing some drivers, and now there is no sound at all, and no sound devices show up in System-Preferences-Sound-hardware

I'm using the on board HD Audio (ALC 889A) and using the optical Audio out for 5.1 Surround sound.

I've tried just using the Stereo ( Green Jack ) out, and still nothing. The suggestions on the on the Ubuntu site, and the following post didn't seem to work either. 

[http://ubuntuforums.org/showthread.php?t=658902&page=1]("http://ubuntuforums.org/showthread.php?t=658902&page=1")

I Can't find a great deal of posts with the Realtek HD audio.

If Anyone would be able to help me out it would be very much appreciated :D

Thank you all in advance.
Josh

---

### Post by lidex on 2011-04-12
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

