---
title: "no connection to insecure wireless network"
date: 2011-01-04
forum: Networking &amp; Wireless
---

### Post by dieter-erich on 2011-01-04
Hi,
Ubuntu 10.04: no problems to connect to secured wifi networks. However, when trying to establish a connection to an** insecure wifi after some time I get the message "disconnected, you are now offline" without ever having been connected**. Once out of about 30 times I get a normal connection. My eeePC 1005HA is double boot and I can connect from WinXP without problems. There seems to be a DHCP timeout (see attached output of syslog). I have seen some posts about the same problem but none of them had a solution. I hate it to use WinXP just for the sake of connecting to the spot. Any suggestins are highly appreciated!
D-E

---

### Post by PatchesTheCaveman on 2011-01-04
It looks like there's a bug in the ath9k driver that's causing this.

A lot of people have a better experience with the *madwifi* driver for Atheros wireless cards.  You can install it by either getting your wireless going for a little bit or plugging into a wired Ethernet connection, and then going to System > Administration > Additional Drivers on your top panel.  Then, click the *madwifi* driver and click Install.

As always, let us know if you have any trouble.  Good luck!

---

### Post by dieter-erich on 2011-01-06
Thanks a lot for the hint! However, I cannot find System > Administration **>Additional Drivers**. There is just "Hardware Drivers" and this says, after a while, that the system does not use proprietary drivers.

I neither find madwifi with the Synaptic Package Manager. So, how to install it without going through all the compiling stuff? Are there binaries somewhere?

Does madwifi support mobile access as well? I use this sometimes when there is no wifi available!

I am a bit afraid that I screw up my otherwise well-functioning UBUNTU. Can I go back to the current  configuration easily in case that madwifi does not do better or anything goes wrong?

Thanks, D-E

---

### Post by PatchesTheCaveman on 2011-01-06
I keep forgetting 10.04 and 10.10 call it something slightly different.

Apparently Ubuntu does not provide precompiled *madwifi* binaries, so you would have to compile and install it to use it.

