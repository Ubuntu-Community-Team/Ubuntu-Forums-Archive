---
title: "zd1211 in ubuntu?Sparklan WUBZ-103 showing Fiberline WL-430U"
date: 2009-02-07
forum: Networking &amp; Wireless
---

### Post by RedeyeAce on 2009-02-07
EDIT: Solved!!!

the -110 error is a timeout issue, it turns out the permissions on the directory for the drivers was incorrect, this was solved by the following

sudo chown -R root.root /lib/firmware/zd1211
sudo find /lib/firmware -type d -exec chmod 755 {} \;
sudo find /lib/firmware/zd1211 -type f -exec chmod 644 {} \;

My thanks go to Hin-Tak Leung for providing solution
And To Kerry_S who was extremely helpfull in aiding me toward this stage

EDIT: 2nd page post 16 is starting from scratch again with a clean install, please pick this up from there.

Please help peeps, even someone with little knowledge has more knowledge than I. I think this should be simple to fix.

I am learning (well i feel) a lot along this process and have attempted lots of stuff with guides and info i have found out along the way, but need help. 

I posted earlier, but didnt adhere to sticky post so here goes again.

I need to get a sparklan usb wifi card working in  ubuntu 8.1.

Issue: instaling Sparklan WUBZ-103
been to Sparklan.com downloaded linux driver and its ZD1211 drivers

 I run lsusb = Fiberline WL-430U, so is this correct for the zd1211 drivers? EDIT: I have now found out that this is a yes! [http://linuxwireless.org/en/users/Drivers/zd1211rw/devices](http://linuxwireless.org/en/users/Drivers/zd1211rw/devices)

I didnt know it was inbuilt to start with and have tried to build the driver from the website download and make that work, rather unsuccsesfully, it kept erroring on certin config and directories. Original Post=http://ubuntuforums.org/showthread.php?t=1063154

the downloaded file from sparklan.com is trying to install ZD1211 diver which according to [http://www.linuxwireless.org/en/users/Drivers/zd1211rw](http://www.linuxwireless.org/en/users/Drivers/zd1211rw) should already be installed in the linux kernel.

Are the ZD1211 drivers already included in Ubuntu 8.1 then? EDIT: I have found the ZD1211 drivers using synaptics and installed them but it didnt do anything

How do i get the inbuilt driver to work? EDIT: I have found supposedly more updated drivers (Firmware) from [http://sourceforge.net/project/showfiles.php?group_id=129083&package_id=187875&release_id=544191](http://sourceforge.net/project/showfiles.php?group_id=129083&package_id=187875&release_id=544191)

So i am currently still stuck on getting it working :(

Thanks

---

### Post by RedeyeAce on 2009-02-08
Just tried using sudo lshw -C network, cos ive read it lists hardware and drivers and this came up.

Does this mean the driver is installed, however the network is disabled. I.e. i just need to setup the wireless connection?



john@john-laptop:~/Documents/Downloads/Drivers/Sparklan/Uncompresed$ sudo lshw -C network
[sudo] password for john: 
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 8
       bus info: pci@0000:00:08.0
       logical name: eth0
       version: 10
       serial: 00:e0:18:1b:7b:3c
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.66 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: d2:ac:65:e7:77:6c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
  *-network:1 DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:0e:8e:16:62:72
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

---

### Post by RedeyeAce on 2009-02-08
lspci=
john@john-laptop:~/Documents/Downloads/Drivers/Sparklan/Uncompresed$ lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:06.0 Multimedia audio controller: ESS Technology ES1988 Allegro-1 (rev 12)
00:06.1 Communication controller: ESS Technology ESS Modem (rev 12)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
00:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0a.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 80)
00:0a.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 80)
01:00.0 VGA compatible controller: S3 Inc. 86C270-294 Savage/MX-MV (rev 11)

---

### Post by RedeyeAce on 2009-02-08
iwconfig=
john@john-laptop:~/Documents/Downloads/Drivers/Sparklan/Uncompresed$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

john@john-laptop:~/Documents/Downloads/Drivers/Sparklan/Uncompresed$

---

### Post by RedeyeAce on 2009-02-08
ifconfig=

john@john-laptop:~/Documents/Downloads/Drivers/Sparklan/Uncompresed$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:e0:18:1b:7b:3c  
          inet addr:192.168.1.66  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:18ff:fe1b:7b3c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:69554 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42094 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:52391611 (52.3 MB)  TX bytes:5008866 (5.0 MB)
          Interrupt:9 Base address:0xf000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by RedeyeAce on 2009-02-08
ls /lib/modules/`uname -r`/build
arch           drivers   init    lib             net       sound
block          firmware  ipc     Makefile        samples   ubuntu
crypto         fs        Kbuild  mm              scripts   usr
Documentation  include   kernel  Module.symvers  security


So theres no install folder and config file.. Is this why i have no luck running the driver?

I was just about to follow the procedure for the ndiswrapper however this is the ifrst thing it asks you to do.. So how do i get these files? im presuming i jut cant create them and there must be something i need to install.

---

### Post by RedeyeAce on 2009-02-08
I have just been playing with synaptic package manager to install some buid stuff and just out of curiosity i looked for the zd1211 files and found them, so ive installed them but again i get nowhere, ive restarted the system and nothing wireless still shows.

Please can someone give some input here, i think ive done a lot on my own, but im obviously out of my depth.

---

### Post by RedeyeAce on 2009-02-08
managed to get ndiswrapper installed and installed the gui.  

now this says zd1211bu ihardware present yes in the gui

john@john-laptop:~$ ndiswrapper -l
zd1211bu : driver installed
	device (1582:6003) present (alternate driver: zd1211rw)

so it looks as tho the system know there is a driver zd1211rw available in the system, i just dont know how to use it.

---

### Post by kerry_s on 2009-02-08
your iwconfig shows it as wlan0, so:

sudo ifup wlan0
sudo iwconfig wlan0 essid "your-wireless's-name"
sudo dhclient wlan0

arch has is fantastic with my zd1211, i use there netcfg works every time.

---

### Post by RedeyeAce on 2009-02-08
oooh a reply yay, thanks kerry, was getting a bit fed up talking to meself and getting nowhere lol

just tried the first part and get the following

john@john-laptop:~$ sudo ifup wlan0
[sudo] password for john: 
Ignoring unknown interface wlan0=wlan0.
john@john-laptop:~$ 

also with the windows ndiswrapper gui thing, the configure network icon comes up with could not find network configuration tool.

So looks like i cant use the ndiswraper either.

can someone hold my hand through this procedure please, perhaps i need to start back from the beginning or something?

Ive read a lot and tried a lot now perhaps its something easy, i dunno anymore.

ooh and what is this arch has thing please? are you suggesting that it could be easier to configure and setup this usb device?

---

### Post by RedeyeAce on 2009-02-09
So anyone with any ideas?

---

### Post by kerry_s on 2009-02-09
for the zd1211 you only need to install the firmware, it's in the repo.

**sudo apt-get install zd1211-firmware**
if it doesn't find it, you probably don't have all your repo's on.

post the /var/log/dmesg.log

that netcfg thing is arch specific, your not ready for arch linux, everything is manual setup. ;)

---

### Post by RedeyeAce on 2009-02-09
john@john-laptop:~$ sudo apt-get install zd1211-firmware
[sudo] password for john: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package zd1211-firmware is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package zd1211-firmware has no installation candidate


john@john-laptop:~$ /var/log/dmesg.log
bash: /var/log/dmesg.log: No such file or directory
john@john-laptop:~$ gedit /var/log/dmesg.log

just tries to create dmesg.log, i probably used the wrong comand but thought gedit would open that file if it was there.

Thanks for your help i do appreciate it. what would you like me to do next and yeh, im definately not ready for the arch thing if its manual only lol

---

### Post by RedeyeAce on 2009-02-09
ok so i have found the zd1211-firmware from [http://sourceforge.net/project/showfiles.php?group_id=129083&package_id=187875&release_id=544191](http://sourceforge.net/project/showfiles.php?group_id=129083&package_id=187875&release_id=544191)

I couldnt work out how to install them to /lib/firmware/zd1211 as i needed root access, but have found the lovely tool called nautilus so i used that and overwrote all the files in that directory to the files downloaded from sourceforge.

Also on my travels i have found that the fiberline is indeed using the zd1211 drivers [http://linuxwireless.org/en/users/Drivers/zd1211rw/devices](http://linuxwireless.org/en/users/Drivers/zd1211rw/devices)

So i know we are definately on the right track.

So i reboot the computer without the wired connection thinking it would pick up the usb device but when i get into ubuntu i'm at the same position with the usb wireless not working.

What would you like me to try now please :) if it wasnt for the fact that im taking on board and learning a lot i think this process would of annoyed the hell out of me :)

Did i do right? what commands do i have to run to see where we are again, or what would you like me to do next please :)

---

### Post by RedeyeAce on 2009-02-09
ok so i used the gui and navigated to the var/log directory and found 2 files dmesg and dmesg.0

