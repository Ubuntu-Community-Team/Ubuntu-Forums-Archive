---
title: "ALS300+: Sound card detected but no volume. HELP!"
date: 2005-11-20
forum: Multimedia &amp; Video
---

### Post by mickeyckm on 2005-11-20
Hi everyone,

I have a laptop with a sound card from AvanceLogic and the device manager detected on Ubuntu Breezy is ALS300+ PCI. However, there is no sound coming out. Anyone can help me out? Thanks in advance. 

Best Regards,
Mickey

---

### Post by DriverDevel on 2005-12-16
Hi,

someone is currently developing an ALS300 ALSA driver (playback already initially working!). It will hopefully be able to support ALS300+, too. Contact me for further information.

About the "Sound card detected": well, if you consider correctly listing PCI information bits and pieces to be "detected"... ;-)

---

### Post by mickeyckm on 2005-12-16
thanks for the reply. I've solved the problem with OSS. They have the driver. :)

---

### Post by rem on 2005-12-28
[QUOTE=DriverDevel]Hi,

someone is currently developing an ALS300 ALSA driver (playback already initially working!). It will hopefully be able to support ALS300+, too. Contact me for further information.

About the "Sound card detected": well, if you consider correctly listing PCI information bits and pieces to be "detected"... ;-)[/QUOTE]

Hi,

I talked my brother into installing Ubuntu for his desktop. He's having ALS300 also, but can't find a driver to it. Can you help me please?

---

### Post by Lord Illidan on 2005-12-28
From what what the above said, you have to configure it so that it uses OSS instead of ALSA (forgot how to do it in GNOME)

---

### Post by rem on 2005-12-28
ok, got it thanks but that's exactly the big issue... hoe to configure it with OSS :(

---

