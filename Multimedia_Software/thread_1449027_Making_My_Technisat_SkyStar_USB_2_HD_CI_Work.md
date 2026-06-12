---
title: "Making My Technisat SkyStar USB 2 HD CI Work"
date: 2010-04-07
forum: Multimedia Software
---

### Post by linuxus95 on 2010-04-07
Hey, and thanks for checking this out. I recently purchased the DVB-S tuner mentioned in the title. I now realize it is not natively supported in linux, but i don't know how to get it to work. I found some instructions written in German (which I don't understand), so I couldn't use that. I need to know what patch/driver I need to compile into the kernel and how to do it. Under lsusb, the device shows as ID 14f7:0002. If it there is no solution for this at the moment, will this be supported in future kernels? Will be glad for all replies!

---

### Post by linuxus95 on 2010-04-11
I've kind of figured something out... I found this wiki page on Linux TV:[ http://linuxtv.org/wiki/index.php/Technisat_SkyStar_USB_2_HD_CI]("http://linuxtv.org/wiki/index.php/Technisat_SkyStar_USB_2_HD_CI"). There seems to be some info as to where to download and how to compile a driver for this card. Mercurial fails to find the repository, though. If anybody has any further suggestions, I would be glad to hear from you!

---

### Post by linuxus95 on 2010-04-17
I've managed to compile the v4ldvb driver with the patch. The Linux TV wiki says something like "you will need to change the USB ID to make it work." Tuner still has the same 0002 id under lsusb. Any ideas on how to do that?:)

---

### Post by limotux on 2011-05-24
Bump!

I'm interested as well to get the same working on lucid.

Can someone help please.
I'll appreciate a step by step guidance.

---

### Post by limotux on 2011-05-25
bump

---

