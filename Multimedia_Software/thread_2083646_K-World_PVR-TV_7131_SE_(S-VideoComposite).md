---
title: "K-World PVR-TV 7131 SE (S-Video/Composite)"
date: 2012-11-13
forum: Multimedia Software
---

### Post by M1hai on 2012-11-13
Hello I'm new to Ubuntu and ubuntuforums.org. I am using Ubuntu 12.10 32-bit and it is awesome (besides some error reports that appear). OK so myproblem is: I have installed a tv tuner: K-World PCI Analog TV Card (PVR-TV 7131 SE) and I think it uses saa7134. Ubuntu doesn't recognize my tv card (I've tried all methods I could find on the intrnet: NOTHING works)

I am posting some reports:

sudo lspci -v: > 00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device 823b
	Flags: bus master, fast devsel, latency 0
	Capabilities: [e0] Vendor Specific Information: Len=09 <?>

00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: de000000-dfcfffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dbffffff
	Capabilities: [88] Subsystem: Intel Corporation Device 0000
	Capabilities: [80] Power Management version 3
	Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [a0] Express Root Port (Slot+), MSI 00
	Capabilities: [100] Virtual Channel
	Capabilities: [140] Root Complex Link
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. Device 81eb
	Flags: bus master, medium devsel, latency 0, IRQ 22
	I/O ports at c880 [size=32]
	Kernel driver in use: uhci_hcd

00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. Device 81eb
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at cc00 [size=32]
	Kernel driver in use: uhci_hcd

00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02) (prog-if 20 [EHCI])
	Subsystem: ASUSTeK Computer Inc. Device 81eb
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at ddfffc00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device 8249
	Flags: bus master, fast devsel, latency 0, IRQ 43
	Memory at ddff8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel
	Capabilities: [130] Root Complex Link
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 00001000-00001fff
	Memory behind bridge: dfe00000-dfefffff
	Prefetchable memory behind bridge: 00000000dc000000-00000000dc1fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: ASUSTeK Computer Inc. Device 81eb
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel
	Capabilities: [180] Root Complex Link
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: dfd00000-dfdfffff
	Prefetchable memory behind bridge: 00000000dc200000-00000000dc3fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: ASUSTeK Computer Inc. Device 81eb
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel
	Capabilities: [180] Root Complex Link
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. Device 81eb
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at c400 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. Device 81eb
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at c480 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. Device 81eb
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at c800 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02) (prog-if 20 [EHCI])
	Subsystem: ASUSTeK Computer Inc. Device 81eb
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at ddfff800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
	Memory behind bridge: dff00000-dfffffff
	Capabilities: [50] Subsystem: ASUSTeK Computer Inc. Device 81eb

00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device 81eb
	Flags: bus master, medium devsel, latency 0
	Capabilities: [e0] Vendor Specific Information: Len=0c <?>
	Kernel driver in use: lpc_ich
	Kernel modules: lpc_ich

00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA Controller [IDE mode] (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: ASUSTeK Computer Inc. Device 81eb
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 18
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at ff90 [size=16]
	I/O ports at ffa0 [size=16]
	Capabilities: [70] Power Management version 3
	Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device 81eb
	Flags: medium devsel, IRQ 5
	Memory at ddfff400 (32-bit, non-prefetchable) [size=256]
	I/O ports at 0400 [size=32]
	Kernel modules: i2c-i801

00:1f.5 IDE interface: Intel Corporation 82801HR/HO/HH (ICH8R/DO/DH) 2 port SATA Controller [IDE mode] (rev 02) (prog-if 85 [Master SecO PriO])
	Subsystem: ASUSTeK Computer Inc. Device 81eb
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 18
	I/O ports at c080 [size=8]
	I/O ports at c000 [size=4]
	I/O ports at bc00 [size=8]
	I/O ports at b880 [size=4]
	I/O ports at b800 [size=16]
	I/O ports at b480 [size=16]
	Capabilities: [70] Power Management version 3
	Kernel driver in use: ata_piix

01:00.0 VGA compatible controller: NVIDIA Corporation GF108 [GeForce GT 430] (rev a1) (prog-if 00 [VGA controller])
	Subsystem: Giga-byte Technology Device 3505
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at de000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=128M]
	Memory at da000000 (64-bit, prefetchable) [size=32M]
	I/O ports at dc00 [size=128]
	[virtual] Expansion ROM at dfc00000 [disabled] [size=512K]
	Capabilities: [60] Power Management version 3
	Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
	Capabilities: [78] Express Endpoint, MSI 00
	Capabilities: [b4] Vendor Specific Information: Len=14 <?>
	Capabilities: [100] Virtual Channel
	Capabilities: [128] Power Budgeting <?>
	Capabilities: [600] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>
	Kernel driver in use: nvidia
	Kernel modules: nvidia_current, nouveau, nvidiafb

