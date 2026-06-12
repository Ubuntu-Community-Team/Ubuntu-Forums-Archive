---
title: "How to enable sound driver at startup?"
date: 2015-04-05
forum: Multimedia Software
---

### Post by eamner on 2015-04-05
Hello

After trying many possible solutions, I figured out why I'm not getting sound in my computer. I have a m-audio delta 1010lt soundcard. 
Long story short: I realized I can have sound back with this line:
```
sudo modprobe snd-ice1712
```

That enables the M-audio Delta 1010LT Analog Stereo device in my System Settings.
However, if I restart the computer, the device is grayed out again.

I already tried adding this line to /etc/modprobe.d/alsa-base.conf:
```
options snd-ice1712 model=delta1010lt
```

...but everytime I reboot, I still get the device grayed out.
I suppose there's a simple solution. Can anybody help me?

---

### Post by eamner on 2015-04-05
By the way, I forgot to mention that the issue is present in two different user accounts in my PC.

---

### Post by eamner on 2015-04-05
edited.

---

### Post by Yellow Pasque on 2015-04-06
Try adding snd-ice1712 to /etc/modules so the module will be loaded at startup.

---

### Post by eamner on 2015-04-06
> **Temüjin said:**
> Try adding snd-ice1712 to /etc/modules so the module will be loaded at startup.

Thanks! that did it.
My question: is this the 'proper' way to load these driver? I ask because  the only things I had there were:

```

lp
tun

```

Is this normal? I'm afraid to re-install the drivers of the soundcard again because that's what originally ruined my sound configuration (in addition to other things I messed with).

---

### Post by Yellow Pasque on 2015-04-06
Yes, the /etc/modules file is for modules/drivers that you want loaded at startup. It is equivalent to modprobe, but it runs at startup.
EDIT: Theoretically, the module should be loaded automatically. Perhaps you have a card with a different PCI ID? If you want to, give your info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by eamner on 2015-04-07
> **Temüjin said:**
> Yes, the /etc/modules file is for modules/drivers that you want loaded at startup. It is equivalent to modprobe, but it runs at startup.
EDIT: Theoretically, the module should be loaded automatically. Perhaps you have a card with a different PCI ID? If you want to, give your info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

Hi. This is the link to the output:

[http://www.alsa-project.org/db/?f=c8064fda7db4b8c8751fc36bcb264c93fb658bbd](http://www.alsa-project.org/db/?f=c8064fda7db4b8c8751fc36bcb264c93fb658bbd)

BTW my sound card is a m-audio delta 1010lt.
Thanks.

---

