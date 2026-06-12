---
title: "Installing 3com 3c905b NIC in Ubuntu 8.10"
date: 2008-12-30
forum: Networking &amp; Wireless
---

### Post by kbarrow on 2008-12-30
I have an older system I am setting up with Ubuntu 8.10 which I installed the gnome desktop after the installation. The Primary Nic is a SIS900 on the motherboard that was configued during the installation.
The secondary NIN is a 3com 3c905b which was not detected during installation.

I have the redhat driver 3c90x-1.0.0i.tar.gz .

I am assuming it will work with Ubuntu but would like to know if there is a Ubuntu driver for the 3com 3c905b NIC. I have been unable to find one so far.

If the redhat driver will work how do I setup the alias and Kernal in Ubuntu?

---

### Post by Jose Catre-Vandis on 2008-12-30
Should be working by default. There may be bugs if you are on the latest kernel update, though.

That said, try the following:

```
sudo modprobe -v 3c59x
```

if this works you can add an entry to your /etc/modules file

and / or

Check your bios for "Plug and Play aware OS". Set this to NO. Works for some folks

and / or

Disable the other NIC in your bios and try reinstall?

---

### Post by kbarrow on 2008-12-31
Your suggestion did not seem to work. I am still unable to get the card recognized by Ubuntu. I am aware that the 3COM 3C905B has issues with running in Ubuntu at full duplex and am aware of how to correct that.

I am unable to replace the card at this time and require both the SIS900 and the 3C905B to work for my Lan.This PC will be used as a Gateway router and DHCP server to the internal network.

I have no problems using Windows to configure the network but I would prefer to change to a full Linux system.

I am a Ubuntu newbie, I have forgotten my Dos, Unix and Linux code many years ago. Although I am comfortable with computers and networking overall, this has me stumped. If any assistance can be provided, it would be appreciated.

---

### Post by jrusso2 on 2008-12-31
Those old 3com cards could be set with a dos floppy if you have a floppy drive I think the disk is still available on 3 coms web site.  I have many of those running and this pc has one on ubuntu.

Boot off the floppy and set the speed of the ethernet to 100 mbs full duplex.

---

### Post by kbarrow on 2008-12-31
> **jrusso2 said:**
> Those old 3com cards could be set with a dos floppy if you have a floppy drive I think the disk is still available on 3 coms web site.  I have many of those running and this pc has one on ubuntu.

Boot off the floppy and set the speed of the ethernet to 100 mbs full duplex.

Stetting the card to full duplex is not the issue.

Setting Ubuntu up to use the needed driver (3C59x) so that it is recognized on bootup is the issue.

How do I accomplish this? 

Thanks in advance

---

### Post by kbarrow on 2008-12-31
This is the results of lshw -C network

> lshw -C network
  *-network               
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 1.1
       bus info: pci@0000:00:01.1
       logical name: eth0
       version: 84
       serial: 00:07:95:aa:43:69
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=full ip=75.109.152.29 latency=64 link=yes maxlatency=11 mingnt=52 module=sis900 multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 4e:cf:d2:15:ab:62
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


---

### Post by Jose Catre-Vandis on 2009-01-01
Do you get the module 3c59x loaded?
```
sudo modprobe 3c59x
lsmod | grep 3c
sudo lshw
lspci -v
```

Research shows this was in the kernel in 8.04/7.04 and should work out of the box on those systems

Was there any plug and play setting in the bios?

Not sure if this will help (I think for older/other cards) but you could try installing and running this tool
```
sudo apt-get install nictools-nopci
```
> Diagnostic tools for many non-PCI ethernet cards
These are tools to diagnose problems with your non-PCI ethernet cards.
Some card can be set up or the EEPROM can be updated.

 3c515-diag    : Diagnostic program for 3Com 3c515 Ethernet cards
 3c5x9setup    : Setup program for 3Com EtherLink III Ethernet cards
 at1700-diag   : Diagnostic program for the Allied Telesis AT1700
 atlantic-setup: Setup program for AT/LANTIC DP83905 Ethernet cards
 atp-diag      : Diagnostic for Realtek RTL8002/RTL8012 pocket Ethernet
                 adapter
 eexpress      : Diagnostic program for Intel EtherExpress 16 cards
 el3diag       : Diagnostic program for 3c509 and 3c579 Ethernet cards
 e21-diag      : Diagnostic program for Cabletron E2100 Ethernet cards
 hp+-diag      : Diagnostic program for HP PC LAN+ (27247B & 27252A) cards
 hp100vg-diag  : Diagnostic program for Lucent ATT2MD01 Ethernet cards
 ne2k-diag     : Diagnostics and EEPROM setup for NE2000 clones
 wdsetup       : Configuration utility for Western Digital and SMC Ethernet
                 cards

This package replaces the old 3c5x9utils and wdsetup packages. 

---

### Post by albinootje on 2009-01-01
> **kbarrow said:**
> Your suggestion did not seem to work. I am still unable to get the card recognized by Ubuntu.

Can you post the output of :
```

sudo apt-get install ethtool
sudo ethtool eth0
sudo ethtool eth1
sudo modprobe -r 3c59x
sudo modprobe -v 3c59x
dmesg|tail -n 20
tail -f -n20 /var/log/kern.log

```

---

### Post by kbarrow on 2009-01-01
> **albinootje said:**
> Can you post the output of :
```

sudo apt-get install ethtool
sudo ethtool eth0
sudo ethtool eth1
sudo modprobe -r 3c59x
sudo modprobe -v 3c59x
dmesg|tail -n 20
tail -f -n20 /var/log/kern.log

```

The results of the requested output follows.

sudo ethtool eth0
```

Settings for eth0:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 1
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pg
	Wake-on: d
	Current message level: 0x000000c5 (197)
	Link detected: yes

```

sudo ethtool eth1
```

Settings for eth1:
Cannot get device settings: No such device
Cannot get wake-on-lan settings: No such device
Cannot get message level: No such device
Cannot get link status: No such device
No data available

```

