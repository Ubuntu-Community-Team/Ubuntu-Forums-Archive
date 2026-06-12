---
title: "Wireless on Twinhead Efio D212A"
date: 2005-12-30
forum: Networking &amp; Wireless
---

### Post by noeluylee on 2005-12-30
Hi Guys,

I am setting up my friend's notebook computer model Twinhead EFIO D212A, everything was okay, from video to usb and ethernet adapter, but the built-in wireless lan/ wifi is not detected, I was doing  search on the net but its no avail, I cannot find it, maybe some of you guys have encountered this issue and could help me out. 

Thank you so much...

---

### Post by Lambert on 2005-12-30
Try these commands


sudo lshw

sudo lspci -v | grep Ethernet (or just lspci -v if no output when piping to grep)

Does the device show up in this output? If so post it here.

---

### Post by noeluylee on 2005-12-30
Hi , Thanks heres the output.


 *-network
             description: Ethernet interface
             product: VT6102 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@00:12.0
             logical name: eth0
             version: 74
             serial: 00:40:45:1b:9d:c1
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical tp mii 10bt 10b t-fd 100bt 100bt-fd autonegociation
             configuration: autonegociation=on broadcast=yes driver=via-rhine dr iverversion=1.2.0-2.6 duplex=full ip=14.12.88.100 link=yes multicast=yes port=MI I speed=100MB/s
             resources: ioport:d800-d8ff iomemory:dffffe00-dffffeff irq:11
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: wlan0


       capabilities: ethernet physical
       configuration: broadcast=yes driver=p80211_prism2_usb driverversion=0.2.2  link=no multicast=yes
jason@Jason:~$ sudo lspci -v | grep Ethernet
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
jason@Jason:~$


saw a wlan0 disabled, how can i enable it?

Thanks

---

### Post by omenix on 2006-09-16
I have the same problem.. anyone can resolve this?

---

