---
title: "hd 4330 driver problem"
date: 2010-08-04
forum: Multimedia Software
---

### Post by soultrav on 2010-08-04
Hello, 

I am running Ubuntu 10.04 on a laptop with a HD 4330 video card and after an update, I noticed the system didn't detect my video card...so I opened Hardware Drivers, and saw that the driver I was using, "ATI/AMD proprietary FGLRX graphics driver" was deactivated.
When I try to activate it, it gives an error and tells me to log at /var/log/jockey.log

So, here's the log, I have no idea what could be the problem...

```

2010-08-04 11:39:30,774 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c25d2c>
2010-08-04 11:39:30,776 DEBUG: reading modalias file /lib/modules/2.6.31-16-generic/modules.alias
2010-08-04 11:39:30,889 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-08-04 11:39:30,889 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-08-04 11:39:30,918 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-08-04 11:39:30,919 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2010-08-04 11:39:30,922 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-71
2010-08-04 11:39:30,923 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2010-08-04 11:39:30,925 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2010-08-04 11:39:30,928 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2010-08-04 11:39:31,188 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2010-08-04 11:39:31,199 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2010-08-04 11:39:31,199 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2010-08-04 11:39:31,199 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2010-08-04 11:39:31,203 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2010-08-04 11:39:31,204 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2010-08-04 11:39:31,204 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2010-08-04 11:39:31,204 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2010-08-04 11:39:31,210 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2010-08-04 11:39:31,211 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2010-08-04 11:39:31,219 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-08-04 11:39:31,222 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2010-08-04 11:39:31,223 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2010-08-04 11:39:31,231 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-08-04 11:39:31,231 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2010-08-04 11:39:31,235 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2010-08-04 11:39:31,236 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2010-08-04 11:39:31,244 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-08-04 11:39:31,244 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2010-08-04 11:39:31,256 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2010-08-04 11:39:31,257 DEBUG: Firmware for DVB cards not available
2010-08-04 11:39:31,257 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2010-08-04 11:39:31,268 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2010-08-04 11:39:31,278 DEBUG: Software modem not available
2010-08-04 11:39:31,278 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2010-08-04 11:39:31,283 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-08-04 11:39:31,285 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2010-08-04 11:39:31,295 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2010-08-04 11:39:31,295 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2010-08-04 11:39:31,314 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2010-08-04 11:39:31,314 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2010-08-04 11:39:31,318 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2010-08-04 11:39:31,318 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2010-08-04 11:39:31,318 DEBUG: all custom handlers loaded
2010-08-04 11:39:31,319 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c25d2c> about HardwareID('modalias', 'pci:v00001002d0000AA38sv00001002sd0000AA38bc04sc03i00')
2010-08-04 11:39:31,742 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2010-08-04 11:39:31,743 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2010-08-04 11:39:31,743 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c25d2c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-08-04 11:39:31,746 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-08-04 11:39:31,746 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c25d2c> about HardwareID('modalias', 'pci:v00008086d00002929sv0000103Csd00003074bc01sc06i01')
2010-08-04 11:39:31,951 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c25d2c> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-08-04 11:39:31,954 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c25d2c> about HardwareID('modalias', 'acpi:PNP0000:')
2010-08-04 11:39:31,954 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c25d2c> about HardwareID('modalias', 'acpi:PNP0200:')
2010-08-04 11:39:31,954 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c25d2c> about HardwareID('modalias', 'pci:v00008086d00002937sv0000103Csd00003074bc0Csc03i00')
2010-08-04 11:39:31,957 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c25d2c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-08-04 11:39:31,957 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-08-04 11:39:31,957 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c25d2c> about HardwareID('modalias', 'platform:eisa')
2010-08-04 11:39:31,957 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c25d2c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-08-04 11:39:31,981 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c25d2c> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-08-04 11:39:31,981 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-08-04 11:39:31,982 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c25d2c> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-08-04 11:39:31,982 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c25d2c> about HardwareID('modalias', 'platform:lis3lv02d')
2010-08-04 11:39:31,982 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c25d2c> about HardwareID('modalias', 'pci:v000011ABd0000436Csv0000103Csd00003074bc02sc00i00')
2010-08-04 11:39:32,007 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sky2', 'jockey_handler': 'KernelModuleHandler'}
2010-08-04 11:39:32,008 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c25d2c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-08-04 11:39:32,008 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c25d2c> about HardwareID('modalias', 'pci:v00008086d00002919sv0000103Csd00003074bc06sc01i00')
2010-08-04 11:39:32,010 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2010-08-04 11:39:32,010 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c25d2c> about HardwareID('modalias', 'pci:v00008086d00002A40sv0000103Csd00003074bc06sc00i00')
2010-08-04 11:39:32,013 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_agp', 'jockey_handler': 'KernelModuleHandler'}
2010-08-04 11:39:32,013 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c25d2c> about HardwareID('modalias', 'usb:v04F3p0230d2458dc00dsc00dp00ic03isc01ip02')
2010-08-04 11:39:32,014 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2010-08-04 11:39:32,014 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c25d2c> about HardwareID('modalias', 'acpi:PNP0C32:')
2010-08-04 11:39:32,014 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c25d2c> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-08-04 11:39:32,014 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c25d2c> about HardwareID('modalias', 'pci:v00001002d00009552sv0000103Csd00003074bc03sc00i00')
2010-08-04 11:39:32,020 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-08-04 11:39:32,134 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-08-04 11:39:32,022 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2010-08-04 11:39:32,134 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2010-08-04 11:39:32,134 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c25d2c> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2010-08-04 11:39:32,135 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c25d2c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-08-04 11:39:32,135 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c25d2c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-08-04 11:39:32,135 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c25d2c> about HardwareID('modalias', 'acpi:PNP0303:')
2010-08-04 11:39:32,135 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c25d2c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-08-04 11:39:32,136 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c25d2c> about HardwareID('modalias', 'pci:v00008086d0000293Csv0000103Csd00003074bc0Csc03i20')
2010-08-04 11:39:32,138 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c25d2c> about HardwareID('modalias', 'pci:v00008086d0000293Asv0000103Csd00003074bc0Csc03i20')
2010-08-04 11:39:32,141 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c25d2c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-08-04 11:39:32,141 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-08-04 11:39:32,141 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c25d2c> about HardwareID('modalias', 'input:b0003v5986p03B0e0220-e0,1,kD4,ramlsfw')
2010-08-04 11:39:32,141 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-08-04 11:39:32,142 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c25d2c> about HardwareID('modalias', 'usb:v5986p03B0d0220dcEFdsc02dp01ic0Eisc02ip00')
2010-08-04 11:39:32,142 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c25d2c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,112,145,14A,ra0,1,18,1C,mlsfw')
2010-08-04 11:39:32,142 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-08-04 11:39:32,142 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-08-04 11:39:32,142 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-08-04 11:39:32,143 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c25d2c> about HardwareID('modalias', 'pci:v00008086d00002939sv0000103Csd00003074bc0Csc03i00')
2010-08-04 11:39:32,145 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c25d2c> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvr68PZIVer.F.0D:bd09/10/2009:svnHewlett-Packard:pnHPProBook4510s:pvrF.0D:rvnHewlett-Packard:rn3074:rvrKBCVersion24.0D:cvnHewlett-Packard:ct10:cvr:')
2010-08-04 11:39:32,160 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c25d2c> about HardwareID('modalias', 'acpi:PNP0100:')
2010-08-04 11:39:32,160 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c25d2c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,3,kra0,1,2,mlsfw')
2010-08-04 11:39:32,160 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-08-04 11:39:32,160 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-08-04 11:39:32,160 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c25d2c> about HardwareID('modalias', 'usb:v03F0p171Dd0100dcE0dsc01dp01icE0isc01ip01')
2010-08-04 11:39:32,175 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2010-08-04 11:39:32,176 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c25d2c> about HardwareID('modalias', 'usb:v03F0p171Dd0100dcE0dsc01dp01icFFiscFFipFF')
2010-08-04 11:39:32,176 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2010-08-04 11:39:32,176 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c25d2c> about HardwareID('modalias', 'acpi:SYN0149:SYN0100:SYN0002:PNP0F13:')
2010-08-04 11:39:32,176 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c25d2c> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-08-04 11:39:32,177 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c25d2c> about HardwareID('modalias', 'pci:v00008086d00002936sv0000103Csd00003074bc0Csc03i00')
2010-08-04 11:39:32,179 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c25d2c> about HardwareID('modalias', 'usb:v5986p03B0d0220dcEFdsc02dp01ic0Eisc01ip00')
2010-08-04 11:39:32,179 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2010-08-04 11:39:32,180 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c25d2c> about HardwareID('modalias', 'pci:v00008086d00002938sv0000103Csd00003074bc0Csc03i00')
2010-08-04 11:39:32,182 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c25d2c> about HardwareID('modalias', 'pci:v00008086d00002935sv0000103Csd00003074bc0Csc03i00')
2010-08-04 11:39:32,185 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c25d2c> about HardwareID('modalias', 'pci:v00008086d0000293Esv0000103Csd00003075bc04sc03i00')
2010-08-04 11:39:32,187 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2010-08-04 11:39:32,187 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c25d2c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2010-08-04 11:39:32,187 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-08-04 11:39:32,187 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c25d2c> about HardwareID('modalias', 'acpi:INT0800:')
2010-08-04 11:39:32,188 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c25d2c> about HardwareID('modalias', 'usb:v03F0p171Dd0100dcE0dsc01dp01icFEisc01ip00')
2010-08-04 11:39:32,188 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2010-08-04 11:39:32,188 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c25d2c> about HardwareID('modalias', 'pci:v000014E4d00004315sv0000103Csd00001508bc02sc80i00')
2010-08-04 11:39:32,235 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ssb', 'jockey_handler': 'KernelModuleHandler'}
2010-08-04 11:39:32,334 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-08-04 11:39:32,235 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, enabled] Broadcom STA wireless driver)
2010-08-04 11:39:32,432 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-08-04 11:39:32,334 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, enabled] Broadcom STA wireless driver)
2010-08-04 11:39:32,433 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c25d2c> about HardwareID('modalias', 'platform:pcspkr')
2010-08-04 11:39:32,433 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2010-08-04 11:39:32,433 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2010-08-04 11:39:32,434 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c25d2c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-08-04 11:39:32,443 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2010-08-04 11:39:32,444 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2010-08-04 11:39:32,444 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c25d2c> about HardwareID('modalias', 'usb:v058Fp6366d0100dc00dsc00dp00ic08isc06ip50')
2010-08-04 11:39:32,446 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2010-08-04 11:39:32,446 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c25d2c> about HardwareID('modalias', 'input:b0003v04F3p0230e0111-e0,1,2,4,k110,111,112,r0,1,8,am4,lsfw')
2010-08-04 11:39:32,447 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-08-04 11:39:32,447 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c25d2c> about HardwareID('modalias', 'pci:v00008086d00002934sv0000103Csd00003074bc0Csc03i00')
2010-08-04 11:39:32,450 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c25d2c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-08-04 11:39:32,450 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-08-04 11:39:32,450 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c25d2c> about HardwareID('modalias', 'input:b0001v11D4p194Ae0001-e0,12,kramls1,2,fw')
2010-08-04 11:39:32,450 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-08-04 11:39:32,450 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c25d2c> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2010-08-04 11:39:32,450 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fcc98c> about HardwareID('modalias', 'pci:v00001002d0000AA38sv00001002sd0000AA38bc04sc03i00')
2010-08-04 11:39:32,451 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fcc98c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-08-04 11:39:32,451 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fcc98c> about HardwareID('modalias', 'pci:v00008086d00002929sv0000103Csd00003074bc01sc06i01')
2010-08-04 11:39:32,451 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fcc98c> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-08-04 11:39:32,451 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fcc98c> about HardwareID('modalias', 'acpi:PNP0000:')
2010-08-04 11:39:32,451 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fcc98c> about HardwareID('modalias', 'acpi:PNP0200:')
2010-08-04 11:39:32,451 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fcc98c> about HardwareID('modalias', 'pci:v00008086d00002937sv0000103Csd00003074bc0Csc03i00')
2010-08-04 11:39:32,451 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fcc98c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-08-04 11:39:32,451 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fcc98c> about HardwareID('modalias', 'platform:eisa')
2010-08-04 11:39:32,451 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fcc98c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-08-04 11:39:32,451 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fcc98c> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-08-04 11:39:32,452 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fcc98c> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-08-04 11:39:32,452 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fcc98c> about HardwareID('modalias', 'platform:lis3lv02d')
2010-08-04 11:39:32,452 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fcc98c> about HardwareID('modalias', 'pci:v000011ABd0000436Csv0000103Csd00003074bc02sc00i00')
2010-08-04 11:39:32,452 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fcc98c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-08-04 11:39:32,452 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fcc98c> about HardwareID('modalias', 'pci:v00008086d00002919sv0000103Csd00003074bc06sc01i00')
2010-08-04 11:39:32,452 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fcc98c> about HardwareID('modalias', 'pci:v00008086d00002A40sv0000103Csd00003074bc06sc00i00')
2010-08-04 11:39:32,452 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fcc98c> about HardwareID('modalias', 'usb:v04F3p0230d2458dc00dsc00dp00ic03isc01ip02')
2010-08-04 11:39:32,452 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fcc98c> about HardwareID('modalias', 'acpi:PNP0C32:')
2010-08-04 11:39:32,452 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fcc98c> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-08-04 11:39:32,452 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fcc98c> about HardwareID('modalias', 'pci:v00001002d00009552sv0000103Csd00003074bc03sc00i00')
2010-08-04 11:39:32,453 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fcc98c> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2010-08-04 11:39:32,453 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fcc98c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-08-04 11:39:32,453 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fcc98c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-08-04 11:39:32,453 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fcc98c> about HardwareID('modalias', 'acpi:PNP0303:')
2010-08-04 11:39:32,453 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fcc98c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-08-04 11:39:32,453 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fcc98c> about HardwareID('modalias', 'pci:v00008086d0000293Csv0000103Csd00003074bc0Csc03i20')
2010-08-04 11:39:32,453 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fcc98c> about HardwareID('modalias', 'pci:v00008086d0000293Asv0000103Csd00003074bc0Csc03i20')
2010-08-04 11:39:32,453 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fcc98c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-08-04 11:39:32,453 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fcc98c> about HardwareID('modalias', 'input:b0003v5986p03B0e0220-e0,1,kD4,ramlsfw')
2010-08-04 11:39:32,453 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fcc98c> about HardwareID('modalias', 'usb:v5986p03B0d0220dcEFdsc02dp01ic0Eisc02ip00')
2010-08-04 11:39:32,454 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fcc98c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,112,145,14A,ra0,1,18,1C,mlsfw')
2010-08-04 11:39:32,454 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fcc98c> about HardwareID('modalias', 'pci:v00008086d00002939sv0000103Csd00003074bc0Csc03i00')
2010-08-04 11:39:32,454 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fcc98c> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvr68PZIVer.F.0D:bd09/10/2009:svnHewlett-Packard:pnHPProBook4510s:pvrF.0D:rvnHewlett-Packard:rn3074:rvrKBCVersion24.0D:cvnHewlett-Packard:ct10:cvr:')
2010-08-04 11:39:32,454 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fcc98c> about HardwareID('modalias', 'acpi:PNP0100:')
2010-08-04 11:39:32,454 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fcc98c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,3,kra0,1,2,mlsfw')
2010-08-04 11:39:32,454 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fcc98c> about HardwareID('modalias', 'usb:v03F0p171Dd0100dcE0dsc01dp01icE0isc01ip01')
2010-08-04 11:39:32,454 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fcc98c> about HardwareID('modalias', 'usb:v03F0p171Dd0100dcE0dsc01dp01icFFiscFFipFF')
2010-08-04 11:39:32,454 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fcc98c> about HardwareID('modalias', 'acpi:SYN0149:SYN0100:SYN0002:PNP0F13:')
2010-08-04 11:39:32,454 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fcc98c> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-08-04 11:39:32,454 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fcc98c> about HardwareID('modalias', 'pci:v00008086d00002936sv0000103Csd00003074bc0Csc03i00')
2010-08-04 11:39:32,455 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fcc98c> about HardwareID('modalias', 'usb:v5986p03B0d0220dcEFdsc02dp01ic0Eisc01ip00')
2010-08-04 11:39:32,455 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fcc98c> about HardwareID('modalias', 'pci:v00008086d00002938sv0000103Csd00003074bc0Csc03i00')
2010-08-04 11:39:32,455 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fcc98c> about HardwareID('modalias', 'pci:v00008086d00002935sv0000103Csd00003074bc0Csc03i00')
2010-08-04 11:39:32,455 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fcc98c> about HardwareID('modalias', 'pci:v00008086d0000293Esv0000103Csd00003075bc04sc03i00')
2010-08-04 11:39:32,455 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fcc98c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2010-08-04 11:39:32,455 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fcc98c> about HardwareID('modalias', 'acpi:INT0800:')
2010-08-04 11:39:32,455 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fcc98c> about HardwareID('modalias', 'usb:v03F0p171Dd0100dcE0dsc01dp01icFEisc01ip00')
2010-08-04 11:39:32,455 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fcc98c> about HardwareID('modalias', 'pci:v000014E4d00004315sv0000103Csd00001508bc02sc80i00')
2010-08-04 11:39:32,455 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fcc98c> about HardwareID('modalias', 'platform:pcspkr')
2010-08-04 11:39:32,456 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fcc98c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-08-04 11:39:32,456 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fcc98c> about HardwareID('modalias', 'usb:v058Fp6366d0100dc00dsc00dp00ic08isc06ip50')
2010-08-04 11:39:32,456 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fcc98c> about HardwareID('modalias', 'input:b0003v04F3p0230e0111-e0,1,2,4,k110,111,112,r0,1,8,am4,lsfw')
2010-08-04 11:39:32,456 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fcc98c> about HardwareID('modalias', 'pci:v00008086d00002934sv0000103Csd00003074bc0Csc03i00')
2010-08-04 11:39:32,456 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fcc98c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-08-04 11:39:32,456 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fcc98c> about HardwareID('modalias', 'input:b0001v11D4p194Ae0001-e0,12,kramls1,2,fw')
2010-08-04 11:39:32,456 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fcc98c> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2010-08-04 11:39:32,624 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-08-04 11:39:32,826 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-08-04 11:39:32,983 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-08-04 11:39:33,110 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-08-04 11:39:33,308 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-08-04 11:39:33,457 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-08-04 11:39:33,662 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-08-04 11:39:35,798 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-08-04 11:39:36,916 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-08-04 11:39:41,262 DEBUG: Installing package: linux-headers-2.6.31-16-generic
2010-08-04 11:39:41,540 DEBUG: Package linux-headers-2.6.31-16-generic does not exist, aborting
2010-08-04 11:39:41,858 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-08-04 11:39:41,858 WARNING: /sys/module/fglrx/drivers does not exist, cannot rebind fglrx driver
2010-08-04 11:39:41,859 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2010-08-04 11:39:51,296 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-08-04 11:39:51,412 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-08-04 11:39:53,257 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-08-04 11:39:53,459 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-08-04 11:39:53,599 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-08-04 11:39:53,715 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-08-04 11:39:53,863 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-08-04 11:39:53,985 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-08-04 11:39:54,134 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-08-04 11:39:54,340 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-08-04 11:40:02,623 DEBUG: Shutting down

```

---

