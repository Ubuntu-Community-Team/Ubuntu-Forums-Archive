---
title: "[SOLVED]Nvidia driver works... until computer is rebooted!"
date: 2006-11-29
forum: Multimedia &amp; Video
---

### Post by asta on 2006-11-29
A strange problem indeed. When I reboot my computer, I cannot get the nvidia driver (tested both with the lats 9629 and edgy default) to work immediately. Instead I have to boot in to fail-safe mode, chang the driver to "nv", and start my system. After that I can change back to "nvidia" and restart X-server with Ctrl-Alt-Backspace. The log file now shows that the nvdidi driver is running and all is well (glxgears works etc)

Any hints where I should start looking to fix this? HW problem?

.
.
.
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): NVIDIA GPU GeForce2 MX/MX 400 at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 65536 kBytes
(--) NVIDIA(0): VideoBIOS: 03.11.00.08.00
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): Interlaced video modes are not supported on this GPU
.
.
.
.

---

### Post by myname on 2006-11-29
I have a similar problem.  I can install the nvidia drivers per the many instructions, and everything is cool, I can get my resolution in 1280x1024, however, the second I reboot, X fails to start with an error, I don't remember the error right now.  I need to copy over the original Xorg.conf file to get into the GUI.

Any ideas?

--kevin

---

### Post by asta on 2006-11-29
SOLVED! AGP problem. MY BIOS had setting of 64M AGP aperture, but agpgart discovered 128M aperture. Changing BIOS to 128M seemed to solve it.

I'm not sure what it actually means, though...

---

