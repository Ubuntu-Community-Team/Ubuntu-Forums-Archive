---
title: "wireless stopped working after kubuntu uninstall"
date: 2010-01-24
forum: Networking &amp; Wireless
---

### Post by Docaltmed on 2010-01-24
I briefly installed kubuntu to see what it was like these days. After checking it out, I uninstalled it. When I rebooted into ubuntu, I no longer had wireless connection. Looking at the hardware drivers, the Broadcomm STA wireless driver was not activated. When I told it to activate this driver, it gave me an error message with details in jockey.log.

Here's the jockey.log file. I don't understand anything except for the fact that it looks like the Broadcomm drivers were blacklisted for some reason.

Can someone help me figure this out? I've got to have wireless back for work monday morning! Thanks.

(sorry for the long post. The forum would not let me append this as a .txt file)

```

2010-01-24 12:02:21,791 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a335ec>
2010-01-24 12:02:21,793 DEBUG: reading modalias file /lib/modules/2.6.31-17-generic-pae/modules.alias
2010-01-24 12:02:22,117 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-01-24 12:02:22,123 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-01-24 12:02:22,231 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2010-01-24 12:02:22,238 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-185
2010-01-24 12:02:22,250 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2010-01-24 12:02:22,259 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2010-01-24 12:02:22,260 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2010-01-24 12:02:23,712 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2010-01-24 12:02:23,778 DEBUG: Software modem is available
2010-01-24 12:02:23,779 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2010-01-24 12:02:23,979 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2010-01-24 12:02:23,980 DEBUG: Firmware for DVB cards not available
2010-01-24 12:02:23,980 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2010-01-24 12:02:24,039 WARNING: modinfo for module nvidia failed: ERROR: modinfo: could not find module nvidia

2010-01-24 12:02:24,058 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver from name NvidiaDriver
2010-01-24 12:02:24,058 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-01-24 12:02:24,058 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2010-01-24 12:02:24,378 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2010-01-24 12:02:24,379 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2010-01-24 12:02:24,431 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2010-01-24 12:02:24,431 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2010-01-24 12:02:24,431 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2010-01-24 12:02:24,461 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-01-24 12:02:24,595 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2010-01-24 12:02:24,597 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2010-01-24 12:02:24,597 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2010-01-24 12:02:24,618 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-01-24 12:02:24,623 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2010-01-24 12:02:24,692 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2010-01-24 12:02:24,692 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2010-01-24 12:02:24,702 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2010-01-24 12:02:24,704 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2010-01-24 12:02:24,704 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2010-01-24 12:02:24,704 DEBUG: all custom handlers loaded
2010-01-24 12:02:24,704 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a335ec> about HardwareID('modalias', 'pci:v00001002d00009612sv0000103Csd000030F1bc03sc00i00')
2010-01-24 12:02:25,804 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2010-01-24 12:02:25,804 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a335ec> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-01-24 12:02:25,813 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-24 12:02:25,813 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a335ec> about HardwareID('modalias', 'pci:v00001022d00001303sv00000000sd00000000bc06sc00i00')
2010-01-24 12:02:25,842 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a335ec> about HardwareID('modalias', 'pci:v00001022d00001301sv00000000sd00000000bc06sc00i00')
2010-01-24 12:02:25,843 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a335ec> about HardwareID('modalias', 'acpi:PNP0000:')
2010-01-24 12:02:25,843 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a335ec> about HardwareID('modalias', 'acpi:PNP0103:')
2010-01-24 12:02:25,844 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a335ec> about HardwareID('modalias', 'pci:v000014E4d0000432Bsv0000103Csd0000137Fbc02sc80i00')
2010-01-24 12:02:25,977 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ssb', 'jockey_handler': 'KernelModuleHandler'}
2010-01-24 12:02:25,984 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-01-24 12:02:25,985 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-01-24 12:02:25,984 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2010-01-24 12:02:25,985 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a335ec> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-01-24 12:02:25,986 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-24 12:02:25,986 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a335ec> about HardwareID('modalias', 'platform:eisa')
2010-01-24 12:02:25,987 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a335ec> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-01-24 12:02:26,050 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a335ec> about HardwareID('modalias', 'pci:v00001022d00001304sv00000000sd00000000bc06sc00i00')
2010-01-24 12:02:26,051 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a335ec> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,5,k8A,94,E0,E1,E2,166,ramlsfw1,5,')
2010-01-24 12:02:26,051 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-24 12:02:26,052 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a335ec> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-01-24 12:02:26,052 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a335ec> about HardwareID('modalias', 'platform:hp-wmi')
2010-01-24 12:02:26,052 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a335ec> about HardwareID('modalias', 'pci:v00001002d00004385sv0000103Csd000030F1bc0Csc05i00')
2010-01-24 12:02:26,060 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2010-01-24 12:02:26,060 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a335ec> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-01-24 12:02:26,061 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a335ec> about HardwareID('modalias', 'pci:v00001022d00001302sv00000000sd00000000bc06sc00i00')
2010-01-24 12:02:26,062 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a335ec> about HardwareID('modalias', 'pci:v00001022d00009600sv0000103Csd000030F1bc06sc00i00')
2010-01-24 12:02:26,063 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a335ec> about HardwareID('modalias', 'usb:v04F2pB09Bd6756dcEFdsc02dp01ic0Eisc02ip00')
2010-01-24 12:02:26,065 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a335ec> about HardwareID('modalias', 'acpi:PNP0C01:')
2010-01-24 12:02:26,065 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a335ec> about HardwareID('modalias', 'acpi:PNP0800:')
2010-01-24 12:02:26,066 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a335ec> about HardwareID('modalias', 'pci:v00001022d00009602sv00000000sd00000000bc06sc04i00')
2010-01-24 12:02:26,066 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'shpchp', 'jockey_handler': 'KernelModuleHandler'}
2010-01-24 12:02:26,067 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a335ec> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2010-01-24 12:02:26,067 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a335ec> about HardwareID('modalias', 'acpi:ENE0100:')
2010-01-24 12:02:26,067 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a335ec> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-01-24 12:02:26,067 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a335ec> about HardwareID('modalias', 'acpi:PNP0303:')
2010-01-24 12:02:26,068 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a335ec> about HardwareID('modalias', 'usb:v03F0p171Dd0100dcE0dsc01dp01icFFiscFFipFF')
2010-01-24 12:02:26,107 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2010-01-24 12:02:26,107 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a335ec> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-01-24 12:02:26,108 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a335ec> about HardwareID('modalias', 'pci:v00001022d00001300sv00000000sd00000000bc06sc00i00')
2010-01-24 12:02:26,108 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a335ec> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-01-24 12:02:26,109 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-24 12:02:26,109 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a335ec> about HardwareID('modalias', 'input:b0003v04F2pB09Be6756-e0,1,kD4,ramlsfw')
2010-01-24 12:02:26,109 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-24 12:02:26,110 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a335ec> about HardwareID('modalias', 'usb:v04F2pB09Bd6756dcEFdsc02dp01ic0Eisc01ip00')
2010-01-24 12:02:26,111 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2010-01-24 12:02:26,111 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a335ec> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,112,145,14A,ra0,1,18,1C,mlsfw')
2010-01-24 12:02:26,112 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-01-24 12:02:26,112 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-01-24 12:02:26,112 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-24 12:02:26,112 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a335ec> about HardwareID('modalias', 'acpi:PNP0C32:')
2010-01-24 12:02:26,113 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a335ec> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvrF.06:bd07/08/2008:svnHewlett-Packard:pnHPPaviliontx2500NotebookPC:pvrRev1:rvnQuanta:rn30F1:rvr97.18:cvnQuanta:ct10:cvrN/A:')
2010-01-24 12:02:26,147 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a335ec> about HardwareID('modalias', 'usb:v056Ap0093d0403dc00dsc00dp00ic03isc00ip00')
2010-01-24 12:02:26,222 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'wacom', 'jockey_handler': 'KernelModuleHandler'}
2010-01-24 12:02:26,223 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2010-01-24 12:02:26,223 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a335ec> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-01-24 12:02:26,223 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a335ec> about HardwareID('modalias', 'usb:v056Ap0093d0403dc00dsc00dp00ic03isc01ip02')
2010-01-24 12:02:26,225 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'wacom', 'jockey_handler': 'KernelModuleHandler'}
2010-01-24 12:02:26,226 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2010-01-24 12:02:26,226 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a335ec> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-01-24 12:02:26,226 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-24 12:02:26,226 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a335ec> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-01-24 12:02:26,228 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a335ec> about HardwareID('modalias', 'usb:v0BDAp0158d5887dc00dsc00dp00ic08isc06ip50')
2010-01-24 12:02:26,243 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2010-01-24 12:02:26,245 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a335ec> about HardwareID('modalias', 'acpi:SYN014C:SYN0100:SYN0002:PNP0F13:')
2010-01-24 12:02:26,245 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a335ec> about HardwareID('modalias', 'acpi:PNP0100:')
2010-01-24 12:02:26,245 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a335ec> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2010-01-24 12:02:26,252 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a335ec> about HardwareID('modalias', 'usb:v03F0p171Dd0100dcE0dsc01dp01icFEisc01ip00')
2010-01-24 12:02:26,253 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2010-01-24 12:02:26,254 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a335ec> about HardwareID('modalias', 'pci:v000010ECd00008168sv0000103Csd000030F1bc02sc00i00')
2010-01-24 12:02:26,268 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2010-01-24 12:02:26,268 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a335ec> about HardwareID('modalias', 'pci:v00001002d0000439Dsv0000103Csd000030F1bc06sc01i00')
2010-01-24 12:02:26,274 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a335ec> about HardwareID('modalias', 'pci:v00001002d00004391sv0000103Csd000030F1bc01sc06i01')
2010-01-24 12:02:26,281 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a335ec> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2010-01-24 12:02:26,282 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-24 12:02:26,282 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a335ec> about HardwareID('modalias', 'acpi:PNP0200:')
2010-01-24 12:02:26,282 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a335ec> about HardwareID('modalias', 'usb:v03F0p171Dd0100dcE0dsc01dp01icE0isc01ip01')
2010-01-24 12:02:26,284 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2010-01-24 12:02:26,284 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a335ec> about HardwareID('modalias', 'pci:v00001002d00004396sv0000103Csd000030F1bc0Csc03i20')
2010-01-24 12:02:26,298 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a335ec> about HardwareID('modalias', 'platform:pcspkr')
2010-01-24 12:02:26,299 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2010-01-24 12:02:26,299 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2010-01-24 12:02:26,300 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a335ec> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-01-24 12:02:26,328 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2010-01-24 12:02:26,329 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2010-01-24 12:02:26,329 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a335ec> about HardwareID('modalias', 'usb:v08FFp1600d0C10dcFFdscFFdpFFicFFiscFFipFF')
2010-01-24 12:02:26,330 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a335ec> about HardwareID('modalias', 'input:b0003v056Ap0093e0403-e0,1,3,k140,141,14A,14B,14C,14D,ra0,1,3,4,18,28,mlsfw')
2010-01-24 12:02:26,330 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-01-24 12:02:26,331 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-01-24 12:02:26,331 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-24 12:02:26,331 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a335ec> about HardwareID('modalias', 'pci:v00001002d00004383sv0000103Csd000030F1bc04sc03i00')
2010-01-24 12:02:26,338 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2010-01-24 12:02:26,338 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2010-01-24 12:02:26,338 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a335ec> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-01-24 12:02:26,340 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-24 12:02:26,340 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a335ec> about HardwareID('modalias', 'input:b0001v10ECp0268e0001-e0,12,kramls1,2,fw')
2010-01-24 12:02:26,340 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-24 12:02:26,340 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a335ec> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-01-24 12:02:26,341 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8db14ec> about HardwareID('modalias', 'pci:v00001002d00009612sv0000103Csd000030F1bc03sc00i00')
2010-01-24 12:02:26,341 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8db14ec> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-01-24 12:02:26,341 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8db14ec> about HardwareID('modalias', 'pci:v00001022d00001303sv00000000sd00000000bc06sc00i00')
2010-01-24 12:02:26,341 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8db14ec> about HardwareID('modalias', 'pci:v00001022d00001301sv00000000sd00000000bc06sc00i00')
2010-01-24 12:02:26,342 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8db14ec> about HardwareID('modalias', 'acpi:PNP0000:')
2010-01-24 12:02:26,342 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8db14ec> about HardwareID('modalias', 'acpi:PNP0103:')
2010-01-24 12:02:26,342 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8db14ec> about HardwareID('modalias', 'pci:v000014E4d0000432Bsv0000103Csd0000137Fbc02sc80i00')
2010-01-24 12:02:26,342 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8db14ec> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-01-24 12:02:26,342 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8db14ec> about HardwareID('modalias', 'platform:eisa')
2010-01-24 12:02:26,343 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8db14ec> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-01-24 12:02:26,343 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8db14ec> about HardwareID('modalias', 'pci:v00001022d00001304sv00000000sd00000000bc06sc00i00')
2010-01-24 12:02:26,343 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8db14ec> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,5,k8A,94,E0,E1,E2,166,ramlsfw1,5,')
2010-01-24 12:02:26,343 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8db14ec> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-01-24 12:02:26,344 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8db14ec> about HardwareID('modalias', 'platform:hp-wmi')
2010-01-24 12:02:26,344 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8db14ec> about HardwareID('modalias', 'pci:v00001002d00004385sv0000103Csd000030F1bc0Csc05i00')
2010-01-24 12:02:26,344 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8db14ec> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-01-24 12:02:26,344 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8db14ec> about HardwareID('modalias', 'pci:v00001022d00001302sv00000000sd00000000bc06sc00i00')
2010-01-24 12:02:26,344 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8db14ec> about HardwareID('modalias', 'pci:v00001022d00009600sv0000103Csd000030F1bc06sc00i00')
2010-01-24 12:02:26,345 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8db14ec> about HardwareID('modalias', 'usb:v04F2pB09Bd6756dcEFdsc02dp01ic0Eisc02ip00')
2010-01-24 12:02:26,345 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8db14ec> about HardwareID('modalias', 'acpi:PNP0C01:')
2010-01-24 12:02:26,345 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8db14ec> about HardwareID('modalias', 'acpi:PNP0800:')
2010-01-24 12:02:26,345 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8db14ec> about HardwareID('modalias', 'pci:v00001022d00009602sv00000000sd00000000bc06sc04i00')
2010-01-24 12:02:26,346 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8db14ec> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2010-01-24 12:02:26,346 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8db14ec> about HardwareID('modalias', 'acpi:ENE0100:')
2010-01-24 12:02:26,346 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8db14ec> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-01-24 12:02:26,346 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8db14ec> about HardwareID('modalias', 'acpi:PNP0303:')
2010-01-24 12:02:26,346 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8db14ec> about HardwareID('modalias', 'usb:v03F0p171Dd0100dcE0dsc01dp01icFFiscFFipFF')
2010-01-24 12:02:26,347 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8db14ec> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-01-24 12:02:26,347 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8db14ec> about HardwareID('modalias', 'pci:v00001022d00001300sv00000000sd00000000bc06sc00i00')
2010-01-24 12:02:26,347 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8db14ec> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-01-24 12:02:26,347 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8db14ec> about HardwareID('modalias', 'input:b0003v04F2pB09Be6756-e0,1,kD4,ramlsfw')
2010-01-24 12:02:26,348 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8db14ec> about HardwareID('modalias', 'usb:v04F2pB09Bd6756dcEFdsc02dp01ic0Eisc01ip00')
2010-01-24 12:02:26,348 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8db14ec> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,112,145,14A,ra0,1,18,1C,mlsfw')
2010-01-24 12:02:26,348 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8db14ec> about HardwareID('modalias', 'acpi:PNP0C32:')
2010-01-24 12:02:26,348 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8db14ec> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvrF.06:bd07/08/2008:svnHewlett-Packard:pnHPPaviliontx2500NotebookPC:pvrRev1:rvnQuanta:rn30F1:rvr97.18:cvnQuanta:ct10:cvrN/A:')
2010-01-24 12:02:26,348 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8db14ec> about HardwareID('modalias', 'usb:v056Ap0093d0403dc00dsc00dp00ic03isc00ip00')
2010-01-24 12:02:26,349 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8db14ec> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-01-24 12:02:26,349 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8db14ec> about HardwareID('modalias', 'usb:v056Ap0093d0403dc00dsc00dp00ic03isc01ip02')
2010-01-24 12:02:26,349 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8db14ec> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-01-24 12:02:26,349 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8db14ec> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-01-24 12:02:26,350 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8db14ec> about HardwareID('modalias', 'usb:v0BDAp0158d5887dc00dsc00dp00ic08isc06ip50')
2010-01-24 12:02:26,350 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8db14ec> about HardwareID('modalias', 'acpi:SYN014C:SYN0100:SYN0002:PNP0F13:')
2010-01-24 12:02:26,350 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8db14ec> about HardwareID('modalias', 'acpi:PNP0100:')
2010-01-24 12:02:26,350 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8db14ec> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2010-01-24 12:02:26,350 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8db14ec> about HardwareID('modalias', 'usb:v03F0p171Dd0100dcE0dsc01dp01icFEisc01ip00')
2010-01-24 12:02:26,351 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8db14ec> about HardwareID('modalias', 'pci:v000010ECd00008168sv0000103Csd000030F1bc02sc00i00')
2010-01-24 12:02:26,351 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8db14ec> about HardwareID('modalias', 'pci:v00001002d0000439Dsv0000103Csd000030F1bc06sc01i00')
2010-01-24 12:02:26,351 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8db14ec> about HardwareID('modalias', 'pci:v00001002d00004391sv0000103Csd000030F1bc01sc06i01')
2010-01-24 12:02:26,351 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8db14ec> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2010-01-24 12:02:26,352 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8db14ec> about HardwareID('modalias', 'acpi:PNP0200:')
2010-01-24 12:02:26,352 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8db14ec> about HardwareID('modalias', 'usb:v03F0p171Dd0100dcE0dsc01dp01icE0isc01ip01')
2010-01-24 12:02:26,352 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8db14ec> about HardwareID('modalias', 'pci:v00001002d00004396sv0000103Csd000030F1bc0Csc03i20')
2010-01-24 12:02:26,352 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8db14ec> about HardwareID('modalias', 'platform:pcspkr')
2010-01-24 12:02:26,352 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8db14ec> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-01-24 12:02:26,353 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8db14ec> about HardwareID('modalias', 'usb:v08FFp1600d0C10dcFFdscFFdpFFicFFiscFFipFF')
2010-01-24 12:02:26,353 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8db14ec> about HardwareID('modalias', 'input:b0003v056Ap0093e0403-e0,1,3,k140,141,14A,14B,14C,14D,ra0,1,3,4,18,28,mlsfw')
2010-01-24 12:02:26,353 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8db14ec> about HardwareID('modalias', 'pci:v00001002d00004383sv0000103Csd000030F1bc04sc03i00')
2010-01-24 12:02:26,353 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8db14ec> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-01-24 12:02:26,354 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8db14ec> about HardwareID('modalias', 'input:b0001v10ECp0268e0001-e0,12,kramls1,2,fw')
2010-01-24 12:02:26,354 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8db14ec> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-01-24 12:02:34,303 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-01-24 12:02:35,266 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-01-24 12:02:35,337 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-01-24 12:02:51,255 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-01-24 12:02:56,328 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-01-24 12:02:56,329 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2010-01-24 12:02:56,356 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-01-24 12:03:00,289 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-01-24 12:03:00,919 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-01-24 12:03:00,975 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-01-24 12:11:43,311 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c305ec>
2010-01-24 12:11:43,367 DEBUG: reading modalias file /lib/modules/2.6.31-17-generic-pae/modules.alias
2010-01-24 12:11:43,666 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-01-24 12:11:43,682 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-01-24 12:11:43,821 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2010-01-24 12:11:43,828 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-185
2010-01-24 12:11:43,835 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2010-01-24 12:11:43,849 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2010-01-24 12:11:43,851 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2010-01-24 12:11:44,396 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2010-01-24 12:11:44,472 DEBUG: Software modem is available
2010-01-24 12:11:44,473 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2010-01-24 12:11:44,671 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2010-01-24 12:11:44,673 DEBUG: Firmware for DVB cards not available
2010-01-24 12:11:44,673 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2010-01-24 12:11:44,747 WARNING: modinfo for module nvidia failed: ERROR: modinfo: could not find module nvidia

2010-01-24 12:11:44,750 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver from name NvidiaDriver
2010-01-24 12:11:44,750 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-01-24 12:11:44,750 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2010-01-24 12:11:44,956 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2010-01-24 12:11:44,956 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2010-01-24 12:11:44,990 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2010-01-24 12:11:44,991 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2010-01-24 12:11:44,992 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2010-01-24 12:11:45,026 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-01-24 12:11:45,148 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2010-01-24 12:11:45,149 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2010-01-24 12:11:45,149 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2010-01-24 12:11:45,184 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-01-24 12:11:45,190 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2010-01-24 12:11:45,277 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2010-01-24 12:11:45,278 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2010-01-24 12:11:45,301 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2010-01-24 12:11:45,302 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2010-01-24 12:11:45,302 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2010-01-24 12:11:45,302 DEBUG: all custom handlers loaded
2010-01-24 12:11:45,303 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c305ec> about HardwareID('modalias', 'pci:v00001002d00009612sv0000103Csd000030F1bc03sc00i00')
2010-01-24 12:11:46,648 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2010-01-24 12:11:46,649 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c305ec> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-01-24 12:11:46,657 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-24 12:11:46,658 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c305ec> about HardwareID('modalias', 'pci:v00001022d00001303sv00000000sd00000000bc06sc00i00')
2010-01-24 12:11:46,689 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c305ec> about HardwareID('modalias', 'pci:v00001022d00001301sv00000000sd00000000bc06sc00i00')
2010-01-24 12:11:46,690 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c305ec> about HardwareID('modalias', 'acpi:PNP0000:')
2010-01-24 12:11:46,691 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c305ec> about HardwareID('modalias', 'acpi:PNP0103:')
2010-01-24 12:11:46,691 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c305ec> about HardwareID('modalias', 'pci:v000014E4d0000432Bsv0000103Csd0000137Fbc02sc80i00')
2010-01-24 12:11:46,810 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ssb', 'jockey_handler': 'KernelModuleHandler'}
2010-01-24 12:11:46,817 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-01-24 12:11:46,818 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-01-24 12:11:46,818 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2010-01-24 12:11:46,819 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c305ec> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-01-24 12:11:46,819 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-24 12:11:46,820 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c305ec> about HardwareID('modalias', 'platform:eisa')
2010-01-24 12:11:46,820 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c305ec> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-01-24 12:11:46,879 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c305ec> about HardwareID('modalias', 'pci:v00001022d00001304sv00000000sd00000000bc06sc00i00')
2010-01-24 12:11:46,880 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c305ec> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,5,k8A,94,E0,E1,E2,166,ramlsfw1,5,')
2010-01-24 12:11:46,881 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-24 12:11:46,881 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c305ec> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-01-24 12:11:46,881 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c305ec> about HardwareID('modalias', 'platform:hp-wmi')
2010-01-24 12:11:46,882 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c305ec> about HardwareID('modalias', 'pci:v00001002d00004385sv0000103Csd000030F1bc0Csc05i00')
2010-01-24 12:11:46,889 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2010-01-24 12:11:46,889 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c305ec> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-01-24 12:11:46,890 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c305ec> about HardwareID('modalias', 'pci:v00001022d00001302sv00000000sd00000000bc06sc00i00')
2010-01-24 12:11:46,891 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c305ec> about HardwareID('modalias', 'pci:v00001022d00009600sv0000103Csd000030F1bc06sc00i00')
2010-01-24 12:11:46,891 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c305ec> about HardwareID('modalias', 'usb:v04F2pB09Bd6756dcEFdsc02dp01ic0Eisc02ip00')
2010-01-24 12:11:46,894 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c305ec> about HardwareID('modalias', 'acpi:PNP0C01:')
2010-01-24 12:11:46,894 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c305ec> about HardwareID('modalias', 'acpi:PNP0800:')
2010-01-24 12:11:46,894 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c305ec> about HardwareID('modalias', 'pci:v00001022d00009602sv00000000sd00000000bc06sc04i00')
2010-01-24 12:11:46,895 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'shpchp', 'jockey_handler': 'KernelModuleHandler'}
2010-01-24 12:11:46,895 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c305ec> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2010-01-24 12:11:46,896 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c305ec> about HardwareID('modalias', 'acpi:ENE0100:')
2010-01-24 12:11:46,896 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c305ec> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-01-24 12:11:46,896 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c305ec> about HardwareID('modalias', 'acpi:PNP0303:')
2010-01-24 12:11:46,896 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c305ec> about HardwareID('modalias', 'usb:v03F0p171Dd0100dcE0dsc01dp01icFFiscFFipFF')
2010-01-24 12:11:46,934 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2010-01-24 12:11:46,934 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c305ec> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-01-24 12:11:46,935 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c305ec> about HardwareID('modalias', 'pci:v00001022d00001300sv00000000sd00000000bc06sc00i00')
2010-01-24 12:11:46,935 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c305ec> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-01-24 12:11:46,936 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-24 12:11:46,936 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c305ec> about HardwareID('modalias', 'input:b0003v04F2pB09Be6756-e0,1,kD4,ramlsfw')
2010-01-24 12:11:46,937 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-24 12:11:46,937 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c305ec> about HardwareID('modalias', 'usb:v04F2pB09Bd6756dcEFdsc02dp01ic0Eisc01ip00')
2010-01-24 12:11:46,938 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2010-01-24 12:11:46,938 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c305ec> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,112,145,14A,ra0,1,18,1C,mlsfw')
2010-01-24 12:11:46,939 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-01-24 12:11:46,939 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-01-24 12:11:46,939 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-24 12:11:46,940 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c305ec> about HardwareID('modalias', 'acpi:PNP0C32:')
2010-01-24 12:11:46,940 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c305ec> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvrF.06:bd07/08/2008:svnHewlett-Packard:pnHPPaviliontx2500NotebookPC:pvrRev1:rvnQuanta:rn30F1:rvr97.18:cvnQuanta:ct10:cvrN/A:')
2010-01-24 12:11:46,974 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c305ec> about HardwareID('modalias', 'usb:v056Ap0093d0403dc00dsc00dp00ic03isc00ip00')
2010-01-24 12:11:47,052 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'wacom', 'jockey_handler': 'KernelModuleHandler'}
2010-01-24 12:11:47,052 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2010-01-24 12:11:47,052 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c305ec> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-01-24 12:11:47,053 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c305ec> about HardwareID('modalias', 'usb:v056Ap0093d0403dc00dsc00dp00ic03isc01ip02')
2010-01-24 12:11:47,055 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'wacom', 'jockey_handler': 'KernelModuleHandler'}
2010-01-24 12:11:47,055 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2010-01-24 12:11:47,055 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c305ec> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-01-24 12:11:47,056 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-24 12:11:47,056 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c305ec> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-01-24 12:11:47,057 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c305ec> about HardwareID('modalias', 'usb:v0BDAp0158d5887dc00dsc00dp00ic08isc06ip50')
2010-01-24 12:11:47,068 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2010-01-24 12:11:47,068 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c305ec> about HardwareID('modalias', 'acpi:SYN014C:SYN0100:SYN0002:PNP0F13:')
2010-01-24 12:11:47,069 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c305ec> about HardwareID('modalias', 'acpi:PNP0100:')
2010-01-24 12:11:47,069 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c305ec> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2010-01-24 12:11:47,075 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c305ec> about HardwareID('modalias', 'usb:v03F0p171Dd0100dcE0dsc01dp01icFEisc01ip00')
2010-01-24 12:11:47,077 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2010-01-24 12:11:47,077 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c305ec> about HardwareID('modalias', 'pci:v000010ECd00008168sv0000103Csd000030F1bc02sc00i00')
2010-01-24 12:11:47,090 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2010-01-24 12:11:47,090 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c305ec> about HardwareID('modalias', 'pci:v00001002d0000439Dsv0000103Csd000030F1bc06sc01i00')
2010-01-24 12:11:47,097 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c305ec> about HardwareID('modalias', 'pci:v00001002d00004391sv0000103Csd000030F1bc01sc06i01')
2010-01-24 12:11:47,103 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c305ec> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2010-01-24 12:11:47,103 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-24 12:11:47,104 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c305ec> about HardwareID('modalias', 'acpi:PNP0200:')
2010-01-24 12:11:47,104 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c305ec> about HardwareID('modalias', 'usb:v03F0p171Dd0100dcE0dsc01dp01icE0isc01ip01')
2010-01-24 12:11:47,105 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2010-01-24 12:11:47,106 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c305ec> about HardwareID('modalias', 'pci:v00001002d00004396sv0000103Csd000030F1bc0Csc03i20')
2010-01-24 12:11:47,112 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c305ec> about HardwareID('modalias', 'platform:pcspkr')
2010-01-24 12:11:47,113 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2010-01-24 12:11:47,113 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2010-01-24 12:11:47,113 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c305ec> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-01-24 12:11:47,137 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2010-01-24 12:11:47,137 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2010-01-24 12:11:47,137 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c305ec> about HardwareID('modalias', 'usb:v08FFp1600d0C10dcFFdscFFdpFFicFFiscFFipFF')
2010-01-24 12:11:47,138 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c305ec> about HardwareID('modalias', 'input:b0003v056Ap0093e0403-e0,1,3,k140,141,14A,14B,14C,14D,ra0,1,3,4,18,28,mlsfw')
2010-01-24 12:11:47,139 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-01-24 12:11:47,139 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-01-24 12:11:47,139 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-24 12:11:47,140 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c305ec> about HardwareID('modalias', 'pci:v00001002d00004383sv0000103Csd000030F1bc04sc03i00')
2010-01-24 12:11:47,146 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2010-01-24 12:11:47,146 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2010-01-24 12:11:47,147 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c305ec> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-01-24 12:11:47,147 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-24 12:11:47,147 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c305ec> about HardwareID('modalias', 'input:b0001v10ECp0268e0001-e0,12,kramls1,2,fw')
2010-01-24 12:11:47,148 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-01-24 12:11:47,148 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8c305ec> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-01-24 12:11:47,148 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fae20c> about HardwareID('modalias', 'pci:v00001002d00009612sv0000103Csd000030F1bc03sc00i00')
2010-01-24 12:11:47,149 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fae20c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-01-24 12:11:47,149 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fae20c> about HardwareID('modalias', 'pci:v00001022d00001303sv00000000sd00000000bc06sc00i00')
2010-01-24 12:11:47,149 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fae20c> about HardwareID('modalias', 'pci:v00001022d00001301sv00000000sd00000000bc06sc00i00')
2010-01-24 12:11:47,149 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fae20c> about HardwareID('modalias', 'acpi:PNP0000:')
2010-01-24 12:11:47,149 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fae20c> about HardwareID('modalias', 'acpi:PNP0103:')
2010-01-24 12:11:47,150 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fae20c> about HardwareID('modalias', 'pci:v000014E4d0000432Bsv0000103Csd0000137Fbc02sc80i00')
2010-01-24 12:11:47,150 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fae20c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-01-24 12:11:47,150 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fae20c> about HardwareID('modalias', 'platform:eisa')
2010-01-24 12:11:47,150 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fae20c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-01-24 12:11:47,151 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fae20c> about HardwareID('modalias', 'pci:v00001022d00001304sv00000000sd00000000bc06sc00i00')
2010-01-24 12:11:47,151 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fae20c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,5,k8A,94,E0,E1,E2,166,ramlsfw1,5,')
2010-01-24 12:11:47,151 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fae20c> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-01-24 12:11:47,151 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fae20c> about HardwareID('modalias', 'platform:hp-wmi')
2010-01-24 12:11:47,151 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fae20c> about HardwareID('modalias', 'pci:v00001002d00004385sv0000103Csd000030F1bc0Csc05i00')
2010-01-24 12:11:47,152 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fae20c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-01-24 12:11:47,152 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fae20c> about HardwareID('modalias', 'pci:v00001022d00001302sv00000000sd00000000bc06sc00i00')
2010-01-24 12:11:47,152 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fae20c> about HardwareID('modalias', 'pci:v00001022d00009600sv0000103Csd000030F1bc06sc00i00')
2010-01-24 12:11:47,152 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fae20c> about HardwareID('modalias', 'usb:v04F2pB09Bd6756dcEFdsc02dp01ic0Eisc02ip00')
2010-01-24 12:11:47,153 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fae20c> about HardwareID('modalias', 'acpi:PNP0C01:')
2010-01-24 12:11:47,153 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fae20c> about HardwareID('modalias', 'acpi:PNP0800:')
2010-01-24 12:11:47,153 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fae20c> about HardwareID('modalias', 'pci:v00001022d00009602sv00000000sd00000000bc06sc04i00')
2010-01-24 12:11:47,153 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fae20c> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2010-01-24 12:11:47,153 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fae20c> about HardwareID('modalias', 'acpi:ENE0100:')
2010-01-24 12:11:47,154 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fae20c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-01-24 12:11:47,154 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fae20c> about HardwareID('modalias', 'acpi:PNP0303:')
2010-01-24 12:11:47,154 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fae20c> about HardwareID('modalias', 'usb:v03F0p171Dd0100dcE0dsc01dp01icFFiscFFipFF')
2010-01-24 12:11:47,154 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fae20c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-01-24 12:11:47,155 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fae20c> about HardwareID('modalias', 'pci:v00001022d00001300sv00000000sd00000000bc06sc00i00')
2010-01-24 12:11:47,155 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fae20c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-01-24 12:11:47,155 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fae20c> about HardwareID('modalias', 'input:b0003v04F2pB09Be6756-e0,1,kD4,ramlsfw')
2010-01-24 12:11:47,155 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fae20c> about HardwareID('modalias', 'usb:v04F2pB09Bd6756dcEFdsc02dp01ic0Eisc01ip00')
2010-01-24 12:11:47,155 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fae20c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,112,145,14A,ra0,1,18,1C,mlsfw')
2010-01-24 12:11:47,156 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fae20c> about HardwareID('modalias', 'acpi:PNP0C32:')
2010-01-24 12:11:47,156 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fae20c> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvrF.06:bd07/08/2008:svnHewlett-Packard:pnHPPaviliontx2500NotebookPC:pvrRev1:rvnQuanta:rn30F1:rvr97.18:cvnQuanta:ct10:cvrN/A:')
2010-01-24 12:11:47,156 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fae20c> about HardwareID('modalias', 'usb:v056Ap0093d0403dc00dsc00dp00ic03isc00ip00')
2010-01-24 12:11:47,156 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fae20c> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-01-24 12:11:47,157 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fae20c> about HardwareID('modalias', 'usb:v056Ap0093d0403dc00dsc00dp00ic03isc01ip02')
2010-01-24 12:11:47,157 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fae20c> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-01-24 12:11:47,157 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fae20c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-01-24 12:11:47,157 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fae20c> about HardwareID('modalias', 'usb:v0BDAp0158d5887dc00dsc00dp00ic08isc06ip50')
2010-01-24 12:11:47,158 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fae20c> about HardwareID('modalias', 'acpi:SYN014C:SYN0100:SYN0002:PNP0F13:')
2010-01-24 12:11:47,158 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fae20c> about HardwareID('modalias', 'acpi:PNP0100:')
2010-01-24 12:11:47,158 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fae20c> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2010-01-24 12:11:47,158 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fae20c> about HardwareID('modalias', 'usb:v03F0p171Dd0100dcE0dsc01dp01icFEisc01ip00')
2010-01-24 12:11:47,158 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fae20c> about HardwareID('modalias', 'pci:v000010ECd00008168sv0000103Csd000030F1bc02sc00i00')
2010-01-24 12:11:47,159 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fae20c> about HardwareID('modalias', 'pci:v00001002d0000439Dsv0000103Csd000030F1bc06sc01i00')
2010-01-24 12:11:47,159 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fae20c> about HardwareID('modalias', 'pci:v00001002d00004391sv0000103Csd000030F1bc01sc06i01')
2010-01-24 12:11:47,159 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fae20c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2010-01-24 12:11:47,159 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fae20c> about HardwareID('modalias', 'acpi:PNP0200:')
2010-01-24 12:11:47,160 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fae20c> about HardwareID('modalias', 'usb:v03F0p171Dd0100dcE0dsc01dp01icE0isc01ip01')
2010-01-24 12:11:47,160 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fae20c> about HardwareID('modalias', 'pci:v00001002d00004396sv0000103Csd000030F1bc0Csc03i20')
2010-01-24 12:11:47,160 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fae20c> about HardwareID('modalias', 'platform:pcspkr')
2010-01-24 12:11:47,160 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fae20c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-01-24 12:11:47,160 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fae20c> about HardwareID('modalias', 'usb:v08FFp1600d0C10dcFFdscFFdpFFicFFiscFFipFF')
2010-01-24 12:11:47,161 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fae20c> about HardwareID('modalias', 'input:b0003v056Ap0093e0403-e0,1,3,k140,141,14A,14B,14C,14D,ra0,1,3,4,18,28,mlsfw')
2010-01-24 12:11:47,161 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fae20c> about HardwareID('modalias', 'pci:v00001002d00004383sv0000103Csd000030F1bc04sc03i00')
2010-01-24 12:11:47,161 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fae20c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-01-24 12:11:47,161 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fae20c> about HardwareID('modalias', 'input:b0001v10ECp0268e0001-e0,12,kramls1,2,fw')
2010-01-24 12:11:47,162 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fae20c> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-01-24 12:11:47,245 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-01-24 12:11:48,354 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-01-24 12:11:48,410 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-01-24 12:11:54,286 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-01-24 12:11:57,923 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-01-24 12:12:06,333 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-01-24 12:12:06,334 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2010-01-24 12:12:06,366 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-01-24 12:12:22,309 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-01-24 12:12:22,948 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-01-24 12:12:23,009 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
```

---

### Post by Docaltmed on 2010-01-24
So I tried compiling the STA driver from the broadcomm site (I'm using a BCM 4322 wireless). Here's the result:

```
KBUILD_NOPEDANTIC=1 make -C /lib/modules/`uname -r`/build M=`pwd`
make: *** /lib/modules/2.6.31-17-generic-pae/build: No such file or directory.  Stop.
make: *** [all] Error 2

```

Looking around, there seems to be a lot of this kind of thing going on, all revolving around the 2.6.31-17 kernel. All recent. What gives?

---

### Post by Docaltmed on 2010-01-29
Took the zombie way out. Re-installed Karmic. What a pain.

---

