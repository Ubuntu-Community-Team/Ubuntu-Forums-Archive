---
title: "PCM sound stopped working through SPDIF"
date: 2008-12-09
forum: Multimedia Software
---

### Post by oblib on 2008-12-09
I got pulseaudio sound working just fine on my Intrepid Mythtv box (not mythbuntu). PCM sound goes through pulseaudio out the digital out, and Dolby encoded stuff goes directy out to the receiver (receiving the digital signal). I added "load-module module-alsa-sink device=hw:0,1" to my default.pa to make this work. It works great as long as I don't try to use pulse sound and Dolby sound at the same time (I have to reload pulse if I do that).

This was all working just fine until Sunday morning when normal (non-Dolby) sound stopped working. Mythtv,mplayer, aplay, etc. cannot make sound come out at all for non-Dolby stuff. The volume meter in pulseaudio still shows sound getting to it, but it doesn't get to the receiver. Dolby stuff still goes directly through just fine. The only thing I can think could have changed between working and not working was that I performed the recommended package upgrades on Saturday (I don't remember what they were, but I don't think there was anything directly audio related).

I have plenty of practice debugging audio problems but this one has me stumped. I've tried rebooting, reloading pulseaudio, disabling pulseaudio and using alsa directly, and nothing comes out. Any ideas?

---

### Post by tsaarni on 2009-01-09
> **oblib said:**
> 
This was all working just fine until Sunday morning when normal (non-Dolby) sound stopped working. Mythtv,mplayer, aplay, etc. cannot make sound come out at all for non-Dolby stuff. 

I think I'm experiencing the same problem.  Have you found solution for this?

---

### Post by tsaarni on 2009-01-09
Found a fix/workaround [here]("http://ubuntuforums.org/archive/index.php/t-445536.html") i.e. replaced the value field in "IEC958 Playback Default" control in /var/lib/alsa/asound.state.  Not elegant but worked for me...

---

### Post by markbuntu on 2009-01-09
Did anybody file a bug report on this?
It won't get fixed unless someone tells the devs something is wrong.

---

### Post by tsaarni on 2009-01-10
It seems to be fairly well known problem, [see link]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/25632").  I'm pretty sure it must be logged in alsa bug tracker too but didn't find it... Their search kind of sucks. 
There might be more than one causes for this problem though as it seems to be so common and still unfixed after several years.

---

