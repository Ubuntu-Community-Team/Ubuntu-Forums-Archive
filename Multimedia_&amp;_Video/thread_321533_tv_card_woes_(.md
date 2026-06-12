---
title: "tv card woes :("
date: 2006-12-19
forum: Multimedia &amp; Video
---

### Post by mrpixels0 on 2006-12-19
I am having trouble getting my tv card to work, i have read all the read mes i could find on the subject but to no avail now after 2 months of looking i have come to the conclusion i am going to need expert advice.

Card specs: 

phillips 713x chipset
plug and play compliant
full channel cable / antenna ready tuner
composite / s video inputs
remote control

dmesg output:

[17227268.628000] saa7130[0]: subsystem: 1131:0000, board: UNKNOWN/GENERIC [card=0,autodetected]
[17227268.648000] saa7130[0]: board init: gpio is 3f000
[17227268.752000] saa7130[0]: Huh, no eeprom present (err=-5)?
[17227268.780000] saa7130[0]: registered device video0 [v4l2]
[17227268.804000] saa7130[0]: registered device vbi0
[17227268.820000] saa7134 ALSA driver for DMA sound loaded
[17227268.820000] saa7130[0]/alsa: saa7130[0] at 0xfdeff000 irq 58 registered as card -1
[17227332.892000] saa7134 ALSA driver for DMA sound unloaded
[17227332.952000] saa7130/34: v4l2 driver version 0.2.14 loaded
[17227332.956000] ACPI: PCI Interrupt 0000:01:08.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 58
[17227332.956000] saa7130[0]: found at 0000:01:08.0, rev: 1, irq: 58, latency: 64, mmio: 0xfdeff000
[17227332.956000] saa7134: <rant>
[17227332.956000] saa7134:  Congratulations!  Your TV card vendor saved a few
[17227332.956000] saa7134:  cents for a eeprom, thus your pci board has no
[17227332.956000] saa7134:  subsystem ID and I can't identify it automatically
[17227332.956000] saa7134: </rant>
[17227332.956000] saa7134: I feel better now.  Ok, here are the good news:
[17227332.956000] saa7134: You can use the card=<nr> insmod option to specify
[17227332.956000] saa7134: which board do you have.  The list:
[17227332.956000] saa7134:   card=0 -> UNKNOWN/GENERIC
[17227332.956000] saa7134:   card=1 -> Proteus Pro [philips reference design]   1131:2001 1131:2001
[17227332.956000] saa7134:   card=2 -> LifeView FlyVIDEO3000                    5168:0138 4e42:0138
[17227332.956000] saa7134:   card=3 -> LifeView/Typhoon FlyVIDEO2000            5168:0138 4e42:0138
[17227332.956000] saa7134:   card=4 -> EMPRESS                                  1131:6752
[17227332.956000] saa7134:   card=5 -> SKNet Monster TV                         1131:4e85
[17227332.956000] saa7134:   card=6 -> Tevion MD 9717
[17227332.956000] saa7134:   card=7 -> KNC One TV-Station RDS / Typhoon TV Tune 1131:fe01 1894:fe01
[17227332.956000] saa7134:   card=8 -> Terratec Cinergy 400 TV                  153b:1142
[17227332.956000] saa7134:   card=9 -> Medion 5044
[17227332.956000] saa7134:   card=10 -> Kworld/KuroutoShikou SAA7130-TVPCI
[17227332.956000] saa7134:   card=11 -> Terratec Cinergy 600 TV                  153b:1143
[17227332.956000] saa7134:   card=12 -> Medion 7134                              16be:0003
[17227332.956000] saa7134:   card=13 -> Typhoon TV+Radio 90031
[17227332.956000] saa7134:   card=14 -> ELSA EX-VISION 300TV                     1048:226b
[17227332.956000] saa7134:   card=15 -> ELSA EX-VISION 500TV                     1048:226a
[17227332.956000] saa7134:   card=16 -> ASUS TV-FM 7134                          1043:4842 1043:4830 1043:4840
[17227332.956000] saa7134:   card=17 -> AOPEN VA1000 POWER                       1131:7133
[17227332.956000] saa7134:   card=18 -> BMK MPEX No Tuner
[17227332.956000] saa7134:   card=19 -> Compro VideoMate TV                      185b:c100
[17227332.956000] saa7134:   card=20 -> Matrox CronosPlus                        102b:48d0
[17227332.956000] saa7134:   card=21 -> 10MOONS PCI TV CAPTURE CARD              1131:2001
[17227332.956000] saa7134:   card=22 -> AverMedia M156 / Medion 2819             1461:a70b
[17227332.956000] saa7134:   card=23 -> BMK MPEX Tuner
[17227332.956000] saa7134:   card=24 -> KNC One TV-Station DVR                   1894:a006
[17227332.956000] saa7134:   card=25 -> ASUS TV-FM 7133                          1043:4843
[17227332.956000] saa7134:   card=26 -> Pinnacle PCTV Stereo (saa7134)           11bd:002b
[17227332.956000] saa7134:   card=27 -> Manli MuchTV M-TV002/Behold TV 403 FM
[17227332.956000] saa7134:   card=28 -> Manli MuchTV M-TV001/Behold TV 401
[17227332.956000] saa7134:   card=29 -> Nagase Sangyo TransGear 3000TV           1461:050c
[17227332.956000] saa7134:   card=30 -> Elitegroup ECS TVP3XP FM1216 Tuner Card( 1019:4cb4
[17227332.956000] saa7134:   card=31 -> Elitegroup ECS TVP3XP FM1236 Tuner Card  1019:4cb5
[17227332.956000] saa7134:   card=32 -> AVACS SmartTV
[17227332.956000] saa7134:   card=33 -> AVerMedia DVD EZMaker                    1461:10ff
[17227332.956000] saa7134:   card=34 -> Noval Prime TV 7133
[17227332.956000] saa7134:   card=35 -> AverMedia AverTV Studio 305              1461:2115
[17227332.956000] saa7134:   card=36 -> UPMOST PURPLE TV                         12ab:0800
[17227332.956000] saa7134:   card=37 -> Items MuchTV Plus / IT-005
[17227332.956000] saa7134:   card=38 -> Terratec Cinergy 200 TV                  153b:1152
[17227332.956000] saa7134:   card=39 -> LifeView FlyTV Platinum Mini             5168:0212 4e42:0212
[17227332.956000] saa7134:   card=40 -> Compro VideoMate TV PVR/FM               185b:c100
[17227332.956000] saa7134:   card=41 -> Compro VideoMate TV Gold+                185b:c100
[17227332.956000] saa7134:   card=42 -> Sabrent SBT-TVFM (saa7130)
[17227332.956000] saa7134:   card=43 -> :Zolid Xpert TV7134
[17227332.956000] saa7134:   card=44 -> Empire PCI TV-Radio LE
[17227332.956000] saa7134:   card=45 -> Avermedia AVerTV Studio 307              1461:9715
[17227332.956000] saa7134:   card=46 -> AVerMedia Cardbus TV/Radio (E500)        1461:d6ee
[17227332.956000] saa7134:   card=47 -> Terratec Cinergy 400 mobile              153b:1162
[17227332.956000] saa7134:   card=48 -> Terratec Cinergy 600 TV MK3              153b:1158
[17227332.956000] saa7134:   card=49 -> Compro VideoMate Gold+ Pal               185b:c200
[17227332.956000] saa7134:   card=50 -> Pinnacle PCTV 300i DVB-T + PAL           11bd:002d
[17227332.956000] saa7134:   card=51 -> ProVideo PV952                           1540:9524
[17227332.956000] saa7134:   card=52 -> AverMedia AverTV/305                     1461:2108
[17227332.956000] saa7134:   card=53 -> ASUS TV-FM 7135                          1043:4845
[17227332.956000] saa7134:   card=54 -> LifeView FlyTV Platinum FM / Gold        5168:0214 1489:0214 5168:0304
[17227332.956000] saa7134:   card=55 -> LifeView FlyDVB-T DUO                    5168:0306
[17227332.956000] saa7134:   card=56 -> Avermedia AVerTV 307                     1461:a70a
[17227332.956000] saa7134:   card=57 -> Avermedia AVerTV GO 007 FM               1461:f31f
[17227332.956000] saa7134:   card=58 -> ADS Tech Instant TV (saa7135)            1421:0350 1421:0351 1421:0370 1421:1370
[17227332.956000] saa7134:   card=59 -> Kworld/Tevion V-Stream Xpert TV PVR7134
[17227332.956000] saa7134:   card=60 -> LifeView/Typhoon FlyDVB-T Duo Cardbus    5168:0502 4e42:0502
[17227332.956000] saa7134:   card=61 -> Philips TOUGH DVB-T reference design     1131:2004
[17227332.956000] saa7134:   card=62 -> Compro VideoMate TV Gold+II
[17227332.956000] saa7134:   card=63 -> Kworld Xpert TV PVR7134
[17227332.956000] saa7134:   card=64 -> FlyTV mini Asus Digimatrix               1043:0210
[17227332.956000] saa7134:   card=65 -> V-Stream Studio TV Terminator
[17227332.956000] saa7134:   card=66 -> Yuan TUN-900 (saa7135)
[17227332.956000] saa7134:   card=67 -> Beholder BeholdTV 409 FM                 0000:4091
[17227332.956000] saa7134:   card=68 -> GoTView 7135 PCI                         5456:7135
[17227332.956000] saa7134:   card=69 -> Philips EUROPA V3 reference design       1131:2004
[17227332.956000] saa7134:   card=70 -> Compro Videomate DVB-T300                185b:c900
[17227332.956000] saa7134:   card=71 -> Compro Videomate DVB-T200                185b:c901
[17227332.956000] saa7134:   card=72 -> RTD Embedded Technologies VFG7350        1435:7350
[17227332.956000] saa7134:   card=73 -> RTD Embedded Technologies VFG7330        1435:7330
[17227332.956000] saa7134:   card=74 -> LifeView FlyTV Platinum Mini2            14c0:1212
[17227332.956000] saa7134:   card=75 -> AVerMedia AVerTVHD MCE A180              1461:1044
[17227332.956000] saa7134:   card=76 -> SKNet MonsterTV Mobile                   1131:4ee9
[17227332.956000] saa7134:   card=77 -> Pinnacle PCTV 40i/50i/110i (saa7133)     11bd:002e
[17227332.956000] saa7134:   card=78 -> ASUSTeK P7131 Dual                       1043:4862
[17227332.956000] saa7134:   card=79 -> Sedna/MuchTV PC TV Cardbus TV/Radio (ITO
[17227332.956000] saa7134:   card=80 -> ASUS Digimatrix TV                       1043:0210
[17227332.956000] saa7134:   card=81 -> Philips Tiger reference design           1131:2018
[17227332.956000] saa7134:   card=82 -> MSI TV@Anywhere plus                     1462:6231
[17227332.956000] saa7134:   card=83 -> Terratec Cinergy 250 PCI TV              153b:1160
[17227332.956000] saa7134:   card=84 -> LifeView FlyDVB Trio                     5168:0319
[17227332.956000] saa7134:   card=85 -> AverTV DVB-T 777                         1461:2c05
[17227332.956000] saa7134:   card=86 -> LifeView FlyDVB-T / Genius VideoWonder D 5168:0301 1489:0301
[17227332.956000] saa7134:   card=87 -> ADS Instant TV Duo Cardbus PTV331        0331:1421
[17227332.956000] saa7134:   card=88 -> Tevion/KWorld DVB-T 220RF                17de:7201
[17227332.956000] saa7134:   card=89 -> ELSA EX-VISION 700TV                     1048:226c
[17227332.956000] saa7134:   card=90 -> Kworld ATSC110                           17de:7350
[17227332.956000] saa7134:   card=91 -> AVerMedia A169 B                         1461:7360
[17227332.956000] saa7134:   card=92 -> AVerMedia A169 B1                        1461:6360
[17227332.956000] saa7134:   card=93 -> Medion 7134 Bridge #2                    16be:0005
[17227332.956000] saa7134:   card=94 -> LifeView FlyDVB-T Hybrid Cardbus         5168:3306 5168:3502
[17227332.956000] saa7130[0]: subsystem: 1131:0000, board: UNKNOWN/GENERIC [card=0,autodetected]
[17227332.972000] saa7130[0]: board init: gpio is 3f000
[17227333.076000] saa7130[0]: Huh, no eeprom present (err=-5)?
[17227333.104000] saa7130[0]: registered device video0 [v4l2]
[17227333.132000] saa7130[0]: registered device vbi0

i have no idea where to find a list of tuners to try, just shows a list of cards to try. if anyone could help me figure out why i cannot get KDETV to select anything other than default then that would be great and i would very much be in debt to you.

Thanks mrPixels0

---

### Post by renzokuken on 2006-12-19
have you come across [www.linuxtv.org](www.linuxtv.org) in your travels? seems to have a lot of useful info

---

### Post by mrpixels0 on 2006-12-19
Actually i had no idea that page was there, thanks for the Link :), i now have a working tv card / remote control yes !!!!.

if anyone is intrested here is what i did to make it work:

1. sudo nano /etc/modprobe.d/saa1734

2. added these lines to the file
    
    alias char-major-81 videodev
    alias char-major-81-0 saa7134
    options saa7134 card=2 tuner=17 oss=1

3. sudo rmmod saa7134_alsa && sudo rmmod saa7134 && sudo modprobe saa7134

 and now i can use my tv tuner card that is made by: a compnay known only as "power tv" or at least that is what the FCC I.D. has it listed as some place in china. but it works and that is all that matters. and i am sure that this would work with other super Generic cards like mine that also sport a Phillips 713x chipset.

it seems this card is known to bttv as a fly3000 seris card  (hope that makes sense to someone) according to dmesg.
thanks again  renzokuken for the link you are the greatest ! :)

Peace mrpixels0

---

### Post by DrMega on 2006-12-19
I'm just starting on my TV tuner, and have been having a real headache so far. Is yours digital or analog (or both). Mine is the Pinnacle 300i DVB + PAL. I'm only interested in getting the analog part work for now (I don't have a digital signal - no aeriel on my house and live in a valley anyway).

---

### Post by mrpixels0 on 2006-12-20
hello there Drmega :)

No my card is a very simple $5.00 tuner just analog i'm afraid, as for digital cards i have no idea how they work sorry,

what chipset is it using for it's analog ?, in this thread at the top is a Link given to me by renzokuken and it has a lot of Useful information there that is how i got my card working in mere minutes.

if you have not tried there i would suggest starting there as i did, good luck to you and if you succeed then please post and share how you did it, this way others who have the same card as you can benefit from what you have learned.

MP0

---

### Post by mrpixels0 on 2006-12-20
okay,  i am back with yet another problem my sound card is working great but my tv cards sound output is not working at all and i have it setup as sound out from tv card to line in on my sound card under Alsa /w Oss emulation and v4l module is loaded and working and i have adjusted all my mixer settings for each one the sound card and the tv card.
but to no avail, i get great pictures but no sound and according to my system it should just work as is but it don't.

here is what dmeg has to say:

```

[17179569.184000] Linux version 2.6.17-10-386 (root@terranova) (gcc version 4.1.
2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 Tue Dec 5 22:26:18 UTC 2006
 (Ubuntu 2.6.17-10.34-386)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[17179569.184000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
[17179569.184000]  BIOS-e820: 000000001fff0000 - 000000001fff3000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000001fff3000 - 0000000020000000 (ACPI data)
[17179569.184000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 511MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000f4fe0
[17179569.184000] On node 0 totalpages: 131056
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 126960 pages, LIFO batch:31
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 Nvidia                                ) @ 0x0
00f8ea0
[17179569.184000] ACPI: RSDT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @
 0x1fff3040
[17179569.184000] ACPI: FADT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @
 0x1fff30c0
[17179569.184000] ACPI: MCFG (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @
 0x1fff9440
[17179569.184000] ACPI: MADT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @
 0x1fff9380
[17179569.184000] ACPI: DSDT (v001 NVIDIA AWRDACPI 0x00001000 MSFT 0x0100000e) @
 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x4008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:4 APIC version 16
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] ACPI: IRQ14 used by override.
[17179569.184000] ACPI: IRQ15 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 30000000 (gap: 20000000:c
0000000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=UUID=f92450f9-1af5-4c7c-8298-5567231
ca253 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[17179569.184000] Detected 1607.572 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179572.320000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes
)
[17179572.320000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179572.332000] Memory: 508948k/524224k available (1829k kernel code, 14724k r
eserved, 1038k data, 288k init, 0k highmem)
[17179572.332000] Checking if this processor honours the WP bit even in supervis
or mode... Ok.
[17179572.412000] Calibrating delay using timer specific routine.. 3218.39 BogoM
IPS (lpj=6436799)
[17179572.412000] Security Framework v1.0.0 initialized
[17179572.412000] SELinux:  Disabled at boot.
[17179572.412000] Mount-cache hash table entries: 512
[17179572.412000] CPU: After generic identify, caps: 078bfbff c1d3fbff 00000000
00000000 00000000 00000000 00000000
[17179572.412000] CPU: After vendor identify, caps: 078bfbff c1d3fbff 00000000 0
0000000 00000000 00000000 00000000
[17179572.412000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/li
ne)
[17179572.412000] CPU: L2 Cache: 128K (64 bytes/line)
[17179572.412000] CPU: After all inits, caps: 078bfbff c1d3fbff 00000000 0000041
0 00000000 00000000 00000000
[17179572.412000] CPU: AMD Mobile AMD Athlon(tm) XP-M Processor 2800+ stepping 0
a
[17179572.412000] Checking 'hlt' instruction... OK.
[17179572.428000] SMP alternatives: switching to UP code
[17179572.428000] Freeing SMP alternatives: 0k freed
[17179572.428000] checking if image is initramfs... it is
[17179573.100000] Freeing initrd memory: 6654k freed
[17179573.100000] ACPI: Core revision 20060707
[17179573.100000] ACPI: Looking for DSDT ... not found!
[17179573.108000] ENABLING IO-APIC IRQs
[17179573.108000] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[17179573.256000] NET: Registered protocol family 16
[17179573.256000] EISA bus registered
[17179573.256000] ACPI: bus type pci registered
[17179573.256000] PCI: Using MMCONFIG
[17179573.256000] PCI: No mmconfig possible on 0:18
[17179573.256000] Setting up standard PCI resources
[17179573.264000] ACPI: Interpreter enabled
[17179573.264000] ACPI: Using IOAPIC for interrupt routing
[17179573.268000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179573.268000] PCI: Probing PCI hardware (bus 00)
[17179573.272000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:06.0
[17179573.272000] PCI: Transparent bridge - 0000:00:09.0
[17179573.272000] Boot video device is 0000:05:00.0
[17179573.272000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179573.360000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[17179573.360000] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 7 9 10 11 12 14 15
) *0, disabled.
[17179573.360000] ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 5 7 9 10 11 12 14 15
) *0, disabled.
[17179573.364000] ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 *5 7 9 10 11 12 14 1
5)
[17179573.364000] ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 5 7 9 10 11 12 14 15
) *0, disabled.
[17179573.364000] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 7 9 10 11 12 14 15
) *0, disabled.
[17179573.364000] ACPI: PCI Interrupt Link [LUBA] (IRQs 3 4 5 7 9 *10 11 12 14 1
5)
[17179573.364000] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 5 7 9 10 11 12 14 15
) *0, disabled.
[17179573.364000] ACPI: PCI Interrupt Link [LMAC] (IRQs 3 4 5 7 9 *10 11 12 14 1
5)
[17179573.364000] ACPI: PCI Interrupt Link [LACI] (IRQs 3 4 5 7 9 10 *11 12 14 1
5)
[17179573.364000] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 *5 7 9 10 11 12 14 1
5)
[17179573.364000] ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 *5 7 9 10 11 12 14 1
5)
[17179573.364000] ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 5 7 9 10 *11 12 14 1
5)
[17179573.368000] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 7 9 10 11 12 14 15
) *0, disabled.
[17179573.368000] ACPI: PCI Interrupt Link [LSID] (IRQs 3 4 5 7 9 10 *11 12 14 1
5)
[17179573.368000] ACPI: PCI Interrupt Link [LFID] (IRQs 3 4 5 7 9 *10 11 12 14 1
5)
[17179573.368000] ACPI: PCI Interrupt Link [LPCA] (IRQs 3 4 5 7 9 10 11 12 14 15
) *0, disabled.
[17179573.368000] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[17179573.368000] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[17179573.368000] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[17179573.368000] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[17179573.368000] ACPI: PCI Interrupt Link [APC5] (IRQs *16), disabled.
[17179573.372000] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0, disable
d.
[17179573.372000] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disable
d.
[17179573.372000] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0, disable
d.
[17179573.372000] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0, disable
d.
[17179573.372000] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disable
d.
[17179573.372000] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0, disable
d.
[17179573.372000] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0, disable
d.
[17179573.372000] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disable
d.
[17179573.376000] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0, disable
d.
[17179573.376000] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0, disable
d.
[17179573.376000] ACPI: PCI Interrupt Link [APCP] (IRQs 20 21 22 23) *0, disable
d.
[17179573.380000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179573.380000] pnp: PnP ACPI init
[17179573.388000] pnp: PnP ACPI: found 14 devices
[17179573.388000] PnPBIOS: Disabled by ACPI PNP
[17179573.388000] PCI: Using ACPI for IRQ routing
[17179573.388000] PCI: If a device doesn't work, try "pci=routeirq".  If it help
s, post a report
[17179573.388000] pnp: 00:01: ioport range 0x4000-0x407f could not be reserved
[17179573.388000] pnp: 00:01: ioport range 0x4080-0x40ff has been reserved
[17179573.388000] pnp: 00:01: ioport range 0x4400-0x447f has been reserved
[17179573.388000] pnp: 00:01: ioport range 0x4480-0x44ff could not be reserved
[17179573.388000] pnp: 00:01: ioport range 0x4800-0x487f has been reserved
[17179573.388000] pnp: 00:01: ioport range 0x4880-0x48ff has been reserved
[17179573.388000] PCI: Bridge: 0000:00:09.0
[17179573.388000]   IO window: d000-dfff
[17179573.388000]   MEM window: fde00000-fdefffff
[17179573.388000]   PREFETCH window: fdf00000-fdffffff
[17179573.388000] PCI: Bridge: 0000:00:0b.0
[17179573.388000]   IO window: c000-cfff
[17179573.388000]   MEM window: fdd00000-fddfffff
[17179573.388000]   PREFETCH window: fdc00000-fdcfffff
[17179573.388000] PCI: Bridge: 0000:00:0c.0
[17179573.388000]   IO window: b000-bfff
[17179573.388000]   MEM window: fdb00000-fdbfffff
[17179573.388000]   PREFETCH window: fda00000-fdafffff
[17179573.388000] PCI: Bridge: 0000:00:0d.0
[17179573.388000]   IO window: a000-afff
[17179573.388000]   MEM window: fd900000-fd9fffff
[17179573.388000]   PREFETCH window: fd800000-fd8fffff
[17179573.388000] PCI: Bridge: 0000:00:0e.0
[17179573.388000]   IO window: 9000-9fff
[17179573.388000]   MEM window: fa000000-fcffffff
[17179573.388000]   PREFETCH window: d0000000-dfffffff
[17179573.388000] PCI: Setting latency timer of device 0000:00:09.0 to 64
[17179573.388000] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[17179573.388000] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[17179573.388000] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[17179573.388000] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[17179573.388000] NET: Registered protocol family 2
[17179573.428000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes
)
[17179573.428000] TCP established hash table entries: 16384 (order: 4, 65536 byt
es)
[17179573.428000] TCP bind hash table entries: 8192 (order: 3, 32768 bytes)
[17179573.428000] TCP: Hash tables configured (established 16384 bind 8192)
[17179573.428000] TCP reno registered
[17179573.428000] audit: initializing netlink socket (disabled)
[17179573.428000] audit(1166533939.428:1): initialized
[17179573.428000] VFS: Disk quotas dquot_6.5.1
[17179573.428000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179573.428000] Initializing Cryptographic API
[17179573.428000] io scheduler noop registered
[17179573.428000] io scheduler anticipatory registered
[17179573.428000] io scheduler deadline registered
[17179573.428000] io scheduler cfq registered (default)
[17179573.428000] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[17179573.428000] pcie_portdrv_probe->Dev[005d:10de] has invalid IRQ. Check vend
or BIOS
[17179573.428000] assign_interrupt_mode Found MSI capability
[17179573.428000] Allocate Port Service[0000:00:0b.0:pcie00]
[17179573.428000] Allocate Port Service[0000:00:0b.0:pcie03]
[17179573.428000] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[17179573.428000] pcie_portdrv_probe->Dev[005d:10de] has invalid IRQ. Check vend
or BIOS
[17179573.428000] assign_interrupt_mode Found MSI capability
[17179573.428000] Allocate Port Service[0000:00:0c.0:pcie00]
[17179573.428000] Allocate Port Service[0000:00:0c.0:pcie03]
[17179573.428000] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[17179573.428000] pcie_portdrv_probe->Dev[005d:10de] has invalid IRQ. Check vend
or BIOS
[17179573.428000] assign_interrupt_mode Found MSI capability
[17179573.428000] Allocate Port Service[0000:00:0d.0:pcie00]
[17179573.428000] Allocate Port Service[0000:00:0d.0:pcie03]
[17179573.428000] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[17179573.428000] pcie_portdrv_probe->Dev[005d:10de] has invalid IRQ. Check vend
or BIOS
[17179573.428000] assign_interrupt_mode Found MSI capability
[17179573.428000] Allocate Port Service[0000:00:0e.0:pcie00]
[17179573.428000] Allocate Port Service[0000:00:0e.0:pcie03]
[17179573.428000] isapnp: Scanning for PnP cards...
[17179573.780000] isapnp: No Plug & Play device found
[17179573.808000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ shari
ng enabled
[17179573.808000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179573.808000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179573.808000] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179573.808000] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179573.808000] mice: PS/2 mouse device common for all mice
[17179573.808000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 b
locksize
[17179573.808000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179573.808000] ide: Assuming 33MHz system bus speed for PIO modes; override w
ith idebus=xx
[17179573.808000] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[17179573.808000] PNP: PS/2 controller doesn't have AUX irq; using default 12
[17179573.832000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179573.836000] EISA: Probing bus 0 at eisa.0
[17179573.836000] Cannot allocate resource for EISA slot 4
[17179573.836000] EISA: Detected 0 cards.
[17179573.836000] TCP bic registered
[17179573.836000] NET: Registered protocol family 1
[17179573.836000] NET: Registered protocol family 8
[17179573.836000] NET: Registered protocol family 20
[17179573.836000] Using IPI Shortcut mode
[17179573.836000] ACPI: (supports S0 S1 S4 S5)
[17179573.836000] Freeing unused kernel memory: 288k freed
[17179573.864000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179574.984000] Capability LSM initialized
[17179575.020000] ACPI: Fan [FAN] (on)
[17179575.020000] ACPI: Getting cpuindex for acpiid 0x1
[17179575.024000] ACPI: Thermal Zone [THRM] (22 C)
[17179575.536000] SCSI subsystem initialized
[17179575.536000] libata version 1.20 loaded.
[17179575.540000] sata_nv 0000:00:07.0: version 0.8
[17179575.540000] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
[17179575.540000] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [APSI] -> GSI 23 (
level, low) -> IRQ 217
[17179575.540000] PCI: Setting latency timer of device 0000:00:07.0 to 64
[17179575.540000] ata1: SATA max UDMA/133 cmd 0x9F0 ctl 0xBF2 bmdma 0xF600 irq 2
17
[17179575.540000] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xB72 bmdma 0xF608 irq 2
17
[17179575.744000] ata1: SATA link down (SStatus 0)
[17179575.744000] scsi0 : sata_nv
[17179575.948000] ata2: SATA link up 1.5 Gbps (SStatus 113)
[17179576.112000] ata2: dev 0 cfg 49:2f00 82:7c6b 83:7f09 84:4673 85:7c69 86:3e2
1 87:4663 88:407f
[17179576.112000] ata2: dev 0 ATA-7, max UDMA/133, 586114704 sectors: LBA48
[17179576.112000] nv_sata: Primary device added
[17179576.112000] nv_sata: Primary device removed
[17179576.112000] nv_sata: Secondary device added
[17179576.112000] nv_sata: Secondary device removed
[17179576.120000] ata2: dev 0 configured for UDMA/133
[17179576.120000] scsi1 : sata_nv
[17179576.120000]   Vendor: ATA       Model: Maxtor 6L300S0    Rev: BANC
[17179576.120000]   Type:   Direct-Access                      ANSI SCSI revisio
n: 05
[17179576.120000] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 22
[17179576.120000] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [APSJ] -> GSI 22 (
level, low) -> IRQ 225
[17179576.120000] PCI: Setting latency timer of device 0000:00:08.0 to 64
[17179576.120000] ata3: SATA max UDMA/133 cmd 0x9E0 ctl 0xBE2 bmdma 0xF100 irq 2
25
[17179576.120000] ata4: SATA max UDMA/133 cmd 0x960 ctl 0xB62 bmdma 0xF108 irq 2
25
[17179576.128000] SCSI device sda: 586114704 512-byte hdwr sectors (300091 MB)
[17179576.128000] sda: Write Protect is off
[17179576.128000] sda: Mode Sense: 00 3a 00 00
[17179576.128000] SCSI device sda: drive cache: write back
[17179576.128000] SCSI device sda: 586114704 512-byte hdwr sectors (300091 MB)
[17179576.128000] sda: Write Protect is off
[17179576.128000] sda: Mode Sense: 00 3a 00 00
[17179576.128000] SCSI device sda: drive cache: write back
[17179576.128000]  sda: sda1 sda2 < sda5 sda6 >
[17179576.172000] sd 1:0:0:0: Attached scsi disk sda
[17179576.324000] ata3: SATA link down (SStatus 0)
[17179576.324000] scsi2 : sata_nv
[17179576.528000] ata4: SATA link down (SStatus 0)
[17179576.528000] scsi3 : sata_nv
[17179576.528000] NFORCE-CK804: IDE controller at PCI slot 0000:00:06.0
[17179576.528000] NFORCE-CK804: chipset revision 242
[17179576.528000] NFORCE-CK804: not 100% native mode: will probe irqs later
[17179576.528000] NFORCE-CK804: 0000:00:06.0 (rev f2) UDMA133 controller
[17179576.528000]     ide0: BM-DMA at 0xfb00-0xfb07, BIOS settings: hda:DMA, hdb
:DMA
[17179576.528000]     ide1: BM-DMA at 0xfb08-0xfb0f, BIOS settings: hdc:DMA, hdd
:DMA
[17179576.528000] Probing IDE interface ide0...
[17179577.096000] Probing IDE interface ide1...
[17179577.832000] hdc: MAD DOG MD-16XDVD9A2, ATAPI CD/DVD-ROM drive
[17179578.504000] ide1 at 0x170-0x177,0x376 on irq 15
[17179578.512000] hdc: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA
(33)
[17179578.512000] Uniform CD-ROM driver Revision: 3.20
[17179578.652000] Probing IDE interface ide0...
[17179578.684000] usbcore: registered new driver usbfs
[17179578.684000] usbcore: registered new driver hub
[17179578.688000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI)
Driver (PCI)
[17179578.688000] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 21
[17179578.688000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 21 (
level, low) -> IRQ 233
[17179578.688000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[17179578.688000] ohci_hcd 0000:00:02.0: OHCI Host Controller
[17179578.688000] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus nu
mber 1
[17179578.716000] ohci_hcd 0000:00:02.0: irq 233, io mem 0xfe02f000
[17179578.764000] forcedeth.c: Reverse Engineered nForce ethernet driver. Versio
n 0.54.
[17179578.776000] usb usb1: configuration #1 chosen from 1 choice
[17179578.776000] hub 1-0:1.0: USB hub found
[17179578.776000] hub 1-0:1.0: 10 ports detected
[17179578.880000] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 20
[17179578.880000] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCL] -> GSI 20 (
level, low) -> IRQ 50
[17179578.880000] PCI: Setting latency timer of device 0000:00:02.1 to 64
[17179578.880000] ehci_hcd 0000:00:02.1: EHCI Host Controller
[17179578.880000] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus nu
mber 2
[17179578.880000] ehci_hcd 0000:00:02.1: debug port 1
[17179578.880000] PCI: cache line size of 64 is not supported by device 0000:00:
02.1
[17179578.880000] ehci_hcd 0000:00:02.1: irq 50, io mem 0xfeb00000
[17179578.880000] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 D
ec 2004
[17179578.880000] usb usb2: configuration #1 chosen from 1 choice
[17179578.880000] hub 2-0:1.0: USB hub found
[17179578.880000] hub 2-0:1.0: 10 ports detected
[17179578.984000] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
[17179578.984000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [APCH] -> GSI 23 (
level, low) -> IRQ 217
[17179578.984000] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[17179578.984000] forcedeth: using HIGHDMA
[17179579.224000] ohci_hcd 0000:00:02.0: wakeup
[17179579.504000] eth0: forcedeth.c: subsystem: 01462:7135 bound to 0000:00:0a.0
[17179579.608000] usb 1-1: new low speed USB device using ohci_hcd and address 2
[17179579.752000] EXT3-fs: INFO: recovery required on readonly filesystem.
[17179579.752000] EXT3-fs: write access will be enabled during recovery.
[17179579.820000] usb 1-1: configuration #1 chosen from 1 choice
[17179579.832000] usbcore: registered new driver hiddev
[17179579.840000] input: Logitech Optical USB Mouse as /class/input/input1
[17179579.840000] input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb
-0000:00:02.0-1
[17179579.840000] usbcore: registered new driver usbhid
[17179579.840000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179582.216000] kjournald starting.  Commit interval 5 seconds
[17179582.216000] EXT3-fs: sda6: orphan cleanup on readonly fs
[17179582.216000] ext3_orphan_cleanup: deleting unreferenced inode 14467079
[17179582.632000] ext3_orphan_cleanup: deleting unreferenced inode 15482894
[17179582.632000] ext3_orphan_cleanup: deleting unreferenced inode 15482893
[17179582.632000] EXT3-fs: sda6: 3 orphan inodes deleted
[17179582.632000] EXT3-fs: recovery complete.
[17179582.692000] EXT3-fs: mounted filesystem with ordered data mode.
[17179591.424000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179591.428000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179591.480000] FDC 0 is a post-1991 82077
[17179591.524000] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x4c00
[17179591.524000] i2c_adapter i2c-1: nForce2 SMBus adapter at 0x4c40
[17179591.576000] Real Time Clock Driver v1.12ac
[17179591.880000] Linux agpgart interface v0.101 (c) Dave Jones
[17179591.944000] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 22
[17179591.944000] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [APCJ] -> GSI 22 (
level, low) -> IRQ 225
[17179591.944000] PCI: Setting latency timer of device 0000:00:04.0 to 64
[17179592.264000] intel8x0_measure_ac97_clock: measured 54742 usecs
[17179592.264000] intel8x0: clocking to 46921
[17179592.432000] input: PC Speaker as /class/input/input2
[17179592.464000] parport: PnPBIOS parport detected.
[17179592.464000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[17179592.492000] Linux video capture interface: v1.00
[17179592.600000] saa7130/34: v4l2 driver version 0.2.14 loaded
[17179592.600000] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[17179592.600000] ACPI: PCI Interrupt 0000:01:08.0[A] -> Link [APC3] -> GSI 18 (
level, low) -> IRQ 58
[17179592.600000] saa7130[0]: found at 0000:01:08.0, rev: 1, irq: 58, latency: 1
5, mmio: 0xfdeff000
[17179592.600000] PCI: Setting latency timer of device 0000:01:08.0 to 64
[17179592.600000] saa7130[0]: subsystem: 1131:0000, board: LifeView FlyVIDEO3000
 [card=2,insmod option]
[17179592.600000] saa7130[0]: board init: gpio is 3f000
[17179592.600000] saa7130[0]: there are different flyvideo cards with different
tuners
[17179592.600000] saa7130[0]: out there, you might have to use the tuner=<nr> in
smod
[17179592.600000] saa7130[0]: option to override the default value.
[17179592.600000] input: saa7134 IR (LifeView FlyVIDEO30 as /class/input/input3
[17179592.636000] nvidia: module license 'NVIDIA' taints kernel.
[17179592.676000] ts: Compaq touchscreen protocol output
[17179592.724000] saa7130[0]: Huh, no eeprom present (err=-5)?
[17179592.744000] tuner 2-0061: chip found @ 0xc2 (saa7130[0])
[17179592.744000] tuner 2-0061: type set to 17 (Philips NTSC_M (MK2))
[17179592.744000] saa7130[0]: registered device video0 [v4l2]
[17179592.744000] saa7130[0]: registered device vbi0
[17179592.744000] saa7130[0]: registered device radio0
[17179592.768000] ACPI: PCI Interrupt 0000:05:00.0[A] -> Link [APC3] -> GSI 18 (
level, low) -> IRQ 58
[17179592.768000] PCI: Setting latency timer of device 0000:05:00.0 to 64
[17179592.768000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8776  Mon Oc
t 16 21:56:04 PDT 2006
[17179593.040000] sd 1:0:0:0: Attached scsi generic sg0 type 0
[17179593.052000] saa7134 ALSA driver for DMA sound loaded
[17179593.052000] saa7130[0]/alsa: saa7130[0] at 0xfdeff000 irq 58 registered as
 card 1
[17179593.400000] lp0: using parport0 (interrupt-driven).
[17179593.472000] Adding 4192924k swap on /dev/disk/by-uuid/53471b4d-3edc-490f-9
4ac-62af43ce8029.  Priority:-1 extents:1 across:4192924k
[17179593.584000] NET: Registered protocol family 17
[17179593.588000] EXT3 FS on sda6, internal journal
[17179593.800000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179593.800000] md: bitmap version 4.39
[17179593.820000] NET: Registered protocol family 10
[17179593.820000] lo: Disabled Privacy Extensions
[17179593.820000] IPv6 over IPv4 tunneling driver
[17179593.992000] device-mapper: 4.6.0-ioctl (2006-02-17) initialised: dm-devel@
redhat.com
[17179594.708000] NTFS driver 2.1.27 [Flags: R/O MODULE].
[17179594.756000] NTFS volume version 3.1.
[17179600.876000] ACPI: Power Button (FF) [PWRF]
[17179600.876000] ACPI: Power Button (CM) [PWRB]
[17179600.976000] ibm_acpi: ec object not found
[17179601.008000] pcc_acpi: loading...
[17179601.332000] powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (versi              on 1.60.2)
[17179601.336000] powernow-k8: BIOS error - no PSB or ACPI _PSS objects
[17179601.364000] acpi_cpufreq: Unknown symbol cpu_online_map
[17179602.516000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[17179602.516000] apm: overridden by ACPI.
[17179603.876000] eth0: no IPv6 routers present
[17179605.424000] Bluetooth: Core ver 2.8
[17179605.424000] NET: Registered protocol family 31
[17179605.424000] Bluetooth: HCI device and connection manager initialized
[17179605.424000] Bluetooth: HCI socket layer initialized
[17179605.448000] Bluetooth: L2CAP ver 2.8
[17179605.448000] Bluetooth: L2CAP socket layer initialized
[17179605.452000] Bluetooth: HIDP (Human Interface Emulation) ver 1.1-mh1
[17179605.484000] Bluetooth: RFCOMM socket layer initialized
[17179605.484000] Bluetooth: RFCOMM TTY layer initialized
[17179605.484000] Bluetooth: RFCOMM ver 1.7
russ@russ-desktop:~$

```

so if someone knows what maybe wrong i would appreciate any help on what i did wrong, and thanks again to the community for taking time to help me with this.

peace mr pixels0

---

### Post by mrpixels0 on 2006-12-20
well i have finally solved the sound problem for my tv card and it was so simple i almost cried :)

