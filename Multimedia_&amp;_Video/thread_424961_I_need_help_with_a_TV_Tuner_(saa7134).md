---
title: "I need help with a TV Tuner (saa7134)"
date: 2007-04-27
forum: Multimedia &amp; Video
---

### Post by Verminoz on 2007-04-27
Hello there,
I am running Kubuntu 7.04 and I have an AverMedia TV card in my computer. Giving an lspci on my console gives out this line among others:

"01:00.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)"

I looked for drivers for this chipset and found this:
[http://linux.bytesex.org/v4l2/saa7134.html](http://linux.bytesex.org/v4l2/saa7134.html)
where it says that the drivers are included in my kernel. Kubuntu 7.04 has a 2.6.x kernel version, right?
Which pretty much makes sense because the saa7134 device is listed with other multimedia cards such as my soundcard when taking a look at the available multimedia devices in KMix for example.

I tried using kdeTV, xawTV and other programs but they do not recognize any device. Any ideas?

Thank you in advance.

---

### Post by jolan_jj on 2007-04-27
Take a look here:

[http://gentoo-wiki.com/HARDWARE_saa7134](http://gentoo-wiki.com/HARDWARE_saa7134)

Try modprobe'ing with different card and tuner numbers.

---

