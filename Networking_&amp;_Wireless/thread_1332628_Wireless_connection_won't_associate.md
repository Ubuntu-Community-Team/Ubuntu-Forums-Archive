---
title: "Wireless connection won't associate"
date: 2009-11-20
forum: Networking &amp; Wireless
---

### Post by Mustafa Ismail Mustafa on 2009-11-20
While not a total newbie, I'm still fresh to linux and this playing around is really helping out in figuring out how linux works; but I end up breaking things :oops:

basically, I destroyed my roaming wifi connection on my laptop.

Wireless chipset:
```
Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
        Subsystem: Intel Corporation Device 2741
        Flags: bus master, medium devsel, latency 32, IRQ 22
        Memory at bc007000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [dc] Power Management version 2
        Kernel driver in use: ipw2200
        Kernel modules: ipw2200
```

Interfaces file: (this is where I made the silliest mistake. I should have made a backup like any good programmer knows. Never again)
```

auto eth0
iface eth0 inet dhcp
wireless-essid linksys


iface eth1 inet dhcp

auto lo
iface lo inet loopback

```


Hardware listener output:
```

*-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       logical name: eth0
       version: 05
       serial: 00:16:6f:55:07:e3
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=32 link=no maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=unassociated

*-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes


```



This is on Jaunty and running iwlist scan scans properly and finds all wireless networks in range, but won't associate no matter what I try.

All the help is appreciated.

If there is anything else I should post, then please tell me.

One other question. Is it possible to give an alias to the connection? Meaning instead of referring to it as eth0 perhaps wlan0 ? Or perhaps aliases to different configurations (home vs work etc)

---

### Post by chili555 on 2009-11-20
First, let's restore *interfaces* to it's original configuration. Amend it to look like this:```
auto lo
iface lo inet loopback
```Next, let's address the issue of aliases:> instead of referring to it as eth0 perhaps wlan0 ? Or perhaps aliases to different configurations (home vs work etc)It is probably possible to give an alias of *eth0-home*, etc., but it is a fairly complex task. Network Manager is supposed to take care of all of that for you, however, as long as *interfaces* lists eth0, it won't do so. The driver, ipw2200, instructs the system to use the next available *eth*-whatever interface, I believe. It would therefor be quite difficult to rename it wlan0. I notice that there is no active ethernet device, so the next available eth interface was the first one, namely, eth0.

After a reboot, is Network Manager able to connect? What happens if it doesn't? Is your network encrypted, WEP, WPA or Klingon? Does Network Manager ask for the password or key?

---

### Post by Mustafa Ismail Mustafa on 2009-11-21
So sorry to have kept you hanging dude! Work got in the way and I didn't receive any email notification so I simply assumed that no one replied. I only found out because I came to bump the thread!

Your suggestion of "resetting" the interfaces file worked! I can connect no problem through the wireless connection, I cannot thank you enough!

Would you be able to point me to a really good reference for this? A lot of my work is network based and its important I know this stuff inside and out especially since I've decided to jump into the *nix pool leaving the MS world behind.

---

### Post by chili555 on 2009-11-21
> Would you be able to point me to a really good reference for this?Other than this forum and the 'Search' function, or trial and error, I don't know of one. Here are some resources: [https://wiki.ubuntu.com/CategoryNetworking](https://wiki.ubuntu.com/CategoryNetworking)

I would think there has to be a good book on Linux networking at any well stocked bookstore and at Amazon.com.

Good luck and post a new thread any time and we'll all be glad to help.

---

### Post by Mustafa Ismail Mustafa on 2009-11-21
Many thanks dude!

---

