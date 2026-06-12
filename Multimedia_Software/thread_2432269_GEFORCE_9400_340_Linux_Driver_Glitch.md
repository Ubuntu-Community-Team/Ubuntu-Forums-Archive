---
title: "GEFORCE 9400 340 Linux Driver Glitch"
date: 2019-11-29
forum: Multimedia Software
---

### Post by kmand on 2019-11-29
'm running the Geforce 9400 on Linux Ubuntu 18.04 with the Nvidia 340-107 driver. I periodically get glitchy lines near the botton of the screen. I've actually used this setup for years, and it was only in recent months that I have seen it. I don't know what changed. 

This is running on an old Mac mini which I use as a mythtv frontend, and it does really need the vendors driver vdpau support. Nouveau is not sufficient.

I'm running Ubuntu's packaged 340-107. Its more convenient getting updates then downloading the driver install from Nvidia, which I used to do. But again, I've running the Ubuntu packaged driver for sometime before this problem emerged. I do keep the system up to date with patches, so maybe some patch along the way is the issue.

nvidia-settings does give this error message

ERROR: nvidia-settings could not find the registry key file. This file should
       have been installed along with this driver at
       /usr/share/nvidia/nvidia-application-profiles-key-documentation. The
       application profiles will continue to work, but values cannot be
       preopulated or validated, and will not be listed in the help text.
       Please see the README for possible values and descriptions.

that I don't recall getting before. But its possible that I never ran nvidia-settings against the ubuntu package version.
There are lots of posting sthat go back years with this message. I tend to think its not relevant, since once I'm actually playing a video I don't see any issue, so the driver must be working.

The glitchy artifact lines actually show up when using the desktop, or making the transition in and out of video mode.

Actually, yesterday was the first time I noticed a real problem playing a video. It was a very wide screen video, that left a lot of black space above and below the main image. The glitch lines showed up in the black space. Normally I'm watching full screen video and there is no issue.

Any ideas?

---

### Post by Yellow Pasque on 2019-11-30
It could be the GPU going bad. Certain Geforce 9xxx and 8xxx are infamous for this.

---

