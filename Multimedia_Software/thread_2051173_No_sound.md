---
title: "No sound"
date: 2012-09-01
forum: Multimedia Software
---

### Post by satimis on 2012-09-01
Hi all,

Ubuntu 12.04 desktop 64bit
HDMI

sudo cat /etc/default/grub | grep GRUB_CMDLINE_LINUX_DEFAULT
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash radeon.audio=1"

```

-> System Settings -> Sound
Output
Play sound through
HDMI/DisplayPort
RS780 HDMI Audio [Radeon HD 3000-3300 Series]

Installing;
flashplugin-nonfree-extrasound and browser-plugin-gnash
and reboot
didn't help.

Movie on Movie-Player is jumping.

Pls help.  TIA

B.R.
satimis

---

### Post by TheFu on 2012-09-01
I've found that using alsamixer to select the default audio device (F6) and check the volume levels works.  That assumes you have the correct, non-free, video drivers loaded. Without those loaded and working for your specific GPU, you are SOL.  BTW, the "post release" ATI drivers refused to install for me and removed the prior ATI drivers from the system. I had to reinstall them.

---

### Post by Yellow Pasque on 2012-09-01
> That assumes you have the correct, non-free, video drivers loaded. Without those loaded and working for your specific GPU, you are SOL.
The non-free drivers are optional (i.e. free drivers are not "incorrect"). Non-free drivers are not needed for HDMI audio, except for really recent RadeonHD cards.

---

