---
title: "no sound with Creative X-Fi Xtreme Audio card in Studio"
date: 2010-03-06
forum: Multimedia Software
---

### Post by pianoman10 on 2010-03-06
I've read and tried some things and still can't get my sound to play. Below is what I tried in terminal:
```

[sudo] password for blondsurferknight:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package flashplugin-nonfree-extrasound
blondsurferknight@BATCAVE4468:~$ wget http://ccftp.creative.com/manualdn/D...US_1.00.tar.gz
--2010-03-06 16:30:30-- http://ccftp.creative.com/manualdn/D...US_1.00.tar.gz
Resolving ccftp.creative.com... 209.147.118.93
Connecting to ccftp.creative.com|209.147.118.93|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 70448 (69K) [application/x-gzip]
Saving to: `XFiDrv_Linux_Public_US_1.00.tar.gz.1'
100%[================================================== ================================================== ===========================================>] 70,448 83.8K/s in 0.8s
2010-03-06 16:30:31 (83.8 KB/s) - `XFiDrv_Linux_Public_US_1.00.tar.gz.1' saved [70448/70448]
blondsurferknight@BATCAVE4468:~$ cd XFiDrv_Linux_Public_US_1.00
bash: cd: XFiDrv_Linux_Public_US_1.00: No such file or directory
blondsurferknight@BATCAVE4468:~$ tar -xf XFiDrv_Linux_Public_US_1.00.tar.gz
blondsurferknight@BATCAVE4468:~$ cd XFiDrv_Linux_Public_US_1.00
blondsurferknight@BATCAVE4468:~/XFiDrv_Linux_Public_US_1.00$
blondsurferknight@BATCAVE4468:~/XFiDrv_Linux_Public_US_1.00$ sudo apt-get install build-essential linux-headers-`uname -r`
Reading package lists... Done
Building dependency tree
Reading state information... Done
linux-headers-2.6.31-9-rt is already the newest version.
linux-headers-2.6.31-9-rt set to manually installed.
The following extra packages will be installed:
dpkg-dev g++ g++-4.4 libstdc++6-4.4-dev
Suggested packages:
debian-keyring debian-maintainers g++-multilib g++-4.4-multilib gcc-4.4-doc libstdc++6-4.4-dbg libstdc++6-4.4-doc
The following NEW packages will be installed:
build-essential dpkg-dev g++ g++-4.4 libstdc++6-4.4-dev
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 7,610kB of archives.
After this operation, 25.0MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com karmic-updates/main libstdc++6-4.4-dev 4.4.1-4ubuntu9 [1,526kB]
Get:2 http://us.archive.ubuntu.com karmic-updates/main g++-4.4 4.4.1-4ubuntu9 [5,502kB]
Get:3 http://us.archive.ubuntu.com karmic/main g++ 4:4.4.1-1ubuntu2 [1,448B]
Get:4 http://us.archive.ubuntu.com karmic/main dpkg-dev 1.15.4ubuntu2 [573kB]
Get:5 http://us.archive.ubuntu.com karmic/main build-essential 11.4 [7,170B]
Fetched 7,610kB in 42s (178kB/s)
Selecting previously deselected package libstdc++6-4.4-dev.
(Reading database ... 181091 files and directories currently installed.)
Unpacking libstdc++6-4.4-dev (from .../libstdc++6-4.4-dev_4.4.1-4ubuntu9_amd64.deb) ...
Selecting previously deselected package g++-4.4.
Unpacking g++-4.4 (from .../g++-4.4_4.4.1-4ubuntu9_amd64.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4%3a4.4.1-1ubuntu2_amd64.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.15.4ubuntu2_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.4_amd64.deb) ...
Processing triggers for man-db ...
Setting up dpkg-dev (1.15.4ubuntu2) ...
Setting up libstdc++6-4.4-dev (4.4.1-4ubuntu9) ...
Setting up g++-4.4 (4.4.1-4ubuntu9) ...
Setting up g++ (4:4.4.1-1ubuntu2) ...
update-alternatives: using /usr/bin/g++ to provide /usr/bin/c++ (c++) in auto mode.
Setting up build-essential (11.4) ...
blondsurferknight@BATCAVE4468:~/XFiDrv_Linux_Public_US_1.00$
blondsurferknight@BATCAVE4468:~/XFiDrv_Linux_Public_US_1.00$ lspci -v
00:00.0 Host bridge: Intel Corporation X58 I/O Hub to ESI Port (rev 13)
Subsystem: Dell Device 02b7
Flags: fast devsel
Capabilities: <access denied>
00:01.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 1 (rev 13)
Flags: bus master, fast devsel, latency 0
Bus: primary=00, secondary=0b, subordinate=0b, sec-latency=0
Capabilities: <access denied>
Kernel driver in use: pcieport-driver
Kernel modules: shpchp
00:03.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 3 (rev 13)
Flags: bus master, fast devsel, latency 0
Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=0
I/O behind bridge: 0000e000-0000efff
Memory behind bridge: fbf00000-fbffffff
Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
Capabilities: <access denied>
Kernel driver in use: pcieport-driver
Kernel modules: shpchp
00:07.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 7 (rev 13)
Flags: bus master, fast devsel, latency 0
Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
Memory behind bridge: fbe00000-fbefffff
Prefetchable memory behind bridge: 00000000cff00000-00000000cfffffff
Capabilities: <access denied>
Kernel driver in use: pcieport-driver
Kernel modules: shpchp
00:09.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 9 (rev 13)
Flags: bus master, fast devsel, latency 0
Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
Capabilities: <access denied>
Kernel driver in use: pcieport-driver
Kernel modules: shpchp
00:14.0 PIC: Intel Corporation 5520/5500/X58 I/O Hub System Management Registers (rev 13)
Flags: fast devsel
Capabilities: <access denied>
00:14.1 PIC: Intel Corporation 5520/5500/X58 I/O Hub GPIO and Scratch Pad Registers (rev 13)
Flags: fast devsel
Capabilities: <access denied>
00:14.2 PIC: Intel Corporation 5520/5500/X58 I/O Hub Control Status and RAS Registers (rev 13)
Flags: fast devsel
Capabilities: <access denied>
00:14.3 PIC: Intel Corporation 5520/5500/X58 I/O Hub Throttle Registers (rev 13)
Flags: fast devsel
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
Subsystem: Dell Device 02b7
Flags: bus master, medium devsel, latency 0, IRQ 16
I/O ports at a400 [size=32]
Capabilities: <access denied>
Kernel driver in use: uhci_hcd
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
Subsystem: Dell Device 02b7
Flags: bus master, medium devsel, latency 0, IRQ 21
I/O ports at a480 [size=32]
Capabilities: <access denied>
Kernel driver in use: uhci_hcd
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
Subsystem: Dell Device 02b7
Flags: bus master, medium devsel, latency 0, IRQ 19
I/O ports at a800 [size=32]
Capabilities: <access denied>
Kernel driver in use: uhci_hcd
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2 (prog-if 20)
Subsystem: Dell Device 02b7
Flags: bus master, medium devsel, latency 0, IRQ 18
Memory at fa800000 (32-bit, non-prefetchable) [size=1K]
Capabilities: <access denied>
Kernel driver in use: ehci_hcd
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
Subsystem: Dell Device 02b7
Flags: bus master, fast devsel, latency 0, IRQ 22
Memory at faff8000 (64-bit, non-prefetchable) [size=16K]
Capabilities: <access denied>
Kernel driver in use: HDA Intel
Kernel modules: snd-hda-intel
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 1
Flags: bus master, fast devsel, latency 0
Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
Capabilities: <access denied>
Kernel driver in use: pcieport-driver
Kernel modules: shpchp
00:1c.2 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 3
Flags: bus master, fast devsel, latency 0
Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
I/O behind bridge: 0000d000-0000dfff
Memory behind bridge: fbd00000-fbdfffff
Prefetchable memory behind bridge: 00000000cfe00000-00000000cfefffff
Capabilities: <access denied>
Kernel driver in use: pcieport-driver
Kernel modules: shpchp
00:1c.3 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 4
Flags: bus master, fast devsel, latency 0
Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
I/O behind bridge: 0000c000-0000cfff
Memory behind bridge: fba00000-fbbfffff
Capabilities: <access denied>
Kernel driver in use: pcieport-driver
Kernel modules: shpchp
00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 5
Flags: bus master, fast devsel, latency 0
Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
Memory behind bridge: fb200000-fb9fffff
Capabilities: <access denied>
Kernel driver in use: pcieport-driver
Kernel modules: shpchp
00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 6
Flags: bus master, fast devsel, latency 0
Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
Memory behind bridge: fb000000-fb1fffff
Capabilities: <access denied>
Kernel driver in use: pcieport-driver
Kernel modules: shpchp
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
Subsystem: Dell Device 02b7
Flags: bus master, medium devsel, latency 0, IRQ 23
I/O ports at a880 [size=32]
Capabilities: <access denied>
Kernel driver in use: uhci_hcd
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
Subsystem: Dell Device 02b7
Flags: bus master, medium devsel, latency 0, IRQ 19
I/O ports at ac00 [size=32]
Capabilities: <access denied>
Kernel driver in use: uhci_hcd
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
Subsystem: Dell Device 02b7
Flags: bus master, medium devsel, latency 0, IRQ 18
I/O ports at b000 [size=32]
Capabilities: <access denied>
Kernel driver in use: uhci_hcd
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1 (prog-if 20)
Subsystem: Dell Device 02b7
Flags: bus master, medium devsel, latency 0, IRQ 23
Memory at faa00000 (32-bit, non-prefetchable) [size=1K]
Capabilities: <access denied>
Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90) (prog-if 01)
Flags: bus master, fast devsel, latency 0
Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
Capabilities: <access denied>
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
Subsystem: Dell Device 02b7
Flags: bus master, medium devsel, latency 0
Capabilities: <access denied>
Kernel modules: iTCO_wdt
00:1f.2 SATA controller: Intel Corporation 82801JI (ICH10 Family) SATA AHCI Controller (prog-if 01)
Subsystem: Dell Device 02b7
Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 33
I/O ports at b880 [size=8]
I/O ports at b800 [size=4]
I/O ports at b480 [size=8]
I/O ports at b400 [size=4]
I/O ports at b080 [size=32]
Memory at fac00000 (32-bit, non-prefetchable) [size=2K]
Capabilities: <access denied>
Kernel driver in use: ahci
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
Subsystem: Dell Device 02b7
Flags: medium devsel, IRQ 15
Memory at fafffc00 (64-bit, non-prefetchable) [size=256]
I/O ports at 0400 [size=32]
Kernel modules: i2c-i801
02:00.0 PCI bridge: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG PCI to PCIe Bridge
Flags: bus master, fast devsel, latency 0
Bus: primary=02, secondary=03, subordinate=03, sec-latency=64
Memory behind bridge: fb000000-fb1fffff
Capabilities: <access denied>
Kernel modules: shpchp
03:00.0 Audio device: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG
Subsystem: Creative Labs Device 0018
Flags: bus master, medium devsel, latency 64, IRQ 17
Memory at fb000000 (32-bit, non-prefetchable) [size=16K]
Capabilities: <access denied>
Kernel driver in use: HDA Intel
Kernel modules: snd-hda-intel
04:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller (prog-if 10)
Subsystem: Dell Device 02b7
Flags: bus master, fast devsel, latency 0, IRQ 16
Memory at fb800000 (32-bit, non-prefetchable) [size=2K]
Memory at fb600000 (32-bit, non-prefetchable) [size=128]
Memory at fb400000 (32-bit, non-prefetchable) [size=128]
Memory at fb200000 (32-bit, non-prefetchable) [size=128]
Capabilities: <access denied>
Kernel driver in use: ohci1394
Kernel modules: firewire-ohci, ohci1394
05:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 AHCI Controller (rev 03) (prog-if 01)
Subsystem: Dell Device 02b7
Flags: bus master, fast devsel, latency 0, IRQ 19
Memory at fba00000 (32-bit, non-prefetchable) [size=8K]
Capabilities: <access denied>
Kernel driver in use: ahci
05:00.1 IDE interface: JMicron Technology Corp. JMB362/JMB363 AHCI Controller (rev 03) (prog-if 85 [Master SecO PriO])
Subsystem: Dell Device 02b7
Flags: bus master, fast devsel, latency 0, IRQ 16
I/O ports at cc00 [size=8]
I/O ports at c880 [size=4]
I/O ports at c800 [size=8]
I/O ports at c480
I/O ports at c400
Capabilities: <access denied>
Kernel driver in use: pata_jmicron
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
Subsystem: Dell Device 02b7
Flags: bus master, fast devsel, latency 0, IRQ 34
I/O ports at d800
Memory at fbdff000 (64-bit, non-prefetchable) [size=4K]
Memory at cfef0000 (64-bit, prefetchable) [size=64K]
[virtual] Expansion ROM at cfe00000 [disabled] [size=128K]
Capabilities: <access denied>
Kernel driver in use: r8169
Kernel modules: r8169
09:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
Subsystem: Dell Device 000a
Flags: bus master, fast devsel, latency 0, IRQ 16
Memory at fbefc000 (64-bit, non-prefetchable) [size=16K]
Memory at cff00000 (64-bit, prefetchable) [size=1M]
Capabilities: <access denied>
Kernel driver in use: wl
Kernel modules: wl, ssb
0a:00.0 VGA compatible controller: ATI Technologies Inc RV770 [Radeon HD 4870]
Subsystem: ATI Technologies Inc Device 0502
Flags: bus master, fast devsel, latency 0, IRQ 35
Memory at d0000000 (64-bit, prefetchable) [size=256M]
Memory at fbfe0000 (64-bit, non-prefetchable) [size=64K]
I/O ports at e000
Expansion ROM at fbfc0000 [disabled] [size=128K]
Capabilities: <access denied>
Kernel driver in use: fglrx_pci
Kernel modules: fglrx, radeon
0a:00.1 Audio device: ATI Technologies Inc HD48x0 audio
Subsystem: ATI Technologies Inc HD48x0 audio
Flags: bus master, fast devsel, latency 0, IRQ 17
Memory at fbffc000 (64-bit, non-prefetchable) [size=16K]
Capabilities: <access denied>
Kernel driver in use: HDA Intel
Kernel modules: snd-hda-intel
blondsurferknight@BATCAVE4468:~/XFiDrv_Linux_Public_US_1.00$ make
make -C /lib/modules/2.6.31-9-rt/build M=/home/blondsurferknight/XFiDrv_Linux_Public_US_1.00
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-9-rt'
LD /home/blondsurferknight/XFiDrv_Linux_Public_US_1.00/built-in.o
CC [M] /home/blondsurferknight/XFiDrv_Linux_Public_US_1.00/xfi.o
/home/blondsurferknight/XFiDrv_Linux_Public_US_1.00/xfi.c:14:26: error: sound/driver.h: No such file or directory
/home/blondsurferknight/XFiDrv_Linux_Public_US_1.00/xfi.c: In function &#8216;ct_card_probe&#8217;:
/home/blondsurferknight/XFiDrv_Linux_Public_US_1.00/xfi.c:55: error: implicit declaration of function &#8216;snd_card_new&#8217;
/home/blondsurferknight/XFiDrv_Linux_Public_US_1.00/xfi.c:55: warning: assignment makes pointer from integer without a cast
make[2]: *** [/home/blondsurferknight/XFiDrv_Linux_Public_US_1.00/xfi.o] Error 1
make[1]: *** [_module_/home/blondsurferknight/XFiDrv_Linux_Public_US_1.00] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-9-rt'
make: *** [all] Error 2
```

I've gotten info overload and being new, not sure which thread to follow and what I need to do or undo to resolve this issue. Thanks in advance for any hand-holding walk through help.

---

