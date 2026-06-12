---
title: "Compaq nx6110 Wireless Problems"
date: 2009-12-13
forum: Networking &amp; Wireless
---

### Post by johnmic on 2009-12-13
I've only recently been able to get Ubuntu up and running on my laptop (after many, many trials), but am now struggling to get the Wireless card working.

I followed all the instructions given in [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) up until Section 3.4.2.1, where I received the feedback:
```

bcmwl5.inf: driver installed

```
However, no device name was mentioned. Thus, I went to the advice given at [http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847), which said I probably had the wrong driver. I thus went to the HP website and downloaded the .exe file directly (from [http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=us&prodTypeId=321957&prodSeriesId=449877&prodNameId=449878&swEnvOID=1098&swLang=8&mode=2&taskId=135&swItem=ob-45290-1](http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=us&prodTypeId=321957&prodSeriesId=449877&prodNameId=449878&swEnvOID=1098&swLang=8&mode=2&taskId=135&swItem=ob-45290-1), if you wish to know). I then used cabextract to get the .inf and .sys files - these were the same ones as I had originally used. I then tried the following:
```

philip@Mathis:~$ sudo ndiswrapper -i ~/drivers/bcmwl5.inf
driver bcmwl5 is already installed
philip@Mathis:~$ ndiswrapper -l
bcmwl5 : driver installed

```
Thus, same problem. Can anyone offer any advice?

---

### Post by johnmic on 2009-12-13
OK, I've managed to make some progress - turns out I was being a bit idiotic, and hadn't thought to uninstall the old (defective) .inf file before installing the new one - once that had been done, the drive started being recognised. However, I now get:
```

philip@Mathis:~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
bcmwl5 : driver installed
    device (14E4:4318) present (alternate driver: ssb)

```

The problem is, the output of 'lshw -C Network' throws up this:
```

philip@Mathis:~$ sudo lshw -C Network
  *-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 4
       bus info: pci@0000:02:04.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:21 memory:d0000000-d0001fff
  *-network:1
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: e
       bus info: pci@0000:02:0e.0
       logical name: eth0
       version: 02
       serial: 00:14:c2:dd:cd:2f
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.0.7 latency=64 link=yes multicast=yes port=twisted pair speed=100MB/s

```

From what I can tell of the above, there is no conflict mentioned in the wireless card. If I forge on ahead with blacklisting using 'sudo gedit /etc/modprobe.d/blacklist.conf' and additing 'blacklist ssb', I still get the message for 'ndiswrapper -l' saying there's an alternate driver. This is due to dependency of b44 on ssb - if I also blacklist that, the ethernet doesn't work at all.

Any ideas?

---

### Post by bkratz on 2009-12-13
I'm a bit confused, why are you using ndiswrapper, the B43 site says the card is supported and you seem to be using it.

[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)


 description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 4
       bus info: pci@0000:02:04.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:21 memory:d0000000-d0001fff

it doesn't show any alternate drivers. There may be some sort of conflict between the two drivers, but it doesn't show up here.

When you say the ethernet doesn't work at all are you referring to wireless or wired?  It does show that you have an IP address on wired.

You might just try (in the terminal)

iwlist scan  (IWLIST in lowercase) and see if you see any networks

---

### Post by johnmic on 2009-12-13
I started this whole saga because the wireless didn't seem to work. However, since I seem to be having had issues, I've tried moving back to before I used ndiswrapper. I've done this by removing the blacklist entries in /etc/modprobe.d/blacklist, then running sudo update-initramfs -k

---

### Post by johnmic on 2009-12-13
I started this whole saga because the wireless didn't seem to be working. However, seeing as I haven't had much luck, I tried rolling back to before I started messing around. I've done this by removing the blacklist entries I added to /etc/modprobe.d/blacklist, running 'sudo update-initramfs -k all -u', then rebooting. I then ran 'sudo ndiswrapper -e bcmwl5' to try and bring it back to the very start - if you think I missed anything, please do let me know.

With all that done, running iwlist scan gives this:
```

philip@Mathis:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

```

I know there's a network in range - I connected earlier in XP, and I can actually touch the router if I lean slightly over to my right! However, now a blue light is on for my wireless, so it's a start!

---

### Post by bkratz on 2009-12-13
This thread seems to have worked for a lot of people with Broadcom devices

[http://ubuntuforums.org/showthread.php?t=1288865](http://ubuntuforums.org/showthread.php?t=1288865)



Here is another good one

[http://ubuntuforums.org/showthread.php?t=1336676](http://ubuntuforums.org/showthread.php?t=1336676)

---

### Post by johnmic on 2009-12-14
Unfortunately, the problem remains, despite trying quite a few solutions.

Whenever I install bcmwl-kernel-source, either through the Synaptic Package Manager or through the terminal, when I reboot I not only don't get my wireless, but my wired connection is also lost. When I uninstall bcmwl-kernel-source and reboot, I get the wired connection back, but still no wireless. One curious feature is the Hardware Drivers window, which, when I go into it, it shows up a driver called 'Broadcom B43 wireless driver' - it tells me a different version of this driver is in use, and trying to activate this makes no difference.

Any other ideas would be greatly appreciated - I've been moving through the forums to no great effect on this.

---

### Post by johnmic on 2009-12-15
I'm not sure if this is significant, but I've discovered a change in the output when I run the following in the terminal:
```

philip@Mathis:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 4
       bus info: pci@0000:02:04.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:21 memory:d0000000-d0001fff
  *-network:1
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: e
       bus info: pci@0000:02:0e.0
       logical name: eth0
       version: 02
       serial: 00:14:c2:dd:cd:2f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 multicast=yes
       resources: irq:16 memory:d000e000-d000ffff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:14:a5:2f:74:55
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

```

---

