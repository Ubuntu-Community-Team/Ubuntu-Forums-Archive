---
title: "Netgear N600 WNDA3100 USB Wireless Adaptor Issues"
date: 2012-09-03
forum: Networking &amp; Wireless
---

### Post by scjohnson on 2012-09-03
Hello all,

I just purchased the Netgear WNDA3100 adaptor and used ndiswrapper to pull in the bcmwlhigh5.inf windows driver. It looks like I'm almost there, but I can't tell why it's not working.

```
$ lsusb
Bus 001 Device 003: ID 0846:9011 NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323]
```

and 

```
$ ndiswrapper -l
bcmn43xx64 : driver installed
	device (0846:9011) present
```

look good. But if

```
$ iwconfig 
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Wireless-N(2.4G)"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:E0:4C:81:96:D1   
          Bit Rate=9 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=41/70  Signal level=-69 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:301  Invalid misc:182   Missed beacon:0

eth0      no wireless extensions.

```

shows my old wireless (wlan0). I've been having issues with the onboard wireless card which is why I bought the new one. Any thoughts on why I'm not seeing a wlan1?

Thanks so much for the help!

---

### Post by chili555 on 2012-09-03
I suggest you blacklist the driver for the built-in, reboot and try again. I'd also check the message files:```
dmesg | grep ndis
```This is tricky to get going in 64-bit.

---

### Post by scjohnson on 2012-09-03
Thanks for the note. In the meantime, I determined the ndiswrapper didn't seem to be loaded in the kernel, so I did the kernel dance:


```
apt-get install ndiswrapper-source
cd /usr/src
m-a prepare
m-a a-i ndiswrapper
modprobe ndiswrapper
```

and now I see the wlan1 in iwconfig. All seems to be working.

Sorry to come back with an answer to my own question, but thought I'd post it here for others to learn from my stupidities.

---

### Post by notquitestr8t on 2012-09-09
I am in the same boat trying to load this on 12.4  64 bit. I followed your instructions but cannot see anything.Any other ideas? See my output below:

$ lsusb
Bus 001 Device 003: ID 0846:9011 NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323]

$ ndiswrapper -l
bcmwlhigh6 : driver installed
	device (0846:9011) present

$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

Lots of "unknown symbol" messages. This is a partial view.

$ dmesg | grep ndis

[   90.960656] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionUnbind'
[   90.960658] ndiswrapper (load_sys_files:199): couldn't prepare driver 'bcmwlhigh6'
[   90.960715] ndiswrapper (load_wrap_driver:121): couldn't load driver 'bcmwlhigh6'
[   90.960743] usbcore: registered new interface driver ndiswrapper

---

### Post by chili555 on 2012-09-09
Getting this working for 64-bit is tricky. I suggest you erase the bcmwlhigh6 you have now and try bcmn43x[COLOR="Red"]x64[/COLOR].inf in the package I attached. Post back if you need additional guidance.

If there are any problems, please let us see the relevant dmesg logs again.

---

### Post by notquitestr8t on 2012-09-09
I did some more digging as was able to get this to work.I pulled a driver from another post which worked while the windows driver did not. It is attached if anyone else needs to use it.(Thank you Chili555) The original post is below.

[http://ubuntuforums.org/showthread.php?t=1964173&highlight=wnda3100](http://ubuntuforums.org/showthread.php?t=1964173&highlight=wnda3100)

---

### Post by Alaric on 2013-04-18
Good sirs, you are as Gods among men.   chili555's drivers worked perfectly on my Ubuntu x64 12.04 installation for my 

0846:9011 NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323]

After installing the ndisgtk and dkms-ndiswrapper packages through apt-get.  Thank you for your time and effort.

---

### Post by TorrentGuru on 2013-09-25
Mr chili555:
Thank you for the 64-bit driver.

Works on kali linux (3.7-trunk-amd64-gnome3.4.2) hosted on VMWare Fusion 4.1.3 (OSX 10.8)
Recomplied ndiswrapper from source to 1.58 and bam! iwconfig shows wlan0!!!!

Now I finnaly have WiFi on my 64-bit distros....Thank you again!

---

### Post by chili555 on 2013-09-25
Awesome! Glad it's working!

---

### Post by patrice.brouillet on 2013-12-04
Hi i also have a n600 usb adapter. the driver are install but the ndiswrapper does not reconize the hardware. How do i fix this? I am runing 12.04 lts

---

### Post by chili555 on 2013-12-04
> **patrice.brouillet said:**
> Hi i also have a n600 usb adapter. the driver are install but the ndiswrapper does not reconize the hardware. How do i fix this? I am runing 12.04 ltsPlease run and post:```
lsusb
ndiswrapper -l
dmesg | grep ndis
```

---

### Post by patrice.brouillet on 2013-12-04
this is the answer:
[    0.328971] pci 0000:00:1c.1:   bridge window [mem 0xd8000000-0xd9ffffff]
[    0.328978] pci 0000:00:1c.1:   bridge window [mem 0xd2000000-0xd3ffffff 64bit pref]
[    0.328988] pci 0000:00:1c.2: PCI bridge to [bus 05-06]
[    0.328992] pci 0000:00:1c.2:   bridge window [io  0x3000-0x3fff]
[    0.329001] pci 0000:00:1c.2:   bridge window [mem 0xda000000-0xdbffffff]
[    0.329007] pci 0000:00:1c.2:   bridge window [mem 0xd4000000-0xd5ffffff 64bit pref]
[    0.329020] pci 0000:07:06.0: res[15]=[mem 0x04000000-0x03ffffff pref] get_res_add_size add_size 4000000
[    0.329024] pci 0000:07:06.0: res[16]=[mem 0x04000000-0x03ffffff] get_res_add_size add_size 4000000
[    0.329028] pci 0000:07:06.0: res[13]=[io  0x0100-0x00ff] get_res_add_size add_size 100
[    0.329031] pci 0000:07:06.0: res[14]=[io  0x0100-0x00ff] get_res_add_size add_size 100
[    0.329036] pci 0000:07:06.0: BAR 0: assigned [mem 0x48000000-0x48000fff]
[    0.329044] pci 0000:07:06.0: BAR 15: assigned [mem 0x40000000-0x43ffffff pref]
[    0.329049] pci 0000:07:06.0: BAR 16: assigned [mem 0x4c000000-0x4fffffff]
[    0.329053] pci 0000:07:06.0: BAR 13: assigned [io  0x4400-0x44ff]
[    0.329057] pci 0000:07:06.0: BAR 14: assigned [io  0x4800-0x48ff]
[    0.329061] pci 0000:07:06.0: CardBus bridge to [bus 08-0b]
[    0.329064] pci 0000:07:06.0:   bridge window [io  0x4400-0x44ff]
[    0.329070] pci 0000:07:06.0:   bridge window [io  0x4800-0x48ff]
[    0.329077] pci 0000:07:06.0:   bridge window [mem 0x40000000-0x43ffffff pref]
[    0.329084] pci 0000:07:06.0:   bridge window [mem 0x4c000000-0x4fffffff]
[    0.329091] pci 0000:00:1e.0: PCI bridge to [bus 07]
[    0.329096] pci 0000:00:1e.0:   bridge window [io  0x4000-0x4fff]
[    0.329104] pci 0000:00:1e.0:   bridge window [mem 0xdc000000-0xdc0fffff]
[    0.329110] pci 0000:00:1e.0:   bridge window [mem 0x40000000-0x43ffffff pref]
[    0.329163] pci 0000:00:1e.0: setting latency timer to 64
[    0.329173] pci 0000:07:06.0: enabling device (0000 -> 0003)
[    0.329186] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
[    0.329189] pci_bus 0000:00: resource 5 [mem 0x00000000-0xffffffff]
[    0.329193] pci_bus 0000:02: resource 0 [io  0x5000-0x5fff]
[    0.329196] pci_bus 0000:02: resource 1 [mem 0x44000000-0x441fffff]
[    0.329199] pci_bus 0000:02: resource 2 [mem 0x44200000-0x443fffff 64bit pref]
[    0.329203] pci_bus 0000:03: resource 0 [io  0x2000-0x2fff]
[    0.329206] pci_bus 0000:03: resource 1 [mem 0xd8000000-0xd9ffffff]
[    0.329210] pci_bus 0000:03: resource 2 [mem 0xd2000000-0xd3ffffff 64bit pref]
[    0.329213] pci_bus 0000:05: resource 0 [io  0x3000-0x3fff]
[    0.329216] pci_bus 0000:05: resource 1 [mem 0xda000000-0xdbffffff]
[    0.329220] pci_bus 0000:05: resource 2 [mem 0xd4000000-0xd5ffffff 64bit pref]
[    0.329223] pci_bus 0000:07: resource 0 [io  0x4000-0x4fff]
[    0.329226] pci_bus 0000:07: resource 1 [mem 0xdc000000-0xdc0fffff]
[    0.329230] pci_bus 0000:07: resource 2 [mem 0x40000000-0x43ffffff pref]
[    0.329233] pci_bus 0000:07: resource 4 [io  0x0000-0xffff]
[    0.329236] pci_bus 0000:07: resource 5 [mem 0x00000000-0xffffffff]
[    0.329240] pci_bus 0000:08: resource 0 [io  0x4400-0x44ff]
[    0.329243] pci_bus 0000:08: resource 1 [io  0x4800-0x48ff]
[    0.329246] pci_bus 0000:08: resource 2 [mem 0x40000000-0x43ffffff pref]
[    0.329250] pci_bus 0000:08: resource 3 [mem 0x4c000000-0x4fffffff]
[    0.329298] NET: Registered protocol family 2
[    0.329505] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[    0.329554] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.329601] TCP: Hash tables configured (established 8192 bind 8192)
[    0.329639] TCP: reno registered
[    0.329643] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.329656] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.329728] NET: Registered protocol family 1
[    0.329747] pci 0000:00:02.0: Boot video device
[    0.329935] PCI: CLS mismatch (64 != 16), using 64 bytes
[    0.329954] pci 0000:07:08.0: Firmware left e100 interrupts enabled; disabling
[    0.330016] Trying to unpack rootfs image as initramfs...
[    0.748266] Freeing initrd memory: 15664k freed
[    0.759010] Simple Boot Flag at 0x36 set to 0x1
[    0.759335] Initialise module verification
[    0.759396] audit: initializing netlink socket (disabled)
[    0.759415] type=2000 audit(1386204396.756:1): initialized
[    0.789799] bounce pool size: 64 pages
[    0.789814] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.791920] VFS: Disk quotas dquot_6.5.2
[    0.791987] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.792762] fuse init (API version 7.20)
[    0.792868] msgmni has been set to 1739
[    0.793284] Key type asymmetric registered
[    0.793287] Asymmetric key parser 'x509' registered
[    0.793340] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.793375] io scheduler noop registered
[    0.793378] io scheduler deadline registered (default)
[    0.793386] io scheduler cfq registered
[    0.793606] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.793761] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    0.793909] pcieport 0000:00:1c.2: irq 42 for MSI/MSI-X
[    0.794026] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.794049] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.794141] intel_idle: does not run on family 6 model 14
[    0.794747] ACPI: AC Adapter [ADP0] (on-line)
[    0.794841] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.794868] ACPI: Lid Switch [LID]
[    0.794920] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.794926] ACPI: Power Button [PWRB]
[    0.794988] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.794992] ACPI: Power Button [PWRF]
[    0.795077] ACPI: Fan [FAN0] (off)
[    0.795142] ACPI: Requesting acpi_cpufreq
[    0.795652] tsc: Marking TSC unstable due to TSC halts in idle
[    0.795692] ACPI: acpi_idle registered with cpuidle
[    0.940384] thermal LNXTHERM:00: registered as thermal_zone0
[    0.940387] ACPI: Thermal Zone [TZ00] (61 C)
[    0.954626] thermal LNXTHERM:01: registered as thermal_zone1
[    0.954629] ACPI: Thermal Zone [TZ01] (57 C)
[    0.954723] GHES: HEST is not enabled!
[    0.954977] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.958183] ACPI: Battery Slot [BAT0] (battery present)
[    0.958217] isapnp: Scanning for PnP cards...
[    0.964556] Linux agpgart interface v0.103
[    0.964638] agpgart-intel 0000:00:00.0: Intel 945GM Chipset
[    0.964698] agpgart-intel 0000:00:00.0: detected gtt size: 262144K total, 262144K mappable
[    0.965036] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    0.965183] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[    1.010593] brd: module loaded
[    1.011544] loop: module loaded
[    1.011724] ata_piix 0000:00:1f.2: version 2.13
[    1.011743] ata_piix 0000:00:1f.2: MAP [
[    1.011746]  P0 P2 IDE IDE ]
[    1.185989] ata_piix 0000:00:1f.2: setting latency timer to 64
[    1.229884] scsi0 : ata_piix
[    1.230296] scsi1 : ata_piix
[    1.230660] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x18b0 irq 14
[    1.230663] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x18b8 irq 15
[    1.231179] libphy: Fixed MDIO Bus: probed
[    1.231281] tun: Universal TUN/TAP device driver, 1.6
[    1.231284] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.231334] PPP generic driver version 2.4.2
[    1.231390] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.231392] ehci-pci: EHCI PCI platform driver
[    1.231428] ehci-pci 0000:00:1d.7: setting latency timer to 64
[    1.231433] ehci-pci 0000:00:1d.7: EHCI Host Controller
[    1.231442] ehci-pci 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    1.231462] ehci-pci 0000:00:1d.7: debug port 1
[    1.235361] ehci-pci 0000:00:1d.7: cache line size of 64 is not supported
[    1.235389] ehci-pci 0000:00:1d.7: irq 23, io mem 0xdc444000
[    1.278955] ehci-pci 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.279016] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.279020] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.279023] usb usb1: Product: EHCI Host Controller
[    1.279026] usb usb1: Manufacturer: Linux 3.8.0-34-generic ehci_hcd
[    1.279029] usb usb1: SerialNumber: 0000:00:1d.7
[    1.279161] hub 1-0:1.0: USB hub found
[    1.279168] hub 1-0:1.0: 8 ports detected
[    1.279487] ehci-platform: EHCI generic platform driver
[    1.279498] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.279523] uhci_hcd: USB Universal Host Controller Interface driver
[    1.279548] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.279552] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.279559] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.279587] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001820
[    1.279629] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    1.279633] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.279636] usb usb2: Product: UHCI Host Controller
[    1.279639] usb usb2: Manufacturer: Linux 3.8.0-34-generic uhci_hcd
[    1.279642] usb usb2: SerialNumber: 0000:00:1d.0
[    1.279771] hub 2-0:1.0: USB hub found
[    1.279778] hub 2-0:1.0: 2 ports detected
[    1.279899] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.279904] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.279910] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.279954] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
[    1.280015] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    1.280019] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.280022] usb usb3: Product: UHCI Host Controller
[    1.280025] usb usb3: Manufacturer: Linux 3.8.0-34-generic uhci_hcd
[    1.280028] usb usb3: SerialNumber: 0000:00:1d.1
[    1.280146] hub 3-0:1.0: USB hub found
[    1.280152] hub 3-0:1.0: 2 ports detected
[    1.280276] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.280281] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.280288] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.280329] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[    1.280371] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    1.280375] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.280378] usb usb4: Product: UHCI Host Controller
[    1.280381] usb usb4: Manufacturer: Linux 3.8.0-34-generic uhci_hcd
[    1.280384] usb usb4: SerialNumber: 0000:00:1d.2
[    1.280500] hub 4-0:1.0: USB hub found
[    1.280506] hub 4-0:1.0: 2 ports detected
[    1.280622] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    1.280627] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    1.280634] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    1.280675] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001880
[    1.280719] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    1.280722] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.280725] usb usb5: Product: UHCI Host Controller
[    1.280729] usb usb5: Manufacturer: Linux 3.8.0-34-generic uhci_hcd
[    1.280732] usb usb5: SerialNumber: 0000:00:1d.3
[    1.280849] hub 5-0:1.0: USB hub found
[    1.280855] hub 5-0:1.0: 2 ports detected
[    1.281049] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.326304] isapnp: No Plug & Play device found
[    1.326993] i8042: Detected active multiplexing controller, rev 1.1
[    1.328810] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.328818] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.328854] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.328882] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.328910] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.329036] mousedev: PS/2 mouse device common for all mice
[    1.329219] rtc_cmos 00:06: RTC can wake from S4
[    1.329382] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    1.329418] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.329543] device-mapper: uevent: version 1.0.3
[    1.329617] device-mapper: ioctl: 4.23.1-ioctl (2012-12-18) initialised: [email]dm-devel@redhat.com[/email]
[    1.329639] EISA: Probing bus 0 at eisa.0
[    1.329649] Cannot allocate resource for EISA slot 1
[    1.329651] Cannot allocate resource for EISA slot 2
[    1.329654] Cannot allocate resource for EISA slot 3
[    1.329656] Cannot allocate resource for EISA slot 4
[    1.329658] Cannot allocate resource for EISA slot 5
[    1.329673] EISA: Detected 0 cards.
[    1.329684] cpufreq-nforce2: No nForce2 chipset.
[    1.329711] cpuidle: using governor ladder
[    1.329741] cpuidle: using governor menu
[    1.329746] ledtrig-cpu: registered to indicate activity on CPUs
[    1.329749] EFI Variables Facility v0.08 2004-May-17
[    1.329947] ashmem: initialized
[    1.330108] TCP: cubic registered
[    1.330254] NET: Registered protocol family 10
[    1.330510] NET: Registered protocol family 17
[    1.330523] Key type dns_resolver registered
[    1.330715] Using IPI No-Shortcut mode
[    1.330811] Loading module verification certificates
[    1.336991] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: 6d5f3b29dd810bffe7dee4744355192d09ca4755'
[    1.337009] registered taskstats version 1
[    1.339567] Key type trusted registered
[    1.341713] Key type encrypted registered
[    1.344355] rtc_cmos 00:06: setting system clock to 2013-12-05 00:46:38 UTC (1386204398)
[    1.344576] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.344578] EDD information not available.
[    1.362647] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.392581] ata1.00: ATA-7: HTS541080G9SA00, MB4OC60R, max UDMA/100
[    1.392591] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.396605] ata2.00: ATAPI: MATSHITADVD-RAM UJ-841S, 1.60, max UDMA/33
[    1.408543] ata1.00: configured for UDMA/100
[    1.408817] scsi 0:0:0:0: Direct-Access     ATA      HTS541080G9SA00  MB4O PQ: 0 ANSI: 5
[    1.409238] sd 0:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    1.409313] sd 0:0:0:0: [sda] Write Protect is off
[    1.409317] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.409350] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.409735] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.412526] ata2.00: configured for UDMA/33
[    1.414789] scsi 1:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-841S  1.60 PQ: 0 ANSI: 5
[    1.416472] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.416479] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.416714] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.416839] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.483251]  sda: sda1 sda2 < sda5 >
[    1.483609] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.483672] Freeing unused kernel memory: 796k freed
[    1.484060] Write protecting the kernel text: 6364k
[    1.484127] Write protecting the kernel read-only data: 2496k
[    1.484128] NX-protecting the kernel data: 3876k
[    1.503796] udevd[95]: starting version 175
[    1.596071] usb 1-3: new high-speed USB device number 2 using ehci-pci
[    1.730816] usb 1-3: New USB device found, idVendor=0846, idProduct=9011
[    1.730823] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.730826] usb 1-3: Product: Remote Download Wireless Adapter
[    1.730830] usb 1-3: Manufacturer: Broadcom
[    1.730832] usb 1-3: SerialNumber: 0
[    1.739091] Disabling lock debugging due to kernel taint
[    1.739424] sdhci: Secure Digital Host Controller Interface driver
[    1.739426] sdhci: Copyright(c) Pierre Ossman
[    1.739731] sdhci-pci 0000:07:06.3: SDHCI controller found [104c:803c] (rev 0)
[    1.739784] mmc0: no vqmmc regulator found
[    1.739786] mmc0: no vmmc regulator found
[    1.743142] e100: Intel(R) PRO/100 Network Driver, 3.5.24-k2-NAPI
[    1.743146] e100: Copyright(c) 1999-2006 Intel Corporation
[    1.775132] mmc0: SDHCI controller on PCI [0000:07:06.3] using DMA
[    1.809655] e100 0000:07:08.0 eth0: addr 0xdc005000, irq 20, MAC addr 00:a0:d1:51:48:0d
[    1.864168] firewire_ohci 0000:07:06.1: added OHCI v1.10 device as card 0, 4 IR + 8 IT contexts, quirks 0x2
[    2.127002] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    2.364235] firewire_core 0000:07:06.1: created device fw0: GUID 00080da0d151480d, S400
[    3.577345] init: ureadahead main process (264) terminated with status 5
[    4.694003] Adding 1037308k swap on /dev/sda5.  Priority:-1 extents:1 across:1037308k 
[    5.770205] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    6.034275] udevd[339]: starting version 175
[    6.983570] lp: driver loaded but no devices found
[    7.173613] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[    7.515606] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    7.515875] acpi device:07: registered as cooling_device2
[    7.515902] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    7.516060] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input4
[    7.704483] intel_rng: FWH not detected
[    8.001983] ACPI Warning: 0x00001028-0x0000102f SystemIO conflicts with Region \PMIO 1 (20121018/utaddress-251)
[    8.001996] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    8.002001] ACPI Warning: 0x000011b0-0x000011bf SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
[    8.002006] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    8.002009] ACPI Warning: 0x00001180-0x000011af SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
[    8.002013] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    8.002016] lpc_ich: Resource conflict(s) found affecting gpio_ich
[    8.247630] leds_ss4200: no LED devices found
[    8.365615] cfg80211: Calling CRDA to update world regulatory domain
[    8.466862] microcode: CPU0 sig=0x6e8, pf=0x20, revision=0x39
[    8.733716] [drm] Initialized drm 1.1.0 20060810
[    8.787877] yenta_cardbus 0000:07:06.0: CardBus bridge found [1179:ff10]
[    8.787902] yenta_cardbus 0000:07:06.0: Enabling burst memory read transactions
[    8.787908] yenta_cardbus 0000:07:06.0: Using CSCINT to route CSC interrupts to PCI
[    8.787911] yenta_cardbus 0000:07:06.0: Routing CardBus interrupts to PCI
[    8.787919] yenta_cardbus 0000:07:06.0: TI: mfunc 0x01a01b22, devctl 0x66
[    9.016881] yenta_cardbus 0000:07:06.0: ISA IRQ mask 0x0cf8, PCI irq 18
[    9.016889] yenta_cardbus 0000:07:06.0: Socket status: 30000006
[    9.016895] pci_bus 0000:07: Raising subordinate bus# of parent bus (#07) from #07 to #0b
[    9.016907] yenta_cardbus 0000:07:06.0: pcmcia: parent PCI bridge window: [io  0x4000-0x4fff]
[    9.016911] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x4000-0x4fff:
[    9.018432]  excluding 0x4000-0x403f 0x4400-0x44ff 0x4800-0x48ff
[    9.023754] yenta_cardbus 0000:07:06.0: pcmcia: parent PCI bridge window: [mem 0xdc000000-0xdc0fffff]
[    9.023759] pcmcia_socket pcmcia_socket0: cs: memory probe 0xdc000000-0xdc0fffff:
[    9.023762]  excluding 0xdc000000-0xdc00ffff
[    9.023775] yenta_cardbus 0000:07:06.0: pcmcia: parent PCI bridge window: [mem 0x40000000-0x43ffffff pref]
[    9.023779] pcmcia_socket pcmcia_socket0: cs: memory probe 0x40000000-0x43ffffff:
[    9.023791]  excluding 0x40000000-0x43ffffff
[    9.236610] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    9.296298] psmouse serio4: synaptics: Touchpad model: 1, fw: 6.2, id: 0x25a0b1, caps: 0xa04713/0x0/0x0, board id: 3655, fw id: 53323
[    9.296315] psmouse serio4: synaptics: Toshiba Satellite A100 detected, limiting rate to 40pps.
[    9.330440] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input5
[    9.413153] i915 0000:00:02.0: setting latency timer to 64
[    9.419948] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    9.419953] [drm] Driver supports precise vblank timestamp query.
[    9.420149] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    9.499217] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af:
[    9.500397]  excluding 0x170-0x177 0x1f0-0x1f7 0x370-0x377
[    9.501233] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff:
[    9.501639]  excluding 0x3f0-0x3f7 0x400-0x407 0x4d0-0x4d7
[    9.502025] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff:
[    9.502674]  clean.
[    9.502694] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7:
[    9.503410]  clean.
[    9.503433] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff:
[    9.503438]  excluding 0xc0000-0xc7fff 0xcc000-0xcffff 0xdc000-0xfffff
[    9.503470] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff:
[    9.503488]  clean.
[    9.503507] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff:
[    9.503524]  clean.
[    9.503544] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff:
[    9.504304]  clean.
[    9.578615] [drm] initialized overlay support
[    9.755457] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[    9.755463] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[    9.813949] iwl3945 0000:05:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[    9.813956] iwl3945 0000:05:00.0: Detected Intel Wireless WiFi Link 3945ABG
[    9.814115] iwl3945 0000:05:00.0: irq 43 for MSI/MSI-X
[   10.015802] fbcon: inteldrmfb (fb0) is primary device
[   10.104067] i915: fixme: max PWM is zero
[   10.104248] Console: switching to colour frame buffer device 160x50
[   10.109852] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   10.109855] i915 0000:00:02.0: registered panic notifier
[   10.109867] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   10.167013] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   10.319642] snd_hda_intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[   12.143070] type=1400 audit(1386204409.295:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=639 comm="apparmor_parser"
[   12.143647] type=1400 audit(1386204409.295:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=639 comm="apparmor_parser"
[   12.143979] type=1400 audit(1386204409.295:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=639 comm="apparmor_parser"
[   12.144239] type=1400 audit(1386204409.295:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=651 comm="apparmor_parser"
[   12.144807] type=1400 audit(1386204409.295:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=651 comm="apparmor_parser"
[   12.145140] type=1400 audit(1386204409.295:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=651 comm="apparmor_parser"
[   12.145760] type=1400 audit(1386204409.295:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=721 comm="apparmor_parser"
[   12.146322] type=1400 audit(1386204409.295:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=721 comm="apparmor_parser"
[   12.146650] type=1400 audit(1386204409.295:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=721 comm="apparmor_parser"
[   13.064888] init: failsafe main process (742) killed by TERM signal
[   15.137366] ppdev: user-space parallel port driver
[   15.802510] Bluetooth: Core ver 2.16
[   15.802583] NET: Registered protocol family 31
[   15.802585] Bluetooth: HCI device and connection manager initialized
[   15.802597] Bluetooth: HCI socket layer initialized
[   15.802600] Bluetooth: L2CAP socket layer initialized
[   15.802608] Bluetooth: SCO socket layer initialized
[   15.954920] Bluetooth: RFCOMM TTY layer initialized
[   15.954937] Bluetooth: RFCOMM socket layer initialized
[   15.954940] Bluetooth: RFCOMM ver 1.11
[   16.164260] type=1400 audit(1386204413.315:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=829 comm="apparmor_parser"
[   16.193736] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.193739] Bluetooth: BNEP filters: protocol multicast
[   16.193751] Bluetooth: BNEP socket layer initialized
[   19.610154] iwl3945 0000:05:00.0: loaded firmware version 15.32.2.9
[   19.621057] audit_printk_skb: 3 callbacks suppressed
[   19.621061] type=1400 audit(1386204416.771:13): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=900 comm="apparmor_parser"
[   19.621544] type=1400 audit(1386204416.771:14): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=900 comm="apparmor_parser"
[   19.625362] type=1400 audit(1386204416.775:15): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=901 comm="apparmor_parser"
[   19.625957] type=1400 audit(1386204416.775:16): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=901 comm="apparmor_parser"
[   19.626291] type=1400 audit(1386204416.775:17): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=901 comm="apparmor_parser"
[   19.681979] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.682398] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.705922] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.706444] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.142124] type=1400 audit(1386204417.291:18): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=902 comm="apparmor_parser"
[   20.154746] type=1400 audit(1386204417.303:19): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince//launchpad_integration" pid=902 comm="apparmor_parser"
[   20.156480] type=1400 audit(1386204417.307:20): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince//sanitized_helper" pid=902 comm="apparmor_parser"
[   20.157846] type=1400 audit(1386204417.307:21): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=902 comm="apparmor_parser"
[   20.162160] type=1400 audit(1386204417.311:22): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer//launchpad_integration" pid=902 comm="apparmor_parser"
[   25.491386] wlan0: authenticate with 4c:60:de:26:80:78
[   25.493583] wlan0: send auth to 4c:60:de:26:80:78 (try 1/3)
[   25.495842] wlan0: authenticated
[   25.500017] wlan0: associate with 4c:60:de:26:80:78 (try 1/3)
[   25.502773] wlan0: RX AssocResp from 4c:60:de:26:80:78 (capab=0x411 status=0 aid=4)
[   25.504304] wlan0: associated
[   25.504352] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   64.463485] ISO 9660 Extensions: Microsoft Joliet Level 3
[   64.568216] ISO 9660 Extensions: RRIP_1991A
[   71.463859] usb 1-3: USB disconnect, device number 2
[   75.000056] usb 1-4: new high-speed USB device number 3 using ehci-pci
[   75.135562] usb 1-4: New USB device found, idVendor=0846, idProduct=9011
[   75.135576] usb 1-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[   75.135584] usb 1-4: Product: Remote Download Wireless Adapter
[   75.135591] usb 1-4: Manufacturer: Broadcom
[   75.135598] usb 1-4: SerialNumber: 0
[   75.760897] usb 1-4: USB disconnect, device number 3
[   77.120060] usb 1-3: new high-speed USB device number 4 using ehci-pci
[   77.255394] usb 1-3: New USB device found, idVendor=0846, idProduct=9011
[   77.255404] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[   77.255412] usb 1-3: Product: Remote Download Wireless Adapter
[   77.255419] usb 1-3: Manufacturer: Broadcom
[   77.255426] usb 1-3: SerialNumber: 0

---

### Post by patrice.brouillet on 2013-12-04
lsusb:
pat@pat-Satellite-A100:~$ lsusb
Bus 001 Device 004: ID 0846:9011 NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by patrice.brouillet on 2013-12-04
ndiswrapper -l
bcmn43xx32 : driver installed
bcmwlhigh6 : driver installed

---

### Post by chili555 on 2013-12-05
You seem to have two inf files installed. One, I believe is for 64-bit and one 32-bit. Which do you have?```
arch
```Moreover, you seem to have a perfectly operating Intel 3945 that connects. 

Would you care to tell us why you don't want the perfect Intel in favor of a tricky ndiswrapper device? Do you love pain?

---

### Post by patrice.brouillet on 2013-12-07
pat@pat-Satellite-A100:~$ arch
i686
lol i am using a netgear wireless adapter because the built-in card is 54 kb/s card.

---

### Post by patrice.brouillet on 2013-12-07
wich one should i remove ? 
bcmn43xx32 or the bcmwlhigh6

---

### Post by chili555 on 2013-12-07
>  i am using a netgear wireless adapter because the built-in card is 54 kb/s card. If you get N speeds out of an ndiswrapper device, I will fall off my chair in amazement! However, let's give it the best try we can. First, I suggest you blacklist and unload the built-in driver:```
sudo -i
echo "blacklist iwl3945"  >>  /etc/modprobe.d/blacklist.conf
modprobe -r iwl3945
```Now, let's remove the one inf file I have *never* seen work:```
ndiswrapper -e  bcmwlhigh6
exit
```Now reboot and show us:```
iwconfig
dmesg | grep ndis
```Thanks.

---

### Post by patrice.brouillet on 2013-12-07
pat@pat-Satellite-A100:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

[    0.376271] pnp: PnP ACPI: found 9 devices
[    0.376277] ACPI: ACPI bus type pnp unregistered
[    0.376286] PnPBIOS: Disabled by ACPI PNP
[    0.415664] pci 0000:00:1c.0: bridge window [io  0x1000-0x0fff] to [bus 02] add_size 1000
[    0.415678] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 02] add_size 200000
[    0.415689] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff] to [bus 02] add_size 200000
[    0.415756] pci 0000:07:06.0: res[15]=[mem 0x04000000-0x03ffffff pref] get_res_add_size add_size 4000000
[    0.415767] pci 0000:00:1e.0: bridge window [mem 0x04000000-0x03ffffff pref] to [bus 07] add_size 4000000
[    0.415786] pci 0000:00:1e.0: res[15]=[mem 0x04000000-0x03ffffff pref] get_res_add_size add_size 4000000
[    0.415795] pci 0000:00:1c.0: res[14]=[mem 0x00100000-0x000fffff] get_res_add_size add_size 200000
[    0.415804] pci 0000:00:1c.0: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.415813] pci 0000:00:1c.0: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.415829] pci 0000:00:1e.0: BAR 15: assigned [mem 0x40000000-0x43ffffff pref]
[    0.415839] pci 0000:00:1c.0: BAR 14: assigned [mem 0x44000000-0x441fffff]
[    0.415850] pci 0000:00:1c.0: BAR 15: assigned [mem 0x44200000-0x443fffff 64bit pref]
[    0.415863] pci 0000:00:1c.0: BAR 13: assigned [io  0x5000-0x5fff]
[    0.415872] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.415882] pci 0000:00:1c.0:   bridge window [io  0x5000-0x5fff]
[    0.415897] pci 0000:00:1c.0:   bridge window [mem 0x44000000-0x441fffff]
[    0.415909] pci 0000:00:1c.0:   bridge window [mem 0x44200000-0x443fffff 64bit pref]
[    0.415926] pci 0000:00:1c.1: PCI bridge to [bus 03-04]
[    0.415935] pci 0000:00:1c.1:   bridge window [io  0x2000-0x2fff]
[    0.415949] pci 0000:00:1c.1:   bridge window [mem 0xd8000000-0xd9ffffff]
[    0.415962] pci 0000:00:1c.1:   bridge window [mem 0xd2000000-0xd3ffffff 64bit pref]
[    0.415978] pci 0000:00:1c.2: PCI bridge to [bus 05-06]
[    0.415988] pci 0000:00:1c.2:   bridge window [io  0x3000-0x3fff]
[    0.416024] pci 0000:00:1c.2:   bridge window [mem 0xda000000-0xdbffffff]
[    0.416037] pci 0000:00:1c.2:   bridge window [mem 0xd4000000-0xd5ffffff 64bit pref]
[    0.416061] pci 0000:07:06.0: res[15]=[mem 0x04000000-0x03ffffff pref] get_res_add_size add_size 4000000
[    0.416070] pci 0000:07:06.0: res[16]=[mem 0x04000000-0x03ffffff] get_res_add_size add_size 4000000
[    0.416078] pci 0000:07:06.0: res[13]=[io  0x0100-0x00ff] get_res_add_size add_size 100
[    0.416087] pci 0000:07:06.0: res[14]=[io  0x0100-0x00ff] get_res_add_size add_size 100
[    0.416099] pci 0000:07:06.0: BAR 0: assigned [mem 0x48000000-0x48000fff]
[    0.416114] pci 0000:07:06.0: BAR 15: assigned [mem 0x40000000-0x43ffffff pref]
[    0.416126] pci 0000:07:06.0: BAR 16: assigned [mem 0x4c000000-0x4fffffff]
[    0.416135] pci 0000:07:06.0: BAR 13: assigned [io  0x4400-0x44ff]
[    0.416143] pci 0000:07:06.0: BAR 14: assigned [io  0x4800-0x48ff]
[    0.416152] pci 0000:07:06.0: CardBus bridge to [bus 08-0b]
[    0.416160] pci 0000:07:06.0:   bridge window [io  0x4400-0x44ff]
[    0.416172] pci 0000:07:06.0:   bridge window [io  0x4800-0x48ff]
[    0.416184] pci 0000:07:06.0:   bridge window [mem 0x40000000-0x43ffffff pref]
[    0.416196] pci 0000:07:06.0:   bridge window [mem 0x4c000000-0x4fffffff]
[    0.416208] pci 0000:00:1e.0: PCI bridge to [bus 07]
[    0.416218] pci 0000:00:1e.0:   bridge window [io  0x4000-0x4fff]
[    0.416232] pci 0000:00:1e.0:   bridge window [mem 0xdc000000-0xdc0fffff]
[    0.416244] pci 0000:00:1e.0:   bridge window [mem 0x40000000-0x43ffffff pref]
[    0.416334] pci 0000:00:1e.0: setting latency timer to 64
[    0.416350] pci 0000:07:06.0: enabling device (0000 -> 0003)
[    0.416371] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
[    0.416379] pci_bus 0000:00: resource 5 [mem 0x00000000-0xffffffff]
[    0.416387] pci_bus 0000:02: resource 0 [io  0x5000-0x5fff]
[    0.416394] pci_bus 0000:02: resource 1 [mem 0x44000000-0x441fffff]
[    0.416403] pci_bus 0000:02: resource 2 [mem 0x44200000-0x443fffff 64bit pref]
[    0.416410] pci_bus 0000:03: resource 0 [io  0x2000-0x2fff]
[    0.416418] pci_bus 0000:03: resource 1 [mem 0xd8000000-0xd9ffffff]
[    0.416426] pci_bus 0000:03: resource 2 [mem 0xd2000000-0xd3ffffff 64bit pref]
[    0.416434] pci_bus 0000:05: resource 0 [io  0x3000-0x3fff]
[    0.416442] pci_bus 0000:05: resource 1 [mem 0xda000000-0xdbffffff]
[    0.416450] pci_bus 0000:05: resource 2 [mem 0xd4000000-0xd5ffffff 64bit pref]
[    0.416458] pci_bus 0000:07: resource 0 [io  0x4000-0x4fff]
[    0.416465] pci_bus 0000:07: resource 1 [mem 0xdc000000-0xdc0fffff]
[    0.416473] pci_bus 0000:07: resource 2 [mem 0x40000000-0x43ffffff pref]
[    0.416481] pci_bus 0000:07: resource 4 [io  0x0000-0xffff]
[    0.416488] pci_bus 0000:07: resource 5 [mem 0x00000000-0xffffffff]
[    0.416496] pci_bus 0000:08: resource 0 [io  0x4400-0x44ff]
[    0.416503] pci_bus 0000:08: resource 1 [io  0x4800-0x48ff]
[    0.416511] pci_bus 0000:08: resource 2 [mem 0x40000000-0x43ffffff pref]
[    0.416519] pci_bus 0000:08: resource 3 [mem 0x4c000000-0x4fffffff]
[    0.416613] NET: Registered protocol family 2
[    0.417040] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[    0.417147] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.417248] TCP: Hash tables configured (established 8192 bind 8192)
[    0.417298] TCP: reno registered
[    0.417306] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.417330] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.417478] NET: Registered protocol family 1
[    0.417516] pci 0000:00:02.0: Boot video device
[    0.417800] PCI: CLS mismatch (64 != 16), using 64 bytes
[    0.417834] pci 0000:07:08.0: Firmware left e100 interrupts enabled; disabling
[    0.417951] Trying to unpack rootfs image as initramfs...
[    1.371875] Freeing initrd memory: 15664k freed
[    1.384441] Simple Boot Flag at 0x36 set to 0x1
[    1.384987] Initialise module verification
[    1.385106] audit: initializing netlink socket (disabled)
[    1.385134] type=2000 audit(1386455387.384:1): initialized
[    1.455756] bounce pool size: 64 pages
[    1.455788] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.460537] VFS: Disk quotas dquot_6.5.2
[    1.460683] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.462349] fuse init (API version 7.20)
[    1.462590] msgmni has been set to 1739
[    1.463473] Key type asymmetric registered
[    1.463479] Asymmetric key parser 'x509' registered
[    1.463595] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    1.463670] io scheduler noop registered
[    1.463676] io scheduler deadline registered (default)
[    1.463695] io scheduler cfq registered
[    1.464126] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    1.464371] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    1.464603] pcieport 0000:00:1c.2: irq 42 for MSI/MSI-X
[    1.464817] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.464868] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.465074] intel_idle: does not run on family 6 model 14
[    1.465812] ACPI: AC Adapter [ADP0] (off-line)
[    1.466289] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    1.466494] ACPI: Lid Switch [LID]
[    1.466618] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    1.466630] ACPI: Power Button [PWRB]
[    1.466774] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    1.466784] ACPI: Power Button [PWRF]
[    1.466963] ACPI: Fan [FAN0] (off)
[    1.467104] ACPI: Requesting acpi_cpufreq
[    1.467553] tsc: Marking TSC unstable due to TSC halts in idle
[    1.467574] ACPI: acpi_idle registered with cpuidle
[    1.612808] thermal LNXTHERM:00: registered as thermal_zone0
[    1.612816] ACPI: Thermal Zone [TZ00] (46 C)
[    1.623641] thermal LNXTHERM:01: registered as thermal_zone1
[    1.623648] ACPI: Thermal Zone [TZ01] (39 C)
[    1.623890] GHES: HEST is not enabled!
[    1.624390] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.627763] isapnp: Scanning for PnP cards...
[    1.634125] ACPI: Battery Slot [BAT0] (battery present)
[    1.680824] Linux agpgart interface v0.103
[    1.681006] agpgart-intel 0000:00:00.0: Intel 945GM Chipset
[    1.681138] agpgart-intel 0000:00:00.0: detected gtt size: 262144K total, 262144K mappable
[    1.681764] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    1.682000] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[    1.686267] brd: module loaded
[    1.688494] loop: module loaded
[    1.688863] ata_piix 0000:00:1f.2: version 2.13
[    1.688894] ata_piix 0000:00:1f.2: MAP [
[    1.688899]  P0 P2 IDE IDE ]
[    1.863482] ata_piix 0000:00:1f.2: setting latency timer to 64
[    1.907838] scsi0 : ata_piix
[    1.908738] scsi1 : ata_piix
[    1.909559] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x18b0 irq 14
[    1.909567] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x18b8 irq 15
[    1.910629] libphy: Fixed MDIO Bus: probed
[    1.910866] tun: Universal TUN/TAP device driver, 1.6
[    1.910871] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.910980] PPP generic driver version 2.4.2
[    1.911098] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.911104] ehci-pci: EHCI PCI platform driver
[    1.911167] ehci-pci 0000:00:1d.7: setting latency timer to 64
[    1.911177] ehci-pci 0000:00:1d.7: EHCI Host Controller
[    1.911195] ehci-pci 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    1.911226] ehci-pci 0000:00:1d.7: debug port 1
[    1.915149] ehci-pci 0000:00:1d.7: cache line size of 64 is not supported
[    1.915372] ehci-pci 0000:00:1d.7: irq 23, io mem 0xdc444000
[    1.958880] ehci-pci 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.958976] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.958985] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.958992] usb usb1: Product: EHCI Host Controller
[    1.959000] usb usb1: Manufacturer: Linux 3.8.0-34-generic ehci_hcd
[    1.959007] usb usb1: SerialNumber: 0000:00:1d.7
[    1.959296] hub 1-0:1.0: USB hub found
[    1.959311] hub 1-0:1.0: 8 ports detected
[    1.960035] ehci-platform: EHCI generic platform driver
[    1.960061] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.960118] uhci_hcd: USB Universal Host Controller Interface driver
[    1.960167] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.960176] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.960191] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.960233] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001820
[    1.960316] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    1.960324] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.960332] usb usb2: Product: UHCI Host Controller
[    1.960339] usb usb2: Manufacturer: Linux 3.8.0-34-generic uhci_hcd
[    1.960346] usb usb2: SerialNumber: 0000:00:1d.0
[    1.960635] hub 2-0:1.0: USB hub found
[    1.960649] hub 2-0:1.0: 2 ports detected
[    1.960909] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.960919] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.960934] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.961005] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
[    1.961086] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    1.961095] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.961102] usb usb3: Product: UHCI Host Controller
[    1.961109] usb usb3: Manufacturer: Linux 3.8.0-34-generic uhci_hcd
[    1.961116] usb usb3: SerialNumber: 0000:00:1d.1
[    1.961386] hub 3-0:1.0: USB hub found
[    1.961400] hub 3-0:1.0: 2 ports detected
[    1.961672] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.961682] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.961697] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.961764] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[    1.961849] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    1.961857] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.961865] usb usb4: Product: UHCI Host Controller
[    1.961872] usb usb4: Manufacturer: Linux 3.8.0-34-generic uhci_hcd
[    1.961879] usb usb4: SerialNumber: 0000:00:1d.2
[    1.962143] hub 4-0:1.0: USB hub found
[    1.962157] hub 4-0:1.0: 2 ports detected
[    1.962407] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    1.962417] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    1.962431] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    1.962498] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001880
[    1.962583] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    1.962591] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.962599] usb usb5: Product: UHCI Host Controller
[    1.962606] usb usb5: Manufacturer: Linux 3.8.0-34-generic uhci_hcd
[    1.962613] usb usb5: SerialNumber: 0000:00:1d.3
[    2.006335] isapnp: No Plug & Play device found
[    2.006530] hub 5-0:1.0: USB hub found
[    2.006543] hub 5-0:1.0: 2 ports detected
[    2.006973] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.009757] i8042: Detected active multiplexing controller, rev 1.1
[    2.011280] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.011296] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    2.011373] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    2.011439] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    2.011504] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    2.011788] mousedev: PS/2 mouse device common for all mice
[    2.012212] rtc_cmos 00:06: RTC can wake from S4
[    2.012462] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    2.012511] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    2.012787] device-mapper: uevent: version 1.0.3
[    2.012955] device-mapper: ioctl: 4.23.1-ioctl (2012-12-18) initialised: [email]dm-devel@redhat.com[/email]
[    2.013005] EISA: Probing bus 0 at eisa.0
[    2.013021] Cannot allocate resource for EISA slot 1
[    2.013027] Cannot allocate resource for EISA slot 2
[    2.013032] Cannot allocate resource for EISA slot 3
[    2.013038] Cannot allocate resource for EISA slot 4
[    2.013043] Cannot allocate resource for EISA slot 5
[    2.013068] EISA: Detected 0 cards.
[    2.013088] cpufreq-nforce2: No nForce2 chipset.
[    2.013160] cpuidle: using governor ladder
[    2.013246] cpuidle: using governor menu
[    2.013255] ledtrig-cpu: registered to indicate activity on CPUs
[    2.013260] EFI Variables Facility v0.08 2004-May-17
[    2.013700] ashmem: initialized
[    2.014047] TCP: cubic registered
[    2.014377] NET: Registered protocol family 10
[    2.014954] NET: Registered protocol family 17
[    2.014981] Key type dns_resolver registered
[    2.015407] Using IPI No-Shortcut mode
[    2.015618] Loading module verification certificates
[    2.029997] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: 6d5f3b29dd810bffe7dee4744355192d09ca4755'
[    2.030030] registered taskstats version 1
[    2.035526] Key type trusted registered
[    2.040582] Key type encrypted registered
[    2.046449] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    2.046770] rtc_cmos 00:06: setting system clock to 2013-12-07 22:29:48 UTC (1386455388)
[    2.047214] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.047220] EDD information not available.
[    2.072576] ata1.00: ATA-7: HTS541080G9SA00, MB4OC60R, max UDMA/100
[    2.072586] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.076563] ata2.00: ATAPI: MATSHITADVD-RAM UJ-841S, 1.60, max UDMA/33
[    2.089070] ata1.00: configured for UDMA/100
[    2.089343] scsi 0:0:0:0: Direct-Access     ATA      HTS541080G9SA00  MB4O PQ: 0 ANSI: 5
[    2.089589] sd 0:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    2.089665] sd 0:0:0:0: [sda] Write Protect is off
[    2.089669] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.089702] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.090090] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.092444] ata2.00: configured for UDMA/33
[    2.094706] scsi 1:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-841S  1.60 PQ: 0 ANSI: 5
[    2.097006] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.097010] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.097113] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.097265] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.137824]  sda: sda1 sda2 < sda5 >
[    2.138198] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.138262] Freeing unused kernel memory: 796k freed
[    2.138631] Write protecting the kernel text: 6364k
[    2.138697] Write protecting the kernel read-only data: 2496k
[    2.138699] NX-protecting the kernel data: 3876k
[    2.158557] udevd[95]: starting version 175
[    2.268077] usb 1-4: new high-speed USB device number 2 using ehci-pci
[    2.367165] Disabling lock debugging due to kernel taint
[    2.371299] sdhci: Secure Digital Host Controller Interface driver
[    2.371303] sdhci: Copyright(c) Pierre Ossman
[    2.371609] sdhci-pci 0000:07:06.3: SDHCI controller found [104c:803c] (rev 0)
[    2.371660] mmc0: no vqmmc regulator found
[    2.371662] mmc0: no vmmc regulator found
[    2.408695] e100: Intel(R) PRO/100 Network Driver, 3.5.24-k2-NAPI
[    2.408700] e100: Copyright(c) 1999-2006 Intel Corporation
[    2.422677] usb 1-4: New USB device found, idVendor=0846, idProduct=9011
[    2.422683] usb 1-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.422687] usb 1-4: Product: Remote Download Wireless Adapter
[    2.422690] usb 1-4: Manufacturer: Broadcom
[    2.422693] usb 1-4: SerialNumber: 0
[    2.431121] mmc0: SDHCI controller on PCI [0000:07:06.3] using DMA
[    2.462811] e100 0000:07:08.0 eth0: addr 0xdc005000, irq 20, MAC addr 00:a0:d1:51:48:0d
[    2.516125] firewire_ohci 0000:07:06.1: added OHCI v1.10 device as card 0, 4 IR + 8 IT contexts, quirks 0x2
[    2.677667] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    2.677673] EXT4-fs (sda1): write access will be enabled during recovery
[    3.016319] firewire_core 0000:07:06.1: created device fw0: GUID 00080da0d151480d, S400
[    3.424762] EXT4-fs (sda1): orphan cleanup on readonly fs
[    3.424772] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 4325576
[    3.424890] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 4325520
[    3.424905] EXT4-fs (sda1): 2 orphan inodes deleted
[    3.424908] EXT4-fs (sda1): recovery complete
[    3.547600] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    5.077495] init: ureadahead main process (258) terminated with status 5
[    6.200796] Adding 1037308k swap on /dev/sda5.  Priority:-1 extents:1 across:1037308k 
[    7.322290] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    7.507809] udevd[333]: starting version 175
[    8.668449] lp: driver loaded but no devices found
[    8.901606] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[    9.096547] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    9.096824] acpi device:07: registered as cooling_device2
[    9.096852] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    9.096971] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input4
[    9.477888] intel_rng: FWH not detected
[    9.813316] ACPI Warning: 0x00001028-0x0000102f SystemIO conflicts with Region \PMIO 1 (20121018/utaddress-251)
[    9.813327] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    9.813333] ACPI Warning: 0x000011b0-0x000011bf SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
[    9.813338] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    9.813340] ACPI Warning: 0x00001180-0x000011af SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
[    9.813345] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    9.813347] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   10.087337] leds_ss4200: no LED devices found
[   10.103528] yenta_cardbus 0000:07:06.0: CardBus bridge found [1179:ff10]
[   10.103554] yenta_cardbus 0000:07:06.0: Enabling burst memory read transactions
[   10.103561] yenta_cardbus 0000:07:06.0: Using CSCINT to route CSC interrupts to PCI
[   10.103564] yenta_cardbus 0000:07:06.0: Routing CardBus interrupts to PCI
[   10.103571] yenta_cardbus 0000:07:06.0: TI: mfunc 0x01a01b22, devctl 0x66
[   10.129394] microcode: CPU0 sig=0x6e8, pf=0x20, revision=0x39
[   10.307852] [drm] Initialized drm 1.1.0 20060810
[   10.336892] yenta_cardbus 0000:07:06.0: ISA IRQ mask 0x0cf8, PCI irq 18
[   10.336898] yenta_cardbus 0000:07:06.0: Socket status: 30000006
[   10.336903] pci_bus 0000:07: Raising subordinate bus# of parent bus (#07) from #07 to #0b
[   10.336915] yenta_cardbus 0000:07:06.0: pcmcia: parent PCI bridge window: [io  0x4000-0x4fff]
[   10.336919] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x4000-0x4fff:
[   10.338349]  excluding 0x4000-0x403f 0x4400-0x44ff 0x4800-0x48ff
[   10.343356] yenta_cardbus 0000:07:06.0: pcmcia: parent PCI bridge window: [mem 0xdc000000-0xdc0fffff]
[   10.343360] pcmcia_socket pcmcia_socket0: cs: memory probe 0xdc000000-0xdc0fffff:
[   10.343364]  excluding 0xdc000000-0xdc00ffff
[   10.343377] yenta_cardbus 0000:07:06.0: pcmcia: parent PCI bridge window: [mem 0x40000000-0x43ffffff pref]
[   10.343380] pcmcia_socket pcmcia_socket0: cs: memory probe 0x40000000-0x43ffffff:
[   10.343392]  excluding 0x40000000-0x43ffffff
[   10.746522] psmouse serio4: synaptics: Touchpad model: 1, fw: 6.2, id: 0x25a0b1, caps: 0xa04713/0x0/0x0, board id: 3655, fw id: 53323
[   10.746531] psmouse serio4: synaptics: Toshiba Satellite A100 detected, limiting rate to 40pps.
[   10.781048] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input5
[   10.833567] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   10.874355] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af:
[   10.875495]  excluding 0x170-0x177 0x1f0-0x1f7 0x370-0x377
[   10.876354] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff:
[   10.876760]  excluding 0x3f0-0x3f7 0x400-0x407 0x4d0-0x4d7
[   10.877141] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff:
[   10.877783]  clean.
[   10.877804] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7:
[   10.878511]  clean.
[   10.878535] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff:
[   10.878540]  excluding 0xc0000-0xc7fff 0xcc000-0xcffff 0xdc000-0xfffff
[   10.878572] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff:
[   10.878588]  clean.
[   10.878608] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff:
[   10.878623]  clean.
[   10.878643] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff:
[   10.879372]  clean.
[   11.074231] i915 0000:00:02.0: setting latency timer to 64
[   11.075601] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   11.075607] [drm] Driver supports precise vblank timestamp query.
[   11.075679] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   11.232184] [drm] initialized overlay support
[   11.614969] fbcon: inteldrmfb (fb0) is primary device
[   11.700061] i915: fixme: max PWM is zero
[   11.700240] Console: switching to colour frame buffer device 160x50
[   11.705851] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   11.705855] i915 0000:00:02.0: registered panic notifier
[   11.705866] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   11.706022] snd_hda_intel 0000:00:1b.0: irq 43 for MSI/MSI-X
[   13.418619] type=1400 audit(1386455399.867:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=665 comm="apparmor_parser"
[   13.419194] type=1400 audit(1386455399.867:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=665 comm="apparmor_parser"
[   13.419526] type=1400 audit(1386455399.867:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=665 comm="apparmor_parser"
[   13.420177] type=1400 audit(1386455399.871:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=664 comm="apparmor_parser"
[   13.420745] type=1400 audit(1386455399.871:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=664 comm="apparmor_parser"
[   13.421073] type=1400 audit(1386455399.871:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=664 comm="apparmor_parser"
[   14.496426] init: failsafe main process (711) killed by TERM signal
[   15.837927] ppdev: user-space parallel port driver
[   16.798495] type=1400 audit(1386455403.247:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=792 comm="apparmor_parser"
[   16.799709] type=1400 audit(1386455403.247:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=792 comm="apparmor_parser"
[   16.824162] Bluetooth: Core ver 2.16
[   16.824226] NET: Registered protocol family 31
[   16.824228] Bluetooth: HCI device and connection manager initialized
[   16.824573] Bluetooth: HCI socket layer initialized
[   16.824577] Bluetooth: L2CAP socket layer initialized
[   16.824585] Bluetooth: SCO socket layer initialized
[   16.998073] Bluetooth: RFCOMM TTY layer initialized
[   16.998091] Bluetooth: RFCOMM socket layer initialized
[   16.998093] Bluetooth: RFCOMM ver 1.11
[   17.164903] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   17.164910] Bluetooth: BNEP filters: protocol multicast
[   17.164922] Bluetooth: BNEP socket layer initialized
[   20.053077] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.053651] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.056166] e100 0000:07:08.0 eth0: NIC Link is Up 100 Mbps Full Duplex
[   20.056388] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   20.637996] type=1400 audit(1386455407.087:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=875 comm="apparmor_parser"
[   20.638479] type=1400 audit(1386455407.087:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=875 comm="apparmor_parser"
[   20.643043] type=1400 audit(1386455407.091:12): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=876 comm="apparmor_parser"
[   20.643629] type=1400 audit(1386455407.091:13): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=876 comm="apparmor_parser"
[   20.643967] type=1400 audit(1386455407.091:14): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=876 comm="apparmor_parser"
[   20.762769] type=1400 audit(1386455407.211:15): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=877 comm="apparmor_parser"
[   20.769908] type=1400 audit(1386455407.219:16): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince//launchpad_integration" pid=877 comm="apparmor_parser"
[   20.771983] type=1400 audit(1386455407.219:17): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince//sanitized_helper" pid=877 comm="apparmor_parser"
[   20.773527] type=1400 audit(1386455407.223:18): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=877 comm="apparmor_parser"
[   20.777744] type=1400 audit(1386455407.227:19): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer//launchpad_integration" pid=877 comm="apparmor_parser"

---

### Post by patrice.brouillet on 2013-12-07
grep ndis doesnt show anything

---

### Post by chili555 on 2013-12-07
> **patrice.brouillet said:**
> grep ndis doesnt show anythingIt appears that ndiswrapper didn't load on boot as expected. Let's see what happens when we load it:```
sudo modprobe ndiswrapper
dmesg | grep ndis
```

---

### Post by patrice.brouillet on 2013-12-08
I entered sudo modprobe ndiswrapper and the answer was FATAL: module ndiswrapper not found

---

### Post by chili555 on 2013-12-08
> **patrice.brouillet said:**
> I entered sudo modprobe ndiswrapper and the answer was FATAL: module ndiswrapper not foundWith a temporary wired ethernet connection, please do:```
sudo apt-get install --reinstall ndiswrapper-common
sudo apt-get install --reinstall ndiswrapper-utils-1.9
sudo modprobe ndiswrapper
```

---

### Post by patrice.brouillet on 2013-12-08
after reinstalling and rebooting: 
pat@pat-Satellite-A100:~$ sudo modprobe ndiswrapper
[sudo] password for pat: 
FATAL: Module ndiswrapper not found.

---

### Post by chili555 on 2013-12-08
Weird. Any clues in here?```
dmesg | grep ndis
sudo dpkg -s ndiswrapper-common | head -n10
```

---

### Post by praseodym on 2013-12-08
Did you also install
```

