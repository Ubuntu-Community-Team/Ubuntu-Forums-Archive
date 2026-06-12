---
title: "no networks detected"
date: 2010-04-23
forum: Networking &amp; Wireless
---

### Post by squid1230 on 2010-04-23
no wireless upon re-installation of 9.10
Drivers seem installed.
No wireless networks detected.

lshw -c network

*-network
description: Ethernet interface
product: 88E8038 PCI-E Fast Ethernet Controller
vendor: Marvell Technology Group Ltd.
physical id: 0
bus info: pci@0000:02:00.0
logical name: eth0
version: 14
serial: 00:e0:b8:c2:71:f5
size: 100MB/s
capacity: 100MB/s
width: 64 bits
clock: 33MHz
capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.23 duplex=full firmware=N/A ip=192.168.1.3 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
resources: irq:27 memory:d4000000-d4003fff ioport:2000(size=256)
*-network
description: Wireless interface
product: AR5001 Wireless Network Adapter
vendor: Atheros Communications Inc.
physical id: 0
bus info: pci@0000:03:00.0
logical name: wlan0
version: 01
serial: 00:21:63:62:37:a4
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=ath5k latency=0 multicast=yes wireless=IEEE 802.11bg
resources: irq:17 memory:d6000000-d600ffff



ifconfig:

wlan0 Link encap:Ethernet HWaddr 00:21:63:62:37:a4
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)



I've tried ndiswrapper and madwifi to no avail.

HeeelllllllllllllpppppP!

p.s relative noob

---

### Post by P4man on 2010-04-23
I also have a atheros 5001 wifi card (in my case its a Nec Warpstar aterm WL54AG(S). Cant get it to work no matter what. I tried to install some backport modules someone suggested and that would cause in instant kernel panic.

In dmesg I get some errors about the card not posting. Google doesnt help, its like Im the only one having that error. To be fair, I dont know if the card actually works or maybe is broken. Its impossible to find drivers for it that work on windows either, so I just picked up a different card.

---

### Post by bobyy on 2010-04-23
The network interface seems to be up .
To see wireless networks do a :
#sudo iwlist wlan0 scan

---

### Post by Iowan on 2010-04-23
Short term... unplug the ethernet cable and restart/reboot.

---

### Post by squid1230 on 2010-04-23
> **bobyy said:**
> The network interface seems to be up .
To see wireless networks do a :
#sudo iwlist wlan0 scan


wlan0     No scan results

Ethernet plugged in only to be able to get my email.

---

### Post by squid1230 on 2010-04-26
Hello again,
Recently my laptop crashed in an odd manner. I was stuck in a login loop ( even though I had disabled login on bootup). Upon entry of the login info, the screen would go black for a few seconds and then prompt me for the info again. Needless to say I reinstalled 9.10 but my wireless stopped working. In my frustration I installed beta 10.04 hoping that a newer release would have the cure.

It seems my atheros card is seen and driver is loaded, it just doesn't see any signals. I have blacklisted the Hal and other files including ndiswrapper etc, but to no avail.

So in case some of you guys  want to take a crack at this. . . . . 

[I]t@t-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:e0:b8:c2:71:f5  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:b8ff:fec2:71f5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15792 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16494 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8456710 (8.4 MB)  TX bytes:3188207 (3.1 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:21:63:62:37:a4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
[/I]


[I]t@t-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
[/I]

( I see a lot of "offs" - is that normal?)


[I]t@t-laptop:~$ sudo iwlist wlan0 scan
[sudo] password for t: 
wlan0     No scan results
[/I]


[I]t@t-laptop:~$ 
alsa-base.conf
blacklist
blacklist-ath_pci.conf
blacklist-ath_pci.conf~
blacklist-bcm43.conf
blacklist.conf
blacklist-firewire.conf
blacklist-framebuffer.conf
blacklist-modem.conf
blacklist-oss.conf
blacklist-watchdog.conf
libpisock9.conf
sl-modem.conf
[/I]


[I]t@t-laptop:~$ sudo ifup wlan0
Ignoring unknown interface wlan0=wlan0.[/I]

huh? Might that have something to do with it?

Any help, guys, would be greatly appreciated.

Cheers:D

---

### Post by squid1230 on 2010-05-03
bump. Anyone?

---