all i had to do was run the KDETV channel wizard and select the television (mono only) option and it just worked perfectly.

so the only thing that worked without a lot of trouble and is usually a pain to setup is the IR module. it worked right away with no configuring at all.

well it has been a long 29 hours but i got it all working and i am pleased with the results and i owe it all to renzokuken with whos link help i would have never found the information i needed (all my google searching found forums with similar problems to my own) thanks to him/her and this wonderful community.

MP0

---

### Post by DrMega on 2006-12-20
> **mrpixels0 said:**
> hello there Drmega :)

No my card is a very simple $5.00 tuner just analog i'm afraid, as for digital cards i have no idea how they work sorry,

what chipset is it using for it's analog ?, in this thread at the top is a Link given to me by renzokuken and it has a lot of Useful information there that is how i got my card working in mere minutes.

if you have not tried there i would suggest starting there as i did, good luck to you and if you succeed then please post and share how you did it, this way others who have the same card as you can benefit from what you have learned.

MP0

I'm a bit closer, but when I run the command :

sudo rmmod saa7134_alsa && sudo rmmod saa7134 && sudo modprobe saa7134


.... I get:

ERROR: Module saa7134_alsa is in use


.... I can't seem to get the modules to unload. Any ideas?

---

### Post by mrpixels0 on 2006-12-20
yeah i had that problem too, what you have to is ctrl-alt-f1 to shutdown the KDM desktop this also stops and unloads the alsa modules then run the command. you will have to do this everytime you make a change to modprobe.d / saa7134 (the file that is)

