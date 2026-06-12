---
title: "Trouble Recording Audio"
date: 2009-04-04
forum: Multimedia Software
---

### Post by madnessman on 2009-04-04
I'm just trying to record myself playing guitar to a backing track. My amp has a simulated line out so I connected my amp to my computer's line in. I can hear myself playing through headphones. However, I can't do any recording. I just get no sound. 

Audio Conferencing
Sound Capture: 
HDA ATI SB ACL888 Analog (ALSA)
HDA ATI SB ACL888 Digital (ALSA)
HDA ATI SB ACL888 Analog (ALSA) <= Why do I have 2?
HDA ATI SB ACL888 Analog (OSS)

Any advice?

---

### Post by CJ_Hudson on 2009-04-04
Your best bet is to obtain a proprietary sound-mixer/micro-studio recording software program and run it in Wine (Windows simulator for Linux).

---

### Post by madnessman on 2009-04-05
You mean something like Cubase or Ableton?

---

### Post by madnessman on 2009-04-05
BUMP:
Any more advice? I want to be able to record using Audacity. Right now I can't even get anything using Sound Recorder. So I'm pretty sure it's a driver issue.

---

### Post by markbuntu on 2009-04-05
Get the gnome-alsamixer from the repos and post a screenshot of it and we will see what we can do for you. The gnome-alsamixer is easier to use and shows everything on one page.

---

### Post by pgmer6809 on 2009-04-05
> **madnessman said:**
> I'm just trying to record myself playing guitar to a backing track. My amp has a simulated line out so I connected my amp to my computer's line in. I can hear myself playing through headphones. However, I can't do any recording. I just get no sound. 

Audio Conferencing
Sound Capture: 
HDA ATI SB ACL888 Analog (ALSA)
HDA ATI SB ACL888 Digital (ALSA)
HDA ATI SB ACL888 Analog (ALSA) <= Why do I have 2?
HDA ATI SB ACL888 Analog (OSS)

Any advice?

Sound in Ubuntu seems to have gotten very complicated. There is ALSA, PULSEAUDIO, JACK etc. etc. I never could get all those to work properly for playback and record.
Finally I gave up on ALSA, uninstalled pulseaudio, and just used the latest download of OSS from the 4-Sound web site.
They have a debian package.
I was then able to record in Audacity with no problems or hassle.
See my post: OSS works, ALSA doesn't of a couple of weeks ago.
(search on pgmer6809)
pgmer6809

---

### Post by markbuntu on 2009-04-05
Try this post for recording with audacity

[http://ubuntuforums.org/showthread.php?t=1005196](http://ubuntuforums.org/showthread.php?t=1005196)

---

### Post by CJ_Hudson on 2009-04-14
> **madnessman said:**
> You mean something like Cubase or Ableton?

Yes, they would probably do the job. But perhaps they are overly complicated if you just want to lay down a few chords alongside a backing track.
Sorry for the delay in replying. Busy bringing the sheep into the paddock!

---

