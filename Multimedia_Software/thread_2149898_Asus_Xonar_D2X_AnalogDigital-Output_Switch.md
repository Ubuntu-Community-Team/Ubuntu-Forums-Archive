---
title: "Asus Xonar D2X Analog/Digital-Output Switch?"
date: 2013-05-30
forum: Multimedia Software
---

### Post by 1125 on 2013-05-30
Hey there,

I've just managed to install my Asus Xonar D2X (easy going) and it works perfectly so far.
The problem I have is that I'm using a Headset as analog (3,5mm jack) and my Sound-System as Digital (using Coax).
With my Realtek Onboard Sound I was able to switch between analog and digital by changing the device but this option seems to be gone now.

Also in older versions of Ubuntu there was an option called "Analog Loopback". ([http://fc01.deviantart.com/fs48/f/2009/195/4/4/ASUS_XONAR_D2X_LINUX_by_modmadmike.png](http://fc01.deviantart.com/fs48/f/2009/195/4/4/ASUS_XONAR_D2X_LINUX_by_modmadmike.png))
Is there a possibility to just use the output von both analog and digital?

Thanks for reading :(

Greets,
Chris

---

### Post by Yellow Pasque on 2013-05-31
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by 1125 on 2013-05-31
> **Temüjin said:**
> [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

[http://www.alsa-project.org/db/?f=792ce6bf48201465bb27e9cafe94dc570394cd3e](http://www.alsa-project.org/db/?f=792ce6bf48201465bb27e9cafe94dc570394cd3e)

---

### Post by 1125 on 2013-05-31
Also before selecting a profile (the dropdown was on an empty selection before) the sound came on analog output, so actually this can't be a problem of the driver but there's just a setting missing. (there's just "Digital Stereo (IEC958) Output" in the dropdown... after selecting it switched from analog to digital)

[IMG]http://sv1.imageleak.net/cb81e0b03da39f0d4960b37b19ece446.png[/IMG]

---

### Post by 1125 on 2013-06-04
So I think I found my solution. I'm using pavucontrol which's giving me all the options I need! :p

---

