---
title: "DWL-G510 dot detected with ndiswrapper"
date: 2006-03-06
forum: Networking &amp; Wireless
---

### Post by Benja on 2006-03-06
I have been trying to get my wireless network card working for about 2 days now :mad: I would have thought it would be detected because MadWiFi is installed and supports the g510 but no... So i have installed ndiswrapper followed all the documentation and posts here and have installed the driver 

```
ndiswrapper -i blahblah.ini
```

I get the message the an invalid driver message when i use the command 

```
ndiswrapper &#8211;l
```

I have a GUI tool for ndiswrapper which tells me the hardware is not detected. 

When i click on network settings i see my Ethernet LAN card and a dialup interface(i have no dial-up modem :confused: )

I am running ubuntu 1.10 breezy 32bit(but have 64bit cpu)

edit: woops typo in the title

---

### Post by Lambert on 2006-03-06
What's the output you get for these terminal commands

```
sudo lshw -C network
```

```
cardctl ident
```

```
lspci -v
```

---

### Post by Benja on 2006-03-06
Very sorry for the late reply, i was at TAFE (School)

here is the output:

 ```
 *-network UNCLAIMED
       description: Network controller
       product: RaLink
       vendor: RaLink
       physical id: 8
       bus info: pci@05:08.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       resources: iomemory:fdff8000-fdffffff irq:5
ben@ubuntu:~$
```

```
ben@ubuntu:~$ cardctl ident
no pcmcia driver in /proc/devices
ben@ubuntu:~$
```

```

ben@ubuntu:~$ lspci -v
0000:00:00.0 Memory controller: nVidia Corporation: Unknown device 005e (rev a3)        Subsystem: ABIT Computer Corp.: Unknown device 1c1a
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: <available only to root>

0000:00:01.0 ISA bridge: nVidia Corporation: Unknown device 0050 (rev a3)
        Subsystem: ABIT Computer Corp.: Unknown device 1c1a
        Flags: bus master, 66MHz, fast devsel, latency 0

0000:00:01.1 SMBus: nVidia Corporation: Unknown device 0052 (rev a2)
        Subsystem: ABIT Computer Corp.: Unknown device 1c1a
        Flags: 66MHz, fast devsel, IRQ 7
        I/O ports at bc00 [size=32]
        I/O ports at 1c00 [size=64]
        I/O ports at 1c40 [size=64]
        Capabilities: <available only to root>

0000:00:02.0 USB Controller: nVidia Corporation: Unknown device 005a (rev a2) (prog-if 10 [OHCI])
        Subsystem: ABIT Computer Corp.: Unknown device 1c1a
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
        Memory at fe02a000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:02.1 USB Controller: nVidia Corporation: Unknown device 005b (rev a3) (prog-if 20 [EHCI])
        Subsystem: ABIT Computer Corp.: Unknown device 1c1a
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
        Memory at feb00000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:00:04.0 Multimedia audio controller: nVidia Corporation: Unknown device 0059 (rev a2)
        Subsystem: ABIT Computer Corp.: Unknown device 1c1a
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
        I/O ports at cc00 [size=256]
        I/O ports at c800 [size=256]
        Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:06.0 IDE interface: nVidia Corporation: Unknown device 0053 (rev f2) (prog-if 8a [Master SecP PriP])
        Subsystem: ABIT Computer Corp.: Unknown device 1c1a
        Flags: bus master, 66MHz, fast devsel, latency 0
        I/O ports at d000 [size=16]
        Capabilities: <available only to root>

0000:00:07.0 IDE interface: nVidia Corporation: Unknown device 0054 (rev f3) (prog-if 85 [Master SecO PriO])
        Subsystem: ABIT Computer Corp.: Unknown device 1c1a
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
        I/O ports at 09f0 [size=8]
        I/O ports at 0bf0 [size=4]
        I/O ports at 0970 [size=8]
        I/O ports at 0b70 [size=4]
        I/O ports at d400 [size=16]
        Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:08.0 IDE interface: nVidia Corporation: Unknown device 0055 (rev f3) (prog-if 85 [Master SecO PriO])
        Subsystem: ABIT Computer Corp.: Unknown device 1c1a
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
        I/O ports at 09e0 [size=8]
        I/O ports at 0be0 [size=4]
        I/O ports at 0960 [size=8]
        I/O ports at 0b60 [size=4]
        I/O ports at e800 [size=16]
        Memory at fe02e000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:09.0 PCI bridge: nVidia Corporation: Unknown device 005c (rev a2) (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: fdf00000-fdffffff
        Prefetchable memory behind bridge: fde00000-fdefffff

0000:00:0a.0 Bridge: nVidia Corporation: Unknown device 0057 (rev a3)
        Subsystem: ABIT Computer Corp.: Unknown device 1c1a
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
        Memory at fe02f000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at fc00 [size=8]
        Capabilities: <available only to root>

0000:00:0b.0 PCI bridge: nVidia Corporation: Unknown device 005d (rev a3) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        I/O behind bridge: 00006000-00006fff
        Memory behind bridge: fda00000-fdafffff
        Prefetchable memory behind bridge: 00000000fd900000-00000000fd900000
        Capabilities: <available only to root>

0000:00:0c.0 PCI bridge: nVidia Corporation: Unknown device 005d (rev a3) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        I/O behind bridge: 00007000-00007fff
        Memory behind bridge: fdc00000-fdcfffff
        Prefetchable memory behind bridge: 00000000fdb00000-00000000fdb00000
        Capabilities: <available only to root>

0000:00:0d.0 PCI bridge: nVidia Corporation: Unknown device 005d (rev a3) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 00008000-00008fff
        Memory behind bridge: fd800000-fd8fffff
        Prefetchable memory behind bridge: 00000000fdd00000-00000000fdd00000
        Capabilities: <available only to root>

0000:00:0e.0 PCI bridge: nVidia Corporation: Unknown device 005d (rev a3) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: fa000000-fcffffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000dff00000
        Capabilities: <available only to root>

0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
        Flags: fast devsel
        Capabilities: <available only to root>

0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
        Flags: fast devsel

0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
        Flags: fast devsel

0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
        Flags: fast devsel

0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 0160 (rev a1) (prog-if 00 [VGA])
        Flags: bus master, fast devsel, latency 0, IRQ 18
        Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        Memory at fb000000 (64-bit, non-prefetchable) [size=16M]
        Capabilities: <available only to root>

0000:05:08.0 Network controller: RaLink: Unknown device 0302
        Subsystem: D-Link System Inc: Unknown device 3c09
        Flags: bus master, slow devsel, latency 32, IRQ 5
        Memory at fdff8000 (32-bit, non-prefetchable) [size=32K]
        Capabilities: <available only to root>

ben@ubuntu:~$
```

