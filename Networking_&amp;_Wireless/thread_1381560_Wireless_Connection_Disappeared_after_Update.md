---
title: "Wireless Connection Disappeared after Update"
date: 2010-01-14
forum: Networking &amp; Wireless
---

### Post by VitaminBB on 2010-01-14
Just restarted after updating my Ubuntu and the wireless connection has disappeared and doesnt seem to be working.

If I right click on the network icon and go to "edit connections" I have a wireless tab and it has the right information about my router it in but I dont see anyway to get it to connect wirelessly.

Help! :(

---

### Post by VitaminBB on 2010-01-14
Here is more info if it helps ...

Please, it looks like Ubuntu really dropped the ball this time and everyone is suffering over this bad update.

> **_ifconfig_**

eth0      Link encap:Ethernet  HWaddr 00:16:d3:49:30:fa  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d3ff:fe49:30fa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24666 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19259 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:32343655 (32.3 MB)  TX bytes:2335490 (2.3 MB)
          Interrupt:21 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:41 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2456 (2.4 KB)  TX bytes:2456 (2.4 KB)


> **_lspci_**

00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [GeForce Go 6100] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
04:05.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
04:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
04:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

---

### Post by VitaminBB on 2010-01-15
Come on, anyone?

---

### Post by Silent Warrior on 2010-01-15
I don't know if I can be much help, but I have a similar issue. Note that my particular hardware is a Toshiba Satellite Pro L300-1CZ (Scandinavian naming). My problem is that if I update the kernel or libc6, my wireless (Realtek 8187B) goes down and stays down.

My home-brewn solution - which is really a cheap hack to avoid the problem entirely - is to run a working kernel AND an earlier version of the libc-packages. (In my case, running Mint 8: Kernel 2.6.31-14 and libc6[-etc] 2.10.1-0ubuntu15.) I noticed that trying to downgrade the libc-packages can be... dramatic, to say the least, so I really don't recommend that you try this - I didn't. A reinstall (and subseqently just not upgrading) would be much more painless.

Hm, let's just hold off on trying my 'fix' for the time being, until someone comes up with something that actually aims to solve the underlying problem.

---

### Post by VitaminBB on 2010-01-15
Its just amazing to me that Ubuntu can screw up this badly ...

---

### Post by superprash2003 on 2010-01-15
post output of **lshw -C network** , have you looked under system->admin->hardware drivers for any wifi drivers

---

### Post by VitaminBB on 2010-01-15
When I look all thats listed is the Nvidia video driver.

Here is the output you asked for, thanks for helping btw.

> [B]  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 5
       bus info: pci@0000:04:05.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=168 maxlatency=28 mingnt=10
       resources: memory:c3000000-c300ffff
[/B]

---

### Post by prabhjot on 2010-01-16
Same here. Just finished restarting after installing updates, now i can't connect wirelessly on my Dell Inspiron 1525. :( 
Hate to say it, but now I feel lucky I had windows 7 to fall back on.... (since it ain't possible to connect via LAN cable)

:confused: :confused: :confused: :mad: :mad: :mad:

---

### Post by prabhjot on 2010-01-16
> **superprash2003 said:**
> post output of **lshw -C network** , have you looked under system->admin->hardware drivers for any wifi drivers
Here's the output: 

```
prabhjot@TRNSLTR-LPTP:~$ lshw -c net
WARNING: you should run this program as super-user.
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:23:ae:19:3a:a0
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.23 firmware=N/A latency=0 multicast=yes
       resources: irq:28 memory:fe8fc000-fe8fffff ioport:de00(size=256)
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth2
       version: 01
       serial: 00:24:2b:6f:8f:03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:fe7fc000-fe7fffff

```

---

### Post by Silent Warrior on 2010-01-16
An update on my side:

I just tried the Lucid Alpha 2, and kernel 2.6.32-10 and libc 2.11 work for me. I hope the rest of you will have the same result, come release-day.

---

### Post by bkratz on 2010-01-16
> **prabhjot said:**
> Here's the output: 

```
prabhjot@TRNSLTR-LPTP:~$ lshw -c net
WARNING: you should run this program as super-user.
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:23:ae:19:3a:a0
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.23 firmware=N/A latency=0 multicast=yes
       resources: irq:28 memory:fe8fc000-fe8fffff ioport:de00(size=256)
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth2
       version: 01
       serial: 00:24:2b:6f:8f:03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:fe7fc000-fe7fffff

```



Here is a pretty helpful resource for the 4312.

[http://ubuntuforums.org/showpost.php?p=8510764&postcount=12](http://ubuntuforums.org/showpost.php?p=8510764&postcount=12)

---

### Post by prabhjot on 2010-01-16
> **bkratz said:**
> Here is a pretty helpful resource for the 4312.

[http://ubuntuforums.org/showpost.php?p=8510764&postcount=12](http://ubuntuforums.org/showpost.php?p=8510764&postcount=12)

Thanks for your effort, but it doesn't make any difference. :( 

Wireless was working perfectly fine just before restarting after performing update, I think it was libc . (I even updated over wireless)

I also tried [http://linuxfanatic.wordpress.com/2010/01/13/solved-wireless-driver-for-compaq-cq40-bcm4312/]("http://linuxfanatic.wordpress.com/2010/01/13/solved-wireless-driver-for-compaq-cq40-bcm4312/").
But I can't compile since I have 64 bit karmic.

Any other suggestions?

---

### Post by prabhjot on 2010-01-16
> **Silent Warrior said:**
> An update on my side:

I just tried the Lucid Alpha 2, and kernel 2.6.32-10 and libc 2.11 work for me. I hope the rest of you will have the same result, come release-day.

Any backports available for the wireless driver?

---

### Post by VitaminBB on 2010-01-23
Why isent there more information on this?

A TON of people have been affected by this and the help is nowhere to be seen these days.

---

### Post by VitaminBB on 2010-01-27
Any news about this?

---

### Post by Pitel on 2010-02-21
I'm having this issue too.

---

### Post by lostsoul86 on 2010-02-21
I have the same issue on inspiron 1525 with intel wireless. I can't connect the wireless through network-manager, although I can connect by manualy launching wpa-supplicant in the console.

---

