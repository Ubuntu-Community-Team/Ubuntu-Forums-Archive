---
title: "What's going on with my nVidia driver/settings, or is it GoogleEarth?"
date: 2007-03-16
forum: Multimedia &amp; Video
---

### Post by robenroute on 2007-03-16
Hi there,

I've got a Gigabyte M55Plus motherboard in my system, and I'm using the on-board VGA: nVidia Quattro NVS210s. Through Automatix2, I've installed the latest (?) nVidia driver (1.0-8776) and the latest GoogleEarth (4.0.2735).

Now, starting up GoogleEarth gives me very convoluted images (see the attached example). Whether I select High Graphics (16 bit) or True Graphics (32 bit) or set the "Safe Graphics Mode", it doesn't make a bleeping difference.

Is there anyone out there that can tell me what I'm doing wrong? Thanks!

Rob

---

### Post by tseliot on 2007-03-16
Try Envy:
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by robenroute on 2007-03-16
Hi Alberto,

Thanks for your quick response. I've just installed Envy (0.9.1), but it says it can't detect my hardware (which is, according to the nVidia driver installed through Automatix, a C51 Graphics processor (Quadro NVS210s)).

The envy-installer.log file suggests installing manually (and on my own risk). Now, can I use Envy to install (forced) the latest nVidia driver anyway?

Thanks,
Rob

---

### Post by robenroute on 2007-03-16
Never mind, I just saw that my on-board VGA is only supported throug hthe legacy driver (1.0-96xx). The new 97xx series doesn't support my hardware anymore.

I guess I'll be buying a new graphics card soon....

Thanks anyway!

---

### Post by robenroute on 2007-03-27
> **robenroute said:**
> ....The new 97xx series doesn't support my hardware anymore....




Somehow, the info on the NVidia pages is wrong! I installed the latest (1.0-9755) driver manually and guess what: everything went like a charm and even GoogleEarth is happy (or should I say, *I'm the happy chappy*....)

Hope this is useful for others.

---

