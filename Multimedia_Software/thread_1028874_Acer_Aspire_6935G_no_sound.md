---
title: "Acer Aspire 6935G no sound"
date: 2009-01-02
forum: Multimedia Software
---

### Post by frozen_zeus on 2009-01-02
Hi all, I can't get the sound working on my new laptop. I'm using Ubuntu 8.10 64 bit, the sound card is shown below which I got from lspci -v

```

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio 
Controller (rev 03)
        Subsystem: Acer Incorporated [ALI] Device 0146
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at db300000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: oss_hdaudio
        Kernel modules: snd-hda-intel

```

The sound card works in vista. I have checked the ALSA website and they do not appear to support ICH9 sound cards. I've tried a number of different methods using the ALSA drivers and I have also tried stopping ALSA and using OSS. I am hoping that if I put this on the forum either someone else will have a solution or someone that knows what they are doing will see this and maybe create a solution.

Many Thanks.

---

### Post by frozen_zeus on 2009-01-05
*bump*

---

### Post by IQRules on 2009-01-05
Assume it is similar to Thinkpad T400,

[http://www.thinkwiki.org/wiki/Install_Ubuntu_8.10_(Intrepid_Ibex)_on_a_Thinkpad_T400](http://www.thinkwiki.org/wiki/Install_Ubuntu_8.10_(Intrepid_Ibex)_on_a_Thinkpad_T400)

---

### Post by frozen_zeus on 2009-01-06
Unfortunately that site does not say anything about sound drivers or anything. Any other ideas?

---

### Post by AJB2K3 on 2009-01-06
I've got an 3690 and installed every thing as the guide said but still had the trouble.
I went to System>Preferances>sound and found it had changed the 
**Default mixer device.**
I changed it back to the inbuild sound and it seams to work again.
Try changing between the sound card and pulse audio options to see if that works.

---

### Post by greg batmarx on 2009-01-25
i have exactly the same problem...
i tried everything but nothing worked...:(

---

### Post by iasenko on 2009-02-15
I just ordered my new 6935G today, and now I saw this thread,what happened? Have you fixed the problem? It looks like there will be a lot of work to do. BTW what's your impression about this notebook?

10x :)

---

### Post by rimas79 on 2009-04-08
Try add 

```

alias snd-card-0 snd-hda-intel
options snd-hda-intel enable_msi=1
options snd-hda-intel model=auto
options snd-hda-intel single_cmd=1

```
at the end of /etc/modprobe.d/alsa-base.conf

---

