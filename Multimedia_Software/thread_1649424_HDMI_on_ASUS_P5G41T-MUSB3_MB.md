---
title: "HDMI on ASUS P5G41T-M/USB3 MB"
date: 2010-12-20
forum: Multimedia Software
---

### Post by lesliem on 2010-12-20
Hi,
Upgraded to above MB with Intel dual core CPU. Tried monitor connected to onboard video, Intel GMA X4500 GPU via HDMI port and removed nvidia card.
Result during boot "top left" monitor displays analogue/digital alert window only. Then nothing, black screen only the OS loads as I can hear boot up process. Sound works fine
Running Mint Julia x64. Have reverted to old video card till get this cracked.
Is this an X driver problem??
Any ideas very welcome.

Cheers & Merry Christmas to all out in LinuxLand.
:D

---

### Post by BicyclerBoy on 2010-12-21
Have you un-installed the nvidia driver ?

You may need to edit (backup & delete) /etc/X11/xorg.conf   as it probably contains driver info for nvidia driver.

The newer drivers recreate/don't need the xorg.conf file.

The intel X4500 is still rubbish compared to nvidia GPU.
The GT430 is an excellent cheap option - full HDMI audio etc.

---

