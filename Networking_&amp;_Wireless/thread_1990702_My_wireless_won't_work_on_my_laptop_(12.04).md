---
title: "My wireless won't work on my laptop (12.04)"
date: 2012-05-29
forum: Networking &amp; Wireless
---

### Post by PumaYohn on 2012-05-29
First off, let me say that I know LITTLE to NOTHING about Linux and that I have been searching for over a week for a solution to this problem, but I can't found anything so I've finally decided to join the forums and see if I can get some help this way. I have a dell laptop (Inspiron e1505). It has a built in wireless card that Ubuntu recognizes, but for some reason won't use it. I've also tried using a USB wireless adapter, and it recognized it, but when I tried to connect it wouldn't work.

For some reason Fedora 16 and Knoppix works flawlessly with both my wireless card and my usb wireless adapter. But Ubunbu, Kubuntu, Lubunbu, Xubunbu (all versions 12.04), Linux Mint (12 and 13), and OpenSUSE have the exact same problem and it's this (I've tried with both live CDs and full installed versions):

When I first turn the laptop on (on fresh install, or live CD), I get this once it's booted up:
[IMG]http://desmond.imageshack.us/Himg32/scaled.php?server=32&filename=screenshotfrom201205300.png&res=landing[/IMG]
[IMG]http://desmond.imageshack.us/Himg708/scaled.php?server=708&filename=screenshotfrom201205300.png&res=landing[/IMG]

