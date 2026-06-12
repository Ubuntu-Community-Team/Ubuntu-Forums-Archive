---
title: "flash video (youtube) sound is out of sync"
date: 2009-07-26
forum: Multimedia Software
---

### Post by Tyrsius on 2009-07-26
I'm am not even sure where to start with this one. If I am watching a video thats in flash, or whatever youtube uses, the sound gets progressively farther from synced with the video. This doesn't happen with all streaming video, just flash.

Anyone have any ideas?

---

### Post by igorzwx on 2009-07-26
Type on terminal:

aplay -l

---

### Post by Tyrsius on 2009-07-26
> **igorzwx said:**
> Type on terminal:

aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC662 Analog [ALC662 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

This was the output from that command.

---

### Post by igorzwx on 2009-07-26
check if your hardware is supported by OSS4
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)
**Does OSS Support My Hardware?**

 Check the list [here]("http://mercurial.opensound.com/?file/6bf18b4a87d6/devlists/Linux"). Some devices may not have full functionality (e.g. the X-fi module is limited to stereo output at the time of this writing, and jack sensing may not work on Azalia-compliant "High-Definition" devices, which are very common on motherboards and laptops today). If you're in doubt, consult the "Additional Support" sources found towards the end of this document.

---