hope this helps.

MP0

---

### Post by DrMega on 2006-12-20
> **mrpixels0 said:**
> yeah i had that problem too, what you have to is ctrl-alt-f1 to shutdown the KDM desktop this also stops and unloads the alsa modules then run the command. you will have to do this everytime you make a change to modprobe.d / saa7134 (the file that is)

hope this helps.

MP0

Thanks for this. I've been able to run the commands now without any errors, but still no luck. As a last resort I booted into Windows where I know the card had been working, but now it seems it isn't working in Windows anymore. To sort out an earlier sound problem I put an old Soundblaster card in. That's the only hardware change I've made to the system since I last saw the tuner card working under Windows. Without dismantling my machine again is there any way to test the hardware and/or check for conflicts?

---

### Post by DrMega on 2006-12-21
Update: I got the card working again under Windows. I removed the old Soundblaster card and went back to onboard sound. There must have been some sort of conflict between the PCI cards.

Now the card works under Windows, I set about trying to get it going again under Ubuntu, but with no luck. I've create a called saa7134 in a folder called modprobe.d, done the rmmods and modprobe 7134, then tvtime-scanner, but no luck.

The file I put the Option card=50 tuner=33 in did not exist until I created it. Does this give any clues? I have no idea whether the file I created is making any difference. is there anyway to tell?

