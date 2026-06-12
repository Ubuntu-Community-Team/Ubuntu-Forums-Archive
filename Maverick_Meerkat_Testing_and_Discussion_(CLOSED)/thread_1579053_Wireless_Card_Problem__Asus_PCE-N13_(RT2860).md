---
title: "Wireless Card Problem:  Asus PCE-N13 (RT2860)"
date: 2010-09-21
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by wadam on 2010-09-21
Hi everybody.  I just did a wipe and install, going from Lucid to Maverick beta.  For the most part, I see a lot of improvement.  But I am experiencing one significant problem.  The OS seems to recognise that I have an Asus PCE-N13 wireless card installed.  It seems to be loading the appropriate kernel modules to make it function.  But the NetworkManager applet refuses to bring up a list of available wireless networks.  And when I attempt to type in my wireless network's SSID, the connection fails almost immediately.

Any thoughts on how to solve this?

Thanks a lot.

---

### Post by cariboo on 2010-09-21
Can you post the output of:

```
sudo lshw -C network
```

so we can make sure the wireless device is detected properly and the driver loaded.

---

### Post by wadam on 2010-09-21
Thanks so much.  There is the problem:

```
  *-network DISABLED
       description: Wireless interface
       product: RT2860
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 00
       serial: e0:cb:4e:86:2b:fb
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=2.6.35-22-generic firmware=N/A latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:fbdf0000-fbdfffff

```

But how do I enable the interface?

---

### Post by wadam on 2010-09-21
As an addendum to the last post:  I just used ifconfig to try to enable the network interface, and got the following error message:

> SIOCSIFFLAGS: Device or resource busy

I have no idea what to make of that.

---

### Post by wadam on 2010-09-22
Any further thoughts?

---

### Post by 65 mustang on 2010-10-03
Did you file a bug report on launchpad?
[https://launchpad.net/ubuntu]("https://launchpad.net/ubuntu")

---

### Post by 65 mustang on 2010-10-03
Filed a bug report:  [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/654104](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/654104)

Might want to click that it affects you also.  :(

---

### Post by fooman on 2010-10-03
> **wadam said:**
> Thanks so much.  There is the problem:

```
  *-network DISABLED
       description: Wireless interface
       product: RT2860
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 00
       serial: e0:cb:4e:86:2b:fb
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=2.6.35-22-generic firmware=N/A latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:fbdf0000-fbdfffff

```But how do I enable the interface?

have you tried right-clicking on the network icon in the panel....and putting a check next to "enable wireless"?

---

### Post by Optln on 2010-10-03
I have an EasyNote laptop which has an RT2860 and having this problem too. Enable Wireless is ticked by the way.

---

### Post by wadam on 2010-10-03
> **fooman said:**
> have you tried right-clicking on the network icon in the panel....and putting a check next to "enable wireless"?

I have tried that.  It seems that there is some sort of conflict amongst the kernel modules that breaks support.  I have since fixed it, but I don't remember exactly how.  If you search for PCE-N13 in the Maverick forum, there is an earlier thread that addresses the problem.

---

### Post by Mokkan on 2010-10-03
I had the same problem with this card, but I finally figured it out. Apparently the rt2800/rt2x00 modules are problematic (not mature?). To fix this problem, all I needed to do was blacklist them in /etc/modprobe.d/blacklist.conf

```
blacklist rt2800pci
blacklist rt2800usb
blacklist rt2x00lib
blacklist rt2x00pci
blacklist rt2x00usb
blacklist rt2x00lib
```

I hope this information is useful.

---

### Post by 65 mustang on 2010-10-03
Ok, will have to try that fix.  The card maxed out at 54mbs in 10.04 its like it would only use the G mode.  Do you get N rates in 10.10?

---

### Post by Mokkan on 2010-10-03
I only get 54mbps/G mode, as well.

---

### Post by cariboo on 2010-10-04
Open a terminal and type:

```
sudo iwconfig <device> essid "<essid name>"
```

where <device> = whatever your device is wlan0, eth0, etc. <essid-name> = the name you gave your ap, router, etc.

If it connects, you should see it trying to acquire an ip address.

---

### Post by dhimmels on 2010-10-06
This method worked for me on the pre-release 64 bit version of ubuntu 10.10. I didn't include the last blacklist line because it is a duplicated of the second line. Thanks!

> **Mokkan said:**
> I had the same problem with this card, but I finally figured it out. Apparently the rt2800/rt2x00 modules are problematic (not mature?). To fix this problem, all I needed to do was blacklist them in /etc/modprobe.d/blacklist.conf

```
blacklist rt2800pci
blacklist rt2800usb
blacklist rt2x00lib
blacklist rt2x00pci
blacklist rt2x00usb
blacklist rt2x00lib
```

I hope this information is useful.

---

### Post by scokem on 2010-10-07
The issues with the rt2860 have already been covered and we already had a bug report:

[http://ubuntuforums.org/showthread.php?t=1586613](http://ubuntuforums.org/showthread.php?t=1586613)

Blacklisting didn't work for me so I downloaded and built the module from Ralink's site and it works flawlessly including n.

---

