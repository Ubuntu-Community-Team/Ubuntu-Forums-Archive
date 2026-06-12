---
title: "Unable to use AMD drivers after 9.10 to 1.04 upgrade"
date: 2010-04-30
forum: Multimedia Software
---

### Post by fusa on 2010-04-30
I upgraded from 9.10 to 10.4.  Prior to the upgrade I disabled the AMD drivers.  I am now unable to activate the AMD drivers in 10.4.  The log files is below:

```

2010-04-30 02:07:02,566 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cf6a6c>
2010-04-30 02:07:02,580 DEBUG: reading modalias file /lib/modules/2.6.31-21-generic/modules.alias
2010-04-30 02:07:02,849 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-04-30 02:07:02,863 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-04-30 02:07:02,939 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-04-30 02:07:02,947 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2010-04-30 02:07:02,964 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-177
2010-04-30 02:07:02,995 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2010-04-30 02:07:03,004 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2010-04-30 02:07:03,012 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2010-04-30 02:07:03,694 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2010-04-30 02:07:03,799 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2010-04-30 02:07:03,799 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2010-04-30 02:07:03,821 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2010-04-30 02:07:03,822 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2010-04-30 02:07:03,822 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2010-04-30 02:07:03,851 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2010-04-30 02:07:03,921 DEBUG: Software modem not available
2010-04-30 02:07:03,922 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2010-04-30 02:07:03,959 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-04-30 02:07:03,969 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2010-04-30 02:07:03,982 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2010-04-30 02:07:03,982 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2010-04-30 02:07:03,992 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2010-04-30 02:07:03,994 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2010-04-30 02:07:04,010 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-04-30 02:07:04,018 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2010-04-30 02:07:04,021 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2010-04-30 02:07:04,038 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-04-30 02:07:04,039 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2010-04-30 02:07:04,059 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2010-04-30 02:07:04,061 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2010-04-30 02:07:04,082 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-04-30 02:07:04,082 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2010-04-30 02:07:04,142 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2010-04-30 02:07:04,143 DEBUG: Firmware for DVB cards not available
2010-04-30 02:07:04,143 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2010-04-30 02:07:04,150 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2010-04-30 02:07:04,152 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2010-04-30 02:07:04,152 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2010-04-30 02:07:04,152 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2010-04-30 02:07:04,173 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-04-30 02:07:04,195 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2010-04-30 02:07:04,196 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2010-04-30 02:07:04,196 DEBUG: all custom handlers loaded
2010-04-30 02:07:04,196 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cf6a6c> about HardwareID('modalias', 'pci:v00001002d00009495sv00001682sd00000028bc03sc00i00')
2010-04-30 02:07:04,852 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-04-30 02:07:06,810 DEBUG: XorgDriverHandler isDriverEnabled (fglrx, fglrx, fglrx): considering xorg driver disabled
2010-04-30 02:07:04,854 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2010-04-30 02:07:07,325 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 02:07:07,325 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cf6a6c> about HardwareID('modalias', 'acpi:PNP0100:')
2010-04-30 02:07:07,325 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cf6a6c> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-04-30 02:07:07,326 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cf6a6c> about HardwareID('modalias', 'pci:v00001002d0000AA38sv00001682sd0000AA38bc04sc03i00')
2010-04-30 02:07:07,334 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 02:07:07,334 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 02:07:07,334 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cf6a6c> about HardwareID('modalias', 'platform:eisa')
2010-04-30 02:07:07,335 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cf6a6c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-04-30 02:07:07,386 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cf6a6c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-04-30 02:07:07,393 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 02:07:07,393 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cf6a6c> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-04-30 02:07:07,393 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cf6a6c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-04-30 02:07:07,394 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cf6a6c> about HardwareID('modalias', 'platform:w83627hf')
2010-04-30 02:07:07,394 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cf6a6c> about HardwareID('modalias', 'pci:v00001039d00000003sv00000000sd00000000bc06sc04i00')
2010-04-30 02:07:07,432 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'shpchp', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 02:07:07,432 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cf6a6c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-04-30 02:07:07,433 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cf6a6c> about HardwareID('modalias', 'pci:v00001039d00007002sv00001043sd0000810Ebc0Csc03i20')
2010-04-30 02:07:07,434 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cf6a6c> about HardwareID('modalias', 'acpi:PNP0200:')
2010-04-30 02:07:07,435 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cf6a6c> about HardwareID('modalias', 'pci:v00001039d00000655sv00001043sd000080AAbc06sc00i00')
2010-04-30 02:07:07,436 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sis_agp', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 02:07:07,436 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cf6a6c> about HardwareID('modalias', 'acpi:PNP0700:')
2010-04-30 02:07:07,436 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cf6a6c> about HardwareID('modalias', 'pci:v00001039d00000900sv00001043sd000080A7bc02sc00i00')
2010-04-30 02:07:07,437 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sis900', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 02:07:07,438 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cf6a6c> about HardwareID('modalias', 'acpi:PNP0800:')
2010-04-30 02:07:07,438 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cf6a6c> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-04-30 02:07:07,438 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cf6a6c> about HardwareID('modalias', 'usb:v046Dp08B2d0000dc00dsc00dp00ic01isc01ip00')
2010-04-30 02:07:07,506 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pwc', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 02:07:07,506 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 02:07:07,506 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cf6a6c> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2010-04-30 02:07:07,525 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 02:07:07,526 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cf6a6c> about HardwareID('modalias', 'input:b0003v046DpC041e0111-e0,1,2,4,k110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,r0,1,6,8,am4,lsfw')
2010-04-30 02:07:07,526 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 02:07:07,526 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cf6a6c> about HardwareID('modalias', 'usb:v051Dp0002d0101dc00dsc00dp00ic03isc00ip00')
2010-04-30 02:07:07,528 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 02:07:07,529 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cf6a6c> about HardwareID('modalias', 'input:b0003v046DpC315e0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2010-04-30 02:07:07,529 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 02:07:07,530 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cf6a6c> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr1006.002:bd06/15/2006:svnToBeFilledByO.E.M.:pnToBeFilledByO.E.M.:pvrToBeFilledByO.E.M.:rvnASUSTeKComputerINC.:rnP4S800D-X:rvrRev1.xx:cvnChassisManufacture:ct3:cvrChassisVersion:')
2010-04-30 02:07:07,564 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cf6a6c> about HardwareID('modalias', 'usb:v046DpC041d4602dc00dsc00dp00ic03isc01ip02')
2010-04-30 02:07:07,566 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 02:07:07,566 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cf6a6c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-04-30 02:07:07,566 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cf6a6c> about HardwareID('modalias', 'usb:v046DpC315d2800dc00dsc00dp00ic03isc01ip01')
2010-04-30 02:07:07,568 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 02:07:07,568 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cf6a6c> about HardwareID('modalias', 'usb:v0A12p0001d1915dcE0dsc01dp01icE0isc01ip01')
2010-04-30 02:07:07,569 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 02:07:07,570 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cf6a6c> about HardwareID('modalias', 'usb:v046DpC041d4602dc00dsc00dp00ic03isc00ip00')
2010-04-30 02:07:07,573 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 02:07:07,575 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cf6a6c> about HardwareID('modalias', 'usb:v0A12p0001d1915dcE0dsc01dp01icFEisc01ip00')
2010-04-30 02:07:07,576 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 02:07:07,576 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cf6a6c> about HardwareID('modalias', 'pci:v00001039d00007012sv00001043sd0000810Dbc04sc01i00')
2010-04-30 02:07:07,577 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_intel8x0', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 02:07:07,577 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cf6a6c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-04-30 02:07:07,578 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cf6a6c> about HardwareID('modalias', 'usb:v046Dp08B2d0000dc00dsc00dp00ic01isc02ip00')
2010-04-30 02:07:07,580 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pwc', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 02:07:07,580 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cf6a6c> about HardwareID('modalias', 'pci:v00001039d00000964sv00000000sd00000000bc06sc01i00')
2010-04-30 02:07:07,581 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cf6a6c> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-04-30 02:07:07,582 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 02:07:07,582 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cf6a6c> about HardwareID('modalias', 'acpi:PNP0000:')
2010-04-30 02:07:07,582 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cf6a6c> about HardwareID('modalias', 'usb:v046Dp08B2d0000dc00dsc00dp00icFFisc00ip00')
2010-04-30 02:07:07,584 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pwc', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 02:07:07,584 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cf6a6c> about HardwareID('modalias', 'platform:pcspkr')
2010-04-30 02:07:07,585 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 02:07:07,585 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 02:07:07,585 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cf6a6c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-04-30 02:07:07,586 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 02:07:07,587 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 02:07:07,587 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cf6a6c> about HardwareID('modalias', 'usb:v05E3p0608d0901dc09dsc00dp01ic09isc00ip00')
2010-04-30 02:07:07,593 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cf6a6c> about HardwareID('modalias', 'input:b0003v046Dp08B2e0000-e0,1,kD4,ramlsfw')
2010-04-30 02:07:07,594 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 02:07:07,594 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8cf6a6c> about HardwareID('modalias', 'acpi:PNP0C01:')
2010-04-30 02:07:07,595 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f8294c> about HardwareID('modalias', 'pci:v00001002d00009495sv00001682sd00000028bc03sc00i00')
2010-04-30 02:07:07,595 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f8294c> about HardwareID('modalias', 'acpi:PNP0100:')
2010-04-30 02:07:07,595 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f8294c> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-04-30 02:07:07,596 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f8294c> about HardwareID('modalias', 'pci:v00001002d0000AA38sv00001682sd0000AA38bc04sc03i00')
2010-04-30 02:07:07,596 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f8294c> about HardwareID('modalias', 'platform:eisa')
2010-04-30 02:07:07,596 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f8294c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-04-30 02:07:07,596 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f8294c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-04-30 02:07:07,596 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f8294c> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-04-30 02:07:07,597 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f8294c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-04-30 02:07:07,597 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f8294c> about HardwareID('modalias', 'platform:w83627hf')
2010-04-30 02:07:07,597 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f8294c> about HardwareID('modalias', 'pci:v00001039d00000003sv00000000sd00000000bc06sc04i00')
2010-04-30 02:07:07,597 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f8294c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-04-30 02:07:07,597 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f8294c> about HardwareID('modalias', 'pci:v00001039d00007002sv00001043sd0000810Ebc0Csc03i20')
2010-04-30 02:07:07,598 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f8294c> about HardwareID('modalias', 'acpi:PNP0200:')
2010-04-30 02:07:07,598 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f8294c> about HardwareID('modalias', 'pci:v00001039d00000655sv00001043sd000080AAbc06sc00i00')
2010-04-30 02:07:07,598 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f8294c> about HardwareID('modalias', 'acpi:PNP0700:')
2010-04-30 02:07:07,598 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f8294c> about HardwareID('modalias', 'pci:v00001039d00000900sv00001043sd000080A7bc02sc00i00')
2010-04-30 02:07:07,598 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f8294c> about HardwareID('modalias', 'acpi:PNP0800:')
2010-04-30 02:07:07,599 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f8294c> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-04-30 02:07:07,599 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f8294c> about HardwareID('modalias', 'usb:v046Dp08B2d0000dc00dsc00dp00ic01isc01ip00')
2010-04-30 02:07:07,599 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f8294c> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2010-04-30 02:07:07,600 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f8294c> about HardwareID('modalias', 'input:b0003v046DpC041e0111-e0,1,2,4,k110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,r0,1,6,8,am4,lsfw')
2010-04-30 02:07:07,600 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f8294c> about HardwareID('modalias', 'usb:v051Dp0002d0101dc00dsc00dp00ic03isc00ip00')
2010-04-30 02:07:07,600 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f8294c> about HardwareID('modalias', 'input:b0003v046DpC315e0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2010-04-30 02:07:07,600 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f8294c> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr1006.002:bd06/15/2006:svnToBeFilledByO.E.M.:pnToBeFilledByO.E.M.:pvrToBeFilledByO.E.M.:rvnASUSTeKComputerINC.:rnP4S800D-X:rvrRev1.xx:cvnChassisManufacture:ct3:cvrChassisVersion:')
2010-04-30 02:07:07,600 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f8294c> about HardwareID('modalias', 'usb:v046DpC041d4602dc00dsc00dp00ic03isc01ip02')
2010-04-30 02:07:07,601 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f8294c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-04-30 02:07:07,601 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f8294c> about HardwareID('modalias', 'usb:v046DpC315d2800dc00dsc00dp00ic03isc01ip01')
2010-04-30 02:07:07,601 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f8294c> about HardwareID('modalias', 'usb:v0A12p0001d1915dcE0dsc01dp01icE0isc01ip01')
2010-04-30 02:07:07,601 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f8294c> about HardwareID('modalias', 'usb:v046DpC041d4602dc00dsc00dp00ic03isc00ip00')
2010-04-30 02:07:07,601 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f8294c> about HardwareID('modalias', 'usb:v0A12p0001d1915dcE0dsc01dp01icFEisc01ip00')
2010-04-30 02:07:07,602 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f8294c> about HardwareID('modalias', 'pci:v00001039d00007012sv00001043sd0000810Dbc04sc01i00')
2010-04-30 02:07:07,602 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f8294c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-04-30 02:07:07,602 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f8294c> about HardwareID('modalias', 'usb:v046Dp08B2d0000dc00dsc00dp00ic01isc02ip00')
2010-04-30 02:07:07,602 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f8294c> about HardwareID('modalias', 'pci:v00001039d00000964sv00000000sd00000000bc06sc01i00')
2010-04-30 02:07:07,602 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f8294c> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-04-30 02:07:07,603 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f8294c> about HardwareID('modalias', 'acpi:PNP0000:')
2010-04-30 02:07:07,603 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f8294c> about HardwareID('modalias', 'usb:v046Dp08B2d0000dc00dsc00dp00icFFisc00ip00')
2010-04-30 02:07:07,603 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f8294c> about HardwareID('modalias', 'platform:pcspkr')
2010-04-30 02:07:07,603 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f8294c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-04-30 02:07:07,604 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f8294c> about HardwareID('modalias', 'usb:v05E3p0608d0901dc09dsc00dp01ic09isc00ip00')
2010-04-30 02:07:07,604 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f8294c> about HardwareID('modalias', 'input:b0003v046Dp08B2e0000-e0,1,kD4,ramlsfw')
2010-04-30 02:07:07,604 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8f8294c> about HardwareID('modalias', 'acpi:PNP0C01:')
2010-04-30 02:07:08,069 DEBUG: XorgDriverHandler isDriverEnabled (fglrx, fglrx, fglrx): considering xorg driver disabled
2010-04-30 02:07:08,783 DEBUG: XorgDriverHandler isDriverEnabled (fglrx, fglrx, fglrx): considering xorg driver disabled
2010-04-30 02:07:09,211 DEBUG: XorgDriverHandler isDriverEnabled (fglrx, fglrx, fglrx): considering xorg driver disabled
2010-04-30 02:08:45,784 DEBUG: XorgDriverHandler isDriverEnabled (fglrx, fglrx, fglrx): considering xorg driver disabled
2010-04-30 02:08:52,000 DEBUG: Installing package: linux-headers-2.6.31-21-generic
2010-04-30 02:08:52,747 DEBUG: Package linux-headers-2.6.31-21-generic does not exist, aborting
2010-04-30 02:08:53,829 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-04-30 02:08:53,831 WARNING: /sys/module/fglrx/drivers does not exist, cannot rebind fglrx driver
2010-04-30 02:08:53,831 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2010-04-30 02:09:09,369 DEBUG: XorgDriverHandler isDriverEnabled (fglrx, fglrx, fglrx): considering xorg driver disabled
2010-04-30 02:09:09,704 DEBUG: XorgDriverHandler isDriverEnabled (fglrx, fglrx, fglrx): considering xorg driver disabled


```

---

### Post by fusa on 2010-04-30
> sudo nano /etc/default/grub.
Add radeon.modeset=1 to the end of the line GRUB_CMDLINE_LINUX_DEFAULT=.
Then sudo update-grub

Corrected this issue

---

