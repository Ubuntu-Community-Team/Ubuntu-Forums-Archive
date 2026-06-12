---
title: "Error activating driver: 'B43legacy' for BCM4303 on Ubuntu 10.10"
date: 2011-03-27
forum: Networking &amp; Wireless
---

### Post by foetus66 on 2011-03-27
I'm new to Ubuntu as of yesterday, and know very little of Linux in general.  I tried RedHat for a while about 10 years ago and remember almost nothing from the experience.  I'm up and running with everything working great with one exception -- my wireless.

The error:
[IMG]http://peebomb.com/wtvr/b43legacyactivateerror.png[/IMG]

Contents of jockey.log as suggested:
-Sorry, it's long.  Not sure what (if anything) is relevant.
```
2011-03-26 20:00:15,477 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d16fcc>
2011-03-26 20:00:15,479 DEBUG: reading modalias file /lib/modules/2.6.35-28-generic/modules.alias
2011-03-26 20:00:15,693 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2011-03-26 20:00:15,694 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2011-03-26 20:00:15,694 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-03-26 20:00:15,762 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2011-03-26 20:00:15,764 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2011-03-26 20:00:15,768 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2011-03-26 20:00:15,771 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2011-03-26 20:00:15,777 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2011-03-26 20:00:16,208 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2011-03-26 20:00:16,232 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2011-03-26 20:00:16,233 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2011-03-26 20:00:16,253 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2011-03-26 20:00:16,253 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2011-03-26 20:00:16,253 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2011-03-26 20:00:16,262 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2011-03-26 20:00:16,263 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2011-03-26 20:00:16,279 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-03-26 20:00:16,284 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-03-26 20:00:16,285 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2011-03-26 20:00:16,298 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-03-26 20:00:16,298 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2011-03-26 20:00:16,304 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-03-26 20:00:16,305 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2011-03-26 20:00:16,318 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-03-26 20:00:16,319 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2011-03-26 20:00:16,339 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2011-03-26 20:00:16,340 DEBUG: Firmware for DVB cards not available
2011-03-26 20:00:16,340 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2011-03-26 20:00:16,346 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2011-03-26 20:00:16,347 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2011-03-26 20:00:16,347 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2011-03-26 20:00:16,347 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2011-03-26 20:00:16,363 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-03-26 20:00:16,364 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2011-03-26 20:00:16,393 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2011-03-26 20:00:16,393 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2011-03-26 20:00:16,423 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2011-03-26 20:00:16,450 DEBUG: Software modem not available
2011-03-26 20:00:16,451 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-03-26 20:00:16,465 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-03-26 20:00:16,483 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2011-03-26 20:00:16,483 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2011-03-26 20:00:16,483 DEBUG: all custom handlers loaded
2011-03-26 20:00:16,483 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d16fcc> about HardwareID('modalias', 'pci:v000010DEd000001EDsv00001043sd000080ACbc05sc00i00')
2011-03-26 20:00:17,064 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d16fcc> about HardwareID('modalias', 'pci:v00001095d00003112sv00001095sd00006112bc01sc04i00')
2011-03-26 20:00:17,251 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sata_sil', 'jockey_handler': 'KernelModuleHandler'}
2011-03-26 20:00:17,252 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d16fcc> about HardwareID('modalias', 'pci:v000011ABd00004320sv00001043sd0000811Abc02sc00i00')
2011-03-26 20:00:17,300 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'skge', 'jockey_handler': 'KernelModuleHandler'}
2011-03-26 20:00:17,301 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d16fcc> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-03-26 20:00:17,301 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d16fcc> about HardwareID('modalias', 'acpi:PNP0200:')
2011-03-26 20:00:17,301 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d16fcc> about HardwareID('modalias', 'pci:v000010DEd000001ECsv00001043sd000080ACbc05sc00i00')
2011-03-26 20:00:17,309 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d16fcc> about HardwareID('modalias', 'platform:eisa')
2011-03-26 20:00:17,311 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d16fcc> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2011-03-26 20:00:17,348 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d16fcc> about HardwareID('modalias', 'pci:v000010DEd00000065sv00001043sd00000C11bc01sc01i8a')
2011-03-26 20:00:17,357 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_amd', 'jockey_handler': 'KernelModuleHandler'}
2011-03-26 20:00:17,357 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d16fcc> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-03-26 20:00:17,366 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-03-26 20:00:17,366 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d16fcc> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-03-26 20:00:17,366 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d16fcc> about HardwareID('modalias', 'pci:v000010DEd0000006Esv00001043sd0000809Abc0Csc00i10')
2011-03-26 20:00:17,375 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ohci1394', 'jockey_handler': 'KernelModuleHandler'}
2011-03-26 20:00:17,375 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2011-03-26 20:00:17,375 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d16fcc> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-03-26 20:00:17,376 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d16fcc> about HardwareID('modalias', 'pci:v000010DEd00000068sv00001043sd00000C11bc0Csc03i20')
2011-03-26 20:00:17,385 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d16fcc> about HardwareID('modalias', 'platform:regulatory')
2011-03-26 20:00:17,386 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d16fcc> about HardwareID('modalias', 'pci:v000014E4d00004301sv00001737sd00004301bc02sc80i00')
2011-03-26 20:00:17,465 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ssb', 'jockey_handler': 'KernelModuleHandler'}
2011-03-26 20:00:17,465 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d16fcc> about HardwareID('modalias', 'pci:v000010DEd000001E0sv00001043sd000080ACbc06sc00i00')
2011-03-26 20:00:17,473 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_agp', 'jockey_handler': 'KernelModuleHandler'}
2011-03-26 20:00:17,474 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d16fcc> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-03-26 20:00:17,474 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d16fcc> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-03-26 20:00:17,475 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d16fcc> about HardwareID('modalias', 'pci:v000010DEd000001EBsv00001043sd000080ACbc05sc00i00')
2011-03-26 20:00:17,483 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d16fcc> about HardwareID('modalias', 'acpi:PNP0800:')
2011-03-26 20:00:17,483 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d16fcc> about HardwareID('modalias', 'acpi:PNPB006:')
2011-03-26 20:00:17,484 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d16fcc> about HardwareID('modalias', 'acpi:device:')
2011-03-26 20:00:17,484 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d16fcc> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-03-26 20:00:17,484 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d16fcc> about HardwareID('modalias', 'pci:v0000102Bd00000525sv0000102Bsd00003693bc03sc00i00')
2011-03-26 20:00:17,492 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'matroxfb_base', 'jockey_handler': 'KernelModuleHandler'}
2011-03-26 20:00:17,492 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'matrox_w1', 'jockey_handler': 'KernelModuleHandler'}
2011-03-26 20:00:17,492 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d16fcc> about HardwareID('modalias', 'acpi:LNXTHERM:')
2011-03-26 20:00:17,493 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d16fcc> about HardwareID('modalias', 'pci:v000010DEd0000006Csv00000000sd00000000bc06sc04i00')
2011-03-26 20:00:17,501 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'shpchp', 'jockey_handler': 'KernelModuleHandler'}
2011-03-26 20:00:17,502 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d16fcc> about HardwareID('modalias', 'input:b0003v045Ep0040e0100-e0,1,2,4,k110,111,112,r0,1,8,am4,lsfw')
2011-03-26 20:00:17,502 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-03-26 20:00:17,503 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d16fcc> about HardwareID('modalias', 'ssb:v4243id0807rev01')
2011-03-26 20:00:17,507 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d16fcc> about HardwareID('modalias', 'acpi:PNPB02F:')
2011-03-26 20:00:17,507 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d16fcc> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2011-03-26 20:00:17,507 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d16fcc> about HardwareID('modalias', 'dmi:bvnPhoenixTechnologies,LTD:bvrASUSA7N8X-EDeluxeACPIBIOSRev1008:bd12/05/2003:svnASUSTeKComputerINC.:pnA7N8X-E:pvrREV2.xx:rvnASUSTeKComputerINC.:rnA7N8X-E:rvrREV2.xx:cvnChassisManufactture:ct3:cvrChassisVersion:')
2011-03-26 20:00:17,531 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d16fcc> about HardwareID('modalias', 'acpi:PNP0100:')
2011-03-26 20:00:17,532 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d16fcc> about HardwareID('modalias', 'ssb:v4243id0806rev02')
2011-03-26 20:00:17,532 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'b44', 'jockey_handler': 'KernelModuleHandler'}
2011-03-26 20:00:17,532 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d16fcc> about HardwareID('modalias', 'usb:v413Cp2107d0080dc00dsc00dp00ic03isc01ip01')
2011-03-26 20:00:17,558 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-03-26 20:00:17,559 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d16fcc> about HardwareID('modalias', 'usb:v045Ep0040d0121dc00dsc00dp00ic03isc01ip02')
2011-03-26 20:00:17,665 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-03-26 20:00:17,665 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d16fcc> about HardwareID('modalias', 'acpi:PNP0401:')
2011-03-26 20:00:17,666 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d16fcc> about HardwareID('modalias', 'acpi:PNP0501:')
2011-03-26 20:00:17,666 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d16fcc> about HardwareID('modalias', 'pci:v000010DEd0000006Asv00001043sd00008095bc04sc01i00')
2011-03-26 20:00:17,675 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_intel8x0', 'jockey_handler': 'KernelModuleHandler'}
2011-03-26 20:00:17,675 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d16fcc> about HardwareID('modalias', 'pci:v000010DEd000001EFsv00001043sd000080ACbc05sc00i00')
2011-03-26 20:00:17,683 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d16fcc> about HardwareID('modalias', 'pci:v000010DEd0000006Bsv00001043sd00000C11bc04sc01i00')
2011-03-26 20:00:17,692 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d16fcc> about HardwareID('modalias', 'pci:v000010DEd00000060sv00001043sd000080ADbc06sc01i00')
2011-03-26 20:00:17,700 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d16fcc> about HardwareID('modalias', 'pci:v000010DEd000001EEsv00001043sd000080ACbc05sc00i00')
2011-03-26 20:00:17,709 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d16fcc> about HardwareID('modalias', 'acpi:PNP0000:')
2011-03-26 20:00:17,710 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d16fcc> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2011-03-26 20:00:17,710 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'option', 'jockey_handler': 'KernelModuleHandler'}
2011-03-26 20:00:17,711 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d16fcc> about HardwareID('modalias', 'pci:v000010DEd00000064sv00001043sd00000C11bc0Csc05i00')
2011-03-26 20:00:17,720 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_nforce2', 'jockey_handler': 'KernelModuleHandler'}
2011-03-26 20:00:17,720 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d16fcc> about HardwareID('modalias', 'platform:pcspkr')
2011-03-26 20:00:17,721 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2011-03-26 20:00:17,721 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2011-03-26 20:00:17,721 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d16fcc> about HardwareID('modalias', 'pci:v000010DEd000001E8sv00000000sd00000000bc06sc04i00')
2011-03-26 20:00:17,730 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'shpchp', 'jockey_handler': 'KernelModuleHandler'}
2011-03-26 20:00:17,730 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d16fcc> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2011-03-26 20:00:17,745 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2011-03-26 20:00:17,746 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d16fcc> about HardwareID('modalias', 'ssb:v4243id0812rev02')
2011-03-26 20:00:17,746 DEBUG: got handler firmware:b43legacy([B43LegacyHandler, free, disabled] Broadcom B43legacy wireless driver)
2011-03-26 20:00:17,870 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d16fcc> about HardwareID('modalias', 'pci:v000010DEd00000066sv00001043sd000080A7bc02sc00i00')
2011-03-26 20:00:17,879 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'forcedeth', 'jockey_handler': 'KernelModuleHandler'}
2011-03-26 20:00:17,880 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d16fcc> about HardwareID('modalias', 'input:b0003v413Cp2107e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8C,8E,96,98,9E,9F,A1,A3,A4,A5,A6,AD,B0,B1,B2,B3,B4,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2011-03-26 20:00:17,880 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-03-26 20:00:17,880 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d16fcc> about HardwareID('modalias', 'acpi:PNP0700:')
2011-03-26 20:00:17,880 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fd564c> about HardwareID('modalias', 'pci:v000010DEd000001EDsv00001043sd000080ACbc05sc00i00')
2011-03-26 20:00:17,881 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fd564c> about HardwareID('modalias', 'pci:v00001095d00003112sv00001095sd00006112bc01sc04i00')
2011-03-26 20:00:17,881 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fd564c> about HardwareID('modalias', 'pci:v000011ABd00004320sv00001043sd0000811Abc02sc00i00')
2011-03-26 20:00:17,881 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fd564c> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-03-26 20:00:17,881 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fd564c> about HardwareID('modalias', 'acpi:PNP0200:')
2011-03-26 20:00:17,881 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fd564c> about HardwareID('modalias', 'pci:v000010DEd000001ECsv00001043sd000080ACbc05sc00i00')
2011-03-26 20:00:17,881 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fd564c> about HardwareID('modalias', 'platform:eisa')
2011-03-26 20:00:17,881 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fd564c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2011-03-26 20:00:17,882 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fd564c> about HardwareID('modalias', 'pci:v000010DEd00000065sv00001043sd00000C11bc01sc01i8a')
2011-03-26 20:00:17,882 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fd564c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-03-26 20:00:17,882 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fd564c> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-03-26 20:00:17,883 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fd564c> about HardwareID('modalias', 'pci:v000010DEd0000006Esv00001043sd0000809Abc0Csc00i10')
2011-03-26 20:00:17,883 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fd564c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-03-26 20:00:17,883 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fd564c> about HardwareID('modalias', 'pci:v000010DEd00000068sv00001043sd00000C11bc0Csc03i20')
2011-03-26 20:00:17,883 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fd564c> about HardwareID('modalias', 'platform:regulatory')
2011-03-26 20:00:17,883 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fd564c> about HardwareID('modalias', 'pci:v000014E4d00004301sv00001737sd00004301bc02sc80i00')
2011-03-26 20:00:17,883 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fd564c> about HardwareID('modalias', 'pci:v000010DEd000001E0sv00001043sd000080ACbc06sc00i00')
2011-03-26 20:00:17,884 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fd564c> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-03-26 20:00:17,884 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fd564c> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-03-26 20:00:17,884 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fd564c> about HardwareID('modalias', 'pci:v000010DEd000001EBsv00001043sd000080ACbc05sc00i00')
2011-03-26 20:00:17,884 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fd564c> about HardwareID('modalias', 'acpi:PNP0800:')
2011-03-26 20:00:17,884 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fd564c> about HardwareID('modalias', 'acpi:PNPB006:')
2011-03-26 20:00:17,884 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fd564c> about HardwareID('modalias', 'acpi:device:')
2011-03-26 20:00:17,885 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fd564c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-03-26 20:00:17,885 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fd564c> about HardwareID('modalias', 'pci:v0000102Bd00000525sv0000102Bsd00003693bc03sc00i00')
2011-03-26 20:00:17,885 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fd564c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2011-03-26 20:00:17,885 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fd564c> about HardwareID('modalias', 'pci:v000010DEd0000006Csv00000000sd00000000bc06sc04i00')
2011-03-26 20:00:17,885 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fd564c> about HardwareID('modalias', 'input:b0003v045Ep0040e0100-e0,1,2,4,k110,111,112,r0,1,8,am4,lsfw')
2011-03-26 20:00:17,885 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fd564c> about HardwareID('modalias', 'ssb:v4243id0807rev01')
2011-03-26 20:00:17,885 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fd564c> about HardwareID('modalias', 'acpi:PNPB02F:')
2011-03-26 20:00:17,886 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fd564c> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2011-03-26 20:00:17,886 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fd564c> about HardwareID('modalias', 'dmi:bvnPhoenixTechnologies,LTD:bvrASUSA7N8X-EDeluxeACPIBIOSRev1008:bd12/05/2003:svnASUSTeKComputerINC.:pnA7N8X-E:pvrREV2.xx:rvnASUSTeKComputerINC.:rnA7N8X-E:rvrREV2.xx:cvnChassisManufactture:ct3:cvrChassisVersion:')
2011-03-26 20:00:17,886 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fd564c> about HardwareID('modalias', 'acpi:PNP0100:')
2011-03-26 20:00:17,886 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fd564c> about HardwareID('modalias', 'ssb:v4243id0806rev02')
2011-03-26 20:00:17,886 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fd564c> about HardwareID('modalias', 'usb:v413Cp2107d0080dc00dsc00dp00ic03isc01ip01')
2011-03-26 20:00:17,886 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fd564c> about HardwareID('modalias', 'usb:v045Ep0040d0121dc00dsc00dp00ic03isc01ip02')
2011-03-26 20:00:17,887 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fd564c> about HardwareID('modalias', 'acpi:PNP0401:')
2011-03-26 20:00:17,887 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fd564c> about HardwareID('modalias', 'acpi:PNP0501:')
2011-03-26 20:00:17,887 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fd564c> about HardwareID('modalias', 'pci:v000010DEd0000006Asv00001043sd00008095bc04sc01i00')
2011-03-26 20:00:17,887 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fd564c> about HardwareID('modalias', 'pci:v000010DEd000001EFsv00001043sd000080ACbc05sc00i00')
2011-03-26 20:00:17,887 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fd564c> about HardwareID('modalias', 'pci:v000010DEd0000006Bsv00001043sd00000C11bc04sc01i00')
2011-03-26 20:00:17,887 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fd564c> about HardwareID('modalias', 'pci:v000010DEd00000060sv00001043sd000080ADbc06sc01i00')
2011-03-26 20:00:17,887 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fd564c> about HardwareID('modalias', 'pci:v000010DEd000001EEsv00001043sd000080ACbc05sc00i00')
2011-03-26 20:00:17,888 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fd564c> about HardwareID('modalias', 'acpi:PNP0000:')
2011-03-26 20:00:17,888 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fd564c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2011-03-26 20:00:17,888 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fd564c> about HardwareID('modalias', 'pci:v000010DEd00000064sv00001043sd00000C11bc0Csc05i00')
2011-03-26 20:00:17,888 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fd564c> about HardwareID('modalias', 'platform:pcspkr')
2011-03-26 20:00:17,888 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fd564c> about HardwareID('modalias', 'pci:v000010DEd000001E8sv00000000sd00000000bc06sc04i00')
2011-03-26 20:00:17,888 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fd564c> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2011-03-26 20:00:17,889 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fd564c> about HardwareID('modalias', 'ssb:v4243id0812rev02')
2011-03-26 20:00:17,889 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fd564c> about HardwareID('modalias', 'pci:v000010DEd00000066sv00001043sd000080A7bc02sc00i00')
2011-03-26 20:00:17,889 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fd564c> about HardwareID('modalias', 'input:b0003v413Cp2107e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8C,8E,96,98,9E,9F,A1,A3,A4,A5,A6,AD,B0,B1,B2,B3,B4,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2011-03-26 20:00:17,889 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fd564c> about HardwareID('modalias', 'acpi:PNP0700:')
2011-03-26 20:00:31,573 DEBUG: unbind/rebind on driver /sys/module/b43legacy/drivers/ssb:b43legacy: device ssb0:0
2011-03-26 20:00:35,537 DEBUG: writing back check cache /var/cache/jockey/check
2011-03-26 20:00:36,162 DEBUG: writing back check cache /var/cache/jockey/check
2011-03-26 20:00:36,758 DEBUG: writing back check cache /var/cache/jockey/check
2011-03-26 20:02:46,065 DEBUG: Shutting down
```

