---
title: "Internet connection ubuntu 8.10"
date: 2009-01-04
forum: Networking &amp; Wireless
---

### Post by riddz on 2009-01-04
Unable to connect internet on ubountu 8.10 . I have an MSI 
mother board model: MS-7309
network card:NVIDIA nForce Networking Controler
Modem :- NOKIA SIEMENS ADSL MODEM
Model :- C2110

connecting through network card .

---

### Post by wmoore on 2009-01-04
Need more information. Open a terminal and type```
ifconfig
``` then type ```
route
``` and paste the result of both commands here.

You are obviously on the internet on another computer to post here - is this on the same network? Can you ping other machines on the network from the affected machine?

---

### Post by riddz on 2009-01-04
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:db:2a:65:1d  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:dbff:fe2a:651d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:134 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3727 (3.7 KB)  TX bytes:19836 (19.8 KB)
          Interrupt:220 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:486 errors:0 dropped:0 overruns:0 frame:0
          TX packets:486 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:30448 (30.4 KB)  TX bytes:30448 (30.4 KB)


$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         MyDslModem.loca 0.0.0.0         UG    0      0        0 eth0

---

### Post by riddz on 2009-01-04
I have only one pc in my home beside ubuntu i have windows xp

---

### Post by albinootje on 2009-01-04
> **riddz said:**
> I have only one pc in my home beside ubuntu i have windows xp

Can you please post the output of the following :
```

lshw -c network
lspci
sudo dhclient
cat /etc/resolv.conf
route -n
ping -c4 62.108.1.65
dmesg

```
Thanks in advance.

---

### Post by riddz on 2009-01-04
deleted

---

### Post by riddz on 2009-01-04
deleted

---

### Post by riddz on 2009-01-04
i m sorry it got messed up 2gather.... i will give u the results in a suitable size & format

---

### Post by riddz on 2009-01-04
riddz@ubuntu:~$ lshw -c network
WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 46:55:66:5b:e1:46
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
riddz@ubuntu:~$

---

### Post by riddz on 2009-01-04
riddz@ubuntu:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation GeForce 6100 nForce 405 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:09.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
riddz@ubuntu:~$

---

### Post by riddz on 2009-01-04
riddz@ubuntu:~$ sudo dhclient
[sudo] password for riddz: 
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/pan0/46:55:66:5b:e1:46
Sending on   LPF/pan0/46:55:66:5b:e1:46
Listening on LPF/eth0/00:19:db:2a:65:1d
Sending on   LPF/eth0/00:19:db:2a:65:1d
Sending on   Socket/fallback
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 4
DHCPREQUEST of 192.168.1.3 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.3 from 192.168.1.1
bound to 192.168.1.3 -- renewal in 20339 seconds.
riddz@ubuntu:~$

---

### Post by riddz on 2009-01-04
riddz@ubuntu:~$ cat /etc/resolv.conf
domain local.lan
search local.lan
nameserver 192.168.1.1
riddz@ubuntu:~$

---

### Post by riddz on 2009-01-04
riddz@ubuntu:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 pan0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 pan0
riddz@ubuntu:~$

---

### Post by riddz on 2009-01-04
riddz@ubuntu:~$ ping -c4 62.108.1.65
PING 62.108.1.65 (62.108.1.65) 56(84) bytes of data.
From 192.168.1.1 icmp_seq=1 Destination Net Unreachable
From 192.168.1.1 icmp_seq=2 Destination Net Unreachable
From 192.168.1.1 icmp_seq=3 Destination Net Unreachable
From 192.168.1.1 icmp_seq=4 Destination Net Unreachable

--- 62.108.1.65 ping statistics ---
4 packets transmitted, 0 received, +4 errors, 100% packet loss, time 3002ms

riddz@ubuntu:~$

---

