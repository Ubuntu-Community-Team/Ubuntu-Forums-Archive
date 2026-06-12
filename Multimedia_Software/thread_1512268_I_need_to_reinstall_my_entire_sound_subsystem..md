---
title: "I need to reinstall my entire sound subsystem."
date: 2010-06-17
forum: Multimedia Software
---

### Post by Konqueror on 2010-06-17
I have been in the IRC asking around what to do about my problem. A very helpful guy (paultag) found out I'm apparently missing the WHOLE subsystem to my audio part. I am a complete beginner to the whole Linux experience and what he said is that my installation is missing /dev/mixer. No idea what that is, but I'm missing it. Ubuntu can recognize my sound card (Creative X-Fi Xtreme Audio) but it doesn't know what to do with it. Does anyone have any ideas on how I can reinstall the subsystem required to make this work?

---

### Post by lidex on 2010-06-18
Try this. Using a Terminal="Applications->Accessories->Terminal"
```
sudo apt-get update
sudo apt-get upgrade
```
```
sudo apt-get install --reinstall alsa-utils alsa-oss alsa-base libasound2 libasound2-plugins linux-sound-base gstreamer0.10-alsa
```
**Reboot.**

You may find this helpful:
[http://ubuntuforums.org/showthread.php?t=870001&highlight=creative+xfi]("http://ubuntuforums.org/showthread.php?t=870001&highlight=creative+xfi")

---

