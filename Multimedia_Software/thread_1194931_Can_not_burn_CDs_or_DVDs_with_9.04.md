---
title: "Can not burn CDs or DVDs with 9.04"
date: 2009-06-23
forum: Multimedia Software
---

### Post by henrismail on 2009-06-23
I have recently installed 9.04, burnable CDs and DVDs are now not recognized. It worked fine when I had 8.10.:confused:

---

### Post by regala on 2009-06-23
> **henrismail said:**
> I have recently installed 9.04, burnable CDs and DVDs are now not recognized. It worked fine when I had 8.10.:confused:

model, lscpi, and dmesg please :)
these are the least needed.

---

### Post by henrismail on 2009-06-23
I don't know how to find the model.
```
lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51G [GeForce 6100] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a2)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a2)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a2)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.2 Multimedia audio controller: nVidia Corporation MCP51 AC97 Audio Controller (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:06.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
03:07.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
03:08.0 Communication controller: Agere Systems Device 0620
```

```
[986588.704284] npviewer.bin[12382]: segfault at ff9bea2c ip 00000000ff9bea2c sp 00000000ffc90e4c error 14
[1025863.487221] possible SYN flooding on port 7059. Sending cookies.
[1028442.351710] possible SYN flooding on port 7059. Sending cookies.
[1029298.194545] possible SYN flooding on port 7059. Sending cookies.
[1034609.117432] possible SYN flooding on port 7059. Sending cookies.
[1036295.794629] possible SYN flooding on port 7059. Sending cookies.
[1061016.665588] npviewer.bin[12284]: segfault at eaa63d94 ip 00000000f6c300cf sp 00000000eca52eb0 error 4 in libflashplayer.so[f6845000+96d000]
[1062117.679687] npviewer.bin[27911]: segfault at f1da02e8 ip 00000000f78154f6 sp 00000000eca7b298 error 4 in libc-2.9.so[f779b000+15c000]
[1062117.679735] npviewer.bin[27904]: segfault at f1e5b740 ip 00000000f6dae076 sp 00000000f1addfc0 error 4 in libflashplayer.so[f6889000+96d000]
[1062772.311389] npviewer.bin[31137]: segfault at f3520d8c ip 00000000f78a29e0 sp 00000000f1a91f74 error 4 in libpthread-2.9.so[f789b000+15000]
[1062772.598457] npviewer.bin[30308]: segfault at f555ad6c ip 00000000f6c8e3c3 sp 00000000ec9f8310 error 4 in libflashplayer.so[f6817000+96d000]
[1067349.121462] ath5k phy0: noise floor calibration timeout (2462MHz)
[1072001.688328] possible SYN flooding on port 7059. Sending cookies.
[1077895.587668] PM: Syncing filesystems ... done.
[1077895.589590] PM: Preparing system for mem sleep
[1077895.589594] Freezing user space processes ... (elapsed 0.17 seconds) done.
[1077895.764990] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
[1077895.765075] PM: Entering mem sleep
[1077895.765091] Suspending console(s) (use no_console_suspend to debug)
[1077896.240103] sd 2:0:0:0: [sda] Synchronizing SCSI cache
[1077896.240241] sd 2:0:0:0: [sda] Stopping disk
[1077896.240472] ACPI handle has no context!
[1077896.240785] parport_pc 00:07: disabled
[1077896.241087] ath5k_pci 0000:03:07.0: PCI INT A disabled
[1077896.256069] ACPI handle has no context!
[1077896.272251] forcedeth 0000:00:14.0: wake-up capability disabled by ACPI
[1077896.272254] forcedeth 0000:00:14.0: PME# disabled
[1077896.288195] Intel ICH 0000:00:10.2: PCI INT C disabled
[1077896.288295] sata_nv 0000:00:0e.0: PCI INT A disabled
[1077896.320051] ehci_hcd 0000:00:0b.1: PCI INT B disabled
[1077896.336050] ohci_hcd 0000:00:0b.0: PCI INT A disabled
[1077896.352027] ohci_hcd 0000:00:0b.0: PME# enabled
[1077896.352033] ohci_hcd 0000:00:0b.0: wake-up capability enabled by ACPI
[1077896.352036] ohci_hcd 0000:00:0b.0: PME# enabled
[1077896.352038] ohci_hcd 0000:00:0b.0: wake-up capability enabled by ACPI
[1077896.514875] PM: suspend devices took 0.748 seconds
[1077896.514929] ACPI: Preparing to enter system sleep state S3
[1077896.633106] Disabling non-boot CPUs ...
[1077896.736021] CPU 1 is now offline
[1077896.736024] SMP alternatives: switching to UP code
[1077896.885884] CPU0 attaching NULL sched-domain.
[1077896.885888] CPU1 attaching NULL sched-domain.
[1077896.904401] CPU0 attaching NULL sched-domain.
[1077896.904618] CPU1 is down
[1077896.904618] Back to C!
[1077896.904618] Enabling non-boot CPUs ...
[1077896.904618] SMP alternatives: switching to SMP code
[1077897.053568] Booting processor 1 APIC 0x1 ip 0x6000
[1077896.885719] Initializing CPU#1
[1077896.885719] Calibrating delay using timer specific routine.. 4008.37 BogoMIPS (lpj=8016744)
[1077896.885719] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[1077896.885719] CPU: L2 Cache: 512K (64 bytes/line)
[1077896.885719] CPU: Physical Processor ID: 0
[1077896.885719] CPU: Processor Core ID: 1
[1077897.144210] CPU1: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ stepping 02
[1077897.144249] CPU0 attaching NULL sched-domain.
[1077897.148040] Switched to high resolution mode on CPU 1
[1077897.161089] CPU0 attaching sched-domain:
[1077897.161093]  domain 0: span 0-1 level CPU
[1077897.161095]   groups: 0 1
[1077897.161100] CPU1 attaching sched-domain:
[1077897.161101]  domain 0: span 0-1 level CPU
[1077897.161102]   groups: 1 0
[1077897.161426] CPU1 is up
[1077897.161429] ACPI: Waking up from system sleep state S3
[1077897.162303] ACPI: Unable to turn cooling device [ffff880077836060] 'off'
[1077897.162314] pci 0000:00:00.0: restoring config space at offset 0xf (was 0x0, writing 0xff)
[1077897.162330] pci 0000:00:00.1: restoring config space at offset 0xf (was 0xffffffff, writing 0x0)
[1077897.162334] pci 0000:00:00.1: restoring config space at offset 0xe (was 0xffffffff, writing 0x0)
[1077897.162338] pci 0000:00:00.1: restoring config space at offset 0xd (was 0xffffffff, writing 0x0)
[1077897.162342] pci 0000:00:00.1: restoring config space at offset 0xc (was 0xffffffff, writing 0x0)
[1077897.162346] pci 0000:00:00.1: restoring config space at offset 0xb (was 0xffffffff, writing 0xca8105b)
[1077897.162350] pci 0000:00:00.1: restoring config space at offset 0xa (was 0xffffffff, writing 0x0)
[1077897.162354] pci 0000:00:00.1: restoring config space at offset 0x9 (was 0xffffffff, writing 0x0)
[1077897.162358] pci 0000:00:00.1: restoring config space at offset 0x8 (was 0xffffffff, writing 0x0)
[1077897.162362] pci 0000:00:00.1: restoring config space at offset 0x7 (was 0xffffffff, writing 0x0)
[1077897.162366] pci 0000:00:00.1: restoring config space at offset 0x6 (was 0xffffffff, writing 0x0)
[1077897.162370] pci 0000:00:00.1: restoring config space at offset 0x5 (was 0xffffffff, writing 0x0)
[1077897.162374] pci 0000:00:00.1: restoring config space at offset 0x4 (was 0xffffffff, writing 0x0)
[1077897.162378] pci 0000:00:00.1: restoring config space at offset 0x3 (was 0xffffffff, writing 0x800000)
[1077897.162383] pci 0000:00:00.1: restoring config space at offset 0x2 (was 0xffffffff, writing 0x50000a2)
[1077897.162387] pci 0000:00:00.1: restoring config space at offset 0x1 (was 0xffffffff, writing 0x200100)
[1077897.162391] pci 0000:00:00.1: restoring config space at offset 0x0 (was 0xffffffff, writing 0x2fa10de)
[1077897.162409] pci 0000:00:00.3: restoring config space at offset 0xf (was 0x0, writing 0xff)
[1077897.162422] pci 0000:00:00.4: restoring config space at offset 0xf (was 0x0, writing 0xff)
[1077897.162436] pci 0000:00:00.5: restoring config space at offset 0xf (was 0x0, writing 0xff)
[1077897.162453] pci 0000:00:00.6: restoring config space at offset 0x1 (was 0x200100, writing 0x200102)
[1077897.162477] pcieport-driver 0000:00:03.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
[1077897.162491] pcieport-driver 0000:00:03.0: setting latency timer to 64
[1077897.162506] pcieport-driver 0000:00:04.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
[1077897.162519] pcieport-driver 0000:00:04.0: setting latency timer to 64
[1077897.284417] pci 0000:00:09.0: restoring config space at offset 0xf (was 0x0, writing 0xff)
[1077897.284525] ohci_hcd 0000:00:0b.0: wake-up capability disabled by ACPI
[1077897.284529] ohci_hcd 0000:00:0b.0: PME# disabled
[1077897.284531] ohci_hcd 0000:00:0b.0: wake-up capability disabled by ACPI
[1077897.284534] ohci_hcd 0000:00:0b.0: PME# disabled
[1077897.301027] ohci_hcd 0000:00:0b.0: PCI INT A -> Link[APCF] -> GSI 21 (level, low) -> IRQ 21
[1077897.301031] ohci_hcd 0000:00:0b.0: setting latency timer to 64
[1077897.340025] ehci_hcd 0000:00:0b.1: PCI INT B -> Link[APCL] -> GSI 22 (level, low) -> IRQ 22
[1077897.340028] ehci_hcd 0000:00:0b.1: setting latency timer to 64
[1077897.356043] pata_amd 0000:00:0d.0: setting latency timer to 64
[1077897.372038] sata_nv 0000:00:0e.0: restoring config space at offset 0x1 (was 0xb00000, writing 0xb00007)
[1077897.372051] sata_nv 0000:00:0e.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
[1077897.372054] sata_nv 0000:00:0e.0: setting latency timer to 64
[1077897.372079] pci 0000:00:10.0: restoring config space at offset 0x7 (was 0x280a0a0, writing 0x8280a0a0)
[1077897.372141] pci 0000:00:10.0: setting latency timer to 64
[1077897.372268] Intel ICH 0000:00:10.2: PCI INT C -> Link[APCJ] -> GSI 23 (level, low) -> IRQ 23
[1077897.372272] Intel ICH 0000:00:10.2: setting latency timer to 64
[1077897.396040] forcedeth 0000:00:14.0: wake-up capability disabled by ACPI
[1077897.396043] forcedeth 0000:00:14.0: PME# disabled
[1077897.460897] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[fe9ff000-fe9ff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[1077897.460950] ath5k_pci 0000:03:07.0: restoring config space at offset 0x3 (was 0x2008, writing 0xa808)
[1077897.472028] ath5k_pci 0000:03:07.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
[1077897.473124] parport_pc 00:07: activated
[1077897.473204] sd 2:0:0:0: [sda] Starting disk
[1077898.110481] ata1: SATA link down (SStatus 0 SControl 300)
[1077898.120969] ata2: SATA link down (SStatus 0 SControl 300)
[1077899.428313] ata3.00: ACPI cmd ef/03:45:00:00:00:a0 filtered out
[1077899.428315] ata3.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
[1077899.472177] ata3: nv_mode_filter: 0x3f01f&0x3f01f->0x3f01f, BIOS=0x3f000 (0xc60000c0) ACPI=0x3f01f (20:600:0x13)
[1077899.538667] ata3.00: configured for UDMA/100
[1077899.586500] sd 2:0:0:0: [sda] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[1077899.586518] sd 2:0:0:0: [sda] Write Protect is off
[1077899.586520] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[1077899.586542] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[1077899.928227] PM: resume devices took 2.768 seconds
[1077899.928257] PM: Finishing wakeup.
[1077899.928258] Restarting tasks ... done.
[1077902.761395] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[1077913.424031] eth0: no IPv6 routers present
[1081792.612943] npviewer.bin[31738]: segfault at dff7aa20 ip 00000000f6aa5ec0 sp 00000000ed9a9280 error 4 in libflashplayer.so[f67b4000+96d000]
[1081945.347874] npviewer.bin[7117]: segfault at ff9bea2c ip 00000000ff9bea2c sp 00000000ffcb65ec error 14
[1118404.848523] possible SYN flooding on port 7059. Sending cookies.
[1144754.965964] possible SYN flooding on port 7059. Sending cookies.
[1144815.215009] possible SYN flooding on port 7059. Sending cookies.
[1144875.231606] possible SYN flooding on port 7059. Sending cookies.
[1158685.882077] possible SYN flooding on port 7059. Sending cookies.
[1164499.306112] possible SYN flooding on port 7059. Sending cookies.
[1175571.068385] possible SYN flooding on port 7059. Sending cookies.
[1179787.848104] possible SYN flooding on port 7059. Sending cookies.
[1180292.600253] possible SYN flooding on port 7059. Sending cookies.
[1190500.796370] possible SYN flooding on port 7059. Sending cookies.
[1193734.481238] possible SYN flooding on port 7059. Sending cookies.
[1193794.593410] possible SYN flooding on port 7059. Sending cookies.
[1193854.632608] possible SYN flooding on port 7059. Sending cookies.
[1193915.090953] possible SYN flooding on port 7059. Sending cookies.
[1193975.132081] possible SYN flooding on port 7059. Sending cookies.
[1194035.781228] possible SYN flooding on port 7059. Sending cookies.
[1194096.103505] possible SYN flooding on port 7059. Sending cookies.
[1194156.158725] possible SYN flooding on port 7059. Sending cookies.
[1194216.175781] possible SYN flooding on port 7059. Sending cookies.
[1194276.366394] possible SYN flooding on port 7059. Sending cookies.
[1194336.970886] possible SYN flooding on port 7059. Sending cookies.
[1194397.691239] possible SYN flooding on port 7059. Sending cookies.
[1194458.220793] possible SYN flooding on port 7059. Sending cookies.
[1194518.416271] possible SYN flooding on port 7059. Sending cookies.
[1194578.488048] possible SYN flooding on port 7059. Sending cookies.
[1194639.254936] possible SYN flooding on port 7059. Sending cookies.
[1194699.387588] possible SYN flooding on port 7059. Sending cookies.
[1194760.770252] possible SYN flooding on port 7059. Sending cookies.
[1194820.820160] possible SYN flooding on port 7059. Sending cookies.
[1194880.999762] possible SYN flooding on port 7059. Sending cookies.
[1194941.464705] possible SYN flooding on port 7059. Sending cookies.
[1195004.059964] possible SYN flooding on port 7059. Sending cookies.
[1195064.256940] possible SYN flooding on port 7059. Sending cookies.
[1195125.624622] possible SYN flooding on port 7059. Sending cookies.
[1195185.838046] possible SYN flooding on port 7059. Sending cookies.
[1195246.136843] possible SYN flooding on port 7059. Sending cookies.
[1195306.149450] possible SYN flooding on port 7059. Sending cookies.
[1195366.536717] possible SYN flooding on port 7059. Sending cookies.
[1195426.554435] possible SYN flooding on port 7059. Sending cookies.
[1195487.170699] possible SYN flooding on port 7059. Sending cookies.
[1200458.076686] pidgin[15159]: segfault at 2a3bdd ip 00007f41b71a1225 sp 00007fffc28cc700 error 4 in libc-2.9.so[7f41b7127000+168000]
[1202137.008249] possible SYN flooding on port 7059. Sending cookies.
[1207065.429948] possible SYN flooding on port 7059. Sending cookies.
[1207327.568967] possible SYN flooding on port 7059. Sending cookies.
[1208242.849053] possible SYN flooding on port 7059. Sending cookies.
[1214216.831972] possible SYN flooding on port 7059. Sending cookies.
[1218437.282663] NVRM: Xid (0000:05): 13, 0000 e0016100 0000008a 00000104 000091d6 00000002
[1218437.285061] NVRM: Xid (0000:05): 9, Channel 00000020 Instance 00000000 Intr 00100000
[1221660.701915] possible SYN flooding on port 7059. Sending cookies.
[1223339.527351] possible SYN flooding on port 7059. Sending cookies.
[1225225.968286] possible SYN flooding on port 7059. Sending cookies.
[1231904.749026] TCP: Treason uncloaked! Peer 90.59.18.150:16642/50443 shrinks window 3241942010:3241946258. Repaired.
[1231905.877042] TCP: Treason uncloaked! Peer 90.59.18.150:16642/50443 shrinks window 3241942010:3241946258. Repaired.
[1231908.133028] TCP: Treason uncloaked! Peer 90.59.18.150:16642/50443 shrinks window 3241942010:3241946258. Repaired.
[1231912.645027] TCP: Treason uncloaked! Peer 90.59.18.150:16642/50443 shrinks window 3241942010:3241946258. Repaired.
[1233145.579790] npviewer.bin[17767]: segfault at ff9bea2c ip 00000000ff9bea2c sp 00000000fff0064c error 14
[1234316.496663] possible SYN flooding on port 7059. Sending cookies.
[1236435.375070] possible SYN flooding on port 7059. Sending cookies.
[1238761.322121] possible SYN flooding on port 7059. Sending cookies.
[1240433.315193] possible SYN flooding on port 7059. Sending cookies.
[1240807.661000] possible SYN flooding on port 7059. Sending cookies.
[1251085.663634] possible SYN flooding on port 7059. Sending cookies.
[1251145.727574] possible SYN flooding on port 7059. Sending cookies.
[1262923.672269] possible SYN flooding on port 7059. Sending cookies.
[1283705.063459] possible SYN flooding on port 7059. Sending cookies.
[1295829.100586] npviewer.bin[9120]: segfault at 2c ip 00000000f687faf5 sp 00000000ffa8f990 error 4 in libflashplayer.so[f6839000+96d000]
[1301319.447313] possible SYN flooding on port 7059. Sending cookies.
[1302874.863139] possible SYN flooding on port 7059. Sending cookies.
[1302935.778121] possible SYN flooding on port 7059. Sending cookies.
[1302996.473200] possible SYN flooding on port 7059. Sending cookies.
[1308124.826184] npviewer.bin[17271]: segfault at ff9bea2c ip 00000000ff9bea2c sp 00000000fff8533c error 14
[1314712.342372] possible SYN flooding on port 7059. Sending cookies.
[1337261.653604] npviewer.bin[18495]: segfault at ff9bea2c ip 00000000ff9bea2c sp 00000000ffb8ef3c error 14
[1344394.246593] npviewer.bin[27000]: segfault at f54ffd6c ip 00000000f6c333c3 sp 00000000ec9a4310 error 4<6>npviewer.bin[27624]: segfault at eb272b94 ip 00000000f78479e0 sp 00000000eaffef74 error 4 in libflashplayer.so[f67bc000+96d000] in libpthread-2.9.so[f7840000+15000]
[1344394.246637] 
[1344796.886980] possible SYN flooding on port 7059. Sending cookies.
[1344857.913169] possible SYN flooding on port 7059. Sending cookies.
[1344918.688701] possible SYN flooding on port 7059. Sending cookies.
[1344979.695022] possible SYN flooding on port 7059. Sending cookies.
[1345040.497002] possible SYN flooding on port 7059. Sending cookies.
[1345100.713833] possible SYN flooding on port 7059. Sending cookies.
[1345167.236737] possible SYN flooding on port 7059. Sending cookies.
[1345232.511795] possible SYN flooding on port 7059. Sending cookies.
[1345292.998404] possible SYN flooding on port 7059. Sending cookies.
[1345353.382873] possible SYN flooding on port 7059. Sending cookies.
[1345415.822526] possible SYN flooding on port 7059. Sending cookies.
[1345478.495507] possible SYN flooding on port 7059. Sending cookies.
[1345542.644221] possible SYN flooding on port 7059. Sending cookies.
[1345604.164261] possible SYN flooding on port 7059. Sending cookies.
[1345683.501217] possible SYN flooding on port 7059. Sending cookies.
[1345793.572193] possible SYN flooding on port 7059. Sending cookies.
[1345853.746387] possible SYN flooding on port 7059. Sending cookies.
[1345914.340186] possible SYN flooding on port 7059. Sending cookies.
[1345974.879323] possible SYN flooding on port 7059. Sending cookies.
[1346045.583431] possible SYN flooding on port 7059. Sending cookies.
[1346106.308746] possible SYN flooding on port 7059. Sending cookies.
[1346183.453994] possible SYN flooding on port 7059. Sending cookies.
[1346244.651191] possible SYN flooding on port 7059. Sending cookies.
[1346323.997434] possible SYN flooding on port 7059. Sending cookies.
[1346385.540794] possible SYN flooding on port 7059. Sending cookies.
[1346471.926368] possible SYN flooding on port 7059. Sending cookies.
[1346555.025065] possible SYN flooding on port 7059. Sending cookies.
[1351932.351569] possible SYN flooding on port 7059. Sending cookies.
[1352056.298845] possible SYN flooding on port 7059. Sending cookies.
[1352870.196881] possible SYN flooding on port 7059. Sending cookies.
[1352930.644126] possible SYN flooding on port 7059. Sending cookies.
[1352990.965722] possible SYN flooding on port 7059. Sending cookies.
[1353051.318271] possible SYN flooding on port 7059. Sending cookies.
[1353111.473932] possible SYN flooding on port 7059. Sending cookies.
[1353171.704827] possible SYN flooding on port 7059. Sending cookies.
[1353231.977452] possible SYN flooding on port 7059. Sending cookies.
[1353292.839534] possible SYN flooding on port 7059. Sending cookies.
[1353353.818000] possible SYN flooding on port 7059. Sending cookies.
[1353413.838604] possible SYN flooding on port 7059. Sending cookies.
[1353474.028256] possible SYN flooding on port 7059. Sending cookies.
[1353534.063447] possible SYN flooding on port 7059. Sending cookies.
[1353594.582568] possible SYN flooding on port 7059. Sending cookies.
[1353655.090738] possible SYN flooding on port 7059. Sending cookies.
[1353715.894295] possible SYN flooding on port 7059. Sending cookies.
[1353776.073891] possible SYN flooding on port 7059. Sending cookies.
[1353836.246098] possible SYN flooding on port 7059. Sending cookies.
[1353896.535788] possible SYN flooding on port 7059. Sending cookies.
[1353956.703592] possible SYN flooding on port 7059. Sending cookies.
[1354017.605133] possible SYN flooding on port 7059. Sending cookies.
[1354078.235541] possible SYN flooding on port 7059. Sending cookies.
[1354138.309047] possible SYN flooding on port 7059. Sending cookies.
[1354198.872324] possible SYN flooding on port 7059. Sending cookies.
[1354259.147529] possible SYN flooding on port 7059. Sending cookies.
[1354319.425560] possible SYN flooding on port 7059. Sending cookies.
[1354379.720752] possible SYN flooding on port 7059. Sending cookies.
[1354440.891046] possible SYN flooding on port 7059. Sending cookies.
[1354501.159578] possible SYN flooding on port 7059. Sending cookies.
[1354563.455242] possible SYN flooding on port 7059. Sending cookies.
[1354623.540126] possible SYN flooding on port 7059. Sending cookies.
[1367901.561975] possible SYN flooding on port 7059. Sending cookies.
[1381612.935654] possible SYN flooding on port 7059. Sending cookies.
[1381673.035353] possible SYN flooding on port 7059. Sending cookies.
[1381733.293085] possible SYN flooding on port 7059. Sending cookies.
[1381793.318427] possible SYN flooding on port 7059. Sending cookies.
[1381853.796854] possible SYN flooding on port 7059. Sending cookies.
[1381913.923258] possible SYN flooding on port 7059. Sending cookies.
[1381974.450318] possible SYN flooding on port 7059. Sending cookies.
[1382035.292977] possible SYN flooding on port 7059. Sending cookies.
[1382095.843499] possible SYN flooding on port 7059. Sending cookies.
[1382155.987279] possible SYN flooding on port 7059. Sending cookies.
[1384673.614541] pidgin[9908]: segfault at 7f1ed0000000 ip 00007f1ed5592243 sp 00007fffe0cbe300 error 4 in libc-2.9.so[7f1ed5518000+168000]
[1384902.231602] possible SYN flooding on port 7059. Sending cookies.
[1387694.611243] possible SYN flooding on port 7059. Sending cookies.
[1387847.092408] possible SYN flooding on port 7059. Sending cookies.
[1395125.353027] TCP: Treason uncloaked! Peer 85.241.117.254:58745/7059 shrinks window 316829438:316830028. Repaired.
[1395476.200033] TCP: Treason uncloaked! Peer 85.241.117.254:58745/7059 shrinks window 317727454:317728283. Repaired.
[1395494.553036] TCP: Treason uncloaked! Peer 85.241.117.254:58745/7059 shrinks window 317782750:317783697. Repaired.
[1395551.969039] TCP: Treason uncloaked! Peer 85.241.117.254:58745/7059 shrinks window 317955806:317959327. Repaired.
[1396578.145677] possible SYN flooding on port 7059. Sending cookies.
[1396638.803187] possible SYN flooding on port 7059. Sending cookies.
[1396699.200553] possible SYN flooding on port 7059. Sending cookies.
[1396759.503431] possible SYN flooding on port 7059. Sending cookies.
[1396819.590206] possible SYN flooding on port 7059. Sending cookies.
[1396880.612018] possible SYN flooding on port 7059. Sending cookies.
[1396940.855924] possible SYN flooding on port 7059. Sending cookies.
[1397001.563475] possible SYN flooding on port 7059. Sending cookies.
[1397061.598937] possible SYN flooding on port 7059. Sending cookies.
[1397122.415360] possible SYN flooding on port 7059. Sending cookies.
[1397182.521318] possible SYN flooding on port 7059. Sending cookies.
[1400712.178450] possible SYN flooding on port 7059. Sending cookies.
[1409738.570526] possible SYN flooding on port 7059. Sending cookies.
[1409799.129437] possible SYN flooding on port 7059. Sending cookies.
[1427764.782521] npviewer.bin[16139]: segfault at ff9bea2c ip 00000000ff9bea2c sp 00000000ffadee8c error 14
[1440725.578028] possible SYN flooding on port 7059. Sending cookies.
[1444066.598669] possible SYN flooding on port 7059. Sending cookies.
[1444126.725558] possible SYN flooding on port 7059. Sending cookies.
[1444189.393794] possible SYN flooding on port 7059. Sending cookies.
[1444249.794969] possible SYN flooding on port 7059. Sending cookies.
[1444312.738832] possible SYN flooding on port 7059. Sending cookies.
[1444382.341784] possible SYN flooding on port 7059. Sending cookies.
[1444443.108126] possible SYN flooding on port 7059. Sending cookies.
[1444510.413626] possible SYN flooding on port 7059. Sending cookies.
[1444575.355449] possible SYN flooding on port 7059. Sending cookies.
[1444641.699030] possible SYN flooding on port 7059. Sending cookies.
[1444720.064199] possible SYN flooding on port 7059. Sending cookies.
[1444797.399300] possible SYN flooding on port 7059. Sending cookies.
[1444888.776188] possible SYN flooding on port 7059. Sending cookies.
[1444967.537091] possible SYN flooding on port 7059. Sending cookies.
[1445050.130322] possible SYN flooding on port 7059. Sending cookies.
[1445119.704346] possible SYN flooding on port 7059. Sending cookies.
[1445195.283397] possible SYN flooding on port 7059. Sending cookies.
[1445255.468156] possible SYN flooding on port 7059. Sending cookies.
[1445315.851296] possible SYN flooding on port 7059. Sending cookies.
[1445390.599837] possible SYN flooding on port 7059. Sending cookies.
[1445465.965396] possible SYN flooding on port 7059. Sending cookies.
[1445526.654855] possible SYN flooding on port 7059. Sending cookies.
[1445587.593378] possible SYN flooding on port 7059. Sending cookies.
[1445666.128967] possible SYN flooding on port 7059. Sending cookies.
[1445769.545804] possible SYN flooding on port 7059. Sending cookies.
[1445837.170122] possible SYN flooding on port 7059. Sending cookies.
[1472174.834551] pidgin[16085]: segfault at 7fb6fffffffa ip 00007fb7770ff225 sp 00007fff8282aa70 error 4 in libc-2.9.so[7fb777085000+168000]
[1474544.573386] npviewer.bin[22234]: segfault at 2c ip 00000000f6852af5 sp 00000000ff863770 error 4 in libflashplayer.so[f680c000+96d000]
[1477627.367443] possible SYN flooding on port 7059. Sending cookies.
[1516438.131707] possible SYN flooding on port 7059. Sending cookies.
[1520314.345213] possible SYN flooding on port 7059. Sending cookies.
[1523538.640073] possible SYN flooding on port 7059. Sending cookies.
[1560890.973278] npviewer.bin[13177]: segfault at ff9bea2c ip 00000000ff9bea2c sp 00000000ffb9c12c error 14
[1588391.504620] possible SYN flooding on port 7059. Sending cookies.
[1588754.473796] Intel ICH 0000:00:10.2: PCI INT C disabled
[1588755.999796] Intel ICH 0000:00:10.2: PCI INT C -> Link[APCJ] -> GSI 23 (level, low) -> IRQ 23
[1588755.999881] Intel ICH 0000:00:10.2: setting latency timer to 64
[1588756.322752] intel8x0_measure_ac97_clock: measured 57329 usecs
[1588756.322758] intel8x0: clocking to 46906
[1591818.801002] npviewer.bin[24557]: segfault at ff9bea2c ip 00000000ff9bea2c sp 00000000ffbcef7c error 14
[1606887.342366] npviewer.bin[11461]: segfault at ff9bea2c ip 00000000ff9bea2c sp 00000000ffc5900c error 14
[1606904.384765] npviewer.bin[30793]: segfault at ff9bea2c ip 00000000ff9bea2c sp 00000000ff93433c error 14
[1618563.971436] UDP: short packet: From 65.91.48.74:34611 25649/109 to 192.168.1.201:7059
[1627930.118471] possible SYN flooding on port 7059. Sending cookies.
[1685856.628191] npviewer.bin[12840]: segfault at ef3bcf84 ip 00000000f78cc9e0 sp 00000000eb13bf74 error 4 in libpthread-2.9.so[f78c5000+15000]
[1691872.924485] npviewer.bin[14758]: segfault at 13 ip 00000000f6ebb1b7 sp 00000000ffc5c9a4 error 4 in libflashplayer.so[f6803000+96d000]
[1699689.662231] possible SYN flooding on port 7059. Sending cookies.
[1699750.050435] possible SYN flooding on port 7059. Sending cookies.
[1699810.151059] possible SYN flooding on port 7059. Sending cookies.
[1699870.474525] possible SYN flooding on port 7059. Sending cookies.
[1699930.857220] possible SYN flooding on port 7059. Sending cookies.
[1699991.213298] possible SYN flooding on port 7059. Sending cookies.
[1700051.467999] possible SYN flooding on port 7059. Sending cookies.
[1700111.719118] possible SYN flooding on port 7059. Sending cookies.
[1700172.140820] possible SYN flooding on port 7059. Sending cookies.
[1700232.229567] possible SYN flooding on port 7059. Sending cookies.
[1700292.553356] possible SYN flooding on port 7059. Sending cookies.
[1700352.672221] possible SYN flooding on port 7059. Sending cookies.
[1700413.597715] possible SYN flooding on port 7059. Sending cookies.
[1700473.645467] possible SYN flooding on port 7059. Sending cookies.
[1700534.582065] possible SYN flooding on port 7059. Sending cookies.
[1700594.738000] possible SYN flooding on port 7059. Sending cookies.
[1700654.835854] possible SYN flooding on port 7059. Sending cookies.
[1700715.013720] possible SYN flooding on port 7059. Sending cookies.
[1700775.782987] possible SYN flooding on port 7059. Sending cookies.
[1700836.113204] possible SYN flooding on port 7059. Sending cookies.
[1700896.290261] possible SYN flooding on port 7059. Sending cookies.
[1700956.715853] possible SYN flooding on port 7059. Sending cookies.
[1701016.735848] possible SYN flooding on port 7059. Sending cookies.
[1701077.422753] possible SYN flooding on port 7059. Sending cookies.
[1701137.452227] possible SYN flooding on port 7059. Sending cookies.
[1701199.265448] possible SYN flooding on port 7059. Sending cookies.
[1701259.302628] possible SYN flooding on port 7059. Sending cookies.
[1701319.438570] possible SYN flooding on port 7059. Sending cookies.
[1701379.578312] possible SYN flooding on port 7059. Sending cookies.
[1701439.994042] possible SYN flooding on port 7059. Sending cookies.
[1715389.279993] eth0: link down.
[1715391.221425] eth0: link up.
[1728495.600562] possible SYN flooding on port 7059. Sending cookies.
[1729853.195731] possible SYN flooding on port 7059. Sending cookies.
[1750677.235765] possible SYN flooding on port 7059. Sending cookies.
[1752930.470865] possible SYN flooding on port 7059. Sending cookies.
[1752990.663022] possible SYN flooding on port 7059. Sending cookies.
[1753050.668922] possible SYN flooding on port 7059. Sending cookies.
[1753110.928266] possible SYN flooding on port 7059. Sending cookies.
[1753171.100913] possible SYN flooding on port 7059. Sending cookies.
[1753231.374634] possible SYN flooding on port 7059. Sending cookies.
[1753291.611750] possible SYN flooding on port 7059. Sending cookies.
[1753352.024133] possible SYN flooding on port 7059. Sending cookies.
[1753412.159101] possible SYN flooding on port 7059. Sending cookies.
[1756677.055607] npviewer.bin[21668]: segfault at f1af2b94 ip 00000000f78739e0 sp 00000000ef63ff74 error 4 in libpthread-2.9.so[f786c000+15000]
[1759110.928866] possible SYN flooding on port 7059. Sending cookies.
[1760952.682895] npviewer.bin[4997]: segfault at ff9bea2c ip 00000000ff9bea2c sp 00000000ffcb470c error 14
[1774155.841024] npviewer.bin[5711]: segfault at ff9bea2c ip 00000000ff9bea2c sp 00000000ffe9023c error 14
[1774376.893045] TCP: Treason uncloaked! Peer 208.180.52.193:36625/56561 shrinks window 907019804:907019872. Repaired.
[1774382.893032] TCP: Treason uncloaked! Peer 208.180.52.193:36625/56561 shrinks window 907019804:907019872. Repaired.
[1774389.820622] npviewer.bin[9106]: segfault at ff9bea2c ip 00000000ff9bea2c sp 00000000ff9e4c6c error 14
[1774587.633025] TCP: Treason uncloaked! Peer 208.180.52.193:36625/59823 shrinks window 4226091915:4226091983. Repaired.
[1774593.633024] TCP: Treason uncloaked! Peer 208.180.52.193:36625/59823 shrinks window 4226091915:4226091983. Repaired.
[1774673.005028] possible SYN flooding on port 7059. Sending cookies.
[1774780.205021] TCP: Treason uncloaked! Peer 208.180.52.193:36625/47813 shrinks window 2943529789:2943529857. Repaired.
[1774786.205029] TCP: Treason uncloaked! Peer 208.180.52.193:36625/47813 shrinks window 2943529789:2943529857. Repaired.
[1775064.157033] TCP: Treason uncloaked! Peer 208.180.52.193:36625/55703 shrinks window 3102274262:3102274330. Repaired.
[1775070.157038] TCP: Treason uncloaked! Peer 208.180.52.193:36625/55703 shrinks window 3102274262:3102274330. Repaired.
[1775462.405032] TCP: Treason uncloaked! Peer 208.180.52.193:36625/41710 shrinks window 763519734:763519802. Repaired.
[1775468.405043] TCP: Treason uncloaked! Peer 208.180.52.193:36625/41710 shrinks window 763519734:763519802. Repaired.
[1775804.421033] TCP: Treason uncloaked! Peer 208.180.52.193:36625/37909 shrinks window 1822660873:1822660941. Repaired.
[1775810.421029] TCP: Treason uncloaked! Peer 208.180.52.193:36625/37909 shrinks window 1822660873:1822660941. Repaired.
[1776208.765032] TCP: Treason uncloaked! Peer 208.180.52.193:36625/45779 shrinks window 3861649346:3861649414. Repaired.
[1776214.765028] TCP: Treason uncloaked! Peer 208.180.52.193:36625/45779 shrinks window 3861649346:3861649414. Repaired.
[1781935.763749] possible SYN flooding on port 7059. Sending cookies.
[1781996.064756] possible SYN flooding on port 7059. Sending cookies.
[1784185.706780] UDP: short packet: From 84.101.70.46:34873 25649/109 to 192.168.1.201:7059

```

---

