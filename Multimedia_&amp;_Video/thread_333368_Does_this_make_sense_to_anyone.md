---
title: "Does this make sense to anyone"
date: 2007-01-07
forum: Multimedia &amp; Video
---

### Post by JParkus on 2007-01-07
Im still trying to get sound out of my ess18xx(I think its a ess1869)

oem@oldp2:~$ sudo dpkg-reconfigure alsa-source
 
Package `alsa-source' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: alsa-source is not installed

oem@oldp2:~$ sudo modprobe snd-es18xx enable=1 isapnp=0 port=0×220 

mpu_port=0×38 8 fm_port=0×33$
FATAL: Error inserting snd_es18xx (/lib/modules/2.6.15-27-386/kernel/sound/isa/s nd-es18xx.ko): No such device
oem@oldp2:~$ sudo nano /lib/modules/2.6.15-27-386/kernel/sound/isa/snd-es18xx.ko ): No such device
bash: syntax error near unexpected token `)'

oem@oldp2:~$  sudo nano /lib/modules/2.6.15-27-386/kernel/sound/isa/snd-es18xx.k o

^@<3>invalid dma2 %d
^@<3>reset at 0x%lx failed!!!
^@ES18xx - CTRL^@ES%x^@ESS AudioDrive ES%x^@ES18xx^@ES18xx DMA 1^@ES18xx DMA 2^@%s at 0x%lx, irq$^@<3>dsp_get_byte failed: 0x%lx = 0x%x!!!
^@^@^@^@Hardware Master Playback Volume^@Hardware Master Playback Switch^@<3>es18xx: unable go g$^@^@^@<3>es18xx: [0x%lx] ESS chip not found
^@^@<3>[0x%lx] unsupported chip ES%x
^@^@^@<3>es18xx: unable to grap ports 0x%lx-0x%lx
^@^@^@^@<3>es18xx: unable to grap IRQ %d
^@^@^@<3>es18xx: unable to grap DMA1 %d
^@^@<3>es18xx: unable to grap DMA2 %d
^@^@<3>es18xx: PnP control configure failure (out of resources?)
^@^@^@<3>es18xx: PnP manual resources are invalid, using auto config
^@<3>es18xx: PnP configure failure (out of resources?)
^@^@^@<3>es18xx: unable to install ISA PnP hack, expect malfunction
^@^@<3>es18xx: unable to find a free IRQ
^@^@^@<3>es18xx: unable to find a free DMA1
^@^@<3>es18xx: unable to find a free DMA2
^@^@%s at 0x%lx, irq %d, dma1 %d, dma2 %d^@^@^@<4>es18xx: opl3 not detected at 0x%lx
^@^@<3>ESS AudioDrive ES18xx soundcard not found or device busy
^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@author=Christian Fischbach <fishbach@pool.informatik.rwth-aachen$

Im guessing i need to reinstall ALSA but the only way i know how to do it is through synaptic

I downloaded everything i could form the alsa site but i dont know how to install it form my home folder

---

### Post by AndrewB on 2007-01-07
You are not alone. I tried and tried to get the same chipset working on my Gateway laptop (SOLO 5100) to no avail. Ended up reinstalling Win98se and calling it a wrap.

Andrew

---

### Post by JParkus on 2007-01-07
Im not ready for that Im probably going to be stuck buying a soundcard

---

