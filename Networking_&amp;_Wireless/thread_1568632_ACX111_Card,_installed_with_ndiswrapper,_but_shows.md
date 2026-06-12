---
title: "ACX111 Card, installed with ndiswrapper, but shows as wired card"
date: 2010-09-05
forum: Networking &amp; Wireless
---

### Post by carlosjoan91 on 2010-09-05
Hi, i just instanlled lubuntu 10.04 to an old laptop i has laying around (AMD athlon 700 mhz, and 256 MB RAM if you&#341;e curious) and it runs pretty well actually, everything in the laptop was detected and working, except for a cardbus Airlink+ AWLC3025 card, that is based on the ACX111 chipset, i searched and found that the best option was installing with ndiswrapper, so I did (with the Win 2k drivers, since the win xp came as a setup.exe)

What i did with ndiswrapper was install the inf, and then run ndiswrappe -m, then -ma, and then -mi, then rebooted, found that the power led lit on the card, and gets detected in network manager, but as Wired Netword(Texas Instruments ACX111 54mbps Wireless Interface), on system profiler it does appear as a wireless interface. iwconfig says this:

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     no wireless extensions.
```

and, tried to connect manually as per a tutorial i found here, and after i ready everything, when i run wpa_supplicant...
it gets stuck on a loop of:

```
ioctl[SIOCGIWSCAN]: Operation not supported
ioctl[SIOCSIWSCAN]: Operation not supported
Failed to initiate AP scan.
```

Does anyone have any idea if there&#347; a way to get this card working? Thanks

Almost forgot, this is the output of ndiswrapper -l

```
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
tnet1130 : driver installed
	device (104C:9066) present
```

Thanks in advance

---

