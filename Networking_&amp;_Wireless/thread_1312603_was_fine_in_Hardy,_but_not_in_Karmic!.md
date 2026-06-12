---
title: "was fine in Hardy, but not in Karmic!"
date: 2009-11-03
forum: Networking &amp; Wireless
---

### Post by leorolla on 2009-11-03
Wow, more than 1,500, ops, 5,200, ops, 6,300, ops, 7,400 views!

Let me write the solution here, I hope it is useful.

Thanks t0mppa for his help!

_____________________________________________

I installed Karmic. Wireless was not working.

My wireless driver:
```

lspci -vnn | grep 14e4

```gives
 ```

 01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)

```if yours is the same, it should work. If it isn't you can try.

[B]Solution:
[/B] 
1. Get wired internet access

2. System -> Administration -> Update Manager

3. Check

4. Install Updates

5. Reboot

6. System -> Administration -> Hardware Drivers

There were two:
Broadcom B43
Broadcom STA wireless driver

7. Choose Broadcom STA wireless driver, Activate.

8. Reboot

9. System -> Administration -> Hardware Drivers

Confirm that B43 disappeared.

Wireless works fine.
[B]
Warning[/B]:

You should NOT have any package named like linux-backports-modules-karmic* installed. If you have, remove it.

_____________________________________________

Hi,

I have an Acer Aspire One 150.

When I install Ubuntu 8.04 with wubi, wifi works out of the box (I cannot turn it on and off etc but it works), so I can do all the updates and tweaks with wireless network.

When I install Ubuntu 9.10 with wubi, wifi is just OFF !

Anyone know how to fix it?

Thanks!

---

### Post by t0mppa on 2009-11-03
You're going to have to provide a bit more information before anyone can suggest what to do. So, why don't you open up a terminal, run **lshw -C network** and post the results here.

---

### Post by leorolla on 2009-11-03
sudo lshw -C network > foo.txt


Form a CD trial version. Then copied foo.txt to the HD.

Here's Foo.txt:

  *-network
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:16 memory:55100000-55103fff
  *-network
       description: Ethernet interface
       product: Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: b0
       serial: 00:23:5a:57:47:ed
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI firmware=L1e latency=0 link=no multicast=yes port=twisted pair
       resources: irq:28 memory:53000000-5303ffff ioport:1000(size=128)


Thank you!!!

---

### Post by t0mppa on 2009-11-04
Ok, you have the b43 driver associated with the wireless interface. It is dependent on firmware, that because of it being proprietary does not get automatically installed, for the wireless to work though.

