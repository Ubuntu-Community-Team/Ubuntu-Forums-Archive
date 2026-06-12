---
title: "Intrepid Wireless Issues"
date: 2008-12-20
forum: Networking &amp; Wireless
---

### Post by Jimmy9pints on 2008-12-20
I have intrepid installed on 5 laptops (2 of my own and 3 of friends and family) and all of them have wireless and wired networking issues. 

Often it is fixed by going restarting several times or in the case of the dual booters, going into Windows, using the internet for a while, logging back out and going into Ubuntu. 

The laptops are all different ages and brands, so I don't see anything in common really. 

Often, the network manager icon doesn't even appear. 

Right now, my little laptop won't connect to the internet. Restarting doesn't help. 

```
ping google.com
``` gives "unknown host"
```
ping localhost
``` gives 
```
ping: icmp open socket: Operation not permitted
```

```
sudo ifdown eth0 && sudo ifup eth0 
``` gives
```
ifdown: interface eth0 not configured
```
Which is strange because I am absolutely sure that the ethernet interface was labelled eth0 before.

I have tried changing /etc/network/interfaces from
```
auto eth0
iface eth0 inet dhcp
```
to
```
auto lo 
iface lo inet loopback
```

I didn't know what I was doing here, just having a stab in the dark.

So I have 5 laptops that all intermittently don't connect to the internet.

Furthermore, I have a friend who is suffering under a virus loaded Vista. I have suggested he would be much better off using Ubuntu. But given this burdensome problem I am now very reluctant to suggest this to him. 

If anyone can give me some advice or point me in the right direction for the ultimate Intrepid wired/wireless trouble shooting guide, I and my friends using Ubuntu would be very much obliged. 

James.

---

### Post by lswest on 2008-12-20
can you post the output of ```
sudo lshw -C network
sudo iwconfig
``` please?  eth0 should be the ethernet device, and so you seem to be missing an interface.

---

### Post by Jimmy9pints on 2008-12-20
Thanks

Output of lshw -C network

```
  *-network               
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 7
       bus info: pci@0000:05:07.0
       logical name: eth0
       version: 02
       serial: 00:16:36:ce:f3:fb
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=32 link=no module=ssb multicast=yes port=twisted pair speed=10MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 92:70:72:f8:4e:c0
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

and iwconfig
```
 
lo no wireless extension.

eth0 no wireless extension.

pan0 no wireless extension.

```

If we could just sort out my WIRED extensions, that'd be a huge step in the right direction.

Cheers,

James.

---

### Post by albandy on 2008-12-20
do a lspci in console and paste it here. It will show your hardware

sudo lspci

---

### Post by Jimmy9pints on 2008-12-20
Hi, the output of lspci is
```
 00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
05:07.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
05:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
05:09.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
05:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
```

---

### Post by Jimmy9pints on 2008-12-20
By the way, my internet connection was working yesterday with no problems (except the network manager icon had a little red cross as if it wasn't connected - but it was). And as far as I know, I haven't changed any settings since then.

---

### Post by mpokrywka on 2008-12-20
Looks like your laptop has no wireless interface (maybe usb wifi?), and your wired ethernet card has no link (link=no), maybe network cable is defective/disconnected/loose in your computer or in your switch/router?

---

### Post by Jimmy9pints on 2008-12-20
OK I will try switching cables and ports (physical cable port in the router) and see how we go.

The wireless card is indeed a USB. I reckon sorting that out needs a new thread tho.

---

### Post by Jimmy9pints on 2008-12-20
OK I feel stupid. It was a dodgy cable causing the problem. That clears up the intermitent problems on two of five computers because they were sharing that cable. Thanks to those who helped here. 

As I said I'll start a new thread if I want to start sorting out the wireless on both machines. 

But before I wrap this thread up, a couple of questions:
Why did

```


sudo ifdown eth0 && sudo ifup eth0 
```

give
```


ifdown: interface eth0 not configured

```
???

And why is ping localhost not permitted?

---

### Post by mpokrywka on 2008-12-21
```
ifdown: interface eth0 not configured

```
It is probable exactly like it says: interface is not configured (was not configured earlier).
This command line is buggy, should be:
```
sudo ifdown eth0; sudo ifup eth0
```
(note ; instead of &&)
because you do not care about "ifdown" status, most important is "ifup" and you probably want it be done regardless.

"ping localhost not permitted" - I assume that you got:
```
user@host:~$ ping localhost
PING localhost (127.0.0.1) 56(84) bytes of data.
ping: sendmsg: Operation not permitted

```
This is caused by firewall rules

---

