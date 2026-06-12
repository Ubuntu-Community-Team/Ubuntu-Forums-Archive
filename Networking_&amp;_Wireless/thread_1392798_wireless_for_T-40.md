---
title: "wireless for T-40"
date: 2010-01-28
forum: Networking &amp; Wireless
---

### Post by Przemian on 2010-01-28
Hi,

I installed Ubuntu and I cant get my wireless connection to work. I found that I need ndiswrapper to update my drivers following the sticky post in here. However there is a problem, because I cant successfully run ndiswrapper on my system. 
Please help.

Ubuntu 9.10, IBM ThinkPad T-40, what am I doing wrong?


prem@prem-laptop:~/Desktop/ndiswrapper-1.55$ make uninstall
NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.
removing /lib/modules/2.6.31-14-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko
/bin/rm: cannot remove `/lib/modules/2.6.31-14-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko': Permission denied
make: *** [uninstall] Error 1
prem@prem-laptop:~/Desktop/ndiswrapper-1.55$


prem@prem-laptop:~/Desktop/ndiswrapper-1.55$ make
make -C driver
make[1]: Entering directory `/home/prem/Desktop/ndiswrapper-1.55/driver'
make -C /usr/src/linux-headers-2.6.31-14-generic M=/home/prem/Desktop/ndiswrapper-1.55/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /home/prem/Desktop/ndiswrapper-1.55/driver/crt.o
In file included from /home/prem/Desktop/ndiswrapper-1.55/driver/crt.c:16:
/home/prem/Desktop/ndiswrapper-1.55/driver/ntoskernel.h: In function ‘PushEntrySList’:
/home/prem/Desktop/ndiswrapper-1.55/driver/ntoskernel.h:905: error: implicit declaration of function ‘cmpxchg8b’
make[3]: *** [/home/prem/Desktop/ndiswrapper-1.55/driver/crt.o] Error 1
make[2]: *** [_module_/home/prem/Desktop/ndiswrapper-1.55/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/prem/Desktop/ndiswrapper-1.55/driver'
make: *** [all] Error 2
prem@prem-laptop:~/Desktop/ndiswrapper-1.55$

---

### Post by chili555 on 2010-01-28
I am answering this post from my T40. I am wondering which wireless chipset yours has that doesn't work natively. What have you tried to get the wireless to work?

---

### Post by Przemian on 2010-01-28
Cisco Aironet Wireless 80.11b

I'm very new to ubuntu, so I tried to read as much about this issue as I can understand (with my limited knowledge). I know my BIOS has the wireless device turned on (Fn + F5 normally works in windows, but in ubuntu I did not notice any changes when I press it).

---

### Post by chili555 on 2010-01-28
Ahh! The good old Aironet! Please open a terminal and do:```
dmesg | grep -i airo
sudo lshw -C network
```Let's see what's happening, or not, under the hood.

---

### Post by Przemian on 2010-01-28
prem@prem-laptop:~$ dmesg | grep -i airo
[   13.562474] airo(): Probing for PCI adapters
[   13.562545] airo 0000:02:02.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[   13.562568] airo(): Found an MPI350 card
[   14.599617] airo(eth1): Firmware version 5.60.10
[   14.599621] airo(eth1): WPA supported.
[   14.599624] airo(eth1): MAC enabled 00:02:8a:ba:5a:f3
[   14.601389] airo(): Finished probing for PCI adapters
[   17.048165] airo(eth1): set_wep_key: key length to set was zero
[   17.048173] airo(eth1): failed to set WEP key at index 0: -1.
[   17.048235] airo(eth1): set_wep_key: key length to set was zero
[   17.048239] airo(eth1): failed to set WEP key at index 1: -1.
[   17.048261] airo(eth1): set_wep_key: key length to set was zero
[   17.048265] airo(eth1): failed to set WEP key at index 2: -1.
[   17.048286] airo(eth1): set_wep_key: key length to set was zero
[   17.048289] airo(eth1): failed to set WEP key at index 3: -1.
[   17.050854] airo(eth1): cmd:1 status:7f01 rsp0:88 rsp1:ff10 rsp2:c0f0
[   17.050860] airo(eth1): Bad MAC enable reason=88, rid=ff10, offset=49392
[   17.144407] airo(eth1): cmd:103 status:7f03 rsp0:0 rsp1:ff10 rsp2:c0f0
[   37.413696] airo(eth1): cmd:103 status:7f03 rsp0:0 rsp1:ff10 rsp2:c0f0
[   67.413565] airo(eth1): cmd:103 status:7f03 rsp0:0 rsp1:ff10 rsp2:c0f0
[  107.413826] airo(eth1): cmd:103 status:7f03 rsp0:0 rsp1:ff10 rsp2:c0f0
[  157.426056] airo(eth1): cmd:103 status:7f03 rsp0:0 rsp1:ff10 rsp2:c0f0

a few pages of the above...


and then

prem@prem-laptop:~$ sudo lshw -C network
[sudo] password for prem: 
  *-network:0 DISABLED    
       description: Wireless interface
       product: Cisco Aironet Wireless 802.11b
       vendor: AIRONET Wireless Communications
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth1
       version: 00
       serial: 00:02:8a:ba:5a:f3
       width: 32 bits
       clock: 33MHz
       capabilities: pm vpd bus_master cap_list rom ethernet physical wireless logical
       configuration: broadcast=yes driver=airo latency=64 maxlatency=4 mingnt=4 multicast=yes wireless=IEEE 802.11-DS
       resources: irq:11 ioport:8000(size=256) memory:c0200000-c0203fff memory:c0400000-c07fffff memory:c0800000-c09fffff(prefetchable)
  *-network:1
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 81
       serial: 00:0d:60:37:27:cb
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.1.67 latency=66 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: irq:11 memory:c0204000-c0204fff ioport:8400(size=64)
prem@prem-laptop:~$

hmmm... DISABLED?

---

### Post by chili555 on 2010-01-28
Please open a terminal and do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add these lines:```
# these aes modules break the airo driver
blacklist padlock-aes
blacklist geode-aes
```Proofread, save and close gedit. Reboot and let us know if the wireless now works. If not, please post:```
lsmod
```Thanks.

---

### Post by Przemian on 2010-01-28
I got it to work. However, I also had to change settings on my router: 

went from hidden, no ssid, wpa-psk, channel 1 (2412Mhz) to 

open WEP, SSID enabled.

wonder why I couldnt find WPA-PSK encryption when left-clicking on the icon in ubuntu. I only had options of WEP 40 and 128 bit.

Thank you for help:)