Once I install the drivers, nothing changes (even if I restart my laptop). If anything, the notice that I need to install the driver just goes away. When I plug in the USB Wireless adapter (it's a D-link PICO N Wireless adapter btw), it immediately shows me all of the available wireless networks, but then when I choose to connect to one, it will do 1 of 3 things:
1. Say it's connected, but the internet doesn't work
2. Say it's connected and then almost immediately disconnects
3. Will say it's connecting and never connects.

I've tried to get this to work with BOTH my neibors wireless interet (which is unencrypted) and my own internet (which is WEP encrypted)... neiter works. Can anyone help me with this?

BTW, I get wireless internet just fine on my other computers and laptops (running windows 7 and xp). And I get internet on my laptop with Ubuntu installed on it if I use an ethernet cable.

---

### Post by gnusci on 2012-05-29
Try to follow the steps at

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by PumaYohn on 2012-05-29
Ok, I'm trying to follow the guide, but how do I get to " **System > Administration >**"? I can get to the system settings menu, but I don't see anywhere that says Administration.

---

### Post by gnusci on 2012-05-29
> **PumaYohn said:**
> Ok, I'm trying to follow the guide, but how do I get to " **System > Administration >**"? I can get to the system settings menu, but I don't see anywhere that says Administration.

If you are using Unity, you have to use <Super>+A to find the application, and also use the System Settings from the Launcher.

---

### Post by PumaYohn on 2012-05-29
I followed every step, but unfortunately, it hasn't changed anything. It's showing me that the driver is activated, but it won't show any wireless options for me to use it.

[IMG]http://desmond.imageshack.us/Himg267/scaled.php?server=267&filename=screenshotfrom201205292.png&res=landing[/IMG]

Maybe this will help? --> When I initially typed everything in the terminal it came up as this (and this is the same thing that came up after I followed all of the steps):
[IMG]http://desmond.imageshack.us/Himg827/scaled.php?server=827&filename=screenshotfrom201205292.png&res=landing[/IMG]

---

### Post by gnusci on 2012-05-29
Check this thread

[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

And post the information. You can also try installing Wicd.

---

### Post by PumaYohn on 2012-05-30
Here's everything you asked for (I did this while my laptop was connected via ethernet cord. I don't know if they messes up the results. If so, I can do it without):
```

1) Machine Brand and Model

It's a Dell e1505 laptop 
``````
                                   
2) Wireless Brand, Model, and Chipset

 ispn@Ispn-U-Lt:~$ lspci -nn | grep 'Wireless Brand'  
 ispn@Ispn-U-Lt:~$ lspci  
 00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)  
 00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)  
 00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)  
 00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)  
 00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 01)  
 00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)  
 00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)  
 00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)  
 00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)  
 00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)  
 00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)  
 00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)  
 00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode] (rev 01)  
 00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)  
 01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Radeon Mobility X1400  
 03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)  
 03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller  
 03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)  
 03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)  
 03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)  
 0b:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)  
 ispn@Ispn-U-Lt:~$ lsusb  
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 001 Device 002: ID 05dc:a817 Lexar Media, Inc.  
   
``````
                                 
  3) Check Interface

 ispn@Ispn-U-Lt:~$ ifconfig  
 eth1      Link encap:Ethernet  HWaddr 00:15:c5:be:ea:c3   
           inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0  
           inet6 addr: fe80::215:c5ff:febe:eac3/64 Scope:Link  
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1  
           RX packets:33617 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:19508 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:34475639 (34.4 MB)  TX bytes:2647140 (2.6 MB)  
           Interrupt:17  
 

 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:16436  Metric:1  
           RX packets:963 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:963 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:99023 (99.0 KB)  TX bytes:99023 (99.0 KB)  
 

 ispn@Ispn-U-Lt:~$ iwconfig  
 lo        no wireless extensions.  
 

 eth1      no wireless extensions.  
 

 ispn@Ispn-U-Lt:~$  
  
``````

                                  4)Check for Module


 ispn@Ispn-U-Lt:~$ lsmod  
 Module                  Size  Used by  
 nls_iso8859_1          12617  1  
 nls_cp437              12751  1  
 vfat                   17308  1  
 fat                    55605  1 vfat  
 rfcomm                 38139  0  
 bnep                   17830  2  
 bluetooth             158438  10 rfcomm,bnep  
 parport_pc             32114  0  
 ppdev                  12849  0  
 joydev                 17393  0  
 binfmt_misc            17292  1  
 dell_wmi               12601  0  
 sparse_keymap          13658  1 dell_wmi  
 dell_laptop            13671  0  
 dcdbas                 14098  1 dell_laptop  
 snd_hda_codec_idt      60251  1  
 b44                    31364  0  
 snd_hda_intel          32765  3  
 snd_hda_codec         109562  2 snd_hda_codec_idt,snd_hda_intel  
 snd_hwdep              13276  1 snd_hda_codec  
 snd_pcm                80845  2 snd_hda_intel,snd_hda_codec  
 psmouse                72919  0  
 snd_seq_midi           13132  0  
 serio_raw              13027  0  
 r852                   17901  0  
 sm_common              16737  1 r852  
 snd_rawmidi            25424  1 snd_seq_midi  
 nand                   49667  2 r852,sm_common  
 nand_ids                8547  1 nand  
 r592                   17808  0  
 mtd                    35584  2 sm_common,nand  
 nand_bch               13003  1 nand  
 bch                    21757  1 nand_bch  
 nand_ecc               13070  1 nand  
 memstick               15857  1 r592  
 ssb                    50691  1 b44  
 mac_hid                13077  0  
 snd_seq_midi_event     14475  1 snd_seq_midi  
 wl                   2646601  0  
 snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event  
 video                  19068  0  
 radeon                733693  3  
 wmi                    18744  1 dell_wmi  
 snd_timer              28931  2 snd_pcm,snd_seq  
 snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq  
 ttm                    65344  1 radeon  
 drm_kms_helper         45466  1 radeon  
 drm                   197692  5 radeon,ttm,drm_kms_helper  
 snd                    62064  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 i2c_algo_bit           13199  1 radeon  
 lib80211               14040  1 wl  
 soundcore              14635  1 snd  
 snd_page_alloc         14108  2 snd_hda_intel,snd_pcm  
 lp                     17455  0  
 parport                40930  3 parport_pc,ppdev,lp  
 usb_storage            39646  1  
 sdhci_pci              18324  0  
 firewire_ohci          40172  0  
 firewire_core          56906  1 firewire_ohci  
 sdhci                  28241  1 sdhci_pci  
 crc_itu_t              12627  1 firewire_core  
 ispn@Ispn-U-Lt:~$ lsmod | grep "wlan_module_name"  
 ispn@Ispn-U-Lt:~$  
  
``````

5) Kernel boot message

                                  :00:1f.0 BAR 13 [io  0x1000-0x107f]  
 [    0.298411] pnp 00:03: disabling [io  0x100a-0x1059] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]  
 [    0.298416] pnp 00:03: disabling [io  0x1060-0x107f] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]  
 [    0.298422] pnp 00:03: disabling [io  0x1010-0x102f] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]  
 [    0.298490] system 00:03: [io  0xf400-0xf4fe] has been reserved  
 [    0.298495] system 00:03: [io  0x1080-0x10bf] has been reserved  
 [    0.298499] system 00:03: [io  0x10c0-0x10df] has been reserved  
 [    0.298504] system 00:03: [io  0x0809] has been reserved  
 [    0.298509] system 00:03: Plug and Play ACPI device, IDs PNP0c01 (active)  
 [    0.298549] pnp 00:04: [irq 12]  
 [    0.298604] pnp 00:04: Plug and Play ACPI device, IDs PNP0f13 (active)  
 [    0.298629] pnp 00:05: [io  0x0060]  
 [    0.298632] pnp 00:05: [io  0x0064]  
 [    0.298635] pnp 00:05: [io  0x0062]  
 [    0.298638] pnp 00:05: [io  0x0066]  
 [    0.298647] pnp 00:05: [irq 1]  
 [    0.298699] pnp 00:05: Plug and Play ACPI device, IDs PNP0303 (active)  
 [    0.298724] pnp 00:06: [io  0x0070-0x0071]  
 [    0.298736] pnp 00:06: [irq 8]  
 [    0.298739] pnp 00:06: [io  0x0072-0x0077]  
 [    0.298791] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)  
 [    0.298819] pnp 00:07: [io  0x0061]  
 [    0.298822] pnp 00:07: [io  0x0063]  
 [    0.298825] pnp 00:07: [io  0x0065]  
 [    0.298829] pnp 00:07: [io  0x0067]  
 [    0.298884] pnp 00:07: Plug and Play ACPI device, IDs PNP0800 (active)  
 [    0.298909] pnp 00:08: [io  0x0c80-0x0cff]  
 [    0.298912] pnp 00:08: [io  0x0910-0x091f]  
 [    0.298915] pnp 00:08: [io  0x0920-0x092f]  
 [    0.298919] pnp 00:08: [io  0x0cb0-0x0cbf]  
 [    0.298922] pnp 00:08: [io  0x0930-0x097f]  
 [    0.299009] system 00:08: [io  0x0c80-0x0cff] could not be reserved  
 [    0.299014] system 00:08: [io  0x0910-0x091f] has been reserved  
 [    0.299018] system 00:08: [io  0x0920-0x092f] has been reserved  
 [    0.299023] system 00:08: [io  0x0cb0-0x0cbf] has been reserved  
 [    0.299027] system 00:08: [io  0x0930-0x097f] has been reserved  
 [    0.299032] system 00:08: Plug and Play ACPI device, IDs PNP0c01 (active)  
 [    0.299062] pnp 00:09: [dma 4]  
 [    0.299065] pnp 00:09: [io  0x0000-0x000f]  
 [    0.299068] pnp 00:09: [io  0x0080-0x0085]  
 [    0.299072] pnp 00:09: [io  0x0087-0x008f]  
 [    0.299075] pnp 00:09: [io  0x00c0-0x00df]  
 [    0.299078] pnp 00:09: [io  0x0010-0x001f]  
 [    0.299081] pnp 00:09: [io  0x0090-0x0091]  
 [    0.299085] pnp 00:09: [io  0x0093-0x009f]  
 [    0.299139] pnp 00:09: Plug and Play ACPI device, IDs PNP0200 (active)  
 [    0.299163] pnp 00:0a: [io  0x00f0-0x00ff]  
 [    0.299172] pnp 00:0a: [irq 13]  
 [    0.299231] pnp 00:0a: Plug and Play ACPI device, IDs PNP0c04 (active)  
 [    0.299299] pnp 00:0b: [mem 0xfed00000-0xfed003ff]  
 [    0.299390] system 00:0b: [mem 0xfed00000-0xfed003ff] has been reserved  
 [    0.299396] system 00:0b: Plug and Play ACPI device, IDs PNP0103 PNP0c01 (active)  
 [    0.299837] pnp: PnP ACPI: found 12 devices  
 [    0.299841] ACPI: ACPI bus type pnp unregistered  
 [    0.299847] PnPBIOS: Disabled by ACPI PNP  
 [    0.337718] PCI: max bus depth: 1 pci_try_num: 2  
 [    0.337789] pci 0000:00:1c.0: BAR 15: assigned [mem 0x80000000-0x801fffff 64bit pref]  
 [    0.337797] pci 0000:00:1c.0: BAR 13: assigned [io  0x2000-0x2fff]  
 [    0.337803] pci 0000:01:00.0: BAR 6: assigned [mem 0xefd00000-0xefd1ffff pref]  
 [    0.337808] pci 0000:00:01.0: PCI bridge to [bus 01-01]  
 [    0.337813] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]  
 [    0.337820] pci 0000:00:01.0:   bridge window [mem 0xefd00000-0xefefffff]  
 [    0.337825] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]  
 [    0.337833] pci 0000:00:1c.0: PCI bridge to [bus 0b-0b]  
 [    0.337838] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]  
 [    0.337847] pci 0000:00:1c.0:   bridge window [mem 0xefc00000-0xefcfffff]  
 [    0.337854] pci 0000:00:1c.0:   bridge window [mem 0x80000000-0x801fffff 64bit pref]  
 [    0.337865] pci 0000:00:1c.3: PCI bridge to [bus 0c-0d]  
 [    0.337870] pci 0000:00:1c.3:   bridge window [io  0xd000-0xdfff]  
 [    0.337879] pci 0000:00:1c.3:   bridge window [mem 0xefa00000-0xefbfffff]  
 [    0.337886] pci 0000:00:1c.3:   bridge window [mem 0xe0000000-0xe01fffff 64bit pref]  
 [    0.337897] pci 0000:00:1e.0: PCI bridge to [bus 03-03]  
 [    0.337905] pci 0000:00:1e.0:   bridge window [mem 0xef900000-0xef9fffff]  
 [    0.337947] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16  
 [    0.337953] pci 0000:00:01.0: setting latency timer to 64  
 [    0.337964] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16  
 [    0.337971] pci 0000:00:1c.0: setting latency timer to 64  
 [    0.337987] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19  
 [    0.337994] pci 0000:00:1c.3: setting latency timer to 64  
 [    0.338005] pci 0000:00:1e.0: setting latency timer to 64  
 [    0.338012] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]  
 [    0.338016] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]  
 [    0.338020] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]  
 [    0.338024] pci_bus 0000:01: resource 1 [mem 0xefd00000-0xefefffff]  
 [    0.338028] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]  
 [    0.338032] pci_bus 0000:0b: resource 0 [io  0x2000-0x2fff]  
 [    0.338036] pci_bus 0000:0b: resource 1 [mem 0xefc00000-0xefcfffff]  
 [    0.338040] pci_bus 0000:0b: resource 2 [mem 0x80000000-0x801fffff 64bit pref]  
 [    0.338044] pci_bus 0000:0c: resource 0 [io  0xd000-0xdfff]  
 [    0.338048] pci_bus 0000:0c: resource 1 [mem 0xefa00000-0xefbfffff]  
 [    0.338052] pci_bus 0000:0c: resource 2 [mem 0xe0000000-0xe01fffff 64bit pref]  
 [    0.338057] pci_bus 0000:03: resource 1 [mem 0xef900000-0xef9fffff]  
 [    0.338061] pci_bus 0000:03: resource 4 [io  0x0000-0xffff]  
 [    0.338064] pci_bus 0000:03: resource 5 [mem 0x00000000-0xffffffff]  
 [    0.338140] NET: Registered protocol family 2  
 [    0.338262] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)  
 [    0.338646] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)  
 [    0.339443] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)  
 [    0.339860] TCP: Hash tables configured (established 131072 bind 65536)  
 [    0.339864] TCP reno registered  
 [    0.339870] UDP hash table entries: 512 (order: 2, 16384 bytes)  
 [    0.339885] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)  
 [    0.340056] NET: Registered protocol family 1  
 [    0.340121] pci 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20  
 [    0.340147] pci 0000:00:1d.0: PCI INT A disabled  
 [    0.340165] pci 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21  
 [    0.340190] pci 0000:00:1d.1: PCI INT B disabled  
 [    0.340207] pci 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22  
 [    0.340231] pci 0000:00:1d.2: PCI INT C disabled  
 [    0.340249] pci 0000:00:1d.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23  
 [    0.340274] pci 0000:00:1d.3: PCI INT D disabled  
 [    0.340288] pci 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20  
 [    0.340325] pci 0000:00:1d.7: PCI INT A disabled  
 [    0.340350] pci 0000:01:00.0: Boot video device  
 [    0.340378] PCI: CLS 64 bytes, default 64  
 [    0.340387] Simple Boot Flag at 0x79 set to 0x1  
 [    0.340955] audit: initializing netlink socket (disabled)  
 [    0.340970] type=2000 audit(1338348277.336:1): initialized  
 [    0.378653] highmem bounce pool size: 64 pages  
 [    0.378662] HugeTLB registered 2 MB page size, pre-allocated 0 pages  
 [    0.392250] VFS: Disk quotas dquot_6.5.2  
 [    0.392372] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)  
 [    0.393340] fuse init (API version 7.17)  
 [    0.393496] msgmni has been set to 1686  
 [    0.394014] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)  
 [    0.394058] io scheduler noop registered  
 [    0.394061] io scheduler deadline registered  
 [    0.394072] io scheduler cfq registered (default)  
 [    0.394266] pcieport 0000:00:01.0: setting latency timer to 64  
 [    0.394318] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X  
 [    0.394397] pcieport 0000:00:1c.0: setting latency timer to 64  
 [    0.394464] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X  
 [    0.394570] pcieport 0000:00:1c.3: setting latency timer to 64  
 [    0.394636] pcieport 0000:00:1c.3: irq 42 for MSI/MSI-X  
 [    0.394783] pci_hotplug: PCI Hot Plug PCI Core version: 0.5  
 [    0.394825] pciehp: PCI Express Hot Plug Controller Driver version: 0.4  
 [    0.394943] intel_idle: MWAIT substates: 0x22220  
 [    0.394946] intel_idle: does not run on family 6 model 14  
 [    0.395352] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared  
 [    0.395718] ACPI: AC Adapter [AC] (on-line)  
 [    0.395850] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0  
 [    0.396229] ACPI: Lid Switch [LID]  
 [    0.396307] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1  
 [    0.396314] ACPI: Power Button [PBTN]  
 [    0.396389] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2  
 [    0.396395] ACPI: Sleep Button [SBTN]  
 [    0.396935] ACPI: acpi_idle registered with cpuidle  
 [    0.403085] thermal LNXTHERM:00: registered as thermal_zone0  
 [    0.403089] ACPI: Thermal Zone [THM] (37 C)  
 [    0.403122] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared  
 [    0.403138] ACPI: Battery Slot [BAT0] (battery present)  
 [    0.403204] ERST: Table is not found!  
 [    0.403207] GHES: HEST is not enabled!  
 [    0.403329] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled  
 [    0.403904] isapnp: Scanning for PnP cards...  
 [    0.440745] ACPI: Battery Slot [BAT0] (battery present)  
 [    0.654102] Freeing initrd memory: 13784k freed  
 [    0.762191] isapnp: No Plug & Play device found  
 [    0.820630] Linux agpgart interface v0.103  
 [    0.823772] brd: module loaded  
 [    0.825254] loop: module loaded  
 [    0.825555] ata_piix 0000:00:1f.2: version 2.13  
 [    0.825591] ata_piix 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17  
 [    0.825600] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]  
 [    0.825661] ata_piix 0000:00:1f.2: setting latency timer to 64  
 [    0.826226] scsi0 : ata_piix  
 [    0.826376] scsi1 : ata_piix  
 [    0.827063] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14  
 [    0.827068] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15  
 [    0.827737] Fixed MDIO Bus: probed  
 [    0.827773] tun: Universal TUN/TAP device driver, 1.6  
 [    0.827776] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>  
 [    0.827922] PPP generic driver version 2.4.2  
 [    0.828139] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver  
 [    0.828166] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20  
 [    0.828187] ehci_hcd 0000:00:1d.7: setting latency timer to 64  
 [    0.828192] ehci_hcd 0000:00:1d.7: EHCI Host Controller  
 [    0.828273] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1  
 [    0.828308] ehci_hcd 0000:00:1d.7: using broken periodic workaround  
 [    0.828324] ehci_hcd 0000:00:1d.7: debug port 1  
 [    0.832214] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported  
 [    0.832241] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xffa80000  
 [    0.848019] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00  
 [    0.848237] hub 1-0:1.0: USB hub found  
 [    0.848244] hub 1-0:1.0: 8 ports detected  
 [    0.848387] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver  
 [    0.848412] uhci_hcd: USB Universal Host Controller Interface driver  
 [    0.848440] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20  
 [    0.848451] uhci_hcd 0000:00:1d.0: setting latency timer to 64  
 [    0.848457] uhci_hcd 0000:00:1d.0: UHCI Host Controller  
 [    0.848530] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2  
 [    0.848563] uhci_hcd 0000:00:1d.0: irq 20, io base 0x0000bf80  
 [    0.848778] hub 2-0:1.0: USB hub found  
 [    0.848784] hub 2-0:1.0: 2 ports detected  
 [    0.848894] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21  
 [    0.848905] uhci_hcd 0000:00:1d.1: setting latency timer to 64  
 [    0.848910] uhci_hcd 0000:00:1d.1: UHCI Host Controller  
 [    0.848986] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3  
 [    0.849033] uhci_hcd 0000:00:1d.1: irq 21, io base 0x0000bf60  
 [    0.849244] hub 3-0:1.0: USB hub found  
 [    0.849250] hub 3-0:1.0: 2 ports detected  
 [    0.849365] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22  
 [    0.849376] uhci_hcd 0000:00:1d.2: setting latency timer to 64  
 [    0.849381] uhci_hcd 0000:00:1d.2: UHCI Host Controller  
 [    0.849458] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4  
 [    0.849505] uhci_hcd 0000:00:1d.2: irq 22, io base 0x0000bf40  
 [    0.849716] hub 4-0:1.0: USB hub found  
 [    0.849722] hub 4-0:1.0: 2 ports detected  
 [    0.849835] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23  
 [    0.849845] uhci_hcd 0000:00:1d.3: setting latency timer to 64  
 [    0.849850] uhci_hcd 0000:00:1d.3: UHCI Host Controller  
 [    0.849930] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5  
 [    0.849977] uhci_hcd 0000:00:1d.3: irq 23, io base 0x0000bf20  
 [    0.850200] hub 5-0:1.0: USB hub found  
 [    0.850207] hub 5-0:1.0: 2 ports detected  
 [    0.850404] usbcore: registered new interface driver libusual  
 [    0.850485] i8042: PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12  
 [    0.853249] serio: i8042 KBD port at 0x60,0x64 irq 1  
 [    0.853259] serio: i8042 AUX port at 0x60,0x64 irq 12  
 [    0.853484] mousedev: PS/2 mouse device common for all mice  
 [    0.853783] rtc_cmos 00:06: RTC can wake from S4  
 [    0.853950] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0  
 [    0.853990] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs  
 [    0.854080] device-mapper: uevent: version 1.0.3  
 [    0.854200] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com  
 [    0.854259] EISA: Probing bus 0 at eisa.0  
 [    0.854329] EISA: Mainboard EW_FFFF detected.  
 [    0.854360] Cannot allocate resource for EISA slot 1  
 [    0.854363] Cannot allocate resource for EISA slot 2  
 [    0.854396] EISA: Detected 0 cards.  
 [    0.854412] cpufreq-nforce2: No nForce2 chipset.  
 [    0.854519] cpuidle: using governor ladder  
 [    0.854689] cpuidle: using governor menu  
 [    0.854693] EFI Variables Facility v0.08 2004-May-17  
 [    0.855161] TCP cubic registered  
 [    0.855368] NET: Registered protocol family 10  
 [    0.856419] NET: Registered protocol family 17  
 [    0.856443] Registering the dns_resolver key type  
 [    0.856488] Using IPI No-Shortcut mode  
 [    0.856728] PM: Hibernation image not present or could not be loaded.  
 [    0.856760] registered taskstats version 1  
 [    0.861987] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3  
 [    0.872108]   Magic number: 12:936:412  
 [    0.872255] rtc_cmos 00:06: setting system clock to 2012-05-30 03:24:38 UTC (1338348278)  
 [    0.873038] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found  
 [    0.873041] EDD information not available.  
 [    0.988575] ata2.00: ATAPI: PHILIPS DVD+/-RW SDVD8820, AD15, max UDMA/33  
 [    0.988864] ata1.00: ATA-7: SAMSUNG HM080II, YE100-15, max UDMA7  
 [    0.988869] ata1.00: 156301488 sectors, multi 8: LBA48 NCQ (depth 0/32)  
 [    0.996491] ata1.00: configured for UDMA/133  
 [    0.996735] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HM080II  YE10 PQ: 0 ANSI: 5  
 [    0.996958] sd 0:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)  
 [    0.997008] sd 0:0:0:0: Attached scsi generic sg0 type 0  
 [    0.997051] sd 0:0:0:0: [sda] Write Protect is off  
 [    0.997056] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00  
 [    0.997096] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA  
 [    1.004336] ata2.00: configured for UDMA/33  
 [    1.009194] scsi 1:0:0:0: CD-ROM            PHILIPS  DVD+-RW SDVD8820 AD15 PQ: 0 ANSI: 5  
 [    1.017474] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray  
 [    1.017479] cdrom: Uniform CD-ROM driver Revision: 3.20  
 [    1.017700] sr 1:0:0:0: Attached scsi CD-ROM sr0  
 [    1.017866] sr 1:0:0:0: Attached scsi generic sg1 type 5  
 [    1.068025]  sda: sda1 sda2 < sda5 >  
 [    1.068820] sd 0:0:0:0: [sda] Attached SCSI disk  
 [    1.068996] Freeing unused kernel memory: 740k freed  
 [    1.069453] Write protecting the kernel text: 5828k  
 [    1.069492] Write protecting the kernel read-only data: 2376k  
 [    1.069495] NX-protecting the kernel data: 4412k  
 [    1.092290] udevd[89]: starting version 175  
 [    1.160056] usb 1-1: new high-speed USB device number 2 using ehci_hcd  
 [    1.229886] firewire_ohci 0000:03:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19  
 [    1.230422] sdhci: Secure Digital Host Controller Interface driver  
 [    1.230425] sdhci: Copyright(c) Pierre Ossman  
 [    1.292149] firewire_ohci: Added fw-ohci device 0000:03:01.0, OHCI v1.10, 4 IR + 4 IT contexts, quirks 0x11  
 [    1.292249] sdhci-pci 0000:03:01.1: SDHCI controller found [1180:0822] (rev 19)  
 [    1.292303] sdhci-pci 0000:03:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18  
 [    1.293382] mmc0: no vmmc regulator found  
 [    1.294429] Registered led device: mmc0::  
 [    1.296599] mmc0: SDHCI controller on PCI [0000:03:01.1] using DMA  
 [    1.471207] Initializing USB Mass Storage driver...  
 [    1.471343] scsi2 : usb-storage 1-1:1.0  
 [    1.471453] usbcore: registered new interface driver usb-storage  
 [    1.471456] USB Mass Storage support registered.  
 [    1.489824] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)  
 [    1.792230] firewire_core: created device fw0: GUID 4a4fc00005088961, S400  
 [    3.460370] scsi 2:0:0:0: Direct-Access     Lexar    USB Flash Drive  1100 PQ: 0 ANSI: 0 CCS  
 [    3.461701] sd 2:0:0:0: Attached scsi generic sg2 type 0  
 [    3.462211] sd 2:0:0:0: [sdb] 122683392 512-byte logical blocks: (62.8 GB/58.5 GiB)  
 [    3.463219] sd 2:0:0:0: [sdb] Write Protect is off  
 [    3.463229] sd 2:0:0:0: [sdb] Mode Sense: 43 00 00 00  
 [    3.464209] sd 2:0:0:0: [sdb] No Caching mode page present  
 [    3.464213] sd 2:0:0:0: [sdb] Assuming drive cache: write through  
 [    3.468218] sd 2:0:0:0: [sdb] No Caching mode page present  
 [    3.468226] sd 2:0:0:0: [sdb] Assuming drive cache: write through  
 [    3.469794]  sdb: sdb1  
 [    3.472955] sd 2:0:0:0: [sdb] No Caching mode page present  
 [    3.472963] sd 2:0:0:0: [sdb] Assuming drive cache: write through  
 [    3.472971] sd 2:0:0:0: [sdb] Attached SCSI removable disk  
 [   20.980292] udevd[322]: starting version 175  
 [   21.050737] lp: driver loaded but no devices found  
 [   21.052139] lib80211: common routines for IEEE802.11 drivers  
 [   21.052145] lib80211_crypt: registered algorithm 'NULL'  
 [   21.066120] [drm] Initialized drm 1.1.0 20060810  
 [   21.118302] Adding 2094076k swap on /dev/sda5.  Priority:-1 extents:1 across:2094076k  
 [   21.135343] wmi: Mapper loaded  
 [   21.137072] [drm] radeon defaulting to kernel modesetting.  
 [   21.137077] [drm] radeon kernel modesetting enabled.  
 [   21.137164] radeon 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16  
 [   21.137172] radeon 0000:01:00.0: setting latency timer to 64  
 [   21.137323] wl: module license 'MIXED/Proprietary' taints kernel.  
 [   21.137327] Disabling lock debugging due to kernel taint  
 [   21.141311] [drm] initializing kernel modesetting (RV515 0x1002:0x7145 0x1028:0x2003).  
 [   21.141349] [drm] register mmio base: 0xEFDF0000  
 [   21.141352] [drm] register mmio size: 65536  
 [   21.141535] ATOM BIOS: M54P  
 [   21.141564] [drm] Generation 2 PCI interface, using max accessible memory  
 [   21.141573] radeon 0000:01:00.0: VRAM: 256M 0x0000000000000000 - 0x000000000FFFFFFF (128M used)  
 [   21.141578] radeon 0000:01:00.0: GTT: 512M 0x0000000010000000 - 0x000000002FFFFFFF  
 [   21.141603] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).  
 [   21.141606] [drm] Driver supports precise vblank timestamp query.  
 [   21.141644] [drm] radeon: irq initialized.  
 [   21.146522] [drm] Detected VRAM RAM=256M, BAR=256M  
 [   21.146527] [drm] RAM width 64bits DDR  
 [   21.167095] [TTM] Zone  kernel: Available graphics memory: 438888 kiB.  
 [   21.167101] [TTM] Zone highmem: Available graphics memory: 1030162 kiB.  
 [   21.167104] [TTM] Initializing pool allocator.  
 [   21.167146] [drm] radeon: 128M of VRAM memory ready  
 [   21.167149] [drm] radeon: 512M of GTT memory ready.  
 [   21.167180] [drm] GART: num cpu pages 131072, num gpu pages 131072  
 [   21.169718] [drm] radeon: 1 quad pipes, 1 z pipes initialized.  
 [   21.169725] NMI: PCI system error (SERR) for reason b1 on CPU 0.  
 [   21.169735] Dazed and confused, but trying to continue  
 [   21.173318] [drm] PCIE GART of 512M enabled (table at 0x0000000000040000).  
 [   21.196731] radeon 0000:01:00.0: WB enabled  
 [   21.199215] [drm] Loading R500 Microcode  
 [   21.224474] wl 0000:0b:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16  
 [   21.224486] wl 0000:0b:00.0: setting latency timer to 64  
 [   21.226982] malloc in abgphy done  
 [   21.227133] eth%d: 5.100.82.38 driver failed with code 21  
 [   21.298153] b43-pci-bridge 0000:0b:00.0: setting latency timer to 64  
 [   21.306891] intel_rng: FWH not detected  
 [   21.313967] r592 0000:03:01.2: PCI INT B -> GSI 18 (level, low) -> IRQ 18  
 [   21.313980] r592 0000:03:01.2: setting latency timer to 64  
 [   21.316174] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x11, vendor 0x4243)  
 [   21.316192] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0A, vendor 0x4243)  
 [   21.316208] ssb: Core 2 found: USB 1.1 Host (cc 0x817, rev 0x03, vendor 0x4243)  
 [   21.316224] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x01, vendor 0x4243)  
 [   21.316654] r592: driver successfully loaded  
 [   21.317214] leds_ss4200: no LED devices found  
 [   21.317811] r852 0000:03:01.3: PCI INT B -> GSI 18 (level, low) -> IRQ 18  
 [   21.317823] r852 0000:03:01.3: setting latency timer to 64  
 [   21.320448] r852: Non dma capable device detected, dma disabled  
 [   21.320471] r852: driver loaded successfully  
 [   21.328785] acpi device:24: registered as cooling_device2  
 [   21.329215] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:21/LNXVIDEO:00/input/input4 
 [   21.336442] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)  
 [   21.336536] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.  
 [   21.360192] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21  
 [   21.360271] snd_hda_intel 0000:00:1b.0: irq 43 for MSI/MSI-X  
 [   21.360314] snd_hda_intel 0000:00:1b.0: setting latency timer to 64  
 [   21.372357] ssb: Sonics Silicon Backplane found on PCI device 0000:0b:00.0  
 [   21.373587] b44 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17  
 [   21.392073] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x07, vendor 0x4243)  
 [   21.392084] ssb: Core 1 found: V90 (cc 0x807, rev 0x03, vendor 0x4243)  
 [   21.392093] ssb: Core 2 found: PCI (cc 0x804, rev 0x0A, vendor 0x4243)  
 [   21.415729] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5  
 [   21.415873] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6  
 [   21.416782] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro  
 [   21.432402] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0  
 [   21.432475] b44: Broadcom 44xx/47xx 10/100 PCI ethernet driver version 2.0  
 [   21.454792] b44 ssb1:0: eth0: Broadcom 44xx/47xx 10/100 PCI ethernet driver 00:15:c5:be:ea:c3  
 [   21.527114] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)  
 [   21.823270] type=1400 audit(1338348299.446:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=596 comm="apparmor_parser"  
 [   21.823944] type=1400 audit(1338348299.446:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=596 comm="apparmor_parser"  
 [   21.824380] type=1400 audit(1338348299.450:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=596 comm="apparmor_parser"  
 [   21.914630] input: Dell WMI hotkeys as /devices/virtual/input/input7  
 [   21.925418] [drm] radeon: ring at 0x0000000010001000  
 [   21.925455] [drm] ring test succeeded in 9 usecs  
 [   21.925700] [drm] radeon: ib pool ready.  
 [   21.926271] [drm] ib test succeeded in 0 usecs  
 [   21.927128] [drm] Radeon Display Connectors  
 [   21.927132] [drm] Connector 0:  
 [   21.927134] [drm]   VGA  
 [   21.927138] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c  
 [   21.927141] [drm]   Encoders:  
 [   21.927144] [drm]     CRT1: INTERNAL_KLDSCP_DAC1  
 [   21.927147] [drm] Connector 1:  
 [   21.927149] [drm]   LVDS  
 [   21.927152] [drm]   DDC: 0x7e30 0x7e30 0x7e34 0x7e34 0x7e38 0x7e38 0x7e3c 0x7e3c  
 [   21.927155] [drm]   Encoders:  
 [   21.927157] [drm]     LCD1: INTERNAL_LVTM1  
 [   21.927160] [drm] Connector 2:  
 [   21.927162] [drm]   S-video  
 [   21.927164] [drm]   Encoders:  
 [   21.927166] [drm]     TV1: INTERNAL_KLDSCP_DAC2  
 [   21.927199] [drm] radeon: power management initialized  
 [   21.974328] init: failsafe main process (687) killed by TERM signal  
 [   21.980039] psmouse serio1: synaptics: Touchpad model: 1, fw: 6.2, id: 0x180b1, caps: 0xa04713/0x200000/0x0  
 [   22.020817] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8  
 [   22.044840] udevd[340]: renamed network interface eth0 to eth1  
 [   22.194822] ppdev: user-space parallel port driver  
 [   22.259131] Bluetooth: Core ver 2.16 
 [   22.259210] NET: Registered protocol family 31  
 [   22.259214] Bluetooth: HCI device and connection manager initialized  
 [   22.259218] Bluetooth: HCI socket layer initialized  
 [   22.259221] Bluetooth: L2CAP socket layer initialized  
 [   22.259658] Bluetooth: SCO socket layer initialized  
 [   22.263234] Bluetooth: BNEP (Ethernet Emulation) ver 1.3  
 [   22.263240] Bluetooth: BNEP filters: protocol multicast  
 [   22.272866] Bluetooth: RFCOMM TTY layer initialized  
 [   22.272874] Bluetooth: RFCOMM socket layer initialized  
 [   22.272877] Bluetooth: RFCOMM ver 1.11  
 [   22.315439] type=1400 audit(1338348299.938:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=772 comm="apparmor_parser"  
 [   22.324643] type=1400 audit(1338348299.950:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=772 comm="apparmor_parser"  
 [   22.395327] type=1400 audit(1338348300.018:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=814 comm="apparmor_parser"  
 [   22.402330] type=1400 audit(1338348300.026:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=815 comm="apparmor_parser"  
 [   22.403291] type=1400 audit(1338348300.026:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=815 comm="apparmor_parser"  
 [   22.403688] type=1400 audit(1338348300.026:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=815 comm="apparmor_parser"  
 [   22.426692] type=1400 audit(1338348300.050:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=820 comm="apparmor_parser"  
 [   22.535508] [drm] fb mappable at 0xD00C0000  
 [   22.535512] [drm] vram apper at 0xD0000000  
 [   22.535515] [drm] size 4096000  
 [   22.535517] [drm] fb depth is 24  
 [   22.535519] [drm]    pitch is 5120  
 [   22.535987] fbcon: radeondrmfb (fb0) is primary device  
 [   22.536694] Console: switching to colour frame buffer device 160x50  
 [   22.536743] fb0: radeondrmfb frame buffer device  
 [   22.536746] drm: registered panic notifier  
 [   22.536757] [drm] Initialized radeon 2.12.0 20080528 for 0000:01:00.0 on minor 0  
 [   22.537925] ADDRCONF(NETDEV_UP): eth1: link is not ready  
 [   22.546027] ADDRCONF(NETDEV_UP): eth1: link is not ready  
 [   25.804212] b44 ssb1:0: eth1: Link is up at 100 Mbps, full duplex  
 [   25.804217] b44 ssb1:0: eth1: Flow control is off for TX and off for RX  
 [   25.804526] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready  
 [   36.424047] eth1: no IPv6 routers present  
 [ 6355.964157] CE: hpet increased min_delta_ns to 20113 nsec  
 ispn@Ispn-U-Lt:~$  
  
``````

6) Network Configuration
                                  ispn@Ispn-U-Lt:~$ sudo lshw -C network  
 [sudo] password for ispn:  
   *-network                
        description: Network controller  
        product: BCM4311 802.11b/g WLAN  
        vendor: Broadcom Corporation  
        physical id: 0  
        bus info: pci@0000:0b:00.0  
        version: 01  
        width: 32 bits  
        clock: 33MHz  
        capabilities: pm msi pciexpress bus_master cap_list  
        configuration: driver=b43-pci-bridge latency=0  
        resources: irq:16 memory:efcfc000-efcfffff  
   *-network  
        description: Ethernet interface  
        product: BCM4401-B0 100Base-TX  
        vendor: Broadcom Corporation  
        physical id: 0  
        bus info: pci@0000:03:00.0  
        logical name: eth1  
        version: 02  
        serial: 00:15:c5:be:ea:c3  
        size: 100Mbit/s  
        capacity: 100Mbit/s  
        width: 32 bits  
        clock: 33MHz  
        capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation  
        configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.100 latency=64 link=yes multicast=yes port=twisted pair speed=100Mbit/s  
        resources: irq:17 memory:ef9fe000-ef9fffff  
 ispn@Ispn-U-Lt:~$  
  
``````

7) Scan for networks
                                  

 ispn@Ispn-U-Lt:~$ iwlist scan  
 lo        Interface doesn't support scanning.  
 

 eth1      Interface doesn't support scanning.  
 

 ispn@Ispn-U-Lt:~$  
  
``````

                                  8) Ubuntu Version


 ispn@Ispn-U-Lt:~$ lsb_release -d
 Description:    Ubuntu 12.04 LTS
  
``````

                                  9) Kernel/architecture


 ispn@Ispn-U-Lt:~$ uname -mr  
 3.2.0-24-generic-pae i686  
  
``````

10) Restarting the network

                                  ispn@Ispn-U-Lt:~$ sudo /etc/init.d/networking restart  
 [sudo] password for ispn:  
  * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces 
  * Reconfiguring network interfaces...                                   [ OK ]  
 ispn@Ispn-U-Lt:~$  
  
```

---

### Post by carl4926 on 2012-05-30
That device should work with b43
So I don't know why you installed 'wl'

---

### Post by carl4926 on 2012-05-30
IIRC most of the problem with these Dell machines is they don't have a proper physical wireless switch.

Having said that, me eeepc doesn't but it works perfectly

I read something recently, I will see if I can find it.

---

### Post by PumaYohn on 2012-05-30
By wl you mean when I put in the terminal "sudo apt-get install bcmwl-kernel-sorce"? I did it because that's what the link the guy showed me told me to do. 

> **gnusci said:**
> Try to follow the steps at

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)
Before I did that, the wireless wasn't working then either.

