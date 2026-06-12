---
title: "snd_hda_intel, no Microphone. VIA VT1802"
date: 2013-02-24
forum: Multimedia Software
---

### Post by gcbzzzz on 2013-02-24
on an Asus S200 (aka X202e), sound output works perfectly, but sound input is nil.

$ dmesg | grep snd
[   20.384757] snd_hda_intel 0000:00:1b.0: irq 44 for MSI/MSI-X


i'm testing booting several times with and withut acpi_osi=Linux
Without it, i get mic to work sporadically (if some time pass or i touch anything in the volume controls, mic is gone)

alsamixer fiddling does not help. volumes and flags seem to be fine. everything get's detect aparently correctly.

i've spent hours... days... on all guides on how to trouble shoot snd_hda_intel and the docs provided under /usr/share/alsa-base and i'm still clueless.

$ cat /proc/asound/card0/codec* | grep Codec
Codec: VIA VT1802
Codec: Intel PantherPoint HDMI

anyone already got this to work?

---

### Post by Yellow Pasque on 2013-02-24
First thing I'd suggest is using the latest driver:
[https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

---

### Post by kevdog on 2013-02-25
Is the driver just not loading or is it something else?

what's the result of 
aplay -l

---

### Post by azeam on 2013-10-27
> **gcbzzzz said:**
> on an Asus S200 (aka X202e), sound output works perfectly, but sound input is nil.

$ dmesg | grep snd
[   20.384757] snd_hda_intel 0000:00:1b.0: irq 44 for MSI/MSI-X


i'm testing booting several times with and withut acpi_osi=Linux
Without it, i get mic to work sporadically (if some time pass or i touch anything in the volume controls, mic is gone)

alsamixer fiddling does not help. volumes and flags seem to be fine. everything get's detect aparently correctly.

i've spent hours... days... on all guides on how to trouble shoot snd_hda_intel and the docs provided under /usr/share/alsa-base and i'm still clueless.

$ cat /proc/asound/card0/codec* | grep Codec
Codec: VIA VT1802
Codec: Intel PantherPoint HDMI

anyone already got this to work?

Were you ever able to sort this out? I've got a computer using VIA VT1802 and can't get the microphone working no matter what I try. The closest I've gotten is being able to record a few words with very bad sound but after a while it stops working and even with the same settings I can rarely get it working again even after a reboot. The driver is loading and I'm using the latest driver.

---

### Post by Yellow Pasque on 2013-10-27
azeam, I would file a bug since you've verified that the issue occurs with latest driver.
```
ubuntu-bug audio
```

---

### Post by charles18 on 2014-05-29
hi guys

I am not sure if you have found a fix but I found a temporary fix so that sound works on your *VT1802 card*

have a look, post #2 - #4 for indepth details [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1318434](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1318434)

**in short:**

 - add or modify your alsa-base.conf file(the last line) to look like
   this
 - options snd-hda-intel model=auto indep_hp = true
 - reboot
 - sleep the system
 - wake it up again
 - login, sound works (hopefully)

I hope this works for you guys, been looking for a fix for this for a couple of years...

---