### Post by riddz on 2009-01-04
low) -> IRQ 21
[    3.056651] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    3.056654] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    3.056681] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[    3.056707] ehci_hcd 0000:00:02.1: debug port 1
[    3.056712] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[    3.056728] ehci_hcd 0000:00:02.1: irq 21, io mem 0xfeafac00
[    3.232020] usb 1-2: new low speed USB device using ohci_hcd and address 2
[    3.245014] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.245183] usb usb2: configuration #1 chosen from 1 choice
[    3.245210] hub 2-0:1.0: USB hub found
[    3.245219] hub 2-0:1.0: 8 ports detected
[    3.300034] hub 1-0:1.0: unable to enumerate USB device on port 2
[    3.452584] pata_amd 0000:00:06.0: version 0.3.10
[    3.452631] pata_amd 0000:00:06.0: setting latency timer to 64
[    3.452724] scsi0 : pata_amd
[    3.453035] scsi1 : pata_amd
[    3.454410] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    3.454413] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    3.616288] ata1.00: ATAPI: HL-DT-ST DVDRAM GSA-H42N, RL00, max UDMA/66
[    3.616302] ata1: nv_mode_filter: 0x1f39f&0x1f01f->0x1f01f, BIOS=0x1f000 (0xc5000000) ACPI=0x1f01f (30:900:0x11)
[    3.632222] ata1.00: configured for UDMA/66
[    3.632256] ata2: port disabled. ignoring.
[    3.635698] scsi 0:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-H42N  RL00 PQ: 0 ANSI: 5
[    3.640881] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 20
[    3.640893] pata_acpi 0000:00:08.0: PCI INT A -> Link[LSA0] -> GSI 20 (level, low) -> IRQ 20
[    3.640929] pata_acpi 0000:00:08.0: setting latency timer to 64
[    3.640941] pata_acpi 0000:00:08.0: PCI INT A disabled
[    3.648141] sata_nv 0000:00:08.0: version 3.5
[    3.648163] sata_nv 0000:00:08.0: PCI INT A -> Link[LSA0] -> GSI 20 (level, low) -> IRQ 20
[    3.648218] sata_nv 0000:00:08.0: setting latency timer to 64
[    3.648449] scsi2 : sata_nv
[    3.648536] scsi3 : sata_nv
[    3.648715] ata3: SATA max UDMA/133 cmd 0xe400 ctl 0xe080 bmdma 0xd880 irq 20
[    3.648718] ata4: SATA max UDMA/133 cmd 0xe000 ctl 0xdc00 bmdma 0xd888 irq 20
[    3.651132] scsi 0:0:0:0: Attached scsi generic sg0 type 5
[    3.675656] Driver 'sr' needs updating - please use bus_type methods
[    3.687004] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.687010] Uniform CD-ROM driver Revision: 3.20
[    3.687106] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    3.812020] usb 1-2: new low speed USB device using ohci_hcd and address 3
[    4.023167] usb 1-2: configuration #1 chosen from 1 choice
[    4.041591] usbcore: registered new interface driver hiddev
[    4.047360] input: USB-compliant keyboard as /devices/pci0000:00/0000:00:02.0/usb1/1-2/1-2:1.0/input/input1
[    4.048154] input,hidraw0: USB HID v1.10 Keyboard [USB-compliant keyboard] on usb-0000:00:02.0-2
[    4.057543] input: USB-compliant keyboard as /devices/pci0000:00/0000:00:02.0/usb1/1-2/1-2:1.1/input/input2
[    4.057897] input,hiddev96,hidraw1: USB HID v1.10 Mouse [USB-compliant keyboard] on usb-0000:00:02.0-2
[    4.057918] usbcore: registered new interface driver usbhid
[    4.057921] usbhid: v2.6:USB HID core driver
[    4.116043] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    4.124215] ata3.00: ATA-7: WDC WD800BD-00LRA1, 10.01E01, max UDMA/133
[    4.124219] ata3.00: 156301488 sectors, multi 16: LBA48 
[    4.132216] ata3.00: configured for UDMA/133
[    4.600035] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    4.608197] ata4.00: ATA-7: WDC WD800BD-00LRA1, 10.01E01, max UDMA/133
[    4.608199] ata4.00: 156301488 sectors, multi 16: LBA48 
[    4.616210] ata4.00: configured for UDMA/133
[    4.616325] scsi 2:0:0:0: Direct-Access     ATA      WDC WD800BD-00LR 10.0 PQ: 0 ANSI: 5
[    4.616505] scsi 2:0:0:0: Attached scsi generic sg1 type 0
[    4.616581] scsi 3:0:0:0: Direct-Access     ATA      WDC WD800BD-00LR 10.0 PQ: 0 ANSI: 5
[    4.616660] scsi 3:0:0:0: Attached scsi generic sg2 type 0
[    4.637499] Driver 'sd' needs updating - please use bus_type methods
[    4.637629] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    4.637652] sd 2:0:0:0: [sda] Write Protect is off
[    4.637654] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.637691] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.637769] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    4.637789] sd 2:0:0:0: [sda] Write Protect is off
[    4.637791] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.637826] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.637831]  sda: sda1 sda2 < sda5 >
[    4.660770] sd 2:0:0:0: [sda] Attached SCSI disk
[    4.660864] sd 3:0:0:0: [sdb] 156301488 512-byte hardware sectors (80026 MB)
[    4.660886] sd 3:0:0:0: [sdb] Write Protect is off
[    4.660888] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    4.660924] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.660992] sd 3:0:0:0: [sdb] 156301488 512-byte hardware sectors (80026 MB)
[    4.661013] sd 3:0:0:0: [sdb] Write Protect is off
[    4.661016] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    4.661052] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.661056]  sdb: sdb1 sdb2 < sdb5 >
[    4.695904] sd 3:0:0:0: [sdb] Attached SCSI disk
[    5.161418] loop: module loaded
[    5.177773] EXT3-fs: INFO: recovery required on readonly filesystem.
[    5.177778] EXT3-fs: write access will be enabled during recovery.
[    6.023695] kjournald starting.  Commit interval 5 seconds
[    6.023714] EXT3-fs: recovery complete.
[    6.023905] EXT3-fs: mounted filesystem with ordered data mode.
[   11.315370] udevd version 124 started
[   11.871344] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[   11.888042] ACPI: Power Button (FF) [PWRF]
[   11.888190] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4
[   11.920049] ACPI: Power Button (CM) [PWRB]
[   11.938915] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x5000
[   11.938933] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x6000
[   12.365657] parport_pc 00:07: reported by Plug and Play ACPI
[   12.365702] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   12.740739] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   12.770503] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   12.894854] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   12.948194] Linux video capture interface: v2.00
[   13.123316] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 23
[   13.123325] HDA Intel 0000:00:05.0: PCI INT B -> Link[LAZA] -> GSI 23 (level, low) -> IRQ 23
[   13.123365] HDA Intel 0000:00:05.0: setting latency timer to 64
[   13.155583] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   13.157421] saa7130/34: v4l2 driver version 0.2.14 loaded
[   13.192470] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 19
[   13.192484] saa7134 0000:01:09.0: PCI INT A -> Link[LNKB] -> GSI 19 (level, low) -> IRQ 19
[   13.192491] saa7130[0]: found at 0000:01:09.0, rev: 1, irq: 19, latency: 64, mmio: 0xfebffc00
[   13.192498] saa7134: <rant>
[   13.192499] saa7134:  Congratulations!  Your TV card vendor saved a few
[   13.192500] saa7134:  cents for a eeprom, thus your pci board has no
[   13.192502] saa7134:  subsystem ID and I can't identify it automatically
[   13.192503] saa7134: </rant>
[   13.192504] saa7134: I feel better now.  Ok, here are the good news:
[   13.192505] saa7134: You can use the card=<nr> insmod option to specify
[   13.192506] saa7134: which board do you have.  The list:
[   13.192510] saa7134:   card=0 -> UNKNOWN/GENERIC                         
[   13.192514] saa7134:   card=1 -> Proteus Pro [philips reference design]   1131:2001 1131:2001
[   13.192519] saa7134:   card=2 -> LifeView FlyVIDEO3000                    5168:0138 4e42:0138
[   13.192523] saa7134:   card=3 -> LifeView/Typhoon FlyVIDEO2000            5168:0138 4e42:0138
[   13.192528] saa7134:   card=4 -> EMPRESS                                  1131:6752
[   13.192531] saa7134:   card=5 -> SKNet Monster TV                         1131:4e85
[   13.192535] saa7134:   card=6 -> Tevion MD 9717                          
[   13.192538] saa7134:   card=7 -> KNC One TV-Station RDS / Typhoon TV Tune 1131:fe01 1894:fe01
[   13.192543] saa7134:   card=8 -> Terratec Cinergy 400 TV                  153b:1142
[   13.192546] saa7134:   card=9 -> Medion 5044                             
[   13.192550] saa7134:   card=10 -> Kworld/KuroutoShikou SAA7130-TVPCI      
[   13.192553] saa7134:   card=11 -> Terratec Cinergy 600 TV                  153b:1143
[   13.192556] saa7134:   card=12 -> Medion 7134                              16be:0003
[   13.192560] saa7134:   card=13 -> Typhoon TV+Radio 90031                  
[   13.192563] saa7134:   card=14 -> ELSA EX-VISION 300TV                     1048:226b
[   13.192567] saa7134:   card=15 -> ELSA EX-VISION 500TV                     1048:226a
[   13.192571] saa7134:   card=16 -> ASUS TV-FM 7134                          1043:4842 1043:4830 1043:4840
[   13.192576] saa7134:   card=17 -> AOPEN VA1000 POWER                       1131:7133
[   13.192580] saa7134:   card=18 -> BMK MPEX No Tuner                       
[   13.192583] saa7134:   card=19 -> Compro VideoMate TV                      185b:c100
[   13.192586] saa7134:   card=20 -> Matrox CronosPlus                        102b:48d0
[   13.192590] saa7134:   card=21 -> 10MOONS PCI TV CAPTURE CARD              1131:2001
[   13.192594] saa7134:   card=22 -> AverMedia M156 / Medion 2819             1461:a70b
[   13.192598] saa7134:   card=23 -> BMK MPEX Tuner                          
[   13.192601] saa7134:   card=24 -> KNC One TV-Station DVR                   1894:a006
[   13.192604] saa7134:   card=25 -> ASUS TV-FM 7133                          1043:4843
[   13.192608] saa7134:   card=26 -> Pinnacle PCTV Stereo (saa7134)           11bd:002b
[   13.192612] saa7134:   card=27 -> Manli MuchTV M-TV002                    
[   13.192615] saa7134:   card=28 -> Manli MuchTV M-TV001                    
[   13.192618] saa7134:   card=29 -> Nagase Sangyo TransGear 3000TV           1461:050c
[   13.192622] saa7134:   card=30 -> Elitegroup ECS TVP3XP FM1216 Tuner Card( 1019:4cb4
[   13.192626] saa7134:   card=31 -> Elitegroup ECS TVP3XP FM1236 Tuner Card  1019:4cb5
[   13.192629] saa7134:   card=32 -> AVACS SmartTV                           
[   13.192632] saa7134:   card=33 -> AVerMedia DVD EZMaker                    1461:10ff
[   13.192636] saa7134:   card=34 -> Noval Prime TV 7133                     
[   13.192639] saa7134:   card=35 -> AverMedia AverTV Studio 305              1461:2115
[   13.192643] saa7134:   card=36 -> UPMOST PURPLE TV                         12ab:0800
[   13.192646] saa7134:   card=37 -> Items MuchTV Plus / IT-005              
[   13.192649] saa7134:   card=38 -> Terratec Cinergy 200 TV                  153b:1152
[   13.192653] saa7134:   card=39 -> LifeView FlyTV Platinum Mini             5168:0212 4e42:0212 5169:1502
[   13.192658] saa7134:   card=40 -> Compro VideoMate TV PVR/FM               185b:c100
[   13.192662] saa7134:   card=41 -> Compro VideoMate TV Gold+                185b:c100
[   13.192666] saa7134:   card=42 -> Sabrent SBT-TVFM (saa7130)              
[   13.192669] saa7134:   card=43 -> :Zolid Xpert TV7134                     
[   13.192672] saa7134:   card=44 -> Empire PCI TV-Radio LE                  
[   13.192675] saa7134:   card=45 -> Avermedia AVerTV Studio 307              1461:9715
[   13.192679] saa7134:   card=46 -> AVerMedia Cardbus TV/Radio (E500)        1461:d6ee
[   13.192682] saa7134:   card=47 -> Terratec Cinergy 400 mobile              153b:1162
[   13.192686] saa7134:   card=48 -> Terratec Cinergy 600 TV MK3              153b:1158
[   13.192690] saa7134:   card=49 -> Compro VideoMate Gold+ Pal               185b:c200
[   13.192693] saa7134:   card=50 -> Pinnacle PCTV 300i DVB-T + PAL           11bd:002d
[   13.192697] saa7134:   card=51 -> ProVideo PV952                           1540:9524
[   13.192701] saa7134:   card=52 -> AverMedia AverTV/305                     1461:2108
[   13.192704] saa7134:   card=53 -> ASUS TV-FM 7135                          1043:4845
[   13.192708] saa7134:   card=54 -> LifeView FlyTV Platinum FM / Gold        5168:0214 5168:5214 1489:0214 5168:0304
[   13.192714] saa7134:   card=55 -> LifeView FlyDVB-T DUO / MSI TV@nywhere D 5168:0306 4e42:0306
[   13.192718] saa7134:   card=56 -> Avermedia AVerTV 307                     1461:a70a
[   13.192722] saa7134:   card=57 -> Avermedia AVerTV GO 007 FM               1461:f31f
[   13.192725] saa7134:   card=58 -> ADS Tech Instant TV (saa7135)            1421:0350 1421:0351 1421:0370 1421:1370
[   13.192731] saa7134:   card=59 -> Kworld/Tevion V-Stream Xpert TV PVR7134 
[   13.192734] saa7134:   card=60 -> LifeView/Typhoon/Genius FlyDVB-T Duo Car 5168:0502 4e42:0502 1489:0502
[   13.192739] saa7134:   card=61 -> Philips TOUGH DVB-T reference design     1131:2004
[   13.192743] saa7134:   card=62 -> Compro VideoMate TV Gold+II             
[   13.192746] saa7134:   card=63 -> Kworld Xpert TV PVR7134                 
[   13.192749] saa7134:   card=64 -> FlyTV mini Asus Digimatrix               1043:0210
[   13.192752] saa7134:   card=65 -> V-Stream Studio TV Terminator           
[   13.192755] saa7134:   card=66 -> Yuan TUN-900 (saa7135)                  
[   13.192759] saa7134:   card=67 -> Beholder BeholdTV 409 FM                 0000:4091
[   13.192762] saa7134:   card=68 -> GoTView 7135 PCI                         5456:7135
[   13.192766] saa7134:   card=69 -> Philips EUROPA V3 reference design       1131:2004
[   13.192770] saa7134:   card=70 -> Compro Videomate DVB-T300                185b:c900
[   13.192774] saa7134:   card=71 -> Compro Videomate DVB-T200                185b:c901
[   13.192778] saa7134:   card=72 -> RTD Embedded Technologies VFG7350        1435:7350
[   13.192781] saa7134:   card=73 -> RTD Embedded Technologies VFG7330        1435:7330
[   13.192785] saa7134:   card=74 -> LifeView FlyTV Platinum Mini2            14c0:1212
[   13.192789] saa7134:   card=75 -> AVerMedia AVerTVHD MCE A180              1461:1044
[   13.192793] saa7134:   card=76 -> SKNet MonsterTV Mobile                   1131:4ee9
[   13.192796] saa7134:   card=77 -> Pinnacle PCTV 40i/50i/110i (saa7133)     11bd:002e
[   13.192800] saa7134:   card=78 -> ASUSTeK P7131 Dual                       1043:4862 1043:4857
[   13.192804] saa7134:   card=79 -> Sedna/MuchTV PC TV Cardbus TV/Radio (ITO
[   13.192807] saa7134:   card=80 -> ASUS Digimatrix TV                       1043:0210
[   13.192811] saa7134:   card=81 -> Philips Tiger reference design           1131:2018
[   13.192815] saa7134:   card=82 -> MSI TV@Anywhere plus                     1462:6231 1462:8624
[   13.192819] saa7134:   card=83 -> Terratec Cinergy 250 PCI TV              153b:1160
[   13.192823] saa7134:   card=84 -> LifeView FlyDVB Trio                     5168:0319
[   13.192827] saa7134:   card=85 -> AverTV DVB-T 777                         1461:2c05 1461:2c05
[   13.192831] saa7134:   card=86 -> LifeView FlyDVB-T / Genius VideoWonder D 5168:0301 1489:0301
[   13.192835] saa7134:   card=87 -> ADS Instant TV Duo Cardbus PTV331        0331:1421
[   13.192839] saa7134:   card=88 -> Tevion/KWorld DVB-T 220RF                17de:7201
[   13.192843] saa7134:   card=89 -> ELSA EX-VISION 700TV                     1048:226c
[   13.192847] saa7134:   card=90 -> Kworld ATSC110/115                       17de:7350 17de:7352
[   13.192851] saa7134:   card=91 -> AVerMedia A169 B                         1461:7360
[   13.192855] saa7134:   card=92 -> AVerMedia A169 B1                        1461:6360
[   13.192858] saa7134:   card=93 -> Medion 7134 Bridge #2                    16be:0005
[   13.192862] saa7134:   card=94 -> LifeView FlyDVB-T Hybrid Cardbus/MSI TV  5168:3306 5168:3502 5168:3307 4e42:3502
[   13.192868] saa7134:   card=95 -> LifeView FlyVIDEO3000 (NTSC)             5169:0138
[   13.192871] saa7134:   card=96 -> Medion Md8800 Quadro                     16be:0007 16be:0008 16be:000d
[   13.192876] saa7134:   card=97 -> LifeView FlyDVB-S /Acorp TV134DS         5168:0300 4e42:0300
[   13.192880] saa7134:   card=98 -> Proteus Pro 2309                         0919:2003
[   13.192884] saa7134:   card=99 -> AVerMedia TV Hybrid A16AR                1461:2c00
[   13.192888] saa7134:   card=100 -> Asus Europa2 OEM                         1043:4860
[   13.192892] saa7134:   card=101 -> Pinnacle PCTV 310i                       11bd:002f
[   13.192895] saa7134:   card=102 -> Avermedia AVerTV Studio 507              1461:9715
[   13.192899] saa7134:   card=103 -> Compro Videomate DVB-T200A              
[   13.192902] saa7134:   card=104 -> Hauppauge WinTV-HVR1110 DVB-T/Hybrid     0070:6700 0070:6701 0070:6702 0070:6703 0070:6704 0070:6705
[   13.192909] saa7134:   card=105 -> Terratec Cinergy HT PCMCIA               153b:1172
[   13.192913] saa7134:   card=106 -> Encore ENLTV                             1131:2342 1131:2341 3016:2344
[   13.192918] saa7134:   card=107 -> Encore ENLTV-FM                          1131:230f
[   13.192921] saa7134:   card=108 -> Terratec Cinergy HT PCI                  153b:1175
[   13.192925] saa7134:   card=109 -> Philips Tiger - S Reference design      
[   13.192928] saa7134:   card=110 -> Avermedia M102                           1461:f31e
[   13.192932] saa7134:   card=111 -> ASUS P7131 4871                          1043:4871
[   13.192936] saa7134:   card=112 -> ASUSTeK P7131 Hybrid                     1043:4876
[   13.192940] saa7134:   card=113 -> Elitegroup ECS TVP3XP FM1246 Tuner Card  1019:4cb6
[   13.192943] saa7134:   card=114 -> KWorld DVB-T 210                         17de:7250
[   13.192947] saa7134:   card=115 -> Sabrent PCMCIA TV-PCB05                  0919:2003
[   13.192951] saa7134:   card=116 -> 10MOONS TM300 TV Card                    1131:2304
[   13.192955] saa7134:   card=117 -> Avermedia Super 007                      1461:f01d
[   13.192958] saa7134:   card=118 -> Beholder BeholdTV 401                    0000:4016
[   13.192962] saa7134:   card=119 -> Beholder BeholdTV 403                    0000:4036
[   13.192966] saa7134:   card=120 -> Beholder BeholdTV 403 FM                 0000:4037
[   13.192969] saa7134:   card=121 -> Beholder BeholdTV 405                    0000:4050
[   13.192973] saa7134:   card=122 -> Beholder BeholdTV 405 FM                 0000:4051
[   13.192977] saa7134:   card=123 -> Beholder BeholdTV 407                    0000:4070
[   13.192980] saa7134:   card=124 -> Beholder BeholdTV 407 FM                 0000:4071
[   13.192984] saa7134:   card=125 -> Beholder BeholdTV 409                    0000:4090
[   13.192988] saa7134:   card=126 -> Beholder BeholdTV 505 FM/RDS             0000:5051 0000:505b 5ace:5050
[   13.192993] saa7134:   card=127 -> Beholder BeholdTV 507 FM/RDS / BeholdTV  0000:5071 0000:507b 5ace:5070 5ace:5090
[   13.192998] saa7134:   card=128 -> Beholder BeholdTV Columbus TVFM          0000:5201
[   13.193002] saa7134:   card=129 -> Beholder BeholdTV 607 / BeholdTV 609     5ace:6070 5ace:6071 5ace:6072 5ace:6073 5ace:6090 5ace:6091 5ace:6092 5ace:6093
[   13.193010] saa7134:   card=130 -> Beholder BeholdTV M6                     5ace:6190
[   13.193014] saa7134:   card=131 -> Twinhan Hybrid DTV-DVB 3056 PCI          1822:0022
[   13.193017] saa7134:   card=132 -> Genius TVGO AM11MCE                     
[   13.193020] saa7134:   card=133 -> NXP Snake DVB-S reference design        
[   13.193024] saa7134:   card=134 -> Medion/Creatix CTX953 Hybrid             16be:0010
[   13.193027] saa7134:   card=135 -> MSI TV@nywhere A/D v1.1                  1462:8625
[   13.193031] saa7134:   card=136 -> AVerMedia Cardbus TV/Radio (E506R)       1461:f436
[   13.193035] saa7134:   card=137 -> AVerMedia Hybrid TV/Radio (A16D)         1461:f936
[   13.193039] saa7134:   card=138 -> Avermedia M115                           1461:a836
[   13.193042] saa7134:   card=139 -> Compro VideoMate T750                    185b:c900
[   13.193046] saa7134:   card=140 -> Avermedia DVB-S Pro A700                 1461:a7a1
[   13.193050] saa7134:   card=141 -> Avermedia DVB-S Hybrid+FM A700           1461:a7a2
[   13.193054] saa7134:   card=142 -> Beholder BeholdTV H6                     5ace:6290
[   13.193057] saa7134:   card=143 -> Beholder BeholdTV M63                    5ace:6191
[   13.193061] saa7134:   card=144 -> Beholder BeholdTV M6 Extra               5ace:6193
[   13.193065] saa7134:   card=145 -> AVerMedia MiniPCI DVB-T Hybrid M103      1461:f636
[   13.193069] saa7134:   card=146 -> ASUSTeK P7131 Analog                    
[   13.193072] saa7130[0]: subsystem: 1131:0000, board: UNKNOWN/GENERIC [card=0,autodetected]
[   13.193091] saa7130[0]: board init: gpio is 3e500
[   13.296207] saa7130[0]: Huh, no eeprom present (err=-5)?
[   13.296445] saa7130[0]: registered device video0 [v4l2]
[   13.296481] saa7130[0]: registered device vbi0
[   13.422141] saa7134 ALSA driver for DMA sound loaded
[   13.422178] saa7130[0]/alsa: saa7130[0] at 0xfebffc00 irq 19 registered as card -2
[   13.615741] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input6
[   15.342498] lp0: using parport0 (interrupt-driven).
[   15.974329] EXT3 FS on loop0, internal journal
[   27.654326] Adding 976552k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:1 across:976552k
[   27.754363] type=1505 audit(1231113775.521:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4426
[   27.935569] type=1505 audit(1231113775.701:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4431
[   27.935815] type=1505 audit(1231113775.701:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4431
[   28.029454] ip_tables: (C) 2000-2006 Netfilter Core Team
[   28.481586] ACPI: WMI: Mapper loaded
[   28.758083] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ processors (2 cpu cores) (version 2.20.00)
[   28.758644] powernow-k8: ACPI Processor support is required for SMP systems but is absent. Please load the ACPI Processor module before starting this driver.
[   28.758788] powernow-k8: ACPI Processor support is required for SMP systems but is absent. Please load the ACPI Processor module before starting this driver.
[   29.268395] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   29.317171] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   29.317181] apm: disabled - APM is not SMP safe.
[   29.431520] ppdev: user-space parallel port driver
[   30.718554] Bluetooth: Core ver 2.13
[   30.718781] NET: Registered protocol family 31
[   30.718786] Bluetooth: HCI device and connection manager initialized
[   30.718790] Bluetooth: HCI socket layer initialized
[   30.731231] Bluetooth: L2CAP ver 2.11
[   30.731240] Bluetooth: L2CAP socket layer initialized
[   30.741099] Bluetooth: SCO (Voice Link) ver 0.6
[   30.741108] Bluetooth: SCO socket layer initialized
[   30.753066] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   30.753074] Bluetooth: BNEP filters: protocol multicast
[   30.760285] Bluetooth: RFCOMM socket layer initialized
[   30.760304] Bluetooth: RFCOMM TTY layer initialized
[   30.760306] Bluetooth: RFCOMM ver 1.10
[   30.789504] Bridge firewalling registered
[   30.789691] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   35.017365] NET: Registered protocol family 17
[  122.416361] ppdev0: registered pardevice
[  122.464207] ppdev0: unregistered pardevice
[  122.490227] ppdev0: registered pardevice
[  122.536249] ppdev0: unregistered pardevice
[  122.568196] type=1503 audit(1231113870.334:5): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/5949/net/" pid=5949 profile="/usr/sbin/cupsd"
[  123.590180] type=1503 audit(1231113871.357:6): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/5953/net/" pid=5953 profile="/usr/sbin/cupsd"
[  123.654968] NET: Registered protocol family 10
[  123.655610] lo: Disabled Privacy Extensions
[  123.657047] type=1503 audit(1231113871.425:7): operation="socket_create" family="ax25" sock_type="dgram" protocol=0 pid=5953 profile="/usr/sbin/cupsd"
[  123.657064] type=1503 audit(1231113871.425:8): operation="socket_create" family="netrom" sock_type="seqpacket" protocol=0 pid=5953 profile="/usr/sbin/cupsd"
[  123.657072] type=1503 audit(1231113871.425:9): operation="socket_create" family="rose" sock_type="dgram" protocol=0 pid=5953 profile="/usr/sbin/cupsd"
[  123.657078] type=1503 audit(1231113871.425:10): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=5953 profile="/usr/sbin/cupsd"
[  123.657085] type=1503 audit(1231113871.425:11): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=5953 profile="/usr/sbin/cupsd"
[  123.657092] type=1503 audit(1231113871.425:12): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=5953 profile="/usr/sbin/cupsd"
[  123.657099] type=1503 audit(1231113871.425:13): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=5953 profile="/usr/sbin/cupsd"
[  123.657105] type=1503 audit(1231113871.425:14): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=5953 profile="/usr/sbin/cupsd"
[  124.782383] ppdev0: registered pardevice
[  124.828024] ppdev0: unregistered pardevice
[  133.896012] eth0: no IPv6 routers present
[  249.512012] pan0: no IPv6 routers present
riddz@ubuntu:~$ riddz@ubuntu:~$ ping -c4 62.108.1.65
bash: riddz@ubuntu:~$: command not found
riddz@ubuntu:~$ PING 62.108.1.65 (62.108.1.65) 56(84) bytes of data.
bash: syntax error near unexpected token `('
riddz@ubuntu:~$ From 192.168.1.1 icmp_seq=1 Destination Net Unreachable
bash: From: command not found
riddz@ubuntu:~$ From 192.168.1.1 icmp_seq=2 Destination Net Unreachable
bash: From: command not found
riddz@ubuntu:~$ From 192.168.1.1 icmp_seq=3 Destination Net Unreachable
bash: From: command not found
riddz@ubuntu:~$ From 192.168.1.1 icmp_seq=4 Destination Net Unreachable
bash: From: command not found
riddz@ubuntu:~$ 
riddz@ubuntu:~$ --- 62.108.1.65 ping statistics ---
bash: ---: command not found
riddz@ubuntu:~$ 4 packets transmitted, 0 received, +4 errors, 100% packet loss, time 3002ms
bash: 4: command not found
riddz@ubuntu:~$ 
riddz@ubuntu:~$ riddz@ubuntu:~$ 
bash: riddz@ubuntu:~$: command not found
riddz@ubuntu:~$

---

### Post by riddz on 2009-01-04
i think thats all u wanted...

---

### Post by albinootje on 2009-01-04
> **riddz said:**
> riddz@ubuntu:~$ ping -c4 62.108.1.65
PING 62.108.1.65 (62.108.1.65) 56(84) bytes of data.
From 192.168.1.1 icmp_seq=1 Destination Net Unreachable
From 192.168.1.1 icmp_seq=2 Destination Net Unreachable
From 192.168.1.1 icmp_seq=3 Destination Net Unreachable
From 192.168.1.1 icmp_seq=4 Destination Net Unreachable


Thanks!

Pan0 is about bluetooth apparently, you get an address, but no internet at all.

Strange thing is that your ethernet device is not showing up at all.
Is it enabled in the BIOS or not ?
According to a quick search for your Motherboard type, it should be some Realtek card.

---

### Post by riddz on 2009-01-04
> **albinootje said:**
> Thanks!

Pan0 is about bluetooth apparently, you get an address, but no internet at all.

Strange thing is that your ethernet device is not showing up at all.
Is it enabled in the BIOS or not ?
According to a quick search for your Motherboard type, it should be some Realtek card.

yaa realtek is my sound driver or audio device...

i dont knw about the ethernet connection bt i am running the internet cunnection through LAN in windows...

---

### Post by riddz on 2009-01-04
another thing is that when i turn off or restart ubuntu a blck screen much like a console comes up... u can only tipe in it. hehe!

then i hav 2 shut down my pc manually...

---

### Post by riddz on 2009-01-04
1 thing i for got i have to put the user name & password provided by the internet connection provider in order to log in to a internet connection

---

### Post by albinootje on 2009-01-04
> **riddz said:**
> yaa realtek is my sound driver or audio device...

i dont knw about the ethernet connection bt i am running the internet cunnection through LAN in windows...

Okay, can you try this first :

[http://wiki.archlinux.org/index.php/Configuring_network#Realtek_No_Link_.2F_WOL_issue](http://wiki.archlinux.org/index.php/Configuring_network#Realtek_No_Link_.2F_WOL_issue)

Method 2.

---

### Post by albinootje on 2009-01-04
> **riddz said:**
> another thing is that when i turn off or restart ubuntu a blck screen much like a console comes up... u can only tipe in it. hehe!

then i hav 2 shut down my pc manually...

That sounds like a power-management issue.
Try searching in a search-engine for the word ubuntu (or linux) and the motherboard type you have.

---

### Post by riddz on 2009-01-04
> **albinootje said:**
> Okay, can you try this first :

[http://wiki.archlinux.org/index.php/Configuring_network#Realtek_No_Link_.2F_WOL_issue](http://wiki.archlinux.org/index.php/Configuring_network#Realtek_No_Link_.2F_WOL_issue)

Method 2.

thanks!
 i did as instructed
but its not realtec its: NVDIA nForce Networking Controller

---

### Post by riddz on 2009-01-04
it was allready enabled...

---

### Post by riddz on 2009-01-04
i loaded ubuntu 7.10 earlyer... it didnt hav the problem of turning on or off.......or restart!

---

### Post by albinootje on 2009-01-04
> **riddz said:**
> thanks!
 i did as instructed
but its not realtec its: NVDIA nForce Networking Controller

I re read your posting, and in one of the first comments, there is a eth0 with an ip-address, in your later comments there's only pan0 :|

And did you have a working internet connection with 7.10 ?

---

### Post by riddz on 2009-01-04
> **albinootje said:**
> I re read your posting, and in one of the first comments, there is a eth0 with an ip-address, in your later comments there's only pan0 :|

And did you have a working internet connection with 7.10 ?

no i wasnt able to establish a connection even then

---

