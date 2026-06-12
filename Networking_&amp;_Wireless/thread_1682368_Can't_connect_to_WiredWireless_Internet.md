---
title: "Can't connect to Wired/Wireless Internet"
date: 2011-02-05
forum: Networking &amp; Wireless
---

### Post by decirue on 2011-02-05
Hi everyone,

   I've installed ubuntu for the first time today and am having trouble with the internet connection.  I cannot connect wired or wireless, the computer doesn't pick it up.  It's fine on my Windows 7 though.  I've read through some previous threads about similar problems, but I found it either too confusing, not the same version, or not the exact same problem.  The problem is with my HP laptop and if you're curious I am posting from my other computer.

Here are some details about my laptop:

When running lspci -v:
```
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
    Subsystem: Hewlett-Packard Company Device 3055
    Flags: bus master, 66MHz, medium devsel, latency 64

00:02.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Graphics Port 0) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00009000-00009fff
    Memory behind bridge: bfe00000-bfefffff
    Prefetchable memory behind bridge: 00000000c0000000-00000000dfffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=07, sec-latency=0
    Memory behind bridge: f0200000-f02fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=08, subordinate=0d, sec-latency=0
    I/O behind bridge: 0000a000-0000afff
    Memory behind bridge: be000000-be0fffff
    Prefetchable memory behind bridge: 00000000f0400000-00000000f04fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA (prog-if 01 [AHCI 1.0])
    Subsystem: Hewlett-Packard Company Device 3055
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 21
    I/O ports at 8440 [size=8]
    I/O ports at 8434 [size=4]
    I/O ports at 8438 [size=8]
    I/O ports at 8430 [size=4]
    I/O ports at 8400 [size=16]
    Memory at f0309000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0) (prog-if 10 [OHCI])
    Subsystem: Hewlett-Packard Company Device 3055
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
    Memory at f0304000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1) (prog-if 10 [OHCI])
    Subsystem: Hewlett-Packard Company Device 3055
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at f0305000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2) (prog-if 10 [OHCI])
    Subsystem: Hewlett-Packard Company Device 3055
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at f0306000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3) (prog-if 10 [OHCI])
    Subsystem: Hewlett-Packard Company Device 3055
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at f0307000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4) (prog-if 10 [OHCI])
    Subsystem: Hewlett-Packard Company Device 3055
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at f0308000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI) (prog-if 20 [EHCI])
    Subsystem: Hewlett-Packard Company Device 3055
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
    Memory at f0309400 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
    Subsystem: Hewlett-Packard Company Device 3055
    Flags: 66MHz, medium devsel
    I/O ports at 8410 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: piix4_smbus
    Kernel modules: i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc SB600 IDE (prog-if 80 [Master])
    Subsystem: Hewlett-Packard Company Device 3055
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 8420 [size=16]
    Kernel driver in use: pata_atiixp
    Kernel modules: pata_atiixp

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
    Subsystem: Hewlett-Packard Company Device 3055
    Flags: bus master, slow devsel, latency 64, IRQ 16
    Memory at f0300000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
    Subsystem: Hewlett-Packard Company Device 3055
    Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01 [Subtractive decode])
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=0e, subordinate=13, sec-latency=64

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
    Flags: fast devsel
    Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
    Flags: fast devsel
    Kernel modules: amd64_edac_mod

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
    Flags: fast devsel
    Capabilities: <access denied>
    Kernel driver in use: k8temp
    Kernel modules: k8temp

01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3400 Series (prog-if 00 [VGA controller])
    Subsystem: Hewlett-Packard Company Device 3055
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at c0000000 (32-bit, prefetchable) [size=512M]
    I/O ports at 9000 [size=256]
    Memory at bfef0000 (32-bit, non-prefetchable) [size=64K]
    [virtual] Expansion ROM at bfe00000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: radeon
    Kernel modules: radeon

01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]
    Subsystem: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at bfeec000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

02:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
    Subsystem: Hewlett-Packard Company Device 1509
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at f0200000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb

08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
    Subsystem: Hewlett-Packard Company Device 3055
    Flags: bus master, fast devsel, latency 0, IRQ 43
    I/O ports at a000 [size=256]
    Memory at f0410000 (64-bit, prefetchable) [size=4K]
    Memory at f0400000 (64-bit, prefetchable) [size=64K]
    [virtual] Expansion ROM at f0420000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169
```When running ifconfig -a:
```
eth0      Link encap:Ethernet  HWaddr 00:21:cc:38:91:d5  
          inet6 addr: fe80::221:ccff:fe38:91d5/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2278 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:142612 (142.6 KB)  TX bytes:8925 (8.9 KB)
          Interrupt:43 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:244 errors:0 dropped:0 overruns:0 frame:0
          TX packets:244 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:19176 (19.1 KB)  TX bytes:19176 (19.1 KB)
```When running iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.
```When running uname -r:
```
2.6.35-22-generic
```Thank you for your time and effort :)

---

### Post by decirue on 2011-02-06
Suggestions anyone?

---

### Post by chili555 on 2011-02-06
Let's get the wired working first; it will make getting wireless going a lot easier. Please be sure the ethernet cable is attached and then run:```
sudo lshw -C network
```Does the ethernet card show 'link=no' even though the cable is attached? Then see: [http://ubuntuforums.org/showthread.php?t=53844](http://ubuntuforums.org/showthread.php?t=53844)> As of 27 May 2007, in kernel 2.6.21.3, you may experience the issues with the r8169 driver if you dual boot Windows on some systems. Windows by defaults disables the NIC at Windows shutdown time in order to disable Wake-On-Lan, and this NIC will remain disabled until the next time Windows turns it onAfter the ethernet is working, go to System > Administration > Additional Drivers and activate your Broadcom wireless.

Post back if you need additional guidance.

---

### Post by decirue on 2011-02-06
Thanks for the help.  Now when I connected my ethernet cable, I was able to connect wired, which is odd since it wouldn't before.  Anyway now there's a new problem.  I opened additional drivers and it tells me "No proprietary drivers are in use on this system."  In addition, when I update using the update manager, it takes a really long time to load after I click authenticate.  Then when it's done loading, the checkboxes remain and what I thought was just updated, remains un-updated.

---

### Post by decirue on 2011-02-06
> **decirue said:**
> Thanks for the help.  Now when I connected my ethernet cable, I was able to connect wired, which is odd since it wouldn't before.  Anyway now there's a new problem.  I opened additional drivers and it tells me "No proprietary drivers are in use on this system."  In addition, when I update using the update manager, it takes a really long time to load after I click authenticate.  Then when it's done loading, the checkboxes remain and what I thought was just updated, remains un-updated.

Scratch that.  Now the drivers showed up after a few times- the update problem however still remains.

---

### Post by chili555 on 2011-02-06
Let's troubleshoot the wired connection. Please run and post:```
ifconfig eth0
ping -c3 www.google.com
sudo ethtool eth0
```Let's also see what's happening with your wireless:```
dmesg | grep b43
```Thanks.

---

### Post by decirue on 2011-02-06
ifconfig eth0 gives me
```
eth0      Link encap:Ethernet  HWaddr 00:21:cc:38:91:d5  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:ccff:fe38:91d5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24798 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18384 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:30401014 (30.4 MB)  TX bytes:2089793 (2.0 MB)
          Interrupt:43 Base address:0x8000 