---

### Post by Lambert on 2006-03-07
1. Are you using the stock kernel or did you compile and install your own?

2. I don't believe your pcmcia modules are loading and it might be because of number 1.

 run this command.

```
sudo lsmod | grep pcmc
```

you should see something like this.

```

pcmcia                 40508  0
pcmcia_core            42640  3 pcmcia,yenta_socket,rsrc_nonstatic

```

---

### Post by Benja on 2006-03-07
Yes i am using the stock kernel, I ran that command and got no output :confused: 

```
ben@ubuntu:~$ sudo lsmod | grep pcmc
ben@ubuntu:~$

```

---

### Post by Lambert on 2006-03-07
so let's see what happens when you try to load the modules.

from terminal:

```

sudo modprobe pcmcia
sudo modprobe pcmcia_core

```

---

### Post by Benja on 2006-03-07
I typed in both commands and can now get the output 

```
pcmcia                 26632  0
pcmcia_core            49668  1 pcmcia

```

---

### Post by SBFC on 2006-03-07
I&#7743; having a similar problem...maybe, same card and such.

When I try and load the pcmia modules it says they aren´t found. Just wondering how to get them.

Thanks.

---

### Post by Stone123 on 2006-03-10
Hello Lambert

I have same problem as the above , using stock ? kernel only 686-smp . 
Any update on how to fix after pcmcia . I added pcmcia and core to /etc/modules
And nothing after reboot.
And btw why are pcmcia modules needed for pci card? pcmcia are other type of device /cards ?

---

