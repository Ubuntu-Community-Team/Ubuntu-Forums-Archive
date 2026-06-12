---
title: "Inspiron 1525 10.04 no connections at all"
date: 2011-07-08
forum: Networking &amp; Wireless
---

### Post by vlad43210 on 2011-07-08
Hi, 

relatively light Ubuntu user here. Installing Ubuntu on my mom's laptop. Installation went smoothly, but I don't have any internet. There seems to be no driver installed for the wireless, I tried to plug the computer into my modem, but it doesn't connect to the internet, won't even find the router. I copy paste some commands from the laptop. Any help would be greatly appreciated!

Vlad
[B]
ifconfig[/B]    eth0      Link encap:Ethernet  HWaddr 00:23:ae:14:26:ac  
              inet6 addr: fe80::223:aeff:fe14:26ac/64 Scope:Link
              UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
              RX packets:0 errors:0 dropped:0 overruns:0 frame:0
              TX packets:108 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:1000 
              RX bytes:0 (0.0 B)  TX bytes:26973 (26.9 KB)
              Interrupt:16 
     
   
  eth0:avahi Link encap:Ethernet  HWaddr 00:23:ae:14:26:ac  
              inet addr:169.254.6.176  Bcast:169.254.255.255  Mask:255.255.0.0
              UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
              Interrupt:16 
     
   
  lo        Link encap:Local Loopback  
              inet addr:127.0.0.1  Mask:255.0.0.0
              inet6 addr: ::1/128 Scope:Host
              UP LOOPBACK RUNNING  MTU:16436  Metric:1
              RX packets:735 errors:0 dropped:0 overruns:0 frame:0
              TX packets:735 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:0 
              RX bytes:57792 (57.7 KB)  TX bytes:57792 (57.7 KB)
     
   
  ** lspci**
    00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
    00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
    00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
    00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
    00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
    00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
    00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
    00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
    00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
    00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
    00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
    00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
    00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
    00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
    00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
    00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
    00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
    00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
    00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
    02:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
    02:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
    02:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
    02:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
    02:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
    09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
    0b:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

**sudo lshw -C network**      *-network               
           description: Ethernet interface
           product: 88E8040 PCI-E Fast Ethernet Controller
           vendor: Marvell Technology Group Ltd.
           physical id: 0
           bus info: pci@0000:09:00.0
           logical name: eth0
           version: 12
           serial: 00:23:ae:14:26:ac
           size: 100MB/s
           capacity: 100MB/s
           width: 64 bits
           clock: 33MHz
           capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
           configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 duplex=full firmware=N/A latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
           resources: irq:27 memory:fe8fc000-fe8fffff ioport:de00(size=256)
      *-network
           description: Network controller
           product: BCM4312 802.11b/g
           vendor: Broadcom Corporation
           physical id: 0
           bus info: pci@0000:0b:00.0
           version: 01
           width: 64 bits
           clock: 33MHz
           capabilities: pm msi pciexpress bus_master cap_list
           configuration: driver=b43-pci-bridge latency=0
           resources: irq:17 memory:fe7fc000-fe7fffff
      *-network DISABLED
           description: Wireless interface
           physical id: 2
           logical name: wlan0
           serial: 00:24:2b:3d:9a:18
           capabilities: ethernet physical wireless
           configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
    [FONT=&quot]
[/FONT]

---

### Post by vlad43210 on 2011-07-09
bump

---

### Post by spiky001 on 2011-07-09
Hi you could try running from live cd see if internet works, if it dose it might be worth while as it,s a new install reinstalling with wired cable connected

---

### Post by vlad43210 on 2011-07-09
Hi,

short version: I got wireless internet on the laptop working but I think wired still doesn't work.

I ran the system from LiveCD, and the wireless worked! Specifically, at first nothing worked (neither wireless nor wired), then I loaded up Hardware Drivers, and it showed me two Broadcom drivers that were available. I tried activating the first one, it failed. I tried activating the second one, it told me a restart would be needed. I waited a little bit, and the second driver seemed to activate by itself. After that, I was able to see wireless networks. I typed in my network password and was able to connect and use the Internet.

I reinstalled 10.04 with an ethernet cable connected. No connections availble. Since on LiveCD activating Broadcom seemed to help, I tried to look for Hardware Drivers. It says "No proprietary drivers are in use on this system." I then followed the instructions in: 

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

and installed both the STA and the B43 drivers, using a USB stick to copy the B43 firmware over. The instructions indicate that at the end the user should go to Administration -> Hardware Drivers and activate the new drivers. However, when I did that, the system still told me no new drivers were available. On the other hand, wireless networks were now showing up under the internet connections toolbar (the radio lines on the top right). I selected my network, typed in the password, and was able to access the internet. 

However, it seems that the wired connection is still not working, which is a little troubling. The driver for it seems to be installed (see my original message) but it's not able to connect to the internet. I did a quick google search but wasn't able to find anything. If anyone has sage advice, would be much appreciated!

---

### Post by nm_geo on 2011-07-09
Please do this in terminal

```
lspci -nn
```

Have you updated and upgraded?

```
sudo apt-get update 

```
```
sudo apt-get upgrade
```

---

### Post by vlad43210 on 2011-07-09
Hi,

I updated and upgraded with those commands, everything seemed to go fine. Checked that wired connection still not working after update + upgrade:

-disconnected wireless
-plugged in ethernet cable
-clicked on "auto eth0" under wired networks
-after a wait, there was a red exclam over the radio icon and a message saying the wired connection was disconnected (offline).

with the ethernet cable plugged in:
lspci -nn 
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 0c)
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a03] (rev 0c)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 02)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 02)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 02)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 [8086:2847] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 02)
02:09.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
02:09.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
02:09.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
02:09.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 12)
09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 12)
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)

---

### Post by nm_geo on 2011-07-09
Ok gives us 

```
sudo lshw -C network
```

---

### Post by vlad43210 on 2011-07-10
It was in the original post, but here it is again:

*-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:23:ae:14:26:ac
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:27 memory:fe8fc000-fe8fffff ioport:de00(size=256)
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth1
       version: 01
       serial: 00:24:2b:3d:9a:18
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=192.168.1.2 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:fe7fc000-fe7fffff

---

### Post by vlad43210 on 2011-07-10
PS I don't know if this is relevant or not, but I checked the system kernel log, and it has messages like this:

[   13.441746] sky2 eth0: enabling interface
[   13.441851] ADDRCONF(NETDEV_UP): eth0: link is not ready

---

### Post by nm_geo on 2011-07-10
> **vlad43210 said:**
> PS I don't know if this is relevant or not, but I checked the system kernel log, and it has messages like this:

[   13.441746] sky2 eth0: enabling interface
[   13.441851] ADDRCONF(NETDEV_UP): eth0: link is not ready

I assume you have tried to reboot with the ethernet cable attached and that we are sure the cable is a good one.  I thought maybe you needed firmware installed but everywhere I looked the sky2 driver looks just like yours. We could look at the dmesg in more depth, but I see nothing wrong.

Try the following line copy and paste in terminal.

```
dmesg | egrep 'ound|irmware|eth|ath|wl|ipw|b43|witch|sky2|ssb|ndiswrapper' 
```

---