sudo apt-get install linux-headers-generic linux-headers-$(uname -r) build-essential dkms ndiswrapper-dkms
```

---

### Post by patrice.brouillet on 2013-12-08
no i did not am i suppose to replace uname with my computer name?

---

### Post by patrice.brouillet on 2013-12-08
pat@pat-Satellite-A100:~$ sudo dpkg -s ndiswrapper-common | head -n10
[sudo] password for pat: 
Package: ndiswrapper-common
Status: install ok installed
Priority: optional
Section: misc
Installed-Size: 71
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: all
Source: ndiswrapper
Version: 1.57-1ubuntu1
Replaces: ndiswrapper-utils
and pat@pat-Satellite-A100:~$ dmesg | grep ndis doesnt do anything

---

### Post by chili555 on 2013-12-08
What do you think, praseodym, shall we download and compile 1.58?

---

### Post by patrice.brouillet on 2013-12-08
just ran: 
sudo apt-get install linux-headers-generic linux-headers-$(uname -r) build-essential dkms ndiswrapper-dkms
and it gave me an error :ndiswrapper-dkms 1.57-1ubuntu1: ndiswrapper kernel module failed to build

---

### Post by praseodym on 2013-12-08
Yes, I recommend using 1.58!

---

### Post by chili555 on 2013-12-08
Please download this to your desktop: [http://downloads.sourceforge.net/project/ndiswrapper/stable/ndiswrapper-1.58.tar.gz](http://downloads.sourceforge.net/project/ndiswrapper/stable/ndiswrapper-1.58.tar.gz)  Right-click it and select 'Extract Here.' Then in a terminal:```
sudo apt-get remove ndiswrapper-dkms ndiswrapper-common ndiswrapper-utils-1.9
cd Desktop/ndiswrapper-1.58
make
sudo make install
sudo modprobe ndiswraper
```Please note and post any errors; warnings are OK.

Any improvement?

---

### Post by patrice.brouillet on 2013-12-08
this was the result: 
pat@pat-Satellite-A100:~$ sudo apt-get remove ndiswrapper-dkms ndiswrapper-common ndiswrapper-utils-1.9
[sudo] password for pat: 
Sorry, try again.
[sudo] password for pat: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  thunderbird-globalmenu gir1.2-ubuntuoneui-3.0 libubuntuoneui-3.0-1
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  ndisgtk ndiswrapper-common ndiswrapper-dkms ndiswrapper-utils-1.9
0 upgraded, 0 newly installed, 4 to remove and 22 not upgraded.
After this operation, 1,844 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 196710 files and directories currently installed.)
Removing ndisgtk ...
Removing ndiswrapper-utils-1.9 ...
Removing ndiswrapper-common ...
dpkg: warning: while removing ndiswrapper-common, directory '/etc/ndiswrapper' not empty so not removed.
Removing ndiswrapper-dkms ...

------------------------------
Deleting module version: 1.57
completely from the DKMS tree.
------------------------------
Done.
Processing triggers for man-db ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
pat@pat-Satellite-A100:~$ cd Desktop/ndiswrapper-1.58
pat@pat-Satellite-A100:~/Desktop/ndiswrapper-1.58$ make
make -C utils
make[1]: Entering directory `/home/pat/Desktop/ndiswrapper-1.58/utils'
gcc -g -Wall -I../driver  -o loadndisdriver loadndisdriver.c
make[1]: Leaving directory `/home/pat/Desktop/ndiswrapper-1.58/utils'
make -C driver
make[1]: Entering directory `/home/pat/Desktop/ndiswrapper-1.58/driver'
make -C /usr/src/linux-headers-3.8.0-34-generic M=/home/pat/Desktop/ndiswrapper-1.58/driver
make[2]: Entering directory `/usr/src/linux-headers-3.8.0-34-generic'
  LD      /home/pat/Desktop/ndiswrapper-1.58/driver/built-in.o
  MKEXPORT /home/pat/Desktop/ndiswrapper-1.58/driver/crt_exports.h
  MKEXPORT /home/pat/Desktop/ndiswrapper-1.58/driver/hal_exports.h
  MKEXPORT /home/pat/Desktop/ndiswrapper-1.58/driver/ndis_exports.h
  MKEXPORT /home/pat/Desktop/ndiswrapper-1.58/driver/ntoskernel_exports.h
  MKEXPORT /home/pat/Desktop/ndiswrapper-1.58/driver/ntoskernel_io_exports.h
  MKEXPORT /home/pat/Desktop/ndiswrapper-1.58/driver/rtl_exports.h
  MKEXPORT /home/pat/Desktop/ndiswrapper-1.58/driver/usb_exports.h
  CC [M]  /home/pat/Desktop/ndiswrapper-1.58/driver/crt.o
  CC [M]  /home/pat/Desktop/ndiswrapper-1.58/driver/hal.o
  CC [M]  /home/pat/Desktop/ndiswrapper-1.58/driver/iw_ndis.o
  CC [M]  /home/pat/Desktop/ndiswrapper-1.58/driver/loader.o
  CC [M]  /home/pat/Desktop/ndiswrapper-1.58/driver/ndis.o
  CC [M]  /home/pat/Desktop/ndiswrapper-1.58/driver/ntoskernel.o
  CC [M]  /home/pat/Desktop/ndiswrapper-1.58/driver/ntoskernel_io.o
  CC [M]  /home/pat/Desktop/ndiswrapper-1.58/driver/pe_linker.o
  CC [M]  /home/pat/Desktop/ndiswrapper-1.58/driver/pnp.o
  CC [M]  /home/pat/Desktop/ndiswrapper-1.58/driver/proc.o
  CC [M]  /home/pat/Desktop/ndiswrapper-1.58/driver/rtl.o
  CC [M]  /home/pat/Desktop/ndiswrapper-1.58/driver/wrapmem.o
  CC [M]  /home/pat/Desktop/ndiswrapper-1.58/driver/wrapndis.o
  CC [M]  /home/pat/Desktop/ndiswrapper-1.58/driver/wrapper.o
  CC [M]  /home/pat/Desktop/ndiswrapper-1.58/driver/usb.o
  CC [M]  /home/pat/Desktop/ndiswrapper-1.58/driver/divdi3.o
  LD [M]  /home/pat/Desktop/ndiswrapper-1.58/driver/ndiswrapper.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/pat/Desktop/ndiswrapper-1.58/driver/ndiswrapper.mod.o
  LD [M]  /home/pat/Desktop/ndiswrapper-1.58/driver/ndiswrapper.ko
make[2]: Leaving directory `/usr/src/linux-headers-3.8.0-34-generic'
make[1]: Leaving directory `/home/pat/Desktop/ndiswrapper-1.58/driver'
pat@pat-Satellite-A100:~/Desktop/ndiswrapper-1.58$ sudo make install
make -C driver install
make[1]: Entering directory `/home/pat/Desktop/ndiswrapper-1.58/driver'
mkdir -p -m 755 /lib/modules/3.8.0-34-generic/misc
install -m 0644 ndiswrapper.ko /lib/modules/3.8.0-34-generic/misc
/sbin/depmod -a 3.8.0-34-generic
make[1]: Leaving directory `/home/pat/Desktop/ndiswrapper-1.58/driver'
make -C utils install
make[1]: Entering directory `/home/pat/Desktop/ndiswrapper-1.58/utils'
mkdir -p -m 755 /sbin
mkdir -p -m 755 /usr/sbin
install -m 755 loadndisdriver /sbin
install -m 755 ndiswrapper /usr/sbin
install -m 755 ndiswrapper-buginfo /usr/sbin
make[1]: Leaving directory `/home/pat/Desktop/ndiswrapper-1.58/utils'
mkdir -p -m 755 /usr/share/man/man8
install -m 644 ndiswrapper.8 /usr/share/man/man8
install -m 644 loadndisdriver.8 /usr/share/man/man8
pat@pat-Satellite-A100:~/Desktop/ndiswrapper-1.58$ sudo modprobe ndiswraper
FATAL: Module ndiswraper not found.
pat@pat-Satellite-A100:~/Desktop/ndiswrapper-1.58$ sudo modprobe ndiswrapper
pat@pat-Satellite-A100:~/Desktop/ndiswrapper-1.58$

---

### Post by chili555 on 2013-12-08
> pat@pat-Satellite-A100:~/Desktop/ndiswrapper-1.58$ sudo modprobe ndiswrapper
pat@pat-Satellite-A100:~/Desktop/ndiswrapper-1.58$ Awesome. Now how about:```
ndiswrapper -l
dmesg | grep ndis
iwconfig
```

---

### Post by patrice.brouillet on 2013-12-08
pat@pat-Satellite-A100:~/Desktop/ndiswrapper-1.58$ ndiswrapper -l
bcmn43xx32 : driver installed
pat@pat-Satellite-A100:~/Desktop/ndiswrapper-1.58$ dmesg | grep ndis
[ 2471.440189] ndiswrapper version 1.58 loaded (smp=yes, preempt=no)
[ 2471.454481] usbcore: registered new interface driver ndiswrapper
pat@pat-Satellite-A100:~/Desktop/ndiswrapper-1.58$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pat@pat-Satellite-A100:~/Desktop/ndiswrapper-1.58$

---

### Post by chili555 on 2013-12-08
> pat@pat-Satellite-A100:~/Desktop/ndiswrapper-1.58$ ndiswrapper -l
bcmn43xx32 : driver installedWe don't see 'device present;' that indicates that the inf and sys files are not correct for the device. It was inserted, right?

Here is a set that covers your device: [https://dl.dropboxusercontent.com/u/58267392/Broadcom_bcm43xx_USB_32_64bit_v2_amended.zip](https://dl.dropboxusercontent.com/u/58267392/Broadcom_bcm43xx_USB_32_64bit_v2_amended.zip)

Do you need some guidance to remove and replace?

---

### Post by patrice.brouillet on 2013-12-08
lo        no wireless extensions.

eth0      no wireless extensions.

pat@pat-Satellite-A100:~/Desktop/ndiswrapper-1.58$

---

### Post by patrice.brouillet on 2013-12-08
if you dont mind thanks

---

### Post by patrice.brouillet on 2013-12-08
the file is save and extracted on my desktop

---

### Post by chili555 on 2013-12-08
Please do:```
sudo modprobe -r ndiswrapper
sudo ndiswrapper -e bcmn43xx32
sudo rm -rf  /etc/ndiswrapper/*
sudo ndiswrapper -i Desktop/Broadcom_bcm43xx_USB_32_64bit_v2/bcmn43xx32.inf
sudo ndiswrapper -m
sudo modprobe ndiswrapper
ndiswrapper -l
```Pleease be sure the device is inserted.

---

### Post by patrice.brouillet on 2013-12-08
this the result
pat@pat-Satellite-A100:~$ sudo modprobe -r ndiswrapper
[sudo] password for pat: 
pat@pat-Satellite-A100:~$ sudo ndiswrapper -e bcmn43xx32
pat@pat-Satellite-A100:~$ sudo rm -rf  /etc/ndiswrapper/*
pat@pat-Satellite-A100:~$ sudo ndiswrapper -i Desktop/Broadcom_bcm43xx_USB_32_64bit_v2/bcmn43xx32.inf
couldn't find SourceDisksFiles section - continuing anyway...
installing bcmn43xx32 ...
pat@pat-Satellite-A100:~$ sudo ndiswrapper -m
module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

pat@pat-Satellite-A100:~$ sudo ndiswrapper -m
module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

pat@pat-Satellite-A100:~$ sudo modprobe ndiswrapper
pat@pat-Satellite-A100:~$ ndiswrapper -l
bcmn43xx32 : driver installed
    device (0846:9011) present

---

### Post by patrice.brouillet on 2013-12-08
this the result
pat@pat-Satellite-A100:~$ sudo modprobe -r ndiswrapper
[sudo] password for pat: 
pat@pat-Satellite-A100:~$ sudo ndiswrapper -e bcmn43xx32
pat@pat-Satellite-A100:~$ sudo rm -rf  /etc/ndiswrapper/*
pat@pat-Satellite-A100:~$ sudo ndiswrapper -i Desktop/Broadcom_bcm43xx_USB_32_64bit_v2/bcmn43xx32.inf
couldn't find SourceDisksFiles section - continuing anyway...
installing bcmn43xx32 ...
pat@pat-Satellite-A100:~$ sudo ndiswrapper -m
module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

pat@pat-Satellite-A100:~$ sudo ndiswrapper -m
module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

pat@pat-Satellite-A100:~$ sudo modprobe ndiswrapper
pat@pat-Satellite-A100:~$ ndiswrapper -l
bcmn43xx32 : driver installed
    device (0846:9011) present

---

### Post by chili555 on 2013-12-08
> pat@pat-Satellite-A100:~$ ndiswrapper -l
bcmn43xx32 : driver installed
[COLOR="#FF0000"]device (0846:9011) present [/COLOR]We're getting closer! Now:```
iwconfig
sudo iwlist scanning
```

---

### Post by patrice.brouillet on 2013-12-08
now i can see the network but i cant connect to it

---

### Post by patrice.brouillet on 2013-12-08
```
pat@pat-Satellite-A100:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:72 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:65/100  Signal level:-54 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```
```

pat@pat-Satellite-A100:~$ sudo iwlist scanning
[sudo] password for pat: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan1     Scan completed :
          Cell 01 - Address: 4C:60:DE:26:80:78
                    ESSID:"Scott"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality:79/100  Signal level:-45 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 000553636F7474
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A6C181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606081600000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD7F0050F204104A00011010440001021041000100103B00010310470010BE12DD3220E537CF673BA452600E7D9A1021000D4E4554474541522C20496E632E10230009574E5231303030763310240009574E523130303076331042000538333235381054000800060050F204000110110009574E52313030307633100800020084
                    IE: Unknown: DD090010180203F0050000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336C181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406081600000000000000000000000000000000000000
          Cell 02 - Address: 00:1C:F0:C4:D6:25
                    ESSID:"dlink"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality:28/100  Signal level:-78 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 0005646C696E6B
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334C101FFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401000500000000000000000000000000000000000000
                    IE: Unknown: 2D1A4C101FFFFF000000000000000000000000000004000000000000
                    IE: Unknown: 3D1601000100000000000000000000000000000000000000
                    IE: Unknown: DD7F0050F204104A0001101044000101103B00010310470010A3DF56432BAB3C3F95B79D7FFD084AB11021000E442D4C696E6B2053797374656D73102300074449522D363535102400024133104200046E6F6E651054000800060050F204000110110017587472656D65204E204749474142495420526F75746572100800020004
          Cell 03 - Address: 00:26:5A:FF:06:14
                    ESSID:"abby-gal"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality:26/100  Signal level:-79 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 0008616262792D67616C
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 200100
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401080800000000000000000000000000000000000000
                    IE: Unknown: 3D1601080800000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD7B0050F204104A00011010440001021041000100103B00010310470010565AA94967C14C0EAA8FF349E6F5931110210006442D4C696E6B1023000D442D4C696E6B20526F75746572102400074449522D363135104200046E6F6E651054000800060050F204000110110006442D4C696E6B100800020084103C000101
                    IE: Unknown: DD050050F20500
```

---

### Post by chili555 on 2013-12-08
Sorry, I will be off for the evening; perhaps one of my colleagues can help.

---

### Post by chili555 on 2013-12-09
> **patrice.brouillet said:**
> now i can see the network but i cant connect to itWhat do the logs report?```
cat /var/log/syslog | grep -e wlan -e etwork | tail -n20
```Run as you are trying to connect, of course.

---

### Post by patrice.brouillet on 2013-12-15
pat@pat-Satellite-A100:~$ cat /var/log/syslog | grep -e wlan -e etwork | tail -n20
Dec 15 17:44:44 pat-Satellite-A100 NetworkManager[843]: <info> (wlan1): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Dec 15 17:44:44 pat-Satellite-A100 NetworkManager[843]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) scheduled...
Dec 15 17:44:44 pat-Satellite-A100 NetworkManager[843]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) complete.
Dec 15 17:44:44 pat-Satellite-A100 NetworkManager[843]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) starting...
Dec 15 17:44:44 pat-Satellite-A100 NetworkManager[843]: <info> (wlan1): device state change: prepare -> config (reason 'none') [40 50 0]
Dec 15 17:44:44 pat-Satellite-A100 NetworkManager[843]: <info> Activation (wlan1/wireless): connection 'Scott 1' has security, and secrets exist.  No new secrets needed.
Dec 15 17:44:44 pat-Satellite-A100 NetworkManager[843]: <info> Config: added 'ssid' value 'Scott'
Dec 15 17:44:44 pat-Satellite-A100 NetworkManager[843]: <info> Config: added 'scan_ssid' value '1'
Dec 15 17:44:44 pat-Satellite-A100 NetworkManager[843]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Dec 15 17:44:44 pat-Satellite-A100 NetworkManager[843]: <info> Config: added 'auth_alg' value 'OPEN'
Dec 15 17:44:44 pat-Satellite-A100 NetworkManager[843]: <info> Config: added 'psk' value '<omitted>'
Dec 15 17:44:44 pat-Satellite-A100 NetworkManager[843]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) complete.
Dec 15 17:44:44 pat-Satellite-A100 NetworkManager[843]: <info> Config: set interface ap_scan to 1
Dec 15 17:44:44 pat-Satellite-A100 NetworkManager[843]: <info> (wlan1): supplicant interface state: disconnected -> scanning
Dec 15 17:44:49 pat-Satellite-A100 NetworkManager[843]: <info> (wlan1): supplicant interface state: scanning -> associating
Dec 15 17:44:50 pat-Satellite-A100 NetworkManager[843]: <info> (wlan1): supplicant interface state: associating -> 4-way handshake
Dec 15 17:44:59 pat-Satellite-A100 NetworkManager[843]: <info> (wlan1): supplicant interface state: 4-way handshake -> disconnected
Dec 15 17:45:00 pat-Satellite-A100 NetworkManager[843]: <info> (wlan1): supplicant interface state: disconnected -> scanning
Dec 15 17:45:05 pat-Satellite-A100 NetworkManager[843]: <info> (wlan1): supplicant interface state: scanning -> associating
Dec 15 17:45:05 pat-Satellite-A100 NetworkManager[843]: <info> (wlan1): supplicant interface state: associating -> 4-way handshake

---

### Post by patrice.brouillet on 2013-12-15
this is the result of the last command.

---