---

### Post by carl4926 on 2012-05-30
Here is a link to a comment by one of the b43 devs
[http://forums.opensuse.org/english/get-technical-help-here/wireless/475613-vostro-1520-wireless-2.html#post2465593](http://forums.opensuse.org/english/get-technical-help-here/wireless/475613-vostro-1520-wireless-2.html#post2465593)

It looks like you tried all sorts to me, so I'm not sure where you are

---

### Post by PumaYohn on 2012-05-30
Ugh, I can't figure it out either... but that parts not that bad I guess. I have a wireless adapter that I can use instead of trying to use the build in wireless card, but I have a problem with this one too. This is the link to the wireless adapter I have:
[http://www.dlink.com/dwa-121](http://www.dlink.com/dwa-121)

Immediately after I plug it in, my laptop will tell me that there are wireless connections that I can connect to. The problem is that it won't connect to them. I've tried 2 different wireless connections:

1. My neighbors wireless internet is unencrypted. But when I try to connect, it will act like it's trying to connect, but it never does. Instead it will just say "disconnected from the network (or something like that)" instead of fully connecting.

2. My wireless network is encrypted. When I try to connect to mine, it asks me for the password and I type it in correctly, but it will try to connect for a few seconds and then it will ask me for the password again OR or will just say I'm not connected and that I'm offline.

Any ideas on how I can fix this?

---

### Post by PumaYohn on 2012-05-30
I should also mention that *sometimes *the wireless will connect and work (only if I'm connecting to my encrypted network), but it only works for a few seconds and then it stops working all together.

---

### Post by carl4926 on 2012-05-30
Not having encryption doesn't mean you will be able to connect, the router may have access control enabled.

But your situation is odd

---

