---
title: "ioctl(SIOCSIFFLAGS) failed: Unknown error 132: Aircrack"
date: 2009-10-16
forum: Networking &amp; Wireless
---

### Post by linuxus95 on 2009-10-16
I am trying to test my wireless AP with aircrack-ng, and I am using the beta version of Karmic Koala. I have a dell laptot with a 1390 Wireless Network Card and I use the B43 driver. According to the aircrack-ng website, I do not need to apply any patches to the driver, but just extract the firmware. Whenever I try to run any aircrack related commands from terminal (such as "sudo airomon-ng start wlan0") I get the error message ioctl(SIOCSIFFLAGS) failed: Unknown error 132. I think that this is probably related to an incorrect firmware extracted to the lib/firmware directory. I have no idea how to solve this, though, so any help would be greatly appreciated. Thanks a lot.

---

### Post by irvotheturbo on 2009-11-01
Same problem here. I upgraded from Jaunty (2.6.28-15 kernel) and now airmon-ng gives me the following error:
```
$ sudo airmon-ng start wlan0
Interface	Chipset		Driver
wlan0		Broadcom	b43 - [phy0]SIOCSIFFLAGS: Unknown error 132
				(monitor mode enabled on mon0)
```

I removed b43-fwcutter (purge) and reinstalled it, rebooted, but still the same message. Wireless works perfectly normal though. 
Using a Broadcom 4318 on my Acer Aspire 5003.


Seems like I made a very stupid mistake... On the old kernel it didn't matter if you had the wireless switch turned off. Airmon-ng would start normally, but Kismet (or other progs) would not receive any packets. This is where I would normally turn it on. Now it just gives you "Unknown error 132".
After turning the wlan switch on it functions normally and Airmon-ng / Kismet start like they would before.

---

