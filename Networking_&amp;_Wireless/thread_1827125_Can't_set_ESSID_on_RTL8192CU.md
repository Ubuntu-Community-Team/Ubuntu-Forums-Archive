---
title: "Can't set ESSID on RTL8192CU"
date: 2011-08-17
forum: Networking &amp; Wireless
---

### Post by Grimm Spector on 2011-08-17
I'm trying to manually setup my wireless USB key, I've compiled the driver using the script, no errors after a small fix, I can see the wlan0 device on iwconfig, however I cannot issue settings to it. I get the message:

```

Error for wireless request "Set ESSID" (8B1A) :
      SET failed on device wlan0 ; Operation not permitted.

```

I get the same error message no matter what properties I try to manually set, and of course the built in wireless/ethernet panel doesn't DO anything when I set it all up. I've disabled it for now.

Any help would be greatly appreciated, I have no way of wiring this system currently I have to do it over wireless and it's so far been a ridiculous headache!

---

### Post by praseodym on 2011-08-21
This driver lacks the firmware, but it is there, just inside of the wrong folder:

```
sudo mkdir /lib/firmware/RTL8192SU
sudo cp /lib/firmware/RTL8192SE/rtl8192sfw.bin /lib/firmware/RTL8192SU/  
sudo modprobe -rf r8192s_usb
sudo modprobe r8192s_usb
```

---

