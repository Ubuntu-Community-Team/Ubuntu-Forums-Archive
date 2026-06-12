---
title: "Auto Eth0 disconnecting"
date: 2010-11-13
forum: Networking &amp; Wireless
---

### Post by sm3 on 2010-11-13
Whenever I try to connect to my only available wired network (Auto Eth0, it tries to connect for a few minutes then disconnects. 

I did not have this problem with Ubuntu version 9.04 (Which is the last time I had Ubuntu on this computer... I got rid of that when I got Windows seven, and then just today put Ubuntu 10.10 64 bit on it.)

I am running it on an Acer Aspire m5100. It is connected to a Linksys WRT54G Router which connects to a ambiguous modem that I think is functioning in that mode where it does nothing but pass signals through.

I've made sure to get all my modem stuff and Ubuntu settings seeming like they should work. When I unplug the cable to my modem, Auto Eth0 stops appearing on my available networks list... when I try to connect to it, it just keeps loading for a bit and then tells me I'm disconnected.

---

### Post by uncaspi on 2010-11-13
Downgrade to 10.04. Ubuntu 10.10 is very buggy.

---

### Post by sm3 on 2010-11-13
How do I do that? and once I do that, I should be able to re-upgrade with Ethernet settings and drivers in tact, right?

---

### Post by uncaspi on 2010-11-13
I don't know how to do it I know that others have done it.

---

### Post by sm3 on 2010-11-14
Was really hoping to get this resolved in a way that didn't involve me resorting back to a older release.... anyone have any ideas? if not, I will probably end up googling the older release... Installing the older version over the new version shouldn't hurt my Windows 7 Hard-drive space, should it?

---

### Post by dineshs on 2010-11-14
Can you post the outputs of ```
sudo lshw -C network
```and```
sudo gedit /etc/network/interfaces
```

---

### Post by sm3 on 2010-11-14
This is what I get from sudo lshw -C network: ```
*-network               
       description: Ethernet interface
       product: 88E8056 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 20
       serial: 00:1c:25:2e:a4:06
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 duplex=full firmware=N/A latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:41 memory:fdcfc000-fdcfffff ioport:ee00(size=256) memory:fdf00000-fdf1ffff

```

And when I use the sudo gedit /etc/network/interfaces terminal face, it opens a text file (Who would of thought that 'gedit' meant it was something that gedit opened?) that says this: 
```
auto lo
iface lo inet loopback
```

In case I missed some details, here is a screenshot... [http://i55.tinypic.com/ezpytv.jpg](http://i55.tinypic.com/ezpytv.jpg)

---

### Post by dineshs on 2010-11-14
lshw says> 88E8056 PCI-E Gigabit Ethernet Controller           
and the driver loaded> driver=sky2
Saw a thread (Not sure it can help)
[http://ubuntuforums.org/showthread.php?t=596196](http://ubuntuforums.org/showthread.php?t=596196)

---

### Post by sm3 on 2010-11-14
I tried the fix that that forum claims to have encountered (going to Marvell: Support and downloading the appropriate driver.)

I went to [http://www.marvell.com/support.html](http://www.marvell.com/support.html) and searched by the id number thingy, and got a list of drivers. I downloaded the one that said "Linux Kernel 2.4.20 and Higher" ... and when I tried to run it, I got an error.... It told me that in the "functions" document, "(" on line 44 was unexpected.

---

### Post by mathia on 2010-12-04
Hi,
Please install the following driver as follows:
[http://www.marvell.com/support.html](http://www.marvell.com/support.html)  -> "88E8056 Search" -> Kernel 2.6.x Linux Driver Install Package for Yukon Devices    Linux 2.6 - Fedora v10.85.9.3

 $ sudo bash ./install.sh

and let me know if it works.

have a lot of fun ...:razz:

---

### Post by Geremia on 2011-04-24
> **mathia said:**
> Hi,
Please install the following driver as follows:
[http://www.marvell.com/support.html](http://www.marvell.com/support.html)  -> "88E8056 Search" -> Kernel 2.6.x Linux Driver Install Package for Yukon Devices    Linux 2.6 - Fedora v10.85.9.3

 $ sudo bash ./install.sh

and let me know if it works.

have a lot of fun ...:razz:It didn't appear to work for me. I think there might be a hardware issue with my internal ethernet card, though (same card as the OP's). When I plug it in to a router, the light on the router never turns on indicating it is connected. I had a similar problem when Mac OS X was on my MacBook, and it appeared that it requires a very specific, high-quality ethernet cable? Thanks

---

### Post by mathia on 2011-04-27
Geremia,
which kernel is in use?
$ sudo uname -a

There is a newer linux 2.6 driver 10.87.3.3 on marvell web. Lets give it a try and let me know about the results.

Thanks.

---

### Post by Geremia on 2011-04-27
> **mathia said:**
> Geremia,
which kernel is in use?
$ sudo uname -a

There is a newer linux 2.6 driver 10.87.3.3 on marvell web. Lets give it a try and let me know about the results.

Thanks.
```
Linux geremia 2.6.35-28-generic #50-Ubuntu SMP Fri Mar 18 18:42:20 UTC 2011 x86_64 GNU/Linux

```Also, I installed the recent Marvell driver for Linux 2.6, but it didn't fix anything. I am beginning to think it's a hardware issue because it worked intermittently even with Mac OS X.

Thanks

---

### Post by Geremia on 2011-04-29
> **mathia said:**
> Geremia,
which kernel is in use?
$ sudo uname -a

There is a newer linux 2.6 driver 10.87.3.3 on marvell web. Lets give it a try and let me know about the results.

Thanks.I'll let you know if Ubuntu 11.04 fixes things. My MacBook's updating right now.

---