01:00.1 Audio device: NVIDIA Corporation GF108 High Definition Audio Controller (rev a1)
	Subsystem: Giga-byte Technology Device 3505
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at dfcfc000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [60] Power Management version 3
	Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
	Capabilities: [78] Express Endpoint, MSI 00
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel

02:00.0 IDE interface: JMicron Technology Corp. JMB368 IDE controller (prog-if 85 [Master SecO PriO])
	Subsystem: ASUSTeK Computer Inc. Device 827e
	Flags: bus master, fast devsel, latency 0, IRQ 17
	I/O ports at ec00 [size=8]
	I/O ports at e880 [size=4]
	I/O ports at e800 [size=8]
	I/O ports at e480 [size=4]
	I/O ports at e400 [size=16]
	Expansion ROM at dfdf0000 [disabled] [size=64K]
	Capabilities: [68] Power Management version 2
	Capabilities: [50] Express Legacy Endpoint, MSI 01
	Capabilities: [70] MSI: Enable- Count=1/1 Maskable- 64bit-
	Kernel driver in use: pata_jmicron
	Kernel modules: pata_jmicron

03:00.0 Ethernet controller: Atheros Communications Inc. Attansic L1 Gigabit Ethernet (rev b0)
	Subsystem: ASUSTeK Computer Inc. P5KPL-VM Motherboard
	Flags: bus master, fast devsel, latency 0, IRQ 44
	Memory at dfec0000 (64-bit, non-prefetchable) [size=256K]
	Expansion ROM at dfea0000 [disabled] [size=128K]
	Capabilities: [40] Power Management version 2
	Capabilities: [48] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [58] Express Endpoint, MSI 00
	Capabilities: [6c] Vital Product Data
	Capabilities: [100] Advanced Error Reporting
	Kernel driver in use: atl1
	Kernel modules: atl1

04:01.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
	Subsystem: KWorld Computer Co. Ltd. Device 7136
	Flags: bus master, medium devsel, latency 64, IRQ 21
	Memory at dffff800 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [40] Power Management version 2
	Kernel driver in use: saa7134
	Kernel modules: saa7134


