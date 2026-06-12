---
title: "Problem with DHCP connection"
date: 2009-09-25
forum: Networking &amp; Wireless
---

### Post by Valerys on 2009-09-25
Today I received the free CD with Ubuntu 9.04 and installed it from inside Windows. While the issue I had in the past with my videocard (x1650pro) that didn't work at all was fixed, my internet connection is still not working.
Ubuntu makes a default connection named "Auto eth0" based on DHCP, but after trying for 20-30s to obtain the address it fails. I am not quite sure what should I do so I ask for your help (with 8.04 the connection wasn't even recognized as DHCP and didn't work at all, but this time it is recognized but not working). In tray it says Wired Connection Offline.

---

### Post by Iowan on 2009-09-25
I suppose the first question would be whether you are trying wired or wireless. (One might assume wired from the eth0... but my wireless is defined as eth1) [This]("http://ubuntuforums.org/showthread.php?t=1156441") fixed my wired DHCP problem... but you might also have a driver problem.  What are results of **lshw -C network**?

---

### Post by Valerys on 2009-09-26
It's wired. It is based on an Nforce 3 chipset. It works well under Windows and OpenSUSE 11.0, which I removed because of Ubuntu.

I tried with the # in front rfc3442 and deleting the reference in request, but still the same.

> valerys@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 6a:51:40:2f:a6:ad
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes



---

### Post by Iowan on 2009-09-26
Eth0 is ominously absent from the hardware list. I presume that points to drivers (which I can't help with).

---