---

### Post by Przemian on 2010-01-29
Also, after the change of router settings, all my other devices on the network (2 laps, iphone and a PS3) get intermittent connection.  hhmmmmmm......

---

### Post by Przemian on 2010-01-29
Do I need wpa_supplicant and do I need to edit /user/network/interfaces in 9.10? 
Will this interfere with Network Manager?

---

### Post by chili555 on 2010-01-29
> Do I need wpa_supplicantProbably so.```
sudo apt-get install wpa-supplicant
```> do I need to edit /user/network/interfaces in 9.10? It's actually *[COLOR="Red"]/etc[/COLOR]/network/interfaces*, and no, you don't need to touch it.> Will this interfere with Network Manager? *interfaces* most definitely will.

---

### Post by cedricsolignac on 2010-06-04
> **chili555 said:**
> Please open a terminal and do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add these lines:```
# these aes modules break the airo driver
blacklist padlock-aes
blacklist geode-aes
```Proofread, save and close gedit. Reboot and let us know if the wireless now works. If not, please post:```
lsmod
```Thanks.
Hi,

First, thank you for your help !

My laptop running a environnement Ubuntu Lucid Lynx 10.04 with genius "IBM ThinkPad T40".

Why my laptop boot in 34 seconds, it's very slow, no ?


This my dmesg, a problem exist on 1.762339 seconds directly 19.201024 seconds.
I have hightlight bold below.

