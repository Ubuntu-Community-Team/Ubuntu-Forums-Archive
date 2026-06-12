---
title: "Unblacklist atheros wireless drivers in ubuntu 11.04"
date: 2011-04-28
forum: Networking &amp; Wireless
---

### Post by Stord on 2011-04-28
In previous versions of ubuntu, my wireless driver didnt work too well at all. In this version, i was afraid it wouldnt work to well.

I found solution here
[http://axcoto.com/blog/article/tag/siocsifflags-operation-not-possible-due-to-rf-kill](http://axcoto.com/blog/article/tag/siocsifflags-operation-not-possible-due-to-rf-kill)

I would suggest unblacklisting ath_pci in /etc/modprobe.d/blacklist-ath_pci.conf


Once i did this and restarted, wireless worked perfectly (at least in the couple of hours ive been using it!)

I think this could be considered a bug, but i dont know how to report a general bug like this using ubuntu-bug...

In case one wonders, sudo lshw -C network produces

```

*-network               
       description: Ethernet interface
       product: MCP77 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1f:16:78:95:83
       capacity: 100Mbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
       resources: irq:41 memory:c0009000-c0009fff ioport:30f8(size=8) memory:c0007c00-c0007cff memory:c0007800-c000780f
  *-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 01
       serial: 00:24:2b:91:e3:89
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.38-8-generic firmware=N/A ip=10.4.188.239 latency=0 link=yes multicast=yes wireless=IEEE 802.11bg
       resources: irq:23 memory:c2000000-c200ffff

```

---

### Post by akin-lombok on 2011-04-28
thanks for this usefull info.
i planned to update my laptop in short time

---

### Post by chrisblue on 2011-06-18
Thanks, worked perfectly for me

---

### Post by MetalFletcher on 2011-10-05
My Acer Aspire one uses the same atheros wireless driver, but this solution did not work for me.

---

### Post by WarrenSensei on 2011-10-05
I have been helping (trying to help) a new convert to Ubuntu get through this problem. I have already tried this fix, but it did not solve the problem. All the other solutions I've encountered depend on outdated backports packages, and the current backports don't contain the component needed.

The computer is an Acer Aspire One ZG5 with the identical wireless hardware described above and was connecting to wireless just fine under Window$XP. Now running Ubuntu 11.04, the wireless device refuses to be enabled, the hardware switch does nothing, and of course cannot see any networks available. The wired Ethernet works fine. The relevant sudo lshw -C network says "*-network - disabled" before describing the hardware correctly.

My friend has been wanting to make the switch to Ubuntu for a while and now that I've wiped his drive clean of the virus known as Windows, it's broken, so any help anyon can give would be GREATLY appreciated!

~Warren

---

### Post by WarrenSensei on 2011-10-05
Hey, it's the friend I was trying to help! He's totally new (as of Monday) to Linux, so be gentle!

> **MetalFletcher said:**
> My Acer Aspire one uses the same atheros wireless driver, but this solution did not work for me.

---

