---
title: "Wi-fi not working on Compaq C500 laptop"
date: 2010-10-05
forum: Networking &amp; Wireless
---

### Post by gf97 on 2010-10-05
I have a Compaq C500 laptop and I just put Ubuntu 10.04 on yesterday. I can't seem to get the wi-fi to run. It is a Broadcom card with the b43 driver. If I run dmesg it says
```

b43 ssb0:0: firmware: requesting b43/ucode5.fw
b43 ssb0:0: firmware: requesting b43-open/ucode5.fw
b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.

```
It repeats this twice. I don't want to update the firmware if I don't have too but I don't know what else to do.


sudo ifconfig wlan0 up gives me
```

SIOCSIFFLAGS: No such file or directory

```

I couldn't find anything on google about what to do.

---

