---
title: "nvidia driver issue"
date: 2008-12-15
forum: Multimedia Software
---

### Post by tendu on 2008-12-15
Hi guys,

I'm new in the Ubuntu community but not from Linux...
I just converted my Hardy machina to Intrepid and the nvidia driver stuff didn't go silky smooth.... :(

I don't get the "Direct redering" and when I launch the nvidia-settings command from a console, here is what I guet:


Error: API mismatch: the NVIDIA kernel module has version 177.80,
but this NVIDIA driver component has version 177.82.  Please make
sure that the kernel module and all NVIDIA driver components
have the same version.
NVIDIA: Direct rendering failed; attempting indirect rendering.
Error: API mismatch: the NVIDIA kernel module has version 177.80,
but this NVIDIA driver component has version 177.82.  Please make
sure that the kernel module and all NVIDIA driver components
have the same version.
NVIDIA: Direct rendering failed; attempting indirect rendering.
Error: API mismatch: the NVIDIA kernel module has version 177.80,
but this NVIDIA driver component has version 177.82.  Please make
sure that the kernel module and all NVIDIA driver components
have the same version.
NVIDIA: Direct rendering failed; attempting indirect rendering.
Error: API mismatch: the NVIDIA kernel module has version 177.80,
but this NVIDIA driver component has version 177.82.  Please make
sure that the kernel module and all NVIDIA driver components
have the same version.
NVIDIA: Direct rendering failed; attempting indirect rendering.
Error: API mismatch: the NVIDIA kernel module has version 177.80,
but this NVIDIA driver component has version 177.82.  Please make
sure that the kernel module and all NVIDIA driver components
have the same version.
NVIDIA: Direct rendering failed; attempting indirect rendering.


I've removed the nvidia-kernel-common, installed again, same with the driver through the automatic utility from the "System/administration/Hardware Drivers" menu... Nothing! still the same message.

I have to say that before upgrading my machine from Hardy to Intrepid I tried (stupidly) to install the nvidia driver (the *.run) manually... Is it the source of the problem?

If anyone has any clue about that I will be very happy to hear it ;)

Thanks by advance!

---

### Post by kpkeerthi on 2008-12-15
Uninstall nvidia-glx-177 and nvidia-settings (if you installed it offline from other sources on the web, follow the uninstallation procedure that is applicable for the method). Switch to 'nv' open source driver. **Reboot.** (so that the kernel module unloads). And install using System -> Admin -> Hardware Driver.

---

### Post by n0th1n on 2008-12-24
yea, I'm encountering the same error using World of Warcraft in WINE. 

I tried what you suggested, and it the problem is the same. There IS a 177.82 kernel module, isn't there?

---

### Post by Synthandrus on 2009-01-07
Had the same problem after the latest auto update on Intrepid. Re-installed 177 through apt and all is good again.

apt-get install --reinstall nvidia-glx-177

did the trick for me. :)

---

### Post by Gary13579 on 2009-01-07
> **Synthandrus said:**
> Had the same problem after the latest auto update on Intrepid. Re-installed 177 through apt and all is good again.

apt-get install --reinstall nvidia-glx-177

did the trick for me. :)

Fixed it, thank you!

Please note I had to restart after this command.

Edit: Video card is an nVidia GeForce 9600 GT.

---

