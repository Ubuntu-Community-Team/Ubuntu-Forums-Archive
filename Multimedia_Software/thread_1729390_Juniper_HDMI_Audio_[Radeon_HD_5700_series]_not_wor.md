---
title: "Juniper HDMI Audio [Radeon HD 5700 series] not working in ubuntu10.10"
date: 2011-04-14
forum: Multimedia Software
---

### Post by yld629 on 2011-04-14
Hi, new to Ubuntu. I have a HP Envy 17 that has sound for the analog device but can't get anything to output from the HDMI device.  fchin1@FrozenSteppes:~$ aplay -l **** List of PLAYBACK Hardware Devices **** card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]   Subdevices: 1/1   Subdevice #0: subdevice #0 card 1: Generic [HD-Audio Generic], device 3: ATI HDMI [ATI HDMI]   Subdevices: 1/1   Subdevice #0: subdevice #0  I'm not sure how to proceed from here, any advice would be greatly appreciated.

---

### Post by papibe on 2011-04-14
Did you install the ATI proprietary drivers?
Regards.

---

### Post by yld629 on 2011-04-15
I'm not really sure where to find that information tbh.

---

### Post by K_45 on 2011-04-15
Did you set the correct output in the sound applet?

---

### Post by yld629 on 2011-04-15
> **K_45 said:**
> Did you set the correct output in the sound applet?

 That's actually where I noticed it. I saw that it was set to the analog and I wanted to switch it to the HDMI device but when I did nothing was forthcoming from the speakers at max volume.

---

### Post by K_45 on 2011-04-15
In the System Menu, look for Additional Drivers, and activate the ones listed. Reboot. Result?

---

### Post by yld629 on 2011-04-15
> **papibe said:**
> Did you install the ATI proprietary drivers?
Regards.

 I'm not sure if it's the driver that installed with the additional drivers you are talking about but I did install that one.. it seems to be a proprietary one.

---

### Post by yld629 on 2011-04-15
> **K_45 said:**
> In the System Menu, look for Additional Drivers, and activate the ones listed. Reboot. Result?

Ah, yes then I do have those to no effect sadly.

---

### Post by K_45 on 2011-04-15
Deactivate the drivers, more info here, and try the other steps also listed:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by kwikshot on 2011-05-05
I have this same problem to with the same Graphics Card

---

