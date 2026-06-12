---
title: "RTL8188CE, Ubuntu 12.04"
date: 2013-04-13
forum: Networking &amp; Wireless
---

### Post by Jonno303 on 2013-04-13
I've recently started using Ubuntu 12.04 64bit on a new Lenovo W530, dual booting with Windows 7. I have to admit that I do not know much about computers let alone how to use Ubuntu type commands, although copying and pasting them from instructive pages has helped a great deal.

I seem to be having really inconsistent WIFI issues. I usually connect via a repeater, but WICD takes a very long time to connect to it (WICD usually gets stuck on "obtaining IP address), so I try to move to a room closer to the main router and use the wifi there. Unfortunately that too is quite unstable. There are times when I get decent internet through the repeater but it can be choppy. If I'm using Skype the line almost always drops out (but at random times). Sometimes I can get it working after turning the modem, router and repeater off and on again.

I have tried to read through the past posts on the forums but it seems the problems are quite individual/unique. I do not know what information is required (and what commands I need to put in to display them). If someone could please instruct me how to display the relevant information I will gladly post it to this thread.

Many thanks in advance!

---

### Post by TheFu on 2013-04-13
Wifi sucks. Even if you get everything working perfectly, there is no guaranty that it still won't suck for your location. Any sort of radio interference can cause drops.  Neighbors can cause drops. Microwaves can cause drops.  Too many devices on the same channel or on any of the 10 channels around the channel can cause drops.

Wifi sucks.

Sorry, not any help, but wired is always better.

If you can accurately describe 
* your hardware
* your network
* your RF environment
perhaps we can help?

google for "wifi troubleshooter ubuntu" to get started.  The top 4 hits explain much.

---

### Post by Jonno303 on 2013-04-15
Thanks for the speedy response and I'm very grateful that a received a response to my question.

I googled[COLOR=#000000] "wifi troubleshooter ubuntu" but was quickly lost on the terminology. Perhaps the first three search results were different from yours? 

As I'm new to the tech world, I'm not sure if I can provide the detail you ask. But I can say that on my dual booted machine, the Windows side picks up wifi without any trouble. So I don't think the RF environment would play a significant part in my particular case. 

My network (hopefully this is the information you want): Siemens speedstream 4200 modem --> Netgear WGR614 v7 ---> Netgear Wifi extender WN 2000RPT.

As for the hardware:
[/COLOR][TABLE="width: 90%, align: center"]
[TR="bgcolor: #F7F7F7"]
[TD="width: 30%, align: left"]**Processor**[/TD]
[TD="width: 70%"]Intel Core i5-3360M[/TD]
[/TR]
[TR="bgcolor: white"]
[TD="align: left"]**Operating system**[/TD]
[TD]Windows 7 Home Premium 64[/TD]
[/TR]
[TR="bgcolor: #F7F7F7"]
[TD="width: 30%, align: left"]**Operating system Language**[/TD]
[TD="width: 70%"]Win7 HP64 English[/TD]
[/TR]
[TR="bgcolor: white"]
[TD="align: left"]**Total memory**[/TD]
[TD]8 GB PC3-12800 DDR3 (2 DIMM)[/TD]
[/TR]
[TR="bgcolor: #F7F7F7"]
[TD="width: 30%, align: left"]**Hard drive**[/TD]
[TD="width: 70%"]256GB SSD SATA3 OPAL[/TD]
[/TR]
[TR="bgcolor: white"]
[TD="align: left"]**Optical device**[/TD]
[TD]DVD Recordable, UBE w/SWR[/TD]
[/TR]
[TR="bgcolor: #F7F7F7"]
[TD="width: 30%, align: left"]**Battery**[/TD]
[TD="width: 70%"]9cell LI Battery TWL70++[/TD]
[/TR]
[TR="bgcolor: white"]
[TD="align: left"]**Bluetooth**[/TD]
[TD]Bluetooth 4.0 w/ antenna[/TD]
[/TR]
[TR="bgcolor: #F7F7F7"]
[TD="width: 30%, align: left"]**WiFi wireless LAN adapters**[/TD]
[TD="width: 70%"]ThinkPad 1x1 b/g/n[/TD]
[/TR]
[TR="bgcolor: white"]
[TD="align: left"]**Wireless WAN accessories**[/TD]
[TD]Mobile Broadband upgradable


[/TD]
[/TR]
[/TABLE]

---

### Post by Jonno303 on 2013-04-20
Update:

[COLOR=#000000]sudo lshw -C network

[/COLOR] ```
*-network               
       description: Ethernet interface
       product: 82579LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 04
       serial: 3c:97:0e:83:5a:fd
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.0.0-k firmware=0.13-3 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:42 memory:f3a00000-f3a1ffff memory:f3a3b000-f3a3bfff ioport:7080(size=32)
  *-network
       description: Wireless interface
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: a4:17:31:f7:5d:f5
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192ce driverversion=3.5.0-27-generic firmware=N/A ip=192.168.1.4 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 ioport:4000(size=256) memory:f3000000-f3003fff

```

[COLOR=#000000]

[/COLOR]

---

### Post by ahallubuntu on 2013-04-21
~

---

### Post by ahallubuntu on 2013-04-21
~

---

### Post by Jonno303 on 2013-04-21
many thanks for the constructive advice! 

building packages is a bit advanced for me at this stage, but I suppose that is the only way forward from here... 

As for Wicd, I came across it whilst searching for a solution to my wifi problems. It hasn't made much (if any) difference to my internet connection, but I can see how handy it can be. 

I'll start looking into the Realtek problem now. Thanks again for pointing me in this direction!

---

### Post by TheFu on 2013-04-21
> **Jonno303 said:**
> many thanks for the constructive advice! 

building packages is a bit advanced for me at this stage, but I suppose that is the only way forward from here... 

As for Wicd, I came across it whilst searching for a solution to my wifi problems. It hasn't made much (if any) difference to my internet connection, but I can see how handy it can be. 

I'll start looking into the Realtek problem now. Thanks again for pointing me in this direction!

Those instructions to use 
```
sudo apt-get install linux-headers-$(uname -r) build-essential
```
which will lead to you reinstalling the headers with every kernel update, which will be a pain.  However, there is a fix for this, at least to keep the current kernel headers loaded on your system.
One of three kernel header packages is required. Run
```
$ uname -r
```
and based on the returned string, install one of these:
{}-generic-pae = ```
apt-get install linux-headers-generic-pae
```
{}-generic = ```
apt-get install linux-headers-generic
```
{}-server = ```
apt-get install linux-headers-server
```

it will not fix the need to recompile and relink the driver after a new kernel is installed, however.  Hopefully, in the future, this specific driver will become core to the supported modules in Linux.  Only a DKMS solution will help with that.  Being tied to a specific kernel simply sucks, but if wifi is important and this is the hardware that you have, just be certain that once you have the correct kernel that works, you do use 
```
sudo apt-get upgrade
``` in your weekly patching, not **dist-upgrade** as it recommended for most desktop systems.  

Being on 12.04 is also smart. The kernel should be supported via backported security fixes for 4 more years.

---

### Post by Jonno303 on 2013-04-22
Thanks for these instructions. I have followed them (when I had a relatively strong internet connection) and will report back after 10 days or so. 

Thank you again! :)

---

### Post by Jonno303 on 2013-05-25
SOLVED (well mostly anyway):

I followed Ahallubunut and TheFu's advice. My wifi has been slow at times and sometimes my wifi extender needs to be reset, but the overall reliability of my internet connection has improved by about 80%. That's good enough for me right now, although I hope that future updates to 12.04 (and other Ubuntu releases) will be more wifi friendly.

Many thanks to the contributors to this thread!

---