Luckily, compiling them yourself is not hard.  Just follow these instructions:  [http://ubuntuforums.org/showthread.php?t=1484242](http://ubuntuforums.org/showthread.php?t=1484242)

If they make it worse (which is unlikely from what I hear), you can switch back by removing the lines the instructions tell you to add to /etc/modules and /etc/modprobe.d/blacklist.conf.

---

### Post by dieter-erich on 2011-01-08
Hi,
  I went through the complicated but well described procedure step by step but now it does not find any wireless and iwconfig says "no wireless extension". I am afraid that the extensive changes made to the system are difficult to reverse. What might have gone wrong? How can I find out? 
Thanks, D-E

---

### Post by PatchesTheCaveman on 2011-01-08
Run these commands on a terminal and copy/paste the output:
```
lsmod
dmesg | grep -i madwifi
dmesg | grep -i ath
```

---

### Post by dieter-erich on 2011-01-08
output of the commands attached. 
 
dmesg | grep -i madwifi did not result in anything!

---

### Post by PatchesTheCaveman on 2011-01-09
It shouldn't have.  My mistake.

Odd, the *madwifi* driver is running, but not doing anything, nor is it reporting any error.

Try running these commands to unload and reload and see if it responds:
```
sudo modprobe -r ath_pci
sudo modprobe ath_pci
```

If it still doesn't work, run this again:
```
dmesg | grep -i ath
```
to see if it reports something that time.  Copy/paste the output to a reply to this thread.

While you're at it, run this too to check to see what the kernel thinks is running your wireless card:
```
lspci -vnn
```

Then you can run these commands to get your old buggy wireless back for now:
```
sudo modprobe -r ath_pci
sudo modprobe ath9k
```

---

### Post by dieter-erich on 2011-01-09
Hi,
   below is the output of the commands you specified. Unfortunately, after trying to get the old wireless back I could never connect, even when trying about 50 times. Before, it worked at least once in 20 or 30 trials or so. Any ideas? There seems to be something with a config file. Unfortunately, I do not really understand what it means.....
 
--------------------
1) sudo modprobe -r ath_pci
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
2) sudo modprobe ath_pci
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
FATAL: Module ath_pciIf not found.
3) dmesg | grep -i athto
-------nothing -------------
4) lspci -vnn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GME Express Memory Controller Hub [8086:27ac] (rev 03)
Subsystem: ASUSTeK Computer Inc. Device [1043:8340]
Flags: bus master, fast devsel, latency 0
Capabilities: <access denied>
Kernel driver in use: agpgart-intel
Kernel modules: intel-agp
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GME Express Integrated Graphics Controller [8086:27ae] (rev 03)
Subsystem: ASUSTeK Computer Inc. Device [1043:8340]
Flags: bus master, fast devsel, latency 0, IRQ 16
Memory at f7e00000 (32-bit, non-prefetchable) [size=512K]
I/O ports at dc00 [size=8]
Memory at d0000000 (32-bit, prefetchable) [size=256M]
Memory at f7dc0000 (32-bit, non-prefetchable) [size=256K]
Capabilities: <access denied>
Kernel driver in use: i915
Kernel modules: i915
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
Subsystem: ASUSTeK Computer Inc. Device [1043:8340]
Flags: bus master, fast devsel, latency 0
Memory at f7e80000 (32-bit, non-prefetchable) [size=512K]
Capabilities: <access denied>
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
Subsystem: ASUSTeK Computer Inc. Device [1043:8398]
Flags: bus master, fast devsel, latency 0, IRQ 22
Memory at f7db8000 (64-bit, non-prefetchable) [size=16K]
Capabilities: <access denied>
Kernel driver in use: HDA Intel
Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
Flags: bus master, fast devsel, latency 0
Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
I/O behind bridge: 00001000-00001fff
Memory behind bridge: 80000000-801fffff
Prefetchable memory behind bridge: 0000000080200000-00000000803fffff
Capabilities: <access denied>
Kernel driver in use: pcieport
Kernel modules: shpchp
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02)
Flags: bus master, fast devsel, latency 0
Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
I/O behind bridge: 00002000-00002fff
Memory behind bridge: f8000000-fbffffff
Prefetchable memory behind bridge: 00000000f0000000-00000000f6ffffff
Capabilities: <access denied>
Kernel driver in use: pcieport
Kernel modules: shpchp
00:1c.3 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 4 [8086:27d6] (rev 02)
Flags: bus master, fast devsel, latency 0
Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
I/O behind bridge: 0000e000-0000efff
Memory behind bridge: f7f00000-f7ffffff
Prefetchable memory behind bridge: 0000000080400000-00000000805fffff
Capabilities: <access denied>
Kernel driver in use: pcieport
Kernel modules: shpchp
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
Subsystem: ASUSTeK Computer Inc. Device [1043:830f]
Flags: bus master, medium devsel, latency 0, IRQ 23
I/O ports at d400 [size=32]
Kernel driver in use: uhci_hcd
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
Subsystem: ASUSTeK Computer Inc. Device [1043:830f]
Flags: bus master, medium devsel, latency 0, IRQ 19
I/O ports at d480 [size=32]
Kernel driver in use: uhci_hcd
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
Subsystem: ASUSTeK Computer Inc. Device [1043:830f]
Flags: bus master, medium devsel, latency 0, IRQ 18
I/O ports at d800 [size=32]
Kernel driver in use: uhci_hcd
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
Subsystem: ASUSTeK Computer Inc. Device [1043:830f]
Flags: bus master, medium devsel, latency 0, IRQ 16
I/O ports at d880 [size=32]
Kernel driver in use: uhci_hcd
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02) (prog-if 20)
Subsystem: ASUSTeK Computer Inc. Device [1043:830f]
Flags: bus master, medium devsel, latency 0, IRQ 23
Memory at f7db7c00 (32-bit, non-prefetchable) [size=1K]
Capabilities: <access denied>
Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2) (prog-if 01)
Flags: bus master, fast devsel, latency 0
Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
Capabilities: <access denied>
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
Subsystem: ASUSTeK Computer Inc. Device [1043:830f]
Flags: bus master, medium devsel, latency 0
Capabilities: <access denied>
Kernel modules: iTCO_wdt, intel-rng
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 02) (prog-if 8a [Master SecP PriP])
Subsystem: ASUSTeK Computer Inc. Device [1043:830f]
Flags: bus master, medium devsel, latency 0, IRQ 18
I/O ports at 01f0 [size=8]
I/O ports at 03f4 [size=1]
I/O ports at 0170 [size=8]
I/O ports at 0374 [size=1]
I/O ports at ffa0 [size=16]
Kernel driver in use: ata_piix
00:1f.2 SATA controller [0106]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller [8086:27c5] (rev 02) (prog-if 01)
Subsystem: ASUSTeK Computer Inc. Device [1043:830f]
Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 27
I/O ports at d080 [size=8]
I/O ports at d000 [size=4]
I/O ports at cc00 [size=8]
I/O ports at c880 [size=4]
I/O ports at c800 [size=16]
Memory at f7db7800 (32-bit, non-prefetchable) [size=1K]
Capabilities: <access denied>
Kernel driver in use: ahci
Kernel modules: ahci
01:00.0 Ethernet controller [0200]: Atheros Communications Atheros AR8132 / L1c Gigabit Ethernet Adapter [1969:1062] (rev c0)
Subsystem: ASUSTeK Computer Inc. Device [1043:838a]
Flags: bus master, fast devsel, latency 0, IRQ 28
Memory at f7fc0000 (64-bit, non-prefetchable) [size=256K]
I/O ports at ec00 [size=128]
Capabilities: <access denied>
Kernel driver in use: atl1c
Kernel modules: atl1c
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
Subsystem: Device [1a3b:1089]
Flags: bus master, fast devsel, latency 0, IRQ 10
Memory at fbff0000 (64-bit, non-prefetchable) [size=64K]
Capabilities: <access denied>
Kernel modules: ath9k
5) sudo modprobe -r ath_pci
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
blaas@ubuntu:~$ 
6) sudo modprobe ath9k
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
&#12288;

---

### Post by PatchesTheCaveman on 2011-01-10
Some users of this board have had great success with this driver:
[http://sourceforge.net/projects/ath9k-htc/](http://sourceforge.net/projects/ath9k-htc/)

---

### Post by dieter-erich on 2011-01-10
Thanks, I shall try it and let you know. Can you explain, though, what is wrong with Madwifi on my machine!? I'd like to understand. I am not sufficiently experienced with linux to interpret the output of the various commands but it seems to me that everything is correct but the driver is simply not working (maybe because of a particular configuration of my Netbook)?
D-E

---

### Post by PatchesTheCaveman on 2011-01-10
I just came across that solution so I figured I'd offer it to see if it was easier.

I don't know if was a typo but there was an error I saw in your diagnostic output:
> 3) dmesg | grep -i ath[COLOR="Red"]to[/COLOR]

The correct command is:
```
dmesg | grep -i ath
```

Retry all the steps in Post #8 and see if the output changes.

---

### Post by dieter-erich on 2011-01-10
Hi, I also tried your last hint but unfortunately in vain! 

However, bcbc answered to another thread of mine and drew my attention to a post, which finally led to this:  'sudo apt-get install linux-backports-modules-karmic'. I installed it into the backup of my original system and now the wireless connected immediately! Have not yet tried several times though but I am confident! :-))

---

