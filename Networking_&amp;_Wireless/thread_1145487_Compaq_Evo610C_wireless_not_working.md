---
title: "Compaq Evo610C wireless not working"
date: 2009-05-01
forum: Networking &amp; Wireless
---

### Post by Rickkm on 2009-05-01
Have installed Unbuntu 9.04 ... it all looks great. My 1st Linux. WIRED LAN WORKS >>>But no wireless. What I know is:

lsusb (shows)
rick@rick-laptop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

After I hit an "Fn" plus the "F2" keys the lsusb shows:

rick@rick-laptop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 049f:0076 Compaq Computer Corp. Wireless LAN MultiPort W200
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

I've installed the ndisgtk package ... it's ready to go. The "Using Windows Wireless Drivers" doc says simply point the ndisgtk program at the correct Windows .inf file. [COLOR=Red]And there is the rub[/COLOR]. I cannot find such a file anywhere on the web. I did find the Windows EXE driver for a Wireless LAN MultiPort W200. I even installed the "WINE" program to look at all of the files in the Windows EXE prog...no files were an .inf file.

Also:
rick@rick-laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VM (KM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 42
       serial: 00:02:a5:c3:be:ed
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k6-NAPI duplex=full firmware=N/A ip=192.168.2.103 latency=66 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s
 [COLOR=Red] *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: f2:ae:28:fa:2e:4c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
[/COLOR]
ANY IDEAS HOW I MIGHT LOCATE THE RIGHT *.inf FILE? IS THAT ALL I NEED? 

Thanks from the newest guy on this forum.

---