To get this firmware installed, you can install the b43-fwcutter package and answer yes when it asks whether to fetch and install the firmware, this requires a working Internet connection (through your wired card for instance) though. If you can't get the machine connected, you'll have to follow the instructions [here]("http://linuxwireless.org/en/users/Drivers/b43#fw-b43-new") for manually installing the fwcutter and firmware (note that the wget lines are simply downloads, which you'll have to do on another computer and then copy the files over).

An alternative option is to go to System / Administration / Hardware Drivers and enable the Broadcom STA through there to use it instead of b43.

---

### Post by leorolla on 2009-11-04
> An alternative option is to go to System / Administration / Hardware Drivers and enable the Broadcom STA through there to use it instead of b43.

I was happy to try the simpler solution to get started with network connection, but at Hardware Drivers it just says I don't have any proprieatry driver installed.

Using the other method, I must install both fwcutter and firmware?

Thank you very much.

---

### Post by Krudtugle on 2009-11-04
I have the same problem with wireless after upgrading to 9.10, like so many other.

My printout of sudo lshw -C network reads:
```

  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:09:02.0
       logical name: eth0
       version: 10
       serial: 00:16:36:27:4d:bd
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.2.5 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:21 ioport:a000(size=256) memory:c0210000-c02100ff
  *-network:1
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 4
       bus info: pci@0000:09:04.0
       logical name: wifi0
       version: 01
       serial: 00:16:e3:01:d9:27
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=96 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11g
       resources: irq:22 memory:c0200000-c020ffff
```

Does that mean that I use ath-pci driver or that Ubuntu *tries* to use it?

---

### Post by leorolla on 2009-11-04
> **t0mppa said:**
> Ok, you have the b43 driver associated with the wireless interface. It is dependent on firmware, that because of it being proprietary does not get automatically installed, for the wireless to work though.

To get this firmware installed, you can install the b43-fwcutter package and answer yes when it asks whether to fetch and install the firmware, this requires a working Internet connection (through your wired card for instance) though. If you can't get the machine connected, you'll have to follow the instructions [here]("http://linuxwireless.org/en/users/Drivers/b43#fw-b43-new") for manually installing the fwcutter and firmware (note that the wget lines are simply downloads, which you'll have to do on another computer and then copy the files over).

An alternative option is to go to System / Administration / Hardware Drivers and enable the Broadcom STA through there to use it instead of b43.

Hi!

I followed the instructions in the link but nothing happened.
I rebooted and still nothing changes.
Now there is a file b43 at /lib/firmware

Thank you again.

---

### Post by david.m.bailey on 2009-11-04
What if you go to this screen and there is no driver listed to enable?  I am a fresh install (dual operating systems- Win XP and now Ubuntu).

---

### Post by t0mppa on 2009-11-04
> **leorolla said:**
> Using the other method, I must install both fwcutter and firmware?

Thank you very much.

Yes, the fwcutter "cuts" the fw (firmware) for you, so to speak.

> **leorolla said:**
> I followed the instructions in the link but nothing happened.

Can you post the output of **dmesg | grep b43** from the terminal? It should complain, if the firmware is incorrectly installed, if it isn't the driver should be working.

> **Krudtugle said:**
> Does that mean that I use ath-pci driver or that Ubuntu *tries* to use it?

Pretty much both. But if you want help with it, please create your own thread for it, since it's a different card. That way this one doesn't get side tracked and both of you will get better help.

---

### Post by t0mppa on 2009-11-04
> **david.m.bailey said:**
> What if you go to this screen and there is no driver listed to enable?  I am a fresh install (dual operating systems- Win XP and now Ubuntu).

The STA supports BCM4311, BCM4312, BCM4321 or BCM4322 (some users claim that BCM4328 also works, but it's not official) wireless chips and the alternative way to enable it is installing the *bcmwl-kernel-source* package (either with Synaptic or running **sudo apt-get install bcmwl-kernel-source** from terminal).

---

### Post by leorolla on 2009-11-05
Recalling:

```
wget http://bu3sch.de/b43/fwcutter/b43-fwcutter-012.tar.bz2
tar xjf b43-fwcutter-012.tar.bz2
cd b43-fwcutter-012
make
cd ..

``````
export FIRMWARE_INSTALL_DIR="/lib/firmware"
wget http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2
tar xjf broadcom-wl-4.150.10.5.tar.bz2
cd broadcom-wl-4.150.10.5/driver
sudo ../../b43-fwcutter-012/b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta_mimo.o

```I rebooted and still nothing changes.


```
dmesg | grep b43
```gives

```
[    2.983800] b43-pci-bridge 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.983824] b43-pci-bridge 0000:01:00.0: setting latency timer to 64
[    9.355052] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[    9.396369] b43-phy0 ERROR: FOUND UNSUPPORTED PHY (Analog 6, Type 5, Revision 1)
[    9.396476] b43: probe of ssb0:0 failed with error -95

```Thanks again!

---

### Post by t0mppa on 2009-11-05
Ok, that means the b43 driver doesn't support the revision of the BCM4312 that you have. Just to clear things up, run **lspci -vnn | grep 14e4** and see if your chips PCI-ID is [14e4:4315], as that's the lower power version of BCM4312, which isn't yet supported.

That means you'll have to use the STA to get your card working. See [this thread]("http://ubuntuforums.org/showthread.php?t=1308533") for instructions how to enable it, since it isn't found on the Hardware Drivers.

---

### Post by leorolla on 2009-11-05
> **t0mppa said:**
> Ok, that means the b43 driver doesn't support the revision of the BCM4312 that you have. Just to clear things up, run **lspci -vnn | grep 14e4** and see if your chips PCI-ID is [14e4:4315], as that's the lower power version of BCM4312, which isn't yet supported.

That means you'll have to use the STA to get your card working. See [this thread]("http://ubuntuforums.org/showthread.php?t=1308533") for instructions how to enable it, since it isn't found on the Hardware Drivers.

```

leorolla@ubuntu:~$ lspci -vnn | grep 14e4
01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
leorolla@ubuntu:~$
```

I guess it makes no difference, but for the information: I did not run this command in Karmic, but in another installation with Jaunty.

---

### Post by t0mppa on 2009-11-06
Right, the hardware doesn't change, no matter what OS you install on the computer. Had forgotten that revision isn't supported, so sorry about the detour. Anyway, did you try installing the *bcmwl-kernel-source* package or did you just go back to using Jaunty instead?

---

### Post by leorolla on 2009-11-06
I have Hardy, Karmic and Jaunty installed. But I love Karmic much better.

When I get wired connection I will try *bcmwl-kernel-sourc* in Karmic.

Wubi really is a great thing! When I get Karmic running perfectly I will do a true installation.

---

### Post by Tony Ricena on 2009-11-06
The Broadcam firmware/driver is on your ubuntu 9.10 cd!  I had the same problem with my laptop, but looked on the internet and found the solution.  

Goto your Software sources and check the Installable from cd/dvd, put your CD/DVD in

Goto the Synaptic Package Manager, and search for bcmwl-kernel-source.. check and install.. restart computer and boom it works

---

### Post by CoolDreamZ on 2009-11-06
I have a Lenovo S10 with Broadcomm wireless which also worked ok with the previous version of Ubuntu (9.04). The failure of 9.10 to invite the user to use a restricted driver is a serious regression.

Fortunately your fix (install from 9.10 CD) worked a treat (if you have a USB CD drive on your netbook that is!)

---

### Post by CoolDreamZ on 2009-11-08
As this is such a serious issue I checked the release notes and this problem would seem to be an example of a known bug with the restricted hardware driver manager (Jockey) discovered close to release and not fixed in time.

See here for further details: [462704]("https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/462704")

---

### Post by bjaz on 2009-11-08
I don't know if this is related, but I'm not managing to get wirless in ubuntu 9.1

previous version installed was xubuntu, and this was updated to 9.1 and still works.

yet for various reason, including other bugs in xubuntu (sound, touchpad), we would like to focus on the ubuntu install from now on an discard the xubuntu.

computer is an old japanese sony VAIO FS21B, with no built in wireless, using a PCI card adapter.

here's some info on  ifconfig of the ubuntu install with no wireless :

kayo@kayo-ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
06:03.0 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
06:03.2 FireWire (IEEE 1394): Texas Instruments PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller
06:03.3 Mass storage controller: Texas Instruments PCI7420/7620 Combo CardBus, 1394a-2000 OHCI and SD/MS-Pro Controller
06:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 03)
kayo@kayo-ubuntu:~$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
kayo@kayo-ubuntu:~$ lshw -class network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:06:08.0
       logical name: eth0
       version: 03
       serial: 00:01:4a:60:fa:c0
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI firmware=N/A latency=66 maxlatency=56 mingnt=8 multicast=yes
       resources: irq:20 memory:b0106000-b0106fff ioport:2000(size=64)
kayo@kayo-ubuntu:~$ uname -a
Linux kayo-ubuntu 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux
kayo@kayo-ubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 9.10
Release:    9.10
Codename:    karmic
kayo@kayo-ubuntu:~$ 

kayo@kayo-ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
06:03.0 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
06:03.2 FireWire (IEEE 1394): Texas Instruments PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller
06:03.3 Mass storage controller: Texas Instruments PCI7420/7620 Combo CardBus, 1394a-2000 OHCI and SD/MS-Pro Controller
06:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 03)
kayo@kayo-ubuntu:~$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
kayo@kayo-ubuntu:~$ lshw -class network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:06:08.0
       logical name: eth0
       version: 03
       serial: 00:01:4a:60:fa:c0
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI firmware=N/A latency=66 maxlatency=56 mingnt=8 multicast=yes
       resources: irq:20 memory:b0106000-b0106fff ioport:2000(size=64)
kayo@kayo-ubuntu:~$ uname -a
Linux kayo-ubuntu 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux
kayo@kayo-ubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 9.10
Release:    9.10
Codename:    karmic
kayo@kayo-ubuntu:~$

[LEFT]eth0      Link encap:Ethernet  HWaddr 00:01:4a:60:fa:c0  [/LEFT]
    [LEFT]          UP BROADCAST MULTICAST  MTU:1500  Metric:1[/LEFT]
    [LEFT]          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0[/LEFT]
    [LEFT]          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0[/LEFT]
    [LEFT]          collisions:0 lg file transmission:1000 [/LEFT]
    [LEFT]          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)[/LEFT]
    
    [LEFT]lo        Link encap:Boucle locale  [/LEFT]
    [LEFT]          inet adr:127.0.0.1  Masque:255.0.0.0[/LEFT]
    [LEFT]          adr inet6: ::1/128 Scope:Hôte[/LEFT]
    [LEFT]          UP LOOPBACK RUNNING  MTU:16436  Metric:1[/LEFT]
    [LEFT]          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0[/LEFT]
    [LEFT]          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0[/LEFT]
    [LEFT]          collisions:0 lg file transmission:0 [/LEFT]
    [LEFT]          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)[/LEFT]
    
    [LEFT]kayo@kayo-ubuntu:~$