---

### Post by foetus66 on 2011-03-27
Oops, almost forgot -- here's the info requested from the stickied thread:

1. Machine Brand and Model (PC/Laptop):
```
ASUS A7N8X-E ATX motherboard, AMD Athlon 2800, 1gb RAM
```2. Wireless Brand, Model, and Wireless Chipset
```
$ lspci | grep Broadcom
01:09.0 Network controller: Broadcom Corporation BCM4303 802.11b Wireless LAN Controller (rev 02)
```3. check interface:
```
$ iwconfig wlan0
wlan0     IEEE 802.11b  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```4. Check for modules:
```
$ lsmod | grep b43
b43                   168681  0 
b43legacy             115004  0 
mac80211              231959  2 b43,b43legacy
cfg80211              144694  3 b43,b43legacy,mac80211
led_class               2633  2 b43,b43legacy
ssb                    39320  3 b43,b43legacy,b44
```5. Kernel boot messages
```
$ dmesg | grep b43
[    1.624555] b43-pci-bridge 0000:01:09.0: PCI INT A -> Link[APC2] -> GSI 17 (level, high) -> IRQ 17
[   15.334786] b43legacy-phy0: Broadcom 4301 WLAN found
[   15.356048] b43legacy-phy0 debug: Found PHY: Analog 0, Type 1, Revision 4
[   15.356091] b43legacy-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2053, Revision 2
[   15.380075] b43legacy-phy0 debug: Radio initialized
[   16.260128] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[   16.370854] b43legacy-phy0 debug: Chip initialized
[   16.371136] b43legacy-phy0 debug: 30-bit DMA initialized
[   16.386161] b43legacy-phy0 warning: LEDs: Unknown behaviour 0x2B
[   16.386168] b43legacy-phy0 warning: LEDs: Unknown behaviour 0x78
[   16.386171] b43legacy-phy0 warning: LEDs: Unknown behaviour 0x2E
[   16.386174] b43legacy-phy0 warning: LEDs: Unknown behaviour 0x19
[   16.386200] b43legacy-phy0 debug: Wireless interface started
[   16.386231] b43legacy-phy0: Radio hardware status changed to DISABLED
[   16.386236] b43legacy-phy0 debug: Radio initialized
[   16.387532] b43legacy-phy0 debug: Adding Interface type 2
[   16.420068] b43legacy-phy0: Radio turned on by software
[   16.420075] b43legacy-phy0: The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.
[   16.421222] b43legacy-phy0 debug: Removing Interface type 2
[   16.421262] b43legacy-phy0 debug: Wireless interface stopped
[   16.421357] b43legacy-phy0 debug: DMA-30 0x0260 (RX) max used slots: 0/64
[   16.421401] b43legacy-phy0 debug: DMA-30 0x0200 (RX) max used slots: 0/64
[   16.421443] b43legacy-phy0 debug: DMA-30 0x02A0 (TX) max used slots: 0/128
[   16.428067] b43legacy-phy0 debug: DMA-30 0x0280 (TX) max used slots: 0/128
[   16.436078] b43legacy-phy0 debug: DMA-30 0x0260 (TX) max used slots: 0/128
[   16.444065] b43legacy-phy0 debug: DMA-30 0x0240 (TX) max used slots: 0/128
[   16.452204] b43legacy-phy0 debug: DMA-30 0x0220 (TX) max used slots: 0/128
[   16.460067] b43legacy-phy0 debug: DMA-30 0x0200 (TX) max used slots: 0/128
[   16.468048] b43legacy-phy0 debug: Radio initialized
[   16.468063] b43legacy-phy0 debug: Radio initialized
[   98.506116] b43legacy-phy1: Broadcom 4301 WLAN found
[   98.528037] b43legacy-phy1 debug: Found PHY: Analog 0, Type 1, Revision 4
[   98.528063] b43legacy-phy1 debug: Found Radio: Manuf 0x17F, Version 0x2053, Revision 2
[   98.552032] b43legacy-phy1 debug: Radio initialized
[   98.771108] b43legacy-phy1: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[   98.880054] b43legacy-phy1 debug: Chip initialized
[   98.900335] b43legacy-phy1 debug: 30-bit DMA initialized
[   98.901956] b43legacy-phy1 warning: LEDs: Unknown behaviour 0x2B
[   98.901962] b43legacy-phy1 warning: LEDs: Unknown behaviour 0x78
[   98.901965] b43legacy-phy1 warning: LEDs: Unknown behaviour 0x2E
[   98.901968] b43legacy-phy1 warning: LEDs: Unknown behaviour 0x19
[   98.901993] b43legacy-phy1 debug: Wireless interface started
[   98.902023] b43legacy-phy1: Radio hardware status changed to DISABLED
[   98.902028] b43legacy-phy1 debug: Radio initialized
[   98.903488] b43legacy-phy1 debug: Adding Interface type 2
[   98.936052] b43legacy-phy1: Radio turned on by software
[   98.936059] b43legacy-phy1: The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.
[   98.937426] b43legacy-phy1 debug: Removing Interface type 2
[   98.937468] b43legacy-phy1 debug: Wireless interface stopped
[   98.937566] b43legacy-phy1 debug: DMA-30 0x0260 (RX) max used slots: 0/64
[   98.937623] b43legacy-phy1 debug: DMA-30 0x0200 (RX) max used slots: 0/64
[   98.937673] b43legacy-phy1 debug: DMA-30 0x02A0 (TX) max used slots: 0/128
[   98.944049] b43legacy-phy1 debug: DMA-30 0x0280 (TX) max used slots: 0/128
[   98.952057] b43legacy-phy1 debug: DMA-30 0x0260 (TX) max used slots: 0/128
[   98.960049] b43legacy-phy1 debug: DMA-30 0x0240 (TX) max used slots: 0/128
[   98.968058] b43legacy-phy1 debug: DMA-30 0x0220 (TX) max used slots: 0/128
[   98.976062] b43legacy-phy1 debug: DMA-30 0x0200 (TX) max used slots: 0/128
[   98.984049] b43legacy-phy1 debug: Radio initialized
[   98.984063] b43legacy-phy1 debug: Radio initialized
[ 2286.792446] b43legacy-phy2: Broadcom 4301 WLAN found
[ 2286.816024] b43legacy-phy2 debug: Found PHY: Analog 0, Type 1, Revision 4
[ 2286.816049] b43legacy-phy2 debug: Found Radio: Manuf 0x17F, Version 0x2053, Revision 2
[ 2286.840026] b43legacy-phy2 debug: Radio initialized
[ 2287.064056] b43legacy-phy2: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[ 2287.184071] b43legacy-phy2 debug: Chip initialized
[ 2287.196311] b43legacy-phy2 debug: 30-bit DMA initialized
[ 2287.197933] b43legacy-phy2 warning: LEDs: Unknown behaviour 0x2B
[ 2287.197940] b43legacy-phy2 warning: LEDs: Unknown behaviour 0x78
[ 2287.197943] b43legacy-phy2 warning: LEDs: Unknown behaviour 0x2E
[ 2287.197946] b43legacy-phy2 warning: LEDs: Unknown behaviour 0x19
[ 2287.197971] b43legacy-phy2 debug: Wireless interface started
[ 2287.198001] b43legacy-phy2: Radio hardware status changed to DISABLED
[ 2287.198007] b43legacy-phy2 debug: Radio initialized
[ 2287.199476] b43legacy-phy2 debug: Adding Interface type 2
[ 2287.232033] b43legacy-phy2: Radio turned on by software
[ 2287.232040] b43legacy-phy2: The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.
[ 2287.233232] b43legacy-phy2 debug: Removing Interface type 2
[ 2287.233273] b43legacy-phy2 debug: Wireless interface stopped
[ 2287.233369] b43legacy-phy2 debug: DMA-30 0x0260 (RX) max used slots: 0/64
[ 2287.233422] b43legacy-phy2 debug: DMA-30 0x0200 (RX) max used slots: 0/64
[ 2287.233474] b43legacy-phy2 debug: DMA-30 0x02A0 (TX) max used slots: 0/128
[ 2287.240060] b43legacy-phy2 debug: DMA-30 0x0280 (TX) max used slots: 0/128
[ 2287.248050] b43legacy-phy2 debug: DMA-30 0x0260 (TX) max used slots: 0/128
[ 2287.256075] b43legacy-phy2 debug: DMA-30 0x0240 (TX) max used slots: 0/128
[ 2287.264055] b43legacy-phy2 debug: DMA-30 0x0220 (TX) max used slots: 0/128
[ 2287.272048] b43legacy-phy2 debug: DMA-30 0x0200 (TX) max used slots: 0/128
[ 2287.280056] b43legacy-phy2 debug: Radio initialized
[ 2287.280071] b43legacy-phy2 debug: Radio initialized
[ 2398.660442] b43legacy-phy3: Broadcom 4301 WLAN found
[ 2398.684024] b43legacy-phy3 debug: Found PHY: Analog 0, Type 1, Revision 4
[ 2398.684048] b43legacy-phy3 debug: Found Radio: Manuf 0x17F, Version 0x2053, Revision 2
[ 2398.708031] b43legacy-phy3 debug: Radio initialized
[ 2398.900058] b43legacy-phy3: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[ 2399.064351] b43legacy-phy3 debug: Chip initialized
[ 2399.064650] b43legacy-phy3 debug: 30-bit DMA initialized
[ 2399.066104] b43legacy-phy3 warning: LEDs: Unknown behaviour 0x2B
[ 2399.066110] b43legacy-phy3 warning: LEDs: Unknown behaviour 0x78
[ 2399.066113] b43legacy-phy3 warning: LEDs: Unknown behaviour 0x2E
[ 2399.066116] b43legacy-phy3 warning: LEDs: Unknown behaviour 0x19
[ 2399.066141] b43legacy-phy3 debug: Wireless interface started
[ 2399.066171] b43legacy-phy3: Radio hardware status changed to DISABLED
[ 2399.066176] b43legacy-phy3 debug: Radio initialized
[ 2399.067447] b43legacy-phy3 debug: Adding Interface type 2
[ 2399.100054] b43legacy-phy3: Radio turned on by software
[ 2399.100061] b43legacy-phy3: The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.
[ 2399.101277] b43legacy-phy3 debug: Removing Interface type 2
[ 2399.101318] b43legacy-phy3 debug: Wireless interface stopped
[ 2399.101417] b43legacy-phy3 debug: DMA-30 0x0260 (RX) max used slots: 0/64
[ 2399.101463] b43legacy-phy3 debug: DMA-30 0x0200 (RX) max used slots: 0/64
[ 2399.101508] b43legacy-phy3 debug: DMA-30 0x02A0 (TX) max used slots: 0/128
[ 2399.108056] b43legacy-phy3 debug: DMA-30 0x0280 (TX) max used slots: 0/128
[ 2399.116079] b43legacy-phy3 debug: DMA-30 0x0260 (TX) max used slots: 0/128
[ 2399.124044] b43legacy-phy3 debug: DMA-30 0x0240 (TX) max used slots: 0/128
[ 2399.132058] b43legacy-phy3 debug: DMA-30 0x0220 (TX) max used slots: 0/128
[ 2399.140064] b43legacy-phy3 debug: DMA-30 0x0200 (TX) max used slots: 0/128
[ 2399.148049] b43legacy-phy3 debug: Radio initialized
[ 2399.148064] b43legacy-phy3 debug: Radio initialized

```Also did this:```
$ dmesg | grep Broadcom
[   15.334786] b43legacy-phy0: Broadcom 4301 WLAN found
[   15.680517] Broadcom 43xx-legacy driver loaded [ Features: PLID, Firmware-ID: FW10 ]
[   98.506116] b43legacy-phy1: Broadcom 4301 WLAN found
[   98.521443] Broadcom 43xx driver loaded [ Features: PL, Firmware-ID: FW13 ]
[ 2286.792446] b43legacy-phy2: Broadcom 4301 WLAN found
[ 2398.660442] b43legacy-phy3: Broadcom 4301 WLAN found
```
6. Network configuration
```
$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: nForce2 Ethernet Controller
       vendor: nVidia Corporation
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth1
       version: a1
       serial: 00:0e:a6:3d:9c:78
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
       resources: irq:22 memory:ec086000-ec086fff ioport:e400(size=8)
  *-network:0
       description: Ethernet interface
       product: 88E8001 Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 4
       bus info: pci@0000:01:04.0
       logical name: eth0
       version: 13
       serial: 00:0e:a6:3d:a7:fc
       size: 1GB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm vpd bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.13 duplex=full firmware=N/A ip=192.168.137.113 latency=32 link=yes maxlatency=31 mingnt=23 multicast=yes port=twisted pair speed=1GB/s
       resources: irq:17 memory:eb000000-eb003fff ioport:a000(size=256) memory:40080000-4009ffff
  *-network:1
       description: Network controller
       product: BCM4303 802.11b Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:01:09.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=b43-pci-bridge latency=32
       resources: irq:17 memory:eb004000-eb005fff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:06:25:1b:b9:34
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43legacy driverversion=2.6.35-28-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11b
```7. Scan for networks:
```
$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down
```8. Ubuntu version:
```
$ lsb_release -d
Description:    Ubuntu 10.10
```9. Kernel/Architecture (32 bit)
```
$ uname -mr
2.6.35-28-generic i686
```10. Restarting the network:
```
OK
```

