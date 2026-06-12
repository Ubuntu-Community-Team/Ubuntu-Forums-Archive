---
title: "HP Mini 110 USB Karmic Install; can't activate broadcom"
date: 2010-01-19
forum: Networking &amp; Wireless
---

### Post by KrashKharma on 2010-01-19
From what I understand, this problem can be solved easily but you have to insert the install disc into /cdrom/, but I'm on an HP Mini 110 netbook and obviously don't have a cdrom drive...


Is there some way I could redirect it to my usb or something? It doesn't seem to present the option...



Every other release works with my wireless, but this is the only one that works with my sound lol so I'm damned either way. I still use 9.10 sometimes because I love it but I have to hook it up to an ethernet connection and that kind of defeats the purpose of having a netbook :(

---

### Post by Cabs21 on 2010-01-19
next time you hook it up to the internet wired in 9.10 update your drivers to the correct wireless card and it should work fine.  Had the same issue with my bros computer then I connected and updated and the wireless worked great again.

---

### Post by KrashKharma on 2010-01-19
I'm up to date and everything.. 

When I go to Hardware Drivers and click to Activate my Broadcome STA Wireless Driver it says Sorry, Installation of this driver failed. Please have a look at the log file for details: /var/log/jockey.log


which reads


```
2010-01-19 00:47:42,408 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xa3b34ac>
2010-01-19 00:47:42,416 DEBUG: reading modalias file /lib/modules/2.6.31-17-generic/modules.alias
2010-01-19 00:47:42,909 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-01-19 00:47:42,912 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-01-19 00:47:43,074 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-01-19 00:47:43,079 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2010-01-19 00:47:43,092 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-185
2010-01-19 00:47:43,107 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2010-01-19 00:47:43,115 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2010-01-19 00:47:43,121 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2010-01-19 00:47:43,155 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-01-19 00:47:43,157 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2010-01-19 00:47:43,196 DEBUG: ATI/AMD proprietary FGLRX graphics driver not available
2010-01-19 00:47:43,197 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2010-01-19 00:47:43,221 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2010-01-19 00:47:43,256 DEBUG: Software modem not available
2010-01-19 00:47:43,257 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2010-01-19 00:47:43,304 WARNING: modinfo for module nvidia failed: ERROR: modinfo: could not find module nvidia

2010-01-19 00:47:43,306 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver from name NvidiaDriver
2010-01-19 00:47:43,307 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-01-19 00:47:43,308 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2010-01-19 00:47:43,398 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2010-01-19 00:47:43,400 DEBUG: Firmware for DVB cards not available
2010-01-19 00:47:43,401 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2010-01-19 00:47:43,417 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2010-01-19 00:47:43,419 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2010-01-19 00:47:43,420 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2010-01-19 00:47:43,421 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2010-01-19 00:47:43,445 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-01-19 00:47:43,473 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2010-01-19 00:47:43,474 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2010-01-19 00:47:43,474 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2010-01-19 00:47:43,533 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2010-01-19 00:47:43,534 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2010-01-19 00:47:43,556 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2010-01-19 00:47:43,557 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2010-01-19 00:47:43,558 DEBUG: all custom handlers loaded
2010-01-19 00:47:43,559 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa3b34ac> about HardwareID('modalias', 'pci:v00008086d000027A6sv0000103Csd0000308Fbc03sc80i00')
2010-01-19 00:47:44,371 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa3b34ac> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-01-19 00:47:44,833 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-19 00:47:44,833 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa3b34ac> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2010-01-19 00:47:44,834 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa3b34ac> about HardwareID('modalias', 'acpi:PNP0200:')
2010-01-19 00:47:44,834 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa3b34ac> about HardwareID('modalias', 'pci:v00008086d000027D8sv0000103Csd0000308Fbc04sc03i00')
2010-01-19 00:47:44,846 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2010-01-19 00:47:44,847 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa3b34ac> about HardwareID('modalias', 'input:b0001v111Dp7605e0001-e0,12,kramls1,2,fw')
2010-01-19 00:47:44,848 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-19 00:47:44,848 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa3b34ac> about HardwareID('modalias', 'platform:pcspkr')
2010-01-19 00:47:44,850 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2010-01-19 00:47:44,850 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2010-01-19 00:47:44,850 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa3b34ac> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-01-19 00:47:44,947 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa3b34ac> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-01-19 00:47:44,947 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-19 00:47:44,948 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa3b34ac> about HardwareID('modalias', 'acpi:SYN1E0C:SYN1E00:SYN0002:PNP0F13:')
2010-01-19 00:47:44,948 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa3b34ac> about HardwareID('modalias', 'platform:eisa')
2010-01-19 00:47:44,950 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa3b34ac> about HardwareID('modalias', 'pci:v00008086d000027CCsv0000103Csd0000308Fbc0Csc03i20')
2010-01-19 00:47:44,960 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa3b34ac> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-01-19 00:47:44,962 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa3b34ac> about HardwareID('modalias', 'pci:v00008086d000027ACsv0000103Csd0000308Fbc06sc00i00')
2010-01-19 00:47:44,972 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_agp', 'jockey_handler': 'KernelModuleHandler'}
2010-01-19 00:47:44,973 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa3b34ac> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-01-19 00:47:44,973 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa3b34ac> about HardwareID('modalias', 'acpi:PNP0800:')
2010-01-19 00:47:44,974 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa3b34ac> about HardwareID('modalias', 'pci:v00008086d000027AEsv0000103Csd0000308Fbc03sc00i00')
2010-01-19 00:47:44,984 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2010-01-19 00:47:44,985 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa3b34ac> about HardwareID('modalias', 'acpi:PNP0000:')
2010-01-19 00:47:44,985 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa3b34ac> about HardwareID('modalias', 'pci:v00001969d00001062sv0000103Csd0000308Fbc02sc00i00')
2010-01-19 00:47:44,997 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'atl1c', 'jockey_handler': 'KernelModuleHandler'}
2010-01-19 00:47:44,998 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa3b34ac> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-01-19 00:47:44,998 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa3b34ac> about HardwareID('modalias', 'acpi:PNP0103:')
2010-01-19 00:47:44,998 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa3b34ac> about HardwareID('modalias', 'usb:v10F1p1A0Fd2308dcEFdsc02dp01ic0Eisc01ip00')
2010-01-19 00:47:45,000 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2010-01-19 00:47:45,001 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa3b34ac> about HardwareID('modalias', 'pci:v00008086d000027C9sv0000103Csd0000308Fbc0Csc03i00')
2010-01-19 00:47:45,011 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa3b34ac> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-01-19 00:47:45,012 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-19 00:47:45,013 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa3b34ac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-01-19 00:47:45,013 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-19 00:47:45,014 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa3b34ac> about HardwareID('modalias', 'input:b0003v10F1p1A0Fe2308-e0,1,kD4,ramlsfw')
2010-01-19 00:47:45,014 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-19 00:47:45,015 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa3b34ac> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-01-19 00:47:45,016 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-19 00:47:45,016 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa3b34ac> about HardwareID('modalias', 'pci:v00008086d000027C8sv0000103Csd0000308Fbc0Csc03i00')
2010-01-19 00:47:45,027 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa3b34ac> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvr308F0Ver.F.05:bd05/11/2009:svnHewlett-Packard:pnHPMini110-1000:pvr03A8100000000000100300000:rvnHewlett-Packard:rn308F:rvrKBCVersion02.09:cvnHewlett-Packard:ct10:cvr:')
2010-01-19 00:47:45,078 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa3b34ac> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-01-19 00:47:45,078 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa3b34ac> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-01-19 00:47:45,079 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-19 00:47:45,080 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa3b34ac> about HardwareID('modalias', 'usb:v0461p4D0Fd0200dc00dsc00dp00ic03isc01ip02')
2010-01-19 00:47:45,090 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2010-01-19 00:47:45,091 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa3b34ac> about HardwareID('modalias', 'usb:v046DpC315d2800dc00dsc00dp00ic03isc01ip01')
2010-01-19 00:47:45,224 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2010-01-19 00:47:45,224 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa3b34ac> about HardwareID('modalias', 'acpi:PNP0C01:')
2010-01-19 00:47:45,225 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa3b34ac> about HardwareID('modalias', 'input:b0003v046DpC315e0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2010-01-19 00:47:45,226 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-19 00:47:45,226 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa3b34ac> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-01-19 00:47:45,226 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa3b34ac> about HardwareID('modalias', 'pci:v00008086d000027DAsv0000103Csd0000308Fbc0Csc05i00')
2010-01-19 00:47:45,237 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2010-01-19 00:47:45,238 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa3b34ac> about HardwareID('modalias', 'usb:v10F1p1A0Fd2308dcEFdsc02dp01ic0Eisc02ip00')
2010-01-19 00:47:45,239 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa3b34ac> about HardwareID('modalias', 'pci:v000014E4d00004315sv0000103Csd00001507bc02sc80i00')
2010-01-19 00:47:45,414 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ssb', 'jockey_handler': 'KernelModuleHandler'}
2010-01-19 00:47:45,420 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-01-19 00:47:45,422 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-01-19 00:47:45,421 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2010-01-19 00:47:45,423 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa3b34ac> about HardwareID('modalias', 'pci:v00008086d000027B9sv0000103Csd0000308Fbc06sc01i00')
2010-01-19 00:47:45,435 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_rng', 'jockey_handler': 'KernelModuleHandler'}
2010-01-19 00:47:45,436 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2010-01-19 00:47:45,436 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa3b34ac> about HardwareID('modalias', 'pci:v00008086d000027CAsv0000103Csd0000308Fbc0Csc03i00')
2010-01-19 00:47:45,447 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa3b34ac> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2010-01-19 00:47:45,448 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-19 00:47:45,449 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa3b34ac> about HardwareID('modalias', 'acpi:PNP0100:')
2010-01-19 00:47:45,449 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa3b34ac> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-01-19 00:47:45,451 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa3b34ac> about HardwareID('modalias', 'pci:v00008086d000027CBsv0000103Csd0000308Fbc0Csc03i00')
2010-01-19 00:47:45,462 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa3b34ac> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-01-19 00:47:45,499 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2010-01-19 00:47:45,500 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2010-01-19 00:47:45,500 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa3b34ac> about HardwareID('modalias', 'input:b0003v0461p4D0Fe0111-e0,1,2,4,k110,111,112,r0,1,6,8,am4,lsfw')
2010-01-19 00:47:45,502 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-19 00:47:45,502 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa3b34ac> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-01-19 00:47:45,515 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa3b34ac> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,112,145,14A,ra0,1,18,1C,mlsfw')
2010-01-19 00:47:45,516 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-01-19 00:47:45,517 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-01-19 00:47:45,517 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-19 00:47:45,517 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa3b34ac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2010-01-19 00:47:45,518 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-19 00:47:45,519 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa3b34ac> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-01-19 00:47:45,519 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa73bbac> about HardwareID('modalias', 'pci:v00008086d000027A6sv0000103Csd0000308Fbc03sc80i00')
2010-01-19 00:47:45,519 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa73bbac> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-01-19 00:47:45,520 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa73bbac> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2010-01-19 00:47:45,520 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa73bbac> about HardwareID('modalias', 'acpi:PNP0200:')
2010-01-19 00:47:45,521 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa73bbac> about HardwareID('modalias', 'pci:v00008086d000027D8sv0000103Csd0000308Fbc04sc03i00')
2010-01-19 00:47:45,521 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa73bbac> about HardwareID('modalias', 'input:b0001v111Dp7605e0001-e0,12,kramls1,2,fw')
2010-01-19 00:47:45,521 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa73bbac> about HardwareID('modalias', 'platform:pcspkr')
2010-01-19 00:47:45,522 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa73bbac> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-01-19 00:47:45,522 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa73bbac> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-01-19 00:47:45,523 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa73bbac> about HardwareID('modalias', 'acpi:SYN1E0C:SYN1E00:SYN0002:PNP0F13:')
2010-01-19 00:47:45,523 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa73bbac> about HardwareID('modalias', 'platform:eisa')
2010-01-19 00:47:45,523 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa73bbac> about HardwareID('modalias', 'pci:v00008086d000027CCsv0000103Csd0000308Fbc0Csc03i20')
2010-01-19 00:47:45,524 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa73bbac> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-01-19 00:47:45,524 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa73bbac> about HardwareID('modalias', 'pci:v00008086d000027ACsv0000103Csd0000308Fbc06sc00i00')
2010-01-19 00:47:45,525 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa73bbac> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-01-19 00:47:45,525 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa73bbac> about HardwareID('modalias', 'acpi:PNP0800:')
2010-01-19 00:47:45,525 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa73bbac> about HardwareID('modalias', 'pci:v00008086d000027AEsv0000103Csd0000308Fbc03sc00i00')
2010-01-19 00:47:45,526 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa73bbac> about HardwareID('modalias', 'acpi:PNP0000:')
2010-01-19 00:47:45,526 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa73bbac> about HardwareID('modalias', 'pci:v00001969d00001062sv0000103Csd0000308Fbc02sc00i00')
2010-01-19 00:47:45,526 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa73bbac> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-01-19 00:47:45,527 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa73bbac> about HardwareID('modalias', 'acpi:PNP0103:')
2010-01-19 00:47:45,527 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa73bbac> about HardwareID('modalias', 'usb:v10F1p1A0Fd2308dcEFdsc02dp01ic0Eisc01ip00')
2010-01-19 00:47:45,527 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa73bbac> about HardwareID('modalias', 'pci:v00008086d000027C9sv0000103Csd0000308Fbc0Csc03i00')
2010-01-19 00:47:45,528 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa73bbac> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-01-19 00:47:45,528 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa73bbac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-01-19 00:47:45,529 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa73bbac> about HardwareID('modalias', 'input:b0003v10F1p1A0Fe2308-e0,1,kD4,ramlsfw')
2010-01-19 00:47:45,529 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa73bbac> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-01-19 00:47:45,529 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa73bbac> about HardwareID('modalias', 'pci:v00008086d000027C8sv0000103Csd0000308Fbc0Csc03i00')
2010-01-19 00:47:45,530 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa73bbac> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvr308F0Ver.F.05:bd05/11/2009:svnHewlett-Packard:pnHPMini110-1000:pvr03A8100000000000100300000:rvnHewlett-Packard:rn308F:rvrKBCVersion02.09:cvnHewlett-Packard:ct10:cvr:')
2010-01-19 00:47:45,530 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa73bbac> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-01-19 00:47:45,530 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa73bbac> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-01-19 00:47:45,531 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa73bbac> about HardwareID('modalias', 'usb:v0461p4D0Fd0200dc00dsc00dp00ic03isc01ip02')
2010-01-19 00:47:45,531 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa73bbac> about HardwareID('modalias', 'usb:v046DpC315d2800dc00dsc00dp00ic03isc01ip01')
2010-01-19 00:47:45,532 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa73bbac> about HardwareID('modalias', 'acpi:PNP0C01:')
2010-01-19 00:47:45,532 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa73bbac> about HardwareID('modalias', 'input:b0003v046DpC315e0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2010-01-19 00:47:45,533 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa73bbac> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-01-19 00:47:45,533 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa73bbac> about HardwareID('modalias', 'pci:v00008086d000027DAsv0000103Csd0000308Fbc0Csc05i00')
2010-01-19 00:47:45,533 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa73bbac> about HardwareID('modalias', 'usb:v10F1p1A0Fd2308dcEFdsc02dp01ic0Eisc02ip00')
2010-01-19 00:47:45,534 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa73bbac> about HardwareID('modalias', 'pci:v000014E4d00004315sv0000103Csd00001507bc02sc80i00')
2010-01-19 00:47:45,534 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa73bbac> about HardwareID('modalias', 'pci:v00008086d000027B9sv0000103Csd0000308Fbc06sc01i00')
2010-01-19 00:47:45,535 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa73bbac> about HardwareID('modalias', 'pci:v00008086d000027CAsv0000103Csd0000308Fbc0Csc03i00')
2010-01-19 00:47:45,535 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa73bbac> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2010-01-19 00:47:45,535 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa73bbac> about HardwareID('modalias', 'acpi:PNP0100:')
2010-01-19 00:47:45,536 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa73bbac> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-01-19 00:47:45,536 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa73bbac> about HardwareID('modalias', 'pci:v00008086d000027CBsv0000103Csd0000308Fbc0Csc03i00')
2010-01-19 00:47:45,536 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa73bbac> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-01-19 00:47:45,537 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa73bbac> about HardwareID('modalias', 'input:b0003v0461p4D0Fe0111-e0,1,2,4,k110,111,112,r0,1,6,8,am4,lsfw')
2010-01-19 00:47:45,537 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa73bbac> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-01-19 00:47:45,538 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa73bbac> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,112,145,14A,ra0,1,18,1C,mlsfw')
2010-01-19 00:47:45,538 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa73bbac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2010-01-19 00:47:45,538 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa73bbac> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-01-19 00:47:45,712 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-01-19 00:47:45,976 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-01-19 00:47:46,059 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-01-19 00:47:50,112 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-01-19 00:47:54,463 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-01-19 00:47:54,464 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2010-01-19 00:47:54,504 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-01-19 00:48:07,564 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-01-19 00:48:07,615 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-01-19 00:48:07,709 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-01-19 00:50:19,133 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-01-19 00:50:19,329 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-01-19 00:50:19,406 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-01-19 00:50:22,031 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-01-19 00:50:25,585 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-01-19 00:50:25,586 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2010-01-19 00:50:25,620 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-01-19 00:50:27,568 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-01-19 00:50:27,641 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-01-19 00:50:27,723 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-01-19 00:51:30,400 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-01-19 00:51:30,596 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-01-19 00:51:30,705 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-01-19 00:51:32,513 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-01-19 00:51:36,231 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-01-19 00:51:36,233 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2010-01-19 00:51:36,312 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-01-19 00:54:43,838 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-01-19 00:54:43,897 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-01-19 00:54:43,979 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-01-19 00:54:45,407 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-01-19 00:54:48,904 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-01-19 00:54:48,906 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2010-01-19 00:54:48,991 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-01-19 00:54:50,354 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-01-19 00:54:50,418 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-01-19 00:54:50,527 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-01-19 01:08:53,149 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x929a4ac>
2010-01-19 01:08:53,152 DEBUG: reading modalias file /lib/modules/2.6.31-17-generic/modules.alias
2010-01-19 01:08:53,991 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-01-19 01:08:53,992 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-01-19 01:08:54,240 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-01-19 01:08:54,246 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2010-01-19 01:08:54,259 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-185
2010-01-19 01:08:54,277 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2010-01-19 01:08:54,286 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2010-01-19 01:08:54,288 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2010-01-19 01:08:54,313 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-01-19 01:08:54,314 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2010-01-19 01:08:54,335 DEBUG: ATI/AMD proprietary FGLRX graphics driver not available
2010-01-19 01:08:54,336 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2010-01-19 01:08:54,392 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2010-01-19 01:08:54,421 DEBUG: Software modem not available
2010-01-19 01:08:54,422 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2010-01-19 01:08:54,440 WARNING: modinfo for module nvidia failed: ERROR: modinfo: could not find module nvidia

2010-01-19 01:08:54,441 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver from name NvidiaDriver
2010-01-19 01:08:54,441 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-01-19 01:08:54,442 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2010-01-19 01:08:54,484 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2010-01-19 01:08:54,486 DEBUG: Firmware for DVB cards not available
2010-01-19 01:08:54,486 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2010-01-19 01:08:54,506 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2010-01-19 01:08:54,507 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2010-01-19 01:08:54,508 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2010-01-19 01:08:54,508 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2010-01-19 01:08:54,524 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-01-19 01:08:54,563 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2010-01-19 01:08:54,564 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2010-01-19 01:08:54,565 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2010-01-19 01:08:54,611 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2010-01-19 01:08:54,612 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2010-01-19 01:08:54,638 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2010-01-19 01:08:54,639 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2010-01-19 01:08:54,640 DEBUG: all custom handlers loaded
2010-01-19 01:08:54,640 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x929a4ac> about HardwareID('modalias', 'pci:v00008086d000027A6sv0000103Csd0000308Fbc03sc80i00')
2010-01-19 01:08:55,866 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x929a4ac> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-01-19 01:08:56,302 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-19 01:08:56,303 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x929a4ac> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2010-01-19 01:08:56,303 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x929a4ac> about HardwareID('modalias', 'acpi:PNP0200:')
2010-01-19 01:08:56,304 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x929a4ac> about HardwareID('modalias', 'pci:v00008086d000027D8sv0000103Csd0000308Fbc04sc03i00')
2010-01-19 01:08:56,318 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2010-01-19 01:08:56,319 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x929a4ac> about HardwareID('modalias', 'input:b0001v111Dp7605e0001-e0,12,kramls1,2,fw')
2010-01-19 01:08:56,320 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-19 01:08:56,320 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x929a4ac> about HardwareID('modalias', 'platform:pcspkr')
2010-01-19 01:08:56,322 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2010-01-19 01:08:56,323 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2010-01-19 01:08:56,324 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x929a4ac> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-01-19 01:08:56,455 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x929a4ac> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-01-19 01:08:56,456 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-19 01:08:56,456 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x929a4ac> about HardwareID('modalias', 'acpi:SYN1E0C:SYN1E00:SYN0002:PNP0F13:')
2010-01-19 01:08:56,457 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x929a4ac> about HardwareID('modalias', 'platform:eisa')
2010-01-19 01:08:56,459 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x929a4ac> about HardwareID('modalias', 'pci:v00008086d000027CCsv0000103Csd0000308Fbc0Csc03i20')
2010-01-19 01:08:56,473 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x929a4ac> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-01-19 01:08:56,475 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x929a4ac> about HardwareID('modalias', 'pci:v00008086d000027ACsv0000103Csd0000308Fbc06sc00i00')
2010-01-19 01:08:56,489 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_agp', 'jockey_handler': 'KernelModuleHandler'}
2010-01-19 01:08:56,490 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x929a4ac> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-01-19 01:08:56,490 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x929a4ac> about HardwareID('modalias', 'acpi:PNP0800:')
2010-01-19 01:08:56,491 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x929a4ac> about HardwareID('modalias', 'pci:v00008086d000027AEsv0000103Csd0000308Fbc03sc00i00')
2010-01-19 01:08:56,505 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2010-01-19 01:08:56,505 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x929a4ac> about HardwareID('modalias', 'acpi:PNP0000:')
2010-01-19 01:08:56,506 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x929a4ac> about HardwareID('modalias', 'pci:v00001969d00001062sv0000103Csd0000308Fbc02sc00i00')
2010-01-19 01:08:56,520 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'atl1c', 'jockey_handler': 'KernelModuleHandler'}
2010-01-19 01:08:56,521 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x929a4ac> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-01-19 01:08:56,521 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x929a4ac> about HardwareID('modalias', 'acpi:PNP0103:')
2010-01-19 01:08:56,522 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x929a4ac> about HardwareID('modalias', 'usb:v10F1p1A0Fd2308dcEFdsc02dp01ic0Eisc01ip00')
2010-01-19 01:08:56,524 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2010-01-19 01:08:56,525 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x929a4ac> about HardwareID('modalias', 'pci:v00008086d000027C9sv0000103Csd0000308Fbc0Csc03i00')
2010-01-19 01:08:56,540 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x929a4ac> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-01-19 01:08:56,542 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-19 01:08:56,542 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x929a4ac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-01-19 01:08:56,543 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-19 01:08:56,544 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x929a4ac> about HardwareID('modalias', 'input:b0003v10F1p1A0Fe2308-e0,1,kD4,ramlsfw')
2010-01-19 01:08:56,544 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-19 01:08:56,545 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x929a4ac> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-01-19 01:08:56,546 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-19 01:08:56,546 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x929a4ac> about HardwareID('modalias', 'pci:v00008086d000027C8sv0000103Csd0000308Fbc0Csc03i00')
2010-01-19 01:08:56,562 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x929a4ac> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvr308F0Ver.F.05:bd05/11/2009:svnHewlett-Packard:pnHPMini110-1000:pvr03A8100000000000100300000:rvnHewlett-Packard:rn308F:rvrKBCVersion02.09:cvnHewlett-Packard:ct10:cvr:')
2010-01-19 01:08:56,631 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x929a4ac> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-01-19 01:08:56,631 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x929a4ac> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-01-19 01:08:56,633 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-19 01:08:56,634 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x929a4ac> about HardwareID('modalias', 'usb:v0461p4D0Fd0200dc00dsc00dp00ic03isc01ip02')
2010-01-19 01:08:56,646 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2010-01-19 01:08:56,647 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x929a4ac> about HardwareID('modalias', 'usb:v046DpC315d2800dc00dsc00dp00ic03isc01ip01')
2010-01-19 01:08:56,833 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2010-01-19 01:08:56,834 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x929a4ac> about HardwareID('modalias', 'acpi:PNP0C01:')
2010-01-19 01:08:56,834 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x929a4ac> about HardwareID('modalias', 'input:b0003v046DpC315e0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2010-01-19 01:08:56,835 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-19 01:08:56,836 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x929a4ac> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-01-19 01:08:56,836 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x929a4ac> about HardwareID('modalias', 'pci:v00008086d000027DAsv0000103Csd0000308Fbc0Csc05i00')
2010-01-19 01:08:56,850 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2010-01-19 01:08:56,851 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x929a4ac> about HardwareID('modalias', 'usb:v10F1p1A0Fd2308dcEFdsc02dp01ic0Eisc02ip00')
2010-01-19 01:08:56,855 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x929a4ac> about HardwareID('modalias', 'pci:v000014E4d00004315sv0000103Csd00001507bc02sc80i00')
2010-01-19 01:08:57,194 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ssb', 'jockey_handler': 'KernelModuleHandler'}
2010-01-19 01:08:57,203 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-01-19 01:08:57,205 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-01-19 01:08:57,204 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2010-01-19 01:08:57,206 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x929a4ac> about HardwareID('modalias', 'pci:v00008086d000027B9sv0000103Csd0000308Fbc06sc01i00')
2010-01-19 01:08:57,227 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_rng', 'jockey_handler': 'KernelModuleHandler'}
2010-01-19 01:08:57,228 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2010-01-19 01:08:57,228 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x929a4ac> about HardwareID('modalias', 'pci:v00008086d000027CAsv0000103Csd0000308Fbc0Csc03i00')
2010-01-19 01:08:57,243 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x929a4ac> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2010-01-19 01:08:57,244 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-19 01:08:57,245 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x929a4ac> about HardwareID('modalias', 'acpi:PNP0100:')
2010-01-19 01:08:57,245 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x929a4ac> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-01-19 01:08:57,248 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x929a4ac> about HardwareID('modalias', 'pci:v00008086d000027CBsv0000103Csd0000308Fbc0Csc03i00')
2010-01-19 01:08:57,261 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x929a4ac> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-01-19 01:08:57,309 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2010-01-19 01:08:57,310 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2010-01-19 01:08:57,310 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x929a4ac> about HardwareID('modalias', 'input:b0003v0461p4D0Fe0111-e0,1,2,4,k110,111,112,r0,1,6,8,am4,lsfw')
2010-01-19 01:08:57,311 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-19 01:08:57,312 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x929a4ac> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-01-19 01:08:57,330 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x929a4ac> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,112,145,14A,ra0,1,18,1C,mlsfw')
2010-01-19 01:08:57,331 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-01-19 01:08:57,332 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-01-19 01:08:57,333 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-19 01:08:57,333 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x929a4ac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2010-01-19 01:08:57,334 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-19 01:08:57,335 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x929a4ac> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-01-19 01:08:57,335 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9622bac> about HardwareID('modalias', 'pci:v00008086d000027A6sv0000103Csd0000308Fbc03sc80i00')
2010-01-19 01:08:57,337 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9622bac> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-01-19 01:08:57,337 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9622bac> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2010-01-19 01:08:57,338 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9622bac> about HardwareID('modalias', 'acpi:PNP0200:')
2010-01-19 01:08:57,339 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9622bac> about HardwareID('modalias', 'pci:v00008086d000027D8sv0000103Csd0000308Fbc04sc03i00')
2010-01-19 01:08:57,339 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9622bac> about HardwareID('modalias', 'input:b0001v111Dp7605e0001-e0,12,kramls1,2,fw')
2010-01-19 01:08:57,340 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9622bac> about HardwareID('modalias', 'platform:pcspkr')
2010-01-19 01:08:57,341 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9622bac> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-01-19 01:08:57,341 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9622bac> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-01-19 01:08:57,342 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9622bac> about HardwareID('modalias', 'acpi:SYN1E0C:SYN1E00:SYN0002:PNP0F13:')
2010-01-19 01:08:57,343 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9622bac> about HardwareID('modalias', 'platform:eisa')
2010-01-19 01:08:57,344 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9622bac> about HardwareID('modalias', 'pci:v00008086d000027CCsv0000103Csd0000308Fbc0Csc03i20')
2010-01-19 01:08:57,344 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9622bac> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-01-19 01:08:57,345 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9622bac> about HardwareID('modalias', 'pci:v00008086d000027ACsv0000103Csd0000308Fbc06sc00i00')
2010-01-19 01:08:57,345 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9622bac> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-01-19 01:08:57,346 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9622bac> about HardwareID('modalias', 'acpi:PNP0800:')
2010-01-19 01:08:57,346 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9622bac> about HardwareID('modalias', 'pci:v00008086d000027AEsv0000103Csd0000308Fbc03sc00i00')
2010-01-19 01:08:57,347 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9622bac> about HardwareID('modalias', 'acpi:PNP0000:')
2010-01-19 01:08:57,347 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9622bac> about HardwareID('modalias', 'pci:v00001969d00001062sv0000103Csd0000308Fbc02sc00i00')
2010-01-19 01:08:57,348 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9622bac> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-01-19 01:08:57,349 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9622bac> about HardwareID('modalias', 'acpi:PNP0103:')
2010-01-19 01:08:57,350 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9622bac> about HardwareID('modalias', 'usb:v10F1p1A0Fd2308dcEFdsc02dp01ic0Eisc01ip00')
2010-01-19 01:08:57,350 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9622bac> about HardwareID('modalias', 'pci:v00008086d000027C9sv0000103Csd0000308Fbc0Csc03i00')
2010-01-19 01:08:57,351 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9622bac> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-01-19 01:08:57,351 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9622bac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-01-19 01:08:57,352 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9622bac> about HardwareID('modalias', 'input:b0003v10F1p1A0Fe2308-e0,1,kD4,ramlsfw')
2010-01-19 01:08:57,352 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9622bac> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-01-19 01:08:57,353 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9622bac> about HardwareID('modalias', 'pci:v00008086d000027C8sv0000103Csd0000308Fbc0Csc03i00')
2010-01-19 01:08:57,353 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9622bac> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvr308F0Ver.F.05:bd05/11/2009:svnHewlett-Packard:pnHPMini110-1000:pvr03A8100000000000100300000:rvnHewlett-Packard:rn308F:rvrKBCVersion02.09:cvnHewlett-Packard:ct10:cvr:')
2010-01-19 01:08:57,354 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9622bac> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-01-19 01:08:57,354 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9622bac> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-01-19 01:08:57,354 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9622bac> about HardwareID('modalias', 'usb:v0461p4D0Fd0200dc00dsc00dp00ic03isc01ip02')
2010-01-19 01:08:57,355 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9622bac> about HardwareID('modalias', 'usb:v046DpC315d2800dc00dsc00dp00ic03isc01ip01')
2010-01-19 01:08:57,355 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9622bac> about HardwareID('modalias', 'acpi:PNP0C01:')
2010-01-19 01:08:57,356 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9622bac> about HardwareID('modalias', 'input:b0003v046DpC315e0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2010-01-19 01:08:57,356 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9622bac> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-01-19 01:08:57,357 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9622bac> about HardwareID('modalias', 'pci:v00008086d000027DAsv0000103Csd0000308Fbc0Csc05i00')
2010-01-19 01:08:57,357 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9622bac> about HardwareID('modalias', 'usb:v10F1p1A0Fd2308dcEFdsc02dp01ic0Eisc02ip00')
2010-01-19 01:08:57,358 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9622bac> about HardwareID('modalias', 'pci:v000014E4d00004315sv0000103Csd00001507bc02sc80i00')
2010-01-19 01:08:57,358 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9622bac> about HardwareID('modalias', 'pci:v00008086d000027B9sv0000103Csd0000308Fbc06sc01i00')
2010-01-19 01:08:57,358 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9622bac> about HardwareID('modalias', 'pci:v00008086d000027CAsv0000103Csd0000308Fbc0Csc03i00')
2010-01-19 01:08:57,359 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9622bac> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2010-01-19 01:08:57,359 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9622bac> about HardwareID('modalias', 'acpi:PNP0100:')
2010-01-19 01:08:57,361 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9622bac> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-01-19 01:08:57,361 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9622bac> about HardwareID('modalias', 'pci:v00008086d000027CBsv0000103Csd0000308Fbc0Csc03i00')
2010-01-19 01:08:57,362 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9622bac> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-01-19 01:08:57,363 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9622bac> about HardwareID('modalias', 'input:b0003v0461p4D0Fe0111-e0,1,2,4,k110,111,112,r0,1,6,8,am4,lsfw')
2010-01-19 01:08:57,363 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9622bac> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-01-19 01:08:57,364 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9622bac> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,112,145,14A,ra0,1,18,1C,mlsfw')
2010-01-19 01:08:57,364 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9622bac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2010-01-19 01:08:57,365 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9622bac> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-01-19 01:08:57,520 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-01-19 01:08:57,836 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-01-19 01:08:57,958 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-01-19 01:09:13,261 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-01-19 01:09:17,640 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-01-19 01:09:17,642 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2010-01-19 01:09:17,710 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
```

