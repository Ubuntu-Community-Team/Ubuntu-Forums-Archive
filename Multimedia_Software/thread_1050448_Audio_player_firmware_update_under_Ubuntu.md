---
title: "Audio player firmware update under Ubuntu"
date: 2009-01-25
forum: Multimedia Software
---

### Post by kriukov on 2009-01-25
I have a Ritmix RF-5200 audio player. About once a year the firmware gets buggy and I have to reinstall it. I have a Windows installer but under Wine the USB device does not get detected, nor does it under QEMU Windows XP. Inside of the installer program I clearly see the *.db files which must be the images to be written to the player. When I tried writing them using dd, the player didn't work. The only way I could do it was find a Windows machine and use it (don't want to dedicate my real hardware to Windows even temporarily as it's very aggressive about MBR and things like that). Is there a nice way to write the firmware on the player? It seems to me that it must be the process as simple as writing an image file to a storage device and it's a pity they overcomplicate it by using installer programs.

---

