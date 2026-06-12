---
title: "Problem with wireless card linksys WPC300N"
date: 2009-04-29
forum: Networking &amp; Wireless
---

### Post by wubiubiubi on 2009-04-29
I'm having a problem with the wireless card in the title. I know this has been asked before, but I tried all the solutions I could find, and none of them worked. I tried using wifi radar, I tried downloading new drivers from linksys's website, I tried deleting some files from ndsgtk and ndiswrapper, everything. I'm beginning to think I just got a defective card, because the computer doesn't even recognize that it's in. when I try to run "sudo wifi-radar" it returns a message saying that no wireless card was found. wifi-radar does work with my old netgear wireless card though. I got these same results on two computers, a Lenovo and a Dell Inspiron 5160. please help!

---

### Post by coffeeaddict22 on 2009-04-29
Hi,
Can you add a bit of detail.  Open a terminal, type in ```
lshw -C network
```
```
sudo iwconfig
```
```
nm-tool
```
the information from that will confirm what card, tell us  whether you've got a driver installed, what your wireless network looks like, and whether it's doing anything.
Also, are you running network manager?

---

### Post by wubiubiubi on 2009-04-30
see next post

---

### Post by wubiubiubi on 2009-04-30
```
collin@len-laptop:~$ sudo lshw -C network
[sudo] password for collin: 
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:05:01.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:d2:08:78
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network
       description: Network controller
       product: BCM43XG
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:06:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:19:7d:b0:6c:cb
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: a6:1a:57:7b:d7:1c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
collin@len-laptop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

collin@len-laptop:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             unavailable
  Default:           no
  HW Address:        00:0F:B0:D2:08:78

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


```







So here it is. btw, I'm not on ethernet as i write this, i'm using an old wireless card. so i had to put in the card (thereby killing my internet) to get this, and then take it out and put in the working card to post the info, if that make a difference.

---

### Post by coffeeaddict22 on 2009-04-30
If you're changing your hardware setup to make the system work, that's going to complicate things.  Try to keep the hardware setup stable if at all possible.

Your card is recognised.  However, I'm not sure which card it is.  The output from lshw shows you the Broadcom 4311 card doesn't have a logical name (which is bad), but does have a driver- ssb (which is good).
Your ethernet interface is eth0, only worth knowing so we can ignore it.
The BCM43XG card, again doesn't have a logical name.  It appears to be sharing the driver with the 4311, and this could be your biggest problem.  Did you have both cards in?

Reading [this]("http://www.donationcoder.com/Forums/bb/index.php?action=printpage;topic=17934.0") suggests there's a proprietary driver in the repos.  Have a look in System/Adminsitration/Hardware Drivers and see if you can turn it on there; if so, that should be the end of your problem.  It's one of the catches with downloading a driver though- you need an internet connection... the easiest way might be to get an ethernet link, even if it's only for 5 minutes.
 

If that doesn't work, I'd reinstall with the card in place.  One of the major problems with networking at present is that the kernel has got MUCH better at recognising cards in the last 12 months, but documentation is lagging.  If you installed with your old card in, that'll probably be what's causing half your problems.

The second option is to install ndiswrapper.  you haven't got it loaded at present by the looks ( you can confirm that by running ```
lsmod | grep ndiswrapper
``` and at least historically it's been the best way of getting your card running on Linux

---

### Post by wubiubiubi on 2009-04-30
thanks, i found it in the repository...i'm not sure how i managed to download the right driver though, i never used ethernet. in any case, thanks for the help!

---

### Post by coffeeaddict22 on 2009-04-30
Not sure what your question is, rusrek.  These forums are for Ubuntu; if you're using Win XP this is a good place to find people who don't know and are unlikely to care too much.
If you're using Ubuntu and trying to connect to a Win XP machine, that's something we've all had to do, and we're happy to help.  Can you explain exactly what the problem is?

No prob, wubi.    It should set itself up OK, but there are a few problems getting wifi running.  start another thread if you need more help.

Enjoy the ride!

---

