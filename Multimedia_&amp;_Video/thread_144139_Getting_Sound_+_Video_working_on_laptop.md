---
title: "Getting Sound + Video working on laptop"
date: 2006-03-13
forum: Multimedia &amp; Video
---

### Post by Phil99 on 2006-03-13
Just installed Ubuntu 5.10 on my laptop after trying it out on Desktop but have run in to a couple of issues.

Laptop is a really old Fujitsu Lifebook L440, P2-266, 160MB etc.

Firstly, Video:

It detects the videocard fine as "MagicGraph 128XD", it's a pretty basic chip but can run the display at 1024x768 16bit (native) and 800x600 24bit. Problem is I can only seem to get 800x600 :confused: 

/etc/X11/xorg.conf lists 1024x768, but that's about as far as I know to look, I guess it's pretty simple, but I don't have a clue...?

Secondly, Sound:

SuSE is the only distro that's actually properly detected my soundcard and been able to use it.

In "Device Manager" it's detected as "PNP Device (ESS1879)" and "Device Type: Unknown".

Could anyone possible point me in the right direction to get this installed as a sound device please? I've had a look around the GUI but I have a feeling I'm in need of some config file editing etc?

Thanks for any help!

---

### Post by stuporglue on 2006-03-13
> SuSE is the only distro that's actually properly detected my soundcard and been able to use it.

In "Device Manager" it's detected as "PNP Device (ESS1879)" and "Device Type: Unknown".

Could anyone possible point me in the right direction to get this installed as a sound device please? I've had a look around the GUI but I have a feeling I'm in need of some config file editing etc?

I think this is your driver:

```
stuporglue@ubuntoo:~$ modprobe -l | grep es18
/lib/modules/2.6.15-18-686/kernel/sound/isa/snd-es18xx.ko

```

Try adding snd-es18xx to /etc/modules

sudo echo "snd-es18xx" >> /etc/modules

Then reboot and see if it works.

---

### Post by Phil99 on 2006-03-13
I managed to get the 1024x768 resolution by increasing the horizontal sync range in xorg.conf; no idea why it was set low by default, but it's working now :)

Thanks for the reply, but unfortunately that didn't seem to do anything.

I did however Google with the es18xx and found a site with a /etc/modprobe.d/soundcard config that seemed to do something:

```
alias sound-slot-0 snd-card-0
alias snd-card-0 snd-es18xx
options snd-es18xx enable=1 isapnp=0 port=0x220 mpu_port=0x388 fm_port=0x330 irq=5 dma1=1 dma2=0
```

After a reboot it works perfectly, so thanks for pointing me in the right direction!

Just tried my Wireless card; it took all of 30 seconds to install and configure with WEP :mrgreen:

---