dmesg: > [   11.087063] Bluetooth: HCI device and connection manager initialized
[   11.087065] Bluetooth: HCI socket layer initialized
[   11.087066] Bluetooth: L2CAP socket layer initialized
[   11.087071] Bluetooth: SCO socket layer initialized
[   11.089093] microcode: CPU0 sig=0x1067a, pf=0x1, revision=0xa07
[   11.089338] usblp 2-3:1.1: usblp0: USB Bidirectional printer dev 4 if 1 alt 0 proto 2 vid 0x03F0 pid 0x8711
[   11.089383] usbcore: registered new interface driver usblp
[   11.090020] usbcore: registered new interface driver btusb
[   11.090941] Linux video capture interface: v2.00
[   11.091748] uvcvideo: Found UVC 1.00 device Trust Webcam (0c45:62c0)
[   11.109088] input: Trust Webcam as /devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1:1.0/input/input3
[   11.109187] usbcore: registered new interface driver uvcvideo
[   11.109189] USB Video Class driver (1.1.1)
[   11.185707] parport_pc 00:06: reported by Plug and Play ACPI
[   11.185832] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   11.223297] saa7130/34: v4l2 driver version 0, 2, 17 loaded
[   11.223347] saa7133[0]: found at 0000:04:01.0, rev: 209, irq: 21, latency: 64, mmio: 0xdffff800
[   11.223352] saa7134: <rant>
[   11.223352] saa7134:  Congratulations!  Your TV card vendor saved a few
[   11.223352] saa7134:  cents for a eeprom, thus your pci board has no
[   11.223352] saa7134:  subsystem ID and I can't identify it automatically
[   11.223352] saa7134: </rant>
[   11.223352] saa7134: I feel better now.  Ok, here are the good news:
[   11.223352] saa7134: You can use the card=<nr> insmod option to specify
[   11.223352] saa7134: which board do you have.  The list:
[   11.223357] saa7134:   card=0 -> UNKNOWN/GENERIC                         
[   11.223359] saa7134:   card=1 -> Proteus Pro [philips reference design]   1131:2001 1131:2001
[   11.223363] saa7134:   card=2 -> LifeView FlyVIDEO3000                    5168:0138 4e42:0138
[   11.223366] saa7134:   card=3 -> LifeView/Typhoon FlyVIDEO2000            5168:0138 4e42:0138
[   11.223369] saa7134:   card=4 -> EMPRESS                                  1131:6752
[   11.223371] saa7134:   card=5 -> SKNet Monster TV                         1131:4e85
[   11.223374] saa7134:   card=6 -> Tevion MD 9717                          
[   11.223376] saa7134:   card=7 -> KNC One TV-Station RDS / Typhoon TV Tune 1131:fe01 1894:fe01
[   11.223379] saa7134:   card=8 -> Terratec Cinergy 400 TV                  153b:1142
[   11.223381] saa7134:   card=9 -> Medion 5044                             
[   11.223383] saa7134:   card=10 -> Kworld/KuroutoShikou SAA7130-TVPCI      
[   11.223385] saa7134:   card=11 -> Terratec Cinergy 600 TV                  153b:1143
[   11.223388] saa7134:   card=12 -> Medion 7134                              16be:0003 16be:5000
[   11.223391] saa7134:   card=13 -> Typhoon TV+Radio 90031                  
[   11.223392] saa7134:   card=14 -> ELSA EX-VISION 300TV                     1048:226b
[   11.223395] saa7134:   card=15 -> ELSA EX-VISION 500TV                     1048:226a
[   11.223397] saa7134:   card=16 -> ASUS TV-FM 7134                          1043:4842 1043:4830 1043:4840
[   11.223401] saa7134:   card=17 -> AOPEN VA1000 POWER                       1131:7133
[   11.223404] saa7134:   card=18 -> BMK MPEX No Tuner                       
[   11.223406] saa7134:   card=19 -> Compro VideoMate TV                      185b:c100
[   11.223408] saa7134:   card=20 -> Matrox CronosPlus                        102b:48d0
[   11.223411] saa7134:   card=21 -> 10MOONS PCI TV CAPTURE CARD              1131:2001
[   11.223413] saa7134:   card=22 -> AverMedia M156 / Medion 2819             1461:a70b
[   11.223415] saa7134:   card=23 -> BMK MPEX Tuner                          
[   11.223417] saa7134:   card=24 -> KNC One TV-Station DVR                   1894:a006
[   11.223420] saa7134:   card=25 -> ASUS TV-FM 7133                          1043:4843
[   11.223422] saa7134:   card=26 -> Pinnacle PCTV Stereo (saa7134)           11bd:002b
[   11.223425] saa7134:   card=27 -> Manli MuchTV M-TV002                    
[   11.223427] saa7134:   card=28 -> Manli MuchTV M-TV001                    
[   11.223429] saa7134:   card=29 -> Nagase Sangyo TransGear 3000TV           1461:050c
[   11.223431] saa7134:   card=30 -> Elitegroup ECS TVP3XP FM1216 Tuner Card( 1019:4cb4
[   11.223433] saa7134:   card=31 -> Elitegroup ECS TVP3XP FM1236 Tuner Card  1019:4cb5
[   11.223436] saa7134:   card=32 -> AVACS SmartTV                           
[   11.223438] saa7134:   card=33 -> AVerMedia DVD EZMaker                    1461:10ff
[   11.223440] saa7134:   card=34 -> Noval Prime TV 7133                     
[   11.223442] saa7134:   card=35 -> AverMedia AverTV Studio 305              1461:2115
[   11.223444] saa7134:   card=36 -> UPMOST PURPLE TV                         12ab:0800
[   11.223447] saa7134:   card=37 -> Items MuchTV Plus / IT-005              
[   11.223449] saa7134:   card=38 -> Terratec Cinergy 200 TV                  153b:1152
[   11.223451] saa7134:   card=39 -> LifeView FlyTV Platinum Mini             5168:0212 4e42:0212 5169:1502
[   11.223466] saa7134:   card=40 -> Compro VideoMate TV PVR/FM               185b:c100
[   11.223469] saa7134:   card=41 -> Compro VideoMate TV Gold+                185b:c100
[   11.223471] saa7134:   card=42 -> Sabrent SBT-TVFM (saa7130)              
[   11.223473] saa7134:   card=43 -> :Zolid Xpert TV7134                     
[   11.223475] saa7134:   card=44 -> Empire PCI TV-Radio LE                  
[   11.223477] saa7134:   card=45 -> Avermedia AVerTV Studio 307              1461:9715
[   11.223479] saa7134:   card=46 -> AVerMedia Cardbus TV/Radio (E500)        1461:d6ee
[   11.223481] saa7134:   card=47 -> Terratec Cinergy 400 mobile              153b:1162
[   11.223484] saa7134:   card=48 -> Terratec Cinergy 600 TV MK3              153b:1158
[   11.223486] saa7134:   card=49 -> Compro VideoMate Gold+ Pal               185b:c200
[   11.223489] saa7134:   card=50 -> Pinnacle PCTV 300i DVB-T + PAL           11bd:002d
[   11.223491] saa7134:   card=51 -> ProVideo PV952                           1540:9524
[   11.223493] saa7134:   card=52 -> AverMedia AverTV/305                     1461:2108
[   11.223496] saa7134:   card=53 -> ASUS TV-FM 7135                          1043:4845
[   11.223498] saa7134:   card=54 -> LifeView FlyTV Platinum FM / Gold        5168:0214 5168:5214 1489:0214 5168:0304
[   11.223503] saa7134:   card=55 -> LifeView FlyDVB-T DUO / MSI TV@nywhere D 5168:0306 4e42:0306
[   11.223506] saa7134:   card=56 -> Avermedia AVerTV 307                     1461:a70a
[   11.223508] saa7134:   card=57 -> Avermedia AVerTV GO 007 FM               1461:f31f
[   11.223510] saa7134:   card=58 -> ADS Tech Instant TV (saa7135)            1421:0350 1421:0351 1421:0370 1421:1370
[   11.223515] saa7134:   card=59 -> Kworld/Tevion V-Stream Xpert TV PVR7134 
[   11.223516] saa7134:   card=60 -> LifeView/Typhoon/Genius FlyDVB-T Duo Car 5168:0502 4e42:0502 1489:0502
[   11.223520] saa7134:   card=61 -> Philips TOUGH DVB-T reference design     1131:2004
[   11.223523] saa7134:   card=62 -> Compro VideoMate TV Gold+II             
[   11.223524] saa7134:   card=63 -> Kworld Xpert TV PVR7134                 
[   11.223526] saa7134:   card=64 -> FlyTV mini Asus Digimatrix               1043:0210
[   11.223529] saa7134:   card=65 -> V-Stream Studio TV Terminator           
[   11.223530] saa7134:   card=66 -> Yuan TUN-900 (saa7135)                  
[   11.223532] saa7134:   card=67 -> Beholder BeholdTV 409 FM                 0000:4091
[   11.223535] saa7134:   card=68 -> GoTView 7135 PCI                         5456:7135
[   11.223537] saa7134:   card=69 -> Philips EUROPA V3 reference design       1131:2004
[   11.223539] saa7134:   card=70 -> Compro Videomate DVB-T300                185b:c900
[   11.223542] saa7134:   card=71 -> Compro Videomate DVB-T200                185b:c901
[   11.223544] saa7134:   card=72 -> RTD Embedded Technologies VFG7350        1435:7350
[   11.223547] saa7134:   card=73 -> RTD Embedded Technologies VFG7330        1435:7330
[   11.223549] saa7134:   card=74 -> LifeView FlyTV Platinum Mini2            14c0:1212
[   11.223551] saa7134:   card=75 -> AVerMedia AVerTVHD MCE A180              1461:1044
[   11.223554] saa7134:   card=76 -> SKNet MonsterTV Mobile                   1131:4ee9
[   11.223556] saa7134:   card=77 -> Pinnacle PCTV 40i/50i/110i (saa7133)     11bd:002e
[   11.223559] saa7134:   card=78 -> ASUSTeK P7131 Dual                       1043:4862
[   11.223561] saa7134:   card=79 -> Sedna/MuchTV PC TV Cardbus TV/Radio (ITO
[   11.223563] saa7134:   card=80 -> ASUS Digimatrix TV                       1043:0210
[   11.223565] saa7134:   card=81 -> Philips Tiger reference design           1131:2018
[   11.223568] saa7134:   card=82 -> MSI TV@Anywhere plus                     1462:6231 1462:8624
[   11.223571] saa7134:   card=83 -> Terratec Cinergy 250 PCI TV              153b:1160
[   11.223573] saa7134:   card=84 -> LifeView FlyDVB Trio                     5168:0319
[   11.223576] saa7134:   card=85 -> AverTV DVB-T 777                         1461:2c05 1461:2c05
[   11.223579] saa7134:   card=86 -> LifeView FlyDVB-T / Genius VideoWonder D 5168:0301 1489:0301
[   11.223582] saa7134:   card=87 -> ADS Instant TV Duo Cardbus PTV331        0331:1421
[   11.223584] saa7134:   card=88 -> Tevion/KWorld DVB-T 220RF                17de:7201
[   11.223587] saa7134:   card=89 -> ELSA EX-VISION 700TV                     1048:226c
[   11.223589] saa7134:   card=90 -> Kworld ATSC110/115                       17de:7350 17de:7352
[   11.223592] saa7134:   card=91 -> AVerMedia A169 B                         1461:7360
[   11.223595] saa7134:   card=92 -> AVerMedia A169 B1                        1461:6360
[   11.223597] saa7134:   card=93 -> Medion 7134 Bridge #2                    16be:0005
[   11.223599] saa7134:   card=94 -> LifeView FlyDVB-T Hybrid Cardbus/MSI TV  5168:3306 5168:3502 5168:3307 4e42:3502
[   11.223604] saa7134:   card=95 -> LifeView FlyVIDEO3000 (NTSC)             5169:0138
[   11.223606] saa7134:   card=96 -> Medion Md8800 Quadro                     16be:0007 16be:0008 16be:000d
[   11.223610] saa7134:   card=97 -> LifeView FlyDVB-S /Acorp TV134DS         5168:0300 4e42:0300
[   11.223613] saa7134:   card=98 -> Proteus Pro 2309                         0919:2003
[   11.223615] saa7134:   card=99 -> AVerMedia TV Hybrid A16AR                1461:2c00
[   11.223618] saa7134:   card=100 -> Asus Europa2 OEM                         1043:4860
[   11.223620] saa7134:   card=101 -> Pinnacle PCTV 310i                       11bd:002f
[   11.223623] saa7134:   card=102 -> Avermedia AVerTV Studio 507              1461:9715
[   11.223625] saa7134:   card=103 -> Compro Videomate DVB-T200A              
[   11.223627] saa7134:   card=104 -> Hauppauge WinTV-HVR1110 DVB-T/Hybrid     0070:6700 0070:6701 0070:6702 0070:6703 0070:6704 0070:6705
[   11.223632] saa7134:   card=105 -> Terratec Cinergy HT PCMCIA               153b:1172
[   11.223635] saa7134:   card=106 -> Encore ENLTV                             1131:2342 1131:2341 3016:2344
[   11.223639] saa7134:   card=107 -> Encore ENLTV-FM                          1131:230f
[   11.223641] saa7134:   card=108 -> Terratec Cinergy HT PCI                  153b:1175
[   11.223644] saa7134:   card=109 -> Philips Tiger - S Reference design      
[   11.223645] saa7134:   card=110 -> Avermedia M102                           1461:f31e
[   11.223648] saa7134:   card=111 -> ASUS P7131 4871                          1043:4871
[   11.223650] saa7134:   card=112 -> ASUSTeK P7131 Hybrid                     1043:4876
[   11.223653] saa7134:   card=113 -> Elitegroup ECS TVP3XP FM1246 Tuner Card  1019:4cb6
[   11.223655] saa7134:   card=114 -> KWorld DVB-T 210                         17de:7250
[   11.223658] saa7134:   card=115 -> Sabrent PCMCIA TV-PCB05                  0919:2003
[   11.223660] saa7134:   card=116 -> 10MOONS TM300 TV Card                    1131:2304
[   11.223663] saa7134:   card=117 -> Avermedia Super 007                      1461:f01d
[   11.223665] saa7134:   card=118 -> Beholder BeholdTV 401                    0000:4016
[   11.223667] saa7134:   card=119 -> Beholder BeholdTV 403                    0000:4036
[   11.223670] saa7134:   card=120 -> Beholder BeholdTV 403 FM                 0000:4037
[   11.223672] saa7134:   card=121 -> Beholder BeholdTV 405                    0000:4050
[   11.223675] saa7134:   card=122 -> Beholder BeholdTV 405 FM                 0000:4051
[   11.223677] saa7134:   card=123 -> Beholder BeholdTV 407                    0000:4070
[   11.223680] saa7134:   card=124 -> Beholder BeholdTV 407 FM                 0000:4071
[   11.223682] saa7134:   card=125 -> Beholder BeholdTV 409                    0000:4090
[   11.223685] saa7134:   card=126 -> Beholder BeholdTV 505 FM                 5ace:5050
[   11.223687] saa7134:   card=127 -> Beholder BeholdTV 507 FM / BeholdTV 509  5ace:5070 5ace:5090
[   11.223690] saa7134:   card=128 -> Beholder BeholdTV Columbus TV/FM         0000:5201
[   11.223693] saa7134:   card=129 -> Beholder BeholdTV 607 FM                 5ace:6070
[   11.223695] saa7134:   card=130 -> Beholder BeholdTV M6                     5ace:6190
[   11.223698] saa7134:   card=131 -> Twinhan Hybrid DTV-DVB 3056 PCI          1822:0022
[   11.223700] saa7134:   card=132 -> Genius TVGO AM11MCE                     
[   11.223702] saa7134:   card=133 -> NXP Snake DVB-S reference design        
[   11.223704] saa7134:   card=134 -> Medion/Creatix CTX953 Hybrid             16be:0010
[   11.223707] saa7134:   card=135 -> MSI TV@nywhere A/D v1.1                  1462:8625
[   11.223709] saa7134:   card=136 -> AVerMedia Cardbus TV/Radio (E506R)       1461:f436
[   11.223712] saa7134:   card=137 -> AVerMedia Hybrid TV/Radio (A16D)         1461:f936
[   11.223714] saa7134:   card=138 -> Avermedia M115                           1461:a836
[   11.223717] saa7134:   card=139 -> Compro VideoMate T750                    185b:c900
[   11.223719] saa7134:   card=140 -> Avermedia DVB-S Pro A700                 1461:a7a1
[   11.223722] saa7134:   card=141 -> Avermedia DVB-S Hybrid+FM A700           1461:a7a2
[   11.223725] saa7134:   card=142 -> Beholder BeholdTV H6                     5ace:6290
[   11.223727] saa7134:   card=143 -> Beholder BeholdTV M63                    5ace:6191
[   11.223729] saa7134:   card=144 -> Beholder BeholdTV M6 Extra               5ace:6193
[   11.223732] saa7134:   card=145 -> AVerMedia MiniPCI DVB-T Hybrid M103      1461:f636 1461:f736
[   11.223735] saa7134:   card=146 -> ASUSTeK P7131 Analog                    
[   11.223737] saa7134:   card=147 -> Asus Tiger 3in1                          1043:4878
[   11.223740] saa7134:   card=148 -> Encore ENLTV-FM v5.3                     1a7f:2008
[   11.223742] saa7134:   card=149 -> Avermedia PCI pure analog (M135A)        1461:f11d
[   11.223744] saa7134:   card=150 -> Zogis Real Angel 220                    
[   11.223746] saa7134:   card=151 -> ADS Tech Instant HDTV                    1421:0380
[   11.223749] saa7134:   card=152 -> Asus Tiger Rev:1.00                      1043:4857
[   11.223751] saa7134:   card=153 -> Kworld Plus TV Analog Lite PCI           17de:7128
[   11.223754] saa7134:   card=154 -> Avermedia AVerTV GO 007 FM Plus          1461:f31d
[   11.223756] saa7134:   card=155 -> Hauppauge WinTV-HVR1150 ATSC/QAM-Hybrid  0070:6706 0070:6708
[   11.223759] saa7134:   card=156 -> Hauppauge WinTV-HVR1120 DVB-T/Hybrid     0070:6707 0070:6709 0070:670a
[   11.223763] saa7134:   card=157 -> Avermedia AVerTV Studio 507UA            1461:a11b
[   11.223766] saa7134:   card=158 -> AVerMedia Cardbus TV/Radio (E501R)       1461:b7e9
[   11.223768] saa7134:   card=159 -> Beholder BeholdTV 505 RDS                0000:505b
[   11.223771] saa7134:   card=160 -> Beholder BeholdTV 507 RDS                0000:5071
[   11.223773] saa7134:   card=161 -> Beholder BeholdTV 507 RDS                0000:507b
[   11.223776] saa7134:   card=162 -> Beholder BeholdTV 607 FM                 5ace:6071
[   11.223778] saa7134:   card=163 -> Beholder BeholdTV 609 FM                 5ace:6090
[   11.223781] saa7134:   card=164 -> Beholder BeholdTV 609 FM                 5ace:6091
[   11.223783] saa7134:   card=165 -> Beholder BeholdTV 607 RDS                5ace:6072
[   11.223786] saa7134:   card=166 -> Beholder BeholdTV 607 RDS                5ace:6073
[   11.223788] saa7134:   card=167 -> Beholder BeholdTV 609 RDS                5ace:6092
[   11.223790] saa7134:   card=168 -> Beholder BeholdTV 609 RDS                5ace:6093
[   11.223793] saa7134:   card=169 -> Compro VideoMate S350/S300               185b:c900
[   11.223795] saa7134:   card=170 -> AverMedia AverTV Studio 505              1461:a115
[   11.223798] saa7134:   card=171 -> Beholder BeholdTV X7                     5ace:7595
[   11.223800] saa7134:   card=172 -> RoverMedia TV Link Pro FM                19d1:0138
[   11.223803] saa7134:   card=173 -> Zolid Hybrid TV Tuner PCI                1131:2004
[   11.223805] saa7134:   card=174 -> Asus Europa Hybrid OEM                   1043:4847
[   11.223808] saa7134:   card=175 -> Leadtek Winfast DTV1000S                 107d:6655
[   11.223810] saa7134:   card=176 -> Beholder BeholdTV 505 RDS                0000:5051
[   11.223812] saa7134:   card=177 -> Hawell HW-404M7                         
[   11.223814] saa7134:   card=178 -> Beholder BeholdTV H7                     5ace:7190
[   11.223817] saa7134:   card=179 -> Beholder BeholdTV A7                     5ace:7090
[   11.223819] saa7134:   card=180 -> Avermedia PCI M733A                      1461:4155 1461:4255
[   11.223822] saa7134:   card=181 -> TechoTrend TT-budget T-3000              13c2:2804
[   11.223825] saa7134:   card=182 -> Kworld PCI SBTVD/ISDB-T Full-Seg Hybrid  17de:b136
[   11.223827] saa7134:   card=183 -> Compro VideoMate Vista M1F               185b:c900
[   11.223830] saa7134:   card=184 -> Encore ENLTV-FM 3                        1a7f:2108
[   11.223832] saa7134:   card=185 -> MagicPro ProHDTV Pro2 DMB-TH/Hybrid      17de:d136
[   11.223834] saa7134:   card=186 -> Beholder BeholdTV 501                    5ace:5010
[   11.223837] saa7134:   card=187 -> Beholder BeholdTV 503 FM                 5ace:5030
[   11.223839] saa7134:   card=188 -> Sensoray 811/911                         6000:0811 6000:0911
[   11.223842] saa7134:   card=189 -> Kworld PC150-U                           17de:a134
[   11.223845] saa7134:   card=190 -> Asus My Cinema PS3-100                   1043:48cd
[   11.223848] saa7133[0]: subsystem: 17de:7136, board: UNKNOWN/GENERIC [card=0,autodetected]
[   11.223862] saa7133[0]: board init: gpio is 40
[   11.270629] snd_hda_intel 0000:00:1b.0: irq 43 for MSI/MSI-X
[   11.273049] gpio_ich: GPIO from 206 to 255 on gpio_ich
[   11.288453] lp0: using parport0 (interrupt-driven).
[   11.298772] ppdev: user-space parallel port driver
[   11.318021] input: HDA Intel Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input4
[   11.318205] input: HDA Intel Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
[   11.318363] input: HDA Intel Line Out as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   11.318951] hda_intel: Disabling MSI
[   11.318964] hda-intel: 0000:01:00.1: Handle VGA-switcheroo audio client
[   11.370750] microcode: CPU1 sig=0x1067a, pf=0x1, revision=0xa07
[   11.372063] saa7133[0]: i2c eeprom 00: de 17 36 71 10 28 ff ff ff ff ff ff ff ff ff ff
[   11.372074] saa7133[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   11.372084] saa7133[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   11.372093] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   11.372103] saa7133[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   11.372112] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   11.372127] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   11.372137] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   11.372146] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   11.372155] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   11.372165] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   11.372174] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   11.372184] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   11.372193] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   11.372202] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   11.372212] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   11.372513] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   11.373513] saa7133[0]: registered device video1 [v4l2]
[   11.373551] saa7133[0]: registered device vbi0
[   11.375575] saa7134 ALSA driver for DMA sound loaded
[   11.375603] saa7133[0]/alsa: saa7133[0] at 0xdffff800 irq 21 registered as card -2
[   12.076177] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input7
[   12.204168] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input8
[   12.204274] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input9
[   12.204367] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input10
[   12.204474] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input11
[   12.272478] nvidia: module license 'NVIDIA' taints kernel.
[   12.272553] Disabling lock debugging due to kernel taint
[   12.297137] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   12.298467] NVRM: loading NVIDIA UNIX x86 Kernel Module  304.43  Sun Aug 19 20:20:21 PDT 2012
[   12.450967] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   12.528204] init: udev-fallback-graphics main process (752) terminated with status 1
[   12.593459] init: failsafe main process (810) killed by TERM signal
[   12.805696] type=1400 audit(1352803108.712:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=895 comm="apparmor_parser"
[   12.814217] type=1400 audit(1352803108.720:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=906 comm="apparmor_parser"
[   12.814540] type=1400 audit(1352803108.720:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=906 comm="apparmor_parser"
[   12.815179] type=1400 audit(1352803108.720:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/i386-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper" pid=907 comm="apparmor_parser"
[   12.815506] type=1400 audit(1352803108.720:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/i386-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper//chromium_browser" pid=907 comm="apparmor_parser"
[   12.815876] Bluetooth: RFCOMM TTY layer initialized
[   12.815880] Bluetooth: RFCOMM socket layer initialized
[   12.815881] Bluetooth: RFCOMM ver 1.11
[   12.816478] type=1400 audit(1352803108.724:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=895 comm="apparmor_parser"
[   12.840327] type=1400 audit(1352803108.748:11): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=911 comm="apparmor_parser"
[   12.879455] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   12.879460] Bluetooth: BNEP filters: protocol multicast
[   13.066975] atl1 0000:03:00.0: irq 44 for MSI/MSI-X
[   13.067038] atl1 0000:03:00.0: eth0 link is up 100 Mbps full duplex
[   14.423881] usblp0: removed
[   14.425340] usblp 2-3:1.1: usblp0: USB Bidirectional printer dev 4 if 1 alt 0 proto 2 vid 0x03F0 pid 0x8711
[   15.402075] NVRM: GPU at 0000:01:00: GPU-e06bbd7c-6987-3fe4-8a77-a3fb04071331
[   34.496160] audit_printk_skb: 48 callbacks suppressed
[   34.496164] type=1701 audit(1352803130.407:28): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=2062 comm="chrome" reason="seccomp" sig=0 syscall=20 compat=0 ip=0xb358b424 code=0x50000
[   49.353559] type=1701 audit(1352803145.263:29): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=2309 comm="chrome" reason="seccomp" sig=0 syscall=20 compat=0 ip=0xb34e9424 code=0x50000
[  522.254092] type=1400 audit(1352803618.163:30): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld" pid=10294 comm="apparmor_parser"
[  522.294697] type=1400 audit(1352803618.203:31): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=10330 comm="apparmor_parser"
[  528.886713] type=1400 audit(1352803624.795:32): apparmor="STATUS" operation="profile_load" name="/usr/sbin/ntpd" pid=10459 comm="apparmor_parser"
[  537.932607] rhythmbox-metad[10280]: segfault at 11c4c81e ip b7513c30 sp bfe5f670 error 4 in libgobject-2.0.so.0.3400.0[b74e2000+4e000]
[  602.812114] NVRM: GPU at 0000:01:00: GPU-e06bbd7c-6987-3fe4-8a77-a3fb04071331
[  627.803839] init: mythtv-backend main process (11298) killed by TERM signal
[  730.291119] type=1701 audit(1352803826.198:33): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=14721 comm="chrome" reason="seccomp" sig=0 syscall=20 compat=0 ip=0xb3589424 code=0x50000
[  731.186803] type=1701 audit(1352803827.093:34): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=14824 comm="chrome" reason="seccomp" sig=0 syscall=20 compat=0 ip=0xb3592424 code=0x50000


PLEASE somebody please help me...i want to use my tuner with S-Video/Composite Mode because my cableprovider uses tv set top box or something like that...:(

---