### Post by Stone123 on 2006-03-10
Ok after search 1 post more i found this :
**[http://www.ubuntuforums.org/showthread.php?t=139329&highlight=dwl-G510](http://www.ubuntuforums.org/showthread.php?t=139329&highlight=dwl-G510)**

Anyway the lspci and lshw are reporting ralink card so it should be posible to use ralink drivers since i think dlink 510 use their chipset, and its supported nativly in linux. Just to install those drivers. 

Well i ll just update to dapper and see what happends,

---

### Post by desicrew on 2006-07-06
I am posting here because no one is responding at the kubuntu forums - below is the cut and paste of what i wrote there - anyone PLEASE help

so i cleaned out everything pertaining to ndiswrapper i.e.
Code:
sudo modprobe -r mrv8k
sudo rmmod ndiswrapper
sudo apt-get remove ndiswrapper-utils
sudo rm -r /etc/ndiswrapper/
sudo rm -r /etc/modprobe.d/ndiswrapper

and did a re-install following the directions and NOW...i have this message "mrv8k51 driver present, hardware present" OH YEA!!!

except that for some reason now wlan0 is not showing up in iwconfig even after i modprobed ndiswrapper!!!


here is the output i get when I dmesg - anyone willing to help!!?!?

[4294696.536000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
[4294696.583000] ndiswrapper: driver mrv8k51 (D-Link,1/09/2004,2.3.0.1) loaded
[4294696.583000] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 19 (level, low) -> IRQ 209
[4294696.584000] ndiswrapper: using irq 209
[4294696.592000] ndiswrapper (miniport_init:240): couldn't initialize device: C0000001
[4294696.592000] ndiswrapper (pnp_start_device:479): Windows driver couldn't initialize the device (C0000001)
[4294696.592000] ndiswrapper (miniport_halt:271): device dfbc0260 is not initialized - not halting
[4294696.592000] ndiswrapper: device eth%d removed
[4294696.592000] unregister_netdevice: device eth%d/dfbc0000 never was registered
[4294696.592000] ACPI: PCI interrupt for device 0000:00:10.0 disabled
[4294696.592000] ndiswrapper: probe of 0000:00:10.0 failed with error -22

---

### Post by 0okami on 2006-08-17
same card, similar problems. Card present, drivers present, but no network. 

I installed ndiswrapper from source (latest version as of this date 8-17-2006 8:50am) I offer the following for review: 

ndiswrapper -l
```
ookami@localhost:/etc/network$ ndiswrapper -l
Installed drivers:
mrv8k51         driver installed, hardware present
ookami@localhost:/etc/network$

```


lspci -v
```

0000:01:06.0 Network controller: Broadcom Corporation BCM4303 802.11b Wireless L AN Controller (rev 02)
        Subsystem: Linksys: Unknown device 4301
        Flags: bus master, fast devsel, latency 32, IRQ 177
        Memory at e0020000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <available only to root>

	
0000:01:08.0 Ethernet controller: Marvell Technology Group Ltd. Marvell W8300 80 2.11 Adapter (rev 07)
        Subsystem: D-Link System Inc: Unknown device 3b09
        Flags: 66MHz, medium devsel, IRQ 217
        Memory at e0000000 (32-bit, non-prefetchable) [size=64K]
        Memory at e0010000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <available only to root>



```


sudo lshw -C network
```

ookami@localhost:~$ sudo lshw -C network
  *-network DISABLED
       description: Ethernet interface
       product: nForce2 Ethernet Controller
       vendor: nVidia Corporation
       physical id: 4
       bus info: pci@00:04.0
       logical name: eth0
       version: a1
       serial: 00:50:8d:fb:cf:dd
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=forcedeth driverversion=0.48 duplex=half link=yes multicast=yes port=MII speed=10MB/s
       resources: iomemory:e1084000-e1084fff ioport:b000-b007 irq:185
  *-network:0 DISABLED
       description: Wireless interface
       product: BCM4303 802.11b Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 6
       bus info: pci@01:06.0
       logical name: eth1
       version: 02
       serial: 00:06:25:1b:7c:e1
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.15-23-386 link=no multicast=yes wireless=IEEE 802.11b
       resources: iomemory:e0020000-e0021fff irq:177
  *-network:1 UNCLAIMED
       description: Ethernet controller
       product: Marvell W8300 802.11 Adapter
       vendor: Marvell Technology Group Ltd.
       physical id: 8
       bus info: pci@01:08.0
       version: 07
       width: 32 bits
       clock: 66MHz
       capabilities: cap_list
       resources: iomemory:e0000000-e000ffff iomemory:e0010000-e001ffff irq:217
ookami@localhost:~$

```


cardcrl ident:
```
ookami@localhost:~$ cardctl ident
no pcmcia driver in /proc/devices
ookami@localhost:~$

```


iwconfig
```
ookami@localhost:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:off/any  Nickname:"Broadcom 4301"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

ookami@localhost:~$

```

dmesg (short version):
```

[4294685.891000] saa7133[0]: registered device radio0
[4294686.524000] ACPI: PCI interrupt for device 0000:01:08.0 disabled
[4294686.524000] mrv8k: mrv8k_init_one: return -2
[4294686.524000] mrv8k: probe of 0000:01:08.0 failed with error -2
[4294686.547000] saa7134 ALSA driver for DMA sound loaded
[4294686.547000] saa7133[0]/alsa: saa7133[0] at 0xe0022000 irq 209 registered as card -1
[4294687.193000] lp: driver loaded but no devices found
[4294687.276000] Adding 2465936k swap on /dev/sda5.  Priority:-1 extents:1 across:2465936k
[4294687.612000] EXT3 FS on sda1, internal journal
[4294687.941000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294687.941000] md: bitmap version 4.39
[4294688.742000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[4294689.580000] cdrom: open failed.
[4294689.992000]   Vendor: SanDisk   Model: Cruzer Micro      Rev: 0.1 
[4294689.992000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[4294689.993000] SCSI device sdb: 4001760 512-byte hdwr sectors (2049 MB)
[4294689.994000] sdb: Write Protect is off
[4294689.994000] sdb: Mode Sense: 03 00 00 00
[4294689.994000] sdb: assuming drive cache: write through
[4294689.996000] SCSI device sdb: 4001760 512-byte hdwr sectors (2049 MB)
[4294689.997000] sdb: Write Protect is off
[4294689.997000] sdb: Mode Sense: 03 00 00 00
[4294689.997000] sdb: assuming drive cache: write through
[4294689.997000]  sdb: sdb1
[4294689.997000] sd 2:0:0:0: Attached scsi removable disk sdb
[4294689.997000] sd 2:0:0:0: Attached scsi generic sg1 type 0
[4294689.998000] usb-storage: device scan complete
[4294691.180000] ACPI: Power Button (FF) [PWRF]
[4294691.180000] ACPI: Power Button (CM) [PWRB]
[4294691.278000] ibm_acpi: ec object not found
[4294691.299000] pcc_acpi: loading...
[4294696.766000] ppdev: user-space parallel port driver
[4294697.058000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[4294697.058000] apm: overridden by ACPI.
[4294700.994000] Bluetooth: Core ver 2.8
[4294700.994000] NET: Registered protocol family 31
[4294700.994000] Bluetooth: HCI device and connection manager initialized
[4294700.994000] Bluetooth: HCI socket layer initialized
[4294701.031000] Bluetooth: L2CAP ver 2.8
[4294701.031000] Bluetooth: L2CAP socket layer initialized
[4294701.034000] Bluetooth: RFCOMM socket layer initialized
[4294701.034000] Bluetooth: RFCOMM TTY layer initialized
[4294701.034000] Bluetooth: RFCOMM ver 1.7
[4294713.653000] NET: Registered protocol family 10
[4294713.653000] lo: Disabled Privacy Extensions
[4294713.653000] IPv6 over IPv4 tunneling driver
[4294716.637000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[4294747.697000] ndiswrapper version 1.23 loaded (preempt=yes,smp=no)
[4294747.798000] ndiswrapper: driver mrv8k51 (D-Link,1/09/2004,2.3.0.1) loaded
[4294747.798000] ACPI: PCI Interrupt 0000:01:08.0[A] -> Link [APC1] -> GSI 16 (level, high) -> IRQ 217
[4294747.798000] ndiswrapper: using irq 217
[4294747.805000] ndiswrapper (miniport_init:264): couldn't initialize device: C0000001
[4294747.805000] ndiswrapper (pnp_start_device:428): Windows driver couldn't initialize the device (C0000001)
[4294747.805000] ndiswrapper (miniport_halt:327): device f754c260 is not initialized - not halting
[4294747.805000] ndiswrapper: device eth%d removed
[4294747.805000] unregister_netdevice: device eth%d/f754c000 never was registered
[4294747.805000] ACPI: PCI interrupt for device 0000:01:08.0 disabled
[4294747.805000] ndiswrapper: probe of 0000:01:08.0 failed with error -22

```

:confused: :confused: :confused: 

OK! i found a solution: 
:KS [http://ubuntuforums.org/showpost.php?p=1389774&postcount=11](http://ubuntuforums.org/showpost.php?p=1389774&postcount=11)
:KS [http://ubuntuforums.org/showthread.php?t=190967](http://ubuntuforums.org/showthread.php?t=190967)
Worked for me.... 

is there anything we can try to get this card working under dapper?

---

