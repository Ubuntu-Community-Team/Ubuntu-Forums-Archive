---
title: "Inconsistent WiFi Connectivity on Dell Laptop"
date: 2009-04-20
forum: Networking &amp; Wireless
---

### Post by laptendo64 on 2009-04-20
Hola amigos!  I'm a newcomer to linux:  never used it at all before I installed Ubuntu on my laptop last week but it's running great and I'm exceptionally hyped on it.  The only problem I've been having is that I can only get my wireless card to work in a roundabout kind of way.

Here's the run-down on my system and the weirdness that's going on:  I'm running Ubuntu 8.10 64-bit on my Dell Vostro 1000 and I've got a wireless 1505 draft 802.11n WLAN mini-card and my ethernet controller is that Broadcom 44x 10/100.  I had a lot of trouble getting my wireless driver installed and I followed several different sets of directions:  used ndiswrapper on the command line, used the graphical ndiswrapper, used the restricted drivers manager, and probably some other stuff that I forgot about.
Anyways, at some point I finally managed to get the driver installed and it was detecting the hardware and the driver, and then when I checked the restricted hardware menu it included "Broadcom STA wireless driver" so I clicked "Activate" and a few seconds later the WiFi light came on and I connected to a wireless network. There was much rejoicing, etc.      
All the jubilation came to an end the next morning when I went down to the local neighborhood coffee shop and booted up the laptop and realized that the WiFi light wasn't on, so I went to the restricted hardware manager and de-activated the driver and then re-activated it but nothing happened and it didn't seem to be detecting my hardware.  The other weird thing that happened was that a few seconds after I activated the driver, the networks icon in my tray flashed a message saying "Disconnected" and then the icon disappeared from the tray and I haven't been able to figure out how to restore it, short of restarting the computer.
As of more recently what I've discovered is that on some WiFi networks de-activating then activating "Broadcom STA wireless driver" on the hardware manager allows me to connect to the network right away.  At other times my laptop has to be directly plugged into the router via an ethernet cable for it to be able to recognize the wireless card and get some WiFi connectivity.

The main things I'm trying to find out about all of this are:
1)  How can I get my WiFi driver to load and be activated and everything automatically when the computer boots?
2)  Why does it often only work when a wired connection is already established?


Also I tried out the dmesg command and found some stuff about my wireless device but I don't really understand what it means.  I was basically doing a lot of trial-and-error with all these different directions for using ndiswrapper and I think maybe I have the wrong stuff blacklisted or not blacklisted or something like that.  

[  424.529228] b44: eth0: powering down PHY
[  424.845247] b44 0000:08:00.0: PCI INT A disabled
[  424.889225] b43-pci-bridge 0000:05:00.0: PCI INT A disabled
[  424.953656] wl: module license 'unspecified' taints kernel.
[  424.957052] wl 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[  424.957068] wl 0000:05:00.0: setting latency timer to 64
[  424.980070] udev: renamed network interface eth0 to eth1
[  424.999357] ieee80211_crypt: registered algorithm 'TKIP'
[  425.000660] eth1: Broadcom BCM4328 802.11 Wireless Controller 5.10.27.12
[  425.036071] b44 0000:08:00.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[  425.096142] ssb: Sonics Silicon Backplane found on PCI device 0000:08:00.0
[  425.097595] b44.c:v2.0
[  425.117266] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:1c:23:9d:dd:f6
[  425.197179] wl 0000:05:00.0: PCI INT A disabled
[  425.197414] wl 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[  425.197424] wl 0000:05:00.0: setting latency timer to 64
[  425.213169] eth1: Broadcom BCM4328 802.11 Wireless Controller 5.10.27.12
[  429.223424] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  432.816238] b44: eth0: Link is up at 100 Mbps, full duplex.
[  432.816253] b44: eth0: Flow control is off for TX and off for RX.
[  432.817497] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  435.992050] eth1: no IPv6 routers present
[  443.072065] eth0: no IPv6 routers present
[  468.816134] b44: eth0: Link is down.



Anyways, if anyone could shed some light on the situation it'd be much appreciated.  This is pretty much the only remaining thing that's not functioning 100%, but that said I've been really impressed with all the support threads on these boards and stuff, so thanks to everyone who's gotten me this far.

---