If I start Ubuntu in recovery mode and run tvtime-scanner, it produces loads of output, each line telling me that the tuner has no way to set the frequency.

---

### Post by mrpixels0 on 2006-12-22
hey doc sorry about the slow resonse time (I work too much) any ways i had to manually set the card type and tuner type but it took some playing around to find the right one, who  is the manufacturer  of your card ?. and is he chipset a phillips 7134 set. if you could give me these details i think i could help you better solve your problems.

MP0

---

### Post by Mariusz on 2007-01-17
LSUSB 

us 004 Device 003: ID 185b:3000 Compro

I try to find the card and tuner number but ther is no informations aboute this card. I use this script 

```
#!/bin/sh 
MAXTUNER=99 
MAXKARTA=99 
i=0 
j=0 
while [ $j -lt $MAXKARTA]; 
do 
while [ $i -lt $MAXTUNER]; 
do 
rmmod tuner saa7134 
modprobe saa7134 card=25 tuner=$i 
Echo " karta:" $j "tuner :" $i 
sleep 1 
tvtime-scan 
i=$(($i+1)) 
done 
j=$(($j+1)) 
i=0; 
done 

```

When TVTime start I get 

videoinput: Cannot open capture device /dev/video0 no such file

---

### Post by DrMega on 2007-01-21
> **mrpixels0 said:**
> hey doc sorry about the slow resonse time (I work too much) any ways i had to manually set the card type and tuner type but it took some playing around to find the right one, who  is the manufacturer  of your card ?. and is he chipset a phillips 7134 set. if you could give me these details i think i could help you better solve your problems.

