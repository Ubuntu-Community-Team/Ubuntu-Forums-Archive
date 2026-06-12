---
title: "Failed to install v.195 Nvidia accelerated graphics driver"
date: 2009-12-23
forum: Multimedia Software
---

### Post by Robbyx on 2009-12-23
After trying to install the nvidia proprietary  driver v.195 via the Hardware drivers option there was an error message saying it had failed. The screen says the driver was recently disabled but is still in use. The error message suggested I look in the jockey.log which I do not understand. Does anyone what is  the status of the driver on my machine. 
Karmic

Jockey.log

```
2009-12-23 19:51:36,322 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x954a4cc>
2009-12-23 19:51:36,384 DEBUG: reading modalias file /lib/modules/2.6.31-17-generic/modules.alias
2009-12-23 19:51:36,501 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2009-12-23 19:51:36,515 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2009-12-23 19:51:36,547 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2009-12-23 19:51:36,558 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2009-12-23 19:51:36,562 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-180
2009-12-23 19:51:36,576 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-190
2009-12-23 19:51:36,591 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-195
2009-12-23 19:51:36,605 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2009-12-23 19:51:36,645 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2009-12-23 19:51:38,121 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2009-12-23 19:51:38,201 DEBUG: Software modem not available
2009-12-23 19:51:38,201 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2009-12-23 19:51:38,290 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2009-12-23 19:51:38,290 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2009-12-23 19:51:38,291 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2009-12-23 19:51:38,291 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2009-12-23 19:51:38,302 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2009-12-23 19:51:38,316 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2009-12-23 19:51:38,322 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2009-12-23 19:51:38,322 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2009-12-23 19:51:38,420 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver from name NvidiaDriver
2009-12-23 19:51:38,420 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2009-12-23 19:51:38,420 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2009-12-23 19:51:38,462 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2009-12-23 19:51:38,462 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2009-12-23 19:51:38,479 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2009-12-23 19:51:38,480 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2009-12-23 19:51:38,480 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2009-12-23 19:51:38,509 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2009-12-23 19:51:38,509 DEBUG: Firmware for DVB cards not available
2009-12-23 19:51:38,509 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2009-12-23 19:51:38,553 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2009-12-23 19:51:38,560 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2009-12-23 19:51:38,560 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2009-12-23 19:51:38,560 DEBUG: all custom handlers loaded
2009-12-23 19:51:38,560 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x954a4cc> about HardwareID('modalias', 'pci:v00008086d00002937sv00001458sd00005004bc0Csc03i00')
2009-12-23 19:51:38,769 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x954a4cc> about HardwareID('modalias', 'input:b0001v10ECp0888e0001-e0,12,kramls1,2,fw')
2009-12-23 19:51:38,888 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2009-12-23 19:51:38,888 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x954a4cc> about HardwareID('modalias', 'pci:v00008086d00002918sv00001458sd00005001bc06sc01i00')
2009-12-23 19:51:38,890 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2009-12-23 19:51:38,890 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x954a4cc> about HardwareID('modalias', 'pci:v000013C1d00001001sv000013C1sd00001001bc01sc04i00')
2009-12-23 19:51:38,893 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': '3w_xxxx', 'jockey_handler': 'KernelModuleHandler'}
2009-12-23 19:51:38,893 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x954a4cc> about HardwareID('modalias', 'acpi:PNP0100:')
2009-12-23 19:51:38,893 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x954a4cc> about HardwareID('modalias', 'acpi:PNP0103:')
2009-12-23 19:51:38,893 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x954a4cc> about HardwareID('modalias', 'pci:v00008086d00002938sv00001458sd00005004bc0Csc03i00')
2009-12-23 19:51:38,895 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x954a4cc> about HardwareID('modalias', 'platform:eisa')
2009-12-23 19:51:38,895 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x954a4cc> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2009-12-23 19:51:38,914 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x954a4cc> about HardwareID('modalias', 'pci:v00008086d00002930sv00001458sd00005001bc0Csc05i00')
2009-12-23 19:51:38,916 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2009-12-23 19:51:38,916 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x954a4cc> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2009-12-23 19:51:38,916 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2009-12-23 19:51:38,917 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x954a4cc> about HardwareID('modalias', 'acpi:PNP0C04:')
2009-12-23 19:51:38,917 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x954a4cc> about HardwareID('modalias', 'platform:it87')
2009-12-23 19:51:38,917 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x954a4cc> about HardwareID('modalias', 'pci:v00008086d00002934sv00001458sd00005004bc0Csc03i00')
2009-12-23 19:51:38,919 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x954a4cc> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2009-12-23 19:51:38,919 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x954a4cc> about HardwareID('modalias', 'pci:v00008086d00001040sv00008086sd00001000bc07sc80i00')
2009-12-23 19:51:38,921 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x954a4cc> about HardwareID('modalias', 'pci:v00008086d000029C0sv00001458sd00005000bc06sc00i00')
2009-12-23 19:51:38,923 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_agp', 'jockey_handler': 'KernelModuleHandler'}
2009-12-23 19:51:38,923 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x954a4cc> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2009-12-23 19:51:38,924 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x954a4cc> about HardwareID('modalias', 'acpi:PNP0C02:')
2009-12-23 19:51:38,924 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x954a4cc> about HardwareID('modalias', 'acpi:PNP0200:')
2009-12-23 19:51:38,924 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x954a4cc> about HardwareID('modalias', 'pci:v000010DEd00000392sv0000107Dsd00002A52bc03sc00i00')
2009-12-23 19:51:39,181 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
2009-12-23 19:51:39,192 DEBUG: got handler xorg:nvidia-173([NvidiaDriver, nonfree, disabled] NVIDIA accelerated graphics driver)
2009-12-23 19:51:39,205 DEBUG: got handler xorg:nvidia-180([NvidiaDriver, nonfree, disabled] NVIDIA accelerated graphics driver)
2009-12-23 19:51:39,218 DEBUG: got handler xorg:nvidia-190([NvidiaDriver, nonfree, disabled] NVIDIA accelerated graphics driver)
2009-12-23 19:51:39,228 DEBUG: got handler xorg:nvidia-195([NvidiaDriver, nonfree, disabled] NVIDIA accelerated graphics driver)
2009-12-23 19:51:39,238 DEBUG: got handler xorg:nvidia-96([NvidiaDriver, nonfree, disabled] NVIDIA accelerated graphics driver)
2009-12-23 19:51:39,238 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x954a4cc> about HardwareID('modalias', 'acpi:PNP0700:')
2009-12-23 19:51:39,238 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x954a4cc> about HardwareID('modalias', 'acpi:PNP0C01:')
2009-12-23 19:51:39,238 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x954a4cc> about HardwareID('modalias', 'acpi:PNP0B00:')
2009-12-23 19:51:39,238 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x954a4cc> about HardwareID('printer_deviceid', 'MFG:Generic;MDL:CUPS-PDF Printer;DES:Generic CUPS-PDF Printer;CMD:POSTSCRIPT;')
2009-12-23 19:51:39,239 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x954a4cc> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2009-12-23 19:51:39,239 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x954a4cc> about HardwareID('modalias', 'usb:v04F9p01B7d0100dc00dsc00dp00ic08isc06ip50')
2009-12-23 19:51:39,239 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2009-12-23 19:51:39,239 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x954a4cc> about HardwareID('modalias', 'pci:v00008086d0000293Csv00001458sd00005006bc0Csc03i20')
2009-12-23 19:51:39,241 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x954a4cc> about HardwareID('modalias', 'pci:v00008086d0000244Esv00000000sd00000000bc06sc04i01')
2009-12-23 19:51:39,243 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x954a4cc> about HardwareID('printer_deviceid', 'MFG:Brother;MDL:MFC-5460CN;CMD:HBP,BRPJL;')
2009-12-23 19:51:39,243 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x954a4cc> about HardwareID('modalias', 'input:b0003v046DpC051e0110-e0,1,2,4,k110,111,112,113,114,115,116,117,r0,1,8,am4,lsfw')
2009-12-23 19:51:39,244 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2009-12-23 19:51:39,244 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x954a4cc> about HardwareID('modalias', 'usb:v03EBp0902d0100dc09dsc00dp00ic09isc00ip00')
2009-12-23 19:51:39,249 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x954a4cc> about HardwareID('modalias', 'acpi:LNXTHERM:')
2009-12-23 19:51:39,249 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x954a4cc> about HardwareID('modalias', 'acpi:INT0800:')
2009-12-23 19:51:39,250 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x954a4cc> about HardwareID('modalias', 'dmi:bvnAwardSoftwareInternational,Inc.:bvrF4:bd04/02/2008:svnGigabyteTechnologyCo.,Ltd.:pnEP35-DS3L:pvr:rvnGigabyteTechnologyCo.,Ltd.:rnEP35-DS3L:rvrx.x:cvnGigabyteTechnologyCo.,Ltd.:ct3:cvr:')
2009-12-23 19:51:39,261 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x954a4cc> about HardwareID('modalias', 'usb:v046Dp0990d0008dcEFdsc02dp01ic01isc01ip00')
2009-12-23 19:51:39,288 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio', 'jockey_handler': 'KernelModuleHandler'}
2009-12-23 19:51:39,288 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio', 'jockey_handler': 'KernelModuleHandler'}
2009-12-23 19:51:39,289 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x954a4cc> about HardwareID('modalias', 'acpi:PNP0400:')
2009-12-23 19:51:39,289 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x954a4cc> about HardwareID('modalias', 'usb:v046Dp0990d0008dcEFdsc02dp01ic0Eisc02ip00')
2009-12-23 19:51:39,289 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio', 'jockey_handler': 'KernelModuleHandler'}
2009-12-23 19:51:39,289 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x954a4cc> about HardwareID('modalias', 'input:b0003v046Dp0990e0008-e0,1,kD4,ramlsfw')
2009-12-23 19:51:39,289 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2009-12-23 19:51:39,290 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x954a4cc> about HardwareID('modalias', 'usb:v046DpC051d3000dc00dsc00dp00ic03isc01ip02')
2009-12-23 19:51:39,290 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2009-12-23 19:51:39,290 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x954a4cc> about HardwareID('modalias', 'usb:v046Dp0990d0008dcEFdsc02dp01ic01isc02ip00')
2009-12-23 19:51:39,291 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio', 'jockey_handler': 'KernelModuleHandler'}
2009-12-23 19:51:39,291 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x954a4cc> about HardwareID('modalias', 'usb:v04F9p01B7d0100dc00dsc00dp00ic07isc01ip02')
2009-12-23 19:51:39,291 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usblp', 'jockey_handler': 'KernelModuleHandler'}
2009-12-23 19:51:39,292 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x954a4cc> about HardwareID('modalias', 'acpi:PNP0303:')
2009-12-23 19:51:39,292 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x954a4cc> about HardwareID('modalias', 'acpi:PNP0800:')
2009-12-23 19:51:39,292 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x954a4cc> about HardwareID('modalias', 'pci:v00008086d0000293Asv00001458sd00005006bc0Csc03i20')
2009-12-23 19:51:39,297 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x954a4cc> about HardwareID('modalias', 'usb:v051Dp0002d0006dc00dsc00dp00ic03isc00ip00')
2009-12-23 19:51:39,298 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2009-12-23 19:51:39,298 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x954a4cc> about HardwareID('modalias', 'pci:v00008086d00002939sv00001458sd00005004bc0Csc03i00')
2009-12-23 19:51:39,300 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x954a4cc> about HardwareID('modalias', 'pci:v00008086d00002936sv00001458sd00005004bc0Csc03i00')
2009-12-23 19:51:39,302 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x954a4cc> about HardwareID('modalias', 'pci:v00008086d0000293Esv00001458sd0000A002bc04sc03i00')
2009-12-23 19:51:39,303 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2009-12-23 19:51:39,304 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x954a4cc> about HardwareID('modalias', 'platform:pcspkr')
2009-12-23 19:51:39,304 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2009-12-23 19:51:39,304 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2009-12-23 19:51:39,304 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x954a4cc> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2009-12-23 19:51:39,304 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2009-12-23 19:51:39,304 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x954a4cc> about HardwareID('modalias', 'acpi:PNP0000:')
2009-12-23 19:51:39,304 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x954a4cc> about HardwareID('modalias', 'usb:v04F9p01B7d0100dc00dsc00dp00icFFiscFFipFF')
2009-12-23 19:51:39,305 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x954a4cc> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001458sd0000E000bc02sc00i00')
2009-12-23 19:51:39,309 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2009-12-23 19:51:39,309 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x954a4cc> about HardwareID('modalias', 'platform:coretemp')
2009-12-23 19:51:39,309 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x954a4cc> about HardwareID('modalias', 'usb:v046Dp0990d0008dcEFdsc02dp01ic0Eisc01ip00')
2009-12-23 19:51:39,310 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio', 'jockey_handler': 'KernelModuleHandler'}
2009-12-23 19:51:39,310 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2009-12-23 19:51:39,310 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x954a4cc> about HardwareID('modalias', 'pci:v00008086d00002935sv00001458sd00005004bc0Csc03i00')
2009-12-23 19:51:39,312 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x954a4cc> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2009-12-23 19:51:39,312 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2009-12-23 19:51:39,312 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x954a4cc> about HardwareID('modalias', 'acpi:PNP0501:')
2009-12-23 19:51:39,312 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x98ee48c> about HardwareID('modalias', 'pci:v00008086d00002937sv00001458sd00005004bc0Csc03i00')
2009-12-23 19:51:39,312 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x98ee48c> about HardwareID('modalias', 'input:b0001v10ECp0888e0001-e0,12,kramls1,2,fw')
2009-12-23 19:51:39,312 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x98ee48c> about HardwareID('modalias', 'pci:v00008086d00002918sv00001458sd00005001bc06sc01i00')
2009-12-23 19:51:39,313 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x98ee48c> about HardwareID('modalias', 'pci:v000013C1d00001001sv000013C1sd00001001bc01sc04i00')
2009-12-23 19:51:39,313 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x98ee48c> about HardwareID('modalias', 'acpi:PNP0100:')
2009-12-23 19:51:39,313 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x98ee48c> about HardwareID('modalias', 'acpi:PNP0103:')
2009-12-23 19:51:39,313 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x98ee48c> about HardwareID('modalias', 'pci:v00008086d00002938sv00001458sd00005004bc0Csc03i00')
2009-12-23 19:51:39,313 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x98ee48c> about HardwareID('modalias', 'platform:eisa')
2009-12-23 19:51:39,313 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x98ee48c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2009-12-23 19:51:39,313 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x98ee48c> about HardwareID('modalias', 'pci:v00008086d00002930sv00001458sd00005001bc0Csc05i00')
2009-12-23 19:51:39,313 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x98ee48c> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2009-12-23 19:51:39,313 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x98ee48c> about HardwareID('modalias', 'acpi:PNP0C04:')
2009-12-23 19:51:39,313 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x98ee48c> about HardwareID('modalias', 'platform:it87')
2009-12-23 19:51:39,313 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x98ee48c> about HardwareID('modalias', 'pci:v00008086d00002934sv00001458sd00005004bc0Csc03i00')
2009-12-23 19:51:39,313 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x98ee48c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2009-12-23 19:51:39,314 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x98ee48c> about HardwareID('modalias', 'pci:v00008086d00001040sv00008086sd00001000bc07sc80i00')
2009-12-23 19:51:39,314 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x98ee48c> about HardwareID('modalias', 'pci:v00008086d000029C0sv00001458sd00005000bc06sc00i00')
2009-12-23 19:51:39,314 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x98ee48c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2009-12-23 19:51:39,314 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x98ee48c> about HardwareID('modalias', 'acpi:PNP0C02:')
2009-12-23 19:51:39,314 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x98ee48c> about HardwareID('modalias', 'acpi:PNP0200:')
2009-12-23 19:51:39,314 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x98ee48c> about HardwareID('modalias', 'pci:v000010DEd00000392sv0000107Dsd00002A52bc03sc00i00')
2009-12-23 19:51:39,314 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x98ee48c> about HardwareID('modalias', 'acpi:PNP0700:')
2009-12-23 19:51:39,314 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x98ee48c> about HardwareID('modalias', 'acpi:PNP0C01:')
2009-12-23 19:51:39,314 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x98ee48c> about HardwareID('modalias', 'acpi:PNP0B00:')
2009-12-23 19:51:39,314 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x98ee48c> about HardwareID('printer_deviceid', 'MFG:Generic;MDL:CUPS-PDF Printer;DES:Generic CUPS-PDF Printer;CMD:POSTSCRIPT;')
2009-12-23 19:51:39,314 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x98ee48c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2009-12-23 19:51:39,315 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x98ee48c> about HardwareID('modalias', 'usb:v04F9p01B7d0100dc00dsc00dp00ic08isc06ip50')
2009-12-23 19:51:39,315 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x98ee48c> about HardwareID('modalias', 'pci:v00008086d0000293Csv00001458sd00005006bc0Csc03i20')
2009-12-23 19:51:39,315 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x98ee48c> about HardwareID('modalias', 'pci:v00008086d0000244Esv00000000sd00000000bc06sc04i01')
2009-12-23 19:51:39,315 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x98ee48c> about HardwareID('printer_deviceid', 'MFG:Brother;MDL:MFC-5460CN;CMD:HBP,BRPJL;')
2009-12-23 19:51:39,315 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x98ee48c> about HardwareID('modalias', 'input:b0003v046DpC051e0110-e0,1,2,4,k110,111,112,113,114,115,116,117,r0,1,8,am4,lsfw')
2009-12-23 19:51:39,315 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x98ee48c> about HardwareID('modalias', 'usb:v03EBp0902d0100dc09dsc00dp00ic09isc00ip00')
2009-12-23 19:51:39,315 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x98ee48c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2009-12-23 19:51:39,315 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x98ee48c> about HardwareID('modalias', 'acpi:INT0800:')
2009-12-23 19:51:39,315 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x98ee48c> about HardwareID('modalias', 'dmi:bvnAwardSoftwareInternational,Inc.:bvrF4:bd04/02/2008:svnGigabyteTechnologyCo.,Ltd.:pnEP35-DS3L:pvr:rvnGigabyteTechnologyCo.,Ltd.:rnEP35-DS3L:rvrx.x:cvnGigabyteTechnologyCo.,Ltd.:ct3:cvr:')
2009-12-23 19:51:39,315 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x98ee48c> about HardwareID('modalias', 'usb:v046Dp0990d0008dcEFdsc02dp01ic01isc01ip00')
2009-12-23 19:51:39,315 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x98ee48c> about HardwareID('modalias', 'acpi:PNP0400:')
2009-12-23 19:51:39,315 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x98ee48c> about HardwareID('modalias', 'usb:v046Dp0990d0008dcEFdsc02dp01ic0Eisc02ip00')
2009-12-23 19:51:39,316 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x98ee48c> about HardwareID('modalias', 'input:b0003v046Dp0990e0008-e0,1,kD4,ramlsfw')
2009-12-23 19:51:39,316 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x98ee48c> about HardwareID('modalias', 'usb:v046DpC051d3000dc00dsc00dp00ic03isc01ip02')
2009-12-23 19:51:39,316 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x98ee48c> about HardwareID('modalias', 'usb:v046Dp0990d0008dcEFdsc02dp01ic01isc02ip00')
2009-12-23 19:51:39,316 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x98ee48c> about HardwareID('modalias', 'usb:v04F9p01B7d0100dc00dsc00dp00ic07isc01ip02')
2009-12-23 19:51:39,316 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x98ee48c> about HardwareID('modalias', 'acpi:PNP0303:')
2009-12-23 19:51:39,316 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x98ee48c> about HardwareID('modalias', 'acpi:PNP0800:')
2009-12-23 19:51:39,316 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x98ee48c> about HardwareID('modalias', 'pci:v00008086d0000293Asv00001458sd00005006bc0Csc03i20')
2009-12-23 19:51:39,316 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x98ee48c> about HardwareID('modalias', 'usb:v051Dp0002d0006dc00dsc00dp00ic03isc00ip00')
2009-12-23 19:51:39,316 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x98ee48c> about HardwareID('modalias', 'pci:v00008086d00002939sv00001458sd00005004bc0Csc03i00')
2009-12-23 19:51:39,316 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x98ee48c> about HardwareID('modalias', 'pci:v00008086d00002936sv00001458sd00005004bc0Csc03i00')
2009-12-23 19:51:39,316 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x98ee48c> about HardwareID('modalias', 'pci:v00008086d0000293Esv00001458sd0000A002bc04sc03i00')
2009-12-23 19:51:39,316 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x98ee48c> about HardwareID('modalias', 'platform:pcspkr')
2009-12-23 19:51:39,317 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x98ee48c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2009-12-23 19:51:39,317 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x98ee48c> about HardwareID('modalias', 'acpi:PNP0000:')
2009-12-23 19:51:39,317 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x98ee48c> about HardwareID('modalias', 'usb:v04F9p01B7d0100dc00dsc00dp00icFFiscFFipFF')
2009-12-23 19:51:39,317 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x98ee48c> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001458sd0000E000bc02sc00i00')
2009-12-23 19:51:39,323 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x98ee48c> about HardwareID('modalias', 'platform:coretemp')
2009-12-23 19:51:39,324 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x98ee48c> about HardwareID('modalias', 'usb:v046Dp0990d0008dcEFdsc02dp01ic0Eisc01ip00')
2009-12-23 19:51:39,324 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x98ee48c> about HardwareID('modalias', 'pci:v00008086d00002935sv00001458sd00005004bc0Csc03i00')
2009-12-23 19:51:39,324 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x98ee48c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2009-12-23 19:51:39,324 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x98ee48c> about HardwareID('modalias', 'acpi:PNP0501:')
2009-12-23 19:52:07,594 DEBUG: Installing package: nvidia-glx-195
2009-12-23 19:52:47,129 DEBUG: install progress statusChange dpkg-exec 0.000000
2009-12-23 19:52:50,565 DEBUG: install progress statusChange nvidia-glx-190 0.000000
2009-12-23 19:52:50,577 DEBUG: install progress statusChange nvidia-glx-190 3.125000
2009-12-23 19:52:50,645 DEBUG: install progress statusChange nvidia-glx-190 6.250000
2009-12-23 19:52:52,761 DEBUG: install progress statusChange nvidia-glx-190 9.375000
2009-12-23 19:52:52,829 DEBUG: install progress statusChange nvidia-190-kernel-source 9.375000
2009-12-23 19:52:52,830 DEBUG: install progress statusChange nvidia-190-kernel-source 12.500000
2009-12-23 19:53:30,089 DEBUG: install progress statusChange nvidia-190-kernel-source 15.625000
2009-12-23 19:53:33,173 DEBUG: install progress statusChange nvidia-190-kernel-source 18.750000
2009-12-23 19:53:33,352 DEBUG: install progress statusChange nvidia-190-libvdpau 18.750000
2009-12-23 19:53:33,352 DEBUG: install progress statusChange nvidia-190-libvdpau 21.875000
2009-12-23 19:53:33,401 DEBUG: install progress statusChange nvidia-190-libvdpau 25.000000
2009-12-23 19:53:33,661 DEBUG: install progress statusChange nvidia-190-libvdpau 28.125000
2009-12-23 19:53:33,777 DEBUG: install progress statusChange nvidia-settings-190 28.125000
2009-12-23 19:53:33,777 DEBUG: install progress statusChange nvidia-settings-190 31.250000
2009-12-23 19:53:33,789 DEBUG: install progress statusChange nvidia-settings-190 34.375000
2009-12-23 19:53:34,317 DEBUG: install progress statusChange nvidia-settings-190 37.500000
2009-12-23 19:53:34,365 DEBUG: install progress statusChange desktop-file-utils 37.500000
2009-12-23 19:53:34,549 DEBUG: install progress statusChange man-db 37.500000
2009-12-23 19:53:37,361 DEBUG: install progress statusChange libc-bin 37.500000
2009-12-23 19:53:40,253 DEBUG: install progress statusChange menu 37.500000
2009-12-23 19:53:40,837 DEBUG: install progress statusChange dpkg-exec 37.500000
2009-12-23 19:53:41,377 DEBUG: install progress statusChange nvidia-195-kernel-source 37.500000
2009-12-23 19:53:41,400 DEBUG: install progress statusChange nvidia-195-kernel-source 40.625000
2009-12-23 19:53:42,342 DEBUG: install progress statusChange nvidia-195-kernel-source 43.750000
2009-12-23 19:53:42,373 DEBUG: install progress statusChange nvidia-195-kernel-source 46.875000
2009-12-23 19:53:42,473 DEBUG: install progress statusChange nvidia-195-libvdpau 46.875000
2009-12-23 19:53:42,489 DEBUG: install progress statusChange nvidia-195-libvdpau 50.000000
2009-12-23 19:53:42,661 DEBUG: install progress statusChange nvidia-195-libvdpau 53.125000
2009-12-23 19:53:42,685 DEBUG: install progress statusChange nvidia-195-libvdpau 56.250000
2009-12-23 19:53:42,785 DEBUG: install progress statusChange nvidia-glx-195 56.250000
2009-12-23 19:53:42,797 DEBUG: install progress statusChange nvidia-glx-195 59.375000
2009-12-23 19:53:47,669 DEBUG: install progress statusChange nvidia-glx-195 62.500000
2009-12-23 19:53:47,681 DEBUG: install progress statusChange nvidia-glx-195 65.625000
2009-12-23 19:53:47,753 DEBUG: install progress statusChange nvidia-settings 65.625000
2009-12-23 19:53:47,781 DEBUG: install progress statusChange nvidia-settings 68.750000
2009-12-23 19:53:48,069 DEBUG: install progress statusChange nvidia-settings 71.875000
2009-12-23 19:53:48,098 DEBUG: install progress statusChange nvidia-settings 75.000000
2009-12-23 19:53:48,137 DEBUG: install progress statusChange man-db 75.000000
2009-12-23 19:53:50,101 DEBUG: install progress statusChange desktop-file-utils 75.000000
2009-12-23 19:53:50,170 DEBUG: install progress statusChange menu 75.000000
2009-12-23 19:53:50,725 DEBUG: install progress statusChange dpkg-exec 75.000000
2009-12-23 19:53:50,901 DEBUG: install progress statusChange nvidia-195-kernel-source 75.000000
2009-12-23 19:53:50,921 DEBUG: install progress statusChange nvidia-195-kernel-source 78.125000
2009-12-23 19:54:34,473 DEBUG: install progress statusChange nvidia-195-kernel-source 81.250000
2009-12-23 19:54:34,513 DEBUG: install progress statusChange nvidia-195-libvdpau 81.250000
2009-12-23 19:54:34,525 DEBUG: install progress statusChange nvidia-195-libvdpau 84.375000
2009-12-23 19:54:34,553 DEBUG: install progress statusChange nvidia-195-libvdpau 87.500000
2009-12-23 19:54:34,588 DEBUG: install progress statusChange nvidia-glx-195 87.500000
2009-12-23 19:54:34,589 DEBUG: install progress statusChange nvidia-glx-195 90.625000
2009-12-23 19:54:35,063 DEBUG: install progress statusChange nvidia-glx-195 93.750000
2009-12-23 19:54:35,112 DEBUG: install progress statusChange nvidia-settings 93.750000
2009-12-23 19:54:35,138 DEBUG: install progress statusChange nvidia-settings 96.875000
2009-12-23 19:54:35,253 DEBUG: install progress statusChange nvidia-settings 100.000000
2009-12-23 19:54:35,317 DEBUG: install progress statusChange libc-bin 100.000000
2009-12-23 19:54:35,461 DEBUG: install progress statusChange menu 100.000000
2009-12-23 19:54:36,085 DEBUG: (Reading database ... 240663 files and directories currently installed.)
Removing nvidia-glx-190 ...
Removing nvidia-190-kernel-source ...
Removing all DKMS Modules
Done.
Removing nvidia-190-libvdpau ...
Removing nvidia-settings-190 ...
Processing triggers for desktop-file-utils ...
Processing triggers for man-db ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for menu ...
Selecting previously deselected package nvidia-195-kernel-source.
(Reading database ... 240398 files and directories currently installed.)
Unpacking nvidia-195-kernel-source (from .../nvidia-195-kernel-source_195.22-0ubuntu3_i386.deb) ...
Selecting previously deselected package nvidia-195-libvdpau.
Unpacking nvidia-195-libvdpau (from .../nvidia-195-libvdpau_195.22-0ubuntu3_i386.deb) ...
Selecting previously deselected package nvidia-glx-195.
Unpacking nvidia-glx-195 (from .../nvidia-glx-195_195.22-0ubuntu3_i386.deb) ...
Selecting previously deselected package nvidia-settings.
Unpacking nvidia-settings (from .../nvidia-settings_190.36-0ubuntu6_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for menu ...
Setting up nvidia-195-kernel-source (195.22-0ubuntu3) ...
Removing all DKMS Modules
Done.
Adding Module to DKMS build system
driver version= 195.22
Doing initial module build
Installing initial module
Done.

Setting up nvidia-195-libvdpau (195.22-0ubuntu3) ...
Setting up nvidia-glx-195 (195.22-0ubuntu3) ...

Setting up nvidia-settings (190.36-0ubuntu6) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for menu ...

2009-12-23 19:54:36,085 ERROR: dpkg: warning: obsolete option '--print-installation-architecture', please use '--print-architecture' instead.

2009-12-23 19:54:36,409 DEBUG: XorgDriverHandler device sections ({0: ['\tIdentifier     "Configured Video Device"\n', '\tDriver         "nv"\n', '\tOption         "NoLogo" "True"\n'], 1: ['\tIdentifier     "Device0"\n', '\tVendorName     "NVIDIA Corporation"\n', '\tBoardName      "GeForce 7600 GS"\n', '\tOption\t"NoLogo"\t"True"\n', '\tDriver\t"nvidia"\n']})
```

---

### Post by kavamaks on 2010-03-08
Hello there.

I'm using NVidia 8400 mobile.
I'm using Karmic, do a fresh instalation, update everything, but when i try to install X 195 version of driver, instalation failed!

So I choose version 190. :)

---

