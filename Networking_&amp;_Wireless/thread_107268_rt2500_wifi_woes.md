---
title: "rt2500 wifi woes"
date: 2005-12-22
forum: Networking &amp; Wireless
---

### Post by philroche on 2005-12-22
Hi posting virgin here :)

I am pulling my hair out trying to get my Asus WL-1676 USB wireless adapter working on 5.10 on my ibook. 

I have followed the instructions @

[https://wiki.ubuntu.com/Rt2500WirelessCardsHowTo/DriverAndRaconfig](https://wiki.ubuntu.com/Rt2500WirelessCardsHowTo/DriverAndRaconfig)

and 

[https://wiki.ubuntu.com/Rt2500WirelessCardsHowTo](https://wiki.ubuntu.com/Rt2500WirelessCardsHowTo)

but the interface does not come up.

My lsmod output does contain
[INDENT]```
rt2500                202388  0
```[/INDENT]

My Modinfo 2500 outputs
[INDENT]
```
filename:       /lib/modules/2.6.12-10-powerpc/kernel/drivers/net/wireless/rt2500.ko
license:        GPL
description:    Ralink RT2500 802.11g WLAN driver 1.1.0 BETA3 2005/07/31
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     ACAEA7EAF913917E5BFBF11
alias:          pci:v00001814d00000201sv*sd*bc*sc*i*
depends:
vermagic:       2.6.12-10-powerpc gcc-3.4
parm:           debug:Enable level: accepted values: 1 to switch debug on, 0 to switch debug off. (i)
parm:           ifname:Network device name (default ra%d) (s)

```
[/INDENT]

ifconfig ra0 up returns

[INDENT]```
ra0: ERROR while getting interface flags: No such device
```[/INDENT]

iwconfig returns
[INDENT]```
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.
```[/INDENT]

ifconfig returns
[INDENT]```
eth0      Link encap:Ethernet  HWaddr 00:0A:95:BB:CE:6E
          inet addr:192.168.0.25  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::20a:95ff:febb:ce6e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2832 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2404 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2187110 (2.0 MiB)  TX bytes:252509 (246.5 KiB)
          Interrupt:41 Base address:0x1000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:25755 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25755 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2332374 (2.2 MiB)  TX bytes:2332374 (2.2 MiB)
```[/INDENT]


I hope this is enough information to give advice..

Cheers, Phil

---

### Post by robotgeek on 2005-12-22
```

echo "alias ra0 rt2500" | sudo tee /etc/modprobe.d/rt2500

```
Did you do this?

---

### Post by Lambert on 2005-12-22
Somebody correct me if I'm wrong but I believe that rt2500 driver is for pci/pcmcia devices. You have a usb device so you need the rt2570 driver.

---

### Post by robotgeek on 2005-12-22
[QUOTE=Lambert]Somebody correct me if I'm wrong but I believe that rt2500 driver is for pci/pcmcia devices. You have a usb device so you need the rt2570 driver.[/QUOTE]
Whoops, yes he needs the rt2570 driver. Sorry!

---

### Post by philroche on 2005-12-23
Yes I did add the alias,

I'll try the rt2570 driver now cheers

---

### Post by philroche on 2005-12-23
I have installed the rt2570 cvs driver and it installed fine and appears in the network admin tool but when I try and configure it or try and ifup it, The machines hangs and I need to reboot. I used iwconfig and passed in my ssid.

Do I need to add anything to /etc/network/interfaces regarding dhcp etc or should I try the non CVS version.

Cheers,

Phil

---

### Post by Lambert on 2005-12-23
It's still a beta driver so there may be bugs not worked out yet.

1. Make sure there are no other ralink modules loaded like the rt2500 before bringing up the interface.
2. When you use iwconfig it just passes the parameters to the interfaces file so there's nothing more to add.
3. In the source files there should be a file TESTING. this will show you how to turn on debugging features for the driver and log them. You may want to turn these on and then ask for help on the serialmonkey site.
4. You can try the beta driver instead of the cvs version to see if it works.
5. I looked on the compatability section of serialmonkey and didn't see your device listed so it's possible it won't work with the driver. report the bugs you find so they can improve the driver and make it work with your device.

And lastly, if all else felse, look into ndiswrapper with the windows drivers if you can't get native driver to work.

---