<code>
AR 6 (0x0-0x1fffff), disabling
[    0.112251] pnp 00:00: mem resource (0xf0000-0xfffff) overlaps 0000:02:02.0 BAR 6 (0x0-0x1fffff), disabling
[    0.112256] pnp 00:00: mem resource (0x100000-0x3fffffff) overlaps 0000:02:02.0 BAR 6 (0x0-0x1fffff), disabling
[    0.115085] pnp: PnP ACPI: found 13 devices
[    0.115088] ACPI: ACPI bus type pnp unregistered
[    0.115094] PnPBIOS: Disabled by ACPI PNP
[    0.115112] system 00:00: iomem range 0xfec00000-0xffffffff could not be reserved
[    0.115123] system 00:02: ioport range 0x1000-0x107f has been reserved
[    0.115127] system 00:02: ioport range 0x1180-0x11bf has been reserved
[    0.115131] system 00:02: ioport range 0x15e0-0x15ef has been reserved
[    0.115135] system 00:02: ioport range 0x1600-0x162f has been reserved
[    0.115139] system 00:02: ioport range 0x1632-0x167f has been reserved
[    0.115144] system 00:02: ioport range 0x1630-0x1631 has been reserved
[    0.149923] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.149928] pci 0000:00:01.0:   IO window: 0x3000-0x3fff
[    0.149933] pci 0000:00:01.0:   MEM window: 0xc0100000-0xc01fffff
[    0.149938] pci 0000:00:01.0:   PREFETCH window: 0xe0000000-0xe7ffffff
[    0.149950] pci 0000:02:00.0: CardBus bridge, secondary bus 0000:03
[    0.149953] pci 0000:02:00.0:   IO window: 0x004000-0x0040ff
[    0.149959] pci 0000:02:00.0:   IO window: 0x004400-0x0044ff
[    0.149964] pci 0000:02:00.0:   PREFETCH window: 0xe8000000-0xebffffff
[    0.149970] pci 0000:02:00.0:   MEM window: 0xc4000000-0xc7ffffff
[    0.149975] pci 0000:02:00.1: CardBus bridge, secondary bus 0000:07
[    0.149979] pci 0000:02:00.1:   IO window: 0x004800-0x0048ff
[    0.149984] pci 0000:02:00.1:   IO window: 0x004c00-0x004cff
[    0.149989] pci 0000:02:00.1:   PREFETCH window: 0xec000000-0xefffffff
[    0.149995] pci 0000:02:00.1:   MEM window: 0xc8000000-0xcbffffff
[    0.150000] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.150005] pci 0000:00:1e.0:   IO window: 0x4000-0x8fff
[    0.150011] pci 0000:00:1e.0:   MEM window: 0xc0200000-0xcfffffff
[    0.150017] pci 0000:00:1e.0:   PREFETCH window: 0xe8000000-0xefffffff
[    0.150037] pci 0000:00:1e.0: setting latency timer to 64
[    0.150430] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[    0.150434] PCI: setting IRQ 11 as level-triggered
[    0.150441] pci 0000:02:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    0.150814] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[    0.150819] pci 0000:02:00.1: PCI INT B -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[    0.150828] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.150832] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.150836] pci_bus 0000:01: resource 0 io:  [0x3000-0x3fff]
[    0.150840] pci_bus 0000:01: resource 1 mem: [0xc0100000-0xc01fffff]
[    0.150843] pci_bus 0000:01: resource 2 pref mem [0xe0000000-0xe7ffffff]
[    0.150847] pci_bus 0000:02: resource 0 io:  [0x4000-0x8fff]
[    0.150851] pci_bus 0000:02: resource 1 mem: [0xc0200000-0xcfffffff]
[    0.150855] pci_bus 0000:02: resource 2 pref mem [0xe8000000-0xefffffff]
[    0.150859] pci_bus 0000:02: resource 3 io:  [0x00-0xffff]
[    0.150862] pci_bus 0000:02: resource 4 mem: [0x000000-0xffffffff]
[    0.150866] pci_bus 0000:03: resource 0 io:  [0x4000-0x40ff]
[    0.150870] pci_bus 0000:03: resource 1 io:  [0x4400-0x44ff]
[    0.150874] pci_bus 0000:03: resource 2 pref mem [0xe8000000-0xebffffff]
[    0.150878] pci_bus 0000:03: resource 3 mem: [0xc4000000-0xc7ffffff]
[    0.150882] pci_bus 0000:07: resource 0 io:  [0x4800-0x48ff]
[    0.150885] pci_bus 0000:07: resource 1 io:  [0x4c00-0x4cff]
[    0.150889] pci_bus 0000:07: resource 2 pref mem [0xec000000-0xefffffff]
[    0.150893] pci_bus 0000:07: resource 3 mem: [0xc8000000-0xcbffffff]
[    0.150949] NET: Registered protocol family 2
[    0.151090] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.151610] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.153332] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.154464] TCP: Hash tables configured (established 131072 bind 65536)
[    0.154470] TCP reno registered
[    0.154666] NET: Registered protocol family 1
[    0.154792] pci 0000:01:00.0: Boot video device
[    0.154964] Simple Boot Flag at 0x35 set to 0x1
[    0.155096] cpufreq-nforce2: No nForce2 chipset.
[    0.155142] Scanning for low memory corruption every 60 seconds
[    0.155342] audit: initializing netlink socket (disabled)
[    0.155369] type=2000 audit(1275635114.151:1): initialized
[    0.169690] Trying to unpack rootfs image as initramfs...
[    0.187787] highmem bounce pool size: 64 pages
[    0.187797] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.190256] VFS: Disk quotas dquot_6.5.2
[    0.190364] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.191364] fuse init (API version 7.13)
[    0.191501] msgmni has been set to 1716
[    0.196055] alg: No test for stdrng (krng)
[    0.196177] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.196181] io scheduler noop registered
[    0.196184] io scheduler anticipatory registered
[    0.196187] io scheduler deadline registered
[    0.196258] io scheduler cfq registered (default)
[    0.196441] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.196473] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.196791] ACPI: AC Adapter [AC] (on-line)
[    0.196885] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.197059] ACPI: Lid Switch [LID]
[    0.197123] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.197129] ACPI: Sleep Button [SLPB]
[    0.197204] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.197208] ACPI: Power Button [PWRF]
[    0.204120] Marking TSC unstable due to TSC halts in idle
[    0.204249] processor LNXCPU:00: registered as cooling_device0
[    0.206118] Switching to clocksource acpi_pm
[    0.213467] thermal LNXTHERM:01: registered as thermal_zone0
[    0.213481] ACPI: Thermal Zone [THM0] (46 C)
[    0.215589] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.215729] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a NS16550A
[    0.216764] serial 00:0a: activated
[    0.216884] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a NS16550A
[    0.217018] serial 0000:00:1f.6: PCI INT B -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[    0.217027] serial 0000:00:1f.6: PCI INT B disabled
[    0.218374] brd: module loaded
[    0.219025] loop: module loaded
[    0.219144] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.219301] ata_piix 0000:00:1f.1: version 2.13
[    0.219311] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
[    0.219728] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[    0.219734] ata_piix 0000:00:1f.1: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    0.219792] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.224574] isapnp: Scanning for PnP cards...
[    0.230182] scsi0 : ata_piix
[    0.231398] scsi1 : ata_piix
[    0.233134] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1860 irq 14
[    0.233138] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1868 irq 15
[    0.236982] Fixed MDIO Bus: probed
[    0.237037] PPP generic driver version 2.4.2
[    0.237138] tun: Universal TUN/TAP device driver, 1.6
[    0.237141] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.237325] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.294607] ACPI: Battery Slot [BAT0] (battery present)
[    0.294782] ehci_hcd 0000:00:1d.7: power state changed by ACPI to D0
[    0.295186] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[    0.295192] ehci_hcd 0000:00:1d.7: PCI INT D -> Link[LNKH] -> GSI 11 (level, low) -> IRQ 11
[    0.295219] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.295224] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.295338] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.295382] ehci_hcd 0000:00:1d.7: debug port 1
[    0.299278] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.301620] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xc0000000
[    0.324405] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.324638] usb usb1: configuration #1 chosen from 1 choice
[    0.324685] hub 1-0:1.0: USB hub found
[    0.324703] hub 1-0:1.0: 6 ports detected
[    0.324809] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.324840] uhci_hcd: USB Universal Host Controller Interface driver
[    0.325191] uhci_hcd 0000:00:1d.0: power state changed by ACPI to D0
[    0.325205] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    0.325218] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.325223] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.325301] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.325334] uhci_hcd 0000:00:1d.0: irq 11, io base 0x00001800
[    0.325474] usb usb2: configuration #1 chosen from 1 choice
[    0.325517] hub 2-0:1.0: USB hub found
[    0.325528] hub 2-0:1.0: 2 ports detected
[    0.325767] uhci_hcd 0000:00:1d.1: power state changed by ACPI to D0
[    0.326171] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[    0.326177] uhci_hcd 0000:00:1d.1: PCI INT B -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    0.326186] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.326190] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.326240] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.326265] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00001820
[    0.326405] usb usb3: configuration #1 chosen from 1 choice
[    0.326441] hub 3-0:1.0: USB hub found
[    0.326452] hub 3-0:1.0: 2 ports detected
[    0.326507] uhci_hcd 0000:00:1d.2: PCI INT C -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    0.326514] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.326518] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.326560] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.326583] uhci_hcd 0000:00:1d.2: irq 11, io base 0x00001840
[    0.326720] usb usb4: configuration #1 chosen from 1 choice
[    0.326755] hub 4-0:1.0: USB hub found
[    0.326764] hub 4-0:1.0: 2 ports detected
[    0.326903] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[    0.336740] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.336756] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.336994] mice: PS/2 mouse device common for all mice
[    0.337696] rtc_cmos 00:06: RTC can wake from S4
[    0.337771] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.337806] rtc0: alarms up to one month, y3k, 114 bytes nvram
[    0.338045] device-mapper: uevent: version 1.0.3
[    0.339233] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    0.341059] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.344326] device-mapper: multipath: version 1.1.0 loaded
[    0.344331] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.344623] EISA: Probing bus 0 at eisa.0
[    0.344632] Cannot allocate resource for EISA slot 1
[    0.344636] Cannot allocate resource for EISA slot 2
[    0.344639] Cannot allocate resource for EISA slot 3
[    0.344642] Cannot allocate resource for EISA slot 4
[    0.344645] Cannot allocate resource for EISA slot 5
[    0.344648] Cannot allocate resource for EISA slot 6
[    0.344651] Cannot allocate resource for EISA slot 7
[    0.344654] Cannot allocate resource for EISA slot 8
[    0.344656] EISA: Detected 0 cards.
[    0.392375] cpuidle: using governor ladder
[    0.392456] cpuidle: using governor menu
[    0.393194] TCP cubic registered
[    0.393452] NET: Registered protocol family 10
[    0.394154] lo: Disabled Privacy Extensions
[    0.394639] NET: Registered protocol family 17
[    0.394902] P-state transition latency capped at 20 uS
[    0.395210] Using IPI No-Shortcut mode
[    0.395357] PM: Resume from disk failed.
[    0.395375] registered taskstats version 1
[    0.395693]   Magic number: 14:551:65
[    0.395783] pci 0000:00:1e.0: hash matches
[    0.395848] rtc_cmos 00:06: setting system clock to 2010-06-04 07:05:15 UTC (1275635115)
[    0.395852] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.395855] EDD information not available.
[    0.408609] ata1.00: HPA unlocked: 74306546 -> 78140160, native 78140160
[    0.408620] ata1.00: ATA-5: IC25N040ATCS05-0, CS4OA61A, max UDMA/100
[    0.408624] ata1.00: 78140160 sectors, multi 16: LBA 
[    0.425081] ata1.00: configured for UDMA/100
[    0.436490] ata2.01: NODEV after polling detection
[    0.484424] ata2.00: ATAPI: UJDA745 DVD/CDRW, 1.02, max UDMA/33
[    0.501117] ata2.00: configured for UDMA/33
[    0.835145] Freeing initrd memory: 7779k freed
[    0.892272] isapnp: No Plug & Play device found
[    0.892314] usb 3-2: new low speed USB device using uhci_hcd and address 2
[    0.892570] scsi 0:0:0:0: Direct-Access     ATA      IC25N040ATCS05-0 CS4O PQ: 0 ANSI: 5
[    0.892810] sd 0:0:0:0: [sda] 78140160 512-byte logical blocks: (40.0 GB/37.2 GiB)
[    0.892875] sd 0:0:0:0: [sda] Write Protect is off
[    0.892879] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.892912] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.893144]  sda:
[    0.893393] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.896489] scsi 1:0:0:0: CD-ROM            MATSHITA UJDA745 DVD/CDRW 1.02 PQ: 0 ANSI: 5
[    0.903661] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    0.903666] Uniform CD-ROM driver Revision: 3.20
[    0.903824] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    0.903893] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    0.916558]  sda1 sda2 < sda5 >
[    0.945636] sd 0:0:0:0: [sda] Attached SCSI disk
[    0.945660] Freeing unused kernel memory: 656k freed
[    0.946378] Write protecting the kernel text: 4676k
[    0.946433] Write protecting the kernel read-only data: 1840k
[    0.968856] udev: starting version 151
[    1.080372] usb 3-2: configuration #1 chosen from 1 choice
[    1.260250] Intel(R) PRO/1000 Network Driver - version 7.3.21-k5-NAPI
[    1.260280] Copyright (c) 1999-2006 Intel Corporation.
[    1.260416] e1000 0000:02:01.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    1.270939] usbcore: registered new interface driver hiddev
[    1.514678] e1000: 0000:02:01.0: e1000_probe: (PCI:33MHz:32-bit) 00:09:6b:bf:76:16
[    1.515595] input: HID 04d9:0420 as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input5
[    1.515876] generic-usb 0003:04D9:0420.0001: input,hidraw0: USB HID v1.10 Mouse [HID 04d9:0420] on usb-0000:00:1d.1-2/input0
[    1.515910] usbcore: registered new interface driver usbhid
[    1.516068] usbhid: v2.6:USB HID core driver
[    1.549794] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[B][    1.762339] EXT4-fs (sda1): mounted filesystem with ordered data mode
[   19.201024] Adding 1648632k swap on /dev/sda5.  Priority:-1 extents:1 across:1648632k [/B]
[   19.228882] udev: starting version 151
[   19.581514] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   19.589371] intel_rng: FWH not detected
[   19.775041] Linux agpgart interface v0.103
[   19.816215] lp: driver loaded but no devices found
[   19.843937] parport_pc 00:0b: reported by Plug and Play ACPI
[   19.843984] parport0: PC-style at 0x3bc, irq 7 [PCSPP,TRISTATE]
[   19.917048] Non-volatile memory driver v1.3
[   19.919584] irda_init()
[   19.919604] NET: Registered protocol family 23
[   19.931755] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:02/LNXVIDEO:00/input/input6
[   19.931943] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   19.932253] lp0: using parport0 (interrupt-driven).
[   19.984813] agpgart-intel 0000:00:00.0: Intel 855PM Chipset
[   20.095922] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[   20.106514] type=1505 audit(1275635135.208:2):  operation="profile_load" pid=538 name="/sbin/dhclient3"
[   20.107331] type=1505 audit(1275635135.208:3):  operation="profile_load" pid=538 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   20.107801] type=1505 audit(1275635135.208:4):  operation="profile_load" pid=538 name="/usr/lib/connman/scripts/dhclient-script"
[   20.182194] [drm] Initialized drm 1.1.0 20060810
[   20.193502] airo(): Probing for PCI adapters
[   20.193559] airo 0000:02:02.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[   20.193580] airo(): Found an MPI350 card
[   20.207019] ppdev: user-space parallel port driver
[   20.236078] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 3.
[   20.236284] nsc-ircc, chip->init
[   20.236294] nsc-ircc, Found chip at base=0x02e
[   20.236318] nsc-ircc, driver loaded (Dag Brattli)
[   20.236538] nsc_ircc_open(), can't get iobase of 0x2f8
[   20.236568] nsc-ircc, Found chip at base=0x02e
[   20.236592] nsc-ircc, driver loaded (Dag Brattli)
[   20.236596] nsc_ircc_open(), can't get iobase of 0x2f8
[   20.237874] nsc-ircc 00:0c: disabled
[   20.353297] thinkpad_acpi: ThinkPad ACPI Extras v0.24
[   20.353303] thinkpad_acpi: [http://ibm-acpi.sf.net/](http://ibm-acpi.sf.net/)
[   20.353306] thinkpad_acpi: ThinkPad BIOS 1RETDRWW (3.23 ), EC 1RHT71WW-3.04
[   20.353309] thinkpad_acpi: IBM ThinkPad T40 , model 2374PG2
[   20.373888] Registered led device: tpacpi::thinklight
[   20.374625] Registered led device: tpacpi::power
[   20.375055] Registered led device: tpacpi::standby
[   20.385342] thinkpad_acpi: Console audio control enabled, mode: monitor (read only)
[   20.417003] input: ThinkPad Extra Buttons as /devices/platform/thinkpad_acpi/input/input7
[   20.573387] type=1505 audit(1275635135.676:5):  operation="profile_load" pid=648 name="/usr/share/gdm/guest-session/Xsession"
[   20.589194] type=1505 audit(1275635135.692:6):  operation="profile_replace" pid=652 name="/sbin/dhclient3"
[   20.604269] type=1505 audit(1275635135.708:7):  operation="profile_replace" pid=652 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   20.604726] type=1505 audit(1275635135.708:8):  operation="profile_replace" pid=652 name="/usr/lib/connman/scripts/dhclient-script"
[   20.641124] type=1505 audit(1275635135.744:9):  operation="profile_load" pid=654 name="/usr/bin/evince"
[   20.664053] pci 0000:01:00.0: power state changed by ACPI to D0
[   20.664069] pci 0000:01:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[   20.665050] [drm] Initialized radeon 1.32.0 20080528 for 0000:01:00.0 on minor 0
[   20.691274] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x2c6ab1, caps: 0x884793/0x0
[   20.691282] serio: Synaptics pass-through port at isa0060/serio1/input0
[   20.707472] vga16fb: initializing
[   20.707478] vga16fb: mapped to 0xc00a0000
[   20.707697] fb0: VGA16 VGA frame buffer device
[   20.712679] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.727487] type=1505 audit(1275635135.828:10):  operation="profile_load" pid=654 name="/usr/bin/evince-previewer"
[   20.736752] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[   20.880740] type=1505 audit(1275635135.984:11):  operation="profile_load" pid=654 name="/usr/bin/evince-thumbnailer"
[   21.245717] airo(eth1): Firmware version 5.41.00
[   21.245721] airo(eth1): WPA supported.
[   21.245724] airo(eth1): MAC enabled 00:02:8a:a9:69:c3
[   21.245932] yenta_cardbus 0000:02:00.0: CardBus bridge found [1014:0512]
[   21.245955] yenta_cardbus 0000:02:00.0: Using INTVAL to route CSC interrupts to PCI
[   21.245958] yenta_cardbus 0000:02:00.0: Routing CardBus interrupts to PCI
[   21.245964] yenta_cardbus 0000:02:00.0: TI: mfunc 0x01d21022, devctl 0x64
[   21.247484] airo(): Finished probing for PCI adapters
[   21.306212] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[   21.306273] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   21.317681] Console: switching to colour frame buffer device 80x30
[   21.476812] yenta_cardbus 0000:02:00.0: ISA IRQ mask 0x0438, PCI irq 11
[   21.476820] yenta_cardbus 0000:02:00.0: Socket status: 30000020
[   21.476831] yenta_cardbus 0000:02:00.0: pcmcia: parent PCI bridge I/O window: 0x4000 - 0x8fff
[   21.476843] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x4000-0x8fff: clean.
[   21.478225] yenta_cardbus 0000:02:00.0: pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xcfffffff
[   21.478230] yenta_cardbus 0000:02:00.0: pcmcia: parent PCI bridge Memory window: 0xe8000000 - 0xefffffff
[   21.480414] yenta_cardbus 0000:02:00.1: CardBus bridge found [1014:0512]
[   21.480435] yenta_cardbus 0000:02:00.1: Using INTVAL to route CSC interrupts to PCI
[   21.480439] yenta_cardbus 0000:02:00.1: Routing CardBus interrupts to PCI
[   21.480445] yenta_cardbus 0000:02:00.1: TI: mfunc 0x01d21022, devctl 0x64
[   21.712563] yenta_cardbus 0000:02:00.1: ISA IRQ mask 0x0438, PCI irq 11
[   21.712570] yenta_cardbus 0000:02:00.1: Socket status: 30000006
[   21.712584] yenta_cardbus 0000:02:00.1: pcmcia: parent PCI bridge I/O window: 0x4000 - 0x8fff
[   21.712590] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x4000-0x8fff: clean.
[   21.713973] yenta_cardbus 0000:02:00.1: pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xcfffffff
[   21.713978] yenta_cardbus 0000:02:00.1: pcmcia: parent PCI bridge Memory window: 0xe8000000 - 0xefffffff
[   22.116068] pcmcia_socket pcmcia_socket0: pccard: CardBus card inserted into slot 0
[   22.116119] pci 0000:03:00.0: reg 10 io port: [0x00-0xff]
[   22.116129] pci 0000:03:00.0: reg 14 32bit mmio: [0x000000-0x0000ff]
[   22.116188] pci 0000:03:00.0: supports D1 D2
[   22.116192] pci 0000:03:00.0: PME# supported from D1 D2 D3hot D3cold
[   22.116198] pci 0000:03:00.0: PME# disabled
[   22.134604] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   22.134645] 8139cp 0000:03:00.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[   22.143746] 8139too Fast Ethernet driver 0.9.28
[   22.143799] 8139too 0000:03:00.0: enabling device (0000 -> 0003)
[   22.143815] 8139too 0000:03:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[   22.143834] 8139too 0000:03:00.0: setting latency timer to 64
[   22.146348] eth2: RealTek RTL8139 at 0x4000, 00:0a:cd:18:2c:b5, IRQ 11
[   22.165636] eth2: link down
[   22.166003] ADDRCONF(NETDEV_UP): eth2: link is not ready
[   22.232098] intel8x0_measure_ac97_clock: measured 55428 usecs (2670 samples)
[   22.232104] intel8x0: clocking to 48000
[   22.412622] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x100-0x3af: clean.
[   22.413644] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   22.414085] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x820-0x8ff: clean.
[   22.414459] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xc00-0xcf7: clean.
[   22.415000] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xa00-0xaff: clean.
[   22.415754] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   22.416824] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   22.417263] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   22.417637] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   22.418175] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   23.096476] agpgart-intel 0000:00:00.0: AGP 2.0 bridge
[   23.096498] agpgart-intel 0000:00:00.0: putting AGP V2 device into 4x mode
[   23.096539] pci 0000:01:00.0: putting AGP V2 device into 4x mode
[   23.297644] psmouse serio2: ID: 10 00 64
[   23.321277] [drm] Setting GART location based on new memory map
[   23.321378] [drm] Loading R100 Microcode
[   23.321385] platform radeon_cp.0: firmware: requesting radeon/R100_cp.bin
[   23.329384] [drm] writeback test succeeded in 2 usecs
[   23.509443] eth2: link up, 100Mbps, full-duplex, lpa 0x45E1
[   23.509728] ADDRCONF(NETDEV_CHANGE): eth2: link becomes ready
[   26.698884] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   26.933056] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/serio2/input/input9
[   27.421900] ttyS1: LSR safety check engaged!
[   32.020042] eth1: no IPv6 routers present
[   34.440034] eth2: no IPv6 routers present
</code>

