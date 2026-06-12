---
title: "Issue with"
date: 2012-05-19
forum: Multimedia Software
---

### Post by tallstreet on 2012-05-19
Hi, 

I am having an issue with my onboard sound. 

For some reason I see this in dmesg: 

media@media-desktop:~$ dmesg | grep snd
[   17.623323] snd_intel8x0 0000:00:1e.2: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   17.623365] snd_intel8x0 0000:00:1e.2: setting latency timer to 64
[   18.644062] snd_intel8x0 0000:00:1e.2: PCI INT A disabled
[   18.644084] snd_intel8x0: probe of 0000:00:1e.2 failed with error -5

I ran alsainfo.sh:

[http://www.alsa-project.org/db/?f=1abbb8a3a8c78d9ff242cb4936558a0408ed5493](http://www.alsa-project.org/db/?f=1abbb8a3a8c78d9ff242cb4936558a0408ed5493)

Does anyone know if this is fixable? Or is it a hardware issue? 

Thanks alot for any help!

Gary

---

