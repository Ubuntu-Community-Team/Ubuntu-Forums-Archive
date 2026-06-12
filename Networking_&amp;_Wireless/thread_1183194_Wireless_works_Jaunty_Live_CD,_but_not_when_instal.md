---
title: "Wireless works Jaunty Live CD, but not when installed"
date: 2009-06-09
forum: Networking &amp; Wireless
---

### Post by charonred on 2009-06-09
I just ran the Jaunty Live CD and connected to my wireless network without a problem; but after installing Jaunty from desktop and rebooting, it now won't connect ??

suggestions please ... 


> [I]I have an older 2003 IBM R40e laptop that I could never get to run Linux of any description until Hardy came along; everything pretty much worked 'out of the box' as such except wireless networking. After some fiddling around with ndiswrapper and the windows drivers for the equally as old Minitar PCMCIA card I got it to work; and it seemed pretty reliable.

When I installed Intrepid, even with ndiswrapper and Minitar driver, wireless connections were problematic at best.

This morning I decided to try Jaunty - I thought I'd just see how the OS went running from the CD first - I'm impressed; it detected my wireless network straight off, and without doing anything more than entering the WEP key, it is connected and browsing the web!

Well done and a big THANKYOU to all involved with the wireless networking support in Jaunty ... it works and I didn't have to do a thing

Jaunty is now being installed on my laptop (I've had Hardy installed as my default OS on my desktop PCs since mid '08 )[/I]

---

### Post by charonred on 2009-06-09
weird behaviour; after rebooting back to the Live CD, I could no longer connect, infact my network wasn't even listed.

I rebooted again to the installed version, still no connection or listing ??? 

I changed from 'shared key' to 'opensystem' and still nothing; then after a few minutes I suddenly had a connection and my network is listed - very weird; I shall continue rebooting to see if it can maintain the connection and listing.

---

### Post by superprash2003 on 2009-06-10
post output of **lshw -C network** from the ubuntu terminal

---

### Post by charonred on 2009-06-10
even though wireless connection box is checked to connect automatically, I have to manually connect by checking the radio button of the wireless connection in the network monitor (top panel) - how do I fix that?

once connected though, it seems quite stable (had it connected for a few hours hours earlier today doing updates and installing KDE and other packages)

anyhow, before I check the radio button to connect I get the following;
> john@my-IBM-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5901 100Base-TX
       vendor: Broadcom Corporation
       physical id: b
       bus info: pci@0000:00:0b.0
       logical name: eth0
       version: 01
       serial: 00:06:1b:cb:2a:89
       width: 64 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.94 firmware=5901-v3.6 latency=64 mingnt=64 module=tg3 multicast=yes
  *-network
       description: Wireless interface
       product: Wireless PCI Adapter RT2400 / RT2460
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 00
       serial: 00:08:a1:5b:07:24
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt2400pci latency=64 module=rt2400pci multicast=yes wireless=IEEE 802.11b
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 8e:3b:12:de:79:e6
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes



after connecting
> john@my-IBM-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5901 100Base-TX
       vendor: Broadcom Corporation
       physical id: b
       bus info: pci@0000:00:0b.0
       logical name: eth0
       version: 01
       serial: 00:06:1b:cb:2a:89
       width: 64 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.94 firmware=5901-v3.6 latency=64 mingnt=64 module=tg3 multicast=yes
  *-network
       description: Wireless interface
       product: Wireless PCI Adapter RT2400 / RT2460
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 00
       serial: 00:08:a1:5b:07:24
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt2400pci ip=192.168.1.111 latency=64 module=rt2400pci multicast=yes wireless=IEEE 802.11b
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 8e:3b:12:de:79:e6
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes


also, how do I set the workgroup so the desktop and laptop are in the same home network so I can move files between them  - I did this once before, but can't remember how.

---

### Post by charonred on 2009-06-11
I just booted this laptop up using the new Linux Mint 7 Live CD, entered the WEP key and it connected immediately. 

After I shut down and rebooted into the installed Jaunty, it took 3 attempts before it would connect - once it's connected it is quite stable.

But why is it so temperamental with the installed OS, but fine with a Jaunty or Mint Live CD ?   :confused:

---

### Post by charonred on 2009-08-05
A workaround of sorts; I keep the PCMCIA card out of it's slot until system has booted to desktop, once it is inserted, it is detected and connected - not ideal, but acceptable - maybe something to do with being an older laptop and PCMCIA card

---