---

### Post by bkratz on 2011-03-27
In the boot messages:

The hardware RF-kill button still turns the radio physically off. [COLOR="Red"]Press the button to turn it on[/COLOR].

You might also show the output of 

rfkill list


if no output--(it may not be installed):

sudo apt-get install rfkill

then repeat  the rfkill list

---

### Post by foetus66 on 2011-03-29
Thanks for the response!

```
$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
```

This PCI wireless card doesn't have any kind of physical switch or button.  I tried monkeying around in the BIOS settings but didn't have any luck there either.  It still comes up with that same line about RF-kill in the boot messages.

---

### Post by snafu006 on 2011-03-29
Hey i had the samething happen go to Synaptic Package manager and type B43 (b43 driver LPPHY version) and install that.

---

### Post by foetus66 on 2011-03-29
Hm, I tried that... First uninstalled the b43legacy from the SPM and then I get this error when trying to install the b43-lpphy package:
[img]http://peebomb.com/wtvr/lpphyerror.png[/img]

Also in the description for the lp-phy package it says it is for the BCM4312 chipset but I have the BCM4303 chipset.  Did you get the lp-phy driver working on a 4303 chipset?  Thanks for your help.

---

### Post by benn1e on 2011-03-30
I have exactly the same problem. Except my laptop is an old Siemens Amilo 1840W. It does have a switch but once you switch it off it cannot be switched on again.
The output from all of the above commands is the same.
rfkill list shows "hard blocked"
I've been up and down the forums but no joy. I have even blacklisted b43 and ssb in modprobe.d
Anybody willing to solve this?

thanks

---

### Post by foetus66 on 2011-03-30
Well I tried ndiswrapper with little success -- I would get an error saying that it could not verify the hardware was present, however, when the driver was loaded it would say the hardware was in fact present.  So, could be related to the same problem I had with b43legacy.  I tried moving the card to another PCI slot just for the hell of it and retried the whole b43 process again as well as ndiswrapper -- all the same problems.

Then I found an Airlink101 wifi card in my garage (Ralink RT61 chipset) and tried installing that in place of the WMP11.  I started up the computer and didn't have to do anything at all, my network SSID was listed and all I had to do was put in my access code and I was off.

---

### Post by benn1e on 2011-04-13
Just to let you and perhaps others who have been scratching their heads with b43legacy on amilo laptops.
My cmos battery was completely finished, every time the laptop was switched off, it required a bios setup for date and time.
So i removed it and installed a new one.
Set the bios to defaults, set the date and time, and on the first boot, bingo, wireless lan was up. Logged into the router which was expecting wap2 and the router immediately dropped the connection.
That was the last i saw of it.
It works perfectly well under XP.
So my assumption is that somehow, b43legacy driver and rfkill do not properly report the state of the rfkill button or the card itself to the kernel.

---

