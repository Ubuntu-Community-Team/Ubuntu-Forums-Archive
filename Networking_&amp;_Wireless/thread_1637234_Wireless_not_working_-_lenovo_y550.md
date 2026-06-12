---
title: "Wireless not working - lenovo y550"
date: 2010-12-04
forum: Networking &amp; Wireless
---

### Post by barry853 on 2010-12-04
Hi, 
I've instlled ubutnu 10.04 LTS on my lenovo y550 laptop. My wireless network is not working, I can connect by wire, and my wireless network is working on windows (similar like here [http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=9613210](http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=9613210) ). When i right-click on metwork connections icon in the upper right panel "Enable wireless" option is disabled and I can't enable it. I can't enable it with fn+F5 buttons either.

**lshw -C network**:

  ```
*-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 5100 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 00
       serial: 00:26:c6:19:74:e4
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:32 memory:f5100000-f5101fff
  *-network
       description: Ethernet interface
       product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 10
       serial: 00:26:22:dd:1e:1d
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 duplex=full firmware=sb v2.19 ip=192.168.1.14 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:33 memory:f5200000-f520ffff
```**ifconfig**:
```
eth0      Link encap:Ethernet  HWaddr 00:26:22:dd:1e:1d  
          inet addr:192.168.1.14  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:22ff:fedd:1e1d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14383 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12748 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15451784 (15.4 MB)  TX bytes:1979500 (1.9 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1200 (1.2 KB)  TX bytes:1200 (1.2 KB)

```

**iwconfig:**
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```
When i enter System > Administration > Hardware Drivers i have no proprietary software for my Broadcom wireless card. Only proprietary software available there is a driver for my graphic card

---

### Post by chili555 on 2010-12-04
> When i enter System > Administration > Hardware Drivers i have no proprietary software for my Broadcom wireless card. That's because you don't have a Broadcom wireless card; you have an Intel wireless card:> *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 5100 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
Let's ask your computer why it's not working. Please run and post:```
rfkill list all
dmesg | grep iwlagn
```

---

### Post by grahammechanical on 2010-12-04
I have read somewhere that when you shutdown Windows it switches off the wireless adapter in hardware. I think this is a power saving feature. You do not want the wireless draining battery power when you are not connected to a wireless network. It make sense.

May I suggest: 1). You make sure that the wireless activation key combination (FN+F5) is switching the wireless on before booting Ubuntu. 2) You right click the network manager icon and disable and then enable Networking. I find that that action causes Enable Wireless to enable. 3) Try switching the router/modem Off and then On. The initialization sequence will cause the modem to broadcast a signal that the wireless adapter may receive and be stimulated into action.

If these things do not work you will need to find out if you need drivers, how to obtain them, and how to install them.

Regards.

P.S. I have just seen the post from chili555. That's the person to advise on getting wireless drivers and their installation.

---

### Post by barry853 on 2010-12-04
Thanks for such fast replies.

An update to my problem:
- Wireless stopped working on Windows too. I'm pretty sure it worked before I installed ubuntu, but now I am confused
- I've upgraded to 10.10, not helped

@grahammechanical I tried to do it but as I've just written wireless stopped working on Windows. fn+F5 gives strange result - blank wireless manager, I don't know wtf. I've tried to reinstall energy management on windows but no result either.


**rfkill list all**
```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
```**dmesg | grep iwlagn**
```
[   14.812658] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   14.812661] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[   14.812755] iwlagn 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   14.812786] iwlagn 0000:04:00.0: setting latency timer to 64
[   14.812841] iwlagn 0000:04:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[   14.852574] iwlagn 0000:04:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   14.852708] iwlagn 0000:04:00.0: irq 48 for MSI/MSI-X
[   15.730425] iwlagn 0000:04:00.0: loaded firmware version 8.24.2.12
```

---

### Post by chili555 on 2010-12-04
> 0: phy0: Wireless LAN
    Soft blocked: no
    [COLOR="Red"]Hard blocked: yes[/COLOR]That means the hardware switch on your laptop is moved to 'Off.' That's why it doesn't work in Windows. Please find the switch and ... switch it!

---

### Post by chili555 on 2010-12-04
[http://answers.yahoo.com/question/index?qid=20090921163833AA1V9rX](http://answers.yahoo.com/question/index?qid=20090921163833AA1V9rX)> On the front edge of the system about am inch (2.5 cm) from the left corner is a switch. That needs to be pushed to the right for wireless to work.

---

### Post by barry853 on 2010-12-04
> **chili555 said:**
> That means the hardware switch on your laptop is moved to 'Off.' That's why it doesn't work in Windows. Please find the switch and ... switch it!

Like Apache would say - "It works!", I feel like an idiot though ;) Thank you very much, really admire your patience. Facepalm smiley would come in handy here. I have to change my nick now, and disappear from the net for a while, **** .. ;]

---

### Post by chili555 on 2010-12-04
No worries, we've all done it. Glad it's working.

---

