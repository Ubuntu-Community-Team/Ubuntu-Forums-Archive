---
title: "No Wireless in 10.4, Can't Install Proprietary Drivers"
date: 2010-04-30
forum: Networking &amp; Wireless
---

### Post by Topher88 on 2010-04-30
Just upgraded to Lucid from Karmic.  First thing I notice after restart is that I have no wireless.  No big deal, I probably just need to re-install the proprietary drivers.  I go to do this, and it gives me an error message, saying that the installation has failed.  This has never happened before, and didn't happen when I upgraded from Jaunty to Karmic.  I have an HP dv6 1230us and a Broadcom STA card.

Any ideas what I need to do?  I really need the internet to be working, and didn't anticipate that an upgrade, of all things, would screw it up...

---

### Post by Topher88 on 2010-04-30
Here's a copy of the log it refers me to after it says that the installation failed.  Hopefully this will prove helpful...

```
2010-04-30 13:24:19,175 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x1687248>
2010-04-30 13:24:19,178 DEBUG: reading modalias file /lib/modules/2.6.31-10-rt/modules.alias
2010-04-30 13:24:19,320 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-04-30 13:24:19,366 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-04-30 13:24:19,415 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-04-30 13:24:19,458 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2010-04-30 13:24:19,497 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2010-04-30 13:24:19,537 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2010-04-30 13:24:19,543 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2010-04-30 13:24:19,777 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2010-04-30 13:24:19,856 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2010-04-30 13:24:19,953 DEBUG: Software modem not available
2010-04-30 13:24:19,953 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2010-04-30 13:24:20,134 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-04-30 13:24:20,135 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2010-04-30 13:24:20,146 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2010-04-30 13:24:20,147 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2010-04-30 13:24:20,282 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2010-04-30 13:24:20,282 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2010-04-30 13:24:20,346 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2010-04-30 13:24:20,346 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2010-04-30 13:24:20,347 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2010-04-30 13:24:20,383 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-04-30 13:24:20,394 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2010-04-30 13:24:20,395 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2010-04-30 13:24:20,395 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2010-04-30 13:24:20,458 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2010-04-30 13:24:20,459 DEBUG: Firmware for DVB cards not available
2010-04-30 13:24:20,459 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2010-04-30 13:24:20,483 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2010-04-30 13:24:20,484 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2010-04-30 13:24:20,495 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-04-30 13:24:20,501 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2010-04-30 13:24:20,502 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2010-04-30 13:24:20,513 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-04-30 13:24:20,514 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2010-04-30 13:24:20,548 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2010-04-30 13:24:20,549 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2010-04-30 13:24:20,560 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-04-30 13:24:20,561 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2010-04-30 13:24:20,569 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2010-04-30 13:24:20,569 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2010-04-30 13:24:20,569 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2010-04-30 13:24:20,570 DEBUG: all custom handlers loaded
2010-04-30 13:24:20,570 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1687248> about HardwareID('modalias', 'acpi:INT0800:')
2010-04-30 13:24:20,570 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1687248> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-04-30 13:24:20,793 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:24:20,793 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1687248> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-04-30 13:24:20,793 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1687248> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2010-04-30 13:24:20,794 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1687248> about HardwareID('modalias', 'pci:v00008086d00002A43sv0000103Csd00003627bc03sc80i00')
2010-04-30 13:24:20,993 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1687248> about HardwareID('modalias', 'platform:pcspkr')
2010-04-30 13:24:20,993 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:24:20,993 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:24:20,993 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1687248> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-04-30 13:24:21,016 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1687248> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-04-30 13:24:21,016 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:24:21,016 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1687248> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-04-30 13:24:21,017 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1687248> about HardwareID('modalias', 'acpi:PNP0100:')
2010-04-30 13:24:21,017 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1687248> about HardwareID('modalias', 'platform:lis3lv02d')
2010-04-30 13:24:21,017 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1687248> about HardwareID('modalias', 'input:b0003v5986p0180e0003-e0,1,kD4,ramlsfw')
2010-04-30 13:24:21,017 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:24:21,017 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1687248> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-04-30 13:24:21,018 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1687248> about HardwareID('modalias', 'pci:v00008086d00002A40sv0000103Csd00003627bc06sc00i00')
2010-04-30 13:24:21,020 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_agp', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:24:21,020 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1687248> about HardwareID('modalias', 'pci:v000014E4d0000432Bsv0000103Csd00001509bc02sc80i00')
2010-04-30 13:24:21,064 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ssb', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:24:21,068 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-04-30 13:24:21,069 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-04-30 13:24:21,068 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2010-04-30 13:24:21,069 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1687248> about HardwareID('modalias', 'acpi:PNP0103:')
2010-04-30 13:24:21,069 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1687248> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-04-30 13:24:21,069 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1687248> about HardwareID('modalias', 'pci:v00008086d00002A42sv0000103Csd00003627bc03sc00i00')
2010-04-30 13:24:21,072 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:24:21,072 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1687248> about HardwareID('modalias', 'pci:v00008086d0000293Esv0000103Csd00003627bc04sc03i00')
2010-04-30 13:24:21,075 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:24:21,075 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1687248> about HardwareID('modalias', 'acpi:PNP0000:')
2010-04-30 13:24:21,075 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1687248> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-04-30 13:24:21,077 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1687248> about HardwareID('modalias', 'pci:v00008086d00002936sv0000103Csd00003627bc0Csc03i00')
2010-04-30 13:24:21,080 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1687248> about HardwareID('modalias', 'pci:v00008086d00002930sv0000103Csd00003627bc0Csc05i00')
2010-04-30 13:24:21,082 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:24:21,082 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1687248> about HardwareID('modalias', 'usb:v5986p0180d0003dcEFdsc02dp01ic0Eisc01ip00')
2010-04-30 13:24:21,083 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:24:21,083 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1687248> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-04-30 13:24:21,083 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:24:21,083 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1687248> about HardwareID('modalias', 'input:b0001v111Dp7603e0001-e0,12,kramls1,2,fw')
2010-04-30 13:24:21,083 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:24:21,083 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1687248> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,112,145,14A,ra0,1,18,1C,mlsfw')
2010-04-30 13:24:21,084 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:24:21,084 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:24:21,084 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:24:21,084 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1687248> about HardwareID('modalias', 'acpi:SYN1E04:SYN1E00:SYN0002:PNP0F13:')
2010-04-30 13:24:21,084 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1687248> about HardwareID('modalias', 'pci:v00008086d00002935sv0000103Csd00003627bc0Csc03i00')
2010-04-30 13:24:21,086 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1687248> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-04-30 13:24:21,087 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:24:21,087 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1687248> about HardwareID('modalias', 'acpi:PNP0C32:')
2010-04-30 13:24:21,087 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1687248> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvrF.33:bd08/31/2009:svnHewlett-Packard:pnHPPaviliondv6NotebookPC:pvrRev1:rvnQuanta:rn3627:rvr18.42:cvnQuanta:ct10:cvrN/A:')
2010-04-30 13:24:21,101 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1687248> about HardwareID('modalias', 'pci:v00008086d00002919sv0000103Csd00003627bc06sc01i00')
2010-04-30 13:24:21,103 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:24:21,103 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1687248> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-04-30 13:24:21,103 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1687248> about HardwareID('modalias', 'pci:v00008086d00002939sv0000103Csd00003627bc0Csc03i00')
2010-04-30 13:24:21,106 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1687248> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-04-30 13:24:21,106 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:24:21,106 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1687248> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-04-30 13:24:21,106 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1687248> about HardwareID('modalias', 'usb:v0BDAp0158d5887dc00dsc00dp00ic08isc06ip50')
2010-04-30 13:24:21,111 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:24:21,111 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1687248> about HardwareID('modalias', 'pci:v00008086d00002932sv0000103Csd00003627bc11sc80i00')
2010-04-30 13:24:21,113 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1687248> about HardwareID('modalias', 'pci:v00008086d00002938sv0000103Csd00003627bc0Csc03i00')
2010-04-30 13:24:21,116 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1687248> about HardwareID('modalias', 'pci:v00008086d00002929sv0000103Csd00003627bc01sc06i01')
2010-04-30 13:24:21,118 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1687248> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,3,kra0,1,2,mlsfw')
2010-04-30 13:24:21,118 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:24:21,118 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:24:21,119 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1687248> about HardwareID('modalias', 'acpi:ENE0100:')
2010-04-30 13:24:21,119 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1687248> about HardwareID('modalias', 'pci:v00008086d00002937sv0000103Csd00003627bc0Csc03i00')
2010-04-30 13:24:21,121 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1687248> about HardwareID('modalias', 'acpi:PNP0303:')
2010-04-30 13:24:21,121 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1687248> about HardwareID('modalias', 'usb:v5986p0180d0003dcEFdsc02dp01ic0Eisc02ip00')
2010-04-30 13:24:21,122 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1687248> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2010-04-30 13:24:21,122 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:24:21,122 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1687248> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-04-30 13:24:21,122 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1687248> about HardwareID('modalias', 'usb:v0A12p0001d0134dcE0dsc01dp01icE0isc01ip01')
2010-04-30 13:24:21,123 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:24:21,123 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1687248> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2010-04-30 13:24:21,123 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:24:21,123 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1687248> about HardwareID('modalias', 'pci:v00008086d0000293Asv0000103Csd00003627bc0Csc03i20')
2010-04-30 13:24:21,125 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1687248> about HardwareID('modalias', 'pci:v00008086d0000293Csv0000103Csd00003627bc0Csc03i20')
2010-04-30 13:24:21,128 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1687248> about HardwareID('modalias', 'pci:v00008086d00002934sv0000103Csd00003627bc0Csc03i00')
2010-04-30 13:24:21,130 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1687248> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-04-30 13:24:21,140 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:24:21,140 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:24:21,140 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1687248> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-04-30 13:24:21,140 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:24:21,140 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1687248> about HardwareID('modalias', 'pci:v000010ECd00008136sv0000103Csd00003627bc02sc00i00')
2010-04-30 13:24:21,145 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:24:21,145 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1687248> about HardwareID('modalias', 'acpi:PNP0200:')
2010-04-30 13:24:21,146 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b18680> about HardwareID('modalias', 'acpi:INT0800:')
2010-04-30 13:24:21,146 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b18680> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-04-30 13:24:21,146 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b18680> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-04-30 13:24:21,146 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b18680> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2010-04-30 13:24:21,146 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b18680> about HardwareID('modalias', 'pci:v00008086d00002A43sv0000103Csd00003627bc03sc80i00')
2010-04-30 13:24:21,146 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b18680> about HardwareID('modalias', 'platform:pcspkr')
2010-04-30 13:24:21,146 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b18680> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-04-30 13:24:21,146 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b18680> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-04-30 13:24:21,146 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b18680> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-04-30 13:24:21,147 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b18680> about HardwareID('modalias', 'acpi:PNP0100:')
2010-04-30 13:24:21,147 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b18680> about HardwareID('modalias', 'platform:lis3lv02d')
2010-04-30 13:24:21,147 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b18680> about HardwareID('modalias', 'input:b0003v5986p0180e0003-e0,1,kD4,ramlsfw')
2010-04-30 13:24:21,147 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b18680> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-04-30 13:24:21,147 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b18680> about HardwareID('modalias', 'pci:v00008086d00002A40sv0000103Csd00003627bc06sc00i00')
2010-04-30 13:24:21,147 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b18680> about HardwareID('modalias', 'pci:v000014E4d0000432Bsv0000103Csd00001509bc02sc80i00')
2010-04-30 13:24:21,147 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b18680> about HardwareID('modalias', 'acpi:PNP0103:')
2010-04-30 13:24:21,147 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b18680> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-04-30 13:24:21,147 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b18680> about HardwareID('modalias', 'pci:v00008086d00002A42sv0000103Csd00003627bc03sc00i00')
2010-04-30 13:24:21,147 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b18680> about HardwareID('modalias', 'pci:v00008086d0000293Esv0000103Csd00003627bc04sc03i00')
2010-04-30 13:24:21,148 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b18680> about HardwareID('modalias', 'acpi:PNP0000:')
2010-04-30 13:24:21,148 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b18680> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-04-30 13:24:21,148 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b18680> about HardwareID('modalias', 'pci:v00008086d00002936sv0000103Csd00003627bc0Csc03i00')
2010-04-30 13:24:21,148 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b18680> about HardwareID('modalias', 'pci:v00008086d00002930sv0000103Csd00003627bc0Csc05i00')
2010-04-30 13:24:21,148 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b18680> about HardwareID('modalias', 'usb:v5986p0180d0003dcEFdsc02dp01ic0Eisc01ip00')
2010-04-30 13:24:21,148 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b18680> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-04-30 13:24:21,148 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b18680> about HardwareID('modalias', 'input:b0001v111Dp7603e0001-e0,12,kramls1,2,fw')
2010-04-30 13:24:21,148 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b18680> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,112,145,14A,ra0,1,18,1C,mlsfw')
2010-04-30 13:24:21,148 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b18680> about HardwareID('modalias', 'acpi:SYN1E04:SYN1E00:SYN0002:PNP0F13:')
2010-04-30 13:24:21,149 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b18680> about HardwareID('modalias', 'pci:v00008086d00002935sv0000103Csd00003627bc0Csc03i00')
2010-04-30 13:24:21,149 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b18680> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-04-30 13:24:21,149 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b18680> about HardwareID('modalias', 'acpi:PNP0C32:')
2010-04-30 13:24:21,149 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b18680> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvrF.33:bd08/31/2009:svnHewlett-Packard:pnHPPaviliondv6NotebookPC:pvrRev1:rvnQuanta:rn3627:rvr18.42:cvnQuanta:ct10:cvrN/A:')
2010-04-30 13:24:21,149 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b18680> about HardwareID('modalias', 'pci:v00008086d00002919sv0000103Csd00003627bc06sc01i00')
2010-04-30 13:24:21,149 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b18680> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-04-30 13:24:21,149 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b18680> about HardwareID('modalias', 'pci:v00008086d00002939sv0000103Csd00003627bc0Csc03i00')
2010-04-30 13:24:21,149 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b18680> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-04-30 13:24:21,149 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b18680> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-04-30 13:24:21,149 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b18680> about HardwareID('modalias', 'usb:v0BDAp0158d5887dc00dsc00dp00ic08isc06ip50')
2010-04-30 13:24:21,150 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b18680> about HardwareID('modalias', 'pci:v00008086d00002932sv0000103Csd00003627bc11sc80i00')
2010-04-30 13:24:21,150 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b18680> about HardwareID('modalias', 'pci:v00008086d00002938sv0000103Csd00003627bc0Csc03i00')
2010-04-30 13:24:21,150 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b18680> about HardwareID('modalias', 'pci:v00008086d00002929sv0000103Csd00003627bc01sc06i01')
2010-04-30 13:24:21,150 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b18680> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,3,kra0,1,2,mlsfw')
2010-04-30 13:24:21,150 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b18680> about HardwareID('modalias', 'acpi:ENE0100:')
2010-04-30 13:24:21,150 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b18680> about HardwareID('modalias', 'pci:v00008086d00002937sv0000103Csd00003627bc0Csc03i00')
2010-04-30 13:24:21,150 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b18680> about HardwareID('modalias', 'acpi:PNP0303:')
2010-04-30 13:24:21,150 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b18680> about HardwareID('modalias', 'usb:v5986p0180d0003dcEFdsc02dp01ic0Eisc02ip00')
2010-04-30 13:24:21,150 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b18680> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2010-04-30 13:24:21,150 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b18680> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-04-30 13:24:21,151 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b18680> about HardwareID('modalias', 'usb:v0A12p0001d0134dcE0dsc01dp01icE0isc01ip01')
2010-04-30 13:24:21,151 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b18680> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2010-04-30 13:24:21,151 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b18680> about HardwareID('modalias', 'pci:v00008086d0000293Asv0000103Csd00003627bc0Csc03i20')
2010-04-30 13:24:21,151 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b18680> about HardwareID('modalias', 'pci:v00008086d0000293Csv0000103Csd00003627bc0Csc03i20')
2010-04-30 13:24:21,151 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b18680> about HardwareID('modalias', 'pci:v00008086d00002934sv0000103Csd00003627bc0Csc03i00')
2010-04-30 13:24:21,151 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b18680> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-04-30 13:24:21,151 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b18680> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-04-30 13:24:21,151 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b18680> about HardwareID('modalias', 'pci:v000010ECd00008136sv0000103Csd00003627bc02sc00i00')
2010-04-30 13:24:21,151 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1b18680> about HardwareID('modalias', 'acpi:PNP0200:')
2010-04-30 13:24:21,183 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-04-30 13:24:21,357 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-04-30 13:24:21,392 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-04-30 13:24:35,331 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-04-30 13:24:38,757 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-04-30 13:24:38,758 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2010-04-30 13:24:38,804 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-04-30 13:24:43,223 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-04-30 13:24:43,251 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-04-30 13:24:43,285 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-04-30 13:24:48,912 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-04-30 13:24:53,821 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-04-30 13:24:54,050 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-04-30 13:24:54,051 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2010-04-30 13:24:54,092 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-04-30 13:24:56,959 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-04-30 13:24:56,979 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-04-30 13:24:57,020 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-04-30 13:25:08,620 DEBUG: Shutting down
2010-04-30 13:29:27,798 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x2fa2248>
2010-04-30 13:29:27,800 DEBUG: reading modalias file /lib/modules/2.6.31-10-rt/modules.alias
2010-04-30 13:29:27,928 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-04-30 13:29:27,929 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-04-30 13:29:27,957 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-04-30 13:29:27,958 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2010-04-30 13:29:27,962 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2010-04-30 13:29:27,963 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2010-04-30 13:29:27,967 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2010-04-30 13:29:28,193 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2010-04-30 13:29:28,202 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2010-04-30 13:29:28,212 DEBUG: Software modem not available
2010-04-30 13:29:28,212 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2010-04-30 13:29:28,217 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-04-30 13:29:28,218 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2010-04-30 13:29:28,225 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2010-04-30 13:29:28,225 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2010-04-30 13:29:28,238 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2010-04-30 13:29:28,239 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2010-04-30 13:29:28,243 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2010-04-30 13:29:28,244 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2010-04-30 13:29:28,244 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2010-04-30 13:29:28,250 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-04-30 13:29:28,259 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2010-04-30 13:29:28,260 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2010-04-30 13:29:28,260 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2010-04-30 13:29:28,274 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2010-04-30 13:29:28,275 DEBUG: Firmware for DVB cards not available
2010-04-30 13:29:28,275 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2010-04-30 13:29:28,283 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2010-04-30 13:29:28,284 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2010-04-30 13:29:28,292 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-04-30 13:29:28,296 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2010-04-30 13:29:28,297 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2010-04-30 13:29:28,304 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-04-30 13:29:28,304 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2010-04-30 13:29:28,308 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2010-04-30 13:29:28,309 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2010-04-30 13:29:28,316 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-04-30 13:29:28,317 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2010-04-30 13:29:28,321 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2010-04-30 13:29:28,322 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2010-04-30 13:29:28,322 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2010-04-30 13:29:28,322 DEBUG: all custom handlers loaded
2010-04-30 13:29:28,322 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2fa2248> about HardwareID('modalias', 'acpi:INT0800:')
2010-04-30 13:29:28,323 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2fa2248> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-04-30 13:29:28,433 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:29:28,434 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2fa2248> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-04-30 13:29:28,434 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2fa2248> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2010-04-30 13:29:28,434 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2fa2248> about HardwareID('modalias', 'pci:v00008086d00002A43sv0000103Csd00003627bc03sc80i00')
2010-04-30 13:29:28,633 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2fa2248> about HardwareID('modalias', 'platform:pcspkr')
2010-04-30 13:29:28,634 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:29:28,634 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:29:28,634 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2fa2248> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-04-30 13:29:28,657 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2fa2248> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-04-30 13:29:28,657 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:29:28,657 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2fa2248> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-04-30 13:29:28,657 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2fa2248> about HardwareID('modalias', 'acpi:PNP0100:')
2010-04-30 13:29:28,658 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2fa2248> about HardwareID('modalias', 'platform:lis3lv02d')
2010-04-30 13:29:28,658 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2fa2248> about HardwareID('modalias', 'input:b0003v5986p0180e0003-e0,1,kD4,ramlsfw')
2010-04-30 13:29:28,658 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:29:28,658 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2fa2248> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-04-30 13:29:28,658 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2fa2248> about HardwareID('modalias', 'pci:v00008086d00002A40sv0000103Csd00003627bc06sc00i00')
2010-04-30 13:29:28,661 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_agp', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:29:28,661 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2fa2248> about HardwareID('modalias', 'pci:v000014E4d0000432Bsv0000103Csd00001509bc02sc80i00')
2010-04-30 13:29:28,705 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ssb', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:29:28,709 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-04-30 13:29:28,710 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-04-30 13:29:28,709 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2010-04-30 13:29:28,710 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2fa2248> about HardwareID('modalias', 'acpi:PNP0103:')
2010-04-30 13:29:28,710 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2fa2248> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-04-30 13:29:28,710 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2fa2248> about HardwareID('modalias', 'pci:v00008086d00002A42sv0000103Csd00003627bc03sc00i00')
2010-04-30 13:29:28,713 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:29:28,713 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2fa2248> about HardwareID('modalias', 'pci:v00008086d0000293Esv0000103Csd00003627bc04sc03i00')
2010-04-30 13:29:28,716 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:29:28,716 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2fa2248> about HardwareID('modalias', 'acpi:PNP0000:')
2010-04-30 13:29:28,716 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2fa2248> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-04-30 13:29:28,718 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2fa2248> about HardwareID('modalias', 'pci:v00008086d00002936sv0000103Csd00003627bc0Csc03i00')
2010-04-30 13:29:28,721 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2fa2248> about HardwareID('modalias', 'pci:v00008086d00002930sv0000103Csd00003627bc0Csc05i00')
2010-04-30 13:29:28,723 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:29:28,723 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2fa2248> about HardwareID('modalias', 'usb:v5986p0180d0003dcEFdsc02dp01ic0Eisc01ip00')
2010-04-30 13:29:28,724 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:29:28,724 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2fa2248> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-04-30 13:29:28,724 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:29:28,724 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2fa2248> about HardwareID('modalias', 'input:b0001v111Dp7603e0001-e0,12,kramls1,2,fw')
2010-04-30 13:29:28,725 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:29:28,725 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2fa2248> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,112,145,14A,ra0,1,18,1C,mlsfw')
2010-04-30 13:29:28,725 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:29:28,725 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:29:28,725 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:29:28,725 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2fa2248> about HardwareID('modalias', 'acpi:SYN1E04:SYN1E00:SYN0002:PNP0F13:')
2010-04-30 13:29:28,725 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2fa2248> about HardwareID('modalias', 'pci:v00008086d00002935sv0000103Csd00003627bc0Csc03i00')
2010-04-30 13:29:28,728 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2fa2248> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-04-30 13:29:28,728 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:29:28,728 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2fa2248> about HardwareID('modalias', 'acpi:PNP0C32:')
2010-04-30 13:29:28,728 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2fa2248> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvrF.33:bd08/31/2009:svnHewlett-Packard:pnHPPaviliondv6NotebookPC:pvrRev1:rvnQuanta:rn3627:rvr18.42:cvnQuanta:ct10:cvrN/A:')
2010-04-30 13:29:28,742 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2fa2248> about HardwareID('modalias', 'pci:v00008086d00002919sv0000103Csd00003627bc06sc01i00')
2010-04-30 13:29:28,744 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:29:28,745 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2fa2248> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-04-30 13:29:28,745 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2fa2248> about HardwareID('modalias', 'pci:v00008086d00002939sv0000103Csd00003627bc0Csc03i00')
2010-04-30 13:29:28,747 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2fa2248> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-04-30 13:29:28,747 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:29:28,747 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2fa2248> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-04-30 13:29:28,748 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2fa2248> about HardwareID('modalias', 'usb:v0BDAp0158d5887dc00dsc00dp00ic08isc06ip50')
2010-04-30 13:29:28,752 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:29:28,752 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2fa2248> about HardwareID('modalias', 'pci:v00008086d00002932sv0000103Csd00003627bc11sc80i00')
2010-04-30 13:29:28,755 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2fa2248> about HardwareID('modalias', 'pci:v00008086d00002938sv0000103Csd00003627bc0Csc03i00')
2010-04-30 13:29:28,757 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2fa2248> about HardwareID('modalias', 'pci:v00008086d00002929sv0000103Csd00003627bc01sc06i01')
2010-04-30 13:29:28,760 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2fa2248> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,3,kra0,1,2,mlsfw')
2010-04-30 13:29:28,760 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:29:28,760 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:29:28,760 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2fa2248> about HardwareID('modalias', 'acpi:ENE0100:')
2010-04-30 13:29:28,760 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2fa2248> about HardwareID('modalias', 'pci:v00008086d00002937sv0000103Csd00003627bc0Csc03i00')
2010-04-30 13:29:28,763 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2fa2248> about HardwareID('modalias', 'acpi:PNP0303:')
2010-04-30 13:29:28,763 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2fa2248> about HardwareID('modalias', 'usb:v5986p0180d0003dcEFdsc02dp01ic0Eisc02ip00')
2010-04-30 13:29:28,763 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2fa2248> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2010-04-30 13:29:28,763 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:29:28,763 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2fa2248> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-04-30 13:29:28,764 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2fa2248> about HardwareID('modalias', 'usb:v0A12p0001d0134dcE0dsc01dp01icE0isc01ip01')
2010-04-30 13:29:28,764 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:29:28,764 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2fa2248> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2010-04-30 13:29:28,764 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:29:28,764 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2fa2248> about HardwareID('modalias', 'pci:v00008086d0000293Asv0000103Csd00003627bc0Csc03i20')
2010-04-30 13:29:28,767 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2fa2248> about HardwareID('modalias', 'pci:v00008086d0000293Csv0000103Csd00003627bc0Csc03i20')
2010-04-30 13:29:28,769 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2fa2248> about HardwareID('modalias', 'pci:v00008086d00002934sv0000103Csd00003627bc0Csc03i00')
2010-04-30 13:29:28,772 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2fa2248> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-04-30 13:29:28,781 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:29:28,781 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:29:28,781 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2fa2248> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-04-30 13:29:28,782 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:29:28,782 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2fa2248> about HardwareID('modalias', 'pci:v000010ECd00008136sv0000103Csd00003627bc02sc00i00')
2010-04-30 13:29:28,786 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:29:28,787 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2fa2248> about HardwareID('modalias', 'acpi:PNP0200:')
2010-04-30 13:29:28,787 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3434680> about HardwareID('modalias', 'acpi:INT0800:')
2010-04-30 13:29:28,787 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3434680> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-04-30 13:29:28,787 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3434680> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-04-30 13:29:28,787 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3434680> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2010-04-30 13:29:28,787 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3434680> about HardwareID('modalias', 'pci:v00008086d00002A43sv0000103Csd00003627bc03sc80i00')
2010-04-30 13:29:28,787 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3434680> about HardwareID('modalias', 'platform:pcspkr')
2010-04-30 13:29:28,787 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3434680> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-04-30 13:29:28,787 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3434680> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-04-30 13:29:28,788 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3434680> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-04-30 13:29:28,788 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3434680> about HardwareID('modalias', 'acpi:PNP0100:')
2010-04-30 13:29:28,788 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3434680> about HardwareID('modalias', 'platform:lis3lv02d')
2010-04-30 13:29:28,788 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3434680> about HardwareID('modalias', 'input:b0003v5986p0180e0003-e0,1,kD4,ramlsfw')
2010-04-30 13:29:28,788 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3434680> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-04-30 13:29:28,788 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3434680> about HardwareID('modalias', 'pci:v00008086d00002A40sv0000103Csd00003627bc06sc00i00')
2010-04-30 13:29:28,788 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3434680> about HardwareID('modalias', 'pci:v000014E4d0000432Bsv0000103Csd00001509bc02sc80i00')
2010-04-30 13:29:28,788 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3434680> about HardwareID('modalias', 'acpi:PNP0103:')
2010-04-30 13:29:28,788 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3434680> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-04-30 13:29:28,788 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3434680> about HardwareID('modalias', 'pci:v00008086d00002A42sv0000103Csd00003627bc03sc00i00')
2010-04-30 13:29:28,789 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3434680> about HardwareID('modalias', 'pci:v00008086d0000293Esv0000103Csd00003627bc04sc03i00')
2010-04-30 13:29:28,789 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3434680> about HardwareID('modalias', 'acpi:PNP0000:')
2010-04-30 13:29:28,789 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3434680> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-04-30 13:29:28,789 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3434680> about HardwareID('modalias', 'pci:v00008086d00002936sv0000103Csd00003627bc0Csc03i00')
2010-04-30 13:29:28,789 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3434680> about HardwareID('modalias', 'pci:v00008086d00002930sv0000103Csd00003627bc0Csc05i00')
2010-04-30 13:29:28,789 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3434680> about HardwareID('modalias', 'usb:v5986p0180d0003dcEFdsc02dp01ic0Eisc01ip00')
2010-04-30 13:29:28,789 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3434680> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-04-30 13:29:28,789 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3434680> about HardwareID('modalias', 'input:b0001v111Dp7603e0001-e0,12,kramls1,2,fw')
2010-04-30 13:29:28,789 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3434680> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,112,145,14A,ra0,1,18,1C,mlsfw')
2010-04-30 13:29:28,790 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3434680> about HardwareID('modalias', 'acpi:SYN1E04:SYN1E00:SYN0002:PNP0F13:')
2010-04-30 13:29:28,790 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3434680> about HardwareID('modalias', 'pci:v00008086d00002935sv0000103Csd00003627bc0Csc03i00')
2010-04-30 13:29:28,790 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3434680> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-04-30 13:29:28,790 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3434680> about HardwareID('modalias', 'acpi:PNP0C32:')
2010-04-30 13:29:28,790 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3434680> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvrF.33:bd08/31/2009:svnHewlett-Packard:pnHPPaviliondv6NotebookPC:pvrRev1:rvnQuanta:rn3627:rvr18.42:cvnQuanta:ct10:cvrN/A:')
2010-04-30 13:29:28,790 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3434680> about HardwareID('modalias', 'pci:v00008086d00002919sv0000103Csd00003627bc06sc01i00')
2010-04-30 13:29:28,790 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3434680> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-04-30 13:29:28,790 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3434680> about HardwareID('modalias', 'pci:v00008086d00002939sv0000103Csd00003627bc0Csc03i00')
2010-04-30 13:29:28,790 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3434680> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-04-30 13:29:28,790 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3434680> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-04-30 13:29:28,791 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3434680> about HardwareID('modalias', 'usb:v0BDAp0158d5887dc00dsc00dp00ic08isc06ip50')
2010-04-30 13:29:28,791 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3434680> about HardwareID('modalias', 'pci:v00008086d00002932sv0000103Csd00003627bc11sc80i00')
2010-04-30 13:29:28,791 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3434680> about HardwareID('modalias', 'pci:v00008086d00002938sv0000103Csd00003627bc0Csc03i00')
2010-04-30 13:29:28,791 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3434680> about HardwareID('modalias', 'pci:v00008086d00002929sv0000103Csd00003627bc01sc06i01')
2010-04-30 13:29:28,791 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3434680> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,3,kra0,1,2,mlsfw')
2010-04-30 13:29:28,791 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3434680> about HardwareID('modalias', 'acpi:ENE0100:')
2010-04-30 13:29:28,791 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3434680> about HardwareID('modalias', 'pci:v00008086d00002937sv0000103Csd00003627bc0Csc03i00')
2010-04-30 13:29:28,791 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3434680> about HardwareID('modalias', 'acpi:PNP0303:')
2010-04-30 13:29:28,791 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3434680> about HardwareID('modalias', 'usb:v5986p0180d0003dcEFdsc02dp01ic0Eisc02ip00')
2010-04-30 13:29:28,791 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3434680> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2010-04-30 13:29:28,792 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3434680> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-04-30 13:29:28,792 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3434680> about HardwareID('modalias', 'usb:v0A12p0001d0134dcE0dsc01dp01icE0isc01ip01')
2010-04-30 13:29:28,792 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3434680> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2010-04-30 13:29:28,792 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3434680> about HardwareID('modalias', 'pci:v00008086d0000293Asv0000103Csd00003627bc0Csc03i20')
2010-04-30 13:29:28,792 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3434680> about HardwareID('modalias', 'pci:v00008086d0000293Csv0000103Csd00003627bc0Csc03i20')
2010-04-30 13:29:28,792 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3434680> about HardwareID('modalias', 'pci:v00008086d00002934sv0000103Csd00003627bc0Csc03i00')
2010-04-30 13:29:28,792 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3434680> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-04-30 13:29:28,792 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3434680> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-04-30 13:29:28,792 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3434680> about HardwareID('modalias', 'pci:v000010ECd00008136sv0000103Csd00003627bc02sc00i00')
2010-04-30 13:29:28,792 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x3434680> about HardwareID('modalias', 'acpi:PNP0200:')
2010-04-30 13:29:28,854 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-04-30 13:29:28,888 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-04-30 13:29:28,923 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-04-30 13:29:44,391 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-04-30 13:29:48,257 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-04-30 13:29:48,257 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2010-04-30 13:29:48,290 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-04-30 13:29:53,806 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-04-30 13:29:53,826 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-04-30 13:29:53,861 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-04-30 13:29:55,824 DEBUG: Shutting down
2010-04-30 13:32:54,551 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bed248>
2010-04-30 13:32:54,560 DEBUG: reading modalias file /lib/modules/2.6.31-10-rt/modules.alias
2010-04-30 13:32:54,755 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-04-30 13:32:54,789 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-04-30 13:32:54,837 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-04-30 13:32:54,870 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2010-04-30 13:32:54,910 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2010-04-30 13:32:54,949 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2010-04-30 13:32:54,956 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2010-04-30 13:32:55,199 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2010-04-30 13:32:55,279 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2010-04-30 13:32:55,377 DEBUG: Software modem not available
2010-04-30 13:32:55,377 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2010-04-30 13:32:55,546 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-04-30 13:32:55,547 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2010-04-30 13:32:55,558 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2010-04-30 13:32:55,559 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2010-04-30 13:32:55,750 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2010-04-30 13:32:55,750 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2010-04-30 13:32:55,791 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2010-04-30 13:32:55,792 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2010-04-30 13:32:55,792 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2010-04-30 13:32:55,799 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-04-30 13:32:55,811 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2010-04-30 13:32:55,811 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2010-04-30 13:32:55,811 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2010-04-30 13:32:55,903 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2010-04-30 13:32:55,904 DEBUG: Firmware for DVB cards not available
2010-04-30 13:32:55,904 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2010-04-30 13:32:55,928 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2010-04-30 13:32:55,929 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2010-04-30 13:32:55,941 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-04-30 13:32:55,947 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2010-04-30 13:32:55,948 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2010-04-30 13:32:55,959 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-04-30 13:32:55,960 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2010-04-30 13:32:55,993 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2010-04-30 13:32:55,994 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2010-04-30 13:32:56,005 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-04-30 13:32:56,006 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2010-04-30 13:32:56,013 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2010-04-30 13:32:56,014 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2010-04-30 13:32:56,014 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2010-04-30 13:32:56,015 DEBUG: all custom handlers loaded
2010-04-30 13:32:56,015 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bed248> about HardwareID('modalias', 'acpi:INT0800:')
2010-04-30 13:32:56,015 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bed248> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-04-30 13:32:56,320 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:32:56,321 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bed248> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-04-30 13:32:56,321 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bed248> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2010-04-30 13:32:56,321 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bed248> about HardwareID('modalias', 'pci:v00008086d00002A43sv0000103Csd00003627bc03sc80i00')
2010-04-30 13:32:56,519 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bed248> about HardwareID('modalias', 'platform:pcspkr')
2010-04-30 13:32:56,520 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:32:56,520 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:32:56,520 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bed248> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-04-30 13:32:56,543 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bed248> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-04-30 13:32:56,544 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:32:56,544 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bed248> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-04-30 13:32:56,544 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bed248> about HardwareID('modalias', 'acpi:PNP0100:')
2010-04-30 13:32:56,544 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bed248> about HardwareID('modalias', 'platform:lis3lv02d')
2010-04-30 13:32:56,544 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bed248> about HardwareID('modalias', 'input:b0003v5986p0180e0003-e0,1,kD4,ramlsfw')
2010-04-30 13:32:56,545 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:32:56,545 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bed248> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-04-30 13:32:56,545 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bed248> about HardwareID('modalias', 'pci:v00008086d00002A40sv0000103Csd00003627bc06sc00i00')
2010-04-30 13:32:56,548 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_agp', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:32:56,548 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bed248> about HardwareID('modalias', 'pci:v000014E4d0000432Bsv0000103Csd00001509bc02sc80i00')
2010-04-30 13:32:56,591 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ssb', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:32:56,595 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-04-30 13:32:56,596 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-04-30 13:32:56,595 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2010-04-30 13:32:56,596 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bed248> about HardwareID('modalias', 'acpi:PNP0103:')
2010-04-30 13:32:56,596 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bed248> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-04-30 13:32:56,596 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bed248> about HardwareID('modalias', 'pci:v00008086d00002A42sv0000103Csd00003627bc03sc00i00')
2010-04-30 13:32:56,599 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:32:56,599 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bed248> about HardwareID('modalias', 'pci:v00008086d0000293Esv0000103Csd00003627bc04sc03i00')
2010-04-30 13:32:56,602 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:32:56,602 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bed248> about HardwareID('modalias', 'acpi:PNP0000:')
2010-04-30 13:32:56,602 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bed248> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-04-30 13:32:56,604 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bed248> about HardwareID('modalias', 'pci:v00008086d00002936sv0000103Csd00003627bc0Csc03i00')
2010-04-30 13:32:56,607 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bed248> about HardwareID('modalias', 'pci:v00008086d00002930sv0000103Csd00003627bc0Csc05i00')
2010-04-30 13:32:56,609 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:32:56,609 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bed248> about HardwareID('modalias', 'usb:v5986p0180d0003dcEFdsc02dp01ic0Eisc01ip00')
2010-04-30 13:32:56,610 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:32:56,610 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bed248> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-04-30 13:32:56,610 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:32:56,610 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bed248> about HardwareID('modalias', 'input:b0001v111Dp7603e0001-e0,12,kramls1,2,fw')
2010-04-30 13:32:56,611 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:32:56,611 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bed248> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,112,145,14A,ra0,1,18,1C,mlsfw')
2010-04-30 13:32:56,611 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:32:56,611 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:32:56,611 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:32:56,611 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bed248> about HardwareID('modalias', 'acpi:SYN1E04:SYN1E00:SYN0002:PNP0F13:')
2010-04-30 13:32:56,611 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bed248> about HardwareID('modalias', 'pci:v00008086d00002935sv0000103Csd00003627bc0Csc03i00')
2010-04-30 13:32:56,614 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bed248> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-04-30 13:32:56,614 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:32:56,614 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bed248> about HardwareID('modalias', 'acpi:PNP0C32:')
2010-04-30 13:32:56,614 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bed248> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvrF.33:bd08/31/2009:svnHewlett-Packard:pnHPPaviliondv6NotebookPC:pvrRev1:rvnQuanta:rn3627:rvr18.42:cvnQuanta:ct10:cvrN/A:')
2010-04-30 13:32:56,628 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bed248> about HardwareID('modalias', 'pci:v00008086d00002919sv0000103Csd00003627bc06sc01i00')
2010-04-30 13:32:56,630 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:32:56,631 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bed248> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-04-30 13:32:56,631 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bed248> about HardwareID('modalias', 'pci:v00008086d00002939sv0000103Csd00003627bc0Csc03i00')
2010-04-30 13:32:56,633 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bed248> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-04-30 13:32:56,633 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:32:56,633 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bed248> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-04-30 13:32:56,634 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bed248> about HardwareID('modalias', 'usb:v0BDAp0158d5887dc00dsc00dp00ic08isc06ip50')
2010-04-30 13:32:56,638 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:32:56,638 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bed248> about HardwareID('modalias', 'pci:v00008086d00002932sv0000103Csd00003627bc11sc80i00')
2010-04-30 13:32:56,641 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bed248> about HardwareID('modalias', 'pci:v00008086d00002938sv0000103Csd00003627bc0Csc03i00')
2010-04-30 13:32:56,643 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bed248> about HardwareID('modalias', 'pci:v00008086d00002929sv0000103Csd00003627bc01sc06i01')
2010-04-30 13:32:56,646 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bed248> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,3,kra0,1,2,mlsfw')
2010-04-30 13:32:56,646 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:32:56,646 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:32:56,646 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bed248> about HardwareID('modalias', 'acpi:ENE0100:')
2010-04-30 13:32:56,646 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bed248> about HardwareID('modalias', 'pci:v00008086d00002937sv0000103Csd00003627bc0Csc03i00')
2010-04-30 13:32:56,649 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bed248> about HardwareID('modalias', 'acpi:PNP0303:')
2010-04-30 13:32:56,649 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bed248> about HardwareID('modalias', 'usb:v5986p0180d0003dcEFdsc02dp01ic0Eisc02ip00')
2010-04-30 13:32:56,649 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bed248> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2010-04-30 13:32:56,649 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:32:56,649 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bed248> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-04-30 13:32:56,650 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bed248> about HardwareID('modalias', 'usb:v0A12p0001d0134dcE0dsc01dp01icE0isc01ip01')
2010-04-30 13:32:56,650 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:32:56,650 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bed248> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2010-04-30 13:32:56,650 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:32:56,650 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bed248> about HardwareID('modalias', 'pci:v00008086d0000293Asv0000103Csd00003627bc0Csc03i20')
2010-04-30 13:32:56,653 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bed248> about HardwareID('modalias', 'pci:v00008086d0000293Csv0000103Csd00003627bc0Csc03i20')
2010-04-30 13:32:56,655 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bed248> about HardwareID('modalias', 'pci:v00008086d00002934sv0000103Csd00003627bc0Csc03i00')
2010-04-30 13:32:56,658 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bed248> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-04-30 13:32:56,667 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:32:56,667 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:32:56,667 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bed248> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-04-30 13:32:56,668 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:32:56,668 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bed248> about HardwareID('modalias', 'pci:v000010ECd00008136sv0000103Csd00003627bc02sc00i00')
2010-04-30 13:32:56,672 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 13:32:56,673 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2bed248> about HardwareID('modalias', 'acpi:PNP0200:')
2010-04-30 13:32:56,673 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x307f680> about HardwareID('modalias', 'acpi:INT0800:')
2010-04-30 13:32:56,673 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x307f680> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-04-30 13:32:56,673 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x307f680> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-04-30 13:32:56,673 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x307f680> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2010-04-30 13:32:56,673 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x307f680> about HardwareID('modalias', 'pci:v00008086d00002A43sv0000103Csd00003627bc03sc80i00')
2010-04-30 13:32:56,673 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x307f680> about HardwareID('modalias', 'platform:pcspkr')
2010-04-30 13:32:56,673 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x307f680> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-04-30 13:32:56,673 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x307f680> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-04-30 13:32:56,674 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x307f680> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-04-30 13:32:56,674 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x307f680> about HardwareID('modalias', 'acpi:PNP0100:')
2010-04-30 13:32:56,674 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x307f680> about HardwareID('modalias', 'platform:lis3lv02d')
2010-04-30 13:32:56,674 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x307f680> about HardwareID('modalias', 'input:b0003v5986p0180e0003-e0,1,kD4,ramlsfw')
2010-04-30 13:32:56,674 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x307f680> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-04-30 13:32:56,674 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x307f680> about HardwareID('modalias', 'pci:v00008086d00002A40sv0000103Csd00003627bc06sc00i00')
2010-04-30 13:32:56,674 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x307f680> about HardwareID('modalias', 'pci:v000014E4d0000432Bsv0000103Csd00001509bc02sc80i00')
2010-04-30 13:32:56,674 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x307f680> about HardwareID('modalias', 'acpi:PNP0103:')
2010-04-30 13:32:56,674 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x307f680> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-04-30 13:32:56,674 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x307f680> about HardwareID('modalias', 'pci:v00008086d00002A42sv0000103Csd00003627bc03sc00i00')
2010-04-30 13:32:56,675 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x307f680> about HardwareID('modalias', 'pci:v00008086d0000293Esv0000103Csd00003627bc04sc03i00')
2010-04-30 13:32:56,675 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x307f680> about HardwareID('modalias', 'acpi:PNP0000:')
2010-04-30 13:32:56,675 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x307f680> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-04-30 13:32:56,675 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x307f680> about HardwareID('modalias', 'pci:v00008086d00002936sv0000103Csd00003627bc0Csc03i00')
2010-04-30 13:32:56,675 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x307f680> about HardwareID('modalias', 'pci:v00008086d00002930sv0000103Csd00003627bc0Csc05i00')
2010-04-30 13:32:56,675 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x307f680> about HardwareID('modalias', 'usb:v5986p0180d0003dcEFdsc02dp01ic0Eisc01ip00')
2010-04-30 13:32:56,675 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x307f680> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-04-30 13:32:56,675 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x307f680> about HardwareID('modalias', 'input:b0001v111Dp7603e0001-e0,12,kramls1,2,fw')
2010-04-30 13:32:56,675 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x307f680> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,112,145,14A,ra0,1,18,1C,mlsfw')
2010-04-30 13:32:56,675 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x307f680> about HardwareID('modalias', 'acpi:SYN1E04:SYN1E00:SYN0002:PNP0F13:')
2010-04-30 13:32:56,676 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x307f680> about HardwareID('modalias', 'pci:v00008086d00002935sv0000103Csd00003627bc0Csc03i00')
2010-04-30 13:32:56,676 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x307f680> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-04-30 13:32:56,676 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x307f680> about HardwareID('modalias', 'acpi:PNP0C32:')
2010-04-30 13:32:56,676 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x307f680> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvrF.33:bd08/31/2009:svnHewlett-Packard:pnHPPaviliondv6NotebookPC:pvrRev1:rvnQuanta:rn3627:rvr18.42:cvnQuanta:ct10:cvrN/A:')
2010-04-30 13:32:56,676 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x307f680> about HardwareID('modalias', 'pci:v00008086d00002919sv0000103Csd00003627bc06sc01i00')
2010-04-30 13:32:56,676 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x307f680> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-04-30 13:32:56,676 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x307f680> about HardwareID('modalias', 'pci:v00008086d00002939sv0000103Csd00003627bc0Csc03i00')
2010-04-30 13:32:56,676 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x307f680> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-04-30 13:32:56,676 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x307f680> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-04-30 13:32:56,677 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x307f680> about HardwareID('modalias', 'usb:v0BDAp0158d5887dc00dsc00dp00ic08isc06ip50')
2010-04-30 13:32:56,677 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x307f680> about HardwareID('modalias', 'pci:v00008086d00002932sv0000103Csd00003627bc11sc80i00')
2010-04-30 13:32:56,677 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x307f680> about HardwareID('modalias', 'pci:v00008086d00002938sv0000103Csd00003627bc0Csc03i00')
2010-04-30 13:32:56,677 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x307f680> about HardwareID('modalias', 'pci:v00008086d00002929sv0000103Csd00003627bc01sc06i01')
2010-04-30 13:32:56,677 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x307f680> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,3,kra0,1,2,mlsfw')
2010-04-30 13:32:56,677 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x307f680> about HardwareID('modalias', 'acpi:ENE0100:')
2010-04-30 13:32:56,677 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x307f680> about HardwareID('modalias', 'pci:v00008086d00002937sv0000103Csd00003627bc0Csc03i00')
2010-04-30 13:32:56,677 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x307f680> about HardwareID('modalias', 'acpi:PNP0303:')
2010-04-30 13:32:56,677 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x307f680> about HardwareID('modalias', 'usb:v5986p0180d0003dcEFdsc02dp01ic0Eisc02ip00')
2010-04-30 13:32:56,677 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x307f680> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2010-04-30 13:32:56,678 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x307f680> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-04-30 13:32:56,678 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x307f680> about HardwareID('modalias', 'usb:v0A12p0001d0134dcE0dsc01dp01icE0isc01ip01')
2010-04-30 13:32:56,678 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x307f680> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2010-04-30 13:32:56,678 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x307f680> about HardwareID('modalias', 'pci:v00008086d0000293Asv0000103Csd00003627bc0Csc03i20')
2010-04-30 13:32:56,678 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x307f680> about HardwareID('modalias', 'pci:v00008086d0000293Csv0000103Csd00003627bc0Csc03i20')
2010-04-30 13:32:56,678 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x307f680> about HardwareID('modalias', 'pci:v00008086d00002934sv0000103Csd00003627bc0Csc03i00')
2010-04-30 13:32:56,678 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x307f680> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-04-30 13:32:56,678 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x307f680> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-04-30 13:32:56,678 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x307f680> about HardwareID('modalias', 'pci:v000010ECd00008136sv0000103Csd00003627bc02sc00i00')
2010-04-30 13:32:56,678 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x307f680> about HardwareID('modalias', 'acpi:PNP0200:')
2010-04-30 13:32:56,767 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-04-30 13:32:56,872 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-04-30 13:32:56,914 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-04-30 13:33:05,186 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-04-30 13:33:08,173 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-04-30 13:33:08,174 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2010-04-30 13:33:08,212 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-04-30 13:33:11,039 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-04-30 13:33:11,058 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-04-30 13:33:11,093 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-04-30 13:33:12,537 DEBUG: Shutting down
2010-04-30 14:57:19,810 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x254d248>
2010-04-30 14:57:20,089 DEBUG: reading modalias file /lib/modules/2.6.31-10-rt/modules.alias
2010-04-30 14:57:20,228 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-04-30 14:57:20,262 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-04-30 14:57:20,312 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-04-30 14:57:20,343 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2010-04-30 14:57:20,383 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2010-04-30 14:57:20,422 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2010-04-30 14:57:20,429 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2010-04-30 14:57:20,683 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2010-04-30 14:57:20,764 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2010-04-30 14:57:20,862 DEBUG: Software modem not available
2010-04-30 14:57:20,862 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2010-04-30 14:57:21,053 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-04-30 14:57:21,053 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2010-04-30 14:57:21,066 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2010-04-30 14:57:21,066 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2010-04-30 14:57:21,300 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2010-04-30 14:57:21,300 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2010-04-30 14:57:21,342 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2010-04-30 14:57:21,342 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2010-04-30 14:57:21,342 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2010-04-30 14:57:21,377 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-04-30 14:57:21,384 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2010-04-30 14:57:21,384 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2010-04-30 14:57:21,384 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2010-04-30 14:57:21,509 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2010-04-30 14:57:21,510 DEBUG: Firmware for DVB cards not available
2010-04-30 14:57:21,510 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2010-04-30 14:57:21,522 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2010-04-30 14:57:21,522 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2010-04-30 14:57:21,530 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-04-30 14:57:21,534 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2010-04-30 14:57:21,534 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2010-04-30 14:57:21,541 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-04-30 14:57:21,542 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2010-04-30 14:57:21,576 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2010-04-30 14:57:21,576 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2010-04-30 14:57:21,584 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-04-30 14:57:21,584 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2010-04-30 14:57:21,590 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2010-04-30 14:57:21,590 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2010-04-30 14:57:21,590 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2010-04-30 14:57:21,591 DEBUG: all custom handlers loaded
2010-04-30 14:57:21,591 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x254d248> about HardwareID('modalias', 'acpi:INT0800:')
2010-04-30 14:57:21,591 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x254d248> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-04-30 14:57:21,895 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 14:57:21,896 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x254d248> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-04-30 14:57:21,896 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x254d248> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2010-04-30 14:57:21,896 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x254d248> about HardwareID('modalias', 'pci:v00008086d00002A43sv0000103Csd00003627bc03sc80i00')
2010-04-30 14:57:22,093 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x254d248> about HardwareID('modalias', 'platform:pcspkr')
2010-04-30 14:57:22,094 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 14:57:22,096 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 14:57:22,096 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x254d248> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-04-30 14:57:22,119 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x254d248> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-04-30 14:57:22,120 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 14:57:22,120 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x254d248> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-04-30 14:57:22,120 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x254d248> about HardwareID('modalias', 'acpi:PNP0100:')
2010-04-30 14:57:22,120 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x254d248> about HardwareID('modalias', 'platform:lis3lv02d')
2010-04-30 14:57:22,121 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x254d248> about HardwareID('modalias', 'input:b0003v5986p0180e0003-e0,1,kD4,ramlsfw')
2010-04-30 14:57:22,121 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 14:57:22,121 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x254d248> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-04-30 14:57:22,121 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x254d248> about HardwareID('modalias', 'pci:v00008086d00002A40sv0000103Csd00003627bc06sc00i00')
2010-04-30 14:57:22,124 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_agp', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 14:57:22,124 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x254d248> about HardwareID('modalias', 'pci:v000014E4d0000432Bsv0000103Csd00001509bc02sc80i00')
2010-04-30 14:57:22,167 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ssb', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 14:57:22,171 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-04-30 14:57:22,172 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-04-30 14:57:22,172 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2010-04-30 14:57:22,172 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x254d248> about HardwareID('modalias', 'acpi:PNP0103:')
2010-04-30 14:57:22,172 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x254d248> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-04-30 14:57:22,172 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x254d248> about HardwareID('modalias', 'pci:v00008086d00002A42sv0000103Csd00003627bc03sc00i00')
2010-04-30 14:57:22,175 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 14:57:22,176 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x254d248> about HardwareID('modalias', 'pci:v00008086d0000293Esv0000103Csd00003627bc04sc03i00')
2010-04-30 14:57:22,178 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 14:57:22,178 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x254d248> about HardwareID('modalias', 'acpi:PNP0000:')
2010-04-30 14:57:22,178 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x254d248> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-04-30 14:57:22,181 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x254d248> about HardwareID('modalias', 'pci:v00008086d00002936sv0000103Csd00003627bc0Csc03i00')
2010-04-30 14:57:22,183 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x254d248> about HardwareID('modalias', 'pci:v00008086d00002930sv0000103Csd00003627bc0Csc05i00')
2010-04-30 14:57:22,185 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 14:57:22,186 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x254d248> about HardwareID('modalias', 'usb:v5986p0180d0003dcEFdsc02dp01ic0Eisc01ip00')
2010-04-30 14:57:22,186 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 14:57:22,186 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x254d248> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-04-30 14:57:22,186 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 14:57:22,187 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x254d248> about HardwareID('modalias', 'input:b0001v111Dp7603e0001-e0,12,kramls1,2,fw')
2010-04-30 14:57:22,187 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 14:57:22,187 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x254d248> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,112,145,14A,ra0,1,18,1C,mlsfw')
2010-04-30 14:57:22,187 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 14:57:22,187 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 14:57:22,187 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 14:57:22,187 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x254d248> about HardwareID('modalias', 'acpi:SYN1E04:SYN1E00:SYN0002:PNP0F13:')
2010-04-30 14:57:22,188 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x254d248> about HardwareID('modalias', 'pci:v00008086d00002935sv0000103Csd00003627bc0Csc03i00')
2010-04-30 14:57:22,190 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x254d248> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-04-30 14:57:22,190 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 14:57:22,190 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x254d248> about HardwareID('modalias', 'acpi:PNP0C32:')
2010-04-30 14:57:22,190 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x254d248> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvrF.33:bd08/31/2009:svnHewlett-Packard:pnHPPaviliondv6NotebookPC:pvrRev1:rvnQuanta:rn3627:rvr18.42:cvnQuanta:ct10:cvrN/A:')
2010-04-30 14:57:22,204 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x254d248> about HardwareID('modalias', 'pci:v00008086d00002919sv0000103Csd00003627bc06sc01i00')
2010-04-30 14:57:22,207 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 14:57:22,207 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x254d248> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-04-30 14:57:22,207 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x254d248> about HardwareID('modalias', 'pci:v00008086d00002939sv0000103Csd00003627bc0Csc03i00')
2010-04-30 14:57:22,209 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x254d248> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-04-30 14:57:22,210 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 14:57:22,210 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x254d248> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-04-30 14:57:22,210 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x254d248> about HardwareID('modalias', 'usb:v0BDAp0158d5887dc00dsc00dp00ic08isc06ip50')
2010-04-30 14:57:22,215 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 14:57:22,218 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x254d248> about HardwareID('modalias', 'pci:v00008086d00002932sv0000103Csd00003627bc11sc80i00')
2010-04-30 14:57:22,221 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x254d248> about HardwareID('modalias', 'pci:v00008086d00002938sv0000103Csd00003627bc0Csc03i00')
2010-04-30 14:57:22,223 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x254d248> about HardwareID('modalias', 'pci:v00008086d00002929sv0000103Csd00003627bc01sc06i01')
2010-04-30 14:57:22,226 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x254d248> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,3,kra0,1,2,mlsfw')
2010-04-30 14:57:22,226 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 14:57:22,226 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 14:57:22,226 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x254d248> about HardwareID('modalias', 'acpi:ENE0100:')
2010-04-30 14:57:22,226 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x254d248> about HardwareID('modalias', 'pci:v00008086d00002937sv0000103Csd00003627bc0Csc03i00')
2010-04-30 14:57:22,229 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x254d248> about HardwareID('modalias', 'acpi:PNP0303:')
2010-04-30 14:57:22,229 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x254d248> about HardwareID('modalias', 'usb:v5986p0180d0003dcEFdsc02dp01ic0Eisc02ip00')
2010-04-30 14:57:22,229 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x254d248> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2010-04-30 14:57:22,229 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 14:57:22,230 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x254d248> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-04-30 14:57:22,230 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x254d248> about HardwareID('modalias', 'usb:v0A12p0001d0134dcE0dsc01dp01icE0isc01ip01')
2010-04-30 14:57:22,230 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 14:57:22,230 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x254d248> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2010-04-30 14:57:22,230 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 14:57:22,231 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x254d248> about HardwareID('modalias', 'pci:v00008086d0000293Asv0000103Csd00003627bc0Csc03i20')
2010-04-30 14:57:22,233 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x254d248> about HardwareID('modalias', 'pci:v00008086d0000293Csv0000103Csd00003627bc0Csc03i20')
2010-04-30 14:57:22,235 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x254d248> about HardwareID('modalias', 'pci:v00008086d00002934sv0000103Csd00003627bc0Csc03i00')
2010-04-30 14:57:22,238 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x254d248> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-04-30 14:57:22,247 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 14:57:22,247 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 14:57:22,247 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x254d248> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-04-30 14:57:22,247 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 14:57:22,248 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x254d248> about HardwareID('modalias', 'pci:v000010ECd00008136sv0000103Csd00003627bc02sc00i00')
2010-04-30 14:57:22,252 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2010-04-30 14:57:22,253 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x254d248> about HardwareID('modalias', 'acpi:PNP0200:')
2010-04-30 14:57:22,253 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29df680> about HardwareID('modalias', 'acpi:INT0800:')
2010-04-30 14:57:22,253 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29df680> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-04-30 14:57:22,253 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29df680> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-04-30 14:57:22,253 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29df680> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2010-04-30 14:57:22,253 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29df680> about HardwareID('modalias', 'pci:v00008086d00002A43sv0000103Csd00003627bc03sc80i00')
2010-04-30 14:57:22,253 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29df680> about HardwareID('modalias', 'platform:pcspkr')
2010-04-30 14:57:22,253 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29df680> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-04-30 14:57:22,253 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29df680> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-04-30 14:57:22,254 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29df680> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-04-30 14:57:22,254 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29df680> about HardwareID('modalias', 'acpi:PNP0100:')
2010-04-30 14:57:22,254 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29df680> about HardwareID('modalias', 'platform:lis3lv02d')
2010-04-30 14:57:22,254 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29df680> about HardwareID('modalias', 'input:b0003v5986p0180e0003-e0,1,kD4,ramlsfw')
2010-04-30 14:57:22,254 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29df680> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-04-30 14:57:22,254 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29df680> about HardwareID('modalias', 'pci:v00008086d00002A40sv0000103Csd00003627bc06sc00i00')
2010-04-30 14:57:22,254 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29df680> about HardwareID('modalias', 'pci:v000014E4d0000432Bsv0000103Csd00001509bc02sc80i00')
2010-04-30 14:57:22,254 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29df680> about HardwareID('modalias', 'acpi:PNP0103:')
2010-04-30 14:57:22,254 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29df680> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-04-30 14:57:22,254 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29df680> about HardwareID('modalias', 'pci:v00008086d00002A42sv0000103Csd00003627bc03sc00i00')
2010-04-30 14:57:22,255 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29df680> about HardwareID('modalias', 'pci:v00008086d0000293Esv0000103Csd00003627bc04sc03i00')
2010-04-30 14:57:22,255 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29df680> about HardwareID('modalias', 'acpi:PNP0000:')
2010-04-30 14:57:22,255 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29df680> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-04-30 14:57:22,255 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29df680> about HardwareID('modalias', 'pci:v00008086d00002936sv0000103Csd00003627bc0Csc03i00')
2010-04-30 14:57:22,255 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29df680> about HardwareID('modalias', 'pci:v00008086d00002930sv0000103Csd00003627bc0Csc05i00')
2010-04-30 14:57:22,255 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29df680> about HardwareID('modalias', 'usb:v5986p0180d0003dcEFdsc02dp01ic0Eisc01ip00')
2010-04-30 14:57:22,255 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29df680> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-04-30 14:57:22,255 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29df680> about HardwareID('modalias', 'input:b0001v111Dp7603e0001-e0,12,kramls1,2,fw')
2010-04-30 14:57:22,255 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29df680> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,112,145,14A,ra0,1,18,1C,mlsfw')
2010-04-30 14:57:22,255 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29df680> about HardwareID('modalias', 'acpi:SYN1E04:SYN1E00:SYN0002:PNP0F13:')
2010-04-30 14:57:22,256 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29df680> about HardwareID('modalias', 'pci:v00008086d00002935sv0000103Csd00003627bc0Csc03i00')
2010-04-30 14:57:22,256 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29df680> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-04-30 14:57:22,256 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29df680> about HardwareID('modalias', 'acpi:PNP0C32:')
2010-04-30 14:57:22,256 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29df680> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvrF.33:bd08/31/2009:svnHewlett-Packard:pnHPPaviliondv6NotebookPC:pvrRev1:rvnQuanta:rn3627:rvr18.42:cvnQuanta:ct10:cvrN/A:')
2010-04-30 14:57:22,256 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29df680> about HardwareID('modalias', 'pci:v00008086d00002919sv0000103Csd00003627bc06sc01i00')
2010-04-30 14:57:22,256 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29df680> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-04-30 14:57:22,256 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29df680> about HardwareID('modalias', 'pci:v00008086d00002939sv0000103Csd00003627bc0Csc03i00')
2010-04-30 14:57:22,256 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29df680> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-04-30 14:57:22,256 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29df680> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-04-30 14:57:22,256 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29df680> about HardwareID('modalias', 'usb:v0BDAp0158d5887dc00dsc00dp00ic08isc06ip50')
2010-04-30 14:57:22,257 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29df680> about HardwareID('modalias', 'pci:v00008086d00002932sv0000103Csd00003627bc11sc80i00')
2010-04-30 14:57:22,257 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29df680> about HardwareID('modalias', 'pci:v00008086d00002938sv0000103Csd00003627bc0Csc03i00')
2010-04-30 14:57:22,257 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29df680> about HardwareID('modalias', 'pci:v00008086d00002929sv0000103Csd00003627bc01sc06i01')
2010-04-30 14:57:22,257 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29df680> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,3,kra0,1,2,mlsfw')
2010-04-30 14:57:22,257 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29df680> about HardwareID('modalias', 'acpi:ENE0100:')
2010-04-30 14:57:22,257 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29df680> about HardwareID('modalias', 'pci:v00008086d00002937sv0000103Csd00003627bc0Csc03i00')
2010-04-30 14:57:22,257 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29df680> about HardwareID('modalias', 'acpi:PNP0303:')
2010-04-30 14:57:22,257 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29df680> about HardwareID('modalias', 'usb:v5986p0180d0003dcEFdsc02dp01ic0Eisc02ip00')
2010-04-30 14:57:22,257 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29df680> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2010-04-30 14:57:22,257 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29df680> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-04-30 14:57:22,258 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29df680> about HardwareID('modalias', 'usb:v0A12p0001d0134dcE0dsc01dp01icE0isc01ip01')
2010-04-30 14:57:22,258 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29df680> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2010-04-30 14:57:22,258 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29df680> about HardwareID('modalias', 'pci:v00008086d0000293Asv0000103Csd00003627bc0Csc03i20')
2010-04-30 14:57:22,258 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29df680> about HardwareID('modalias', 'pci:v00008086d0000293Csv0000103Csd00003627bc0Csc03i20')
2010-04-30 14:57:22,258 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29df680> about HardwareID('modalias', 'pci:v00008086d00002934sv0000103Csd00003627bc0Csc03i00')
2010-04-30 14:57:22,258 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29df680> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-04-30 14:57:22,258 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29df680> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-04-30 14:57:22,258 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29df680> about HardwareID('modalias', 'pci:v000010ECd00008136sv0000103Csd00003627bc02sc00i00')
2010-04-30 14:57:22,258 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29df680> about HardwareID('modalias', 'acpi:PNP0200:')
2010-04-30 14:57:22,298 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-04-30 14:57:22,441 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-04-30 14:57:22,522 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-04-30 14:57:27,336 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-04-30 14:57:30,933 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-04-30 14:57:30,933 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2010-04-30 14:57:30,996 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-04-30 14:57:54,185 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-04-30 14:57:54,205 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-04-30 14:57:54,242 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-04-30 14:57:56,248 DEBUG: Shutting down
```

---

### Post by Topher88 on 2010-04-30
Okay, I fixed the problem...

Followed the advice found in the comment section [here.]("http://www.qc4blog.com/?p=857")

 "To solve it I simply went to Synaptic Package Manager, typed 'broadcom,' right clicked on 'bcmwl-kernel-source' and marked it for  re-installation."


After doing that, the driver appeared to have already been activated, and my wireless is up and running again!


Sorry to be bothersome, but hopefully if anyone else has this problem, they can now find it here!  Thanks anyway!

---