```

 sudo modprobe -r 3c59x
 sudo modprobe -v 3c59x
insmod /lib/modules/2.6.27-9-server/kernel/drivers/net/3c59x.ko 

```

```

dmesg | tail -n 20
[   76.431203] Bluetooth: SCO socket layer initialized
[   83.171307] [drm] Initialized drm 1.1.0 20060810
[   83.251297] pci 0000:01:00.0: setting latency timer to 64
[   83.251297] [drm] Initialized sis 1.3.0 20070626 on minor 0
[   83.251297] agpgart-sis 0000:00:00.0: AGP 2.0 bridge
[   83.251297] agpgart-sis 0000:00:00.0: putting AGP V2 device into 4x mode
[   83.251297] pci 0000:01:00.0: putting AGP V2 device into 4x mode
[  148.386200] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=93.178.68.79 DST=75.109.152.29 LEN=60 TOS=0x00 PREC=0x00 TTL=49 ID=16242 DF PROTO=TCP SPT=2194 DPT=23 WINDOW=5808 RES=0x00 SYN URGP=0 
[  377.605752] ppdev0: registered pardevice
[  377.661330] ppdev0: unregistered pardevice
[  377.965692] ppdev0: registered pardevice
[  378.029644] ppdev0: unregistered pardevice
[  380.009401] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=10.231.64.1 DST=75.109.152.29 LEN=74 TOS=0x00 PREC=0x00 TTL=255 ID=42998 PROTO=UDP SPT=161 DPT=48806 LEN=54 
[  383.545777] ppdev0: registered pardevice
[  383.585789] ppdev0: unregistered pardevice
[ 1333.170219] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=60.222.224.135 DST=75.109.152.29 LEN=622 TOS=0x00 PREC=0x00 TTL=48 ID=0 DF PROTO=UDP SPT=46153 DPT=1026 LEN=602 
[ 1333.170219] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=60.222.224.135 DST=75.109.152.29 LEN=622 TOS=0x00 PREC=0x00 TTL=48 ID=0 DF PROTO=UDP SPT=46153 DPT=1027 LEN=602 
[ 1511.721832] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=60.15.177.162 DST=75.109.152.29 LEN=620 TOS=0x00 PREC=0x00 TTL=49 ID=0 DF PROTO=UDP SPT=37785 DPT=1026 LEN=600 
[ 1887.818532] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=24.187.202.165 DST=75.109.152.29 LEN=48 TOS=0x00 PREC=0x00 TTL=113 ID=28523 DF PROTO=TCP SPT=4253 DPT=5900 WINDOW=65535 RES=0x00 SYN URGP=0 
[ 1890.748543] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=24.187.202.165 DST=75.109.152.29 LEN=48 TOS=0x00 PREC=0x00 TTL=113 ID=30180 DF PROTO=TCP SPT=4253 DPT=5900 WINDOW=65535 RES=0x00 SYN URGP=0 

```

Thanks for your help

---

### Post by kbarrow on 2009-01-01
> **Jose Catre-Vandis said:**
> Do you get the module 3c59x loaded?
```
sudo modprobe 3c59x
lsmod | grep 3c
sudo lshw
lspci -v
```

Research shows this was in the kernel in 8.04/7.04 and should work out of the box on those systems

Was there any plug and play setting in the bios?

Not sure if this will help (I think for older/other cards) but you could try installing and running this tool
```
sudo apt-get install nictools-nopci
```

I'm not sure if the module is loaded properly.
The Bios was set for plug and play and I turned it off as suggested.
I then rebooted with the same results of the NIC card not being found.

I have posted the results of other trouble shooting commands also.

---

### Post by albinootje on 2009-01-02
> **kbarrow said:**
>  I have posted the results of other trouble shooting commands also.

Thanks.
After loading the module, can you show the output of :
```

lsmod|grep 3c

```

---

### Post by kbarrow on 2009-01-02
> **albinootje said:**
> Thanks.
After loading the module, can you show the output of :
```

lsmod|grep 3c

```


Output shows 3c59x and sis900 loaded.
```

3c59x           49064   0
mii             13440   2 3c59x, sis900

```

---

### Post by albinootje on 2009-01-02
> **kbarrow said:**
> Output shows 3c59x and sis900 loaded.
```

3c59x           49064   0
mii             13440   2 3c59x, sis900

```

Well, good.. What gives :
```

ifconfig -a
dmesg | tail -n 40

```

Perhaps it is assigned to eth4 or eth5, hence the -a for ifconfig.
(Not a joke, have seen that in real life before).

---

### Post by kbarrow on 2009-01-02
> **albinootje said:**
> Well, good.. What gives :
```

ifconfig -a
dmesg | tail -n 40

```

Perhaps it is assigned to eth4 or eth5, hence the -a for ifconfig.
(Not a joke, have seen that in real life before).

```

 ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:07:95:aa:43:69  
          inet addr:75.110.150.101  Bcast:75.110.150.255  Mask:255.255.255.0
          inet6 addr: fe80::207:95ff:feaa:4369/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7610 errors:0 dropped:0 overruns:0 frame:0
          TX packets:105 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:584553 (584.5 KB)  TX bytes:13746 (13.7 KB)
          Interrupt:11 Base address:0xde00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

pan0      Link encap:Ethernet  HWaddr 12:ca:1a:04:c3:78  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

```

dmesg | -n tail 40
bash: -n: command not found

```

---

### Post by albinootje on 2009-01-02
Okay, thanks for posting the output.
I'm running out of ideas.

A last request, can you post the output of :
```

dmesg

```
to see whether there's some conflict somewhere or some BIOS bug.

---

### Post by kbarrow on 2009-01-02
> **albinootje said:**
> Okay, thanks for posting the output.
I'm running out of ideas.

A last request, can you post the output of :
```

dmesg

