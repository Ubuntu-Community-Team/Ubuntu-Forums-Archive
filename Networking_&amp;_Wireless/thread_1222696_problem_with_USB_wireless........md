---
title: "problem with USB wireless......."
date: 2009-07-25
forum: Networking &amp; Wireless
---

### Post by LeonLinux on 2009-07-25
Hello everyone :P
i'm newbie with Linux/Ubuntu,
i downloaded ISO DVD Ubuntu v9.04 , and installed it, now i've Dual boot, Vista and Ubuntu,
until now, i've one problem, it is my usb wireless
this model :
[COLOR="#0000ff"][http://www.engeniustech.com/datacom/products/details.aspx?id=154](http://www.engeniustech.com/datacom/products/details.aspx?id=154)[/COLOR]

however, i installed ndiswrapper,
and installed XP driver that supposed to be for Atheros AR5523, because my wireless have Chipset AR5523
the driver i downloadeded was from this link:
[COLOR="Blue"][http://blog.fourthirty.org/?p=132](http://blog.fourthirty.org/?p=132)[/COLOR]

(if you ask me about why i didn't used the driver from CD of my wireless, my answer will be: it has Setup.exe, and can't extract by Winrar)

so when i installed it, i saw that the light of wireless is ON
that means it is work, 
but when i go to the Network Icon in the top toolbar, i see this:

[IMG]http://img119.imageshack.us/img119/6637/screenw.jpg[/IMG]

device not managed?
no network detected?

i tried to use Terminal,
i used: "iwlist wlan1 scan" , i saw a lot of networks that my wireless detected them, so odd. :confused:

this info about my usb wireless might be useful for you to detect the problem,

```
sudo ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
net5523 : driver installed
	device (0CF3:0002) present
______________________________________________________________

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wlan1     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:108 Mb/s   
          Power Management max timeout:0us  mode:All packets received
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

______________________________________________________________

lsusb
Bus 002 Device 007: ID 0cf3:0002 Atheros Communications, Inc. AR5523 (no firmware)
Bus 002 Device 006: ID 0079:0006  
Bus 002 Device 005: ID 05a9:2640 OmniVision Technologies, Inc. 
Bus 002 Device 004: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 15d9:0a37  
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

______________________________________________________________

sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no module=ssb multicast=yes port=twisted pair speed=10MB/s
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
  *-network:1 DISABLED
       description: Wireless interface
       physical id: 3
       logical name: wlan1
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net5523 driverversion=1.53+,07/27/2005,1.5.0.102 link=no multicast=yes wireless=IEEE 802.11g

```

any help?
Thank you :)

---

### Post by LeonLinux on 2009-07-26
I can't believe,, that nobody did help me :(
however, it is work sometimes 
i just deleted the file called : 'interfaces' from this directory '/etc/network'
i deleted that file because it is stored settings of wlan1 that might do some conflicts

```
auto lo
iface lo inet loopback

auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig wlan1 up # line maintained by pppoeconf
provider dsl-provider

auto wlan1
iface wlan1 inet manual

auto --help
iface --help inet manual
```

however, the wireless is work fine after reboot , and i can see it is detected many networks when i select Network Icon in the top toolbar, but sometimes the wireless is not work when i reboot computer again,

don't know what the problem exactly
:confused:

---

### Post by martinbaselier on 2009-07-26
It's al volunteers who try to help here. The person with the right knowledge just needs to see your problem. I have never used ndis myself for example. I do however notice that you need to rename a file:

**sudo mv /etc/modprobe.d/ndiswrapper /etc/modprobe.d/ndiswrapper.conf**

---

### Post by LeonLinux on 2009-07-26
> **martinbaselier said:**
> It's al volunteers who try to help here. The person with the right knowledge just needs to see your problem. I have never used ndis myself for example. I do however notice that you need to rename a file:

**sudo mv /etc/modprobe.d/ndiswrapper /etc/modprobe.d/ndiswrapper.conf**

the wireless is fine now :D
but when i unplug usb wireless , and plunin again, then it will not work, even the light in usb card is OFF ,
any idea?
thank you O:)

Edit: when i restart my computer, the wireless will work

---

### Post by philcamlin on 2009-07-26
i had the same issue with my mac it would only detect it on boot
never fixed it :(

its not loading the drivers after you plug it in. thats all i know :popcorn:

---

### Post by LeonLinux on 2009-07-26
> **philcamlin said:**
> i had the same issue with my mac it would only detect it on boot
never fixed it :(

its not loading the drivers after you plug it in. thats all i know :popcorn:

oh you also have the same problem? :(
we have to cry ](*,)

---

### Post by LeonLinux on 2009-07-27
Up :(

---

### Post by LeonLinux on 2009-07-27
until now,,my wireless is work very well :shock:
even when i unplug usb and plugin again, it is work :P
i don't know what's happened  :-k
anyway, it is work!  \\:D/
thanks folks ):P

---