```

ping -c3 [www.google.com](www.google.com) gives me
```
PING www.l.google.com (74.125.127.103) 56(84) bytes of data.
64 bytes from pz-in-f103.1e100.net (74.125.127.103): icmp_req=1 ttl=53 time=19.9 ms
64 bytes from pz-in-f103.1e100.net (74.125.127.103): icmp_req=2 ttl=53 time=20.1 ms
64 bytes from pz-in-f103.1e100.net (74.125.127.103): icmp_req=3 ttl=53 time=20.7 ms

--- www.l.google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 19.929/20.256/20.726/0.340 ms

```

sudo ethtool eth0 gives me
```
sudo: ethtool: command not found

```

The dmesg command gave me
```

[    1.251720] b43-pci-bridge 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.251732] b43-pci-bridge 0000:02:00.0: setting latency timer to 64
[   17.690386] b43-phy0: Broadcom 4322 WLAN found (core revision 16)
[   17.790191] b43-phy0 ERROR: FOUND UNSUPPORTED PHY (Analog 8, Type 4, Revision 4)
[   17.790307] b43: probe of ssb0:0 failed with error -95

```

Also, the authenticate is still running for updating my drivers so I don't think wireless works yet.  Wired is still OK.  I also just got a message saying the Jockey backend has crashed (message for Additional Drivers update).

---

### Post by chili555 on 2011-02-06
Let's wait until your updates run and install. Your wired appears to be working perfectly. When the updates are done. please run:```
lspci -nn | grep -i 14e4
```If the pci.id for your Broadcom is [COLOR="Red"]14E4:432C[/COLOR] Broadcom Corporation BCM4322 802.11b/g/n, then b43 and ssb are incorrect. You'll need to do:```
sudo apt-get install bcmwl-kernel-source
```*wl* is the correct driver for your device. If the pci.id is different, post back and we'll get it going.

---

### Post by piymon on 2011-02-06
Sorry but i have a similar problem with my hp laptop. i just installed ubuntu 9.04.
my laptop model no. is  hp g42-460tu.
my wireless connectivity is not working thou the wired one is working fine. i m new to ubuntu so need help id that. i hope no one mind me posting on a already posted thread. i m not that known to the rules of this forum so apologies in advance. just tel me what u want to know of my laptop or os and help me please. also the inbuilt sound is not working but if i connect to external speaker or headset its working fine. help me

---

### Post by chili555 on 2011-02-06
> **piymon said:**
> Sorry but i have a similar problem with my hp laptop. i just installed ubuntu 9.04.
my laptop model no. is  hp g42-460tu.
my wireless connectivity is not working thou the wired one is working fine. i m new to ubuntu so need help id that. i hope no one mind me posting on a already posted thread. i m not that known to the rules of this forum so apologies in advance. just tel me what u want to know of my laptop or os and help me please. also the inbuilt sound is not working but if i connect to external speaker or headset its working fine. help meIt's considered impolite to join another thread unless your hardware is exactly the same. Please run:```
lspci -nn
```If your wireless device is not a Broadcom BCM4322, post a new thread and quote what it is. If it is the same, simply watch this thread for instructions.

---

### Post by decirue on 2011-02-06
> **chili555 said:**
> Let's wait until your updates run and install. Your wired appears to be working perfectly. When the updates are done. please run:```
lspci -nn | grep -i 14e4
```If the pci.id for your Broadcom is [COLOR=Red]14E4:432C[/COLOR] Broadcom Corporation BCM4322 802.11b/g/n, then b43 and ssb are incorrect. You'll need to do:```
sudo apt-get install bcmwl-kernel-source
```*wl* is the correct driver for your device. If the pci.id is different, post back and we'll get it going.

Running lspci -nn I get
```
02:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:4ted32b] (rev 01)