```
to see whether there's some conflict somewhere or some BIOS bug.


I have checked the Bios and can't for the life of me see anything set wrong. As usual I've started with the defalt settings with the bios and the installation.
```

[    0.380000] NetLabel:  domain hash size = 128
[    0.380000] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.380000] NetLabel:  unlabeled traffic allowed by default
[    0.380000] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.380000]    actual entries 65620
[    0.380000] AppArmor: AppArmor Filesystem Enabled
[    0.380000] system 00:00: iomem range 0x0-0x9fbff could not be reserved
[    0.380000] system 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
[    0.380000] system 00:00: iomem range 0xdc000-0xdffff could not be reserved
[    0.380000] system 00:00: iomem range 0xf0000-0xfffff could not be reserved
[    0.380000] system 00:00: iomem range 0x100000-0xf7fffff could not be reserved
[    0.380000] system 00:00: iomem range 0xffffffffffef0000-0xffffffffffefffff has been reserved
[    0.380000] system 00:00: iomem range 0xffffffffffff0000-0xffffffffffffffff has been reserved
[    0.390038] pci 0000:00:02.0: PCI bridge, secondary bus 0000:01
[    0.390038] pci 0000:00:02.0:   IO window: 0xc000-0xcfff
[    0.390038] pci 0000:00:02.0:   MEM window: 0xefe00000-0xefefffff
[    0.390038] pci 0000:00:02.0:   PREFETCH window: 0x000000dfc00000-0x000000efcfffff
[    0.390038] pci 0000:00:02.0: setting latency timer to 64
[    0.390038] bus: 00 index 0 io port: [0, ffff]
[    0.390038] bus: 00 index 1 mmio: [0, ffffffffffffffff]
[    0.390038] bus: 01 index 0 io port: [c000, cfff]
[    0.390038] bus: 01 index 1 mmio: [efe00000, efefffff]
[    0.390038] bus: 01 index 2 mmio: [dfc00000, efcfffff]
[    0.390038] bus: 01 index 3 mmio: [0, 0]
[    0.390038] NET: Registered protocol family 2
[    0.395217] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[    0.395217] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[    0.395217] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.395217] TCP: Hash tables configured (established 8192 bind 8192)
[    0.395217] TCP reno registered
[    0.398463] NET: Registered protocol family 1
[    0.398463] checking if image is initramfs... it is
[    2.730061] Freeing initrd memory: 8017k freed
[    2.740061] audit: initializing netlink socket (disabled)
[    2.740061] type=2000 audit(1230948073.740:1): initialized
[    2.750067] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    2.780070] VFS: Disk quotas dquot_6.5.1
[    2.780070] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    2.780070] msgmni has been set to 480
[    2.780070] io scheduler noop registered
[    2.780070] io scheduler anticipatory registered
[    2.780070] io scheduler deadline registered (default)
[    2.780070] io scheduler cfq registered
[    2.840031] pci 0000:01:00.0: Boot video device
[    2.840031] isapnp: Scanning for PnP cards...
[    3.190013] isapnp: No Plug & Play device found
[    3.860080] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    3.870080] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    3.870080] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    3.900077] brd: module loaded
[    3.900077] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    3.900077] PNP: PS/2 Controller [PNP0303] at 0x60,0x64 irq 1
[    3.900077] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    3.900077] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.906528] mice: PS/2 mouse device common for all mice
[    3.916528] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    3.916528] rtc0: alarms up to one day
[    3.916528] EISA: Probing bus 0 at eisa.0
[    3.916528] EISA: Detected 0 cards.
[    3.916528] cpuidle: using governor ladder
[    3.916528] cpuidle: using governor menu
[    3.916528] TCP cubic registered
[    3.916528] Using IPI No-Shortcut mode
[    3.916528] registered taskstats version 1
[    3.916528]   Magic number: 9:362:4
[    3.916528] tty ttybf: hash matches
[    3.916528] rtc_cmos 00:04: setting system clock to 2009-01-03 02:01:17 UTC (1230948077)
[    3.920071] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.920071] EDD information not available.
[    3.920071] Freeing unused kernel memory: 436k freed
[    3.920071] Write protecting the kernel text: 2632k
[    3.920071] Write protecting the kernel read-only data: 956k
[    3.940087] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    4.040088] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    5.010123] fuse init (API version 7.9)
[    5.271365] thermal: Unknown symbol acpi_processor_set_thermal_limit
[    6.710138] SCSI subsystem initialized
[    6.850145] usbcore: registered new interface driver usbfs
[    6.850145] usbcore: registered new interface driver hub
[    6.850145] usbcore: registered new device driver usb
[    6.970151] libata version 3.00 loaded.
[    6.980158] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    6.990158] PCI: setting IRQ 10 as level-triggered
[    6.990158] ohci_hcd 0000:00:01.2: found PCI INT D -> IRQ 10
[    6.990158] ohci_hcd 0000:00:01.2: sharing IRQ 10 with 0000:00:01.3
[    6.990158] ohci_hcd 0000:00:01.2: OHCI Host Controller
[    6.990158] ohci_hcd 0000:00:01.2: new USB bus registered, assigned bus number 1
[    6.990158] ohci_hcd 0000:00:01.2: irq 10, io mem 0xf3ffe000
[    7.000195] sis900.c: v1.08.10 Apr. 2 2006
[    7.050226] usb usb1: configuration #1 chosen from 1 choice
[    7.050226] hub 1-0:1.0: USB hub found
[    7.050226] hub 1-0:1.0: 3 ports detected
[    7.160220] ohci_hcd 0000:00:01.3: found PCI INT D -> IRQ 10
[    7.160220] ohci_hcd 0000:00:01.3: sharing IRQ 10 with 0000:00:01.2
[    7.160220] ohci_hcd 0000:00:01.3: OHCI Host Controller
[    7.160220] ohci_hcd 0000:00:01.3: new USB bus registered, assigned bus number 2
[    7.160220] ohci_hcd 0000:00:01.3: irq 10, io mem 0xf3fff000
[    7.220149] usb usb2: configuration #1 chosen from 1 choice
[    7.220149] hub 2-0:1.0: USB hub found
[    7.220149] hub 2-0:1.0: 2 ports detected
[    7.440150] PCI: setting IRQ 11 as level-triggered
[    7.440150] sis900 0000:00:01.1: found PCI INT C -> IRQ 11
[    7.440150] sis900 0000:00:01.1: sharing IRQ 11 with 0000:00:0f.1
[    7.440150] 0000:00:01.1: SiS 900 Internal MII PHY transceiver found at address 1.
[    7.450150] 0000:00:01.1: Using transceiver found at address 1 as default
[    7.650135] usb 2-2: new low speed USB device using ohci_hcd and address 2
[    7.870143] usb 2-2: configuration #1 chosen from 1 choice
[    9.090162] eth0: SiS 900 PCI Fast Ethernet at 0xde00, IRQ 11, 00:07:95:aa:43:69
[    9.110198] pata_sis 0000:00:00.1: version 0.5.2
[    9.110198] scsi0 : pata_sis
[    9.110198] scsi1 : pata_sis
[    9.110198] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    9.110198] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    9.340175] ata1.00: ATA-5: WDC WD100EB-00CGH0, 24.A4G24, max UDMA/100
[    9.340175] ata1.00: 19541088 sectors, multi 16: LBA 
[    9.340175] ata1.01: ATA-3: WDC AC33200L, 32.41N37, max UDMA/33
[    9.340175] ata1.01: 6346368 sectors, multi 16: LBA 
[    9.380189] ata1.00: configured for UDMA/100
[    9.420180] ata1.01: configured for UDMA/33
[    9.480180] ata1.00: configured for UDMA/100
[    9.520183] ata1.01: configured for UDMA/33
[    9.520183] ata1: EH complete
[    9.680273] ata2.00: ATAPI: ATAPI CDROM, V14AM, max UDMA/33
[    9.700183] ata2.00: configured for UDMA/33
[    9.700183] scsi 0:0:0:0: Direct-Access     ATA      WDC WD100EB-00CG 24.A PQ: 0 ANSI: 5
[    9.700183] scsi 0:0:1:0: Direct-Access     ATA      WDC AC33200L     32.4 PQ: 0 ANSI: 5
[    9.700183] scsi 1:0:0:0: CD-ROM                     ATAPI CDROM.     14AM PQ: 0 ANSI: 5
[   12.660290] usbcore: registered new interface driver hiddev
[   12.670230] input: A4Tech PS/2+USB Mouse as /devices/pci0000:00/0000:00:01.3/usb2/2-2/2-2:1.0/input/input3
[   12.710239] input,hidraw0: USB HID v1.10 Mouse [A4Tech PS/2+USB Mouse] on usb-0000:00:01.3-2
[   12.710239] usbcore: registered new interface driver usbhid
[   12.710239] usbhid: v2.6:USB HID core driver
[   12.750248] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[   12.750248] scsi 0:0:1:0: Attached scsi generic sg1 type 0
[   12.750248] scsi 1:0:0:0: Attached scsi generic sg2 type 5
[   13.000271] Driver 'sd' needs updating - please use bus_type methods
[   13.000271] sd 0:0:0:0: [sda] 19541088 512-byte hardware sectors (10005 MB)
[   13.000271] sd 0:0:0:0: [sda] Write Protect is off
[   13.000271] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   13.000271] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   13.000271] sd 0:0:0:0: [sda] 19541088 512-byte hardware sectors (10005 MB)
[   13.000271] sd 0:0:0:0: [sda] Write Protect is off
[   13.000271] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   13.000271] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   13.000271]  sda: sda1 sda2 <<4>Driver 'sr' needs updating - please use bus_type methods
[   13.070222]  sda5 >
[   13.080222] sd 0:0:0:0: [sda] Attached SCSI disk
[   13.080222] sd 0:0:1:0: [sdb] 6346368 512-byte hardware sectors (3249 MB)
[   13.080222] sd 0:0:1:0: [sdb] Write Protect is off
[   13.080222] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   13.080222] sd 0:0:1:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   13.080222] sd 0:0:1:0: [sdb] 6346368 512-byte hardware sectors (3249 MB)
[   13.080222] sd 0:0:1:0: [sdb] Write Protect is off
[   13.080222] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   13.080222] sd 0:0:1:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   13.080222]  sdb:
[   13.090243] sd 0:0:1:0: [sdb] Attached SCSI disk
[   13.150241] sr0: scsi3-mmc drive: 0x/0x cd/rw xa/form2 cdda tray
[   13.150241] Uniform CD-ROM driver Revision: 3.20
[   13.150241] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   14.250234] PM: Starting manual resume from disk
[   14.250234] PM: Resume from partition 8:5
[   14.250234] PM: Checking hibernation image.
[   14.250234] PM: Resume from disk failed.
[   14.431312] kjournald starting.  Commit interval 5 seconds
[   14.431312] EXT3-fs: mounted filesystem with ordered data mode.
[   25.619508] udevd version 124 started
[   27.980450] Linux agpgart interface v0.103
[   28.120454] agpgart-sis 0000:00:00.0: SiS chipset [1039/0630]
[   28.120454] agpgart-sis 0000:00:00.0: AGP aperture is 64M @ 0xf4000000
[   29.050495] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   29.070482] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   29.100585] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   33.800555] PCI: setting IRQ 9 as level-triggered
[   33.800555] C-Media PCI 0000:00:0f.0: found PCI INT A -> IRQ 9
[   43.373625] loop: module loaded
[   43.710703] parport_pc 00:0a: reported by Plug and Play BIOS
[   43.710703] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   43.790743] lp0: using parport0 (interrupt-driven).
[   45.250723] Adding 465844k swap on /dev/sda5.  Priority:-1 extents:1 across:465844k
[   46.070744] EXT3 FS on sda1, internal journal
[   49.240828] type=1505 audit(1230948122.435:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=3606
[   49.500833] type=1505 audit(1230948122.695:3): operation="profile_load" name="/usr/bin/freshclam" name2="default" pid=3611
[   50.340839] type=1505 audit(1230948123.535:4): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=3615
[   50.340839] type=1505 audit(1230948123.535:5): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3615
[   50.952031] ip_tables: (C) 2000-2006 Netfilter Core Team
[   51.180772] nf_conntrack version 0.5.0 (4096 buckets, 16384 max)
[   51.180772] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Plase use
[   51.180772] nf_conntrack.acct=1 kernel paramater, acct=1 nf_conntrack module option or
[   51.180772] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   51.660805] NET: Registered protocol family 10
[   51.660805] lo: Disabled Privacy Extensions
[   51.720808] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   54.960874] NET: Registered protocol family 17
[   55.410826] eth0: Media Link On 100mbps full-duplex 
[   58.720924] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=84.23.152.213 DST=75.110.150.101 LEN=101 TOS=0x00 PREC=0x00 TTL=107 ID=12605 PROTO=UDP SPT=55147 DPT=8776 LEN=81 
[   58.760931] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=189.69.150.59 DST=75.110.150.101 LEN=101 TOS=0x00 PREC=0x00 TTL=47 ID=28458 PROTO=UDP SPT=19926 DPT=8776 LEN=81 
[   58.850926] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=79.134.64.103 DST=75.110.150.101 LEN=48 TOS=0x00 PREC=0x00 TTL=107 ID=63331 DF PROTO=TCP SPT=1235 DPT=8776 WINDOW=65535 RES=0x00 SYN URGP=0 
[   58.959005] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=83.164.31.101 DST=75.110.150.101 LEN=101 TOS=0x00 PREC=0x00 TTL=108 ID=1272 PROTO=UDP SPT=55141 DPT=8776 LEN=81 
[   59.230938] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=24.164.4.120 DST=75.110.150.101 LEN=101 TOS=0x00 PREC=0x00 TTL=112 ID=7809 PROTO=UDP SPT=55547 DPT=8776 LEN=81 
[   59.296945] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=76.177.12.174 DST=75.110.150.101 LEN=89 TOS=0x00 PREC=0x00 TTL=113 ID=24984 PROTO=UDP SPT=2412 DPT=8776 LEN=69 
[   59.470937] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=122.164.24.1 DST=75.110.150.101 LEN=131 TOS=0x00 PREC=0x00 TTL=110 ID=49706 PROTO=UDP SPT=64243 DPT=55916 LEN=111 
[   59.780907] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=216.211.49.187 DST=75.110.150.101 LEN=48 TOS=0x00 PREC=0x00 TTL=117 ID=8271 DF PROTO=TCP SPT=61669 DPT=30777 WINDOW=8192 RES=0x00 SYN URGP=0 
[   59.860935] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=115.129.17.134 DST=75.110.150.101 LEN=48 TOS=0x00 PREC=0x00 TTL=103 ID=7519 DF PROTO=TCP SPT=55886 DPT=30777 WINDOW=8192 RES=0x00 SYN URGP=0 
[   60.000920] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=79.107.56.233 DST=75.110.150.101 LEN=101 TOS=0x00 PREC=0x00 TTL=110 ID=32400 PROTO=UDP SPT=27114 DPT=8776 LEN=81 
[   63.560465] acpi_cpufreq: Unknown symbol acpi_processor_notify_smm
[   63.560465] acpi_cpufreq: Unknown symbol acpi_processor_unregister_performance
[   63.560465] acpi_cpufreq: Unknown symbol acpi_processor_preregister_performance
[   63.560465] acpi_cpufreq: Unknown symbol acpi_processor_register_performance
[   63.741001] eth0: no IPv6 routers present
[   66.291044] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   66.555091] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   69.666866] ppdev: user-space parallel port driver
[   76.271163] Bluetooth: Core ver 2.13
[   76.271163] NET: Registered protocol family 31
[   76.271163] Bluetooth: HCI device and connection manager initialized
[   76.271163] Bluetooth: HCI socket layer initialized
[   76.371193] Bluetooth: L2CAP ver 2.11
[   76.371193] Bluetooth: L2CAP socket layer initialized
[   76.441660] Bluetooth: RFCOMM socket layer initialized
[   76.441660] Bluetooth: RFCOMM TTY layer initialized
[   76.441660] Bluetooth: RFCOMM ver 1.10
[   76.491199] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   76.491199] Bluetooth: BNEP filters: protocol multicast
[   76.611184] Bridge firewalling registered
[   76.621185] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   76.711205] Bluetooth: SCO (Voice Link) ver 0.6
[   76.711205] Bluetooth: SCO socket layer initialized
[   78.913336] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=200.92.100.162 DST=75.110.150.101 LEN=83 TOS=0x00 PREC=0x00 TTL=112 ID=64670 PROTO=UDP SPT=46269 DPT=8776 LEN=63 
[   83.511300] [drm] Initialized drm 1.1.0 20060810
[   83.551306] pci 0000:01:00.0: setting latency timer to 64
[   83.551306] [drm] Initialized sis 1.3.0 20070626 on minor 0
[   83.561304] agpgart-sis 0000:00:00.0: AGP 2.0 bridge
[   83.561304] agpgart-sis 0000:00:00.0: putting AGP V2 device into 4x mode
[   83.561304] pci 0000:01:00.0: putting AGP V2 device into 4x mode
[   98.907172] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=69.137.223.151 DST=75.110.150.101 LEN=109 TOS=0x00 PREC=0x20 TTL=109 ID=57004 PROTO=UDP SPT=21621 DPT=8776 LEN=89 
[  118.737006] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=24.222.113.110 DST=75.110.150.101 LEN=48 TOS=0x00 PREC=0x00 TTL=111 ID=41623 DF PROTO=TCP SPT=1090 DPT=30777 WINDOW=64512 RES=0x00 SYN URGP=0 
[  138.868125] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=72.63.20.189 DST=75.110.150.101 LEN=101 TOS=0x00 PREC=0x00 TTL=110 ID=3748 PROTO=UDP SPT=22544 DPT=8776 LEN=81 
[  158.782434] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=76.118.218.185 DST=75.110.150.101 LEN=101 TOS=0x00 PREC=0x00 TTL=110 ID=21299 PROTO=UDP SPT=6123 DPT=8776 LEN=81 
[  179.388749] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=96.49.102.43 DST=75.110.150.101 LEN=48 TOS=0x00 PREC=0x00 TTL=112 ID=17810 DF PROTO=TCP SPT=4406 DPT=30777 WINDOW=16384 RES=0x00 SYN URGP=0 
[  198.982467] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=69.146.206.116 DST=75.110.150.101 LEN=109 TOS=0x00 PREC=0x00 TTL=112 ID=52578 PROTO=UDP SPT=46329 DPT=8776 LEN=89 
[  218.742832] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=80.222.54.8 DST=75.110.150.101 LEN=52 TOS=0x00 PREC=0x00 TTL=107 ID=21479 DF PROTO=TCP SPT=16130 DPT=30777 WINDOW=8192 RES=0x00 SYN URGP=0 
[  238.863503] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=81.215.128.242 DST=75.110.150.101 LEN=101 TOS=0x00 PREC=0x00 TTL=109 ID=1996 PROTO=UDP SPT=44628 DPT=8776 LEN=81 
[  246.953773] ppdev0: registered pardevice
[  247.010127] ppdev0: unregistered pardevice
[  247.354167] ppdev0: registered pardevice
[  247.450534] ppdev0: unregistered pardevice
[  253.243813] ppdev0: registered pardevice
[  253.285755] ppdev0: unregistered pardevice
[  258.834859] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=99.194.176.187 DST=75.110.150.101 LEN=48 TOS=0x00 PREC=0x00 TTL=112 ID=3865 DF PROTO=TCP SPT=60511 DPT=30777 WINDOW=8192 RES=0x00 SYN URGP=0 
[  279.036783] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=71.195.206.240 DST=75.110.150.101 LEN=131 TOS=0x00 PREC=0x20 TTL=109 ID=17182 PROTO=UDP SPT=56959 DPT=55417 LEN=111 
[  298.863232] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=76.177.12.174 DST=75.110.150.101 LEN=89 TOS=0x00 PREC=0x00 TTL=113 ID=24253 PROTO=UDP SPT=2412 DPT=8776 LEN=69 
[  318.754433] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=71.241.38.192 DST=75.110.150.101 LEN=101 TOS=0x00 PREC=0x00 TTL=116 ID=21797 PROTO=UDP SPT=28117 DPT=8776 LEN=81 
[  338.945718] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=69.125.111.180 DST=75.110.150.101 LEN=109 TOS=0x00 PREC=0x00 TTL=115 ID=15240 PROTO=UDP SPT=5652 DPT=8776 LEN=89 
[  358.825465] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=207.61.202.196 DST=75.110.150.101 LEN=101 TOS=0x00 PREC=0x00 TTL=111 ID=16226 PROTO=UDP SPT=60742 DPT=8776 LEN=81 
[  378.759110] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=83.252.1.161 DST=75.110.150.101 LEN=48 TOS=0x00 PREC=0x00 TTL=112 ID=21144 DF PROTO=TCP SPT=55103 DPT=30777 WINDOW=8192 RES=0x00 SYN URGP=0 
[  398.727174] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=76.87.250.207 DST=75.110.150.101 LEN=101 TOS=0x00 PREC=0x00 TTL=111 ID=13964 PROTO=UDP SPT=36523 DPT=8776 LEN=81 
[  418.948848] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=84.131.122.51 DST=75.110.150.101 LEN=48 TOS=0x00 PREC=0x00 TTL=118 ID=59233 DF PROTO=TCP SPT=2437 DPT=30777 WINDOW=65535 RES=0x00 SYN URGP=0 
[  438.977859] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=24.58.103.74 DST=75.110.150.101 LEN=109 TOS=0x00 PREC=0x00 TTL=114 ID=12555 PROTO=UDP SPT=14858 DPT=8776 LEN=89 
[  459.362997] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=96.231.104.95 DST=75.110.150.101 LEN=109 TOS=0x00 PREC=0x00 TTL=117 ID=27346 PROTO=UDP SPT=33432 DPT=8776 LEN=89 
[  478.790903] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=60.44.50.20 DST=75.110.150.101 LEN=48 TOS=0x00 PREC=0x00 TTL=108 ID=7417 DF PROTO=TCP SPT=3769 DPT=8776 WINDOW=16384 RES=0x00 SYN URGP=0 
[  498.841677] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=72.171.233.71 DST=75.110.150.101 LEN=44 TOS=0x00 PREC=0x00 TTL=238 ID=62880 DF PROTO=TCP SPT=10561 DPT=8776 WINDOW=16000 RES=0x00 SYN URGP=0 
[  519.050102] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=80.104.117.239 DST=75.110.150.101 LEN=101 TOS=0x00 PREC=0x00 TTL=113 ID=21032 PROTO=UDP SPT=11273 DPT=8776 LEN=81 
[  538.956585] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=76.30.53.134 DST=75.110.150.101 LEN=89 TOS=0x00 PREC=0x20 TTL=110 ID=11457 PROTO=UDP SPT=15857 DPT=8776 LEN=69 
[  558.898488] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=80.212.174.235 DST=75.110.150.101 LEN=48 TOS=0x00 PREC=0x00 TTL=111 ID=21408 DF PROTO=TCP SPT=59958 DPT=30777 WINDOW=8192 RES=0x00 SYN URGP=0 
[  578.778787] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=74.215.226.147 DST=75.110.150.101 LEN=48 TOS=0x00 PREC=0x00 TTL=110 ID=2313 DF PROTO=TCP SPT=50500 DPT=8776 WINDOW=16384 RES=0x00 SYN URGP=0 
[  598.809080] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=67.53.133.245 DST=75.110.150.101 LEN=89 TOS=0x00 PREC=0x00 TTL=112 ID=30734 PROTO=UDP SPT=25931 DPT=8776 LEN=69 
[  618.959443] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=72.171.233.71 DST=75.110.150.101 LEN=44 TOS=0x00 PREC=0x00 TTL=238 ID=43353 DF PROTO=TCP SPT=10708 DPT=8776 WINDOW=16000 RES=0x00 SYN URGP=0 
[  638.828082] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=172.190.200.131 DST=75.110.150.101 LEN=101 TOS=0x00 PREC=0x00 TTL=111 ID=12927 PROTO=UDP SPT=12248 DPT=8776 LEN=81 
[  658.981850] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=200.92.100.162 DST=75.110.150.101 LEN=48 TOS=0x00 PREC=0x00 TTL=112 ID=33578 DF PROTO=TCP SPT=2057 DPT=8776 WINDOW=65535 RES=0x00 SYN URGP=0 
[  678.970378] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=71.207.66.240 DST=75.110.150.101 LEN=101 TOS=0x00 PREC=0x20 TTL=109 ID=23378 PROTO=UDP SPT=36217 DPT=8776 LEN=81 
[  699.284949] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=122.16.154.185 DST=75.110.150.101 LEN=83 TOS=0x00 PREC=0x00 TTL=111 ID=33906 PROTO=UDP SPT=6346 DPT=8776 LEN=63 
[  718.774576] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=24.193.32.70 DST=75.110.150.101 LEN=48 TOS=0x00 PREC=0x00 TTL=114 ID=9763 DF PROTO=TCP SPT=64869 DPT=30777 WINDOW=8192 RES=0x00 SYN URGP=0 
[  739.121189] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=89.139.156.44 DST=75.110.150.101 LEN=48 TOS=0x00 PREC=0x00 TTL=110 ID=16893 DF PROTO=TCP SPT=2618 DPT=30777 WINDOW=65535 RES=0x00 SYN URGP=0 
[  760.608159] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=59.93.241.242 DST=75.110.150.101 LEN=101 TOS=0x00 PREC=0x00 TTL=108 ID=62658 PROTO=UDP SPT=44353 DPT=43359 LEN=81 
[  778.741557] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=68.229.149.65 DST=75.110.150.101 LEN=109 TOS=0x00 PREC=0x00 TTL=115 ID=44101 PROTO=UDP SPT=6346 DPT=8776 LEN=89 
[  798.855404] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=59.100.118.248 DST=75.110.150.101 LEN=109 TOS=0x00 PREC=0x00 TTL=105 ID=53932 PROTO=UDP SPT=9680 DPT=8776 LEN=89 
[  818.762484] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=68.16.155.123 DST=75.110.150.101 LEN=101 TOS=0x00 PREC=0x00 TTL=105 ID=22600 PROTO=UDP SPT=28724 DPT=8776 LEN=81 
[  839.245194] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=69.124.49.149 DST=75.110.150.101 LEN=109 TOS=0x00 PREC=0x00 TTL=116 ID=169 PROTO=UDP SPT=21981 DPT=8776 LEN=89 
[  859.382759] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=24.191.12.198 DST=75.110.150.101 LEN=109 TOS=0x00 PREC=0x00 TTL=115 ID=62 PROTO=UDP SPT=20817 DPT=8776 LEN=89 
[  879.043310] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=64.38.88.220 DST=75.110.150.101 LEN=109 TOS=0x00 PREC=0x00 TTL=114 ID=4956 PROTO=UDP SPT=48878 DPT=8776 LEN=89 
[  899.419610] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=68.16.155.123 DST=75.110.150.101 LEN=101 TOS=0x00 PREC=0x00 TTL=105 ID=28579 PROTO=UDP SPT=28724 DPT=8776 LEN=81 
[  919.239219] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=190.53.154.100 DST=75.110.150.101 LEN=48 TOS=0x00 PREC=0x00 TTL=49 ID=37345 DF PROTO=TCP SPT=56591 DPT=8776 WINDOW=65535 RES=0x00 SYN URGP=0 
[  938.854203] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=204.186.128.157 DST=75.110.150.101 LEN=109 TOS=0x00 PREC=0x00 TTL=111 ID=27737 PROTO=UDP SPT=12926 DPT=8776 LEN=89 
[  958.804522] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=71.65.40.106 DST=75.110.150.101 LEN=52 TOS=0x00 PREC=0x00 TTL=115 ID=14658 DF PROTO=TCP SPT=61922 DPT=8776 WINDOW=8192 RES=0x00 SYN URGP=0 
[  979.094901] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=58.89.159.81 DST=75.110.150.101 LEN=89 TOS=0x00 PREC=0x00 TTL=45 ID=10470 PROTO=UDP SPT=6346 DPT=8776 LEN=69 
[  998.837926] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=83.204.136.23 DST=75.110.150.101 LEN=109 TOS=0x00 PREC=0x00 TTL=112 ID=29987 PROTO=UDP SPT=28555 DPT=8776 LEN=89 
[ 1019.029985] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=141.155.24.203 DST=75.110.150.101 LEN=48 TOS=0x00 PREC=0x00 TTL=114 ID=26977 DF PROTO=TCP SPT=4463 DPT=8776 WINDOW=16384 RES=0x00 SYN URGP=0 
[ 1039.465783] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=88.192.94.120 DST=75.110.150.101 LEN=48 TOS=0x00 PREC=0x00 TTL=108 ID=63603 DF PROTO=TCP SPT=4741 DPT=30777 WINDOW=65535 RES=0x00 SYN URGP=0 
[ 1058.806099] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=96.49.35.113 DST=75.110.150.101 LEN=89 TOS=0x00 PREC=0x00 TTL=112 ID=28795 PROTO=UDP SPT=4509 DPT=8776 LEN=69 
[ 1079.186336] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=98.116.53.207 DST=75.110.150.101 LEN=89 TOS=0x00 PREC=0x00 TTL=116 ID=55317 PROTO=UDP SPT=2994 DPT=8776 LEN=69 
[ 1098.763203] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=71.90.232.255 DST=75.110.150.101 LEN=109 TOS=0x00 PREC=0x00 TTL=109 ID=1060 PROTO=UDP SPT=55148 DPT=8776 LEN=89 
[ 1118.933769] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=75.80.190.87 DST=75.110.150.101 LEN=48 TOS=0x00 PREC=0x00 TTL=111 ID=51549 DF PROTO=TCP SPT=4207 DPT=30777 WINDOW=65535 RES=0x00 SYN URGP=0 
[ 1138.737326] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=98.193.124.138 DST=75.110.150.101 LEN=101 TOS=0x00 PREC=0x20 TTL=108 ID=8709 PROTO=UDP SPT=23849 DPT=8776 LEN=81 
[ 1158.767497] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=77.54.134.245 DST=75.110.150.101 LEN=48 TOS=0x08 PREC=0x40 TTL=108 ID=12876 DF PROTO=TCP SPT=64067 DPT=30777 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 1180.497825] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=93.102.5.246 DST=75.110.150.101 LEN=48 TOS=0x00 PREC=0x00 TTL=105 ID=31781 DF PROTO=TCP SPT=2375 DPT=55419 WINDOW=16384 RES=0x00 SYN URGP=0 
[ 1198.758134] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=142.162.42.141 DST=75.110.150.101 LEN=48 TOS=0x00 PREC=0x00 TTL=107 ID=23334 DF PROTO=TCP SPT=61495 DPT=8776 WINDOW=16384 RES=0x00 SYN URGP=0 
[ 1218.958452] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=71.207.66.240 DST=75.110.150.101 LEN=101 TOS=0x00 PREC=0x20 TTL=109 ID=39451 PROTO=UDP SPT=36217 DPT=8776 LEN=81 
[ 1239.238726] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=68.40.216.122 DST=75.110.150.101 LEN=109 TOS=0x00 PREC=0x20 TTL=108 ID=23005 PROTO=UDP SPT=31886 DPT=8776 LEN=89 
[ 1258.829010] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=77.54.134.245 DST=75.110.150.101 LEN=52 TOS=0x08 PREC=0x40 TTL=108 ID=19057 DF PROTO=TCP SPT=64094 DPT=30777 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 1278.829408] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=75.170.193.2 DST=75.110.150.101 LEN=109 TOS=0x00 PREC=0x00 TTL=111 ID=34515 PROTO=UDP SPT=5861 DPT=8776 LEN=89 
[ 1299.389694] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=71.232.66.98 DST=75.110.150.101 LEN=48 TOS=0x00 PREC=0x20 TTL=106 ID=10422 DF PROTO=TCP SPT=3967 DPT=30777 WINDOW=65535 RES=0x00 SYN URGP=0 
[ 1318.809947] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=69.134.140.135 DST=75.110.150.101 LEN=89 TOS=0x00 PREC=0x00 TTL=112 ID=13346 PROTO=UDP SPT=35498 DPT=8776 LEN=69 
[ 1339.310221] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=71.241.38.192 DST=75.110.150.101 LEN=101 TOS=0x00 PREC=0x00 TTL=116 ID=54046 PROTO=UDP SPT=28117 DPT=8776 LEN=81 
[ 1358.760487] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=69.201.148.56 DST=75.110.150.101 LEN=48 TOS=0x00 PREC=0x00 TTL=115 ID=27746 DF PROTO=TCP SPT=50337 DPT=30777 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 1378.760847] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=24.76.184.20 DST=75.110.150.101 LEN=109 TOS=0x00 PREC=0x00 TTL=110 ID=64957 PROTO=UDP SPT=10877 DPT=8776 LEN=89 
[ 1399.491209] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=90.201.121.156 DST=75.110.150.101 LEN=48 TOS=0x00 PREC=0x00 TTL=115 ID=19745 DF PROTO=TCP SPT=64214 DPT=30777 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 1418.741456] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=75.9.90.31 DST=75.110.150.101 LEN=48 TOS=0x00 PREC=0x00 TTL=110 ID=16125 DF PROTO=TCP SPT=55710 DPT=30777 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 1439.471745] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=62.3.64.29 DST=75.110.150.101 LEN=48 TOS=0x00 PREC=0x00 TTL=111 ID=7483 DF PROTO=TCP SPT=54524 DPT=30777 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 1459.132062] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=99.150.11.60 DST=75.110.150.101 LEN=48 TOS=0x00 PREC=0x00 TTL=113 ID=15588 DF PROTO=TCP SPT=49549 DPT=30777 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 1479.342349] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=68.81.115.62 DST=75.110.150.101 LEN=52 TOS=0x00 PREC=0x00 TTL=110 ID=10042 DF PROTO=TCP SPT=51613 DPT=30777 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 1499.122607] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:07:95:aa:43:69:00:03:6c:4a:f4:21:08:00 SRC=71.141.252.137 DST=75.110.150.101 LEN=101 TOS=0x00 PREC=0x00 TTL=114 ID=60434 PROTO=UDP SPT=39834 DPT=8776 LEN=81 
[ 1516.432891] eth0: Media Link Off

```

---

### Post by Jose Catre-Vandis on 2009-01-03
Back to basics:

1. try a different pci slot for the card?
2. try to disable/remove the NIC that works?
3. try another (non 3com :)) NIC instead?
4. test 3com NIc in another PC (although I think you said it works on same PC under windows?)

Show output of test I asked for, seems that the module is loading, but has nothing to hook onto, thus lshw / lspci are important to know about after module is loaded.

---