and here's the ifconfig of the xubuntu 9.1 with working wireless internet, on the samemachine :

[LEFT]eth0      Link encap:Ethernet  HWaddr 00:01:4a:60:fa:c0  [/LEFT]
    [LEFT]          UP BROADCAST MULTICAST  MTU:1500  Metric:1[/LEFT]
    [LEFT]          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0[/LEFT]
    [LEFT]          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0[/LEFT]
    [LEFT]          collisions:0 lg file transmission:1000 [/LEFT]
    [LEFT]          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)[/LEFT]
    
    [LEFT]lo        Link encap:Boucle locale  [/LEFT]
    [LEFT]          inet adr:127.0.0.1  Masque:255.0.0.0[/LEFT]
    [LEFT]          adr inet6: ::1/128 Scope:Hôte[/LEFT]
    [LEFT]          UP LOOPBACK RUNNING  MTU:16436  Metric:1[/LEFT]
    [LEFT]          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0[/LEFT]
    [LEFT]          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0[/LEFT]
    [LEFT]          collisions:0 lg file transmission:0 [/LEFT]
    [LEFT]          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)[/LEFT]
    
    [LEFT]kayo@kayo-ubuntu:~$

-------------



can anyone help ? I have to figure out wether this is manageable with my newbie skills, or wether I should downgrade back. this is a little urgent as it's my wife's computer and she needs to have it functional for when i'm away.

