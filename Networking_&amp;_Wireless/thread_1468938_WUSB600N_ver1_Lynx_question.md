---
title: "WUSB600N ver1 Lynx question"
date: 2010-05-01
forum: Networking &amp; Wireless
---

### Post by Lithaerien on 2010-05-01
I was wondering if anyone figured out the WUSB600N ver1 with Ubuntu 10.4 yet. It's the chipset rt2870sta which works perfectly on Ubuntu 9.10 after blacklisting the other RT2x modules but following the same steps as I would 9.10 on the new release of Ubuntu won't allow me to connect via wifi at all.

I went back to 9.10 for now but was hoping this would be resolved soon.

---

### Post by Lithaerien on 2010-05-08
I still can't seem to get wireless to work with this USB stick. I've followed instructions to compile the ralink drivers from source after changing the NATIVE_WPA and WPA Supplicant in the config.mk file to "y" (yes).

I need some help here if anyone is willing. I did everything from installing the source into /lib/modules/`uname -r`..../net/wireless/rt2870sta.ko to moving it to the staging/rt2870/rt2870sta.ko directory where the kernel loads by default.

Before I moved the file to the staging directory I found that whenever I tried to remove the module and reload it using insmod <long directory string>/net/wireless/rt2870sta.ko it still loaded the staging module according to:
```
modinfo rt2870sta
```

On another note I have no problem logging into WEP using the default module... it's WPA that's giving me problems with Ubuntu 10.4

---

### Post by Dev0 on 2010-05-21
Hey Lithaerien

Take a look at the guide in this thread.  I had the same problem with WPA security on the rt2870 chipset and found a way to compile a working driver.  Let me know if it works for you.

[http://ubuntuforums.org/showthread.php?t=1487397](http://ubuntuforums.org/showthread.php?t=1487397)

---

