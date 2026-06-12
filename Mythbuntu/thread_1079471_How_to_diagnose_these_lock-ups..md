---
title: "How to diagnose these lock-ups."
date: 2009-02-24
forum: Mythbuntu
---

### Post by mike909 on 2009-02-24
At seemingly random times it locks up. Sometimes I can still access the box via ssh, and other times not at all. This happens during live-tv, playback of recorded tv, or playback of DVD's (both on disk, and ripped). I can reproduce the issue by playing a Tarzan DVD ( it locks up after I hit play on the main menu).
I have attached the logs. This particular crash happned at 8:17 on Feb 24. I have run memtest over night with 0 fails. I can run mprime to check the cpu, but I don't think it's a hardware issue. I had MCE running ok for about 2 years on the box and Myth works great, when it's not crashed. The crashes appear to be random (with the exception of this Tarzan crash, which I can reproduce).

Below are my specs and version info:
[B]Hardware:
Motherboard:[/B]
A8N-SLI DELUXE
Product Link= [http://usa.asus.com/products.aspx?l1=3&l2=15&l3=0&model=375&modelmenu=1](http://usa.asus.com/products.aspx?l1=3&l2=15&l3=0&model=375&modelmenu=1)
**CPU:**
AMD Athlon(tm) 64 Processor 3500+
**Memory:**
1G  DIMM 400 MHz (2.5 ns)
**Capture Card:**
Happauge PVR-500
**Sound Card:**
product: CK804 AC'97 Audio Controller
          vendor: nVidia Corporation
          physical id: 5
          bus info: pci@0000:00:04.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm bus_master cap_list
          configuration: driver=Intel ICH latency=0 maxlatency=5 mingnt=2 module=snd_intel8x0
**Optical Drive:**
             description: DVD writer
             product: CD/DVDW TS-H552U
             vendor: TSSTcorp
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/scd0
             logical name: /dev/sr0
             version: US06
             capabilities: removable audio cd-r cd-rw dvd dvd-r
             configuration: ansiversion=5 status=nodisc
[B]Hard Drives:
Boot drive:[/B]
ATA Disk
             product: SAMSUNG HD040GJ
             bus info: scsi@4:0.0.0
             logical name: /dev/sda
             version: WY10
**Storage drive:**
ATA Disk
             product: ST31500341AS
             vendor: Seagate
             physical id: 1
             bus info: scsi@5:0.0.0
             logical name: /dev/sdb
**$ df**
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             10175300   2424408   7234004  26% /
tmpfs                   516732         0    516732   0% /lib/init/rw
varrun                  516732       352    516380   1% /var/run
varlock                 516732         0    516732   0% /var/lock
udev                    516732      2752    513980   1% /dev
tmpfs                   516732         0    516732   0% /dev/shm
lrm                     516732      2004    514728   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sda6             27843076    324204  27518872   2% /var/lib
/dev/sdb1            1442145212 517623024 851265388  38% /media/storage

**Software:**
$ uname -a
Linux mike-desktop 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux
Mythbuntu 8.10
$ dpkg -l | grep mythtv
 mythtv                                     0.21.0+fixes18722-0ubuntu1
 mythtv-backend                             0.21.0+fixes18722-0ubuntu1
 mythtv-backend-master                      0.21.0+fixes18722-0ubuntu1
 mythtv-common                              0.21.0+fixes18722-0ubuntu1
 mythtv-database                            0.21.0+fixes18722-0ubuntu1
 mythtv-frontend                            0.21.0+fixes18722-0ubuntu1
[B]
Tuner card driver:[/B]
multimedia:0
                description: Multimedia video controller
                product: iTVC16 (CX23416) MPEG-2 Encoder
                vendor: Internext Compression Inc
                physical id: 8
                bus info: pci@0000:06:08.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ivtv latency=64 maxlatency=8 mingnt=128 module=ivtv

**$ sudo lspci**
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8500 GT (rev a1)
05:08.0 PCI bridge: Hint Corp HB6 Universal PCI-PCI bridge (non-transparent mode) (rev 11)
05:0b.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
05:0c.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
06:08.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)


** *-display**
             description: VGA compatible controller
             product: GeForce 8500 GT
             vendor: nVidia Corporation
             physical id: 0
             bus info: pci@0000:01:00.0
             version: a1
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=nvidia latency=0 module=nvidia
[I]
dmesg output attached
Log files attached[/I]

---

### Post by TMcC on 2009-02-24
Have you tried upgrading your Nvidia driver to 180.29?

There's one at: [http://www.avenard.org/files/ubuntu-repos/release/](http://www.avenard.org/files/ubuntu-repos/release/)

Not sure that's going to make any difference though. You have some odd segfaults in kern.log

---

