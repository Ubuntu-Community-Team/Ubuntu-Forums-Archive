---
title: "wireless not working after updates - hardy"
date: 2009-07-01
forum: Networking &amp; Wireless
---

### Post by japhyr on 2009-07-01
Hello all,

I have had a fairly stable system for a long time now.  I had not updated my system for a while, so I installed updates today.  After installing the updates, I shut down.  When I started my computer again later, I could not connect to the internet over wireless.  I am connected over a wired connection now.

I have a Dell 600m running Hardy Heron.  I have an ATI Radeon RV250 Mobility FireGL 9000 wireless card.

If I run "sudo /etc/init.d/networking restart", this is what I get:
```
 * Reconfiguring network interfaces...                                                                                       Ignoring unknown interface eth2=eth2.
Ignoring unknown interface ath0=ath0.
Ignoring unknown interface wlan0=wlan0.
Ignoring unknown interface eth0=eth0.
eth1: ERROR while getting interface flags: No such device
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device eth1 ; No such device.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device eth1 ; No such device.
There is already a pid file /var/run/dhclient.eth1.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.

```

How do I get wireless working again?

---

### Post by The Toxic Mite on 2009-07-01
> **japhyr said:**
> <snip>
I have a Dell 600m running Hardy Heron.  I have an [highlight]ATI Radeon RV250 Mobility FireGL 9000 wireless card.[/highlight]
</snip>


That might be the **graphics** card you are describing.

Go to Applications > Accessories > Terminal, and type in this command:

```
lshw -c network
```Post the results when done.

---

### Post by superprash2003 on 2009-07-01
post output of
1)iwconfig
2)lshw -C network

at bootup , try choosing a previous kernel version and see if wifi works there..

---

### Post by japhyr on 2009-07-01
Sorry, I got so used to dealing with video card issues for a while that was the only card I could think of.

iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

```

lshw -C network:
```
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:14:22:ba:e9:45
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.1.105 latency=32 module=ssb multicast=yes
  *-network:1 UNCLAIMED
       description: Network controller
       product: PRO/Wireless 2915ABG Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=32 maxlatency=24 mingnt=3
```

---

### Post by japhyr on 2009-07-01
Fixed.

I noticed that four of the updates had not installed.  I made the mistake of updating over a wireless connection earlier today.  I finished the updates over the wired connection, restarted, and wireless works again.

Thank you both for the help.

---

### Post by The Toxic Mite on 2009-07-01
> **japhyr said:**
> Fixed.
 
I noticed that four of the updates had not installed. I made the mistake of updating over a wireless connection earlier today. I finished the updates over the wired connection, restarted, and wireless works again.
 
Thank you both for the help.
 
 
Heh! You're welcome! :D

---

### Post by gjb1002 on 2009-08-04
I have a more or less identical problem here. I also have Hardy and also updated today after not doing so for a while. Now my wireless interface is gone with similar symptoms. I even discovered that 4 of the updates had not installed, as did the original poster. But I've now installed them via the wired connection, rebooted and my wireless is still gone with the same symptoms.

Here's my versions of the output previously requested. Help greatly appreciated.

sofa-pc : lshw -C network
```
WARNING: you should run this program as super-user.
 *-network
      description: Ethernet interface
      product: NetLink BCM5906M Fast Ethernet PCI Express
      vendor: Broadcom Corporation
      physical id: 0
      bus info: pci@0000:04:00.0
      logical name: eth0
      version: 02
      serial: 00:1b:38:d0:4f:e6
      width: 64 bits
      clock: 33MHz
      capabilities: bus_master cap_list ethernet physical
      configuration: broadcast=yes driver=tg3 driverversion=3.86
ip=192.168.0.2 latency=0 module=tg3 multicast=yes
 *-network UNCLAIMED
      description: Network controller
      product: RaLink
      vendor: RaLink
      physical id: 0
      bus info: pci@0000:0c:00.0
      version: 00
      width: 32 bits
      clock: 33MHz
      capabilities: bus_master cap_list
      configuration: latency=0

```

iwconfig

```
lo        no wireless extensions.

eth0      no wireless extensions.
```

---

### Post by martinbaselier on 2009-08-04
There is no driver loaded for your wireless card. 

What's the output of:
**sudo lspci -s 0c:00.0 -v**
?

---

### Post by gjb1002 on 2009-08-05
```
0c:00.0 Network controller: RaLink Unknown device 0781
        Subsystem: RaLink Unknown device 2790
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at f8200000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: [40] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/5 Enable-
        Capabilities: [70] Express Endpoint IRQ 0


```

The driver was working before (obviously). When I originally set it up my wireless card wasn't detected, but I downloaded the RT2860PCI driver source from RaLink's website and built and installed it. After doing 

sudo modprobe rt2860sta

I then got it up and running. Executing that command now just produces

FATAL: Module rt2860sta not found.

Any help gratefully received.

---

### Post by gjb1002 on 2009-08-05
I found a tip to boot into an older kernel on a different thread. So I did, and then wireless worked fine again. The working kernel is 2.6.24-16-generic, while the newer broken one is 2.6.24-24-generic

I'm still not sure what to do now. For now it would be useful to make this older kernel the default on booting up (without needing to go into the grub menu and select it every time), would appreciate some tips on how to do that. 

In the longer run I guess I can't keep an old kernel forever, so it would be useful to find a way to decipher why the new kernel isn't finding my wireless card driver.

---

### Post by MadHatter21 on 2009-08-05
Was the update you applied kernel related? The same thing happened to me when I updated the kernel. Try booting off of a different kernel on start up. Turn your system on and click escape. Then try a version of kernel one before the lastest on you are running.

---

### Post by gjb1002 on 2009-08-05
MadHatter21,

I guess you missed my second post. I did indeed get it to work with an older kernel. But I still don't know what to do now.

Thanks,
Geoff

---

### Post by MadHatter21 on 2009-08-05
Reinstall the drivers and your set. I did the same thing yesterday. For some reason the drivers installed on the earlier kernerl did not carry over to the latest kernel. Try to reinstall the driver and lemme kno

madhatter21

---

### Post by gjb1002 on 2009-08-06
OK, I'll try to reinstall the driver when I get a moment. But what did you mean by "my set"?

---

### Post by Crafty Kisses on 2009-08-06
I think he means you're like good to go. I was helping MadHatter yesterday on this issue really in depth, and I finally solved it.

---

### Post by martinbaselier on 2009-08-06
FYI:

If you compiled the driver yourself, you will need to do so again with each kernel update. This is because the driver is in fact a kernel module.

---

### Post by gjb1002 on 2009-08-09
Many thanks for the help. I finally recompiled the driver and now it works fine with the new kernel. 

I guess I can always hope that at some point a new version of Ubuntu will recognise my wireless card "natively" without me needing to recompile it :)

---

