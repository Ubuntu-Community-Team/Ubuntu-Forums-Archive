---
title: "No sound &amp; screen noise"
date: 2010-09-21
forum: Multimedia Software
---

### Post by memsb on 2010-09-21
I'm running the latest version of Ubuntu and have been for a while now without issue. However today (actually now yesterday) i made the giant mistake of upgrading my on board HD3150 graphics to a PCIe HD5570 since then my whole life has fallen to bits.

First i noticed some visual noise on the screen. Concluding this was due to incorrect or out of date drivers i attempted to update them from the Hardware Drivers section. This gave the error:

SystemError: installArchives() failed

Activating from the command line using jockey gave the same error.

Deciding a reboot might be needed i did so. On power up all ubuntu and recovery modes produced an unskinned GUI with no desktop icons that responded to no mouse or keyboard input.

I was forced to reinstall the operating system.

On reinstalling and losing everything i had installed previously (it's going to take many days to get that all back and working again!), i still have the screen noise, have still been getting the same errors on attempting to activate the drivers, except now i also get this:

Sorry, the installation of this driver failed.

Please have a look at the log file for details.: /var/log/jockey.log

```
2010-09-22 01:40:58,589 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa332aec> about HardwareID('modalias', 'usb:v045Ep00E1d0007dc00dsc00dp00ic03isc01ip02')
2010-09-22 01:40:58,589 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa332aec> about HardwareID('modalias', 'usb:v046Dp0804d0009dcEFdsc02dp01ic0Eisc01ip00')
2010-09-22 01:40:58,589 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa332aec> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-09-22 01:40:58,589 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa332aec> about HardwareID('modalias', 'acpi:ATK0110:')
2010-09-22 01:40:58,590 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa332aec> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001043sd00008389bc06sc01i00')
2010-09-22 01:40:58,592 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa332aec> about HardwareID('modalias', 'usb:v046Dp0804d0009dcEFdsc02dp01ic01isc02ip00')
2010-09-22 01:40:58,592 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa332aec> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001043sd000083A3bc02sc00i00')
2010-09-22 01:40:58,593 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa332aec> about HardwareID('modalias', 'pci:v00001002d00004383sv00001043sd0000836Cbc04sc03i00')
2010-09-22 01:40:58,595 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa332aec> about HardwareID('modalias', 'pci:v00001002d00004390sv00001043sd00008389bc01sc06i01')
2010-09-22 01:40:58,597 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa332aec> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-09-22 01:40:58,597 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa332aec> about HardwareID('modalias', 'acpi:device:')
2010-09-22 01:40:58,597 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa332aec> about HardwareID('modalias', 'usb:v046Dp0804d0009dcEFdsc02dp01ic0Eisc02ip00')
2010-09-22 01:40:58,597 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa332aec> about HardwareID('modalias', 'pci:v00001002d00004396sv00001043sd00008389bc0Csc03i20')
2010-09-22 01:40:58,598 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa332aec> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2010-09-22 01:40:58,598 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa332aec> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001043sd00008389bc01sc01i8a')
2010-09-22 01:40:58,598 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa332aec> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-09-22 01:40:58,598 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa332aec> about HardwareID('modalias', 'acpi:PNP0103:')
2010-09-22 01:40:58,598 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'pci:v00001002d0000AA60sv00001787sd0000AA60bc04sc03i00')
2010-09-22 01:40:58,599 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2010-09-22 01:40:58,599 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'pci:v000010ECd00008139sv000010ECsd00008139bc02sc00i00')
2010-09-22 01:40:58,599 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'acpi:PNP0000:')
2010-09-22 01:40:58,599 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'acpi:PNP0200:')
2010-09-22 01:40:58,599 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'pci:v0000197Bd00002380sv00001043sd00008313bc0Csc00i10')
2010-09-22 01:40:58,599 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-09-22 01:40:58,599 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-09-22 01:40:58,599 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2010-09-22 01:40:58,599 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2010-09-22 01:40:58,599 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'acpi:PNP0800:')
2010-09-22 01:40:58,599 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2010-09-22 01:40:58,599 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'platform:pcspkr')
2010-09-22 01:40:58,599 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'pci:v00001002d00004385sv00001043sd00008389bc0Csc05i00')
2010-09-22 01:40:58,599 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-09-22 01:40:58,599 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'pci:v00001814d00000601sv00001814sd00002860bc02sc80i00')
2010-09-22 01:40:58,599 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'pci:v00001022d00009601sv00001043sd000083A2bc06sc00i00')
2010-09-22 01:40:58,599 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'acpi:PNP0501:')
2010-09-22 01:40:58,599 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-09-22 01:40:58,600 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'pci:v00001002d000068D9sv00001787sd00002009bc03sc00i00')
2010-09-22 01:40:58,600 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-09-22 01:40:58,600 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'acpi:PNP0400:')
2010-09-22 01:40:58,600 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'acpi:PNP0100:')
2010-09-22 01:40:58,600 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-09-22 01:40:58,600 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'usb:v046Dp0804d0009dcEFdsc02dp01ic01isc01ip00')
2010-09-22 01:40:58,600 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2010-09-22 01:40:58,600 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-09-22 01:40:58,600 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2010-09-22 01:40:58,600 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'input:b0003v045Ep00E1e0111-e0,1,2,4,k110,111,112,113,114,r0,1,6,7,8,am4,lsfw')
2010-09-22 01:40:58,600 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-09-22 01:40:58,600 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'acpi:PNP0C01:')
2010-09-22 01:40:58,600 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr2005:bd03/28/2010:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerINC.:rnM4A785TD-MEVO:rvrRevX.0x:cvnChassisManufacture:ct3:cvrChassisVersion:')
2010-09-22 01:40:58,600 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2010-09-22 01:40:58,600 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'usb:v045Ep00E1d0007dc00dsc00dp00ic03isc01ip02')
2010-09-22 01:40:58,600 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'usb:v046Dp0804d0009dcEFdsc02dp01ic0Eisc01ip00')
2010-09-22 01:40:58,600 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-09-22 01:40:58,600 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'acpi:ATK0110:')
2010-09-22 01:40:58,600 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001043sd00008389bc06sc01i00')
2010-09-22 01:40:58,601 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'usb:v046Dp0804d0009dcEFdsc02dp01ic01isc02ip00')
2010-09-22 01:40:58,601 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001043sd000083A3bc02sc00i00')
2010-09-22 01:40:58,601 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'pci:v00001002d00004383sv00001043sd0000836Cbc04sc03i00')
2010-09-22 01:40:58,601 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'pci:v00001002d00004390sv00001043sd00008389bc01sc06i01')
2010-09-22 01:40:58,601 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-09-22 01:40:58,601 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'acpi:device:')
2010-09-22 01:40:58,601 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'usb:v046Dp0804d0009dcEFdsc02dp01ic0Eisc02ip00')
2010-09-22 01:40:58,601 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'pci:v00001002d00004396sv00001043sd00008389bc0Csc03i20')
2010-09-22 01:40:58,601 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2010-09-22 01:40:58,601 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001043sd00008389bc01sc01i8a')
2010-09-22 01:40:58,601 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-09-22 01:40:58,601 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'acpi:PNP0103:')
2010-09-22 01:40:58,722 DEBUG: fglrx is not the alternative in use
2010-09-22 01:41:05,721 DEBUG: update_driverdb: updating jockey.detection.LocalKernelModulesDriverDB
2010-09-22 01:41:05,722 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xa332aec>
2010-09-22 01:41:05,724 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-09-22 01:41:05,725 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-09-22 01:41:05,726 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-09-22 01:41:05,728 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2010-09-22 01:41:05,734 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2010-09-22 01:41:05,737 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2010-09-22 01:41:05,739 DEBUG: update_driverdb: updating jockey.detection.OpenPrintingDriverDB
2010-09-22 01:41:05,739 DEBUG: updating <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac>
2010-09-22 01:41:05,739 DEBUG: Querying openprinting.org database...
2010-09-22 01:41:05,913 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2010-09-22 01:41:05,917 WARNING: modinfo for module b43legacy failed: ERROR: modinfo: could not open /lib/modules/2.6.32-25-generic/modules.dep

2010-09-22 01:41:05,917 DEBUG: Could not instantiate Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
  File "/usr/share/jockey/handlers/b43.py", line 58, in __init__
    KernelModuleHandler.__init__(self, ui, 'b43legacy')
  File "/usr/lib/python2.6/dist-packages/jockey/handlers.py", line 391, in __init__
    assert self._modinfo, 'kernel module %s exists' % self.module
AssertionError: kernel module b43legacy exists
2010-09-22 01:41:05,920 WARNING: modinfo for module b43 failed: ERROR: modinfo: could not open /lib/modules/2.6.32-25-generic/modules.dep

2010-09-22 01:41:05,920 DEBUG: Could not instantiate Handler subclass __builtin__.B43Handler from name B43Handler
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
  File "/usr/share/jockey/handlers/b43.py", line 16, in __init__
    KernelModuleHandler.__init__(self, ui, 'b43')
  File "/usr/lib/python2.6/dist-packages/jockey/handlers.py", line 391, in __init__
    assert self._modinfo, 'kernel module %s exists' % self.module
AssertionError: kernel module b43 exists
2010-09-22 01:41:05,920 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2010-09-22 01:41:05,924 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not open /lib/modules/2.6.32-25-generic/modules.dep

2010-09-22 01:41:05,924 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2010-09-22 01:41:05,924 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2010-09-22 01:41:05,924 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2010-09-22 01:41:05,928 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not open /lib/modules/2.6.32-25-generic/modules.dep

2010-09-22 01:41:05,929 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2010-09-22 01:41:05,929 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-09-22 01:41:05,932 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not open /lib/modules/2.6.32-25-generic/modules.dep

2010-09-22 01:41:05,932 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2010-09-22 01:41:05,933 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-09-22 01:41:05,933 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2010-09-22 01:41:05,936 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not open /lib/modules/2.6.32-25-generic/modules.dep

2010-09-22 01:41:05,936 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2010-09-22 01:41:05,937 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-09-22 01:41:05,937 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2010-09-22 01:41:05,943 WARNING: modinfo for module wl failed: ERROR: modinfo: could not open /lib/modules/2.6.32-25-generic/modules.dep

2010-09-22 01:41:05,943 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2010-09-22 01:41:05,944 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2010-09-22 01:41:05,944 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2010-09-22 01:41:05,949 WARNING: modinfo for module dvb_usb failed: ERROR: modinfo: could not open /lib/modules/2.6.32-25-generic/modules.dep

2010-09-22 01:41:05,950 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2010-09-22 01:41:05,951 DEBUG: Firmware for DVB cards not available
2010-09-22 01:41:05,951 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2010-09-22 01:41:05,955 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2010-09-22 01:41:05,955 ERROR: could not open /proc/asound/cards: [Errno 2] No such file or directory: '/proc/asound/cards'
2010-09-22 01:41:05,960 DEBUG: Software modem not available
2010-09-22 01:41:05,961 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2010-09-22 01:41:05,968 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not open /lib/modules/2.6.32-25-generic/modules.dep

2010-09-22 01:41:05,968 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2010-09-22 01:41:05,969 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2010-09-22 01:41:05,969 DEBUG: all custom handlers loaded
2010-09-22 01:41:05,969 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa332aec> about HardwareID('modalias', 'pci:v00001002d0000AA60sv00001787sd0000AA60bc04sc03i00')
2010-09-22 01:41:05,972 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa332aec> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2010-09-22 01:41:05,972 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa332aec> about HardwareID('modalias', 'pci:v000010ECd00008139sv000010ECsd00008139bc02sc00i00')
2010-09-22 01:41:05,973 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa332aec> about HardwareID('modalias', 'acpi:PNP0000:')
2010-09-22 01:41:05,973 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa332aec> about HardwareID('modalias', 'acpi:PNP0200:')
2010-09-22 01:41:05,973 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa332aec> about HardwareID('modalias', 'pci:v0000197Bd00002380sv00001043sd00008313bc0Csc00i10')
2010-09-22 01:41:05,973 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa332aec> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-09-22 01:41:05,974 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa332aec> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-09-22 01:41:05,974 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa332aec> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2010-09-22 01:41:05,974 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa332aec> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2010-09-22 01:41:05,974 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa332aec> about HardwareID('modalias', 'acpi:PNP0800:')
2010-09-22 01:41:05,975 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa332aec> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2010-09-22 01:41:05,975 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa332aec> about HardwareID('modalias', 'platform:pcspkr')
2010-09-22 01:41:05,975 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa332aec> about HardwareID('modalias', 'pci:v00001002d00004385sv00001043sd00008389bc0Csc05i00')
2010-09-22 01:41:05,977 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa332aec> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-09-22 01:41:05,978 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa332aec> about HardwareID('modalias', 'pci:v00001814d00000601sv00001814sd00002860bc02sc80i00')
2010-09-22 01:41:05,978 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa332aec> about HardwareID('modalias', 'pci:v00001022d00009601sv00001043sd000083A2bc06sc00i00')
2010-09-22 01:41:05,978 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa332aec> about HardwareID('modalias', 'acpi:PNP0501:')
2010-09-22 01:41:05,978 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa332aec> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-09-22 01:41:05,979 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa332aec> about HardwareID('modalias', 'pci:v00001002d000068D9sv00001787sd00002009bc03sc00i00')
2010-09-22 01:41:05,985 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not open /lib/modules/2.6.32-25-generic/modules.dep

2010-09-22 01:41:06,053 DEBUG: fglrx is not the alternative in use
2010-09-22 01:41:05,986 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2010-09-22 01:41:06,054 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa332aec> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-09-22 01:41:06,054 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa332aec> about HardwareID('modalias', 'acpi:PNP0400:')
2010-09-22 01:41:06,055 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa332aec> about HardwareID('modalias', 'acpi:PNP0100:')
2010-09-22 01:41:06,055 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa332aec> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-09-22 01:41:06,055 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa332aec> about HardwareID('modalias', 'usb:v046Dp0804d0009dcEFdsc02dp01ic01isc01ip00')
2010-09-22 01:41:06,055 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa332aec> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2010-09-22 01:41:06,056 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa332aec> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-09-22 01:41:06,056 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa332aec> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2010-09-22 01:41:06,058 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa332aec> about HardwareID('modalias', 'input:b0003v045Ep00E1e0111-e0,1,2,4,k110,111,112,113,114,r0,1,6,7,8,am4,lsfw')
2010-09-22 01:41:06,059 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa332aec> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-09-22 01:41:06,059 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa332aec> about HardwareID('modalias', 'acpi:PNP0C01:')
2010-09-22 01:41:06,059 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa332aec> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr2005:bd03/28/2010:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerINC.:rnM4A785TD-MEVO:rvrRevX.0x:cvnChassisManufacture:ct3:cvrChassisVersion:')
2010-09-22 01:41:06,059 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa332aec> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2010-09-22 01:41:06,060 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa332aec> about HardwareID('modalias', 'usb:v045Ep00E1d0007dc00dsc00dp00ic03isc01ip02')
2010-09-22 01:41:06,060 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa332aec> about HardwareID('modalias', 'usb:v046Dp0804d0009dcEFdsc02dp01ic0Eisc01ip00')
2010-09-22 01:41:06,060 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa332aec> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-09-22 01:41:06,060 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa332aec> about HardwareID('modalias', 'acpi:ATK0110:')
2010-09-22 01:41:06,061 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa332aec> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001043sd00008389bc06sc01i00')
2010-09-22 01:41:06,063 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa332aec> about HardwareID('modalias', 'usb:v046Dp0804d0009dcEFdsc02dp01ic01isc02ip00')
2010-09-22 01:41:06,063 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa332aec> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001043sd000083A3bc02sc00i00')
2010-09-22 01:41:06,064 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa332aec> about HardwareID('modalias', 'pci:v00001002d00004383sv00001043sd0000836Cbc04sc03i00')
2010-09-22 01:41:06,066 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa332aec> about HardwareID('modalias', 'pci:v00001002d00004390sv00001043sd00008389bc01sc06i01')
2010-09-22 01:41:06,067 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa332aec> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-09-22 01:41:06,067 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa332aec> about HardwareID('modalias', 'acpi:device:')
2010-09-22 01:41:06,067 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa332aec> about HardwareID('modalias', 'usb:v046Dp0804d0009dcEFdsc02dp01ic0Eisc02ip00')
2010-09-22 01:41:06,067 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa332aec> about HardwareID('modalias', 'pci:v00001002d00004396sv00001043sd00008389bc0Csc03i20')
2010-09-22 01:41:06,068 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa332aec> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2010-09-22 01:41:06,068 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa332aec> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001043sd00008389bc01sc01i8a')
2010-09-22 01:41:06,069 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa332aec> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-09-22 01:41:06,069 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa332aec> about HardwareID('modalias', 'acpi:PNP0103:')
2010-09-22 01:41:06,069 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'pci:v00001002d0000AA60sv00001787sd0000AA60bc04sc03i00')
2010-09-22 01:41:06,069 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2010-09-22 01:41:06,069 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'pci:v000010ECd00008139sv000010ECsd00008139bc02sc00i00')
2010-09-22 01:41:06,069 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'acpi:PNP0000:')
2010-09-22 01:41:06,069 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'acpi:PNP0200:')
2010-09-22 01:41:06,069 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'pci:v0000197Bd00002380sv00001043sd00008313bc0Csc00i10')
2010-09-22 01:41:06,069 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-09-22 01:41:06,069 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-09-22 01:41:06,069 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2010-09-22 01:41:06,069 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2010-09-22 01:41:06,069 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'acpi:PNP0800:')
2010-09-22 01:41:06,069 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2010-09-22 01:41:06,069 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'platform:pcspkr')
2010-09-22 01:41:06,069 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'pci:v00001002d00004385sv00001043sd00008389bc0Csc05i00')
2010-09-22 01:41:06,070 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-09-22 01:41:06,070 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'pci:v00001814d00000601sv00001814sd00002860bc02sc80i00')
2010-09-22 01:41:06,070 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'pci:v00001022d00009601sv00001043sd000083A2bc06sc00i00')
2010-09-22 01:41:06,070 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'acpi:PNP0501:')
2010-09-22 01:41:06,070 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-09-22 01:41:06,070 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'pci:v00001002d000068D9sv00001787sd00002009bc03sc00i00')
2010-09-22 01:41:06,070 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-09-22 01:41:06,070 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'acpi:PNP0400:')
2010-09-22 01:41:06,070 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'acpi:PNP0100:')
2010-09-22 01:41:06,070 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-09-22 01:41:06,070 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'usb:v046Dp0804d0009dcEFdsc02dp01ic01isc01ip00')
2010-09-22 01:41:06,070 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2010-09-22 01:41:06,070 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-09-22 01:41:06,070 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2010-09-22 01:41:06,070 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'input:b0003v045Ep00E1e0111-e0,1,2,4,k110,111,112,113,114,r0,1,6,7,8,am4,lsfw')
2010-09-22 01:41:06,070 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-09-22 01:41:06,070 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'acpi:PNP0C01:')
2010-09-22 01:41:06,070 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr2005:bd03/28/2010:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerINC.:rnM4A785TD-MEVO:rvrRevX.0x:cvnChassisManufacture:ct3:cvrChassisVersion:')
2010-09-22 01:41:06,071 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2010-09-22 01:41:06,071 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'usb:v045Ep00E1d0007dc00dsc00dp00ic03isc01ip02')
2010-09-22 01:41:06,071 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'usb:v046Dp0804d0009dcEFdsc02dp01ic0Eisc01ip00')
2010-09-22 01:41:06,071 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-09-22 01:41:06,071 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'acpi:ATK0110:')
2010-09-22 01:41:06,071 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001043sd00008389bc06sc01i00')
2010-09-22 01:41:06,071 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'usb:v046Dp0804d0009dcEFdsc02dp01ic01isc02ip00')
2010-09-22 01:41:06,071 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001043sd000083A3bc02sc00i00')
2010-09-22 01:41:06,071 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'pci:v00001002d00004383sv00001043sd0000836Cbc04sc03i00')
2010-09-22 01:41:06,071 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'pci:v00001002d00004390sv00001043sd00008389bc01sc06i01')
2010-09-22 01:41:06,071 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-09-22 01:41:06,071 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'acpi:device:')
2010-09-22 01:41:06,071 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'usb:v046Dp0804d0009dcEFdsc02dp01ic0Eisc02ip00')
2010-09-22 01:41:06,071 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'pci:v00001002d00004396sv00001043sd00008389bc0Csc03i20')
2010-09-22 01:41:06,071 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2010-09-22 01:41:06,071 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001043sd00008389bc01sc01i8a')
2010-09-22 01:41:06,071 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-09-22 01:41:06,071 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa47cbac> about HardwareID('modalias', 'acpi:PNP0103:')
2010-09-22 01:41:31,534 DEBUG: fglrx is not the alternative in use
2010-09-22 01:41:36,852 DEBUG: Installing package: linux-headers-2.6.32-25-generic
2010-09-22 01:41:37,048 DEBUG: Package linux-headers-2.6.32-25-generic does not exist, aborting
2010-09-22 01:41:37,173 DEBUG: Installing package: fglrx
2010-09-22 01:41:37,484 DEBUG: install progress statusChange dpkg-exec 0.000000
2010-09-22 01:41:37,549 DEBUG: install progress statusChange dkms 0.000000
2010-09-22 01:41:37,651 DEBUG: install progress statusChange dkms 11.111100
2010-09-22 01:41:37,993 DEBUG: install progress statusChange dkms 22.222200
2010-09-22 01:41:38,086 DEBUG: install progress statusChange dkms 33.333300
2010-09-22 01:41:38,113 DEBUG: install progress statusChange fglrx 33.333300
2010-09-22 01:41:38,214 DEBUG: install progress statusChange fglrx 44.444400
2010-09-22 01:41:38,278 DEBUG: install progress statusChange fglrx 55.555600
2010-09-22 01:42:03,365 DEBUG: install progress statusChange fglrx 66.666700
2010-09-22 01:42:03,591 DEBUG: install progress statusChange python-gmenu 66.666700
2010-09-22 01:42:03,776 DEBUG: install progress statusChange fglrx-amdcccle 66.666700
2010-09-22 01:42:03,794 DEBUG: install progress statusChange fglrx-amdcccle 77.777800
2010-09-22 01:42:03,795 DEBUG: install progress statusChange fglrx-amdcccle 88.888900
2010-09-22 01:42:03,812 DEBUG: install progress statusChange fglrx-amdcccle 100.000000
2010-09-22 01:42:03,847 DEBUG: install progress statusChange initramfs-tools 100.000000
2010-09-22 01:42:11,844 DEBUG: install progress statusChange libc-bin 100.000000
2010-09-22 01:42:12,023 DEBUG: install progress statusChange python-support 100.000000
2010-09-22 01:42:12,425 DEBUG: Setting up dkms (2.1.1.2-2fakesync1) ...

Setting up fglrx (2:8.723.1-0ubuntu4) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/GL.conf (gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
Loading new fglrx-8.723.1 DKMS files...
First Installation: checking all kernels...
Building only for 2.6.32-25-generic
Building for architecture i686
Building initial module for 2.6.32-24-generic-pae
Done.

fglrx.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.32-24-generic-pae/updates/dkms/

depmod......

DKMS: install Completed.
update-initramfs: deferring update (trigger activated)

Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.POSIX.cache...
Setting up fglrx-amdcccle (2:8.723.1-0ubuntu4) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-24-generic-pae
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...

2010-09-22 01:42:12,567 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not open /lib/modules/2.6.32-25-generic/modules.dep

2010-09-22 01:42:12,568 WARNING: /sys/module/fglrx/drivers does not exist, cannot rebind fglrx driver
2010-09-22 01:42:12,568 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2010-09-22 01:42:19,851 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-09-22 01:42:19,926 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-09-22 01:52:32,291 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-09-22 01:52:32,356 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-09-22 01:52:48,031 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-09-22 01:52:48,102 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-09-22 01:52:54,205 DEBUG: Installing package: linux-headers-2.6.32-25-generic
2010-09-22 01:52:54,398 DEBUG: Package linux-headers-2.6.32-25-generic does not exist, aborting
2010-09-22 01:52:54,586 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not open /lib/modules/2.6.32-25-generic/modules.dep

2010-09-22 01:52:54,587 WARNING: /sys/module/fglrx/drivers does not exist, cannot rebind fglrx driver
2010-09-22 01:52:54,587 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2010-09-22 01:53:01,893 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-09-22 01:53:01,959 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-09-22 01:59:44,503 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-09-22 01:59:44,580 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-09-22 01:59:44,701 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-09-22 01:59:44,788 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-09-22 01:59:44,950 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-09-22 01:59:45,014 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-09-22 01:59:47,250 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-09-22 01:59:47,316 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-09-22 01:59:50,498 DEBUG: Installing package: linux-headers-2.6.32-25-generic
2010-09-22 01:59:50,693 DEBUG: Package linux-headers-2.6.32-25-generic does not exist, aborting
2010-09-22 01:59:50,877 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not open /lib/modules/2.6.32-25-generic/modules.dep

2010-09-22 01:59:50,878 WARNING: /sys/module/fglrx/drivers does not exist, cannot rebind fglrx driver
2010-09-22 01:59:50,879 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2010-09-22 01:59:58,142 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-09-22 01:59:58,207 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches

```

Also my sound doesn't work. Everything i've found that i could type into terminal to diagnose the problem results in not found.

To be honest, i'm extremely annoyed and disappointed that a graphics card upgrade has resulted in a full reinstall of the operating system, and despite that it still doesn't work.

Yet from the first second it was inserted it's worked faultlessly in windows. I'm in serious danger of losing the faith here.

---

### Post by 23dornot23d on 2010-09-21
I had a search around .... and cannot see any major problems that people are facing with this card and as you have it running in Windows its not a power supply problem.

The only advice I can give is to try another driver ..... [LINK]("http://www.opendrivers.com/driver/2126308/ati-radeon-hd-5570-driver-10.6-linux-x86-x64-free-download.html")

You say you are running the latest UBUNTU can you do this and post the result ....

uname -a

---

### Post by memsb on 2010-09-21
I restarted the system again. As before it loaded the very basic GUI with no desktop icons and accepted no keyboard or mouse input.

I've twice since installed 32Bit Ubuntu from the downloads page via a USB pen drive. Every time the reformat -> installation finishes and the system restarts it seems to boot as normal, but then stops at a black screen just before the desktop would normally appear.

I created the USB stick on Windows 7 using:

[http://www.pendrivelinux.com/downloads/Universal-USB-Installer/Universal-USB-Installer.exe](http://www.pendrivelinux.com/downloads/Universal-USB-Installer/Universal-USB-Installer.exe)

File system: Ext4
Install location: /
Format: Yes.

The only thing i can think of is that when attempting to use a default or downloaded driver ubuntu locks up.

So far i've spent over 15 hours on this and reinstalled the operating system 6 times. Pretty disgraceful just to get a graphics card upgrade to work.

---

### Post by lkjoel on 2010-09-24
> **memsb said:**
> I'm running the latest version of Ubuntu and have been for a while now without issue. However today (actually now yesterday) i made the giant mistake of upgrading my on board HD3150 graphics to a PCIe HD5570 since then my whole life has fallen to bits.

First i noticed some visual noise on the screen. Concluding this was due to incorrect or out of date drivers i attempted to update them from the Hardware Drivers section. This gave the error:

SystemError: installArchives() failed

Activating from the command line using jockey gave the same error.

Deciding a reboot might be needed i did so. On power up all ubuntu and recovery modes produced an unskinned GUI with no desktop icons that responded to no mouse or keyboard input.

I was forced to reinstall the operating system.

On reinstalling and losing everything i had installed previously (it's going to take many days to get that all back and working again!), i still have the screen noise, have still been getting the same errors on attempting to activate the drivers, except now i also get this:

Sorry, the installation of this driver failed.

Please have a look at the log file for details.: /var/log/jockey.log
...
Also my sound doesn't work. Everything i've found that i could type into terminal to diagnose the problem results in not found.

To be honest, i'm extremely annoyed and disappointed that a graphics card upgrade has resulted in a full reinstall of the operating system, and despite that it still doesn't work.

Yet from the first second it was inserted it's worked faultlessly in windows. I'm in serious danger of losing the faith here.
Try Fix your sound! in my signature.
Then use Post-Fix your sound! in my signature.

---