---

### Post by Cabs21 on 2010-01-19
when connected to the internet what is the output of 
```
ifconfig
```
and
```
iwconfig
```

when entered in the command line?

had this same problem with a broadcomm and kept choosing the wrong driver that looked like the correct one.

---

### Post by KrashKharma on 2010-01-19
ifconfig:

```


eth0      Link encap:Ethernet  HWaddr 00:24:81:6d:d4:ae  
          inet addr:IPIPIP  Bcast:IPIPIP  Mask:255.255.255.0
          inet6 addr: fe80::224:81ff:fe6d:d4ae/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:85977 errors:0 dropped:0 overruns:0 frame:0
          TX packets:90562 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:75737404 (75.7 MB)  TX bytes:22571134 (22.5 MB)
          Interrupt:26 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:168 errors:0 dropped:0 overruns:0 frame:0
          TX packets:168 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:20014 (20.0 KB)  TX bytes:20014 (20.0 KB)
```
iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

```

This really sucks because it seems like I'd  be able to fix the issue easily if I could just redirect the request to check /cdrom/ to checking my USB instead :(

---

### Post by KrashKharma on 2010-01-20
FIXED!




Note for anyone with an HP Mini having this problem (I know that's a lot of you if google is accurate...)

Just install Ubuntu while connected via ethernet and your drivers will be available and able to be activated when you start up for the first time :)

---