thanks a lot for your precious help

b
[/LEFT]

[/LEFT]

---

### Post by leorolla on 2009-11-09
> **t0mppa said:**
> Right, the hardware doesn't change, no matter what OS you install on the computer. Had forgotten that revision isn't supported, so sorry about the detour. Anyway, did you try installing the *bcmwl-kernel-source* package or did you just go back to using Jaunty instead?

Once I hade wired connection, I did

sudo apt-get update
sudo apt-get upgrade

Reboot

System -> Administration -> Hardware Drivers

There were two:
Broadcom B43 -> didn't work
Broadcom STA wireless driver -> works!

After reboot, I have wireless working fine and B43 disappeared.

Thank you very much.

---

### Post by scoopy on 2009-11-23
Hey there friends.  I'm having issues too with my Compaq v6000.  The Broadcom drivers isn't showing up in "Hardware Drivers".  I've install fwcutter, modaliases, bcmwl-kernel-source restarted still nothing in "Hardware Drivers"

Some more info:

luke@luke-laptop:~$ lspci
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
00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce Go 6150] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)


luke@luke-laptop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


lshw -class network
I get nothing for this?

luke@luke-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.




I'm pretty new to all this so please dumb down your advice for a dummy.

Thanks

---

### Post by leorolla on 2009-11-24
Did you try

```
sudo apt-get install bcm43xx-fwcutter

```
?

---

