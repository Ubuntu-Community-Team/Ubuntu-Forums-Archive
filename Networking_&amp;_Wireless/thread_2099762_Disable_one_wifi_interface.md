---
title: "Disable one wifi interface?"
date: 2012-12-30
forum: Networking &amp; Wireless
---

### Post by mr_si on 2012-12-30
I've been without broadband over Christmas. }-(. The temporary fix is to stick a wifi dongle out of the window via a long USB cable and log onto my neighbour's wifi. 

UB doesn't seem to appreciate having multiple wireless cards though and always tries to connect via my laptop's built in device - any idea how I can disable the internal one so leaving it to use the usb dongle? 

I've just got a virgin install of Kubuntu 12.x.

Thanks

---

### Post by steeldriver on 2012-12-30
What's worked for me in the past is to specify it as an 'unmanaged device' in the NetworkManager.conf file HOWEVER I know other people have been unsuccessful with that method

The more brute force approach is to blacklist the driver - obviously that's only if the new dongle doesn't use the same driver as the old one ;)

Both methods described here

[http://ubuntuforums.org/showthread.php?t=2056652&highlight=unmanaged-devices](http://ubuntuforums.org/showthread.php?t=2056652&highlight=unmanaged-devices)

FWIW I seem to remember the MAC address in the unmanaged-devices line being case sensitive

---

### Post by matt_symes on 2012-12-30
Hi 

Look in the BIOS and see if there is an option to disable the internal wireless card.

Most Bios's have that option.

Kind regards

---

### Post by mr_si on 2012-12-30
> **matt_symes said:**
> Hi 

Look in the BIOS and see if there is an option to disable the internal wireless card.


Yeah but it disables all wifi devices

---

### Post by haqking on 2012-12-30
```
ifconfig <wlanx> down
```

Where x is the 0 or 1 or whatever pertaining to the wifi you want to disable

---

### Post by mr_si on 2012-12-30
> **steeldriver said:**
> What's worked for me in the past is to specify it as an 'unmanaged device' in the NetworkManager.conf file HOWEVER I know other people have been unsuccessful with that method


Well I get a new dialog up whenever I try to connect the USB dongle - 'Secrets for [network name] - KDE Daemon' asking for a password. If this is the wifi key why doesn't it say so? and it keeps failing to connect..

---

### Post by mr_si on 2012-12-30
> **haqking said:**
> ```
ifconfig <wlanx> down
```

Where x is the 0 or 1 or whatever pertaining to the wifi you want to disable

Simple :-) Fails :-( I get a connection alright but the built in browser (or ping) can't do a DNS lookup - is it trying to use the disabled network?

---

### Post by matt_symes on 2012-12-31
Hi

Disabling the internal network card in  the BIOS should have no effect on any USB network adaptor.

Haqking's suggestion would have also disabled the internal wireless card only, assuming you selected the correct interface.

It seems to me your problem is not related to the internal wireless card but, maybe, to the USB wireless dongle.

Open a terminal and type (with the dongle connected)

```
lspci
```

```
ifconfig
```

```
iwconfig
```

```
ping 8.8.8.8
```

```
nslookup www.google.com
```

Please post the results of these commands back here.

Kind regards

---

### Post by Hadaka on 2012-12-31
Hi, you can also edit your wireless connections and
uncheck connect automatically, then simply use what ever
connection you want when the menu comes up that wireless
connections have been found.
@matt_symes, depending on how you disable wireless in bios it
can kill any wireless ....atleast in a dell.
one option disables any ability to use any wireless, the disable
pci card,will kill just the internal card. The only option marked
"Wireless" is the one that disables any form of wireless.

---