### Post by mike909 on 2009-02-24
I have not tried those drivers. I can give that a shot. Hopefully the documentation on how to remove the old ones and install the new ones is straight forward.

---

### Post by TMcC on 2009-02-24
I think you've got 180.22 installed, it should be straightforward to go to 180.29 by installing the deb from the posted link?

---

### Post by mike909 on 2009-02-24
I believe i'm on 177 (see below)...
$ dpkg -l | grep nvidia
ii  nvidia-173-modaliases                      173.14.12-1-0ubuntu5.1                  Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-177-kernel-source                   177.82-0ubuntu0.1                       NVIDIA binary kernel module source
ii  nvidia-177-modaliases                      177.82-0ubuntu0.1                       Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-71-modaliases                       71.86.04-0ubuntu10                      Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-96-modaliases                       96.43.09-0ubuntu1.1                     Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-common                              0.2.4                                   Find obsolete NVIDIA drivers
ii  nvidia-glx-177                             177.82-0ubuntu0.1                       NVIDIA binary Xorg driver
ii  nvidia-settings                            177.78-0ubuntu2.1                       Tool of configuring the NVIDIA graphics driv

---

### Post by TMcC on 2009-02-24
Ah, woops. 177.82 sorry. Should have bought those reading glasses (binoculars) after all....

Your graphics card, 8500 GT, can support HD (?) - so probably worth trying to update to the 180 series anyway?

Hmm, could be hard to go from 177 to 180, as lots of myth dependencies.

---

