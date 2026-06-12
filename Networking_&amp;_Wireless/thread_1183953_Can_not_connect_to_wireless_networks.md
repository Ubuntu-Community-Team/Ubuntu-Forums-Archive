---
title: "Can not connect to wireless networks"
date: 2009-06-10
forum: Networking &amp; Wireless
---

### Post by imdmill on 2009-06-10
I installed ubuntu as a dual boot option on my Toshiba Satellite late d uring last semester.  After using it without problems for a while, it would no longer connect to my school's wireless network and eventually it started having troubles with connecting to the ethernet connection I had in my dorm room.  I came home from school, and have since been using the wireless network at my house without problems.

Yesterday, my computer stopped connecting to the wireless network.  It attempts to validate the connection, but then just repeatedly asks for the network key.  I browsed through these forums to try and find out if there was a specific problem.

I tried to fix it by installing Wicd, but that did not help any.  Then I found the [workaround to the Intel WiFiLink 5100]("http://ubuntuforums.org/showpost.php?p=7415234&postcount=3"), which is my wifi card.  I followed the steps on the workaround, downloading the file, using nautilus to copy it to the right directory, and then entering those commands into the terminal.  However, there is still no change, I can not connect to my home network secured with WPA.

I'm new to linux so I really don't know how to fix this.  I want to find a solution, however, before I start having troubles with auto eth0 like I had last time.

---

### Post by imdmill on 2009-06-11
Bump?

---

### Post by superprash2003 on 2009-06-11
does it work with WEP networks?? trying changing to WEP to test.

---

### Post by pastalavista on 2009-06-11
The kind of wireless card you have would be helpful information. Are you using any proprietary hardware drivers? You might try disabling them and then re-inabling them if still no connection. It sometimes helps to boot to a previous kernel if you have one and see if it still works OK.

If you don't know what kind of card you have check the output of this terminal command
```
sudo lshw -c network
```

---

### Post by imdmill on 2009-06-11
Yes, WEP networks are working.  It's just my school and my home's WPA networks that aren't.

```
*-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:33:55:67:f3
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.14 latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s
  *-network
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 01
       serial: 00:21:63:36:fe:4f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 module=ath9k multicast=yes wireless=IEEE 802.11bgn
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 7a:29:c4:66:bf:4c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

Also, yes I know the network is disabled, I got tired of it consistently telling me to input the network key.

---