### Post by t0mppa on 2009-11-24
@scoopy: I cannot see a Broadcom device on the lspci output, thus if you have a wireless PCI card with a Broadcom chip in it, it's not getting recognized. The only reference to wireless is the:```
Bus 002 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
```

[QUOTE=b43 driver page]If you have an USB device with Broadcom chip, please try the RNDIS driver. The b43/b43legacy driver will never support this device.[/QUOTE]

Also, the STA only supports a few PCI cards, no USB either. Thus you'll have to use NDISwrapper for it, if it indeed has a Broadcom chip to begin with. I've never dealt with USB wireless devices, so can't really help you much with that.

To get proper help, you really should start your own thread, so people can see you actually have a problem. Posting at the end of a long thread that's marked solved is likely to get very few or no responses from people who didn't participate in the thread earlier.

---

### Post by scoopy on 2009-11-27
Thanks  for your reply.  Good advice.

Scoopy

---

### Post by CoolDreamZ on 2009-11-28
I have seen several threads on this issue and I am pointing people here for the solution as it seems be a common problem with 9.10.

Do you think it might be a good idea to change the title of this thread to something like "Broadcomm wireless problem on 9.10"? (if possible!)

---

### Post by leorolla on 2009-11-28
How can I change the title of a thread?

---

### Post by CoolDreamZ on 2009-11-28
I am not sure if you can, had a quick look around and can't see anything on the Forum FAQ or menu options. Sorry! :?

---

### Post by ncdad2004 on 2009-12-06
Hello. I'm glad I found this forum. Hope someone can help me as this is getting very frustrating. I installed 9.10 on my son's Dell D600 laptop with a Broadcom 4306 chipset and everything seems to work fine except for the wireless (wired works fine).

I'm a noob but have tried to do my homework and have searched the net to find the 9.10 bug with broadcom chips and have tried just about every suggested fix out there, including the one posted here.  I'm sooooo close to getting the wireless working and think I just need someone to help push me that last little bit over the top. I can see other wireless networks, it tries to connect to my wireless but eventually gives up.

Hope this info helps.

nicholas@nicklaptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 02)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)
02:01.0 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:01.1 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

nicholas@nicklaptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5705M Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:11:43:42:54:a2
       width: 64 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.99 firmware=5705-v3.16 ip=xxx latency=32 mingnt=64 multicast=yes
       resources: irq:11 memory:faff0000-faffffff
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32
       resources: irq:5 memory:fafee000-fafeffff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:0b:7d:13:84:f7
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

nicholas@nicklaptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  Mode:Managed  Frequency:2.447 GHz  
          Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

nicholas@nicklaptop:~$ lsmod
Module                  Size  Used by
isofs                  31620  1 
udf                    80900  0 
crc_itu_t               1852  1 udf
binfmt_misc             8356  1 
snd_intel8x0           30168  2 
arc4                    1660  2 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
ecb                     2524  2 
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
b43                   122136  0 
ssb                    35300  1 b43
snd_seq_dummy           2656  0 
pcmcia                 36808  0 
mac80211              181236  1 b43
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
cfg80211               93052  2 b43,mac80211
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
led_class               4096  1 b43
yenta_socket           24200  4 
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
rsrc_nonstatic         11644  1 yenta_socket
snd_timer              22276  2 snd_pcm,snd_seq
pcmcia_core            35792  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ppdev                   6688  0 
snd                    59204  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport_pc             31940  1 
iptable_filter          3100  0 
soundcore               7264  1 snd
psmouse                56180  0 
dell_wmi                2564  0 
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
shpchp                 32272  0 
serio_raw               5280  0 
dcdbas                  7292  0 
ip_tables              11692  1 iptable_filter
joydev                 10272  0 
x_tables               16544  1 ip_tables
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp
usbhid                 38208  0 
tg3                   109600  0 
video                  19380  0 
output                  2780  1 video
radeon                636000  2 
ttm                    36212  1 radeon
drm                   159584  4 radeon,ttm
i2c_algo_bit            5760  1 radeon
intel_agp              27484  1 
agpgart                34988  3 ttm,drm,intel_agp

I've tried downloading the broadcom drivers and the b43-fwcutter.
I've tried downloading the bcmwl-kernel-source using the synaptic package manager.
I've tried using the instructions in this thread. The only hardware driver that shows up is the Broadcom B43 wireless driver. (the STA one doesn't show).

Can anyone help me go the last few inches (or cm..) and get this thing working?
Let me know if you need more info.
Thanks!

---

### Post by northd_tech on 2009-12-06
I believe that Broadcom 4306 wireless should need a similar fix to the Broadcom 4311 and 4312 wireless.  See these "solved" threads here:

[http://ubuntuforums.org/showthread.php?t=1327450](http://ubuntuforums.org/showthread.php?t=1327450)

[http://ubuntuforums.org/showthread.php?t=1336676](http://ubuntuforums.org/showthread.php?t=1336676)

---

### Post by ncdad2004 on 2009-12-07
> **northd_tech said:**
> I believe that Broadcom 4306 wireless should need a similar fix to the Broadcom 4311 and 4312 wireless.  See these "solved" threads here:

[http://ubuntuforums.org/showthread.php?t=1327450](http://ubuntuforums.org/showthread.php?t=1327450)

[http://ubuntuforums.org/showthread.php?t=1336676](http://ubuntuforums.org/showthread.php?t=1336676)

northd-tech - thanks for your quick reply. I spent the last few hours trying the various fixes from your links but still no luck. :(

I dl'ed the 32 bit driver from broadcom and followed the instructions in the readme. I blacklisted b43 and ssb but when I rebooted there they were again and still no STA driver, but at least the wl driver showed up.

Here's an excerpt from the blacklist.conf file and my lsmod output after I rebooted.

/snip
# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist ssb
blacklist b43
/end snip

nicholas@nicklaptop:~$ lsmod
Module                  Size  Used by
binfmt_misc             8356  1 
snd_intel8x0           30168  2 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
pcmcia                 36808  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
wl                   1272936  0 
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
lib80211                6432  1 wl
iptable_filter          3100  0 
arc4                    1660  2 
snd_timer              22276  2 snd_pcm,snd_seq
yenta_socket           24200  4 
ip_tables              11692  1 iptable_filter
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
rsrc_nonstatic         11644  1 yenta_socket
ecb                     2524  2 
x_tables               16544  1 ip_tables
snd                    59204  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_core            35792  3 pcmcia,yenta_socket,rsrc_nonstatic
b43                   122136  0 
ssb                    35300  1 b43
mac80211              181236  1 b43
soundcore               7264  1 snd
cfg80211               93052  2 b43,mac80211
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
dell_wmi                2564  0 
led_class               4096  1 b43
joydev                 10272  0 
ppdev                   6688  0 
psmouse                56180  0 
dcdbas                  7292  0 
shpchp                 32272  0 
serio_raw               5280  0 
parport_pc             31940  1 
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp
usbhid                 38208  0 
tg3                   109600  0 
video                  19380  0 
output                  2780  1 video
radeon                636000  2 
ttm                    36212  1 radeon
drm                   159584  4 radeon,ttm
i2c_algo_bit            5760  1 radeon
intel_agp              27484  1 
agpgart                34988  3 ttm,drm,intel_agp

I even tried these instructions again too, but again all I ever get is the B43 wireless driver in the hardware manager window (not active). 

> sudo apt-get update
sudo apt-get upgrade

Reboot

System -> Administration -> Hardware Drivers

There were two:
Broadcom B43 -> didn't work
Broadcom STA wireless driver -> works!

After reboot, I have wireless working fine and B43 disappeared.It seems I just can't get the driver to load correctly, yet I'm seeing other wireless networks. One other thing, I use a key code for my wireless so in Win XP I enter a hex(?) password, but it doesn't fit in Ubuntu so I type in the original ascii equivalent - is that correct? Hope it's not something stupid like that...

Any other suggestions?
Thanks again for your help.

---

### Post by ncdad2004 on 2009-12-07
Aww crap... [IMG]http://ubuntuforums.org/images/icons/icon8.gif[/IMG]

I just entered my wireless password in hex and now it works fine!
When I tried it in hex before, it went to the end of the text box and I thought it wasn't accepting the rest of the password as the cursor and dots didn't move so I stopped typing and switched to ascii. (yeah, I'm a noob). Just for the heck of it, I did it again and kept on typing the whole thing out anyway and whaddya you know, the darned thing worked.

However, it's still a mystery to me how the wireless is working at all since the hardware driver window shows only the B43 wireless driver and it's not active. Ah well, it works, so onward and upward. 

Sorry for the false alarm. I feel like such a moron...  [IMG]http://ubuntuforums.org/images/icons/icon11.gif[/IMG]

---

### Post by hiloguy on 2010-01-16
After not being able to get connected with a fresh 9.10 install on my Dell D620, I followed the above advice: sudo apt-get update and
sudo apt-get upgrade and was instantly connected!  But . . . after shutting down and restarting, I get the connected message and the signal is excellent, but now I can't get in the Internet.  Connecting a cable works.

What am I missing here?

Thanks!

---

### Post by leorolla on 2010-01-16
Recently Ubuntu left us without connection again.

See
[http://ubuntuforums.org/showthread.php?t=1347483](http://ubuntuforums.org/showthread.php?t=1347483)
[http://ubuntuforums.org/showthread.php?t=1369975](http://ubuntuforums.org/showthread.php?t=1369975)

---