and

lsmod

<code>
lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
8139too                18545  0 
8139cp                 16186  0 
mii                     4381  2 8139too,8139cp
pcmcia                 33024  0 
snd_intel8x0           25588  2 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
aes_i586                7268  1 
snd_mixer_oss          13746  1 snd_pcm_oss
aes_generic            26863  1 aes_i586
snd_pcm                70662  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
joydev                  8708  0 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
vga16fb                11385  1 
vgastate                8961  1 vga16fb
radeon                674135  2 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ttm                    49943  1 radeon
thinkpad_acpi          68083  0 
drm_kms_helper         29297  1 radeon
yenta_socket           20408  3 
snd                    54148  15 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device,thinkpad_acpi
led_class               2864  1 thinkpad_acpi
ppdev                   5259  0 
rsrc_nonstatic         10015  1 yenta_socket
airo                   67901  0 
drm                   162471  5 radeon,ttm,drm_kms_helper
i2c_algo_bit            5028  1 radeon
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
intel_agp              24177  1 
psmouse                63245  0 
video                  17375  0 
nvram                   6171  1 thinkpad_acpi
irda                  186556  0 
crc_ccitt               1339  1 irda
parport_pc             25962  1 
lp                      7028  0 
soundcore               6620  1 snd
output                  1871  1 video
serio_raw               3978  0 
agpgart                31724  3 ttm,drm,intel_agp
shpchp                 28820  0 
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
parport                32635  3 ppdev,parport_pc,lp
usbhid                 36110  0 
hid                    67032  1 usbhid
e1000                  97396  0
</code>