```

By the way, my Update Manager still isn't working properly so I didn't really get a chance to update anything.  Every time I click "authenticate", I wait around 5 minutes and nothing really happens.  Update Manager ends up where it started in the first place.

---

### Post by piymon on 2011-02-06
sorry but i cant find the lnk to create a new thread
please post me the link and th info required is

piyush@piyush-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Device [8086:0044] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation Device [8086:0046] (rev 02)
00:16.0 Communication controller [0780]: Intel Corporation Ibex Peak HECI Controller [8086:3b64] (rev 06)
00:1a.0 USB Controller [0c03]: Intel Corporation Ibex Peak USB2 Enhanced Host Controller [8086:3b3c] (rev 05)
00:1b.0 Audio device [0403]: Intel Corporation Ibex Peak High Definition Audio [8086:3b56] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation Ibex Peak PCI Express Root Port 1 [8086:3b42] (rev 05)
00:1c.1 PCI bridge [0604]: Intel Corporation Ibex Peak PCI Express Root Port 2 [8086:3b44] (rev 05)
00:1d.0 USB Controller [0c03]: Intel Corporation Ibex Peak USB2 Enhanced Host Controller [8086:3b34] (rev 05)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a5)
00:1f.0 ISA bridge [0601]: Intel Corporation Ibex Peak LPC Interface Controller [8086:3b09] (rev 05)
00:1f.2 SATA controller [0106]: Intel Corporation Ibex Peak 4 port SATA AHCI Controller [8086:3b29] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation Ibex Peak SMBus Controller [8086:3b30] (rev 05)
00:1f.6 Signal processing controller [1180]: Intel Corporation Ibex Peak Thermal Subsystem [8086:3b32] (rev 05)
02:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4727] (rev 01)
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
ff:00.0 Host bridge [0600]: Intel Corporation Device [8086:2c62] (rev 02)
ff:00.1 Host bridge [0600]: Intel Corporation Device [8086:2d01] (rev 02)
ff:02.0 Host bridge [0600]: Intel Corporation Device [8086:2d10] (rev 02)
ff:02.1 Host bridge [0600]: Intel Corporation Device [8086:2d11] (rev 02)
ff:02.2 Host bridge [0600]: Intel Corporation Device [8086:2d12] (rev 02)
ff:02.3 Host bridge [0600]: Intel Corporation Device [8086:2d13] (rev 02)
piyush@piyush-laptop:~$

---

### Post by sammiev on 2011-02-06
> **decirue said:**
> By the way, my Update Manager still isn't working properly so I didn't really get a chance to update anything.  Every time I click "authenticate", I wait around 5 minutes and nothing really happens.  Update Manager ends up where it started in the first place.

After entering in your password, just press "enter" and not "authenticate" GL :)

---

### Post by sammiev on 2011-02-06
piymon go to Absolute Beginner Talk and press the "New Thread" button. GL :)

---

### Post by piymon on 2011-02-06
sorry but still cant create. its saying not yet activated or administrative suspended from posting
help me
i tried 2 check my mail but found nothing in it

---

### Post by decirue on 2011-02-06
Alright, the "enter" thing worked.  I now have Broadcom B43 wireless driver enabled and am currently installing updates.  I'll wait until the updates are done to test if the wireless actually works now.  Thanks.

---

### Post by chili555 on 2011-02-06
> sorry but i cant find the lnk to create a new threadRight at the top, Forum Tools > Post a New Thread.

---

### Post by piymon on 2011-02-07
not able 2 create thread showing
> **piymon**, you do not have permission to access this page. This could be due to one of several reasons:
  
[LIST=1]
[*]Your user account may not have sufficient privileges to access this page. Are you trying to edit someone else's post, access administrative features or some other privileged system?
[*]If you are trying to post, the administrator may have disabled your account, or it may be awaiting activation.
[/LIST]


---

### Post by chili555 on 2011-02-07
Are you at the top of the forum itself and ***not*** this thread? Please see attached.

---

### Post by piymon on 2011-02-07
finally able 2 create the thread link is
[http://ubuntuforums.org/showthread.php?p=10435982#post10435982](http://ubuntuforums.org/showthread.php?p=10435982#post10435982)

---

### Post by sammiev on 2011-02-07
> **decirue said:**
> Alright, the "enter" thing worked.  I now have Broadcom B43 wireless driver enabled and am currently installing updates.  I'll wait until the updates are done to test if the wireless actually works now.  Thanks.

Glad I as able to help. Now did the updates work for you? GL :)

---

