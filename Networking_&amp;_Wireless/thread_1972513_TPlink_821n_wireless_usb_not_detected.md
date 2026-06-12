---
title: "TPlink 821n wireless usb not detected?"
date: 2012-05-03
forum: Networking &amp; Wireless
---

### Post by herrNilsson on 2012-05-03
Hello,

I have an old thinkpad t42p with integrated wifi, which is terribly slow. So I bought a tplink 821n usb adapter to speed up the wireless network. The operating system is 10.04 lucid. 

I first disabled the internal wireless card in the bios to avoid conflicting drivers being loaded. I verified that the driver for the onboard card was not being loaded using lsmod | grep ipw2100 which did not return anything. 

When I plug the device, I can see it with lsusb, **but not with** lshw. What is the reason it shows up only when doing lsusb and not in lshw?

Also, the relevant driver, ar9170usb, did not autoload. When I load the driver manually with modprobe ar9170usb I get no error, and then doing lsmod | grep ar9170usb shows the driver is loaded. But the device still does not show up when using lshw. 

The hardware itself works, I tested in in windows. There is a green led on the device which is lit if I boot to windows and connect to a network. That led has never been lit when booted in ubuntu. 

Any ideas on what the problem might be are greatly appreciated.

Thanks in advance

---

### Post by chili555 on 2012-05-03
Very good so far! Let's look at modinfo:```
$ modinfo ar9170usb
filename:       /lib/modules/2.6.32-40-generic/kernel/drivers/net/wireless/ath/ar9170/ar9170usb.ko
[COLOR="Red"]firmware:       ar9170-2.fw
firmware:       ar9170-1.fw
firmware:       ar9170.fw[/COLOR]
description:    Atheros AR9170 802.11n USB wireless
license:        GPL

```Do you have the firmware?```
ls /lib/firmware | grep 9170
```What does dmesg say?```
dmesg | grep 9170
```> What is the reason it shows up only when doing lsusb and not in lshw?For some reason, USB devices usually don't show up until the driver, firmware and hardware marry and create a wireless interface, such as wlan0. Even then, the details are scant.

Are you quite sure that's the correct driver for the device? Mind if we peek at:```
lsusb
```Thanks.

---

### Post by herrNilsson on 2012-05-04
Thanks for the response. The output from the requested commands is pasted below. 

**modinfo ar9170usb**
```

modinfo ar9170usb
filename:       /lib/modules/2.6.32-41-generic/kernel/drivers/net/wireless/ath/ar9170/ar9170usb.ko
firmware:       ar9170-2.fw
firmware:       ar9170-1.fw
firmware:       ar9170.fw
description:    Atheros AR9170 802.11n USB wireless
license:        GPL
author:         Christian Lamparter <chunkeey@web.de>
author:         Johannes Berg <johannes@sipsolutions.net>
srcversion:     C7351BF56F6F8F0130FE9BA
alias:          usb:v057Cp8402d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v057Cp8401d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp093Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019p5304d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApF522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0026d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0023d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p3417d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1435p0326d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1435p0804d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0ACEp1221d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0846p9001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0846p9010d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0846p9040d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3A09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C10d*dc*dsc*dp*ic*isc*ip*
alias:          usb:vCACEp0300d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p1011d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p1010d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p1002d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p1001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p9170d*dc*dsc*dp*ic*isc*ip*
depends:        mac80211,led-class,ath,cfg80211
vermagic:       2.6.32-41-generic SMP mod_unload modversions 586 
parm:           nohwcrypt:Disable hardware encryption. (bool)
parm:           ht:enable MPDU aggregation. (bool)

```

**ls /lib/firmware | grep 9170**
```
ls /lib/firmware | grep 9170
ar9170-1.fw
ar9170-2.fw
ar9170.fw

```


**dmesg | grep 9170**
```

dmesg | grep 9170
[   30.863437] usbcore: registered new interface driver ar9170usb

```

**lsusb**
```

 lsusb
Bus 004 Device 002: ID 1668:2441 Actiontec Electronics, Inc. [hex] BMDC-2 IBM Bluetooth III w.56k
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 001 Device 006: ID 0cf3:7015 Atheros Communications, Inc.** 
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

As for the driver I guess I am kind of sure, according to all the sources I have found on this forum and elsewhere ar9170usb is the appropriate driver for TL-WN821N. Thanks for helping!

Best Regards
Nilsson

---

### Post by chili555 on 2012-05-04
> according to all the sources I have found on this forum and elsewhere ar9170usb is the appropriate driver for TL-WN821N.I'm not quite sure I agree. [https://www.google.com/search?q=0cf3%3A7015&ie=utf-8&oe=utf-8&client=ubuntu&channel=fs](https://www.google.com/search?q=0cf3%3A7015&ie=utf-8&oe=utf-8&client=ubuntu&channel=fs)

It appears that the driver is ath9k_htc. On my computer:```
chili@LAPTOP60:~$ modinfo ath9k_htc | grep 7015
alias:          usb:v[COLOR="Red"]0CF3[/COLOR]p[COLOR="Red"]7015[/COLOR]d*dc*dsc*dp*ic*isc*ip*
```On your 10.04 install, you don't have the more recently developed ath9k_htc.

We could try to find a driver to download and compile, a slightly complex process, or you could upgrade to 12.04, or we could try the Windows XP .inf and .sys files and ndiswrapper; also a slightly complex process. What is your preference? I will be very happy to help you in any case.

---

### Post by zoades on 2012-05-28
i am completely new to ubuntu, but i also had trouble installing the tl-wn821n. 

first i downloaded the 32 bit windows xp driver from:
[http://www.tp-link.com/en/support/download/?model=TL-WN821N](http://www.tp-link.com/en/support/download/?model=TL-WN821N) 

before you do that, you have to look up which version is your dongle by looking at the label on the bottom side of the stick.

in my  mint 13 distribution installation was possible via "control center" and "windows wireless drivers". but before installation was finished, i had to install "ndiswrapper". how i did that, i cannot remember.

hope, i am not in the wrong forum.

---

### Post by chili555 on 2012-05-28
> hope, i am not in the wrong forum.We don't know yet. Do you have a question or a problem? Are you asking how to install Windows wireless drivers? Are you saying you tried to do it and it failed...or...what? Please insert the device, open a terminal and run and post:```
lsusb
```

---

### Post by vlaar on 2012-05-29
Just as a heads up, even if you use ath9k_htc the green light will not turn on. Currently no support for it.

---

