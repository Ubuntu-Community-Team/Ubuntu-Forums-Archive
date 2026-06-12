---
title: "Enable network device - tips needed"
date: 2009-03-18
forum: Networking &amp; Wireless
---

### Post by ergman on 2009-03-18
Hey all,

First off I want to say that I am about 4 hours old to Linux and Ubuntu.  I honestly know very little about Linux and find that Ubuntu is probably my best way to get into it. 

I recently purchased an HP mini 1000 netbook (model 1030NR).  It came with Windows XP SP3 and it is SUPER DUPER slow. Boot times suck, application load times are terrible, and so on. 

This morning I installed Ubuntu 8.10 via my USB thumb drive (thanks to some utilities I found on pendrivelinux).  The install went well... 

Now here is my issue...


It appears that my wireless card is working OK.  I am able to see neighboring wifi connections.  I can even connect to them. 

I went to test my wired connection and I don't get anything. The network management icon on the system bar states "Network disconnected".  The lights on the onboard NIC light up indicating that I at least have a physical connection. I use if config and it states the ip address is 127.0.0.1

All other PCs on my network get assigned an IP address from my router with no issue.

I wasn't sure if I had a network driver loaded so I used the following command and this was the output.

NOTE: the wired device seems to be DISABLED

lshw -c network

*-network
description: Wireless interface
product: BCM4312 802.11b/g
vendor: Broadcom Corporation
physical id:0
bus info: pci@0000:01:00.0
logical name: eth0
version: 01
serial: 00:24:2b:53:xx:xx (assume this is the mac address)
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes
wireless-IEEE802.11

*-network DISABLED
description: Ethernet interface
physical id: 2
logical name: pan0
serial: f2:5b:f3:71:xx:xx (assume this is the mac address)
capabilities: ethernet physical
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A
multicast=yes

Next I tried to enable the wired network device with this command

sudo ifup pan0

Here is the output from that command.  

Ignoring unknown interface pan0=pan0

I assume that I use pan0 because that is the logical name of the device. I have also tried

sudo ifup eth1

Because I am so new to Linux I am stumped.  However I will continue to search and hopefully hear something back from the Ubuntu community. 

Thanks in advance for all of you help. 

-ErgMaN

---

### Post by ergman on 2009-03-18
One additional note.  When I use the ifconfig command I only see eth0 and lo.  From the lshw -c network command it looks like eth0 is my wireless adapter and lo is an internal loopback.  It doens't look like the ifconfig copmmand sees my wired device.

Any thoughts?

-ErgMaN

---

### Post by miegiel on 2009-03-18
**pan0** is a strange network device name. Usually they're called eth0, eth1, wlan0, etc. Try a forum search on "pan0" :)

edit: ```
lspci
``` should show if your wired cards drivers are up and running.

---

### Post by SirScott13 on 2009-03-24
I am having a similar problem.  My wireless card works fine, but my wired card doesn't.  I am fairly sure that my card doesn't have the drive, but I don't know how to assign the driver.

---

### Post by Malalo on 2009-03-24
Don't try to start pan0... Here's the result of my "lshw -c network" :

```
  *-network               
       description: Ethernet interface
       product: 82566DM-2 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: (Mac address)
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 firmware=1.4-0 ip=172.17.8.61 latency=0 module=e1000e multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: (Mac address)
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```

although I only have 1 card installed... it's either the loopback device, or something... no vendor, no bus info, no clock... looks virtual... 
your problem is elsewhere.

---

### Post by miegiel on 2009-03-24
> **SirScott13 said:**
> I am having a similar problem.  My wireless card works fine, but my wired card doesn't.  I am fairly sure that my card doesn't have the drive, but I don't know how to assign the driver.

You mean "lspci" or "lshw -C network" don't show your wired networkcard?

---

