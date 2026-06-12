---
title: "Installing USB Webcam"
date: 2009-09-15
forum: Multimedia Software
---

### Post by Mistersl on 2009-09-15
I have Ubuntu 9.04 and trouble installing Genius VideoCAM Slim USB 2.
Cam is not working with Cheese, gsteamer-properties return nothing,...

Has anybody been successfull with this camera?

Best regards,
Joze

lsusb comand returns:
Bus 001 Device 004: ID 0458:7012 KYE Systems Corp. (Mouse Systems) WebCAM USB2.0
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root 

dmesg returns:
[    0.851471] bus: 1e index 1 mmio: [0xda300000-0xda3fffff]
[    0.851474] bus: 1e index 2 mmio: [0xdca00000-0xdcafffff]
[    0.851476] bus: 1e index 3 mmio: [0x0-0x0]
[    0.851478] bus: 1f index 0 mmio: [0x0-0x0]
[    0.851480] bus: 1f index 1 mmio: [0xda700000-0xda7fffff]
[    0.851482] bus: 1f index 2 mmio: [0xdce00000-0xdcefffff]
[    0.851484] bus: 1f index 3 mmio: [0x0-0x0]
[    0.851486] bus: 20 index 0 mmio: [0x0-0x0]
[    0.851488] bus: 20 index 1 mmio: [0xdab00000-0xdabfffff]
[    0.851490] bus: 20 index 2 mmio: [0xdd200000-0xdd2fffff]
[    0.851492] bus: 20 index 3 mmio: [0x0-0x0]
[    0.851494] bus: 21 index 0 mmio: [0x0-0x0]
[    0.851497] bus: 21 index 1 mmio: [0xdaf00000-0xdaffffff]
[    0.851499] bus: 21 index 2 mmio: [0xdd600000-0xdd6fffff]
[    0.851502] bus: 21 index 3 mmio: [0x0-0x0]
[    0.851504] bus: 22 index 0 mmio: [0x0-0x0]
[    0.851507] bus: 22 index 1 mmio: [0xdb300000-0xdb3fffff]
[    0.851509] bus: 22 index 2 mmio: [0xdda00000-0xddafffff]
[    0.851511] bus: 22 index 3 mmio: [0x0-0x0]
[    0.851519] NET: Registered protocol family 2
[    0.851685] IP route cache hash table entries: 16384 (order: 4, 65536 bytes)
[    0.851734] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
[    0.854248] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.856588] TCP: Hash tables configured (established 65536 bind 65536)
[    0.856591] TCP reno registered
[    0.856663] NET: Registered protocol family 1
[    0.856712] checking if image is initramfs... it is
[    1.084161] Freeing initrd memory: 7372k freed
[    1.084203] Simple Boot Flag at 0x36 set to 0x1
[    1.084252] cpufreq: No nForce2 chipset.
[    1.084301] audit: initializing netlink socket (disabled)
[    1.084345] type=2000 audit(1253045780.084:1): initialized
[    1.088238] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.088319] VFS: Disk quotas dquot_6.5.1
[    1.088356] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.088452] fuse init (API version 7.10)
[    1.088501] msgmni has been set to 994
[    1.088653] alg: No test for stdrng (krng)
[    1.088664] io scheduler noop registered
[    1.088666] io scheduler anticipatory registered
[    1.088668] io scheduler deadline registered
[    1.088678] io scheduler cfq registered (default)
[    1.088690] pci 0000:00:00.0: Limiting direct PCI/PCI transfers
[    1.088712] pci 0000:00:0f.0: Boot video device
[    1.109346] pcieport-driver 0000:00:15.0: setting latency timer to 64
[    1.109803] pcieport-driver 0000:00:15.0: found MSI capability
[    1.110145] pcieport-driver 0000:00:15.0: irq 2303 for MSI/MSI-X
[    1.110273] pci_express 0000:00:15.0:pcie00: allocate port service
[    1.110285] pci_express 0000:00:15.0:pcie02: allocate port service
[    1.110745] pcieport-driver 0000:00:15.1: setting latency timer to 64
[    1.111199] pcieport-driver 0000:00:15.1: found MSI capability
[    1.111537] pcieport-driver 0000:00:15.1: irq 2302 for MSI/MSI-X
[    1.111665] pci_express 0000:00:15.1:pcie00: allocate port service
[    1.111674] pci_express 0000:00:15.1:pcie02: allocate port service
[    1.112017] pcieport-driver 0000:00:15.2: setting latency timer to 64
[    1.112473] pcieport-driver 0000:00:15.2: found MSI capability
[    1.112814] pcieport-driver 0000:00:15.2: irq 2301 for MSI/MSI-X
[    1.112942] pci_express 0000:00:15.2:pcie00: allocate port service
[    1.112951] pci_express 0000:00:15.2:pcie02: allocate port service
[    1.113411] pcieport-driver 0000:00:15.3: setting latency timer to 64
[    1.113865] pcieport-driver 0000:00:15.3: found MSI capability
[    1.114206] pcieport-driver 0000:00:15.3: irq 2300 for MSI/MSI-X
[    1.114333] pci_express 0000:00:15.3:pcie00: allocate port service
[    1.114347] pci_express 0000:00:15.3:pcie02: allocate port service
[    1.114809] pcieport-driver 0000:00:15.4: setting latency timer to 64
[    1.115263] pcieport-driver 0000:00:15.4: found MSI capability
[    1.115602] pcieport-driver 0000:00:15.4: irq 2299 for MSI/MSI-X
[    1.115730] pci_express 0000:00:15.4:pcie00: allocate port service
[    1.115739] pci_express 0000:00:15.4:pcie02: allocate port service
[    1.116085] pcieport-driver 0000:00:15.5: setting latency timer to 64
[    1.116541] pcieport-driver 0000:00:15.5: found MSI capability
[    1.116879] pcieport-driver 0000:00:15.5: irq 2298 for MSI/MSI-X
[    1.117007] pci_express 0000:00:15.5:pcie00: allocate port service
[    1.117016] pci_express 0000:00:15.5:pcie02: allocate port service
[    1.117476] pcieport-driver 0000:00:15.6: setting latency timer to 64
[    1.117930] pcieport-driver 0000:00:15.6: found MSI capability
[    1.118272] pcieport-driver 0000:00:15.6: irq 2297 for MSI/MSI-X
[    1.118399] pci_express 0000:00:15.6:pcie00: allocate port service
[    1.118414] pci_express 0000:00:15.6:pcie02: allocate port service
[    1.118876] pcieport-driver 0000:00:15.7: setting latency timer to 64
[    1.119332] pcieport-driver 0000:00:15.7: found MSI capability
[    1.119670] pcieport-driver 0000:00:15.7: irq 2296 for MSI/MSI-X
[    1.119798] pci_express 0000:00:15.7:pcie00: allocate port service
[    1.119811] pci_express 0000:00:15.7:pcie02: allocate port service
[    1.120155] pcieport-driver 0000:00:16.0: setting latency timer to 64
[    1.120609] pcieport-driver 0000:00:16.0: found MSI capability
[    1.120947] pcieport-driver 0000:00:16.0: irq 2295 for MSI/MSI-X
[    1.121075] pci_express 0000:00:16.0:pcie00: allocate port service
[    1.121084] pci_express 0000:00:16.0:pcie02: allocate port service
[    1.121546] pcieport-driver 0000:00:16.1: setting latency timer to 64
[    1.122000] pcieport-driver 0000:00:16.1: found MSI capability
[    1.122339] pcieport-driver 0000:00:16.1: irq 2294 for MSI/MSI-X
[    1.122467] pci_express 0000:00:16.1:pcie00: allocate port service
[    1.122476] pci_express 0000:00:16.1:pcie02: allocate port service
[    1.122936] pcieport-driver 0000:00:16.2: setting latency timer to 64
[    1.123390] pcieport-driver 0000:00:16.2: found MSI capability
[    1.123729] pcieport-driver 0000:00:16.2: irq 2293 for MSI/MSI-X
[    1.123857] pci_express 0000:00:16.2:pcie00: allocate port service
[    1.123866] pci_express 0000:00:16.2:pcie02: allocate port service
[    1.124212] pcieport-driver 0000:00:16.3: setting latency timer to 64
[    1.124667] pcieport-driver 0000:00:16.3: found MSI capability
[    1.125006] pcieport-driver 0000:00:16.3: irq 2292 for MSI/MSI-X
[    1.125133] pci_express 0000:00:16.3:pcie00: allocate port service
[    1.125147] pci_express 0000:00:16.3:pcie02: allocate port service
[    1.125609] pcieport-driver 0000:00:16.4: setting latency timer to 64
[    1.126064] pcieport-driver 0000:00:16.4: found MSI capability
[    1.126405] pcieport-driver 0000:00:16.4: irq 2291 for MSI/MSI-X
[    1.126533] pci_express 0000:00:16.4:pcie00: allocate port service
[    1.126549] pci_express 0000:00:16.4:pcie02: allocate port service
[    1.127010] pcieport-driver 0000:00:16.5: setting latency timer to 64
[    1.127464] pcieport-driver 0000:00:16.5: found MSI capability
[    1.127803] pcieport-driver 0000:00:16.5: irq 2290 for MSI/MSI-X
[    1.127930] pci_express 0000:00:16.5:pcie00: allocate port service
[    1.127940] pci_express 0000:00:16.5:pcie02: allocate port service
[    1.128279] pcieport-driver 0000:00:16.6: setting latency timer to 64
[    1.128734] pcieport-driver 0000:00:16.6: found MSI capability
[    1.129071] pcieport-driver 0000:00:16.6: irq 2289 for MSI/MSI-X
[    1.129199] pci_express 0000:00:16.6:pcie00: allocate port service
[    1.129209] pci_express 0000:00:16.6:pcie02: allocate port service
[    1.129670] pcieport-driver 0000:00:16.7: setting latency timer to 64
[    1.130125] pcieport-driver 0000:00:16.7: found MSI capability
[    1.130464] pcieport-driver 0000:00:16.7: irq 2288 for MSI/MSI-X
[    1.130592] pci_express 0000:00:16.7:pcie00: allocate port service
[    1.130606] pci_express 0000:00:16.7:pcie02: allocate port service
[    1.131068] pcieport-driver 0000:00:17.0: setting latency timer to 64
[    1.131524] pcieport-driver 0000:00:17.0: found MSI capability
[    1.131863] pcieport-driver 0000:00:17.0: irq 2287 for MSI/MSI-X
[    1.131990] pci_express 0000:00:17.0:pcie00: allocate port service
[    1.131996] pci_express 0000:00:17.0:pcie02: allocate port service
[    1.132385] pcieport-driver 0000:00:17.1: setting latency timer to 64
[    1.132840] pcieport-driver 0000:00:17.1: found MSI capability
[    1.133179] pcieport-driver 0000:00:17.1: irq 2286 for MSI/MSI-X
[    1.133306] pci_express 0000:00:17.1:pcie00: allocate port service
[    1.133319] pci_express 0000:00:17.1:pcie02: allocate port service
[    1.133783] pcieport-driver 0000:00:17.2: setting latency timer to 64
[    1.134237] pcieport-driver 0000:00:17.2: found MSI capability
[    1.134576] pcieport-driver 0000:00:17.2: irq 2285 for MSI/MSI-X
[    1.134703] pci_express 0000:00:17.2:pcie00: allocate port service
[    1.134719] pci_express 0000:00:17.2:pcie02: allocate port service
[    1.135182] pcieport-driver 0000:00:17.3: setting latency timer to 64
[    1.135637] pcieport-driver 0000:00:17.3: found MSI capability
[    1.135976] pcieport-driver 0000:00:17.3: irq 2284 for MSI/MSI-X
[    1.135996] pci_express 0000:00:17.3:pcie00: allocate port service
[    1.135996] pci_express 0000:00:17.3:pcie02: allocate port service
[    1.136463] pcieport-driver 0000:00:17.4: setting latency timer to 64
[    1.136917] pcieport-driver 0000:00:17.4: found MSI capability
[    1.137256] pcieport-driver 0000:00:17.4: irq 2283 for MSI/MSI-X
[    1.137383] pci_express 0000:00:17.4:pcie00: allocate port service
[    1.137394] pci_express 0000:00:17.4:pcie02: allocate port service
[    1.137855] pcieport-driver 0000:00:17.5: setting latency timer to 64
[    1.138309] pcieport-driver 0000:00:17.5: found MSI capability
[    1.138649] pcieport-driver 0000:00:17.5: irq 2282 for MSI/MSI-X
[    1.138777] pci_express 0000:00:17.5:pcie00: allocate port service
[    1.138787] pci_express 0000:00:17.5:pcie02: allocate port service
[    1.139249] pcieport-driver 0000:00:17.6: setting latency timer to 64
[    1.139702] pcieport-driver 0000:00:17.6: found MSI capability
[    1.139996] pcieport-driver 0000:00:17.6: irq 2281 for MSI/MSI-X
[    1.140066] pci_express 0000:00:17.6:pcie00: allocate port service
[    1.140077] pci_express 0000:00:17.6:pcie02: allocate port service
[    1.140539] pcieport-driver 0000:00:17.7: setting latency timer to 64
[    1.140996] pcieport-driver 0000:00:17.7: found MSI capability
[    1.141334] pcieport-driver 0000:00:17.7: irq 2280 for MSI/MSI-X
[    1.141462] pci_express 0000:00:17.7:pcie00: allocate port service
[    1.141477] pci_express 0000:00:17.7:pcie02: allocate port service
[    1.141941] pcieport-driver 0000:00:18.0: setting latency timer to 64
[    1.142396] pcieport-driver 0000:00:18.0: found MSI capability
[    1.142736] pcieport-driver 0000:00:18.0: irq 2279 for MSI/MSI-X
[    1.142864] pci_express 0000:00:18.0:pcie00: allocate port service
[    1.142880] pci_express 0000:00:18.0:pcie02: allocate port service
[    1.143343] pcieport-driver 0000:00:18.1: setting latency timer to 64
[    1.143800] pcieport-driver 0000:00:18.1: found MSI capability
[    1.144028] pcieport-driver 0000:00:18.1: irq 2278 for MSI/MSI-X
[    1.144156] pci_express 0000:00:18.1:pcie00: allocate port service
[    1.144166] pci_express 0000:00:18.1:pcie02: allocate port service
[    1.144630] pcieport-driver 0000:00:18.2: setting latency timer to 64
[    1.145086] pcieport-driver 0000:00:18.2: found MSI capability
[    1.145425] pcieport-driver 0000:00:18.2: irq 2277 for MSI/MSI-X
[    1.145553] pci_express 0000:00:18.2:pcie00: allocate port service
[    1.145563] pci_express 0000:00:18.2:pcie02: allocate port service
[    1.146028] pcieport-driver 0000:00:18.3: setting latency timer to 64
[    1.146483] pcieport-driver 0000:00:18.3: found MSI capability
[    1.146823] pcieport-driver 0000:00:18.3: irq 2276 for MSI/MSI-X
[    1.146951] pci_express 0000:00:18.3:pcie00: allocate port service
[    1.146966] pci_express 0000:00:18.3:pcie02: allocate port service
[    1.147431] pcieport-driver 0000:00:18.4: setting latency timer to 64
[    1.147887] pcieport-driver 0000:00:18.4: found MSI capability
[    1.148106] pcieport-driver 0000:00:18.4: irq 2275 for MSI/MSI-X
[    1.148234] pci_express 0000:00:18.4:pcie00: allocate port service
[    1.148245] pci_express 0000:00:18.4:pcie02: allocate port service
[    1.148712] pcieport-driver 0000:00:18.5: setting latency timer to 64
[    1.149169] pcieport-driver 0000:00:18.5: found MSI capability
[    1.149508] pcieport-driver 0000:00:18.5: irq 2274 for MSI/MSI-X
[    1.149635] pci_express 0000:00:18.5:pcie00: allocate port service
[    1.149652] pci_express 0000:00:18.5:pcie02: allocate port service
[    1.150116] pcieport-driver 0000:00:18.6: setting latency timer to 64
[    1.150571] pcieport-driver 0000:00:18.6: found MSI capability
[    1.150912] pcieport-driver 0000:00:18.6: irq 2273 for MSI/MSI-X
[    1.151040] pci_express 0000:00:18.6:pcie00: allocate port service
[    1.151051] pci_express 0000:00:18.6:pcie02: allocate port service
[    1.151521] pcieport-driver 0000:00:18.7: setting latency timer to 64
[    1.151976] pcieport-driver 0000:00:18.7: found MSI capability
[    1.152192] pcieport-driver 0000:00:18.7: irq 2272 for MSI/MSI-X
[    1.152320] pci_express 0000:00:18.7:pcie00: allocate port service
[    1.152335] pci_express 0000:00:18.7:pcie02: allocate port service
[    1.152715] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.153070] pciehp 0000:00:15.0:pcie02: HPC vendor_id 15ad device_id 7a0 ss_vid 0 ss_did 0
[    1.153295] pciehp 0000:00:15.0:pcie02: service driver pciehp loaded
[    1.153596] pciehp 0000:00:15.1:pcie02: HPC vendor_id 15ad device_id 7a0 ss_vid 0 ss_did 0
[    1.153810] pciehp 0000:00:15.1:pcie02: service driver pciehp loaded
[    1.154110] pciehp 0000:00:15.2:pcie02: HPC vendor_id 15ad device_id 7a0 ss_vid 0 ss_did 0
[    1.154322] pciehp 0000:00:15.2:pcie02: service driver pciehp loaded
[    1.154617] pciehp 0000:00:15.3:pcie02: HPC vendor_id 15ad device_id 7a0 ss_vid 0 ss_did 0
[    1.154842] pciehp 0000:00:15.3:pcie02: service driver pciehp loaded
[    1.155138] pciehp 0000:00:15.4:pcie02: HPC vendor_id 15ad device_id 7a0 ss_vid 0 ss_did 0
[    1.155350] pciehp 0000:00:15.4:pcie02: service driver pciehp loaded
[    1.155664] pciehp 0000:00:15.5:pcie02: HPC vendor_id 15ad device_id 7a0 ss_vid 0 ss_did 0
[    1.155876] pciehp 0000:00:15.5:pcie02: service driver pciehp loaded
[    1.156135] pciehp 0000:00:15.6:pcie02: HPC vendor_id 15ad device_id 7a0 ss_vid 0 ss_did 0
[    1.156375] pciehp 0000:00:15.6:pcie02: service driver pciehp loaded
[    1.156672] pciehp 0000:00:15.7:pcie02: HPC vendor_id 15ad device_id 7a0 ss_vid 0 ss_did 0
[    1.156884] pciehp 0000:00:15.7:pcie02: service driver pciehp loaded
[    1.157192] pciehp 0000:00:16.0:pcie02: HPC vendor_id 15ad device_id 7a0 ss_vid 0 ss_did 0
[    1.157406] pciehp 0000:00:16.0:pcie02: service driver pciehp loaded
[    1.157702] pciehp 0000:00:16.1:pcie02: HPC vendor_id 15ad device_id 7a0 ss_vid 0 ss_did 0
[    1.157914] pciehp 0000:00:16.1:pcie02: service driver pciehp loaded
[    1.158221] pciehp 0000:00:16.2:pcie02: HPC vendor_id 15ad device_id 7a0 ss_vid 0 ss_did 0
[    1.158433] pciehp 0000:00:16.2:pcie02: service driver pciehp loaded
[    1.158729] pciehp 0000:00:16.3:pcie02: HPC vendor_id 15ad device_id 7a0 ss_vid 0 ss_did 0
[    1.158966] pciehp 0000:00:16.3:pcie02: service driver pciehp loaded
[    1.159263] pciehp 0000:00:16.4:pcie02: HPC vendor_id 15ad device_id 7a0 ss_vid 0 ss_did 0
[    1.159475] pciehp 0000:00:16.4:pcie02: service driver pciehp loaded
[    1.159794] pciehp 0000:00:16.5:pcie02: HPC vendor_id 15ad device_id 7a0 ss_vid 0 ss_did 0
[    1.159996] pciehp 0000:00:16.5:pcie02: service driver pciehp loaded
[    1.160283] pciehp 0000:00:16.6:pcie02: HPC vendor_id 15ad device_id 7a0 ss_vid 0 ss_did 0
[    1.160495] pciehp 0000:00:16.6:pcie02: service driver pciehp loaded
[    1.160793] pciehp 0000:00:16.7:pcie02: HPC vendor_id 15ad device_id 7a0 ss_vid 0 ss_did 0
[    1.161005] pciehp 0000:00:16.7:pcie02: service driver pciehp loaded
[    1.161301] pciehp 0000:00:17.0:pcie02: HPC vendor_id 15ad device_id 7a0 ss_vid 0 ss_did 0
[    1.161513] pciehp 0000:00:17.0:pcie02: service driver pciehp loaded
[    1.161809] pciehp 0000:00:17.1:pcie02: HPC vendor_id 15ad device_id 7a0 ss_vid 0 ss_did 0
[    1.162024] pciehp 0000:00:17.1:pcie02: service driver pciehp loaded
[    1.162320] pciehp 0000:00:17.2:pcie02: HPC vendor_id 15ad device_id 7a0 ss_vid 0 ss_did 0
[    1.162532] pciehp 0000:00:17.2:pcie02: service driver pciehp loaded
[    1.162828] pciehp 0000:00:17.3:pcie02: HPC vendor_id 15ad device_id 7a0 ss_vid 0 ss_did 0
[    1.163046] pciehp 0000:00:17.3:pcie02: service driver pciehp loaded
[    1.163343] pciehp 0000:00:17.4:pcie02: HPC vendor_id 15ad device_id 7a0 ss_vid 0 ss_did 0
[    1.163555] pciehp 0000:00:17.4:pcie02: service driver pciehp loaded
[    1.163853] pciehp 0000:00:17.5:pcie02: HPC vendor_id 15ad device_id 7a0 ss_vid 0 ss_did 0
[    1.163996] pciehp 0000:00:17.5:pcie02: service driver pciehp loaded
[    1.164281] pciehp 0000:00:17.6:pcie02: HPC vendor_id 15ad device_id 7a0 ss_vid 0 ss_did 0
[    1.164493] pciehp 0000:00:17.6:pcie02: service driver pciehp loaded
[    1.164789] pciehp 0000:00:17.7:pcie02: HPC vendor_id 15ad device_id 7a0 ss_vid 0 ss_did 0
[    1.165002] pciehp 0000:00:17.7:pcie02: service driver pciehp loaded
[    1.165298] pciehp 0000:00:18.0:pcie02: HPC vendor_id 15ad device_id 7a0 ss_vid 0 ss_did 0
[    1.165510] pciehp 0000:00:18.0:pcie02: service driver pciehp loaded
[    1.165807] pciehp 0000:00:18.1:pcie02: HPC vendor_id 15ad device_id 7a0 ss_vid 0 ss_did 0
[    1.166019] pciehp 0000:00:18.1:pcie02: service driver pciehp loaded
[    1.166316] pciehp 0000:00:18.2:pcie02: HPC vendor_id 15ad device_id 7a0 ss_vid 0 ss_did 0
[    1.166529] pciehp 0000:00:18.2:pcie02: service driver pciehp loaded
[    1.166826] pciehp 0000:00:18.3:pcie02: HPC vendor_id 15ad device_id 7a0 ss_vid 0 ss_did 0
[    1.167039] pciehp 0000:00:18.3:pcie02: service driver pciehp loaded
[    1.167335] pciehp 0000:00:18.4:pcie02: HPC vendor_id 15ad device_id 7a0 ss_vid 0 ss_did 0
[    1.167548] pciehp 0000:00:18.4:pcie02: service driver pciehp loaded
[    1.167857] pciehp 0000:00:18.5:pcie02: HPC vendor_id 15ad device_id 7a0 ss_vid 0 ss_did 0
[    1.167996] pciehp 0000:00:18.5:pcie02: service driver pciehp loaded
[    1.168281] pciehp 0000:00:18.6:pcie02: HPC vendor_id 15ad device_id 7a0 ss_vid 0 ss_did 0
[    1.168494] pciehp 0000:00:18.6:pcie02: service driver pciehp loaded
[    1.168797] pciehp 0000:00:18.7:pcie02: HPC vendor_id 15ad device_id 7a0 ss_vid 0 ss_did 0
[    1.169011] pciehp 0000:00:18.7:pcie02: service driver pciehp loaded
[    1.169021] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.169187] ACPI: AC Adapter [ACAD] (on-line)
[    1.169285] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.169288] ACPI: Power Button (FF) [PWRF]
[    1.169318] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    1.169358] ACPI: Sleep Button (CM) [SLPB]
[    1.169426] processor ACPI_CPU:00: registered as cooling_device0
[    1.169429] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.188161] isapnp: Scanning for PnP cards...
[    1.544223] isapnp: No Plug & Play device found
[    1.544440] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.544909] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.545386] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.545840] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.546304] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.546350] brd: module loaded
[    1.546386] loop: module loaded
[    1.546422] Fixed MDIO Bus: probed
[    1.546427] PPP generic driver version 2.4.2
[    1.546461] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.546479] Driver 'sd' needs updating - please use bus_type methods
[    1.546489] Driver 'sr' needs updating - please use bus_type methods
[    1.546525] ata_piix 0000:00:07.1: version 2.12
[    1.546703] scsi0 : ata_piix
[    1.546764] scsi1 : ata_piix
[    1.546800] ata1: PATA max UDMA/33 cmd 0x1f0 ctl 0x3f6 bmdma 0x10c0 irq 14
[    1.546803] ata2: PATA max UDMA/33 cmd 0x170 ctl 0x376 bmdma 0x10c8 irq 15
[    1.546944] ata1: port disabled. ignoring.
[    1.726387] ata2.00: ATAPI: VMware Virtual IDE CDROM Drive, 00000001, max UDMA/33
[    1.726801] ata2.00: configured for UDMA/33
[    1.727148] scsi 1:0:0:0: CD-ROM            NECVMWar VMware IDE CDR10 1.00 PQ: 0 ANSI: 5
[    1.728215] sr0: scsi3-mmc drive: 1x/1x xa/form2 cdda tray
[    1.728223] Uniform CD-ROM driver Revision: 3.20
[    1.728259] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.728286] sr 1:0:0:0: Attached scsi generic sg0 type 5
[    1.728322] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.728359] ehci_hcd 0000:02:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.728418] ehci_hcd 0000:02:02.0: EHCI Host Controller
[    1.728454] ehci_hcd 0000:02:02.0: new USB bus registered, assigned bus number 1
[    1.728580] ehci_hcd 0000:02:02.0: cache line size of 32 is not supported
[    1.728606] ehci_hcd 0000:02:02.0: irq 16, io mem 0xd8900000
[    1.740054] ehci_hcd 0000:02:02.0: USB 2.0 started, EHCI 1.00
[    1.740126] usb usb1: configuration #1 chosen from 1 choice
[    1.740144] hub 1-0:1.0: USB hub found
[    1.740149] hub 1-0:1.0: 6 ports detected
[    1.740185] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.740218] uhci_hcd: USB Universal Host Controller Interface driver
[    1.740253] uhci_hcd 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.740287] uhci_hcd 0000:02:00.0: UHCI Host Controller
[    1.740317] uhci_hcd 0000:02:00.0: new USB bus registered, assigned bus number 2
[    1.740538] uhci_hcd 0000:02:00.0: irq 18, io base 0x00002080
[    1.740650] usb usb2: configuration #1 chosen from 1 choice
[    1.740666] hub 2-0:1.0: USB hub found
[    1.740672] hub 2-0:1.0: 2 ports detected
[    1.740826] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUS] at 0x60,0x64 irq 1,12
[    2.269696] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.269703] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.272119] mice: PS/2 mouse device common for all mice
[    2.272637] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    2.272798] rtc0: alarms up to one month, y3k, 114 bytes nvram
[    2.272858] device-mapper: uevent: version 1.0.3
[    2.272997] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [email]dm-devel@redhat.com[/email]
[    2.273054] device-mapper: multipath: version 1.0.5 loaded
[    2.273057] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.273128] EISA: Probing bus 0 at eisa.0
[    2.273147] Cannot allocate resource for EISA slot 1
[    2.273150] Cannot allocate resource for EISA slot 2
[    2.273152] Cannot allocate resource for EISA slot 3
[    2.273154] Cannot allocate resource for EISA slot 4
[    2.273157] Cannot allocate resource for EISA slot 5
[    2.273159] Cannot allocate resource for EISA slot 6
[    2.273161] Cannot allocate resource for EISA slot 7
[    2.273163] Cannot allocate resource for EISA slot 8
[    2.273165] EISA: Detected 0 cards.
[    2.273196] cpuidle: using governor ladder
[    2.273198] cpuidle: using governor menu
[    2.273303] TCP cubic registered
[    2.273365] NET: Registered protocol family 10
[    2.273571] lo: Disabled Privacy Extensions
[    2.273677] NET: Registered protocol family 17
[    2.273690] Bluetooth: L2CAP ver 2.11
[    2.273692] Bluetooth: L2CAP socket layer initialized
[    2.273695] Bluetooth: SCO (Voice Link) ver 0.6
[    2.273697] Bluetooth: SCO socket layer initialized
[    2.273725] Bluetooth: RFCOMM socket layer initialized
[    2.273730] Bluetooth: RFCOMM TTY layer initialized
[    2.273732] Bluetooth: RFCOMM ver 1.10
[    2.273758] Using IPI No-Shortcut mode
[    2.273804] registered taskstats version 1
[    2.273892]   Magic number: 9:985:295
[    2.273908] tty tty28: hash matches
[    2.293873] rtc_cmos 00:04: setting system clock to 2009-09-15 20:16:22 UTC (1253045782)
[    2.293879] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.293881] EDD information not available.
[    2.293986] Freeing unused kernel memory: 532k freed
[    2.294091] Write protecting the kernel text: 4116k
[    2.294197] Write protecting the kernel read-only data: 1528k
[    2.295488] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    2.384128] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    2.601053] Floppy drive(s): fd0 is 1.44M
[    2.617177] FDC 0 is a post-1991 82077
[    2.620345] Fusion MPT base driver 3.04.07
[    2.620347] Copyright (c) 1999-2008 LSI Corporation
[    2.620501] Fusion MPT SPI Host driver 3.04.07
[    2.620557] mptspi 0000:00:10.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.621300] mptbase: ioc0: Initiating bringup
[    2.624083] pcnet32.c:v1.35 21.Apr.2008 [email]tsbogend@alpha.franken.de[/email]
[    2.624136] pcnet32 0000:02:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.624267] pcnet32: PCnet/PCI II 79C970A at 0x2000, 00:0c:29:b0:e3:12 assigned IRQ 19.
[    2.624565] eth0: registered as PCnet/PCI II 79C970A
[    2.624609] pcnet32: 1 cards_found.
[    2.692304] ioc0: LSI53C1030 B0: Capabilities={Initiator}
[    2.730516] usb 1-1: configuration #1 chosen from 1 choice
[    2.820557] scsi2 : ioc0: LSI53C1030 B0, FwRev=00000000h, Ports=1, MaxQ=128, IRQ=17
[    2.932667] scsi 2:0:0:0: Direct-Access     VMware,  VMware Virtual S 1.0  PQ: 0 ANSI: 2
[    2.932676] scsi target2:0:0: Beginning Domain Validation
[    2.933226] scsi target2:0:0: Domain Validation skipping write tests
[    2.933229] scsi target2:0:0: Ending Domain Validation
[    2.933255] scsi target2:0:0: FAST-40 WIDE SCSI 80.0 MB/s ST (25 ns, offset 127)
[    2.934111] sd 2:0:0:0: [sda] 8388608 512-byte hardware sectors: (4.29 GB/4.00 GiB)
[    2.934144] sd 2:0:0:0: [sda] Write Protect is off
[    2.934147] sd 2:0:0:0: [sda] Mode Sense: 5d 00 00 00
[    2.934197] sd 2:0:0:0: [sda] Cache data unavailable
[    2.934200] sd 2:0:0:0: [sda] Assuming drive cache: write through
[    2.934287] sd 2:0:0:0: [sda] 8388608 512-byte hardware sectors: (4.29 GB/4.00 GiB)
[    2.934328] sd 2:0:0:0: [sda] Write Protect is off
[    2.934331] sd 2:0:0:0: [sda] Mode Sense: 5d 00 00 00
[    2.934376] sd 2:0:0:0: [sda] Cache data unavailable
[    2.934378] sd 2:0:0:0: [sda] Assuming drive cache: write through
[    2.934381]  sda: sda1 sda2 < sda5 >
[    2.934924] sd 2:0:0:0: [sda] Attached SCSI disk
[    2.934974] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    3.001576] PM: Starting manual resume from disk
[    3.001579] PM: Resume from partition 8:5
[    3.001581] PM: Checking hibernation image.
[    3.001634] PM: Resume from disk failed.
[    3.002788] kjournald starting.  Commit interval 5 seconds
[    3.002799] EXT3-fs: mounted filesystem with ordered data mode.
[    3.716791] udev: starting version 141
[    3.776062] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    3.777710] Linux agpgart interface v0.103
[    3.780028] agpgart-intel 0000:00:00.0: Intel 440BX Chipset
[    3.780697] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0x0
[    3.791831] parport_pc 00:08: reported by Plug and Play ACPI
[    3.791954] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[    3.843994] ACPI: I/O resource piix4_smbus [0x1040-0x1047] conflicts with ACPI region SMB_ [0x1040-0x104b]
[    3.843996] ACPI: Device needs an ACPI driver
[    3.843996] piix4_smbus 0000:00:07.3: Host SMBus controller not enabled!
[    4.018197] input: PC Speaker as /devices/platform/pcspkr/input/input4
[    4.020454] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[    4.021667] psmouse serio1: ID: 10 00 64<6>input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[    4.125368] ppdev: user-space parallel port driver
[    4.157641] lp0: using parport0 (interrupt-driven).
[    4.181685] Adding 433712k swap on /dev/sda5.  Priority:-1 extents:1 across:433712k
[    4.694707] EXT3 FS on sda1, internal journal
[    5.348209] type=1505 audit(1253045785.554:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2016
[    5.360151] type=1505 audit(1253045785.566:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2020
[    5.360255] type=1505 audit(1253045785.566:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2020
[    5.360290] type=1505 audit(1253045785.566:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2020
[    5.360322] type=1505 audit(1253045785.566:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2020
[    5.400199] type=1505 audit(1253045785.606:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2025
[    5.400335] type=1505 audit(1253045785.606:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2025
[    5.408152] type=1505 audit(1253045785.614:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2029
[    5.901931] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    5.901934] Bluetooth: BNEP filters: protocol multicast
[    5.905525] Bridge firewalling registered
[   10.800099] eth0: link up
[   23.756569] eth0: no IPv6 routers present
[ 2051.564227] usb 1-1: USB disconnect, address 2
[ 2059.060504] usb 1-1: new high speed USB device using ehci_hcd and address 3
[ 2059.235484] usb 1-1: configuration #1 chosen from 1 choice
[ 2119.108301] usb 1-1: USB disconnect, address 3
[ 2141.220166] usb 1-1: new high speed USB device using ehci_hcd and address 4
[ 2141.393094] usb 1-1: configuration #1 chosen from 1 choice
[ 2157.074312] ppdev0: registered pardevice
[ 2157.120247] ppdev0: unregistered pardevice
[ 2157.524713] ppdev0: registered pardevice
[ 2157.572562] ppdev0: unregistered pardevice
[ 2157.596255] ppdev0: registered pardevice
[ 2157.645022] ppdev0: unregistered pardevice

---