MP0

The card is a Pinnacle 300i. I found the card number and tuner number (not got them handy but I can get them). I followed someones advice and created a file called saa7134.d or something, and put the card number and tuner type in it, but it made no difference and I have to admit I wasn't entirely sure I'd done it right.

The trouble is I'm still very much a linux novice, and much of the advice on the internet seems to assume that the reader knows a fair bit about linux. What I could do with is a step by step guide.

---

### Post by Mariusz on 2007-03-26
> **Mariusz said:**
> LSUSB 

us 004 Device 003: ID 185b:3000 Compro

I try to find the card and tuner number but ther is no informations aboute this card. I use this script 

```
#!/bin/sh 
MAXTUNER=99 
MAXKARTA=99 
i=0 
j=0 
while [ $j -lt $MAXKARTA]; 
do 
while [ $i -lt $MAXTUNER]; 
do 
rmmod tuner saa7134 
modprobe saa7134 card=25 tuner=$i 
Echo " karta:" $j "tuner :" $i 
sleep 1 
tvtime-scan 
i=$(($i+1)) 
done 
j=$(($j+1)) 
i=0; 
done 

```

When TVTime start I get 

videoinput: Cannot open capture device /dev/video0 no such file


Any one ??

---

### Post by rabigras on 2007-05-01
> **mrpixels0 said:**
> Actually i had no idea that page was there, thanks for the Link :), i now have a working tv card / remote control yes !!!!.

