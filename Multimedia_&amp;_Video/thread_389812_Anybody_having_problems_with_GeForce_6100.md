---
title: "Anybody having problems with GeForce 6100?"
date: 2007-03-21
forum: Multimedia &amp; Video
---

### Post by hise0001 on 2007-03-21
Hi,

I just upgraded my motherboard and cpu and purchased a Biostar socket 939 with the integrated Nvidia Geforce 6100.

The standard nv driver was painfully slow.  I followed the nvidia howto ([https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia?highlight=%28nvidia%29](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia?highlight=%28nvidia%29)) and installed the universal driver and it worked like a charm.

However, I have random screen freezes where the reset button is the only way out.  It happens a lot more frequently when beryl is running, so I've cut out my beryl use for now.  Either way, though, I still experience the same screen freezes.

Funny, I was looking forward to upgrading my video technology as I was using a Geforce2 before that required the legacy driver..... It was rock solid even with beryl... just didn't get all the effects.

Any feedback would be greatly appreciated.

--Hise

---

### Post by chewearn on 2007-03-21
Couple of things you could try:
1. Install nvidia-settings
```
sudo aptitude install nvidia-settings
```

Run it from the terminal:
```
nvidia-settings
```

From this, you can check how much memory the graphics is using.  If it is low (like 128MB) you can try increasing it by going into the BIOS and increase video shared memory.  I believed the max is 256MB.

2. DId you have dual boot to WinXP?  If so, does it have the same problem there?  If yes, then it could be hardware problem: return to manufacturer for replacement/repair).

3. Remove the stable nvidia driver you have installed, then use the Envy script to install latest beta driver.
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

