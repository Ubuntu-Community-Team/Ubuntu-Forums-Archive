---
title: "HELP! lost spdif! Is it fried?"
date: 2008-07-02
forum: Mythbuntu
---

### Post by pssturges on 2008-07-02
My system has been running nicely for quite some time using spdif passthru. I got up this morning and no sound! Checked all the basic stuff like mute, connections etc., no luck. I'm beginning to think my spdif out might be fried. Output of aplay -L is:

```

front:CARD=NVidia,DEV=0
    HDA NVidia, AD198x Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, AD198x Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, AD198x Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, AD198x Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, AD198x Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, AD198x Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
null
    Discard all samples (playback) or generate zero samples (capture)


```

No sign of iec958! Any ideas how I may be able to sort out what's going on, short of replacing the MOBO/soundcard?

Cheers
Phil

---

### Post by jbman on 2008-07-03
have you rebooted and checked the logs on reboot?

---

### Post by pssturges on 2008-07-03
Thanks,
I have rebooted several times, but not sure which logs to look at?

---

### Post by jbman on 2008-07-03
is there light coming out of the cable?

---

### Post by Trollslayer on 2008-07-03
Shut down and disconnect from power for a couple of minutes, it can happen that something 'latches up' and needs power removed completely.

---

### Post by pssturges on 2008-07-04
> **jbman said:**
> is there light coming out of the cable?

Coax SPdif, so no light! I tried booting from the live CD. No sign of iec958 when running aplay -L. That to me would suggest a hardware problem:(

---

### Post by DLLarson on 2008-07-06
> **pssturges said:**
> Coax SPdif, so no light! I tried booting from the live CD. No sign of iec958 when running aplay -L. That to me would suggest a hardware problem:(

I'm thinking this isn't a hardware issue because I'm having the exact same problem after an Ubuntu update. I don't see any ALSA configuration file and see the exact same aplay output as this thread's original poster.

Kernel update perhaps?

Dale

---

### Post by pssturges on 2008-07-06
I don't think I ran any updates in the days preceding this problem occurring. But, I hope your right, at least then there should be a fix at some point. Running on analog stereo just ain't the same.

Which chipset are you running? Mine's a NVIDIA nForce 430 MCP, Asus M2N mobo.

Actually, wasn't there an alsa update recently? Or is my memory shot as well?:confused:



Phil

---

### Post by pssturges on 2008-07-08
Further developments...aplay -l gives:
```

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Shows digital.Maybe driver/asla issue?

---

### Post by jbman on 2008-07-08
what if you run the live cd and check that way same result?

---

### Post by DLLarson on 2008-07-08
> **pssturges said:**
> I don't think I ran any updates in the days preceding this problem occurring. But, I hope your right, at least then there should be a fix at some point. Running on analog stereo just ain't the same.

Which chipset are you running? Mine's a NVIDIA nForce 430 MCP, Asus M2N mobo.

Actually, wasn't there an alsa update recently? Or is my memory shot as well?:confused:
Phil

My motherboard is an "ASUS M2NPV-VM". Looks like the same motherboard as yours. No coincidence here!

Dale

---

