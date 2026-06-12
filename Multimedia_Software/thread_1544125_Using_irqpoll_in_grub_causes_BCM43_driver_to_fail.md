---
title: "Using irqpoll in grub causes BCM43 driver to fail"
date: 2010-08-02
forum: Multimedia Software
---

### Post by trethacker on 2010-08-02
I recently followed directions at [http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=310018&page=1](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=310018&page=1) to resolve video issues under 10.04LTS.

The resolution worked great for my video issues but caused another problem.

I use a Cisco/Linksys WRC-54G Wireless PCMCIA card (v3.1) in my laptop. After installing 10.04LTS, I was prompted to install the Broadcom BCM43 drivers and once I had done so, my wireless card began working (an issue I had a lot of trouble with in previous versions of Ubuntu).

After adding irqpoll to my grub.cfg file and resolving video, my wireless card still sees my router and continues to attempt connection, but will not connect.

If I remove the irqpoll from the grub.cfg and reboot, the wireless card works flawlessly but the video issue returns.

Is there a way to have irqpoll resolve the video trouble but not affect the wireless card/ BCM43 drivers?

Thanks for any help.

---

