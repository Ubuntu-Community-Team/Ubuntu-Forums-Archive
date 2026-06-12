---
title: "Compaq f572us with broadcom 4311 wireless card no detection version 9.04 ubuntu"
date: 2009-06-12
forum: Networking &amp; Wireless
---

### Post by pambrocio on 2009-06-12
i have trying to get my wireless working for week now i cant seem to find viable solution

im posting the following for any whos can help:
[B]
output of lspci[/B]

00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation MCP51 PCI-X GeForce Go 6100 (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control

**Jockey Logs**

009-06-12 10:24:59,996 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ab362c>
2009-06-12 10:25:00,063 DEBUG: reading modalias file /lib/modules/2.6.28-11-generic/modules.alias
2009-06-12 10:25:00,417 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2009-06-12 10:25:00,533 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2009-06-12 10:25:00,537 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2009-06-12 10:25:00,546 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-180
2009-06-12 10:25:00,556 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-71
2009-06-12 10:25:00,561 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2009-06-12 10:25:00,568 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2009-06-12 10:25:00,584 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2009-06-12 10:25:00,607 WARNING: modinfo for module fglrx failed: modinfo: could not find module fglrx

2009-06-12 10:25:00,612 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2009-06-12 10:25:00,651 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2009-06-12 10:25:00,651 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2009-06-12 10:25:00,737 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver from name NvidiaDriver
2009-06-12 10:25:00,738 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2009-06-12 10:25:00,739 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2009-06-12 10:25:00,802 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2009-06-12 10:25:00,823 DEBUG: Software modem not available
2009-06-12 10:25:00,824 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2009-06-12 10:25:00,863 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2009-06-12 10:25:00,864 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2009-06-12 10:25:00,864 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2009-06-12 10:25:00,999 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2009-06-12 10:25:01,000 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2009-06-12 10:25:01,034 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2009-06-12 10:25:01,035 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2009-06-12 10:25:01,036 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2009-06-12 10:25:01,049 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2009-06-12 10:25:01,050 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2009-06-12 10:25:01,050 DEBUG: all custom handlers loaded
2009-06-12 10:25:01,051 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ab362c> about HardwareID('modalias', 'pci:v000010DEd000002FEsv0000103Csd000030B7bc05sc00i00')
2009-06-12 10:25:02,119 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ab362c> about HardwareID('modalias', 'input:b0010v001Fp0001e0100-e0,12,kramls1,2,fw')
2009-06-12 10:25:02,359 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2009-06-12 10:25:02,359 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ab362c> about HardwareID('modalias', 'pci:v000010DEd00000266sv0000103Csd000030B7bc01sc01i85')
2009-06-12 10:25:02,366 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ab362c> about HardwareID('modalias', 'pci:v000010DEd00000271sv0000103Csd000030B7bc0Bsc40i00')
2009-06-12 10:25:02,373 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ab362c> about HardwareID('modalias', 'acpi:PNP0800:')
2009-06-12 10:25:02,373 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ab362c> about HardwareID('modalias', 'acpi:HPQ0006:')
2009-06-12 10:25:02,373 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ab362c> about HardwareID('modalias', 'pci:v000010DEd000002F8sv0000103Csd000030B7bc05sc00i00')
2009-06-12 10:25:02,379 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ab362c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2009-06-12 10:25:02,380 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2009-06-12 10:25:02,380 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ab362c> about HardwareID('modalias', 'platform:pcspkr')
2009-06-12 10:25:02,381 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2009-06-12 10:25:02,381 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2009-06-12 10:25:02,381 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ab362c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2009-06-12 10:25:02,408 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ab362c> about HardwareID('modalias', 'pci:v000010DEd0000026Fsv00000000sd00000000bc06sc04i01')
2009-06-12 10:25:02,415 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ab362c> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2009-06-12 10:25:02,415 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2009-06-12 10:25:02,415 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ab362c> about HardwareID('modalias', 'acpi:PNP0C04:')
2009-06-12 10:25:02,416 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ab362c> about HardwareID('modalias', 'pci:v000010DEd0000026Csv0000103Csd000030B7bc04sc03i00')
2009-06-12 10:25:02,422 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2009-06-12 10:25:02,422 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ab362c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2009-06-12 10:25:02,423 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ab362c> about HardwareID('modalias', 'pci:v000010DEd0000027Esv00000000sd00000000bc05sc00i00')
2009-06-12 10:25:02,434 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ab362c> about HardwareID('modalias', 'platform:eisa')
2009-06-12 10:25:02,435 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ab362c> about HardwareID('modalias', 'pci:v000010DEd0000026Esv0000103Csd000030B7bc0Csc03i20')
2009-06-12 10:25:02,441 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ab362c> about HardwareID('modalias', 'pci:v000010DEd000002F3sv0000103Csd000030B7bc05sc00i00')
2009-06-12 10:25:02,447 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ab362c> about HardwareID('modalias', 'acpi:SYN012A:SYN0100:SYN0002:PNP0F13:')
2009-06-12 10:25:02,448 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ab362c> about HardwareID('modalias', 'acpi:PNP0100:')
2009-06-12 10:25:02,448 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ab362c> about HardwareID('modalias', 'pci:v000010DEd000002FAsv0000103Csd000030B7bc05sc00i00')
2009-06-12 10:25:02,455 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ab362c> about HardwareID('modalias', 'acpi:PNP0C01:')
2009-06-12 10:25:02,455 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ab362c> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2009-06-12 10:25:02,455 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ab362c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2009-06-12 10:25:02,455 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ab362c> about HardwareID('modalias', 'pci:v00001022d00001103sv00000000sd00000000bc06sc00i00')
2009-06-12 10:25:02,476 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k8temp', 'jockey_handler': 'KernelModuleHandler'}
2009-06-12 10:25:02,477 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ab362c> about HardwareID('modalias', 'acpi:PNP0103:')
2009-06-12 10:25:02,477 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ab362c> about HardwareID('modalias', 'pci:v00001022d00001100sv00000000sd00000000bc06sc00i00')
2009-06-12 10:25:02,477 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ab362c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2009-06-12 10:25:02,478 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ab362c> about HardwareID('modalias', 'pci:v000010DEd00000264sv0000103Csd000030B7bc0Csc05i00')
2009-06-12 10:25:02,484 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_nforce2', 'jockey_handler': 'KernelModuleHandler'}
2009-06-12 10:25:02,484 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ab362c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2009-06-12 10:25:02,485 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2009-06-12 10:25:02,485 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ab362c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2009-06-12 10:25:02,485 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2009-06-12 10:25:02,485 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ab362c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,112,145,14A,14D,14E,ra0,1,18,1C,mlsfw')
2009-06-12 10:25:02,486 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2009-06-12 10:25:02,486 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2009-06-12 10:25:02,486 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2009-06-12 10:25:02,486 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ab362c> about HardwareID('modalias', 'acpi:PNP0C32:')
2009-06-12 10:25:02,487 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ab362c> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvrF.1F:bd12/05/2007:svnHewlett-Packard:pnPresarioF500(GF596UA#ABA):pvrRev1:rvnQuanta:rn30D3:rvr65.3A:cvnQuanta:ct10:cvrN/A:')
2009-06-12 10:25:02,506 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ab362c> about HardwareID('modalias', 'acpi:PNP0C02:')
2009-06-12 10:25:02,507 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ab362c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2009-06-12 10:25:02,507 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2009-06-12 10:25:02,507 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ab362c> about HardwareID('modalias', 'usb:v413Cp3200d2910dc00dsc00dp00ic03isc01ip02')
2009-06-12 10:25:02,533 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2009-06-12 10:25:02,533 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2009-06-12 10:25:02,533 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ab362c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2009-06-12 10:25:02,534 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ab362c> about HardwareID('modalias', 'pci:v00001022d00001102sv00000000sd00000000bc06sc00i00')
2009-06-12 10:25:02,535 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ab362c> about HardwareID('modalias', 'acpi:PNP0303:')
2009-06-12 10:25:02,535 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ab362c> about HardwareID('modalias', 'acpi:PNP0B00:')
2009-06-12 10:25:02,535 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ab362c> about HardwareID('modalias', 'pci:v000010DEd00000260sv0000103Csd000030B7bc06sc01i00')
2009-06-12 10:25:02,542 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ab362c> about HardwareID('modalias', 'pci:v000010DEd000002F9sv0000103Csd000030B7bc05sc00i00')
2009-06-12 10:25:02,548 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ab362c> about HardwareID('modalias', 'pci:v00001022d00001101sv00000000sd00000000bc06sc00i00')
2009-06-12 10:25:02,549 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ab362c> about HardwareID('modalias', 'pci:v000010DEd00000270sv0000103Csd000030B7bc05sc00i00')
2009-06-12 10:25:02,555 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ab362c> about HardwareID('modalias', 'pci:v000010DEd000002FFsv0000103Csd000030B7bc05sc00i00')
2009-06-12 10:25:02,562 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ab362c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2009-06-12 10:25:02,562 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2009-06-12 10:25:02,562 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ab362c> about HardwareID('modalias', 'acpi:PNP0000:')
2009-06-12 10:25:02,563 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ab362c> about HardwareID('modalias', 'pci:v000010DEd0000027Fsv0000103Csd000030B7bc05sc00i00')
2009-06-12 10:25:02,569 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ab362c> about HardwareID('modalias', 'pci:v000010DEd00000269sv0000103Csd000030B7bc06sc80i00')
2009-06-12 10:25:02,576 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'forcedeth', 'jockey_handler': 'KernelModuleHandler'}
2009-06-12 10:25:02,576 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ab362c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2009-06-12 10:25:02,592 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2009-06-12 10:25:02,592 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2009-06-12 10:25:02,592 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ab362c> about HardwareID('modalias', 'pci:v000010DEd00000247sv0000103Csd000030B7bc03sc00i00')
2009-06-12 10:25:02,599 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
2009-06-12 10:25:02,615 DEBUG: got handler xorg:nvidia-173([NvidiaDriver, nonfree, disabled] NVIDIA accelerated graphics driver)
2009-06-12 10:25:02,748 DEBUG: got handler xorg:nvidia-180([NvidiaDriver, nonfree, disabled] NVIDIA accelerated graphics driver)
2009-06-12 10:25:02,887 DEBUG: got handler xorg:nvidia-96([NvidiaDriver, nonfree, enabled] NVIDIA accelerated graphics driver)
2009-06-12 10:25:03,009 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ab362c> about HardwareID('modalias', 'input:b0019v0000p0002e0000-e0,1,k74,ramlsfw')
2009-06-12 10:25:03,010 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2009-06-12 10:25:03,010 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ab362c> about HardwareID('modalias', 'input:b0003v413Cp3200e0110-e0,1,2,4,k110,111,112,r0,1,8,am4,lsfw')
2009-06-12 10:25:03,010 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2009-06-12 10:25:03,011 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8ab362c> about HardwareID('modalias', 'acpi:PNP0200:')
2009-06-12 10:25:03,011 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8df88cc> about HardwareID('modalias', 'pci:v000010DEd000002FEsv0000103Csd000030B7bc05sc00i00')
2009-06-12 10:25:03,011 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8df88cc> about HardwareID('modalias', 'input:b0010v001Fp0001e0100-e0,12,kramls1,2,fw')
2009-06-12 10:25:03,011 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8df88cc> about HardwareID('modalias', 'pci:v000010DEd00000266sv0000103Csd000030B7bc01sc01i85')
2009-06-12 10:25:03,011 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8df88cc> about HardwareID('modalias', 'pci:v000010DEd00000271sv0000103Csd000030B7bc0Bsc40i00')
2009-06-12 10:25:03,012 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8df88cc> about HardwareID('modalias', 'acpi:PNP0800:')
2009-06-12 10:25:03,012 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8df88cc> about HardwareID('modalias', 'acpi:HPQ0006:')
2009-06-12 10:25:03,012 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8df88cc> about HardwareID('modalias', 'pci:v000010DEd000002F8sv0000103Csd000030B7bc05sc00i00')
2009-06-12 10:25:03,012 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8df88cc> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2009-06-12 10:25:03,012 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8df88cc> about HardwareID('modalias', 'platform:pcspkr')
2009-06-12 10:25:03,012 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8df88cc> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2009-06-12 10:25:03,013 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8df88cc> about HardwareID('modalias', 'pci:v000010DEd0000026Fsv00000000sd00000000bc06sc04i01')
2009-06-12 10:25:03,013 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8df88cc> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2009-06-12 10:25:03,013 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8df88cc> about HardwareID('modalias', 'acpi:PNP0C04:')
2009-06-12 10:25:03,013 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8df88cc> about HardwareID('modalias', 'pci:v000010DEd0000026Csv0000103Csd000030B7bc04sc03i00')
2009-06-12 10:25:03,013 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8df88cc> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2009-06-12 10:25:03,013 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8df88cc> about HardwareID('modalias', 'pci:v000010DEd0000027Esv00000000sd00000000bc05sc00i00')
2009-06-12 10:25:03,014 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8df88cc> about HardwareID('modalias', 'platform:eisa')
2009-06-12 10:25:03,014 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8df88cc> about HardwareID('modalias', 'pci:v000010DEd0000026Esv0000103Csd000030B7bc0Csc03i20')
2009-06-12 10:25:03,014 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8df88cc> about HardwareID('modalias', 'pci:v000010DEd000002F3sv0000103Csd000030B7bc05sc00i00')
2009-06-12 10:25:03,014 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8df88cc> about HardwareID('modalias', 'acpi:SYN012A:SYN0100:SYN0002:PNP0F13:')
2009-06-12 10:25:03,014 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8df88cc> about HardwareID('modalias', 'acpi:PNP0100:')
2009-06-12 10:25:03,014 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8df88cc> about HardwareID('modalias', 'pci:v000010DEd000002FAsv0000103Csd000030B7bc05sc00i00')
2009-06-12 10:25:03,015 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8df88cc> about HardwareID('modalias', 'acpi:PNP0C01:')
2009-06-12 10:25:03,015 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8df88cc> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2009-06-12 10:25:03,015 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8df88cc> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2009-06-12 10:25:03,015 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8df88cc> about HardwareID('modalias', 'pci:v00001022d00001103sv00000000sd00000000bc06sc00i00')
2009-06-12 10:25:03,015 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8df88cc> about HardwareID('modalias', 'acpi:PNP0103:')
2009-06-12 10:25:03,016 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8df88cc> about HardwareID('modalias', 'pci:v00001022d00001100sv00000000sd00000000bc06sc00i00')
2009-06-12 10:25:03,016 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8df88cc> about HardwareID('modalias', 'acpi:LNXTHERM:')
2009-06-12 10:25:03,016 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8df88cc> about HardwareID('modalias', 'pci:v000010DEd00000264sv0000103Csd000030B7bc0Csc05i00')
2009-06-12 10:25:03,016 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8df88cc> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2009-06-12 10:25:03,016 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8df88cc> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2009-06-12 10:25:03,016 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8df88cc> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,112,145,14A,14D,14E,ra0,1,18,1C,mlsfw')
2009-06-12 10:25:03,017 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8df88cc> about HardwareID('modalias', 'acpi:PNP0C32:')
2009-06-12 10:25:03,017 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8df88cc> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvrF.1F:bd12/05/2007:svnHewlett-Packard:pnPresarioF500(GF596UA#ABA):pvrRev1:rvnQuanta:rn30D3:rvr65.3A:cvnQuanta:ct10:cvrN/A:')
2009-06-12 10:25:03,017 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8df88cc> about HardwareID('modalias', 'acpi:PNP0C02:')
2009-06-12 10:25:03,017 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8df88cc> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2009-06-12 10:25:03,017 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8df88cc> about HardwareID('modalias', 'usb:v413Cp3200d2910dc00dsc00dp00ic03isc01ip02')
2009-06-12 10:25:03,018 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8df88cc> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2009-06-12 10:25:03,018 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8df88cc> about HardwareID('modalias', 'pci:v00001022d00001102sv00000000sd00000000bc06sc00i00')
2009-06-12 10:25:03,018 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8df88cc> about HardwareID('modalias', 'acpi:PNP0303:')
2009-06-12 10:25:03,018 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8df88cc> about HardwareID('modalias', 'acpi:PNP0B00:')
2009-06-12 10:25:03,018 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8df88cc> about HardwareID('modalias', 'pci:v000010DEd00000260sv0000103Csd000030B7bc06sc01i00')
2009-06-12 10:25:03,018 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8df88cc> about HardwareID('modalias', 'pci:v000010DEd000002F9sv0000103Csd000030B7bc05sc00i00')
2009-06-12 10:25:03,019 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8df88cc> about HardwareID('modalias', 'pci:v00001022d00001101sv00000000sd00000000bc06sc00i00')
2009-06-12 10:25:03,019 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8df88cc> about HardwareID('modalias', 'pci:v000010DEd00000270sv0000103Csd000030B7bc05sc00i00')
2009-06-12 10:25:03,019 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8df88cc> about HardwareID('modalias', 'pci:v000010DEd000002FFsv0000103Csd000030B7bc05sc00i00')
2009-06-12 10:25:03,019 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8df88cc> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2009-06-12 10:25:03,019 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8df88cc> about HardwareID('modalias', 'acpi:PNP0000:')
2009-06-12 10:25:03,020 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8df88cc> about HardwareID('modalias', 'pci:v000010DEd0000027Fsv0000103Csd000030B7bc05sc00i00')
2009-06-12 10:25:03,020 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8df88cc> about HardwareID('modalias', 'pci:v000010DEd00000269sv0000103Csd000030B7bc06sc80i00')
2009-06-12 10:25:03,020 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8df88cc> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2009-06-12 10:25:03,020 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8df88cc> about HardwareID('modalias', 'pci:v000010DEd00000247sv0000103Csd000030B7bc03sc00i00')
2009-06-12 10:25:03,020 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8df88cc> about HardwareID('modalias', 'input:b0019v0000p0002e0000-e0,1,k74,ramlsfw')
2009-06-12 10:25:03,021 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8df88cc> about HardwareID('modalias', 'input:b0003v413Cp3200e0110-e0,1,2,4,k110,111,112,r0,1,8,am4,lsfw')
2009-06-12 10:25:03,021 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8df88cc> about HardwareID('modalias', 'acpi:PNP0200:')
2009-06-12 10:43:57,713 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xa4f762c>
2009-06-12 10:43:57,797 DEBUG: reading modalias file /lib/modules/2.6.28-11-generic/modules.alias
2009-06-12 10:43:58,112 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2009-06-12 10:43:58,240 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2009-06-12 10:43:58,243 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2009-06-12 10:43:58,253 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-180
2009-06-12 10:43:58,263 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-71
2009-06-12 10:43:58,267 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2009-06-12 10:43:58,274 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2009-06-12 10:43:58,293 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2009-06-12 10:43:58,332 WARNING: modinfo for module fglrx failed: modinfo: could not find module fglrx

**iwconfig**

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

**lshw**

    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory:0
          description: System memory
          physical id: 1
          size: 2644MiB
     *-cpu
          product: AMD Athlon(tm) 64 X2 Dual-Core Processor TK-53
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 15.8.1
          size: 1700MHz
          capacity: 1700MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 256KiB
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: C51 Host Bridge
          vendor: nVidia Corporation
          physical id: 0
          bus info: pci@0000:00:00.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master cap_list
          configuration: latency=0
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 0
          vendor: nVidia Corporation
          physical id: 0.1
          bus info: pci@0000:00:00.1
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:3 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 1
          vendor: nVidia Corporation
          physical id: 0.2
          bus info: pci@0000:00:00.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:4 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 5
          vendor: nVidia Corporation
          physical id: 0.3
          bus info: pci@0000:00:00.3
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:5 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 4
          vendor: nVidia Corporation
          physical id: 0.4
          bus info: pci@0000:00:00.4
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master
          configuration: latency=0
     *-memory:6 UNCLAIMED
          description: RAM memory
          product: C51 Host Bridge
          vendor: nVidia Corporation
          physical id: 0.5
          bus info: pci@0000:00:00.5
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master cap_list
          configuration: latency=0
     *-memory:7 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 3
          vendor: nVidia Corporation
          physical id: 0.6
          bus info: pci@0000:00:00.6
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:8 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 2
          vendor: nVidia Corporation
          physical id: 0.7
          bus info: pci@0000:00:00.7
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-pci:0
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:1
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 3
          bus info: pci@0000:00:03.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci bus_master cap_list
          configuration: driver=pcieport-driver
     *-display
          description: VGA compatible controller
          product: MCP51 PCI-X GeForce Go 6100
          vendor: nVidia Corporation
          physical id: 5
          bus info: pci@0000:00:05.0
          version: a2
          width: 64 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: driver=nvidia latency=0 module=nvidia
     *-memory:9 UNCLAIMED
          description: RAM memory
          product: MCP51 Host Bridge
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP51 LPC Bridge
          vendor: nVidia Corporation
          physical id: a
          bus info: pci@0000:00:0a.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial
          description: SMBus
          product: MCP51 SMBus
          vendor: nVidia Corporation
          physical id: a.1
          bus info: pci@0000:00:0a.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: cap_list
          configuration: driver=nForce2_smbus latency=0 module=i2c_nforce2
     *-processor UNCLAIMED
          description: Co-processor
          product: MCP51 PMU
          vendor: nVidia Corporation
          physical id: a.3
          bus info: pci@0000:00:0a.3
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master
          configuration: latency=0 maxlatency=1 mingnt=3
     *-usb:0
          description: USB Controller
          product: MCP51 USB Controller
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
     *-usb:1
          description: USB Controller
          product: MCP51 USB Controller
          vendor: nVidia Corporation
          physical id: b.1
          bus info: pci@0000:00:0b.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3 module=ehci_hcd
     *-ide:0
          description: IDE interface
          product: MCP51 IDE
          vendor: nVidia Corporation
          physical id: d
          bus info: pci@0000:00:0d.0
          version: f1
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
     *-ide:1
          description: IDE interface
          product: MCP51 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: e
          bus info: pci@0000:00:0e.0
          version: f1
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3 module=sata_nv
     *-pci:2
          description: PCI bridge
          product: MCP51 PCI Bridge
          vendor: nVidia Corporation
          physical id: 10
          bus info: pci@0000:00:10.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pci bus_master cap_list
     *-multimedia
          description: Audio device
          product: MCP51 High Definition Audio
          vendor: nVidia Corporation
          physical id: 10.1
          bus info: pci@0000:00:10.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2 module=snd_hda_intel
     *-bridge
          description: Ethernet interface
          product: MCP51 Ethernet Controller
          vendor: nVidia Corporation
          physical id: 14
          bus info: pci@0000:00:14.0
          logical name: eth0
          version: a3
          serial: 00:1b:24:56:a4:53
          width: 32 bits
          clock: 66MHz
          capabilities: bridge bus_master cap_list ethernet physical
          configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.1.34 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp module=k8temp
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: e6:59:a8:88:1b:54
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

[B]/etc/modprobe.d/blacklist
[/B]blacklist b43
blacklist b43legacy
blacklist ssb[B]

/etc/modprobe.d/ndiswrapper
a[/B]lias pci:v000014E4d00004311sv00001363sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004311sv00001364sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004311sv00001365sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004311sv00001374sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004311sv00001375sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004311sv00001376sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004311sv00001377sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004311sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004312sv0000135Fsd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004312sv00001360sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004312sv00001361sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004312sv00001362sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004312sv00001370sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004312sv00001371sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004312sv00001372sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004312sv00001373sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004312sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004318sv00001355sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004318sv00001356sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004318sv00001357sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004318sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004319sv00001358sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004319sv00001359sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004319sv0000135Asd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004319sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004320sv000000E7sd00000E11bc*sc*i* ndiswrapper
alias pci:v000014E4d00004320sv000012F4sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004320sv000012F8sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004320sv000012FAsd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004320sv000012FBsd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004320sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004324sv000012F9sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004324sv000012FCsd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004324sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004328sv00001366sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004328sv00001367sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004328sv00001368sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004328sv00001369sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004328sv*sd*bc*sc*i* ndiswrapper

---

### Post by superprash2003 on 2009-06-12
here's a good link for broadcom [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by Ayuthia on 2009-06-12
As you mentioned, your wireless card is not showing up.  Usually the card would have shown up in lspci whether the proper modules and firmware are installed or not.

If you have Windows or any other OS installed, are you able to use the wireless card?

---

### Post by pambrocio on 2009-06-15
[Ayuthia]("http://ubuntuforums.org/member.php?u=286983"): yes have tried swapping hard drives with with a friend of with the same laptop top but uses a vista os . Vista recognized the card. is there anything i can do so that ubuntu 9.04 can recognize the card.

Btw. it recognized it once but it generated a jockey error

---

### Post by Ayuthia on 2009-06-15
If you have a working internet connection in Ubuntu, try the following:
```
sudo apt-get update
sudo apt-get install b43-fwcutter
```
The above commands is pretty much what jockey is going to do.  This will install the missing firmware items that the b43 module needs.  It should ask if you want it to fetch the firmware for you.  Say yes.  From there, you can try:
```
sudo modprobe -r b43 ssb wl ndiswrapper
sudo modprobe b43
sudo iwlist scan
```

---

### Post by pambrocio on 2009-06-16
after running the following code i got this output

sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

still no detection

---

### Post by Ayuthia on 2009-06-16
I am not for sure about what to tell you.  Usually lspci will show the wireless card because if it doesn't, it usually means that it is a hardware issue.  I know that I had a similar issue to yours where Vista was able to find it every once in a while.  I then found out that I had a hardware issue and fortunately HP also just sent out a limited warranty to cover it.

Sorry I can't be of much help here.

---

### Post by MrSmileyJr on 2009-08-12
I put in your commands and now it works :-) It seems the other poster does indeed have a hardware issue...

---

