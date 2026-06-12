---
title: "Wireless Troubles (BCM4309, AR2413)"
date: 2009-12-24
forum: Networking &amp; Wireless
---

### Post by xandr55 on 2009-12-24
Hello Everyone,
Apologies if this is posted in an incorrect place, feel free to move it.
I am unsure what is going on with my wireless internet. I have searched for help but can't find anything at all on this problem. First my setup:

Laptop: Toshiba Satellite M45-S165
Wireless Cards And Chipsets: Broadcom BCM4306, Atheros AR2413, both work under windows and previous versions of ubuntu linux, as well as puppy linux.
OS: Ubuntu 9.1, Linux Mint 8 (also on fresh installations)
Drivers: Atheros: Ndiswrapper, ath5k, ath_pci (compiled madwifi driver instructions from [http://dimitar.me/?p=616](http://dimitar.me/?p=616))
         Broadcom: b43legacy, b43-fwcutter
Managers: Network Manager, wicd (both with wpa_supplicant), and none.

Here is what is going on: Using all of the above configurations I can connect to the internet via wifi for anywhere between, 30 seconds and 30 minutes. When it decides to stop working, the network managers don't seem to realize it, as they will still say that I am connected, but loading pages will time out, and if I am using wicd, it will say connected to network x, at -256dbm, or some other absurdly low number (when it works it says -40-50dbm), and all other networks disappear. At that point```
 iwlist scan
``` will give no scan results.```
 sudo /etc/init.d/networking restart
``` does nothing to rectify the situation,```
 sudo modprobe -r "driver"
``` and ```
sudo modprobe "driver"
``` does nothing, nor does ```
ifconfig device down
```, ```
ifconfig device up
```. The only thing that fixes it is to restart. Sometimes restarts don't even fix it, and I will have to restart multiple times. 

Needless to say this is incredibly frustrating. It isn't the hardware because I know that this computer with those same wireless cards works when running windows and puppy linux. Removing all of network manager, wicd and wpa_supplicant doesn't change the sittuation (monitored with successive iwscan's), as all networks will be initially found and then disappear later. I have tried reinstalling the package that contains ifconfig, and iwconfig, and this also doesn't change the situation. 

Thank you for any ideas, at this point I am willing to try anything! If you need any more information don't hesitate to ask! 

Thank you for your time,
Xander

p.s. My current lspci and lshw -C network
```

lspci
00:00.0 Host bridge: ATI Technologies Inc Device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
01:05.0 VGA compatible controller: ATI Technologies Inc RS400 [Radeon Xpress 200M]
02:04.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 02)
02:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
02:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
```

```
lshw -C network
  *-network:0             
       description: Network controller
       product: BCM4309 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 4
       bus info: pci@0000:02:04.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:17 memory:c0200000-c0201fff
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:02:07.0
       logical name: eth0
       version: 10
       serial: 00:a0:d1:23:0e:95
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:18 ioport:a000(size=256) memory:c0203000-c02030ff
  *-network
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:90:4b:78:9d:1b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.27 multicast=yes wireless=IEEE 802.11bg

```
Again Thank you!

---

### Post by xandr55 on 2009-12-29
So I seem to have figured out something that makes this work better, though once again I have no idea why it works. Once my internet goes down if I effectively install ndiswrapper and uninstall b43legacy, then reboot, then reinstall b43legacy, things work much better for a while (like 4hrs). I am doing this uninstalling and reinstalling by editing /etc/modprobe.d/blacklist.conf and /etc/modules....
Any ideas? 

Does anyone know why I have to do a full reboot for any differences to take effect -ie. sudo /etc/init.d/networking restart, or modprobe -r b43 legacy and then modprobe b43legacy doesn't work?

Even if I lost internet every couple of hours and then had to type some commands in to get it back it would be much better than the 5 minutes or so that a reboot takes....

Please if you have any ideas let me know and I will try it... This current situation is horrendous 

Again thank you all for your time.
Xander

---

### Post by Fueled on 2010-02-06
I'm having almost the same symptoms on my laptop. Have you had any luck in solving this problem?

---