THANK 'S YOUR ANSWER

Cedric

---

### Post by Cloud_704 on 2010-09-22
> **chili555 said:**
> Please open a terminal and do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add these lines:```
# these aes modules break the airo driver
blacklist padlock-aes
blacklist geode-aes
```Proofread, save and close gedit. Reboot and let us know if the wireless now works. If not, please post:```
lsmod
```Thanks.

I have same problem as original poster. Doing the blacklist thing did not work for me. I'm on a Thinkpad R40, not a T40, but the output to the queries above (lshw, et cetera) look the same as far as I can see.

Here is my lsmod output:```
Module                  Size  Used by
binfmt_misc             6587  1 
snd_intel8x0           25588  2 
pcmcia                 33024  0 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
vga16fb                11385  0 
vgastate                8961  1 vga16fb
thinkpad_acpi          68083  0 
snd_pcm                70662  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
aes_i586                7268  1 
snd_seq_dummy           1338  0 
aes_generic            26863  1 aes_i586
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
joydev                  8708  0 
radeon                674135  2 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ttm                    49943  1 radeon
snd                    54148  15 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,thinkpad_acpi,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         29297  1 radeon
yenta_socket           20408  1 
rsrc_nonstatic         10015  1 yenta_socket
ppdev                   5259  0 
nsc_ircc               18220  0 
led_class               2864  1 thinkpad_acpi
video                  17375  0 
drm                   162471  4 radeon,ttm,drm_kms_helper
i2c_algo_bit            5028  1 radeon
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
airo                   67901  0 
parport_pc             25962  1 
nvram                   6171  1 thinkpad_acpi
irda                  186556  1 nsc_ircc
crc_ccitt               1339  1 irda
intel_agp              24177  1 
soundcore               6620  1 snd
output                  1871  1 video
psmouse                63245  0 
serio_raw               3978  0 
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
agpgart                31724  3 ttm,drm,intel_agp
shpchp                 28820  0 
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
floppy                 53016  1 
e100                   28211  0 
mii                     4381  1 e100
```

---

### Post by tenwiseman on 2010-09-23
Try here

[http://ubuntuforums.org/showthread.php?t=1514304](http://ubuntuforums.org/showthread.php?t=1514304)

---

