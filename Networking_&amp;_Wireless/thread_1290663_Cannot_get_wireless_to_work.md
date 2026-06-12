---
title: "Cannot get wireless to work"
date: 2009-10-13
forum: Networking &amp; Wireless
---

### Post by Koga73 on 2009-10-13
Hello. I'm new to linux, and I have been trying to get my wireless working for two days.

I have Ubuntu 9.04 x32 running through VMware Workstation 6.5 running thro Vista x64 with a bridged network connection (guest connects directly to the physical network).

My wifi card is D-Link DWA-556 via PCIe-x1. The card has an Atheros chipset so I initially started with madwifi. I got madwifi installed (no errors). Still could not get wifi to work. Then I tried NdisWrapper, and again didnt work. I uninstalled both, to start fresh and I need your help! :)

iwconfig:
```

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

```

ifconfig:
```

eth0      Link encap:Ethernet  HWaddr 00:0c:29:e1:4e:b6  
          inet addr:192.168.142.128  Bcast:192.168.142.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fee1:4eb6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:72640 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46788 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:93146637 (93.1 MB)  TX bytes:6635831 (6.6 MB)
          Interrupt:19 Base address:0x2024 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:568 (568.0 B)  TX bytes:568 (568.0 B)

```

lspci:
```

00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 01)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 01)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 08)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 08)
00:07.7 System peripheral: VMware Inc Virtual Machine Communication Interface (rev 10)
00:0f.0 VGA compatible controller: VMware Inc Abstract SVGA II Adapter
00:10.0 SCSI storage controller: LSI Logic / Symbios Logic 53c1030 PCI-X Fusion-MPT Dual Ultra320 SCSI (rev 01)
02:00.0 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB
02:01.0 Ethernet controller: Advanced Micro Devices [AMD] 79c970 [PCnet32 LANCE] (rev 10)
02:02.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 02)
02:03.0 USB Controller: VMware Inc Abstract USB2 EHCI Controller

```

My wireless card works 100% in Vista x64, but not in Ubuntu x32.

Any help is appriciated!

---

### Post by t0mppa on 2009-10-13
*Lspci* isn't picking up your wireless card, meaning the system doesn't recognize it at all. Have to get it to appear in there first, before you can start worrying about drivers, etc. Are you sure you haven't just accidentally disabled your wireless through a button or key combination (usually Fn + F5)?

---

### Post by Iowan on 2009-10-13
**lshw -C network** probably won't reveal any additional information, but might be worth checking anyway.

---

### Post by Koga73 on 2009-10-13
> **t0mppa said:**
> *Lspci* isn't picking up your wireless card, meaning the system doesn't recognize it at all. Have to get it to appear in there first, before you can start worrying about drivers, etc. Are you sure you haven't just accidentally disabled your wireless through a button or key combination (usually Fn + F5)?

Its on a desktop, there is no way to disable the wireless like on a laptop. And, I can literally alt-tab out of VMware Workstation and go into Vista and have working wifi.

AND:

lshw -C network:
```

  *-network               
       description: Ethernet interface
       product: 79c970 [PCnet32 LANCE]
       vendor: Advanced Micro Devices [AMD]
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:0c:29:e1:4e:b6
       size: 1GB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical logical tp 1000bt-fd
       configuration: autonegotiation=off broadcast=yes driver=vmxnet driverversion=2.0.1.1 duplex=full firmware=N/A ip=192.168.142.128 latency=64 link=yes maxlatency=255 mingnt=6 module=vmxnet multicast=yes port=twisted pair speed=1GB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: b2:05:df:a2:14:54
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

Nada, what can I do? Could VMware Workstation be the problem? I could format my hdd and install Ubuntu as primary OS and have Vista running thro VMware Workstation... but that sounds like an absolute nightmare with endless problems. Any suggestions?

---

### Post by t0mppa on 2009-10-14
Ah ok, desktop. Well, other than physically removing the card and putting it back, can't think of much that could make it appear on *lspci*. Could always try digging through **dmesg** or the system logs (at */var/log/syslog*) to see if they offer some help, but usually in a case such as that, the card does show up on *lspci*.

Even if your Windows leaves the card on a state from which Ubuntu can't automatically recover it from (a symptom seen sometimes, if rarely, on the forums), it should still show up on *lspci* and thus on *lshw* as disabled.

Perhaps rather than start a massive reinstall process, you could try downloading and running the live CD images of some other Linux distributions and see if they can pick the card up to see if you can narrow down the problem a bit.

---

### Post by Koga73 on 2009-10-14
Hmm, well thanks for the feedback. I think the problem is that its running thro VMware. Currently I have XP and Vista running on seprate partitions with a shared storage drive. I never use XP so im just gonna format that for ubuntu. I'm sure I'll be around the forums alot :)

---

### Post by sjprice on 2009-10-14
You could also try out VirtualBox before reformatting the XP partition, just to be sure it is VMWare...

---

### Post by Koga73 on 2009-10-21
followup... got it working. It was VMware. After installing ubuntu on its own partition everything works fine! Thanks

---