### Post by mike909 on 2009-02-28
On this last crash I noticed something interesting in the "kern" log:
No idea what it means, but here it is:
```
Feb 25 05:08:17 10.0.0.102 kernel: [23873.396424] mythfrontend.re[5921]: segfault at 5024548b ip b506b095 sp bfaaa56c error 4 in libGLcore.so.177.82[b4a9f000+bc8000]
Feb 25 14:17:24 10.0.0.102 kernel: [56817.092723] mythfilldatabas[15167] general protection ip:a04ab72 sp:b48e87ec error:2494
Feb 25 19:24:54 10.0.0.102 kernel: [75265.535284] sr 0:0:0:0: [sr0] unaligned transfer
Feb 25 19:24:54 10.0.0.102 kernel: [75265.535293] Buffer I/O error on device sr0, logical block 64
Feb 25 19:24:54 10.0.0.102 kernel: [75265.535301] sr 0:0:0:0: [sr0] unaligned transfer
Feb 25 19:24:54 10.0.0.102 kernel: [75265.535304] Buffer I/O error on device sr0, logical block 65
Feb 25 19:24:54 10.0.0.102 kernel: [75265.535310] sr 0:0:0:0: [sr0] unaligned transfer
Feb 25 19:24:54 10.0.0.102 kernel: [75265.535312] Buffer I/O error on device sr0, logical block 66
Feb 25 19:24:54 10.0.0.102 kernel: [75265.535318] sr 0:0:0:0: [sr0] unaligned transfer
Feb 25 19:24:54 10.0.0.102 kernel: [75265.535320] Buffer I/O error on device sr0, logical block 67
Feb 25 19:24:54 10.0.0.102 kernel: [75265.535326] sr 0:0:0:0: [sr0] unaligned transfer
Feb 25 19:24:54 10.0.0.102 kernel: [75265.535328] Buffer I/O error on device sr0, logical block 68
Feb 25 19:24:54 10.0.0.102 kernel: [75265.541295] sr 0:0:0:0: [sr0] unaligned transfer
Feb 25 19:24:54 10.0.0.102 kernel: [75265.541301] Buffer I/O error on device sr0, logical block 69
Feb 25 19:24:54 10.0.0.102 kernel: [75265.541305] Buffer I/O error on device sr0, logical block 70
Feb 25 19:24:54 10.0.0.102 kernel: [75265.541307] Buffer I/O error on device sr0, logical block 71
Feb 25 19:24:54 10.0.0.102 kernel: [75265.703981] sr 0:0:0:0: [sr0] unaligned transfer
Feb 25 19:24:54 10.0.0.102 kernel: [75265.703991] Buffer I/O error on device sr0, logical block 16
Feb 25 19:24:54 10.0.0.102 kernel: [75265.705227] sr 0:0:0:0: [sr0] unaligned transfer
Feb 25 19:24:54 10.0.0.102 kernel: [75265.705232] Buffer I/O error on device sr0, logical block 17
Feb 25 19:24:54 10.0.0.102 kernel: [75265.705382] sr 0:0:0:0: [sr0] unaligned transfer
Feb 25 19:24:54 10.0.0.102 kernel: [75265.707142] sr 0:0:0:0: [sr0] unaligned transfer
Feb 25 19:24:54 10.0.0.102 kernel: [75265.707714] sr 0:0:0:0: [sr0] unaligned transfer
Feb 25 19:25:02 10.0.0.102 kernel: [75273.475703] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Feb 25 19:25:02 10.0.0.102 kernel: [75273.475712] sr 0:0:0:0: [sr0] Sense Key : Hardware Error [current] 
Feb 25 19:25:02 10.0.0.102 kernel: [75273.475716] sr 0:0:0:0: [sr0] Add. Sense: Timeout on logical unit
Feb 25 19:25:02 10.0.0.102 kernel: [75273.475722] end_request: I/O error, dev sr0, sector 1422912
Feb 25 19:25:02 10.0.0.102 kernel: [75273.475727] __ratelimit: 54 callbacks suppressed
Feb 25 19:25:02 10.0.0.102 kernel: [75273.475730] Buffer I/O error on device sr0, logical block 355728
Feb 25 19:25:09 10.0.0.102 kernel: [75280.542256] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Feb 25 19:25:09 10.0.0.102 kernel: [75280.542264] sr 0:0:0:0: [sr0] Sense Key : Hardware Error [current] 
Feb 25 19:25:09 10.0.0.102 kernel: [75280.542269] sr 0:0:0:0: [sr0] Add. Sense: Timeout on logical unit
Feb 25 19:25:09 10.0.0.102 kernel: [75280.542274] end_request: I/O error, dev sr0, sector 1422912
Feb 25 19:25:09 10.0.0.102 kernel: [75280.542281] Buffer I/O error on device sr0, logical block 355728
Feb 25 19:25:16 10.0.0.102 kernel: [75287.759331] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Feb 25 19:25:16 10.0.0.102 kernel: [75287.759340] sr 0:0:0:0: [sr0] Sense Key : Hardware Error [current] 
Feb 25 19:25:16 10.0.0.102 kernel: [75287.759344] sr 0:0:0:0: [sr0] Add. Sense: Timeout on logical unit
Feb 25 19:25:16 10.0.0.102 kernel: [75287.759350] end_request: I/O error, dev sr0, sector 1422912
Feb 25 19:25:16 10.0.0.102 kernel: [75287.759357] Buffer I/O error on device sr0, logical block 355728
Feb 25 19:25:23 10.0.0.102 kernel: [75294.880896] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Feb 25 19:25:23 10.0.0.102 kernel: [75294.880904] sr 0:0:0:0: [sr0] Sense Key : Hardware Error [current] 
Feb 25 19:25:23 10.0.0.102 kernel: [75294.880909] sr 0:0:0:0: [sr0] Add. Sense: Timeout on logical unit
Feb 25 19:25:23 10.0.0.102 kernel: [75294.880915] end_request: I/O error, dev sr0, sector 1422912
Feb 25 19:25:23 10.0.0.102 kernel: [75294.880921] Buffer I/O error on device sr0, logical block 355728
Feb 25 19:25:30 10.0.0.102 kernel: [75302.115814] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Feb 25 19:25:30 10.0.0.102 kernel: [75302.115822] sr 0:0:0:0: [sr0] Sense Key : Hardware Error [current] 
Feb 25 19:25:30 10.0.0.102 kernel: [75302.115826] sr 0:0:0:0: [sr0] Add. Sense: Timeout on logical unit
Feb 25 19:25:30 10.0.0.102 kernel: [75302.115832] end_request: I/O error, dev sr0, sector 1422912
Feb 25 19:25:30 10.0.0.102 kernel: [75302.115838] Buffer I/O error on device sr0, logical block 355728
Feb 25 19:25:37 10.0.0.102 kernel: [75309.279623] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Feb 25 19:25:37 10.0.0.102 kernel: [75309.279632] sr 0:0:0:0: [sr0] Sense Key : Hardware Error [current] 
Feb 25 19:25:37 10.0.0.102 kernel: [75309.279636] sr 0:0:0:0: [sr0] Add. Sense: Timeout on logical unit
Feb 25 19:25:37 10.0.0.102 kernel: [75309.279642] end_request: I/O error, dev sr0, sector 1422912
Feb 25 19:25:37 10.0.0.102 kernel: [75309.279648] Buffer I/O error on device sr0, logical block 355728
Feb 25 19:25:45 10.0.0.102 kernel: [75316.483286] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Feb 25 19:25:45 10.0.0.102 kernel: [75316.483294] sr 0:0:0:0: [sr0] Sense Key : Hardware Error [current] 
Feb 25 19:25:45 10.0.0.102 kernel: [75316.483298] sr 0:0:0:0: [sr0] Add. Sense: Timeout on logical unit
Feb 25 19:25:45 10.0.0.102 kernel: [75316.483304] end_request: I/O error, dev sr0, sector 1422912
Feb 25 19:25:45 10.0.0.102 kernel: [75316.483310] Buffer I/O error on device sr0, logical block 355728
Feb 25 19:25:45 10.0.0.102 kernel: [75316.563865] UDF-fs: No VRS found
Feb 25 19:25:52 10.0.0.102 kernel: [75323.938862] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Feb 25 19:25:52 10.0.0.102 kernel: [75323.938870] sr 0:0:0:0: [sr0] Sense Key : Hardware Error [current] 
Feb 25 19:25:52 10.0.0.102 kernel: [75323.938874] sr 0:0:0:0: [sr0] Add. Sense: Timeout on logical unit
Feb 25 19:25:52 10.0.0.102 kernel: [75323.938880] end_request: I/O error, dev sr0, sector 1422512
Feb 25 19:25:52 10.0.0.102 kernel: [75323.938886] Buffer I/O error on device sr0, logical block 355628
Feb 25 19:25:52 10.0.0.102 kernel: [75323.938890] Buffer I/O error on device sr0, logical block 355629
Feb 25 19:26:00 10.0.0.102 kernel: [75331.427323] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Feb 25 19:26:00 10.0.0.102 kernel: [75331.427331] sr 0:0:0:0: [sr0] Sense Key : Hardware Error [current] 
Feb 25 19:26:00 10.0.0.102 kernel: [75331.427335] sr 0:0:0:0: [sr0] Add. Sense: Timeout on logical unit
Feb 25 19:26:00 10.0.0.102 kernel: [75331.427341] end_request: I/O error, dev sr0, sector 1422904
Feb 25 19:26:00 10.0.0.102 kernel: [75331.427347] Buffer I/O error on device sr0, logical block 355726
Feb 25 19:26:00 10.0.0.102 kernel: [75331.427352] Buffer I/O error on device sr0, logical block 355727
Feb 25 19:26:07 10.0.0.102 kernel: [75338.656532] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Feb 25 19:26:07 10.0.0.102 kernel: [75338.656539] sr 0:0:0:0: [sr0] Sense Key : Hardware Error [current] 
Feb 25 19:26:07 10.0.0.102 kernel: [75338.656544] sr 0:0:0:0: [sr0] Add. Sense: Timeout on logical unit
Feb 25 19:26:07 10.0.0.102 kernel: [75338.656549] end_request: I/O error, dev sr0, sector 1422912
Feb 25 19:26:07 10.0.0.102 kernel: [75338.656555] Buffer I/O error on device sr0, logical block 355728
Feb 25 19:26:14 10.0.0.102 kernel: [75345.945878] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Feb 25 19:26:14 10.0.0.102 kernel: [75345.945885] sr 0:0:0:0: [sr0] Sense Key : Hardware Error [current] 
Feb 25 19:26:14 10.0.0.102 kernel: [75345.945889] sr 0:0:0:0: [sr0] Add. Sense: Timeout on logical unit
Feb 25 19:26:14 10.0.0.102 kernel: [75345.945895] end_request: I/O error, dev sr0, sector 1422912
Feb 25 19:26:14 10.0.0.102 kernel: [75345.945901] Buffer I/O error on device sr0, logical block 355728
Feb 25 19:26:14 10.0.0.102 kernel: [75345.949050] ISO 9660 Extensions: Microsoft Joliet Level 3
Feb 25 19:26:15 10.0.0.102 kernel: [75346.444043] ISO 9660 Extensions: RRIP_1991A
Feb 25 19:26:23 10.0.0.102 kernel: [75354.739217] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Feb 25 19:26:23 10.0.0.102 kernel: [75354.739224] sr 0:0:0:0: [sr0] Sense Key : Hardware Error [current] 
Feb 25 19:26:23 10.0.0.102 kernel: [75354.739228] sr 0:0:0:0: [sr0] Add. Sense: Timeout on logical unit
Feb 25 19:26:23 10.0.0.102 kernel: [75354.739234] end_request: I/O error, dev sr0, sector 1422912
Feb 25 19:26:23 10.0.0.102 kernel: [75354.739240] Buffer I/O error on device sr0, logical block 355728
Feb 25 19:26:30 10.0.0.102 kernel: [75361.934528] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Feb 25 19:26:30 10.0.0.102 kernel: [75361.934536] sr 0:0:0:0: [sr0] Sense Key : Hardware Error [current] 
Feb 25 19:26:30 10.0.0.102 kernel: [75361.934541] sr 0:0:0:0: [sr0] Add. Sense: Timeout on logical unit
Feb 25 19:26:30 10.0.0.102 kernel: [75361.934546] end_request: I/O error, dev sr0, sector 1422912
Feb 25 19:26:30 10.0.0.102 kernel: [75361.934552] Buffer I/O error on device sr0, logical block 355728
Feb 25 19:26:38 10.0.0.102 kernel: [75369.396178] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Feb 25 19:26:38 10.0.0.102 kernel: [75369.396186] sr 0:0:0:0: [sr0] Sense Key : Hardware Error [current] 
Feb 25 19:26:38 10.0.0.102 kernel: [75369.396190] sr 0:0:0:0: [sr0] Add. Sense: Timeout on logical unit
Feb 25 19:26:38 10.0.0.102 kernel: [75369.396196] end_request: I/O error, dev sr0, sector 1422912
Feb 25 19:26:38 10.0.0.102 kernel: [75369.396203] Buffer I/O error on device sr0, logical block 355728
Feb 25 19:26:45 10.0.0.102 kernel: [75376.963941] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Feb 25 19:26:45 10.0.0.102 kernel: [75376.963950] sr 0:0:0:0: [sr0] Sense Key : Hardware Error [current] 
Feb 25 19:26:45 10.0.0.102 kernel: [75376.963954] sr 0:0:0:0: [sr0] Add. Sense: Timeout on logical unit
Feb 25 19:26:45 10.0.0.102 kernel: [75376.963960] end_request: I/O error, dev sr0, sector 1422912
Feb 25 19:26:45 10.0.0.102 kernel: [75376.963966] Buffer I/O error on device sr0, logical block 355728
Feb 25 19:26:53 10.0.0.102 kernel: [75384.529941] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Feb 25 19:26:53 10.0.0.102 kernel: [75384.529949] sr 0:0:0:0: [sr0] Sense Key : Hardware Error [current] 
Feb 25 19:26:53 10.0.0.102 kernel: [75384.529953] sr 0:0:0:0: [sr0] Add. Sense: Timeout on logical unit
Feb 25 19:26:53 10.0.0.102 kernel: [75384.529958] end_request: I/O error, dev sr0, sector 1422912
Feb 25 19:26:53 10.0.0.102 kernel: [75384.529964] Buffer I/O error on device sr0, logical block 355728
Feb 25 19:27:04 10.0.0.102 kernel: [75395.828247] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Feb 25 19:27:04 10.0.0.102 kernel: [75395.828256] sr 0:0:0:0: [sr0] Sense Key : Hardware Error [current] 
Feb 25 19:27:04 10.0.0.102 kernel: [75395.828260] sr 0:0:0:0: [sr0] Add. Sense: Timeout on logical unit
Feb 25 19:27:04 10.0.0.102 kernel: [75395.828267] end_request: I/O error, dev sr0, sector 1422912
Feb 25 19:27:04 10.0.0.102 kernel: [75395.828273] Buffer I/O error on device sr0, logical block 355728
Feb 25 19:27:12 10.0.0.102 kernel: [75403.799957] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Feb 25 19:27:12 10.0.0.102 kernel: [75403.799965] sr 0:0:0:0: [sr0] Sense Key : Hardware Error [current] 
Feb 25 19:27:12 10.0.0.102 kernel: [75403.799969] sr 0:0:0:0: [sr0] Add. Sense: Timeout on logical unit
Feb 25 19:27:12 10.0.0.102 kernel: [75403.799976] end_request: I/O error, dev sr0, sector 1422512
Feb 25 19:27:12 10.0.0.102 kernel: [75403.799982] Buffer I/O error on device sr0, logical block 355628
Feb 25 19:27:12 10.0.0.102 kernel: [75403.799986] Buffer I/O error on device sr0, logical block 355629
Feb 25 19:27:20 10.0.0.102 kernel: [75411.819513] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Feb 25 19:27:20 10.0.0.102 kernel: [75411.819522] sr 0:0:0:0: [sr0] Sense Key : Hardware Error [current] 
Feb 25 19:27:20 10.0.0.102 kernel: [75411.819526] sr 0:0:0:0: [sr0] Add. Sense: Timeout on logical unit
Feb 25 19:27:20 10.0.0.102 kernel: [75411.819533] end_request: I/O error, dev sr0, sector 1422904
Feb 25 19:27:20 10.0.0.102 kernel: [75411.819539] Buffer I/O error on device sr0, logical block 355726
Feb 25 19:27:20 10.0.0.102 kernel: [75411.819543] Buffer I/O error on device sr0, logical block 355727
Feb 25 19:27:27 10.0.0.102 kernel: [75418.987142] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Feb 25 19:27:27 10.0.0.102 kernel: [75418.987151] sr 0:0:0:0: [sr0] Sense Key : Hardware Error [current] 
Feb 25 19:27:27 10.0.0.102 kernel: [75418.987155] sr 0:0:0:0: [sr0] Add. Sense: Timeout on logical unit
Feb 25 19:27:27 10.0.0.102 kernel: [75418.987161] end_request: I/O error, dev sr0, sector 1422912
Feb 25 19:27:27 10.0.0.102 kernel: [75418.987167] Buffer I/O error on device sr0, logical block 355728
Feb 25 19:27:35 10.0.0.102 kernel: [75426.364389] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Feb 25 19:27:35 10.0.0.102 kernel: [75426.364397] sr 0:0:0:0: [sr0] Sense Key : Hardware Error [current] 
Feb 25 19:27:35 10.0.0.102 kernel: [75426.364401] sr 0:0:0:0: [sr0] Add. Sense: Timeout on logical unit
Feb 25 19:27:35 10.0.0.102 kernel: [75426.364407] end_request: I/O error, dev sr0, sector 1422912
Feb 25 19:27:35 10.0.0.102 kernel: [75426.364413] Buffer I/O error on device sr0, logical block 355728
Feb 25 19:27:43 10.0.0.102 kernel: [75434.769415] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Feb 25 19:27:43 10.0.0.102 kernel: [75434.769425] sr 0:0:0:0: [sr0] Sense Key : Hardware Error [current] 
Feb 25 19:27:43 10.0.0.102 kernel: [75434.769429] sr 0:0:0:0: [sr0] Add. Sense: Timeout on logical unit
Feb 25 19:27:43 10.0.0.102 kernel: [75434.769434] end_request: I/O error, dev sr0, sector 1422912
Feb 25 19:27:43 10.0.0.102 kernel: [75434.769441] Buffer I/O error on device sr0, logical block 355728
Feb 25 19:27:50 10.0.0.102 kernel: [75441.821507] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Feb 25 19:27:50 10.0.0.102 kernel: [75441.821515] sr 0:0:0:0: [sr0] Sense Key : Hardware Error [current] 
Feb 25 19:27:50 10.0.0.102 kernel: [75441.821520] sr 0:0:0:0: [sr0] Add. Sense: Timeout on logical unit
Feb 25 19:27:50 10.0.0.102 kernel: [75441.821526] end_request: I/O error, dev sr0, sector 1422912
Feb 25 19:27:50 10.0.0.102 kernel: [75441.821532] Buffer I/O error on device sr0, logical block 355728
Feb 25 19:27:57 10.0.0.102 kernel: [75449.284962] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Feb 25 19:27:57 10.0.0.102 kernel: [75449.284970] sr 0:0:0:0: [sr0] Sense Key : Hardware Error [current] 
Feb 25 19:27:57 10.0.0.102 kernel: [75449.284974] sr 0:0:0:0: [sr0] Add. Sense: Timeout on logical unit
Feb 25 19:27:57 10.0.0.102 kernel: [75449.284980] end_request: I/O error, dev sr0, sector 1422912
Feb 25 19:27:57 10.0.0.102 kernel: [75449.284987] Buffer I/O error on device sr0, logical block 355728
Feb 25 19:28:05 10.0.0.102 kernel: [75456.786237] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Feb 25 19:28:05 10.0.0.102 kernel: [75456.786246] sr 0:0:0:0: [sr0] Sense Key : Hardware Error [current] 
Feb 25 19:28:05 10.0.0.102 kernel: [75456.786250] sr 0:0:0:0: [sr0] Add. Sense: Timeout on logical unit
Feb 25 19:28:05 10.0.0.102 kernel: [75456.786261] end_request: I/O error, dev sr0, sector 1422912
Feb 25 19:28:05 10.0.0.102 kernel: [75456.786267] Buffer I/O error on device sr0, logical block 355728
Feb 25 19:28:13 10.0.0.102 kernel: [75464.423268] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Feb 25 19:28:13 10.0.0.102 kernel: [75464.423277] sr 0:0:0:0: [sr0] Sense Key : Hardware Error [current] 
Feb 25 19:28:13 10.0.0.102 kernel: [75464.423282] sr 0:0:0:0: [sr0] Add. Sense: Timeout on logical unit
Feb 25 19:28:13 10.0.0.102 kernel: [75464.423288] end_request: I/O error, dev sr0, sector 1422912
Feb 25 19:28:13 10.0.0.102 kernel: [75464.423294] Buffer I/O error on device sr0, logical block 355728
Feb 25 19:28:20 10.0.0.102 kernel: [75471.476102] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Feb 25 19:28:20 10.0.0.102 kernel: [75471.476110] sr 0:0:0:0: [sr0] Sense Key : Hardware Error [current] 
Feb 25 19:28:20 10.0.0.102 kernel: [75471.476114] sr 0:0:0:0: [sr0] Add. Sense: Timeout on logical unit
Feb 25 19:28:20 10.0.0.102 kernel: [75471.476120] end_request: I/O error, dev sr0, sector 1422912
Feb 25 19:28:20 10.0.0.102 kernel: [75471.476126] Buffer I/O error on device sr0, logical block 355728
Feb 25 19:28:27 10.0.0.102 kernel: [75479.073169] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Feb 25 19:28:27 10.0.0.102 kernel: [75479.073176] sr 0:0:0:0: [sr0] Sense Key : Hardware Error [current] 
Feb 25 19:28:27 10.0.0.102 kernel: [75479.073181] sr 0:0:0:0: [sr0] Add. Sense: Timeout on logical unit
Feb 25 19:28:27 10.0.0.102 kernel: [75479.073187] end_request: I/O error, dev sr0, sector 1422512
Feb 25 19:28:27 10.0.0.102 kernel: [75479.073193] Buffer I/O error on device sr0, logical block 355628
Feb 25 19:28:27 10.0.0.102 kernel: [75479.073197] Buffer I/O error on device sr0, logical block 355629
Feb 25 19:28:35 10.0.0.102 kernel: [75486.354805] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Feb 25 19:28:35 10.0.0.102 kernel: [75486.354813] sr 0:0:0:0: [sr0] Sense Key : Hardware Error [current] 
Feb 25 19:28:35 10.0.0.102 kernel: [75486.354818] sr 0:0:0:0: [sr0] Add. Sense: Timeout on logical unit
Feb 25 19:28:35 10.0.0.102 kernel: [75486.354823] end_request: I/O error, dev sr0, sector 1422904
Feb 25 19:28:35 10.0.0.102 kernel: [75486.354829] Buffer I/O error on device sr0, logical block 355726
Feb 25 19:28:35 10.0.0.102 kernel: [75486.354833] Buffer I/O error on device sr0, logical block 355727
Feb 25 19:28:42 10.0.0.102 kernel: [75493.415933] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Feb 25 19:28:42 10.0.0.102 kernel: [75493.415941] sr 0:0:0:0: [sr0] Sense Key : Hardware Error [current] 
Feb 25 19:28:42 10.0.0.102 kernel: [75493.415945] sr 0:0:0:0: [sr0] Add. Sense: Timeout on logical unit
Feb 25 19:28:42 10.0.0.102 kernel: [75493.415950] end_request: I/O error, dev sr0, sector 1422912
Feb 25 19:28:42 10.0.0.102 kernel: [75493.415957] Buffer I/O error on device sr0, logical block 355728
Feb 25 19:28:49 10.0.0.102 kernel: [75500.657748] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Feb 25 19:28:49 10.0.0.102 kernel: [75500.657757] sr 0:0:0:0: [sr0] Sense Key : Hardware Error [current] 
Feb 25 19:28:49 10.0.0.102 kernel: [75500.657761] sr 0:0:0:0: [sr0] Add. Sense: Timeout on logical unit
Feb 25 19:28:49 10.0.0.102 kernel: [75500.657767] end_request: I/O error, dev sr0, sector 1422912
Feb 25 19:28:49 10.0.0.102 kernel: [75500.657774] Buffer I/O error on device sr0, logical block 355728
Feb 26 21:12:22 10.0.0.102 kernel: [168105.157502] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Feb 26 21:12:22 10.0.0.102 kernel: [168105.157511] sr 0:0:0:0: [sr0] Sense Key : Hardware Error [current] 
Feb 26 21:12:22 10.0.0.102 kernel: [168105.157515] sr 0:0:0:0: [sr0] Add. Sense: Timeout on logical unit
Feb 26 21:12:22 10.0.0.102 kernel: [168105.157521] end_request: I/O error, dev sr0, sector 1394152
Feb 26 21:12:22 10.0.0.102 kernel: [168105.157527] Buffer I/O error on device sr0, logical block 348538
Feb 26 21:12:29 10.0.0.102 kernel: [168112.362142] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Feb 26 21:12:29 10.0.0.102 kernel: [168112.362150] sr 0:0:0:0: [sr0] Sense Key : Hardware Error [current] 
Feb 26 21:12:29 10.0.0.102 kernel: [168112.362154] sr 0:0:0:0: [sr0] Add. Sense: Timeout on logical unit
Feb 26 21:12:29 10.0.0.102 kernel: [168112.362160] end_request: I/O error, dev sr0, sector 1394152
Feb 26 21:12:29 10.0.0.102 kernel: [168112.362166] Buffer I/O error on device sr0, logical block 348538
Feb 26 21:12:36 10.0.0.102 kernel: [168119.832759] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Feb 26 21:12:36 10.0.0.102 kernel: [168119.832767] sr 0:0:0:0: [sr0] Sense Key : Hardware Error [current] 
Feb 26 21:12:36 10.0.0.102 kernel: [168119.832771] sr 0:0:0:0: [sr0] Add. Sense: Timeout on logical unit
Feb 26 21:12:36 10.0.0.102 kernel: [168119.832776] end_request: I/O error, dev sr0, sector 1394176
Feb 26 21:12:36 10.0.0.102 kernel: [168119.832783] Buffer I/O error on device sr0, logical block 348544
Feb 26 21:12:36 10.0.0.102 kernel: [168119.832787] Buffer I/O error on device sr0, logical block 348545
Feb 26 21:12:36 10.0.0.102 kernel: [168119.832791] Buffer I/O error on device sr0, logical block 348546
Feb 26 21:12:36 10.0.0.102 kernel: [168119.832794] Buffer I/O error on device sr0, logical block 348547
Feb 26 21:12:36 10.0.0.102 kernel: [168119.832797] Buffer I/O error on device sr0, logical block 348548
Feb 26 21:12:36 10.0.0.102 kernel: [168119.832800] Buffer I/O error on device sr0, logical block 348549
Feb 26 21:12:36 10.0.0.102 kernel: [168119.832803] Buffer I/O error on device sr0, logical block 348550
Feb 26 21:12:36 10.0.0.102 kernel: [168119.832805] Buffer I/O error on device sr0, logical block 348551
Feb 26 21:12:36 10.0.0.102 kernel: [168119.832808] Buffer I/O error on device sr0, logical block 348552
Feb 26 21:12:36 10.0.0.102 kernel: [168119.832811] Buffer I/O error on device sr0, logical block 348553
Feb 27 13:46:30 10.0.0.102 kernel: [58639.004883] mythfilldatabas[15603]: segfault at 4e ip 08698f78 sp b49117ec error 6
Feb 27 14:35:52 10.0.0.102 kernel: [61600.914886] UDF-fs: Partition marked readonly; forcing readonly mount
Feb 27 14:35:52 10.0.0.102 kernel: [61600.931019] UDF-fs INFO UDF: Mounting volume 'TOMUNEW', timestamp 2005/04/22 15:33 (1e20)
Feb 27 14:35:54 10.0.0.102 kernel: [61602.602838] UDF-fs: Partition marked readonly; forcing readonly mount
Feb 27 14:35:54 10.0.0.102 kernel: [61602.619049] UDF-fs INFO UDF: Mounting volume 'TOMUNEW', timestamp 2005/04/22 15:33 (1e20)
Feb 27 15:19:59 10.0.0.102 kernel: [64247.054169] UDF-fs: Partition marked readonly; forcing readonly mount
Feb 27 15:19:59 10.0.0.102 kernel: [64247.068343] UDF-fs INFO UDF: Mounting volume 'VOLUME2DISCB', timestamp 2003/09/01 15:18 (1e20)
Feb 27 15:22:56 10.0.0.102 kernel: [64424.564146] UDF-fs: Partition marked readonly; forcing readonly mount
Feb 27 15:22:56 10.0.0.102 kernel: [64424.564850] UDF-fs INFO UDF: Mounting volume 'VOLUME2DISCB', timestamp 2003/09/01 15:18 (1e20)
Feb 27 16:33:13 10.0.0.102 kernel: [68641.008655] mythfrontend.re[17186]: segfault at 5 ip b669b700 sp ae2e8130 error 4 in libqt-mt.so.3.3.8[b6189000+6f2000]
Feb 27 16:33:25 10.0.0.102 kernel: [68653.176015] UDF-fs: Partition marked readonly; forcing readonly mount
Feb 27 16:33:25 10.0.0.102 kernel: [68653.192329] UDF-fs INFO UDF: Mounting volume 'VOLUME2DISCB', timestamp 2003/09/01 15:18 (1e20)
Feb 27 23:27:17 10.0.0.102 kernel: [93482.422249] ------------[ cut here ]------------
Feb 27 23:27:17 10.0.0.102 kernel: [93482.422257] kernel BUG at /build/buildd/linux-2.6.27/mm/vmscan.c:760!
Feb 27 23:27:17 10.0.0.102 kernel: [93482.422260] invalid opcode: 0000 [#1] SMP 


```

---

### Post by mike909 on 2009-03-10
I have enabled apport, which, from what I can tell, writes crash files when processes crash. [https://wiki.ubuntu.com/Apport]("https://wiki.ubuntu.com/Apport")
So far I have 2 crash files in /var/crash (both are attached.) Looking at syslog at around the timestamp of the mythfrontend crash I also see:
> Mar  9 07:48:00 mike-desktop kernel: [ 6422.915031] mythfrontend.re[6317]: segfault at 5 ip b5f05def sp bfcac3e8 error 4 in libX11.so.6.2.0[b5ecd000+eb000]
Mar  9 07:48:30 mike-desktop lircd-0.8.4a[3741]: removed client


Edit: nevermind, just realized the crash files are ~10MB each. They are called 
 _usr_bin_mythfilldatabase.104.crash
_usr_bin_mythfrontend.real.1000.crash
If anyone would like to see the contents, I'd be happy to post a ftp link or something.

---

