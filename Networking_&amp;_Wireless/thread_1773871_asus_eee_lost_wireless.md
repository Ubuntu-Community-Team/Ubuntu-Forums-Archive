---
title: "asus eee lost wireless"
date: 2011-06-02
forum: Networking &amp; Wireless
---

### Post by mje1708 on 2011-06-02
Hi 

I just reinstalled Ubuntu 10.04 on my Asus eee PC1000. It has the RT2860 wireless chip in it (which I know causes problems. I managed to solve these when I had it installed previously).

Initially the wireless was working fine and then we lost internet connectivity for a moment - don't know why but it came back on in a few seconds. My daughter's laptop connected again with no problem but my Asus doesn't want to know. It now refuses to connect to any wireless - unsecured, WEP, WPA or anything. Wired internet still works fine.

Is there a way to see what is going on? I have no clue what to do.

Thanks
Mike

---

### Post by leclerc65 on 2011-06-02
Toggle the wireless on/off (Fn + F2) ?

---

### Post by mje1708 on 2011-06-03
Thanks - I tried that - blue light goes off and then when you toggle back on, blue light comes on again. But still no wireless.

In the meantime I did run 11.04 from the CD and the wireless does connect so obviously nothing wrong with my hardware.

---

### Post by m_duck on 2011-06-03
Can you post the output of ```
lsmod | grep rt
```
The only issue I know of with that card (I have an Eee 1000 as well) is that with newer kernels, both the rt2860sta driver and the proper rt2800 (or similar) get autoloaded and both try to take control of the card, which inevitably ends badly since the non-staging driver is/was broken.

Having said that I've not used any recent kernels so I'm not sure if the staging driver is still there but the above should clarify matters.

---

### Post by mje1708 on 2011-06-03
I reinstalled Ubuntu today and I seem now to have some wireless at least. However it will only connect to WEP networks (not WPA as most are nowadays) and the connection is far from reliable. Goes on and off and will not always reconnect,

Output from the command is -


rt2800pci               8495  0 
rt2800lib              23668  1 rt2800pci
rt2x00usb               9694  1 rt2800lib
rt2x00pci               5921  1 rt2800pci
rt2x00lib              26858  4 rt2800pci,rt2800lib,rt2x00usb,rt2x00pci
led_class               2864  1 rt2x00lib
mac80211              225459  3 rt2x00usb,rt2x00pci,rt2x00lib
cfg80211              144266  2 rt2x00lib,mac80211
compat_firmware_class     6554  1 rt2x00lib
eeprom_93cx6            1333  1 rt2800pci
rt2860sta             498817  1 
crc_ccitt               1339  2 rt2800pci,rt2860sta
agpgart                31724  2 drm,intel_agp
parport                32635  2 ppdev,lp

Hope this means something to you :)

Thanks for any help.

Mike

---

### Post by m_duck on 2011-06-04
It looks as though the rt2800 series of drivers are loading in addition to the rt2860sta driver. It used to be the case (and probably still is) that the rt2800 driver doesn't work properly, and since both modules are being loaded there is a conflict. It ***should*** just be a case of blacklisting the rt2800 stuff and rebooting so hopefully control should be given to the rt2860sta driver...

To that end open up /etc/modprobe.d/blacklist.conf as root and add the following to the bottom:
```
blacklist rt2800lib
blacklist rt2800pci
```
Blacklisting those two modules should be enough to stop all that lot loading.

The next step is to reboot and run the previously posted lsmod command again and then you should get a much smaller output, with the only 'rt2*' module being rt2860. Hopefully :p

At this point, you will hopefully be able to use your wireless connection as usual.

---

### Post by mje1708 on 2011-06-04
Thanks for your help. Strangely the wireless on my netbook today has been fine - nothing has changed. Also it is now letting me connect to wpa networks again ???? Anyway I did what you suggested and this is the output now -

rt2860sta             498817  1 
crc_ccitt               1339  1 rt2860sta
agpgart                31724  2 drm,intel_agp
parport                32635  2 ppdev,lp

No 2800 anymore so you were right.

Wireless still seems to be connecting fine so hopefully everything will continue like this.

Thanks

Mike

---

