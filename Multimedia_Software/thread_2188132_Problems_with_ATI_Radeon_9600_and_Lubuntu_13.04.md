---
title: "Problems with ATI Radeon 9600 and Lubuntu 13.04"
date: 2013-11-15
forum: Multimedia Software
---

### Post by Rooster2000 on 2013-11-15
I'm having a bit strange problem with my ATI Radeon 9600 graphics card. The fan started to make noise, so I replaced it with new one which I bought from eBay. Now, I don't know if this is some nocebo effect or what, but after I installed this new fan, my eyes started to get tired after watching the screen for longer than, say 30-60 minutes. If I change the old fan back, this problem doesn't occur. Actually, the same happened when I tried my old Voodoo 3dfx.

I was thinking if there is something wrong with this new fan (which cost $0.99) and it cannot keep the GPU cool enough, but I cannot see any changes or errors in the picture. The screen resolution and refresh rate are also the same as before. I tried to find a way to see GPU temp, but it seems that I should have a driver from ATI/AMD installed. According to [this]("http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Installing_Proprietary_Drivers_a.k.a._Catalyst.2Ffglrx") page Radeon 9600 is no longer supported by latest drivers, and therefore I should use either use older Lubuntu distro (8.04?) with older AMD/ATI drivers or use open-source drivers (which don't allow reading GPU temperature?). Is this information still accurate? Is there any way to get the GPU temperature from my graphics card in my current Lubuntu 13.04 without using aticonfig?

My monitor is HP Pavillion f1904.

---

### Post by Yellow Pasque on 2013-11-16
If the open source kernel module supports temp reading, you should be able to get it by installing lm-sensors and running:
```
sensors
```

---

### Post by Rooster2000 on 2013-11-16
Unfortunately lm-sensors can't find it.

```

~$sensors

via686a-isa-6000
Adapter: ISA adapter
Vcore:        +1.67 V  (min =  +0.06 V, max =  +3.10 V)
in1:          +0.25 V  (min =  +0.06 V, max =  +3.10 V)
+3.3V:        +3.31 V  (min =  +2.98 V, max =  +3.63 V)
+5V:          +4.95 V  (min =  +4.51 V, max =  +5.50 V)
+12V:        +11.95 V  (min = +10.81 V, max = +13.20 V)
fan1:        2896 RPM  (min =    0 RPM, div = 2)
fan2:           0 RPM  (min =    0 RPM, div = 2)
temp1:        +57.8°C  (high = +146.2°C, hyst = -70.9°C)
temp2:        +31.9°C  (high = +146.2°C, hyst = -70.9°C)
temp3:        +25.1°C  (high = +146.2°C, hyst = +146.2°C)

```

Also, when I run sensors-detect it does find my graphics card, but doesn't find any hardware sensors there.

---

### Post by Rooster2000 on 2014-03-30
I replaced my motherboard which had some leaked capacitors near graphics card (see [this]("http://ubuntuforums.org/showthread.php?t=2192181") thread). I also replaced the fan and heat sink of my graphics card by a larger heat sink without a fan. After these changes, I was able to get used to the display, although my eyes were a bit tired in the beginning. Cannot really say if this was a hardware, software or user-based problem but it seems that at the moment my eyes can cope with the picture I have on my display.

---