here is the log from dmesg

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-11-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Jan 29 19:24:39 UTC 2009 (Ubuntu 2.6.27-11.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
[    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e9400 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000000fff0000 (usable)
[    0.000000]  BIOS-e820: 000000000fff0000 - 000000000ffffc00 (ACPI data)
[    0.000000]  BIOS-e820: 000000000ffffc00 - 0000000010000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fffe9400 - 0000000100000000 (reserved)
[    0.000000] DMI 2.1 present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0xfff0 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to fff0000 @ 10000-16000
[    0.000000] RAMDISK: 0f80e000 - 0ffdfe52
[    0.000000] ACPI: RSDP 000F7050, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 0FFFC6ED, 002C (r1 PTLTD    RSDT    6040001  LTP        0)
[    0.000000] ACPI: FACP 0FFFFB65, 0074 (r1 ASUS   L8400B    6040001 PTL     F4240)
[    0.000000] ACPI: DSDT 0FFFC719, 344C (r1  Intel   Trajan  6040001 MSFT  1000004)
[    0.000000] ACPI: FACS 0FFFFFC0, 0040
[    0.000000] ACPI: BOOT 0FFFFBD9, 0027 (r1 PTLTD  $SBFTBL$  6040001  LTP        1)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 255MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 0fff0000
[    0.000000]   low ram: 00000000 - 0fff0000
[    0.000000]   bootmap 00012000 - 00014000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 000fff0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c29e0]    TEXT DATA BSS ==> [0000100000 - 00005c29e0]
[    0.000000]   #4 [000f80e000 - 000ffdfe52]          RAMDISK ==> [000f80e000 - 000ffdfe52]
[    0.000000]   #5 [00005c3000 - 00005c6000]    INIT_PG_TABLE ==> [00005c3000 - 00005c6000]
[    0.000000]   #6 [000009f400 - 0000100000]    BIOS reserved ==> [000009f400 - 0000100000]
[    0.000000]   #7 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #8 [0000012000 - 0000014000]          BOOTMAP ==> [0000012000 - 0000014000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0000fff0
[    0.000000]   HighMem  0x0000fff0 -> 0x0000fff0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0000fff0
[    0.000000] On node 0 totalpages: 65407
[    0.000000] free_area_init_node: node 0, pgdat c048c680, node_mem_map c1000240
[    0.000000]   DMA zone: 3947 pages, LIFO batch:0
[    0.000000]   Normal zone: 60884 pages, LIFO batch:15
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffb000 (01241000)
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000ea000
[    0.000000] PM: Registered nosave memory: 00000000000ea000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 10000000:effe9400)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 64831
[    0.000000] Kernel command line: root=UUID=aa28be40-5548-45de-a7b8-ecb884e60926 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 1024 (order: 10, 4096 bytes)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PMTIMER calibration value
[    0.000000] Detected 851.929 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.004000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[    0.004000] Memory: 246024k/262080k available (2576k kernel code, 15484k reserved, 1165k data, 424k init, 0k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xd0800000 - 0xff3fe000   ( 747 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xcfff0000   ( 255 MB)
[    0.004000]       .init : 0xc04ad000 - 0xc0517000   ( 424 kB)
[    0.004000]       .data : 0xc03840da - 0xc04a7680   (1165 kB)
[    0.004000]       .text : 0xc0100000 - 0xc03840da   (2576 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.004022] Calibrating delay loop (skipped), value calculated using timer frequency.. 1703.85 BogoMIPS (lpj=3407716)
[    0.004074] Security Framework initialized
[    0.004098] SELinux:  Disabled at boot.
[    0.004162] AppArmor: AppArmor initialized
[    0.004185] Mount-cache hash table entries: 512
[    0.004622] Initializing cgroup subsys ns
[    0.004634] Initializing cgroup subsys cpuacct
[    0.004642] Initializing cgroup subsys memory
[    0.004682] CPU: L1 I cache: 16K, L1 D cache: 16K
[    0.004690] CPU: L2 cache: 256K
[    0.004736] Checking 'hlt' instruction... OK.
[    0.020848] SMP alternatives: switching to UP code
[    0.032056] Freeing SMP alternatives: 11k freed
[    0.032069] ACPI: Core revision 20080609
[    0.034482] ACPI: Checking initramfs for custom DSDT
[    0.860185] weird, boot CPU (#0) not listedby the BIOS.
[    0.860197] SMP motherboard not detected.
[    0.860205] Local APIC not detected. Using dummy APIC emulation.
[    0.860211] SMP disabled
[    0.860419] Brought up 1 CPUs
[    0.860427] Total of 1 processors activated (1703.85 BogoMIPS).
[    0.860460] CPU0 attaching NULL sched-domain.
[    0.861193] net_namespace: 840 bytes
[    0.861225] Booting paravirtualized kernel on bare hardware
[    0.864089] Time: 14:09:08  Date: 02/09/09
[    0.864183] NET: Registered protocol family 16
[    0.865237] EISA bus registered
[    0.865298] ACPI: bus type pci registered
[    0.866184] PCI: PCI BIOS revision 2.10 entry at 0xfd9a6, last bus=1
[    0.866195] PCI: Using configuration type 1 for base access
[    0.870786] ACPI: EC: Look up EC in DSDT
[    0.878304] ACPI: Interpreter enabled
[    0.878322] ACPI: (supports S0 S1 S3 S4 S5)
[    0.878375] ACPI: Using PIC for interrupt routing
[    0.883298] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.933623] ACPI: EC: GPE = 0x9, I/O: command/status = 0x66, data = 0x62
[    0.933634] ACPI: EC: driver started in interrupt mode
[    0.933817] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.934013] PCI: 0000:00:00.0 reg 10 32bit mmio: [f8000000, fbffffff]
[    0.934126] PCI: 0000:00:06.0 reg 10 io port: [f800, f8ff]
[    0.934178] pci 0000:00:06.0: supports D1
[    0.934184] pci 0000:00:06.0: supports D2
[    0.934191] pci 0000:00:06.0: PME# supported from D1 D2 D3hot
[    0.934201] pci 0000:00:06.0: PME# disabled
[    0.934236] PCI: 0000:00:06.1 reg 10 io port: [f400, f4ff]
[    0.934287] pci 0000:00:06.1: supports D1
[    0.934292] pci 0000:00:06.1: supports D2
[    0.934299] pci 0000:00:06.1: PME# supported from D1 D2 D3hot D3cold
[    0.934307] pci 0000:00:06.1: PME# disabled
[    0.934415] PCI: 0000:00:07.1 reg 20 io port: [fcf0, fcff]
[    0.934480] PCI: 0000:00:07.2 reg 20 io port: [fcc0, fcdf]
[    0.934566] pci 0000:00:07.3: quirk: region 8000-803f claimed by PIIX4 ACPI
[    0.934576] pci 0000:00:07.3: quirk: region 2180-218f claimed by PIIX4 SMB
[    0.936091] PCI: 0000:00:08.0 reg 10 io port: [f000, f0ff]
[    0.936104] PCI: 0000:00:08.0 reg 14 32bit mmio: [fedffc00, fedffcff]
[    0.936147] pci 0000:00:08.0: supports D1
[    0.936153] pci 0000:00:08.0: supports D2
[    0.936159] pci 0000:00:08.0: PME# supported from D1 D2 D3hot D3cold
[    0.936167] pci 0000:00:08.0: PME# disabled
[    0.936207] PCI: 0000:00:0a.0 reg 10 32bit mmio: [0, fff]
[    0.936227] pci 0000:00:0a.0: supports D1
[    0.936232] pci 0000:00:0a.0: supports D2
[    0.936238] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.936247] pci 0000:00:0a.0: PME# disabled
[    0.936282] PCI: 0000:00:0a.1 reg 10 32bit mmio: [0, fff]
[    0.936301] pci 0000:00:0a.1: supports D1
[    0.936306] pci 0000:00:0a.1: supports D2
[    0.936312] pci 0000:00:0a.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.936321] pci 0000:00:0a.1: PME# disabled
[    0.936403] PCI: 0000:01:00.0 reg 10 32bit mmio: [f0000000, f7ffffff]
[    0.936436] PCI: 0000:01:00.0 reg 30 32bit mmio: [0, ffff]
[    0.936456] pci 0000:01:00.0: supports D1
[    0.936461] pci 0000:01:00.0: supports D2
[    0.936507] PCI: bridge 0000:00:01.0 32bit mmio: [f0000000, f7ffffff]
[    0.936556] bus 00 -> node 0
[    0.936585] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.942210] ACPI: PCI Interrupt Link [LNKA] (IRQs *9)
[    0.942541] ACPI: PCI Interrupt Link [LNKB] (IRQs 9) *0, disabled.
[    0.942883] ACPI: PCI Interrupt Link [LNKC] (IRQs 5 6 7 10) *0, disabled.
[    0.943212] ACPI: PCI Interrupt Link [LNKD] (IRQs 9) *0, disabled.
[    0.943671] ACPI: Power Resource [PFAN] (off)
[    0.943867] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.943993] pnp: PnP ACPI init
[    0.944063] ACPI: bus type pnp registered
[    1.028503] pnp: PnP ACPI: found 13 devices
[    1.028513] ACPI: ACPI bus type pnp unregistered
[    1.028526] PnPBIOS: Disabled by ACPI PNP
[    1.029758] PCI: Using ACPI for IRQ routing
[    1.030048] NET: Registered protocol family 8
[    1.030048] NET: Registered protocol family 20
[    1.030048] NetLabel: Initializing
[    1.030048] NetLabel:  domain hash size = 128
[    1.030048] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.030048] NetLabel:  unlabeled traffic allowed by default
[    1.030048] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    1.030048]    actual entries 65620
[    1.032406] AppArmor: AppArmor Filesystem Enabled
[    1.032677] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    1.032691] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
[    1.032700] system 00:00: iomem range 0x100000-0xfffffff could not be reserved
[    1.032727] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    1.032739] system 00:02: ioport range 0x398-0x399 has been reserved
[    1.032748] system 00:02: ioport range 0x2180-0x218f has been reserved
[    1.032757] system 00:02: ioport range 0x8000-0x803f has been reserved
[    1.032766] system 00:02: ioport range 0x3800-0x383f has been reserved
[    1.032776] system 00:02: iomem range 0xfff80000-0xffffffff could not be reserved
[    1.069382] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    1.069393] pci 0000:00:01.0:   IO window: disabled
[    1.069403] pci 0000:00:01.0:   MEM window: 0xf0000000-0xf7ffffff
[    1.069413] pci 0000:00:01.0:   PREFETCH window: 0x00000030000000-0x000000300fffff
[    1.069427] pci 0000:00:0a.0: CardBus bridge, secondary bus 0000:02
[    1.069434] pci 0000:00:0a.0:   IO window: 0x001000-0x0010ff
[    1.069443] pci 0000:00:0a.0:   IO window: 0x001400-0x0014ff
[    1.069453] pci 0000:00:0a.0:   PREFETCH window: 0x20000000-0x23ffffff
[    1.069462] pci 0000:00:0a.0:   MEM window: 0x24000000-0x27ffffff
[    1.069472] pci 0000:00:0a.1: CardBus bridge, secondary bus 0000:06
[    1.069479] pci 0000:00:0a.1:   IO window: 0x001800-0x0018ff
[    1.069487] pci 0000:00:0a.1:   IO window: 0x001c00-0x001cff
[    1.069496] pci 0000:00:0a.1:   PREFETCH window: 0x28000000-0x2bffffff
[    1.069505] pci 0000:00:0a.1:   MEM window: 0x2c000000-0x2fffffff
[    1.070724] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 9
[    1.070735] PCI: setting IRQ 9 as level-triggered
[    1.070744] pci 0000:00:0a.0: PCI INT A -> Link[LNKA] -> GSI 9 (level, low) -> IRQ 9
[    1.070756] pci 0000:00:0a.0: setting latency timer to 64
[    1.071764] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 9
[    1.071774] pci 0000:00:0a.1: PCI INT B -> Link[LNKB] -> GSI 9 (level, low) -> IRQ 9
[    1.071785] pci 0000:00:0a.1: setting latency timer to 64
[    1.071795] bus: 00 index 0 io port: [0, ffff]
[    1.071801] bus: 00 index 1 mmio: [0, ffffffff]
[    1.071807] bus: 01 index 0 mmio: [0, 0]
[    1.071813] bus: 01 index 1 mmio: [f0000000, f7ffffff]
[    1.071820] bus: 01 index 2 mmio: [30000000, 300fffff]
[    1.071826] bus: 01 index 3 mmio: [0, 0]
[    1.071833] bus: 02 index 0 io port: [1000, 10ff]
[    1.071839] bus: 02 index 1 io port: [1400, 14ff]
[    1.071846] bus: 02 index 2 mmio: [20000000, 23ffffff]
[    1.071852] bus: 02 index 3 mmio: [24000000, 27ffffff]
[    1.071859] bus: 06 index 0 io port: [1800, 18ff]
[    1.071865] bus: 06 index 1 io port: [1c00, 1cff]
[    1.071871] bus: 06 index 2 mmio: [28000000, 2bffffff]
[    1.071878] bus: 06 index 3 mmio: [2c000000, 2fffffff]
[    1.071913] NET: Registered protocol family 2
[    1.072400] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[    1.073129] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[    1.073323] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    1.073514] TCP: Hash tables configured (established 8192 bind 8192)
[    1.073523] TCP reno registered
[    1.073841] NET: Registered protocol family 1
[    1.074224] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[    1.894008]  it is
[    2.934312] Freeing initrd memory: 8007k freed
[    2.934958] Simple Boot Flag at 0x37 set to 0x1
[    2.936364] audit: initializing netlink socket (disabled)
[    2.936414] type=2000 audit(1234188549.936:1): initialized
[    2.952218] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    2.960719] VFS: Disk quotas dquot_6.5.1
[    2.961110] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    2.961469] msgmni has been set to 496
[    2.961945] io scheduler noop registered
[    2.961954] io scheduler anticipatory registered
[    2.961961] io scheduler deadline registered
[    2.962025] io scheduler cfq registered (default)
[    2.962058] pci 0000:00:00.0: Limiting direct PCI/PCI transfers
[    2.962108] pci 0000:01:00.0: Boot video device
[    2.963179] isapnp: Scanning for PnP cards...
[    3.317046] isapnp: No Plug & Play device found
[    3.482143] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    3.482410] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    3.482948] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a NS16550A
[    3.485519] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    3.491558] brd: module loaded
[    3.491829] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    3.492428] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUE] at 0x60,0x64 irq 1,12
[    3.497944] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.497960] serio: i8042 AUX port at 0x60,0x64 irq 12
[    3.499309] mice: PS/2 mouse device common for all mice
[    3.499806] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    3.499843] rtc0: alarms up to one month, y3k
[    3.500282] EISA: Probing bus 0 at eisa.0
[    3.500300] Cannot allocate resource for EISA slot 1
[    3.500314] Cannot allocate resource for EISA slot 3
[    3.500341] Cannot allocate resource for EISA slot 8
[    3.500347] EISA: Detected 0 cards.
[    3.500356] cpuidle: using governor ladder
[    3.500362] cpuidle: using governor menu
[    3.502127] TCP cubic registered
[    3.502217] Using IPI No-Shortcut mode
[    3.503143] registered taskstats version 1
[    3.503427]   Magic number: 13:749:181
[    3.503561] tty ttyr7: hash matches
[    3.503814] rtc_cmos 00:04: setting system clock to 2009-02-09 14:09:11 UTC (1234188551)
[    3.503824] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.503830] EDD information not available.
[    3.505543] Freeing unused kernel memory: 424k freed
[    3.505716] Write protecting the kernel text: 2580k
[    3.505819] Write protecting the kernel read-only data: 940k
[    3.534770] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    4.120183] fuse init (API version 7.9)
[    4.252759] ACPI: Transitioning device [FAN] to D3
[    4.252949] fan PNP0C0B:00: registered as cooling_device0
[    4.252968] ACPI: Fan [FAN] (off)
[    4.283624] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    4.283781] processor ACPI0007:00: registered as cooling_device1
[    4.283793] ACPI: Processor [CPU0] (supports 4 throttling states)
[    4.305089] thermal LNXTHERM:01: registered as thermal_zone0
[    4.311562] ACPI: Thermal Zone [THRM] (70 C)
[    6.176542] No dock devices found.
[    6.414648] SCSI subsystem initialized
[    6.433779] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    6.433849] 8139cp 0000:00:08.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[    6.433860] 8139cp 0000:00:08.0: Try the "8139too" driver instead.
[    6.454424] 8139too Fast Ethernet driver 0.9.28
[    6.506444] 8139too 0000:00:08.0: enabling device (0000 -> 0003)
[    6.507640] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 9
[    6.507653] 8139too 0000:00:08.0: PCI INT A -> Link[LNKD] -> GSI 9 (level, low) -> IRQ 9
[    6.508860] eth0: RealTek RTL8139 at 0xf000, 00:e0:18:1b:7b:3c, IRQ 9
[    6.508868] eth0:  Identified 8139 chip type 'RTL-8139C'
[    6.608773] usbcore: registered new interface driver usbfs
[    6.608844] usbcore: registered new interface driver hub
[    6.612114] usbcore: registered new device driver usb
[    6.625385] USB Universal Host Controller Interface driver v3.0
[    6.625540] uhci_hcd 0000:00:07.2: enabling device (0000 -> 0001)
[    6.625560] uhci_hcd 0000:00:07.2: PCI INT D -> Link[LNKD] -> GSI 9 (level, low) -> IRQ 9
[    6.625586] uhci_hcd 0000:00:07.2: UHCI Host Controller
[    6.625722] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[    6.625768] uhci_hcd 0000:00:07.2: irq 9, io base 0x0000fcc0
[    6.626296] usb usb1: configuration #1 chosen from 1 choice
[    6.626382] hub 1-0:1.0: USB hub found
[    6.626410] hub 1-0:1.0: 2 ports detected
[    6.628805] libata version 3.00 loaded.
[    6.848323] ata_piix 0000:00:07.1: version 2.12
[    6.849550] scsi0 : ata_piix
[    6.850019] scsi1 : ata_piix
[    6.850134] ata1: PATA max UDMA/33 cmd 0x1f0 ctl 0x3f6 bmdma 0xfcf0 irq 14
[    6.850144] ata2: PATA max UDMA/33 cmd 0x170 ctl 0x376 bmdma 0xfcf8 irq 15
[    6.960152] usb 1-2: new full speed USB device using uhci_hcd and address 2
[    7.357770] ata1.00: ATA-5: IBM-DJSA-210, JS2OAB8A, max UDMA/66
[    7.357783] ata1.00: 19640880 sectors, multi 16: LBA 
[    7.357865] ata1.01: ATAPI: TOSHIBA DVD-ROM SD-C2502, 1711, max UDMA/33
[    7.372814] ata1.00: configured for UDMA/33
[    7.388516] ata1.01: configured for UDMA/33
[    7.388625] ata2: port disabled. ignoring.
[    7.388982] scsi 0:0:0:0: Direct-Access     ATA      IBM-DJSA-210     JS2O PQ: 0 ANSI: 5
[    7.391161] scsi 0:0:1:0: CD-ROM            TOSHIBA  DVD-ROM SD-C2502 1711 PQ: 0 ANSI: 5
[    8.493760] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    8.493891] scsi 0:0:1:0: Attached scsi generic sg1 type 5
[    8.584469] Driver 'sd' needs updating - please use bus_type methods
[    8.584795] sd 0:0:0:0: [sda] 19640880 512-byte hardware sectors (10056 MB)
[    8.584847] sd 0:0:0:0: [sda] Write Protect is off
[    8.584856] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    8.584938] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    8.585137] sd 0:0:0:0: [sda] 19640880 512-byte hardware sectors (10056 MB)
[    8.585183] sd 0:0:0:0: [sda] Write Protect is off
[    8.585191] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    8.585271] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    8.585284]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[    8.639385] Marking TSC unstable due to TSC halts in idle
[    8.940185]  sda1 sda2 < sda5 >
[    8.976378] sd 0:0:0:0: [sda] Attached SCSI disk
[    9.030023] sr0: scsi3-mmc drive: 24x/24x cd/rw xa/form2 cdda tray
[    9.030036] Uniform CD-ROM driver Revision: 3.20
[    9.030362] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    9.665591] PM: Starting manual resume from disk
[    9.665607] PM: Resume from partition 8:5
[    9.665613] PM: Checking hibernation image.
[    9.666082] PM: Resume from disk failed.
[    9.803118] kjournald starting.  Commit interval 5 seconds
[    9.803160] EXT3-fs: mounted filesystem with ordered data mode.
[   11.960107] uhci_hcd 0000:00:07.2: Unlink after no-IRQ?  Controller is probably using the wrong IRQ.
[   22.072057] usb 1-2: device descriptor read/64, error -110
[   22.379950] udevd version 124 started
[   24.675588] Linux agpgart interface v0.103
[   24.866258] agpgart-intel 0000:00:00.0: Intel 440BX Chipset
[   24.936061] agpgart-intel 0000:00:00.0: AGP aperture is 64M @ 0xf8000000
[   24.988468] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   25.899809] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   25.992614] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   26.192160] Yenta: CardBus bridge found at 0000:00:0a.0 [1043:1044]
[   26.320893] Yenta: ISA IRQ mask 0x0cb8, PCI irq 9
[   26.320904] Socket status: 30000006
[   26.420508] Yenta: CardBus bridge found at 0000:00:0a.1 [1043:1044]
[   26.548887] Yenta: ISA IRQ mask 0x0cb8, PCI irq 9
[   26.548898] Socket status: 30000006
[   26.551901] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[   26.560148] ACPI: Power Button (FF) [PWRF]
[   26.560610] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input4
[   26.576068] ACPI: Sleep Button (CM) [SLPB]
[   26.576431] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input5
[   26.576643] ACPI: Lid Switch [LID]
[   26.616494] ACPI: I/O resource piix4_smbus [0x2180-0x2187] conflicts with ACPI region SM06 [0x2186-0x2186]
[   26.616509] ACPI: Device needs an ACPI driver
[   26.616526] piix4_smbus 0000:00:07.3: SMBus Host Controller at 0x2180, revision 0
[   26.668803] ACPI: AC Adapter [AC] (on-line)
[   27.600569] ACPI: Battery Slot [BAT0] (battery present)
[   28.201446] Synaptics Touchpad, model: 1, fw: 4.6, id: 0x135ea1, caps: 0x804713/0x0
[   28.241155] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6
[   30.008458] irda_init()
[   30.008503] NET: Registered protocol family 23
[   30.202121] parport_pc 00:09: reported by Plug and Play ACPI
[   30.202187] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   30.288781] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 3.
[   30.288846] nsc-ircc, chip->init
[   30.288854] nsc-ircc, Found chip at base=0x398
[   30.288887] nsc-ircc, driver loaded (Dag Brattli)
[   30.288909] nsc_ircc_open(), can't get iobase of 0x2f8
[   30.288937] nsc-ircc, Found chip at base=0x398
[   30.288969] nsc-ircc, driver loaded (Dag Brattli)
[   30.288977] nsc_ircc_open(), can't get iobase of 0x2f8
[   30.296217] nsc-ircc 00:0b: disabled
[   30.804699] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
[   30.804713] PCI: setting IRQ 10 as level-triggered
[   30.804724] Maestro3 0000:00:06.0: PCI INT A -> Link[LNKC] -> GSI 10 (level, low) -> IRQ 10
[   30.804743] firmware: requesting ess/maestro3_assp_kernel.fw
[   35.596154] cs: IO port probe 0x100-0x3af: excluding 0x200-0x207
[   35.598129] cs: IO port probe 0x3e0-0x4ff: clean.
[   35.599006] cs: IO port probe 0x820-0x8ff: clean.
[   35.599770] cs: IO port probe 0xc00-0xcf7: clean.
[   35.600954] cs: IO port probe 0xa00-0xaff: clean.
[   35.603529] cs: IO port probe 0x100-0x3af: excluding 0x200-0x207
[   35.605574] cs: IO port probe 0x3e0-0x4ff: clean.
[   35.606455] cs: IO port probe 0x820-0x8ff: clean.
[   35.607219] cs: IO port probe 0xc00-0xcf7: clean.
[   35.608402] cs: IO port probe 0xa00-0xaff: clean.
[   36.241787] firmware: requesting ess/maestro3_assp_minisrc.fw
[   37.288130] usb 1-2: device descriptor read/64, error -110
[   37.504062] usb 1-2: new full speed USB device using uhci_hcd and address 3
[   38.423497] lp0: using parport0 (interrupt-driven).
[   38.804373] Adding 465844k swap on /dev/sda5.  Priority:-1 extents:1 across:465844k
[   39.733918] EXT3 FS on sda1, internal journal
[   41.567701] type=1505 audit(1234188589.490:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=3804
[   42.209318] type=1505 audit(1234188590.134:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=3809
[   42.210430] type=1505 audit(1234188590.134:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3809
[   42.561562] ip_tables: (C) 2000-2006 Netfilter Core Team

---

### Post by RedeyeAce on 2009-02-09
Ok so I decided to reinstall ubuntu with the usb card in place (as i didnt have it the first time)

2 reasons for doing this, 1.  In the hope that ubuntu would see it and automatically install it properly, 2.  To make it easier for someone to help me with installing this as we could just do it step by step.

Kerry, after the clean install i did your steps again all results in this post.

so system is restored, left clicking on network icon shows wired network greyed out, eth0 selected, wireless network greyed out,vpn connections, connect to hidden wireless, create wireless network. 

Synaptic packet manager not showing zd1211-source as installed

lsusb showing Bus 001 Device 014: ID 1582:6003 Fiberline WL-430U
 
sudo lshw -C network

description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:0e:8e:16:62:72
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg


iwconfig

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


ifconfig

only shows loopback and inbuilt lan


sudo ifup wlan0

Ignoring unknown interface wlan0=wlan0.


sudo apt-get install zd1211-firmware

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package zd1211-firmware is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package zd1211-firmware has no installation candidate


gedit /var/log/dmesg

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-11-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Jan 29 19:24:39 UTC 2009 (Ubuntu 2.6.27-11.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
[    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e9400 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000000fff0000 (usable)
[    0.000000]  BIOS-e820: 000000000fff0000 - 000000000ffffc00 (ACPI data)
[    0.000000]  BIOS-e820: 000000000ffffc00 - 0000000010000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fffe9400 - 0000000100000000 (reserved)
[    0.000000] DMI 2.1 present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0xfff0 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to fff0000 @ 10000-16000
[    0.000000] RAMDISK: 0f80b000 - 0ffdf505
[    0.000000] ACPI: RSDP 000F7050, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 0FFFC6ED, 002C (r1 PTLTD    RSDT    6040001  LTP        0)
[    0.000000] ACPI: FACP 0FFFFB65, 0074 (r1 ASUS   L8400B    6040001 PTL     F4240)
[    0.000000] ACPI: DSDT 0FFFC719, 344C (r1  Intel   Trajan  6040001 MSFT  1000004)
[    0.000000] ACPI: FACS 0FFFFFC0, 0040
[    0.000000] ACPI: BOOT 0FFFFBD9, 0027 (r1 PTLTD  $SBFTBL$  6040001  LTP        1)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 255MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 0fff0000
[    0.000000]   low ram: 00000000 - 0fff0000
[    0.000000]   bootmap 00012000 - 00014000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 000fff0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c29e0]    TEXT DATA BSS ==> [0000100000 - 00005c29e0]
[    0.000000]   #4 [000f80b000 - 000ffdf505]          RAMDISK ==> [000f80b000 - 000ffdf505]
[    0.000000]   #5 [00005c3000 - 00005c6000]    INIT_PG_TABLE ==> [00005c3000 - 00005c6000]
[    0.000000]   #6 [000009f400 - 0000100000]    BIOS reserved ==> [000009f400 - 0000100000]
[    0.000000]   #7 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #8 [0000012000 - 0000014000]          BOOTMAP ==> [0000012000 - 0000014000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0000fff0
[    0.000000]   HighMem  0x0000fff0 -> 0x0000fff0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0000fff0
[    0.000000] On node 0 totalpages: 65407
[    0.000000] free_area_init_node: node 0, pgdat c048c680, node_mem_map c1000240
[    0.000000]   DMA zone: 3947 pages, LIFO batch:0
[    0.000000]   Normal zone: 60884 pages, LIFO batch:15
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffb000 (01241000)
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000ea000
[    0.000000] PM: Registered nosave memory: 00000000000ea000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 10000000:effe9400)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 64831
[    0.000000] Kernel command line: root=UUID=0b683cb2-4d9a-4d39-850e-003c5fe227ac ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 1024 (order: 10, 4096 bytes)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PMTIMER calibration value
[    0.000000] Detected 851.919 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.004000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[    0.004000] Memory: 246024k/262080k available (2576k kernel code, 15496k reserved, 1165k data, 424k init, 0k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xd0800000 - 0xff3fe000   ( 747 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xcfff0000   ( 255 MB)
[    0.004000]       .init : 0xc04ad000 - 0xc0517000   ( 424 kB)
[    0.004000]       .data : 0xc03840da - 0xc04a7680   (1165 kB)
[    0.004000]       .text : 0xc0100000 - 0xc03840da   (2576 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.004022] Calibrating delay loop (skipped), value calculated using timer frequency.. 1703.83 BogoMIPS (lpj=3407676)
[    0.004074] Security Framework initialized
[    0.004098] SELinux:  Disabled at boot.
[    0.004161] AppArmor: AppArmor initialized
[    0.004185] Mount-cache hash table entries: 512
[    0.004620] Initializing cgroup subsys ns
[    0.004632] Initializing cgroup subsys cpuacct
[    0.004640] Initializing cgroup subsys memory
[    0.004680] CPU: L1 I cache: 16K, L1 D cache: 16K
[    0.004689] CPU: L2 cache: 256K
[    0.004735] Checking 'hlt' instruction... OK.
[    0.020847] SMP alternatives: switching to UP code
[    0.032056] Freeing SMP alternatives: 11k freed
[    0.032068] ACPI: Core revision 20080609
[    0.034482] ACPI: Checking initramfs for custom DSDT
[    0.860182] weird, boot CPU (#0) not listedby the BIOS.
[    0.864038] SMP motherboard not detected.
[    0.864047] Local APIC not detected. Using dummy APIC emulation.
[    0.864053] SMP disabled
[    0.864260] Brought up 1 CPUs
[    0.864268] Total of 1 processors activated (1703.83 BogoMIPS).
[    0.864300] CPU0 attaching NULL sched-domain.
[    0.865029] net_namespace: 840 bytes
[    0.865061] Booting paravirtualized kernel on bare hardware
[    0.865684] Time: 22:36:03  Date: 02/09/09
[    0.865775] NET: Registered protocol family 16
[    0.866828] EISA bus registered
[    0.866886] ACPI: bus type pci registered
[    0.867774] PCI: PCI BIOS revision 2.10 entry at 0xfd9a6, last bus=1
[    0.867784] PCI: Using configuration type 1 for base access
[    0.872416] ACPI: EC: Look up EC in DSDT
[    0.879334] ACPI: Interpreter enabled
[    0.879352] ACPI: (supports S0 S1 S3 S4 S5)
[    0.879406] ACPI: Using PIC for interrupt routing
[    0.884061] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.936557] ACPI: EC: GPE = 0x9, I/O: command/status = 0x66, data = 0x62
[    0.936568] ACPI: EC: driver started in interrupt mode
[    0.936756] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.936959] PCI: 0000:00:00.0 reg 10 32bit mmio: [f8000000, fbffffff]
[    0.937070] PCI: 0000:00:06.0 reg 10 io port: [f800, f8ff]
[    0.937123] pci 0000:00:06.0: supports D1
[    0.937129] pci 0000:00:06.0: supports D2
[    0.937136] pci 0000:00:06.0: PME# supported from D1 D2 D3hot
[    0.937145] pci 0000:00:06.0: PME# disabled
[    0.937181] PCI: 0000:00:06.1 reg 10 io port: [f400, f4ff]
[    0.937232] pci 0000:00:06.1: supports D1
[    0.937237] pci 0000:00:06.1: supports D2
[    0.937243] pci 0000:00:06.1: PME# supported from D1 D2 D3hot D3cold
[    0.937252] pci 0000:00:06.1: PME# disabled
[    0.937359] PCI: 0000:00:07.1 reg 20 io port: [fcf0, fcff]
[    0.937424] PCI: 0000:00:07.2 reg 20 io port: [fcc0, fcdf]
[    0.937511] pci 0000:00:07.3: quirk: region 8000-803f claimed by PIIX4 ACPI
[    0.937521] pci 0000:00:07.3: quirk: region 2180-218f claimed by PIIX4 SMB
[    0.937571] PCI: 0000:00:08.0 reg 10 io port: [f000, f0ff]
[    0.937583] PCI: 0000:00:08.0 reg 14 32bit mmio: [fedffc00, fedffcff]
[    0.937626] pci 0000:00:08.0: supports D1
[    0.937631] pci 0000:00:08.0: supports D2
[    0.937637] pci 0000:00:08.0: PME# supported from D1 D2 D3hot D3cold
[    0.937646] pci 0000:00:08.0: PME# disabled
[    0.937685] PCI: 0000:00:0a.0 reg 10 32bit mmio: [0, fff]
[    0.937704] pci 0000:00:0a.0: supports D1
[    0.937710] pci 0000:00:0a.0: supports D2
[    0.937716] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.937725] pci 0000:00:0a.0: PME# disabled
[    0.937759] PCI: 0000:00:0a.1 reg 10 32bit mmio: [0, fff]
[    0.937778] pci 0000:00:0a.1: supports D1
[    0.937783] pci 0000:00:0a.1: supports D2
[    0.937789] pci 0000:00:0a.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.937798] pci 0000:00:0a.1: PME# disabled
[    0.937880] PCI: 0000:01:00.0 reg 10 32bit mmio: [f0000000, f7ffffff]
[    0.937913] PCI: 0000:01:00.0 reg 30 32bit mmio: [0, ffff]
[    0.937933] pci 0000:01:00.0: supports D1
[    0.937938] pci 0000:01:00.0: supports D2
[    0.937983] PCI: bridge 0000:00:01.0 32bit mmio: [f0000000, f7ffffff]
[    0.938032] bus 00 -> node 0
[    0.938061] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.943709] ACPI: PCI Interrupt Link [LNKA] (IRQs *9)
[    0.944084] ACPI: PCI Interrupt Link [LNKB] (IRQs 9) *0, disabled.
[    0.944427] ACPI: PCI Interrupt Link [LNKC] (IRQs 5 6 7 10) *0, disabled.
[    0.944757] ACPI: PCI Interrupt Link [LNKD] (IRQs 9) *0, disabled.
[    0.945213] ACPI: Power Resource [PFAN] (off)
[    0.945407] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.945532] pnp: PnP ACPI init
[    0.945564] ACPI: bus type pnp registered
[    1.020514] pnp: PnP ACPI: found 13 devices
[    1.020525] ACPI: ACPI bus type pnp unregistered
[    1.020538] PnPBIOS: Disabled by ACPI PNP
[    1.024377] PCI: Using ACPI for IRQ routing
[    1.024669] NET: Registered protocol family 8
[    1.024669] NET: Registered protocol family 20
[    1.024669] NetLabel: Initializing
[    1.024669] NetLabel:  domain hash size = 128
[    1.024669] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.024669] NetLabel:  unlabeled traffic allowed by default
[    1.025109] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    1.025116]    actual entries 65620
[    1.025613] AppArmor: AppArmor Filesystem Enabled
[    1.025728] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    1.025728] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
[    1.025728] system 00:00: iomem range 0x100000-0xfffffff could not be reserved
[    1.025728] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    1.025728] system 00:02: ioport range 0x398-0x399 has been reserved
[    1.025728] system 00:02: ioport range 0x2180-0x218f has been reserved
[    1.025728] system 00:02: ioport range 0x8000-0x803f has been reserved
[    1.025728] system 00:02: ioport range 0x3800-0x383f has been reserved
[    1.025728] system 00:02: iomem range 0xfff80000-0xffffffff could not be reserved
[    1.063333] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    1.063344] pci 0000:00:01.0:   IO window: disabled
[    1.063355] pci 0000:00:01.0:   MEM window: 0xf0000000-0xf7ffffff
[    1.063365] pci 0000:00:01.0:   PREFETCH window: 0x00000030000000-0x000000300fffff
[    1.063379] pci 0000:00:0a.0: CardBus bridge, secondary bus 0000:02
[    1.063386] pci 0000:00:0a.0:   IO window: 0x001000-0x0010ff
[    1.063395] pci 0000:00:0a.0:   IO window: 0x001400-0x0014ff
[    1.063404] pci 0000:00:0a.0:   PREFETCH window: 0x20000000-0x23ffffff
[    1.063413] pci 0000:00:0a.0:   MEM window: 0x24000000-0x27ffffff
[    1.063423] pci 0000:00:0a.1: CardBus bridge, secondary bus 0000:06
[    1.063430] pci 0000:00:0a.1:   IO window: 0x001800-0x0018ff
[    1.063439] pci 0000:00:0a.1:   IO window: 0x001c00-0x001cff
[    1.063448] pci 0000:00:0a.1:   PREFETCH window: 0x28000000-0x2bffffff
[    1.063457] pci 0000:00:0a.1:   MEM window: 0x2c000000-0x2fffffff
[    1.064699] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 9
[    1.064709] PCI: setting IRQ 9 as level-triggered
[    1.064719] pci 0000:00:0a.0: PCI INT A -> Link[LNKA] -> GSI 9 (level, low) -> IRQ 9
[    1.064731] pci 0000:00:0a.0: setting latency timer to 64
[    1.065738] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 9
[    1.065748] pci 0000:00:0a.1: PCI INT B -> Link[LNKB] -> GSI 9 (level, low) -> IRQ 9
[    1.065759] pci 0000:00:0a.1: setting latency timer to 64
[    1.065769] bus: 00 index 0 io port: [0, ffff]
[    1.065775] bus: 00 index 1 mmio: [0, ffffffff]
[    1.065781] bus: 01 index 0 mmio: [0, 0]
[    1.065787] bus: 01 index 1 mmio: [f0000000, f7ffffff]
[    1.065794] bus: 01 index 2 mmio: [30000000, 300fffff]
[    1.065800] bus: 01 index 3 mmio: [0, 0]
[    1.065807] bus: 02 index 0 io port: [1000, 10ff]
[    1.065813] bus: 02 index 1 io port: [1400, 14ff]
[    1.065820] bus: 02 index 2 mmio: [20000000, 23ffffff]
[    1.065826] bus: 02 index 3 mmio: [24000000, 27ffffff]
[    1.065833] bus: 06 index 0 io port: [1800, 18ff]
[    1.065839] bus: 06 index 1 io port: [1c00, 1cff]
[    1.065845] bus: 06 index 2 mmio: [28000000, 2bffffff]
[    1.065852] bus: 06 index 3 mmio: [2c000000, 2fffffff]
[    1.065887] NET: Registered protocol family 2
[    1.066313] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[    1.067039] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[    1.067227] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    1.067418] TCP: Hash tables configured (established 8192 bind 8192)
[    1.067426] TCP reno registered
[    1.067745] NET: Registered protocol family 1
[    1.068172] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[    1.888041]  it is
[    2.928793] Freeing initrd memory: 8017k freed
[    2.929430] Simple Boot Flag at 0x37 set to 0x1
[    2.930761] audit: initializing netlink socket (disabled)
[    2.930812] type=2000 audit(1234218964.928:1): initialized
[    2.946609] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    2.955199] VFS: Disk quotas dquot_6.5.1
[    2.955564] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    2.955929] msgmni has been set to 496
[    2.956480] io scheduler noop registered
[    2.956489] io scheduler anticipatory registered
[    2.956496] io scheduler deadline registered
[    2.956556] io scheduler cfq registered (default)
[    2.956590] pci 0000:00:00.0: Limiting direct PCI/PCI transfers
[    2.956640] pci 0000:01:00.0: Boot video device
[    2.957696] isapnp: Scanning for PnP cards...
[    3.311549] isapnp: No Plug & Play device found
[    3.482285] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    3.482549] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    3.483094] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a NS16550A
[    3.485595] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    3.491649] brd: module loaded
[    3.491925] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    3.492446] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUE] at 0x60,0x64 irq 1,12
[    3.497009] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.497026] serio: i8042 AUX port at 0x60,0x64 irq 12
[    3.498519] mice: PS/2 mouse device common for all mice
[    3.499022] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    3.499058] rtc0: alarms up to one month, y3k
[    3.499453] EISA: Probing bus 0 at eisa.0
[    3.499472] Cannot allocate resource for EISA slot 1
[    3.499487] Cannot allocate resource for EISA slot 3
[    3.499513] Cannot allocate resource for EISA slot 8
[    3.499519] EISA: Detected 0 cards.
[    3.499528] cpuidle: using governor ladder
[    3.499535] cpuidle: using governor menu
[    3.501349] TCP cubic registered
[    3.501438] Using IPI No-Shortcut mode
[    3.502385] registered taskstats version 1
[    3.502669]   Magic number: 13:565:653
[    3.503048] rtc_cmos 00:04: setting system clock to 2009-02-09 22:36:06 UTC (1234218966)
[    3.503058] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.503064] EDD information not available.
[    3.504775] Freeing unused kernel memory: 424k freed
[    3.504948] Write protecting the kernel text: 2580k
[    3.505051] Write protecting the kernel read-only data: 940k
[    3.534775] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    4.128162] fuse init (API version 7.9)
[    4.271083] ACPI: Transitioning device [FAN] to D3
[    4.271268] fan PNP0C0B:00: registered as cooling_device0
[    4.271287] ACPI: Fan [FAN] (off)
[    4.300503] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    4.300661] processor ACPI0007:00: registered as cooling_device1
[    4.300673] ACPI: Processor [CPU0] (supports 4 throttling states)
[    4.321906] thermal LNXTHERM:01: registered as thermal_zone0
[    4.328353] ACPI: Thermal Zone [THRM] (70 C)
[    6.176503] No dock devices found.
[    6.426246] SCSI subsystem initialized
[    6.441128] 8139too Fast Ethernet driver 0.9.28
[    6.441222] 8139too 0000:00:08.0: enabling device (0000 -> 0003)
[    6.442387] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 9
[    6.442399] 8139too 0000:00:08.0: PCI INT A -> Link[LNKD] -> GSI 9 (level, low) -> IRQ 9
[    6.443533] eth0: RealTek RTL8139 at 0xf000, 00:e0:18:1b:7b:3c, IRQ 9
[    6.443541] eth0:  Identified 8139 chip type 'RTL-8139C'
[    6.465169] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    6.623654] usbcore: registered new interface driver usbfs
[    6.623725] usbcore: registered new interface driver hub
[    6.626976] usbcore: registered new device driver usb
[    6.642760] USB Universal Host Controller Interface driver v3.0
[    6.642918] uhci_hcd 0000:00:07.2: enabling device (0000 -> 0001)
[    6.642939] uhci_hcd 0000:00:07.2: PCI INT D -> Link[LNKD] -> GSI 9 (level, low) -> IRQ 9
[    6.642964] uhci_hcd 0000:00:07.2: UHCI Host Controller
[    6.643098] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[    6.643143] uhci_hcd 0000:00:07.2: irq 9, io base 0x0000fcc0
[    6.643681] usb usb1: configuration #1 chosen from 1 choice
[    6.643775] hub 1-0:1.0: USB hub found
[    6.643804] hub 1-0:1.0: 2 ports detected
[    6.646192] libata version 3.00 loaded.
[    6.883280] ata_piix 0000:00:07.1: version 2.12
[    6.884491] scsi0 : ata_piix
[    6.884980] scsi1 : ata_piix
[    6.885087] ata1: PATA max UDMA/33 cmd 0x1f0 ctl 0x3f6 bmdma 0xfcf0 irq 14
[    6.885096] ata2: PATA max UDMA/33 cmd 0x170 ctl 0x376 bmdma 0xfcf8 irq 15
[    6.972196] usb 1-2: new full speed USB device using uhci_hcd and address 2
[    7.336902] ata1.00: ATA-5: IBM-DJSA-210, JS2OAB8A, max UDMA/66
[    7.336915] ata1.00: 19640880 sectors, multi 16: LBA 
[    7.336985] ata1.01: ATAPI: TOSHIBA DVD-ROM SD-C2502, 1711, max UDMA/33
[    7.352761] ata1.00: configured for UDMA/33
[    7.368524] ata1.01: configured for UDMA/33
[    7.368629] ata2: port disabled. ignoring.
[    7.368972] scsi 0:0:0:0: Direct-Access     ATA      IBM-DJSA-210     JS2O PQ: 0 ANSI: 5
[    7.371038] scsi 0:0:1:0: CD-ROM            TOSHIBA  DVD-ROM SD-C2502 1711 PQ: 0 ANSI: 5
[    8.495496] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    8.495626] scsi 0:0:1:0: Attached scsi generic sg1 type 5
[    8.574531] Driver 'sd' needs updating - please use bus_type methods
[    8.574865] sd 0:0:0:0: [sda] 19640880 512-byte hardware sectors (10056 MB)
[    8.574917] sd 0:0:0:0: [sda] Write Protect is off
[    8.574928] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    8.575011] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    8.575218] sd 0:0:0:0: [sda] 19640880 512-byte hardware sectors (10056 MB)
[    8.575265] sd 0:0:0:0: [sda] Write Protect is off
[    8.575273] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    8.575353] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    8.575368]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[    8.629338] Marking TSC unstable due to TSC halts in idle
[    8.935806]  sda1 sda2 < sda5 >
[    8.973630] sd 0:0:0:0: [sda] Attached SCSI disk
[    9.013047] sr0: scsi3-mmc drive: 24x/24x cd/rw xa/form2 cdda tray
[    9.013060] Uniform CD-ROM driver Revision: 3.20
[    9.013393] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    9.573300] PM: Starting manual resume from disk
[    9.573316] PM: Resume from partition 8:5
[    9.573321] PM: Checking hibernation image.
[    9.573855] PM: Resume from disk failed.
[    9.684881] kjournald starting.  Commit interval 5 seconds
[    9.684932] EXT3-fs: mounted filesystem with ordered data mode.
[   11.972087] uhci_hcd 0000:00:07.2: Unlink after no-IRQ?  Controller is probably using the wrong IRQ.
[   21.528795] udevd version 124 started
[   22.084083] usb 1-2: device descriptor read/64, error -110
[   24.384478] Linux agpgart interface v0.103
[   24.484478] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   24.602355] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   24.911499] request region #1
[   24.911525] isp1760: probe of 0000:00:07.3 failed with error -16
[   25.128100] agpgart-intel 0000:00:00.0: Intel 440BX Chipset
[   25.144613] agpgart-intel 0000:00:00.0: AGP aperture is 64M @ 0xf8000000
[   25.260552] Yenta: CardBus bridge found at 0000:00:0a.0 [1043:1044]
[   25.281040] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   25.388922] Yenta: ISA IRQ mask 0x0cb8, PCI irq 9
[   25.388933] Socket status: 30000006
[   25.448506] Yenta: CardBus bridge found at 0000:00:0a.1 [1043:1044]
[   25.576901] Yenta: ISA IRQ mask 0x0cb8, PCI irq 9
[   25.576912] Socket status: 30000006
[   26.082949] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[   26.095013] ACPI: Power Button (FF) [PWRF]
[   26.095392] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input4
[   26.108071] ACPI: Sleep Button (CM) [SLPB]
[   26.108412] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input5
[   26.108617] ACPI: Lid Switch [LID]
[   26.299334] ACPI: AC Adapter [AC] (on-line)
[   26.389906] ACPI: I/O resource piix4_smbus [0x2180-0x2187] conflicts with ACPI region SM06 [0x2186-0x2186]
[   26.389918] ACPI: Device needs an ACPI driver
[   26.389935] piix4_smbus 0000:00:07.3: SMBus Host Controller at 0x2180, revision 0
[   27.035129] ACPI: Battery Slot [BAT0] (battery present)
[   29.113737] Synaptics Touchpad, model: 1, fw: 4.6, id: 0x135ea1, caps: 0x804713/0x0
[   29.117412] irda_init()
[   29.117458] NET: Registered protocol family 23
[   29.164341] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6
[   29.351292] parport_pc 00:09: reported by Plug and Play ACPI
[   29.351355] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   29.448549] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 3.
[   29.448603] nsc-ircc, chip->init
[   29.448610] nsc-ircc, Found chip at base=0x398
[   29.448643] nsc-ircc, driver loaded (Dag Brattli)
[   29.448662] nsc_ircc_open(), can't get iobase of 0x2f8
[   29.448690] nsc-ircc, Found chip at base=0x398
[   29.448723] nsc-ircc, driver loaded (Dag Brattli)
[   29.448731] nsc_ircc_open(), can't get iobase of 0x2f8
[   29.455982] nsc-ircc 00:0b: disabled
[   30.189787] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
[   30.189801] PCI: setting IRQ 10 as level-triggered
[   30.189811] Maestro3 0000:00:06.0: PCI INT A -> Link[LNKC] -> GSI 10 (level, low) -> IRQ 10
[   30.189829] firmware: requesting ess/maestro3_assp_kernel.fw
[   34.996253] cs: IO port probe 0x100-0x3af: excluding 0x200-0x207
[   34.998234] cs: IO port probe 0x3e0-0x4ff: clean.
[   34.999119] cs: IO port probe 0x820-0x8ff: clean.
[   34.999882] cs: IO port probe 0xc00-0xcf7: clean.
[   35.001107] cs: IO port probe 0xa00-0xaff: clean.
[   35.007276] cs: IO port probe 0x100-0x3af: excluding 0x200-0x207
[   35.009336] cs: IO port probe 0x3e0-0x4ff: clean.
[   35.010220] cs: IO port probe 0x820-0x8ff: clean.
[   35.010988] cs: IO port probe 0xc00-0xcf7: clean.
[   35.012175] cs: IO port probe 0xa00-0xaff: clean.
[   35.815427] firmware: requesting ess/maestro3_assp_minisrc.fw
[   37.306973] usb 1-2: device descriptor read/64, error -110
[   37.486413] lp0: using parport0 (interrupt-driven).
[   37.523803] usb 1-2: new full speed USB device using uhci_hcd and address 3
[   37.891788] Adding 465844k swap on /dev/sda5.  Priority:-1 extents:1 across:465844k
[   38.770075] EXT3 FS on sda1, internal journal
[   40.530902] type=1505 audit(1234219003.365:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=3803
[   41.173169] type=1505 audit(1234219004.009:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=3808
[   41.174263] type=1505 audit(1234219004.009:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3808
[   41.512400] ip_tables: (C) 2000-2006 Netfilter Core Team

---

### Post by kerry_s on 2009-02-09
okay first thing:

> sudo apt-get install zd1211-firmware

Reading package lists... Done
Building dependency tree
Reading state information... Done
Package zd1211-firmware is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package zd1211-firmware has no installation candidate


this tells me you don't have all your repos on:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

i don't see the usb wireless in the dmesg, did you have it plugged in when you booted?

---

### Post by RedeyeAce on 2009-02-09
Heya kerry, thanks for stopping by again :)

The usb is plugged in on bootup however i have noticed that after bootup and running lsusb it takes forever to run and the fiberline doesnt show, so i unplug and replug the card, then run lsusb results are almost immediate and it is showing.

So i am under the belief that for some reason the usb hub isnt detecting the card untill everythings fully loaded, then it needs the card reinserted for it to be detected. Could be due to an old bios on this lappy im thinking, its an old p3 850. alternatively could be something todo with network being initialised before bootup perhaps?

Im having a look at the psychocats.net thing now..

---

### Post by RedeyeAce on 2009-02-09
ok so Software Sources> Ubuntu Software tab 
only one not checked is source code and installable from cdrom is unchecked

Software Sources> Third Party Software 2 unchecked items archive.conical.com/ubuntu intrepid partner
archive.conical.com/ubuntu intrepid partner (source code)


Software Sources>Updates, proposed and unsupported unchecked

looks ok to me, bt what do i know eh :)

ok bit of a prem post, its now seen updates, so i'll post more in a bit

hmmm, its downlaoded 46 things, the window for software sources is greyed out, if i click close, it wants me to reload, i do that and its really quick at loading all 46 files (i presume its seeing a cache of them downloaded) but its not doing anything, im thinking of restarting the box and trying again, i'll give it a few more mins.

ok so rebooted tried again, same problem so i closed it.  Re ran Software Sources , changed the server so it effected the update and this time it closed by itself, so for some reason and im guessing it installs a couple of updates first time round, thne you have to close it and run it again for it to then continue and finish.

ok so ive backed up the source list, updated it then ran the get update and all went well untill

Get: 33 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Packages [6843B] 
Fetched 6827kB in 35s (191kB/s)                                                
Reading package lists... Done
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems

so im gonna rerun the get update as suggested.

nope same error, so im gonna presume this is fine

---

### Post by RedeyeAce on 2009-02-09
sudo apt-get install zd1211-firmware
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package zd1211-firmware is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package zd1211-firmware has no installation candidate


so its the same thing as before. is there anyway we can check the repo's against yours? or as i found the zd1211=firmware on opensource, is there anyway to install it properly through that?

When i went to it the other day you download a compressed file from [http://sourceforge.net/project/showf...ease_id=544191](http://sourceforge.net/project/showf...ease_id=544191) and it wants you to overwrite the files in /lib/firmware/zd1211 which i can do using nautilus.  

I would prefer to do it via your method as it seems more of a proper (foolproof) way to do it.  

or is there anyway you can check to see if the update is available i.e. is it worth you running sudo apt-get install zd1211-firmware, jut to check the file update is accessible and not been moved or something?

One thing i did notice on bootup is the screen before the gui loads, there is a bluetooth module scanning the usb's and it seems to be trying to interface with what im going to assume to be the usb wifi card, if you think this could be relevant and you can point me to a location where that final (applet like) loading screen is i'll post it up, just wanted to point it out in case it was relevant.

Thanks for your help again!! :)

---

### Post by RedeyeAce on 2009-02-10
I have just enabled  proposed updates and unsupported updates and run john@john-laptop:~$ sudo apt-get install zdz1211-firmware
[sudo] password for john: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package zdz1211-firmware

So i think if you can check to see whether it is available to you, cos im coming to the belief that the package has been moved and the update hasnt moved to the new location.

---

### Post by kerry_s on 2009-02-10
grab this deb and just double click on it to install.
[http://http.us.debian.org/debian/pool/non-free/z/zd1211-firmware/zd1211-firmware_2.21.0.0-0.1_all.deb](http://http.us.debian.org/debian/pool/non-free/z/zd1211-firmware/zd1211-firmware_2.21.0.0-0.1_all.deb)

sorry, you can't match your repos against mine, i don't use debian or ubuntu anymore. i use arch, it's totally different. :lolflag:

> Software Sources>Updates, proposed and unsupported unchecked

should be checked, it's suppose to be in unsupported.

---

### Post by RedeyeAce on 2009-02-10
Hey Kerry :)

the package failed to install :( according to terminal, im having to writ e out the error as it wont copy and paste.

Selecting previously deselected package zd1211-firmware.
(Reading database ... 115622 files and directories currently installed.)
Unpacking zd1211-firmware (from .../zd1211-firmware_2.21.0.0-0.1_all.deb)...
dpkg: error processing /tmp/zd1211-firmware_2.21.0.0-0.1_all.deb (--install):
 trying to overwrite /lib/firmware/zd1211/zd1211b_uphr', which is also in package linux-package.

now im just going to try and see if i can run this in nautilus, as the other day i couldnt write in that directory as i needed root access and im wondering whether this has failed due to that.

---

### Post by RedeyeAce on 2009-02-10
damn that didnt work.

I copied the package file into the nautilus windows (in a new directory called downloads)

ran it from the nautilus window and exactly the same error happens as per my last post, could it be that it cant install into that directory cos of root access and for some reason nautilus isnt granting the correct permissions for extracting those files?

---

### Post by kerry_s on 2009-02-10
what that's saying is you already have the firmware, so try this:

(switch to root)
**sudo su**
(load the firmware)
**modprobe zd1211**
(make sure its up)
**ifconfig wlan0 up**
(check)
**iwconfig**
(give it a essid, replace name with your name)
**iwconfig wlan0 essid "name"**
(check it has the name)
**iwconfig**
(if it has a name, get dhcp lease)
**dhclient wlan0**
(check)
**iwconfig**

if that don't work, think about trying lenny:
net installer: [http://cdimage.debian.org/cdimage/lenny_di_rc2/i386/iso-cd/debian-Lenny-DI-rc2-i386-businesscard.iso](http://cdimage.debian.org/cdimage/lenny_di_rc2/i386/iso-cd/debian-Lenny-DI-rc2-i386-businesscard.iso)

in lenny, all you have to do is is add "**contrib non-free**" to the end of the repo lines, then:
[B]su
apt-get update
apt-get install zd1211-firmware
[/B]
thats it should work right away.

---

### Post by RedeyeAce on 2009-02-10
Heya,

ok i just tried the first part and got this far

root@john-laptop:/home/john# modprobe zd1211
FATAL: Module zd1211 not found.
root@john-laptop:/home/john#   

so im off to go and try lenny then by the looks of it.

---

### Post by kerry_s on 2009-02-10
> **RedeyeAce said:**
> Heya,

ok i just tried the first part and got this far

root@john-laptop:/home/john# modprobe zd1211
FATAL: Module zd1211 not found.
root@john-laptop:/home/john#   

so im off to go and try lenny then by the looks of it.

yeah, try lenny, i never had any problem, i ain't using lenny anymore cause they dropped my sound card firmware, which was a pain to get it working after that.

---

### Post by RedeyeAce on 2009-02-10
What is lenny by the way? am i correct in thinking its another version of ubuntu?

---

### Post by kerry_s on 2009-02-10
> **RedeyeAce said:**
> What is lenny by the way? am i correct in thinking its another version of ubuntu?

lenny is pure debian, ubuntu is built from debian unstable.
or
debian is the father, ubuntu is the son. :)

---

### Post by RedeyeAce on 2009-02-10
Ah okedokey, i'll probably post tomorrow with how im getting on as i'll have to download it on another box.

Do i have to install a gui interface then? if so what would you reccomend?

and is there anything else i have to do setting it up for auto updates, like i had to do with the psychocats site?

Sorry to ask this i just ant to be in a position tomorrow where i have done all the basics so to speak.

Thanks loads again for all your help to date with this :)

---

### Post by kerry_s on 2009-02-10
> Do i have to install a gui interface then? if so what would you reccomend?

a straight install with the net installer gives you gnome, so it would look just like the ubuntu install, just not fancy.

> and is there anything else i have to do setting it up for auto updates

not sure what you mean, it has the update applet just like ubuntu.

the sources.list, you want add "contrib non-free" to the end, like this:

```

deb http://security.debian.org/ lenny/updates main contrib non-free
deb-src http://security.debian.org/ lenny/updates main contrib non-free

deb http://http.us.debian.org/debian/ lenny main contrib non-free
deb-src http://http.us.debian.org/debian/ lenny main contrib non-free

deb http://www.debian-multimedia.org lenny main

```

---

### Post by gmp34 on 2009-02-17
Personaly I installed a "SMC Wireless EZ Connect g USB2 adapator", spent 2 hours reading forums on ZD1211 installation, seeing that the driver was part of Ubuntu release I decided to "hot plug" my USB adapator on both Ubuntu 8.10 AMD64 and Xubuntu 8.10 (K6 processor)machines.

Both are working like a charm :p as soon as plugged I could see my network name as wireless network, entering my WEP Key and that was it.

The plus of the forum was to tell me that the driver was already part of the standard distribution.:D

Thanks to all.

---

### Post by RedeyeAce on 2009-02-18
Real Life has owned me rather for the past week, so i havent gotten around to downloading lenny yet, 

I did run dmesg after inserting the usb card (read that somewhere lol) and got the following

1542.000081] usb 1-1: new full speed USB device using uhci_hcd and address 2
[ 1542.171266] usb 1-1: configuration #1 chosen from 1 choice
[ 1543.916095] usb 1-1: reset full speed USB device using uhci_hcd and address 2
[ 1544.088987] phy0: Selected rate control algorithm 'pid'
[ 1544.380977] zd1211rw 1-1:1.0: phy0
[ 1544.382031] usbcore: registered new interface driver zd1211rw
[ 1548.629133] firmware: requesting zd1211/zd1211b_ub
[ 1548.831128] firmware: requesting zd1211/zd1211b_uphr
[ 1550.071216] firmware: requesting zd1211/zd1211b_ub
[ 1550.079421] firmware: requesting zd1211/zd1211b_uphr
[ 1551.097617] usb 1-1: USB control request for firmware upload failed. Error number -110
[ 1551.097639] usb 1-1: Could not upload firmware code uph. Error number -110
[ 1551.097694] zd1211rw 1-1:1.0: couldn't load firmware. Error number -110
[ 2309.048123] usb 1-1: USB disconnect, address 2
[ 2314.300061] usb 1-1: new full speed USB device using uhci_hcd and address 3
[ 2314.476774] usb 1-1: configuration #1 chosen from 1 choice
[ 2314.596090] usb 1-1: reset full speed USB device using uhci_hcd and address 3
[ 2314.774716] phy1: Selected rate control algorithm 'pid'
[ 2314.779878] zd1211rw 1-1:1.0: phy1
[ 2319.137065] firmware: requesting zd1211/zd1211b_ub
[ 2319.243689] firmware: requesting zd1211/zd1211b_uphr
[ 2320.312573] firmware: requesting zd1211/zd1211b_ub
[ 2320.320838] firmware: requesting zd1211/zd1211b_uphr
[ 2321.341959] usb 1-1: USB control request for firmware upload failed. Error number -110
[ 2321.341981] usb 1-1: Could not upload firmware code uph. Error number -110
[ 2321.342023] zd1211rw 1-1:1.0: couldn't load firmware. Error number -110


So it is trying to install the zd1211 anyone know what this error code could mean or where i could look it up please.. 

before I try lenny.. 
Thanks folks

---

### Post by RedeyeAce on 2009-02-19
Solved!!!

the -110 error is a timeout issue, it turns out the permissions on the directory for the drivers was incorrect, this was solved by the following

sudo chown -R root.root /lib/firmware/zd1211
sudo find /lib/firmware -type d -exec chmod 755 {} \;
sudo find /lib/firmware/zd1211 -type f -exec chmod 644 {} \; 

My thanks go to Hin-Tak Leung for providing solution
And To Kerry who was extremely helpfull in aiding me toward this stage

THANK YOU!!!

First page being edited with solution and subject being changed to solved

---

