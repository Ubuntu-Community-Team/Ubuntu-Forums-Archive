---
title: "sound quit after hard reset"
date: 2014-05-03
forum: Multimedia Software
---

### Post by fracasdan on 2014-05-03
Hello. I'm using Ubuntu 14.04 with Unity. I was swapping some USB devices to different ports and Unity froze up on me. I eventually reboot by holding the power button for a few seconds. When I logged back in, all sound was gone. Also, in Settings-Sound, I'm pretty sure there should be something in the **Play Sound Through **box. Please see attached png. Thanks in advance.

---

### Post by fracasdan on 2014-05-03
**sudo apt-get remove --purge alsa-base pulseaudio** to remove devices
**sudo apt-get install alsa-base pulseaudio** to reinstall devices

This broke additional things. Now when going into settings, most of the icons are missing.

**sudo apt-get install ubuntu-desktop **fixed both problems for me. Sound and deivces are back. And my settings icons are back, as well.

---

