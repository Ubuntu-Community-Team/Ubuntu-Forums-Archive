---
title: "Only Dummy Output on Compaq CQ45-902TU running 13.04"
date: 2013-09-29
forum: Multimedia Software
---

### Post by tG7pMet on 2013-09-29
Tried everything and all I could get was the Dummy Output on the HP Compaq CQ45-902TU running 13.04 32 bit.
The Analog, Digital & Digital Surround profiles show up on pavucontrol yet Dummy Output is still the only one that is avaliable.

# cat /proc/asound/card0/codec* | grep Codec
Codec: Realtek ALC269VC
Codec: Intel PantherPoint HDMI

Also installed the latest drivers from  oem-audio-hda-daily-dkms_0.201309280823~ubuntu13.04.1_all.deb 

Full Alsa info below.  Any suggestions?

[http://www.alsa-project.org/db/?f=5a7e766494f41ab1694b9d72018b7ef0fd8a436e](http://www.alsa-project.org/db/?f=5a7e766494f41ab1694b9d72018b7ef0fd8a436e)


Thanks!

---

### Post by Yellow Pasque on 2013-09-30
I would get rid of this line in /etc/modprobe.d/alsa-base.conf :
```
options snd_hda_intel model=ref
```

---

### Post by tG7pMet on 2013-09-30
> **Temüjin said:**
> I would get rid of this line in /etc/modprobe.d/alsa-base.conf :
```
options snd_hda_intel model=ref
```

Yes. Tried setting tha to auto and removing the line all together, still same result. :(

---

