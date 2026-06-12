---
title: "network not responding"
date: 2010-02-28
forum: Networking &amp; Wireless
---

### Post by tim.gab on 2010-02-28
hpdc5000mt intelpentium4   recently installed linux thru ubuntu over internet.   installed updates.  using newertech maxpower 802.11n usb stick with cradle to connect to internet.  having problems with connecting.   works fine on windows xp.   installed windows drivers on ubuntu.   icon shows connection but will not allow me to access internet thru firefox.  i have run all the recommended terminal commands.  here they are:

Version:1.0 StartHTML:0000000167 EndHTML:0000066515 StartFragment:0000000484 EndFragment:0000066499                                   administrator@ubuntu:~$ lspci  
 00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)  
 00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)  
 00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)  
 00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)  
 00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)  
 00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)  
 00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)  
 00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)  
 00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)  
 00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)  
 00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)  
 00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)  
 05:02.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5782 Gigabit Ethe
 

 administrator@ubuntu:~$ lsusb  
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 001 Device 003: ID 058f:6387 Alcor Micro Corp. Transcend JetFlash Flash Drive  
 Bus 001 Device 002: ID 15a9:0006   
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
   
 

 administrator@ubuntu:~$ lspci -nn | grep 'Wireless Brand'  
 administrator@ubuntu:~$  
 

 administrator@ubuntu:~$ ifconfig  
 eth0      Link encap:Ethernet  HWaddr 00:12:79:af:1b:20   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1  
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)  
           Interrupt:20  
 

 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:16436  Metric:1  
           RX packets:62 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:62 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:5572 (5.5 KB)  TX bytes:5572 (5.5 KB)  
 

 wlan0     Link encap:Ethernet  HWaddr 00:0e:8e:15:23:5d   
           inet addr:10.0.1.4  Bcast:10.0.1.255  Mask:255.255.255.0  
           inet6 addr: fe80::20e:8eff:fe15:235d/64 Scope:Link  
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1  
           RX packets:5286 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:3336 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
 

 administrator@ubuntu:~$ iwconfig  
 lo        no wireless extensions.  
 

 eth0      no wireless extensions.  
 

 wmaster0  no wireless extensions.  
 

 wlan0     IEEE 802.11bgn  ESSID:"home"   
           Mode:Managed  Frequency:2.412 GHz  Access Point: 00:19:E3:31:69:3A    
           Bit Rate=1 Mb/s   Tx-Power=9 dBm    
           Retry  long limit:7   RTS thrff   Fragment thrff  
           Power Management on  
           Link Quality=70/70  Signal level=44 dBm   
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0  
           Tx excessive retries:0  Invalid misc:0   Missed beacon:0  
 

 

 administrator@ubuntu:~$ iwconfig wlanO  
 wlanO     No such device  
 

 

 administrator@ubuntu:~$ lsmod  
 Module                  Size  Used by  
 nls_iso8859_1           3740  1  
 nls_cp437               5372  1  
 vfat                   10716  1  
 fat                    51452  1 vfat  
 usb_storage            52576  1  
 aes_i586                8124  1  
 aes_generic            27484  1 aes_i586  
 binfmt_misc             8356  1  
 snd_intel8x0           30168  2  
 snd_ac97_codec        101216  1 snd_intel8x0  
 ac97_bus                1532  1 snd_ac97_codec  
 snd_pcm_oss            37920  0  
 snd_mixer_oss          16028  1 snd_pcm_oss  
 snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss  
 rt2870sta             488820  0  
 snd_seq_dummy           2656  0  
 snd_seq_oss            28576  0  
 arc4                    1660  2  
 snd_seq_midi            6432  0  
 ecb                     2524  2  
 snd_rawmidi            22208  1 snd_seq_midi  
 snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi  
 snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event  
 rt2800usb              37372  0  
 snd_timer              22276  2 snd_pcm,snd_seq  
 rt2x00usb              11548  1 rt2800usb  
 snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq  
 rt2x00lib              29756  2 rt2800usb,rt2x00usb  
 led_class               4096  1 rt2x00lib  
 input_polldev           3716  1 rt2x00lib  
 snd                    59204  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 mac80211              181140  2 rt2x00usb,rt2x00lib  
 iptable_filter          3100  0  
 soundcore               7264  1 snd  
 ip_tables              11692  1 iptable_filter  
 snd_page_alloc          9156  2 snd_intel8x0,snd_pcm  
 cfg80211               93052  2 rt2x00lib,mac80211  
 x_tables               16544  1 ip_tables  
 shpchp                 32272  0  
 crc_ccitt               1852  1 rt2800usb  
 ppdev                   6688  0  
 psmouse                56500  0  
 parport_pc             31940  1  
 serio_raw               5280  0  
 lp                      8964  0  
 parport                35340  3 ppdev,parport_pc,lp  
 fbcon                  36640  72  
 tileblit                2460  1 fbcon  
 font                    8124  1 fbcon  
 bitblit                 5372  1 fbcon  
 softcursor              1756  1 bitblit 
 i915                  221320  3  
 drm                   159584  3 i915  
 i2c_algo_bit            5760  1 i915  
 floppy                 54916  0  
 tg3                   109600  0  
 video                  19380  1 i915  
 output                  2780  1 video  
 intel_agp              27484  2 i915  
 agpgart                34988  2 drm,intel_agp  
 

 

  administrator@ubuntu:~$ lsmod | grep "wlan_module_name"  
 administrator@ubuntu:~$  
 

 

 

 adminstrator@ubuntu:~$ dmesg
 disabled.  
 [    0.175262] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *10 11 14 15)  
 [    0.175503] SCSI subsystem initialized  
 [    0.175544] libata version 3.00 loaded.  
 [    0.175544] usbcore: registered new interface driver usbfs  
 [    0.175544] usbcore: registered new interface driver hub  
 [    0.175544] usbcore: registered new device driver usb  
 [    0.175544] ACPI: WMI: Mapper loaded 
 [    0.175544] PCI: Using ACPI for IRQ routing  
 [    0.188012] Bluetooth: Core ver 2.15 
 [    0.188035] NET: Registered protocol family 31  
 [    0.188035] Bluetooth: HCI device and connection manager initialized  
 [    0.188035] Bluetooth: HCI socket layer initialized  
 [    0.188035] NetLabel: Initializing  
 [    0.188035] NetLabel:  domain hash size = 128  
 [    0.188035] NetLabel:  protocols = UNLABELED CIPSOv4  
 [    0.188052] NetLabel:  unlabeled traffic allowed by default  
 [    0.188173] hpet clockevent registered  
 [    0.188177] HPET: 3 timers in total, 0 timers will be used for per-cpu timer  
 [    0.188183] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0  
 [    0.188190] hpet0: 3 comparators, 64-bit 14.318180 MHz counter  
 [    0.204017] pnp: PnP ACPI init  
 [    0.204042] ACPI: bus type pnp registered  
 [    0.206355] pnp 00:0c: io resource (0xf800-0xf81f) overlaps 0000:00:1f.0 BAR 13 (0xf800-0xf87f), disabling  
 [    0.206360] pnp 00:0c: io resource (0xf820-0xf83f) overlaps 0000:00:1f.0 BAR 13 (0xf800-0xf87f), disabling  
 [    0.206365] pnp 00:0c: io resource (0xf840-0xf85f) overlaps 0000:00:1f.0 BAR 13 (0xf800-0xf87f), disabling  
 [    0.206369] pnp 00:0c: io resource (0xf860-0xf87f) overlaps 0000:00:1f.0 BAR 13 (0xf800-0xf87f), disabling  
 [    0.206853] pnp: PnP ACPI: found 14 devices  
 [    0.206857] ACPI: ACPI bus type pnp unregistered  
 [    0.206862] PnPBIOS: Disabled by ACPI PNP  
 [    0.206881] system 00:0b: ioport range 0x4d0-0x4d1 has been reserved  
 [    0.206890] system 00:0c: ioport range 0x400-0x41f has been reserved  
 [    0.206894] system 00:0c: ioport range 0x420-0x43f has been reserved  
 [    0.206897] system 00:0c: ioport range 0x440-0x45f has been reserved  
 [    0.206901] system 00:0c: ioport range 0x460-0x47f has been reserved  
 [    0.206905] system 00:0c: ioport range 0xfa00-0xfa3f has been reserved  
 [    0.206908] system 00:0c: ioport range 0xfc00-0xfc7f could not be reserved  
 [    0.206912] system 00:0c: ioport range 0xfc80-0xfcff has been reserved  
 [    0.206916] system 00:0c: ioport range 0xfe00-0xfe7f has been reserved  
 [    0.206919] system 00:0c: ioport range 0xfe80-0xfeff has been reserved  
 [    0.206929] system 00:0d: iomem range 0x0-0x9ffff could not be reserved  
 [    0.206933] system 00:0d: iomem range 0x100000-0x1f7fffff could not be reserved  
 [    0.206937] system 00:0d: iomem range 0x1f800000-0x1f8fffff has been reserved  
 [    0.206941] system 00:0d: iomem range 0xe0000-0xfffff could not be reserved  
 [    0.206945] system 00:0d: iomem range 0xfec01000-0xffffffff could not be reserved  
 [    0.206949] system 00:0d: iomem range 0xcc600-0xdffff has been reserved  
 [    0.241657] AppArmor: AppArmor Filesystem Enabled  
 [    0.241690] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:05  
 [    0.241695] pci 0000:00:1e.0:   IO window: 0x1000-0x1fff  
 [    0.241702] pci 0000:00:1e.0:   MEM window: 0xfc500000-0xfc7fffff  
 [    0.241707] pci 0000:00:1e.0:   PREFETCH window: disabled  
 [    0.241721] pci 0000:00:1e.0: setting latency timer to 64  
 [    0.241728] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]  
 [    0.241731] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]  
 [    0.241735] pci_bus 0000:05: resource 0 io:  [0x1000-0x1fff]  
 [    0.241738] pci_bus 0000:05: resource 1 mem: [0xfc500000-0xfc7fffff]  
 [    0.241741] pci_bus 0000:05: resource 3 io:  [0x00-0xffff]  
 [    0.241744] pci_bus 0000:05: resource 4 mem: [0x000000-0xffffffff]  
 [    0.241795] NET: Registered protocol family 2  
 [    0.241929] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)  
 [    0.242309] TCP established hash table entries: 16384 (order: 5, 131072 bytes)  
 [    0.242383] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)  
 [    0.242451] TCP: Hash tables configured (established 16384 bind 16384)  
 [    0.242454] TCP reno registered  
 [    0.242539] NET: Registered protocol family 1  
 [    0.242621] Trying to unpack rootfs image as initramfs...  
 [    0.483355] Freeing initrd memory: 7726k freed  
 [    0.488598] cpufreq-nforce2: No nForce2 chipset.  
 [    0.488636] Scanning for low memory corruption every 60 seconds  
 [    0.488770] audit: initializing netlink socket (disabled)  
 [    0.488791] type=2000 audit(1267266118.488:1): initialized  
 [    0.497673] HugeTLB registered 4 MB page size, pre-allocated 0 pages  
 [    0.499534] VFS: Disk quotas dquot_6.5.2  
 [    0.499615] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)  
 [    0.500353] fuse init (API version 7.12)  
 [    0.500461] msgmni has been set to 977  
 [    0.500759] alg: No test for stdrng (krng)  
 [    0.500778] io scheduler noop registered  
 [    0.500782] io scheduler anticipatory registered  
 [    0.500785] io scheduler deadline registered  
 [    0.500841] io scheduler cfq registered (default)  
 [    0.500858] pci 0000:00:02.0: Boot video device  
 [    0.501031] pci_hotplug: PCI Hot Plug PCI Core version: 0.5  
 [    0.501064] pciehp: PCI Express Hot Plug Controller Driver version: 0.4  
 [    0.501231] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0  
 [    0.501236] ACPI: Power Button [PWRF]  
 [    0.501309] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1  
 [    0.501316] ACPI: Power Button [PBTN]  
 [    0.501582] processor LNXCPU:00: registered as cooling_device0  
 [    0.501587] ACPI: Processor [CPU0] (supports 8 throttling states)  
 [    0.501683] processor LNXCPU:01: registered as cooling_device1  
 [    0.501689] ACPI: Processor [CPU1] (supports 8 throttling states)  
 [    0.503324] isapnp: Scanning for PnP cards...  
 [    0.689148] Switched to high resolution mode on CPU 1  
 [    0.692044] Switched to high resolution mode on CPU 0  
 [    0.857267] isapnp: No Plug & Play device found  
 [    0.858732] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled  
 [    0.858838] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A  
 [    0.859261] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A  
 [    0.859421]   alloc irq_desc for 21 on node -1  
 [    0.859424]   alloc kstat_irqs on node -1  
 [    0.859434] serial 0000:05:0a.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21  
 [    0.859510] 0000:05:0a.0: ttyS1 at I/O 0x1000 (irq = 21) is a 16550A  
 [    0.860810] brd: module loaded  
 [    0.861434] loop: module loaded  
 [    0.861531] input: Macintosh mouse button emulation as /devices/virtual/input/input2  
 [    0.861670] ata_piix 0000:00:1f.1: version 2.13  
 [    0.861684] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)  
 [    0.861690]   alloc irq_desc for 18 on node -1  
 [    0.861693]   alloc kstat_irqs on node -1  
 [    0.861699] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18  
 [    0.861746] ata_piix 0000:00:1f.1: setting latency timer to 64  
 [    0.861844] scsi0 : ata_piix  
 [    0.861964] scsi1 : ata_piix  
 [    0.862207] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x24c0 irq 14  
 [    0.862211] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x24c8 irq 15  
 [    0.863384] Fixed MDIO Bus: probed  
 [    0.863434] PPP generic driver version 2.4.2  
 [    0.863557] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver  
 [    0.863584]   alloc irq_desc for 23 on node -1  
 [    0.863587]   alloc kstat_irqs on node -1  
 [    0.863594] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23  
 [    0.863609] ehci_hcd 0000:00:1d.7: setting latency timer to 64  
 [    0.863614] ehci_hcd 0000:00:1d.7: EHCI Host Controller  
 [    0.863681] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1  
 [    0.867593] ehci_hcd 0000:00:1d.7: debug port 1  
 [    0.867601] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported  
 [    0.867618] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfc480000  
 [    0.881011] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00  
 [    0.881106] usb usb1: configuration #1 chosen from 1 choice  
 [    0.881149] hub 1-0:1.0: USB hub found  
 [    0.881161] hub 1-0:1.0: 8 ports detected  
 [    0.881255] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver  
 [    0.881276] uhci_hcd: USB Universal Host Controller Interface driver  
 [    0.881311]   alloc irq_desc for 16 on node -1  
 [    0.881314]   alloc kstat_irqs on node -1  
 [    0.881320] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16  
 [    0.881328] uhci_hcd 0000:00:1d.0: setting latency timer to 64  
 [    0.881332] uhci_hcd 0000:00:1d.0: UHCI Host Controller  
 [    0.881374] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2  
 [    0.881405] uhci_hcd 0000:00:1d.0: irq 16, io base 0x00002440  
 [    0.881504] usb usb2: configuration #1 chosen from 1 choice  
 [    0.881541] hub 2-0:1.0: USB hub found  
 [    0.881551] hub 2-0:1.0: 2 ports detected  
 [    0.881610]   alloc irq_desc for 19 on node -1  
 [    0.881613]   alloc kstat_irqs on node -1  
 [    0.881619] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19  
 [    0.881626] uhci_hcd 0000:00:1d.1: setting latency timer to 64  
 [    0.881630] uhci_hcd 0000:00:1d.1: UHCI Host Controller  
 [    0.881675] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3  
 [    0.881706] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00002460  
 [    0.881804] usb usb3: configuration #1 chosen from 1 choice  
 [    0.881841] hub 3-0:1.0: USB hub found  
 [    0.881851] hub 3-0:1.0: 2 ports detected  
 [    0.881909] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18  
 [    0.881917] uhci_hcd 0000:00:1d.2: setting latency timer to 64  
 [    0.881921] uhci_hcd 0000:00:1d.2: UHCI Host Controller  
 [    0.881963] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4  
 [    0.881993] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00002480  
 [    0.882089] usb usb4: configuration #1 chosen from 1 choice  
 [    0.882126] hub 4-0:1.0: USB hub found  
 [    0.882135] hub 4-0:1.0: 2 ports detected  
 [    0.882269] PNP: PS/2 Controller [PNP0303:KBD,PNP0f0e:PS2M] at 0x60,0x64 irq 1,12  
 [    0.884970] serio: i8042 KBD port at 0x60,0x64 irq 1  
 [    0.884980] serio: i8042 AUX port at 0x60,0x64 irq 12  
 [    0.885091] mice: PS/2 mouse device common for all mice  
 [    0.885218] rtc_cmos 00:03: RTC can wake from S4  
 [    0.885268] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0  
 [    0.885293] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs  
 [    0.885437] device-mapper: uevent: version 1.0.3  
 [    0.885576] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]  
 [    0.885685] device-mapper: multipath: version 1.1.0 loaded  
 [    0.885691] device-mapper: multipath round-robin: version 1.0.0 loaded  
 [    0.885846] EISA: Probing bus 0 at eisa.0  
 [    0.885854] Cannot allocate resource for EISA slot 1  
 [    0.885857] Cannot allocate resource for EISA slot 2  
 [    0.885883] EISA: Detected 0 cards.  
 [    0.886015] cpuidle: using governor ladder  
 [    0.886020] cpuidle: using governor menu  
 [    0.886768] TCP cubic registered  
 [    0.886933] NET: Registered protocol family 10  
 [    0.887542] lo: Disabled Privacy Extensions  
 [    0.887999] NET: Registered protocol family 17  
 [    0.888035] Bluetooth: L2CAP ver 2.13  
 [    0.888038] Bluetooth: L2CAP socket layer initialized  
 [    0.888041] Bluetooth: SCO (Voice Link) ver 0.6  
 [    0.888043] Bluetooth: SCO socket layer initialized  
 [    0.888092] Bluetooth: RFCOMM TTY layer initialized  
 [    0.888098] Bluetooth: RFCOMM socket layer initialized  
 [    0.888102] Bluetooth: RFCOMM ver 1.11  
 [    0.888148] Using IPI No-Shortcut mode  
 [    0.888232] PM: Resume from disk failed.  
 [    0.888252] registered taskstats version 1  
 [    0.888359]   Magic number: 14:884:376  
 [    0.888441] rtc_cmos 00:03: setting system clock to 2010-02-27 10:21:59 UTC (1267266119)  
 [    0.888446] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found  
 [    0.888448] EDD information not available.  
 [    0.907118] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3  
 [    1.032539] ata1.00: ATA-6: WDC WD800BB-60JKA0, 05.01C05, max UDMA/100  
 [    1.032543] ata1.00: 156301488 sectors, multi 16: LBA  
 [    1.032590] ata1.01: ATA-7: Maxtor 6Y080L0, YAR41BW0, max UDMA/100  
 [    1.032593] ata1.01: 156301488 sectors, multi 16: LBA  
 [    1.032935] ata2.00: ATAPI: HL-DT-ST GCE-8486B, 1.02, max UDMA/33  
 [    1.032980] ata2.01: ATAPI: Compaq DVD-ROM DVD-117,  1.03, max UDMA/44  
 [    1.040351] ata1.00: configured for UDMA/100  
 [    1.048347] ata2.00: configured for UDMA/33  
 [    1.056346] ata1.01: configured for UDMA/100  
 [    1.056486] scsi 0:0:0:0: Direct-Access     ATA      WDC WD800BB-60JK 05.0 PQ: 0 ANSI: 5  
 [    1.056640] sd 0:0:0:0: Attached scsi generic sg0 type 0  
 [    1.056732] scsi 0:0:1:0: Direct-Access     ATA      Maxtor 6Y080L0   YAR4 PQ: 0 ANSI: 5  
 [    1.056857] sd 0:0:1:0: Attached scsi generic sg1 type 0  
 [    1.056909] sd 0:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)  
 [    1.056980] sd 0:0:0:0: [sda] Write Protect is off  
 [    1.056984] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00  
 [    1.057020] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA  
 [    1.057207]  sda:  
 [    1.064234] ata2.01: configured for UDMA/44  
 [    1.065534] scsi 1:0:0:0: CD-ROM            HL-DT-ST CD-RW GCE-8486B  1.02 PQ: 0 ANSI: 5  
 [    1.067728]  sda1  
 [    1.067762] sd 0:0:1:0: [sdb] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)  
 [    1.067859] sd 0:0:1:0: [sdb] Write Protect is off  
 [    1.067865] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00  
 [    1.067910] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA  
 [    1.068190] sd 0:0:0:0: [sda] Attached SCSI disk  
 [    1.068234]  sdb:sr0: scsi3-mmc drive: 52x/48x writer cd/rw xa/form2 cdda tray  
 [    1.068607] Uniform CD-ROM driver Revision: 3.20  
 [    1.068703] sr 1:0:0:0: Attached scsi CD-ROM sr0  
 [    1.068767] sr 1:0:0:0: Attached scsi generic sg2 type 5  
 [    1.069881] scsi 1:0:1:0: CD-ROM            Compaq   DVD-ROM DVD-117  1.03 PQ: 0 ANSI: 5  
 [    1.072255] sr1: scsi3-mmc drive: 40x/40x cd/rw xa/form2 cdda tray  
 [    1.072348] sr 1:0:1:0: Attached scsi CD-ROM sr1  
 [    1.072404] sr 1:0:1:0: Attached scsi generic sg3 type 5  
 [    1.084547]  sdb1  
 [    1.084928] sd 0:0:1:0: [sdb] Attached SCSI disk  
 [    1.084956] Freeing unused kernel memory: 540k freed  
 [    1.085413] Write protecting the kernel text: 4568k  
 [    1.085470] Write protecting the kernel read-only data: 1836k  
 [    1.197073] usb 1-4: new high speed USB device using ehci_hcd and address 2  
 [    1.254594] Linux agpgart interface v0.103  
 [    1.269743] agpgart-intel 0000:00:00.0: Intel 865 Chipset  
 [    1.270191] agpgart-intel 0000:00:00.0: detected 8060K stolen memory  
 [    1.272565] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xf0000000  
 [    1.378253] usb 1-4: configuration #1 chosen from 1 choice  
 [    1.379270] tg3.c:v3.99 (April 20, 2009)  
 [    1.379296]   alloc irq_desc for 20 on node -1  
 [    1.379301]   alloc kstat_irqs on node -1  
 [    1.379318] tg3 0000:05:02.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20  
 [    1.394868] tg3 0000:05:02.0: PME# disabled  
 [    1.403598] FDC 0 is a post-1991 82077  
 [    1.420232] [drm] Initialized drm 1.1.0 20060810  
 [    1.443640] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16  
 [    1.443650] i915 0000:00:02.0: setting latency timer to 64  
 [    1.472951] eth0: Tigon3 [partno(BCM95782A50) rev 3003] (PCI:33MHz:32-bit) MAC address 00:12:79:af:1b:20  
 [    1.472958] eth0: attached PHY is 5705 (10/100/1000Base-T Ethernet) (WireSpeed[0])  
 [    1.472964] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]  
 [    1.472968] eth0: dma_rwctrl[763f0000] dma_mask[64-bit]  
 [    1.586835] [drm] fb0: inteldrmfb frame buffer device  
 [    1.586852] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0  
 [    1.673046] render error detected, EIR: 0x00000010  
 [    1.673052] [drm:i915_handle_error] *ERROR* EIR stuck: 0x00000010, masking  
 [    1.673061] render error detected, EIR: 0x00000010  
 [    1.679375] [drm] DAC-5: set mode 1280x1024 16  
 [    1.684242] Console: switching to colour frame buffer device 160x64  
 [    2.120581] EXT4-fs (loop0): barriers enabled  
 [    2.151403] kjournald2 starting: pid 383, dev loop0:8, commit interval 5 seconds  
 [    2.151430] EXT4-fs (loop0): delayed allocation enabled  
 [    2.151435] EXT4-fs: file extents enabled  
 [    2.153434] EXT4-fs: mballoc enabled 
 [    2.153455] EXT4-fs (loop0): mounted filesystem with ordered data mode  
 [    3.128543] type=1505 audit(1267266121.739:2): operation="profile_load" pid=407 name=/usr/share/gdm/guest-session/Xsession  
 [    3.132485] type=1505 audit(1267266121.739:3): operation="profile_load" pid=408 name=/sbin/dhclient3  
 [    3.133265] type=1505 audit(1267266121.744:4): operation="profile_load" pid=408 name=/usr/lib/NetworkManager/nm-dhcp-client.action  
 [    3.133669] type=1505 audit(1267266121.744:5): operation="profile_load" pid=408 name=/usr/lib/connman/scripts/dhclient-script  
 [    3.185424] type=1505 audit(1267266121.795:6): operation="profile_load" pid=409 name=/usr/bin/evince  
 [    3.197489] type=1505 audit(1267266121.808:7): operation="profile_load" pid=409 name=/usr/bin/evince-previewer  
 [    3.204531] type=1505 audit(1267266121.812:8): operation="profile_load" pid=409 name=/usr/bin/evince-thumbnailer  
 [    3.222398] type=1505 audit(1267266121.832:9): operation="profile_load" pid=411 name=/usr/lib/cups/backend/cups-pdf  
 [    3.223264] type=1505 audit(1267266121.832:10): operation="profile_load" pid=411 name=/usr/sbin/cupsd  
 [    9.823870] udev: starting version 147  
 [   10.476244] lp: driver loaded but no devices found  
 [   10.502424] parport_pc 00:07: reported by Plug and Play ACPI  
 [   10.502480] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]  
 [   10.567641] ppdev: user-space parallel port driver  
 [   10.601133] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4  
 [   10.602793] lp0: using parport0 (interrupt-driven).  
 [   10.682608] psmouse serio1: ID: 10 00 64  
 [   10.692755] intel_rng: Firmware space is locked read-only. If you can't or  
 [   10.692758] intel_rng: don't want to disable this in firmware setup, and if  
 [   10.692760] intel_rng: you are certain that your system has a functional  
 [   10.692762] intel_rng: RNG, try using the 'no_fwh_detect' option.  
 [   10.704341] ip_tables: (C) 2000-2006 Netfilter Core Team  
 [   10.737108] cfg80211: Calling CRDA to update world regulatory domain  
 [   11.141706] cfg80211: World regulatory domain updated:  
 [   11.141714]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)  
 [   11.141720]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)  
 [   11.141725]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)  
 [   11.141730]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)  
 [   11.141735]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)  
 [   11.141741]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)  
 [   11.322172] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input4  
 [   11.366464] phy0: Selected rate control algorithm 'minstrel'  
 [   11.367472] Registered led device: rt2800usb-phy0::radio  
 [   11.367501] Registered led device: rt2800usb-phy0::assoc  
 [   11.367528] Registered led device: rt2800usb-phy0::quality  
 [   11.367936] usbcore: registered new interface driver rt2800usb  
 [   11.398224] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.  
 [   11.405099] rtusb init --->  
 [   11.405158] usbcore: registered new interface driver rt2870  
 [   11.456079] rt3070sta: module is from the staging directory, the quality is unknown, you have been warned.  
 [   11.463455] rtusb init --->  
 [   11.463464] Error: Driver 'rt2870' is already registered, aborting...  
 [   11.463472] usbcore: error -16 registering interface     driver rt2870  
 [   11.589376]   alloc irq_desc for 17 on node -1  
 [   11.589383]   alloc kstat_irqs on node -1  
 [   11.589396] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17  
 [   11.589440] Intel ICH 0000:00:1f.5: setting latency timer to 64  
 [   12.009020] intel8x0_measure_ac97_clock: measured 54780 usecs (2639 samples)  
 [   12.009027] intel8x0: clocking to 48000  
 [   14.992802] Adding 262136k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:1 across:262136k  
 [   15.042319] EXT4-fs (loop0): internal journal on loop0:8  
 [   15.714535] __ratelimit: 3 callbacks suppressed  
 [   15.714541] type=1505 audit(1267284134.324:12): operation="profile_replace" pid=853 name=/usr/share/gdm/guest-session/Xsession  
 [   15.717192] type=1505 audit(1267284134.328:13): operation="profile_replace" pid=854 name=/sbin/dhclient3  
 [   15.717936] type=1505 audit(1267284134.328:14): operation="profile_replace" pid=854 name=/usr/lib/NetworkManager/nm-dhcp-client.action  
 [   15.718339] type=1505 audit(1267284134.328:15): operation="profile_replace" pid=854 name=/usr/lib/connman/scripts/dhclient-script  
 [   15.723852] type=1505 audit(1267284134.332:16): operation="profile_replace" pid=855 name=/usr/bin/evince  
 [   15.736549] type=1505 audit(1267284134.344:17): operation="profile_replace" pid=855 name=/usr/bin/evince-previewer  
 [   15.743902] type=1505 audit(1267284134.352:18): operation="profile_replace" pid=855 name=/usr/bin/evince-thumbnailer  
 [   15.756764] type=1505 audit(1267284134.364:19): operation="profile_replace" pid=859 name=/usr/lib/cups/backend/cups-pdf  
 [   15.757839] type=1505 audit(1267284134.368:20): operation="profile_replace" pid=859 name=/usr/sbin/cupsd  
 [   15.761931] type=1505 audit(1267284134.372:21): operation="profile_replace" pid=860 name=/usr/sbin/tcpdump  
 [   16.275299] rt2800usb 1-4:1.0: firmware: requesting rt2870.bin  
 [   16.631580] ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 [   16.634377] tg3 0000:05:02.0: firmware: requesting tigon/tg3_tso5.bin  
 [   16.745615] tg3 0000:05:02.0: PME# disabled  
 [   17.047847] ADDRCONF(NETDEV_UP): eth0: link is not ready  
 [   19.129142] CPU0 attaching NULL sched-domain.  
 [   19.129151] CPU1 attaching NULL sched-domain.  
 [   19.169086] CPU0 attaching sched-domain:  
 [   19.169093]  domain 0: span 0-1 level SIBLING  
 [   19.169098]   groups: 0 1  
 [   19.169104]   domain 1: span 0-1 level MC  
 [   19.169108]    groups: 0-1 (__cpu_power = 2048)  
 [   19.169117] CPU1 attaching sched-domain:  
 [   19.169120]  domain 0: span 0-1 level SIBLING  
 [   19.169123]   groups: 1 0  
 [   19.169128]   domain 1: span 0-1 level MC  
 [   19.169132]    groups: 0-1 (__cpu_power = 2048)  
 [   20.383262] CPU0 attaching NULL sched-domain.  
 [   20.383270] CPU1 attaching NULL sched-domain.  
 [   20.397105] CPU0 attaching sched-domain:  
 [   20.397112]  domain 0: span 0-1 level SIBLING  
 [   20.397116]   groups: 0 1  
 [   20.397125] CPU1 attaching sched-domain:  
 [   20.397128]  domain 0: span 0-1 level SIBLING  
 [   20.397131]   groups: 1 0  
 [  742.913882] wlan0: authenticate with AP 00:19:e3:31:69:3a  
 [  742.918010] wlan0: authenticated  
 [  742.918015] wlan0: associate with AP 00:19:e3:31:69:3a  
 [  742.920890] wlan0: RX AssocResp from 00:19:e3:31:69:3a (capab=0x11 status=0 aid=3)  
 [  742.920895] wlan0: associated  
 [  742.932071] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready  
 [  742.945285] wlan0: deauthenticated (Reason: 2)  
 [  743.944020] wlan0: direct probe to AP 00:19:e3:31:69:3a try 1  
 [  743.946866] wlan0 direct probe responded  
 [  743.946870] wlan0: authenticate with AP 00:19:e3:31:69:3a  
 [  743.949112] wlan0: authenticated  
 [  743.949117] wlan0: associate with AP 00:19:e3:31:69:3a  
 [  743.953426] wlan0: RX ReassocResp from 00:19:e3:31:69:3a (capab=0x11 status=0 aid=3)  
 [  743.953434] wlan0: associated  
 [  753.256015] wlan0: no IPv6 routers present  
 [  755.598142] wlan0: disassociating by local choice (reason=3)  
 [  757.055705] wlan0: authenticate with AP 00:19:e3:31:69:3a  
 [  757.057339] wlan0: authenticated  
 [  757.057343] wlan0: associate with AP 00:19:e3:31:69:3a  
 [  757.060236] wlan0: RX AssocResp from 00:19:e3:31:69:3a (capab=0x11 status=0 aid=3)  
 [  757.060240] wlan0: associated  
 [  757.730315] padlock: VIA PadLock not detected.  
 [  800.933002] wlan0: deauthenticated (Reason: 7)  
 [  802.940017] wlan0: direct probe to AP 00:19:e3:31:69:3a try 1  
 [  802.946927] wlan0 direct probe responded  
 [  802.946931] wlan0: authenticate with AP 00:19:e3:31:69:3a  
 [  803.948015] wlan0: direct probe to AP 00:19:e3:31:69:3a try 1  
 [  803.950647] wlan0 direct probe responded  
 [  803.950651] wlan0: authenticate with AP 00:19:e3:31:69:3a  
 [  803.953896] wlan0: authenticated  
 [  803.953900] wlan0: associate with AP 00:19:e3:31:69:3a  
 [  803.956897] wlan0: RX ReassocResp from 00:19:e3:31:69:3a (capab=0x11 status=0 aid=3)  
 [  803.956901] wlan0: associated  
 [ 1034.941865] wlan0: deauthenticated (Reason: 7)  
 [ 1036.944035] wlan0: direct probe to AP 00:19:e3:31:69:3a try 1  
 [ 1037.144020] wlan0: direct probe to AP 00:19:e3:31:69:3a try 2  
 [ 1037.344036] wlan0: direct probe to AP 00:19:e3:31:69:3a try 3  
 [ 1037.544034] wlan0: direct probe to AP 00:19:e3:31:69:3a timed out  
 [ 1039.449191] wlan0: authenticate with AP 00:19:e3:31:69:3a  
 [ 1039.453324] wlan0: authenticated  
 [ 1039.453329] wlan0: associate with AP 00:19:e3:31:69:3a  
 [ 1039.458480] wlan0: RX ReassocResp from 00:19:e3:31:69:3a (capab=0x11 status=0 aid=3)  
 [ 1039.458488] wlan0: associated  
 [ 1104.190411] transmission[2012]: segfault at 50 ip 003e2f4c sp bf8fa8e0 error 4 in libgdk-x11-2.0.so.0.1800.3[37c000+92000]  
 [ 1330.833128] wlan0: deauthenticated (Reason: 7)  
 [ 1332.836022] wlan0: direct probe to AP 00:19:e3:31:69:3a try 1  
 [ 1332.839721] wlan0 direct probe responded  
 [ 1332.839726] wlan0: authenticate with AP 00:19:e3:31:69:3a  
 [ 1332.841956] wlan0: authenticated  
 [ 1332.841960] wlan0: associate with AP 00:19:e3:31:69:3a  
 [ 1332.846956] wlan0: RX ReassocResp from 00:19:e3:31:69:3a (capab=0x11 status=0 aid=3)  
 [ 1332.846960] wlan0: associated  
 [ 1715.304018] usb 1-6: new high speed USB device using ehci_hcd and address 3  
 [ 1715.439138] usb 1-6: configuration #1 chosen from 1 choice  
 [ 1715.439508] hub 1-0:1.0: over-current change on port 7  
 [ 1715.728295] Initializing USB Mass Storage driver...  
 [ 1715.728452] scsi2 : SCSI emulation for USB Mass Storage devices  
 [ 1715.728573] usbcore: registered new interface driver usb-storage  
 [ 1715.728578] USB Mass Storage support registered.  
 [ 1715.729035] usb-storage: device found at 3  
 [ 1715.729040] usb-storage: waiting for device to settle before scanning  
 [ 1720.728170] usb-storage: device scan complete  
 [ 1720.729018] scsi 2:0:0:0: Direct-Access     USB      Flash Disk       8.07 PQ: 0 ANSI: 2  
 [ 1720.729558] sd 2:0:0:0: Attached scsi generic sg4 type 0  
 [ 1720.738720] sd 2:0:0:0: [sdc] 2009088 512-byte logical blocks: (1.02 GB/981 MiB)  
 [ 1720.740108] sd 2:0:0:0: [sdc] Write Protect is off  
 [ 1720.740116] sd 2:0:0:0: [sdc] Mode Sense: 03 00 00 00  
 [ 1720.740122] sd 2:0:0:0: [sdc] Assuming drive cache: write through  
 [ 1720.742744] sd 2:0:0:0: [sdc] Assuming drive cache: write through  
 [ 1720.742752]  sdc: sdc1  
 [ 1720.925740] sd 2:0:0:0: [sdc] Assuming drive cache: write through  
 [ 1720.925750] sd 2:0:0:0: [sdc] Attached SCSI removable disk  
 [ 3530.942271] type=1503 audit(1267287649.551:22): operation="capable" pid=2481 parent=2468 profile="/usr/sbin/cupsd" name="sys_admin" 
 [ 3827.034956] wlan0: deauthenticated (Reason: 7)  
 [ 3829.040023] wlan0: direct probe to AP 00:19:e3:31:69:3a try 1  
 [ 3829.042544] wlan0 direct probe responded  
 [ 3829.042548] wlan0: authenticate with AP 00:19:e3:31:69:3a  
 [ 3829.044421] wlan0: authenticated  
 [ 3829.044424] wlan0: associate with AP 00:19:e3:31:69:3a  
 [ 3829.047063] wlan0: RX ReassocResp from 00:19:e3:31:69:3a (capab=0x11 status=0 aid=3)  
 [ 3829.047069] wlan0: associated  
 [ 3839.055883] wlan0: disassociating by local choice (reason=3)  
 [ 3840.530364] wlan0: authenticate with AP 00:19:e3:31:69:3a  
 [ 3840.531994] wlan0: authenticated  
 [ 3840.531998] wlan0: associate with AP 00:19:e3:31:69:3a  
 [ 3840.536864] wlan0: RX AssocResp from 00:19:e3:31:69:3a (capab=0x11 status=0 aid=3)  
 [ 3840.536869] wlan0: associated  
 

 

 administrator@ubuntu:~$ sudo lshw -C network  
 [sudo] password for administrator:  
   *-network                
        description: Ethernet interface  
        product: NetXtreme BCM5782 Gigabit Ethernet  
        vendor: Broadcom Corporation  
        physical id: 2  
        bus info: pci@0000:05:02.0  
        logical name: eth0  
        version: 03  
        serial: 00:12:79:af:1b:20  
        capacity: 1GB/s  
        width: 64 bits  
        clock: 66MHz  
        capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation  
        configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 firmware=5782-v3.13 latency=64 link=no mingnt=64 multicast=yes port=twisted pair  
        resources: irq:20 memory:fc500000-fc50ffff  
   *-network  
        description: Wireless interface  
        physical id: 1  
        logical name: wlan0  
        serial: 00:0e:8e:15:23:5d  
        capabilities: ethernet physical wireless  
        configuration: broadcast=yes ip=10.0.1.4 multicast=yes wireless=IEEE 802.11bgn  
 

 

 

 

 administrator@ubuntu:~$ iwlist scan  
 lo        Interface doesn't support scanning.  
 

 eth0      Interface doesn't support scanning.  
 

 wmaster0  Interface doesn't support scanning.  
 

 wlan0     Scan completed :  
           Cell 01 - Address: 00:19:E3:31:69:3A  
                     Channel:1  
                     Frequency:2.412 GHz (Channel 1)  
                     Quality=70/70  Signal level=44 dBm   
                     Encryption key:on  
                     ESSID:"home" 
                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s  
                     Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s  
                               36 Mb/s; 48 Mb/s; 54 Mb/s  
                     Mode:Master  
                     Extra:tsf=0000011659741c62  
                     Extra: Last beacon: 33912ms ago  
                     IE: Unknown: 0004686F6D65  
                     IE: Unknown: 010482848B96  
                     IE: Unknown: 030101 
                     IE: Unknown: 2A0107 
                     IE: Unknown: 2F0107 
                     IE: IEEE 802.11i/WPA2 Version 1  
                         Group Cipher : TKIP  
                         Pairwise Ciphers (2) : CCMP TKIP  
                         Authentication Suites (1) : PSK  
                     IE: Unknown: 32080C1218243048606C  
                     IE: Unknown: DD0700039301030000  
                     IE: Unknown: DD06001018020100  
                     IE: WPA Version 1  
                         Group Cipher : TKIP  
                         Pairwise Ciphers (1) : TKIP  
                         Authentication Suites (1) : PSK  
 

   
 administrator@ubuntu:~$ iwlist scan wlanO  
 iwlist: unknown command `wlanO' (check 'iwlist --help').  
 

 

 administrator@ubuntu:~$ lsb_release -d  
 Description:    Ubuntu 9.10  
 

 

 administrator@ubuntu:~$ uname -mr  
 2.6.31-19-generic i686  
 

 

 

 

 administrator@ubuntu:~$ sudo /etc/init.d/networking restart  
  * Reconfiguring network interfaces...                                   [ OK ]  
 administrator@ubuntu:~$ 





any help understanding all this would be appreciated.
thanks

---

### Post by lloyd_b on 2010-02-28
> administrator@ubuntu:~$ iwconfig wlanO
wlanO No such device I think this one is the result of a typo - The interface is "wlan<zero>", not "wlan<capital oh>".

Could you post the output of the command "route -n"?  You have an active wired interface (with no address defined), and I'm wondering if it's trying to use that instead of the wireless connection...

Lloyd B.

---

### Post by tim.gab on 2010-02-28
loyd,  thanks for the response.  sorry about the 0. stressed!  here are the results of your request:

Version:1.0 StartHTML:0000000167 EndHTML:0000001973 StartFragment:0000000454 EndFragment:0000001957    	 	 	 	 	 	  

 administrator@ubuntu:~$ iwconfig wlan0  
 wlan0     IEEE 802.11bgn  ESSID:"home"   
           Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated    
           Tx-Power=9 dBm    
           Retry  long limit:7   RTS thr:off   Fragment thr:off  
           Power Management:on  
           Link Quality:0  Signal level:0  Noise level:0  
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0  
           Tx excessive retries:0  Invalid misc:0   Missed beacon:0  
 

 administrator@ubuntu:~$ route -n  
 Kernel IP routing table  
 Destination     Gateway         Genmask         Flags Metric Ref    Use Iface  
 administrator@ubuntu:~$ 





let me know if you need anything else. thanks

---

### Post by lloyd_b on 2010-02-28
There's some inconsistency between your two posts.  From post 1:> administrator@ubuntu:~$ iwconfig
lo no wireless extensions.


eth0 no wireless extensions.


wmaster0 no wireless extensions.


wlan0 IEEE 802.11bgn ESSID:"home"
Mode:Managed Frequency:2.412 GHz Access Point: [COLOR="Red"]00:19:E3:31:69:3A[/COLOR]
Bit Rate=1 Mb/s Tx-Power=9 dBm
Retry long limit:7 RTS thrff Fragment thrff
Power Management on
Link Quality=70/70 Signal level=44 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0and from the other post:> administrator@ubuntu:~$ iwconfig wlan0
wlan0 IEEE 802.11bgn ESSID:"home"
Mode:Managed Frequency:2.412 GHz Access Point: [COLOR="Red"]Not-Associated[/COLOR]
Tx-Power=9 dBm
Retry long limit:7 RTS thrff Fragment thrff
Power Managementn
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0 
The 'route' information is meaningless in the second case, because you aren't connected to a network.  Can you see if you can get it connected again, and post the 'route -n' info with it actually connected to the access point?

Lloyd B.

---

### Post by ubun2ibun3 on 2010-02-28
> administrator@ubuntu:~$ route -n  
 Kernel IP routing table  
 Destination     Gateway         Genmask         Flags Metric Ref    Use Iface  
 administrator@ubuntu:~$ 

Hmmm... I'm a noob, and I don't really know what much of the output means ;), but shouldn't the routing table from "route -n" have some entries?

I have a wireless LAN, but I have dialup internet, so when I startup the computer, it tries to use the wireless and not the modem.  To fix it, I have to type:

sudo route add default ppp0

So I would assume you would need something like:

sudo route add default wlan0

But again, I'm not positive :)

---

### Post by tim.gab on 2010-02-28
sorry,  didnt notice not being connected.  sometimes it just stops on its own.  here are new reults while the icon shows connection.

Version:1.0 StartHTML:0000000167 EndHTML:0000002051 StartFragment:0000000454 EndFragment:0000002035                                   

 administrator@ubuntu:~$ iwconfig wlan0  
 wlan0     IEEE 802.11bgn  ESSID:"home"   
           Mode:Managed  Frequency:2.412 GHz  Access Point: 00:19:E3:31:69:3A    
           Bit Rate=1 Mb/s   Tx-Power=9 dBm    
           Retry  long limit:7   RTS thr:off   Fragment thr:off  
           Power Management:on  
           Link Quality=70/70  Signal level=48 dBm   
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0  
           Tx excessive retries:0  Invalid misc:0   Missed beacon:0  
 

 administrator@ubuntu:~$ route -n  
 Kernel IP routing table  
 Destination     Gateway         Genmask         Flags Metric Ref    Use Iface  
 10.0.1.0        0.0.0.0         255.255.255.0   U     2      0        0 wlan0  
 169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0  
 0.0.0.0         10.0.1.1        0.0.0.0         UG    0      0        0 wlan0  
 administrator@ubuntu:~$

Version:1.0 StartHTML:0000000167 EndHTML:0000001752 StartFragment:0000000454 EndFragment:0000001736    	 	 	 	 	 	   administrator@ubuntu:~$ iwconfig  
 lo        no wireless extensions.  
 

 eth0      no wireless extensions.  
 

 wmaster0  no wireless extensions.  
 

 wlan0     IEEE 802.11bgn  ESSID:"home"   
           Mode:Managed  Frequency:2.412 GHz  Access Point: 00:19:E3:31:69:3A    
           Bit Rate=48 Mb/s   Tx-Power=9 dBm    
           Retry  long limit:7   RTS thr:off   Fragment thr:off  
           Power Management:on  
           Link Quality=70/70  Signal level=49 dBm   
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0  
           Tx excessive retries:0  Invalid misc:0   Missed beacon:0  
 

 administrator@ubuntu:~$

---

### Post by lloyd_b on 2010-03-01
> **tim.gab said:**
> sorry,  didnt notice not being connected.  sometimes it just stops on its own.  here are new reults while the icon shows connection.

Version:1.0 StartHTML:0000000167 EndHTML:0000002051 StartFragment:0000000454 EndFragment:0000002035                                   

 administrator@ubuntu:~$ iwconfig wlan0  
 wlan0     IEEE 802.11bgn  ESSID:"home"   
           Mode:Managed  Frequency:2.412 GHz  Access Point: 00:19:E3:31:69:3A    
           Bit Rate=1 Mb/s   Tx-Power=9 dBm    
           Retry  long limit:7   RTS thr:off   Fragment thr:off  
           Power Management:on  
           Link Quality=70/70  Signal level=48 dBm   
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0  
           Tx excessive retries:0  Invalid misc:0   Missed beacon:0  
 

 administrator@ubuntu:~$ route -n  
 Kernel IP routing table  
 Destination     Gateway         Genmask         Flags Metric Ref    Use Iface  
 10.0.1.0        0.0.0.0         255.255.255.0   U     2      0        0 wlan0  
 169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0  
 0.0.0.0         10.0.1.1        0.0.0.0         UG    0      0        0 wlan0  
 administrator@ubuntu:~$

Version:1.0 StartHTML:0000000167 EndHTML:0000001752 StartFragment:0000000454 EndFragment:0000001736    	 	 	 	 	 	   administrator@ubuntu:~$ iwconfig  
 lo        no wireless extensions.  
 

 eth0      no wireless extensions.  
 

 wmaster0  no wireless extensions.  
 

 wlan0     IEEE 802.11bgn  ESSID:"home"   
           Mode:Managed  Frequency:2.412 GHz  Access Point: 00:19:E3:31:69:3A    
           Bit Rate=48 Mb/s   Tx-Power=9 dBm    
           Retry  long limit:7   RTS thr:off   Fragment thr:off  
           Power Management:on  
           Link Quality=70/70  Signal level=49 dBm   
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0  
           Tx excessive retries:0  Invalid misc:0   Missed beacon:0  
 

 administrator@ubuntu:~$

Okay, that looks perfectly normal.  Now let's see if you have a real network connection...

In a terminal window, type "ping 10.0.1.1" and see if it gets any response.  If this works, then the actual network is working correctly, and the problem lies at a higher level.  It's unlikely that this will fail (the thing is getting the IP address and routing information from somewhere, and I assume it's from the network).

If that works, try pinging a well-known site by IP address. Try "ping  91.189.94.12" (that's one of Ubuntuforum's IP addresses).  If this works, then you have full internet connectivity.  If not, then there's an issue with your network.

Assuming that works, try pinging that same site by name ("ping www.ubuntuforums.org").

Also, could you boot to Windows XP, and see what IP address and Gateway it's getting there? The "IPConfig" command (run from a command prompt) will give you this information.

Lloyd B.

---

### Post by tim.gab on 2010-03-01
loyd,  here are the reults of the terminal pings. The sequences just keep going.

Version:1.0 StartHTML:0000000167 EndHTML:0000003528 StartFragment:0000000454 EndFragment:0000003512    	 	 	 	 	 	  administrator@ubuntu:~$ ping 10.0.1.1  
 PING 10.0.1.1 (10.0.1.1) 56(84) bytes of data.  
 64 bytes from 10.0.1.1: icmp_seq=1 ttl=64 time=2.69 ms  
 64 bytes from 10.0.1.1: icmp_seq=2 ttl=64 time=3.27 ms  
 64 bytes from 10.0.1.1: icmp_seq=3 ttl=64 time=2.65 ms  
 64 bytes from 10.0.1.1: icmp_seq=4 ttl=64 time=5.02 ms  
 64 bytes from 10.0.1.1: icmp_seq=5 ttl=64 time=2.75 ms  
 64
 

 

 

 

 administrator@ubuntu:~$ ping 91.189.94.12  
 PING 91.189.94.12 (91.189.94.12) 56(84) bytes of data.  
 64 bytes from 91.189.94.12: icmp_seq=5 ttl=46 time=107 ms  
 64 bytes from 91.189.94.12: icmp_seq=6 ttl=46 time=104 ms  
 64 bytes from 91.189.94.12: icmp_seq=7 ttl=46 time=104 ms  
 64 bytes from 91.189.94.12: icmp_seq=8 ttl=46 time=109 ms  
 6
 

 

 administrator@ubuntu:~$ ping [www.ubuntuforums.org](www.ubuntuforums.org)  
 PING [www.ubuntuforums.org](www.ubuntuforums.org) (91.189.94.12) 56(84) bytes of data.  
 64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=1 ttl=46 time=105 ms  
 64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=2 ttl=46 time=104 ms  
 64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=3 ttl=46 time=108 ms  
 64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=4 ttl=46 time=104 ms  
 64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=5 ttl=46 time=105 ms  
 6
 

 THIS INFO IS COPIED FROM THE NETWORK DEVICE PAGE

 

 Network device:	wlan0  
 Hardware address:	00:0e:8e:15:23:5d  
 Multicast:	Enabled  
 MTU:	1500  
 Link speed:	48 Mbps  
 State:	Active  
 Transmitted packets:	762  
 Transmission errors:	0  
 Received packets:	604  
 Reception errors:	0  
 Collisions:	0 





REGARDING THE IPConfig RUN COMMAND IN WINDOWS XP - STRANGE- THE WINDOW WOULD FLASH WITH THE INFO BUT NOT STAY ON SCREEN.  NO MATTER WHAT I DID IT WOULD NOT STAY UP FOR MORE THAN A SPLIT SECOND.  NOT ENOUGH TIME TO GET INFO.  SO I HAVE THIS INFO FROM "NETWORK CONNECT DETAILS"


Physical address   00-0E-8E-15-23-5D
IP Address            10.0.1.4
Subnet Mask         255.255.255.0
Default Gateway    10.0.1.1
DHCP Server         10.0.1.1
DNS Server           10.0.1.1




AND THIS INFO FROM THE "WIRELESS MONITOR SCREEN" PROVIDED BY THE USB NETWORK STICK:


DHCP Status:                    Enable
Current IP:                        10.0.1.4
Subnet Mask                      255.255.255.0
Default Gateway:                10.0.1.1
DNS Server:                       10.0.1.1


Home Network [00:19:E3:31:69:3A]


uses the "Broadcom Advanced Server Program Driver"




I hope this can help.  I am getting totally confused!!
Tim

---

### Post by lloyd_b on 2010-03-01
<quote>loyd, here are the reults of the terminal pings. The sequences just keep going.</quote>Sorry, I should have warned you - ping will keep going unless you give it an option to tell it to do otherwise.

The pings are perfectly normal.  You can ping the gateway, ping an internet site by number, and ping a site by name.  So there's full internet connectivity, and name resolution is working.

In short - I don't see any problems.  Have you tried getting into Firefox, and entering "www.ubuntuforums.org" in the address bar?  Because it *should* be able to reach these forums.

Are there *any* sites you can reach?  Are there particular ones you *can't* reach?  

One experiment to try.  In a terminal window, "sudo ifconfig wlan0 mtu 1400" and try Firefox.  Repeat this step, decreasing the number by 100 until you get down to about 500.  Sometimes an ISP has problems with standard MTU (Max Transmission Units) packets, in which case it may be necessary to reduce this value.

I wish I could give you something better than "maybe...", but I really don't see anything wrong.

A note on IPConfig - Go to "start->programs->accessories->command prompt", and this will open a DOS window (something like a Linux terminal window).  Run the command from there.

Lloyd B.

---

### Post by tim.gab on 2010-03-01
first,  thank you loyd for all your time .  now to answer your queries.  i have tried the sudo ifconfig wlan0 mtu from 1400 down to 500.  no change that i can tell.  i get the default opening page on firefox.  when i type in an address i never get a full load up.  the google page is the best.  about 90% of that page loads,  enough so that i can actually type a subject in the google search bar,  hit return and the page will half come up, ie i get the paid ads on the right but nothing on the left.

when i type in [www.ubuntuforums.org]("http://www.ubuntuforums.org"),  i only get about half loaded and it then just sits and continues to say "waiting for ubuntu"

i did get into the xp window you ask about. results:
ethernet adapter           media disconnected
ethernet adapter wireless network community: 3
connection-specific DNS suffix:hr.cox.net
ip address :10.0.4.1
subnet mask: 255:255:255:0
default gateway: 10.0.1.1

also. out of curiosity i opened the "windows drivers" folder located in System>Admin
it stated:  drivers:  none listed
and when i asked it to "configure network"  it "could not find a network config tool"

any bearing on this dilemma?

one more curios aspect,  as i said before,  sometimes the net connection will just stop on its own.  when i try to reconnect it will always ask me for my password even though its set to auto.  and the it will take forever to reconnect.  sometimes i have to disconnect the usb device and reconnect to get back on the network.

i am beginning to think their is some incompatibility in the device, drivers, and ubuntu.
tim

just received this from newertech support,  

Dear Tim,
We do not list it as Linux compatible so we cannot support it with Linux  directly.

The chip set in the adapter is from Ralink and they do have drivers on  their site   You may be able to get it to work using something from  their site at [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

Hope that helps some!
    Loyd, I looked at that site and I personally cannot make heads nor tails out of the info. Sounds as though I just may be better off with a different usb stick!  What do you think?

---

### Post by lloyd_b on 2010-03-02
> Loyd, I looked at that site and I personally cannot make heads nor tails out of the info. Sounds as though I just may be better off with a different usb stick! What do you think? 

Well, that's what *I* would do in this case.  It sounds like the problem is that the wireless connection itself is unstable - it works for a bit and then stops, then works a bit more and stops, etc.  I don't see a real chance of trying to fix this one, if the device in question doesn't have properly supported drivers.

Lloyd B.

---