if anyone is intrested here is what i did to make it work:

1. sudo nano /etc/modprobe.d/saa1734

2. added these lines to the file
    
    alias char-major-81 videodev
    alias char-major-81-0 saa7134
    options saa7134 card=2 tuner=17 oss=1

3. sudo rmmod saa7134_alsa && sudo rmmod saa7134 && sudo modprobe saa7134

 and now i can use my tv tuner card that is made by: a compnay known only as "power tv" or at least that is what the FCC I.D. has it listed as some place in china. but it works and that is all that matters. and i am sure that this would work with other super Generic cards like mine that also sport a Phillips 713x chipset.

it seems this card is known to bttv as a fly3000 seris card  (hope that makes sense to someone) according to dmesg.
thanks again  renzokuken for the link you are the greatest ! :)

Peace mrpixels0


Here are my settings:
alias char-major-81 videodev
alias char-major-81-0 saa7134
options saa7134 card=3 tuner=40 oss=0

My card is from Sabrant, for newbies out there, the card number is the location of the card in your computer, in my case it's in the 4th slot, being card 3 cause the first one is card 0 . then you can hit and miss on the tuner. 
Make sure when your changing parameters that you close your TV Tuner program because your changes will not take effect.
Roger.

---

### Post by DigiNeT on 2007-05-15
> **mrpixels0 said:**
> Actually i had no idea that page was there, thanks for the Link :), i now have a working tv card / remote control yes !!!!.

if anyone is intrested here is what i did to make it work:

1. sudo nano /etc/modprobe.d/saa1734

2. added these lines to the file
    
    alias char-major-81 videodev
    alias char-major-81-0 saa7134
    options saa7134 card=2 tuner=17 oss=1

3. sudo rmmod saa7134_alsa && sudo rmmod saa7134 && sudo modprobe saa7134

 and now i can use my tv tuner card that is made by: a compnay known only as "power tv" or at least that is what the FCC I.D. has it listed as some place in china. but it works and that is all that matters. and i am sure that this would work with other super Generic cards like mine that also sport a Phillips 713x chipset.

it seems this card is known to bttv as a fly3000 seris card  (hope that makes sense to someone) according to dmesg.
thanks again  renzokuken for the link you are the greatest ! :)

Peace mrpixels0

I have the same card like you.
Its working fine and i can tune my channels now. :D

---

