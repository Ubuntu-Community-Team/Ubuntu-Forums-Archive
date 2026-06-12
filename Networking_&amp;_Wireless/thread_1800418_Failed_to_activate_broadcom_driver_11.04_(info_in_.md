---
title: "Failed to activate broadcom driver 11.04: (info in page)"
date: 2011-07-08
forum: Networking &amp; Wireless
---

### Post by Ravenlynn12 on 2011-07-08
**SIDENOTE: I have tried to use the solutions provided on the stickied page of the top of the networking troubleshooting, including manual attempts to install the drivers. If you happen to have information pertaining to issues I may have missed, or information on how to understand these bloody logs; please message me or leave a comment below.**

Driver Activation Information: Broadcom STA driver

This package contains Broadcom 802.11 Linux STA wireless driverfor use with Broadcom's BCM4311-, BCM4312-, BCM4313-, BCM4321-,BCM4322-, BCM43224-, and BCM43225-, BCM43227- and BCM43228-basedhardware.


[B]WARNING: BELOW IS THE JOCKEY.LOG file located in /var/logs
IT IS LONG



[/B]```

2011-07-08 22:03:45,981 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x9046aec>
2011-07-08 22:03:49,822 DEBUG: reading modalias file /lib/modules/2.6.38-8-generic-pae/modules.alias
2011-07-08 22:03:49,974 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2011-07-08 22:03:49,982 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-07-08 22:03:50,022 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2011-07-08 22:03:50,045 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-07-08 22:03:50,090 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-07-08 22:03:50,112 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2011-07-08 22:03:50,113 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2011-07-08 22:03:50,113 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2011-07-08 22:03:50,157 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-07-08 22:03:50,158 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2011-07-08 22:03:50,158 DEBUG: fglrx.available: falling back to default
2011-07-08 22:03:50,312 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2011-07-08 22:03:50,312 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2011-07-08 22:03:50,355 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2011-07-08 22:03:50,392 DEBUG: Software modem not available
2011-07-08 22:03:50,392 DEBUG: loading custom handler /usr/share/jockey/handlers/nouveau3d.py
2011-07-08 22:03:50,496 DEBUG: Instantiated Handler subclass __builtin__.Nouveau3DHandler from name Nouveau3DHandler
2011-07-08 22:03:50,497 DEBUG: Experimental 3D support for NVIDIA cards not available
2011-07-08 22:03:50,497 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2011-07-08 22:03:50,545 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2011-07-08 22:03:50,545 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2011-07-08 22:03:50,572 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2011-07-08 22:03:50,573 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2011-07-08 22:03:50,632 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2011-07-08 22:03:50,633 DEBUG: Firmware for DVB cards not available
2011-07-08 22:03:50,633 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2011-07-08 22:03:50,639 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2011-07-08 22:03:50,640 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2011-07-08 22:03:50,640 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2011-07-08 22:03:50,640 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2011-07-08 22:03:50,669 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2011-07-08 22:03:50,671 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2011-07-08 22:03:50,671 DEBUG: nvidia.available: falling back to default
2011-07-08 22:03:50,701 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI xorg-video-abi-8 does not match X.org video ABI xorg-video-abi-10
2011-07-08 22:03:50,702 DEBUG: NVIDIA accelerated graphics driver not available
2011-07-08 22:03:50,707 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-07-08 22:03:50,707 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2011-07-08 22:03:50,708 DEBUG: nvidia.available: falling back to default
2011-07-08 22:03:50,780 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-07-08 22:03:50,781 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 947, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2011-07-08 22:03:50,869 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-07-08 22:03:50,869 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2011-07-08 22:03:50,870 DEBUG: nvidia.available: falling back to default
2011-07-08 22:03:50,927 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-07-08 22:03:50,927 DEBUG: all custom handlers loaded
2011-07-08 22:03:50,927 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9046aec> about HardwareID('modalias', 'pci:v00008086d00002937sv00001028sd000002BEbc0Csc03i00')
2011-07-08 22:03:51,273 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9046aec> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-07-08 22:03:51,451 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:03:51,451 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9046aec> about HardwareID('modalias', 'pci:v00001180d00000592sv00001028sd000002BEbc08sc80i00')
2011-07-08 22:03:51,456 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9046aec> about HardwareID('modalias', 'pci:v00001180d00000822sv00001028sd000002BEbc08sc05i01')
2011-07-08 22:03:51,457 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:03:51,457 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:03:51,457 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9046aec> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-07-08 22:03:51,457 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9046aec> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-07-08 22:03:51,457 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9046aec> about HardwareID('modalias', 'pci:v00008086d00002938sv00001028sd000002BEbc0Csc03i00')
2011-07-08 22:03:51,461 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9046aec> about HardwareID('modalias', 'platform:reg-dummy')
2011-07-08 22:03:51,462 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9046aec> about HardwareID('modalias', 'input:b0003v0C45p6416eA115-e0,1,kD4,ramlsfw')
2011-07-08 22:03:51,463 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:03:51,463 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9046aec> about HardwareID('modalias', 'platform:pcspkr')
2011-07-08 22:03:51,463 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:03:51,464 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:03:51,464 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9046aec> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2011-07-08 22:03:51,494 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9046aec> about HardwareID('modalias', 'pci:v00001180d00000852sv00001028sd000002BEbc08sc80i00')
2011-07-08 22:03:51,494 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r852', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:03:51,494 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9046aec> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,F0,ram4,l0,1,2,sfw')
2011-07-08 22:03:51,495 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:03:51,495 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9046aec> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2011-07-08 22:03:51,495 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9046aec> about HardwareID('modalias', 'pci:v00008086d00002919sv00001028sd000002BEbc06sc01i00')
2011-07-08 22:03:51,498 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:03:51,499 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9046aec> about HardwareID('modalias', 'platform:dell-laptop')
2011-07-08 22:03:51,499 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9046aec> about HardwareID('modalias', 'pci:v00008086d00002935sv00001028sd000002BEbc0Csc03i00')
2011-07-08 22:03:51,503 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9046aec> about HardwareID('modalias', 'platform:dcdbas')
2011-07-08 22:03:51,503 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9046aec> about HardwareID('modalias', 'wmi:A3776CE0-1E88-11DB-A98B-0800200C9A66')
2011-07-08 22:03:51,504 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9046aec> about HardwareID('modalias', 'pci:v00008086d00002A42sv00001028sd000002BEbc03sc00i00')
2011-07-08 22:03:51,507 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:03:51,507 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9046aec> about HardwareID('modalias', 'wmi:A80593CE-A997-11DA-B012-B622A1EF5492')
2011-07-08 22:03:51,508 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9046aec> about HardwareID('modalias', 'pci:v00008086d0000293Csv00001028sd000002BEbc0Csc03i20')
2011-07-08 22:03:51,511 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9046aec> about HardwareID('modalias', 'acpi:PNP0000:')
2011-07-08 22:03:51,511 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9046aec> about HardwareID('modalias', 'pci:v00008086d00002A43sv00001028sd000002BEbc03sc80i00')
2011-07-08 22:03:51,515 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9046aec> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-07-08 22:03:51,515 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9046aec> about HardwareID('modalias', 'pci:v00008086d0000293Esv00001028sd000002BEbc04sc03i00')
2011-07-08 22:03:51,518 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:03:51,518 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9046aec> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-07-08 22:03:51,519 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9046aec> about HardwareID('modalias', 'acpi:PNP0F13:')
2011-07-08 22:03:51,519 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9046aec> about HardwareID('modalias', 'pci:v00008086d00002930sv00001028sd000002BEbc0Csc05i00')
2011-07-08 22:03:51,522 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:03:51,522 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9046aec> about HardwareID('modalias', 'pci:v000014E4d00001698sv00001028sd000002BEbc02sc00i00')
2011-07-08 22:03:51,579 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'tg3', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:03:51,579 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9046aec> about HardwareID('modalias', 'pci:v00001180d00000832sv00001028sd000002BEbc0Csc00i10')
2011-07-08 22:03:51,580 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:03:51,580 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9046aec> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-07-08 22:03:51,580 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:03:51,580 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9046aec> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2011-07-08 22:03:51,581 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:03:51,581 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9046aec> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2011-07-08 22:03:51,581 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:03:51,581 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9046aec> about HardwareID('modalias', 'pci:v000014E4d00004315sv00001028sd0000000Cbc02sc80i00')
2011-07-08 22:03:51,587 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-07-08 22:03:51,588 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-07-08 22:03:51,588 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2011-07-08 22:03:51,589 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ssb', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:03:51,589 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'b43', 'jockey_handler': 'KernelModuleHandler', 'package': 'firmware-b43-lpphy-installer'}
2011-07-08 22:03:51,589 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9046aec> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA08:bd11/07/2009:svnDellInc.:pnStudio1555:pvrA08:rvnDellInc.:rn0D176M:rvrA08:cvnDellInc.:ct8:cvrA08:')
2011-07-08 22:03:51,608 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_laptop', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:03:51,608 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9046aec> about HardwareID('modalias', 'wmi:ABBC0F6C-8EA1-11D1-00A0-C90629100000')
2011-07-08 22:03:51,608 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9046aec> about HardwareID('modalias', 'acpi:PNP0100:')
2011-07-08 22:03:51,609 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9046aec> about HardwareID('modalias', 'wmi:ABBC0F6D-8EA1-11D1-00A0-C90629100000')
2011-07-08 22:03:51,609 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9046aec> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2011-07-08 22:03:51,609 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:03:51,609 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9046aec> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2011-07-08 22:03:51,610 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'option', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:03:51,610 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9046aec> about HardwareID('modalias', 'usb:v0C45p6416dA115dcEFdsc02dp01ic0Eisc01ip00')
2011-07-08 22:03:51,656 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:03:51,656 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9046aec> about HardwareID('modalias', 'pci:v00008086d00002939sv00001028sd000002BEbc0Csc03i00')
2011-07-08 22:03:51,660 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9046aec> about HardwareID('modalias', 'acpi:PNP0303:')
2011-07-08 22:03:51,660 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9046aec> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2011-07-08 22:03:51,663 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9046aec> about HardwareID('modalias', 'wmi:9DBB5994-A997-11DA-B012-B622A1EF5492')
2011-07-08 22:03:51,664 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_wmi', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:03:51,664 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9046aec> about HardwareID('modalias', 'pci:v00008086d0000293Asv00001028sd000002BEbc0Csc03i20')
2011-07-08 22:03:51,667 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9046aec> about HardwareID('modalias', 'pci:v00008086d00002934sv00001028sd000002BEbc0Csc03i00')
2011-07-08 22:03:51,671 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9046aec> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-07-08 22:03:51,671 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9046aec> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2011-07-08 22:03:51,672 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:03:51,672 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:03:51,672 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:03:51,672 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:03:51,673 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9046aec> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2011-07-08 22:03:51,673 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9046aec> about HardwareID('modalias', 'usb:v0C45p6416dA115dcEFdsc02dp01ic0Eisc02ip00')
2011-07-08 22:03:51,674 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9046aec> about HardwareID('modalias', 'wmi:8D9DDCBC-A997-11DA-B012-B622A1EF5492')
2011-07-08 22:03:51,674 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9046aec> about HardwareID('modalias', 'platform:eisa')
2011-07-08 22:03:51,674 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9046aec> about HardwareID('modalias', 'pci:v00008086d00002929sv00001028sd000002BEbc01sc06i01')
2011-07-08 22:03:51,678 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:03:51,678 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:03:51,678 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9046aec> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-07-08 22:03:51,690 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:03:51,690 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:03:51,690 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9046aec> about HardwareID('modalias', 'pci:v00008086d00002936sv00001028sd000002BEbc0Csc03i00')
2011-07-08 22:03:51,693 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9046aec> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,k94,95,A1,E0,E1,E3,EC,EE,F0,ram4,lsfw')
2011-07-08 22:03:51,694 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:03:51,694 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9046aec> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-07-08 22:03:51,694 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:03:51,694 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9046aec> about HardwareID('modalias', 'acpi:PNP0200:')
2011-07-08 22:03:51,695 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x905092c> about HardwareID('modalias', 'pci:v00008086d00002937sv00001028sd000002BEbc0Csc03i00')
2011-07-08 22:03:51,695 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x905092c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-07-08 22:03:51,695 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x905092c> about HardwareID('modalias', 'pci:v00001180d00000592sv00001028sd000002BEbc08sc80i00')
2011-07-08 22:03:51,695 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x905092c> about HardwareID('modalias', 'pci:v00001180d00000822sv00001028sd000002BEbc08sc05i01')
2011-07-08 22:03:51,695 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x905092c> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-07-08 22:03:51,695 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x905092c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-07-08 22:03:51,696 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x905092c> about HardwareID('modalias', 'pci:v00008086d00002938sv00001028sd000002BEbc0Csc03i00')
2011-07-08 22:03:51,696 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x905092c> about HardwareID('modalias', 'platform:reg-dummy')
2011-07-08 22:03:51,696 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x905092c> about HardwareID('modalias', 'input:b0003v0C45p6416eA115-e0,1,kD4,ramlsfw')
2011-07-08 22:03:51,696 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x905092c> about HardwareID('modalias', 'platform:pcspkr')
2011-07-08 22:03:51,696 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x905092c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2011-07-08 22:03:51,696 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x905092c> about HardwareID('modalias', 'pci:v00001180d00000852sv00001028sd000002BEbc08sc80i00')
2011-07-08 22:03:51,696 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x905092c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,F0,ram4,l0,1,2,sfw')
2011-07-08 22:03:51,696 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x905092c> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2011-07-08 22:03:51,697 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x905092c> about HardwareID('modalias', 'pci:v00008086d00002919sv00001028sd000002BEbc06sc01i00')
2011-07-08 22:03:51,697 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x905092c> about HardwareID('modalias', 'platform:dell-laptop')
2011-07-08 22:03:51,697 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x905092c> about HardwareID('modalias', 'pci:v00008086d00002935sv00001028sd000002BEbc0Csc03i00')
2011-07-08 22:03:51,697 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x905092c> about HardwareID('modalias', 'platform:dcdbas')
2011-07-08 22:03:51,697 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x905092c> about HardwareID('modalias', 'wmi:A3776CE0-1E88-11DB-A98B-0800200C9A66')
2011-07-08 22:03:51,697 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x905092c> about HardwareID('modalias', 'pci:v00008086d00002A42sv00001028sd000002BEbc03sc00i00')
2011-07-08 22:03:51,697 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x905092c> about HardwareID('modalias', 'wmi:A80593CE-A997-11DA-B012-B622A1EF5492')
2011-07-08 22:03:51,697 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x905092c> about HardwareID('modalias', 'pci:v00008086d0000293Csv00001028sd000002BEbc0Csc03i20')
2011-07-08 22:03:51,698 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x905092c> about HardwareID('modalias', 'acpi:PNP0000:')
2011-07-08 22:03:51,698 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x905092c> about HardwareID('modalias', 'pci:v00008086d00002A43sv00001028sd000002BEbc03sc80i00')
2011-07-08 22:03:51,698 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x905092c> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-07-08 22:03:51,698 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x905092c> about HardwareID('modalias', 'pci:v00008086d0000293Esv00001028sd000002BEbc04sc03i00')
2011-07-08 22:03:51,698 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x905092c> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-07-08 22:03:51,698 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x905092c> about HardwareID('modalias', 'acpi:PNP0F13:')
2011-07-08 22:03:51,698 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x905092c> about HardwareID('modalias', 'pci:v00008086d00002930sv00001028sd000002BEbc0Csc05i00')
2011-07-08 22:03:51,699 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x905092c> about HardwareID('modalias', 'pci:v000014E4d00001698sv00001028sd000002BEbc02sc00i00')
2011-07-08 22:03:51,699 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x905092c> about HardwareID('modalias', 'pci:v00001180d00000832sv00001028sd000002BEbc0Csc00i10')
2011-07-08 22:03:51,699 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x905092c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-07-08 22:03:51,699 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x905092c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2011-07-08 22:03:51,699 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x905092c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2011-07-08 22:03:51,699 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x905092c> about HardwareID('modalias', 'pci:v000014E4d00004315sv00001028sd0000000Cbc02sc80i00')
2011-07-08 22:03:51,699 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x905092c> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA08:bd11/07/2009:svnDellInc.:pnStudio1555:pvrA08:rvnDellInc.:rn0D176M:rvrA08:cvnDellInc.:ct8:cvrA08:')
2011-07-08 22:03:51,699 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x905092c> about HardwareID('modalias', 'wmi:ABBC0F6C-8EA1-11D1-00A0-C90629100000')
2011-07-08 22:03:51,700 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x905092c> about HardwareID('modalias', 'acpi:PNP0100:')
2011-07-08 22:03:51,700 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x905092c> about HardwareID('modalias', 'wmi:ABBC0F6D-8EA1-11D1-00A0-C90629100000')
2011-07-08 22:03:51,700 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x905092c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2011-07-08 22:03:51,700 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x905092c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2011-07-08 22:03:51,700 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x905092c> about HardwareID('modalias', 'usb:v0C45p6416dA115dcEFdsc02dp01ic0Eisc01ip00')
2011-07-08 22:03:51,700 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x905092c> about HardwareID('modalias', 'pci:v00008086d00002939sv00001028sd000002BEbc0Csc03i00')
2011-07-08 22:03:51,700 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x905092c> about HardwareID('modalias', 'acpi:PNP0303:')
2011-07-08 22:03:51,700 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x905092c> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2011-07-08 22:03:51,701 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x905092c> about HardwareID('modalias', 'wmi:9DBB5994-A997-11DA-B012-B622A1EF5492')
2011-07-08 22:03:51,701 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x905092c> about HardwareID('modalias', 'pci:v00008086d0000293Asv00001028sd000002BEbc0Csc03i20')
2011-07-08 22:03:51,701 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x905092c> about HardwareID('modalias', 'pci:v00008086d00002934sv00001028sd000002BEbc0Csc03i00')
2011-07-08 22:03:51,701 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x905092c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-07-08 22:03:51,701 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x905092c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2011-07-08 22:03:51,701 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x905092c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2011-07-08 22:03:51,701 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x905092c> about HardwareID('modalias', 'usb:v0C45p6416dA115dcEFdsc02dp01ic0Eisc02ip00')
2011-07-08 22:03:51,701 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x905092c> about HardwareID('modalias', 'wmi:8D9DDCBC-A997-11DA-B012-B622A1EF5492')
2011-07-08 22:03:51,702 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x905092c> about HardwareID('modalias', 'platform:eisa')
2011-07-08 22:03:51,702 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x905092c> about HardwareID('modalias', 'pci:v00008086d00002929sv00001028sd000002BEbc01sc06i01')
2011-07-08 22:03:51,702 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x905092c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-07-08 22:03:51,702 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x905092c> about HardwareID('modalias', 'pci:v00008086d00002936sv00001028sd000002BEbc0Csc03i00')
2011-07-08 22:03:51,702 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x905092c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,k94,95,A1,E0,E1,E3,EC,EE,F0,ram4,lsfw')
2011-07-08 22:03:51,702 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x905092c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-07-08 22:03:51,702 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x905092c> about HardwareID('modalias', 'acpi:PNP0200:')
2011-07-08 22:03:51,739 DEBUG: handler kmod:wl previously unseen
2011-07-08 22:03:51,739 DEBUG: writing back check cache /var/cache/jockey/check
2011-07-08 22:03:51,740 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-07-08 22:03:51,755 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-07-08 22:03:56,753 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-07-08 22:03:56,868 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-07-08 22:03:56,908 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-07-08 22:04:01,538 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-07-08 22:04:15,085 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-07-08 22:04:15,086 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2011-07-08 22:04:15,207 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-07-08 22:04:38,543 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-07-08 22:04:38,568 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-07-08 22:04:38,600 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-07-08 22:04:40,795 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-07-08 22:04:42,289 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-07-08 22:04:42,618 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-07-08 22:04:42,618 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2011-07-08 22:04:42,657 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-07-08 22:04:45,927 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-07-08 22:04:45,953 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-07-08 22:04:45,986 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-07-08 22:04:47,837 DEBUG: Shutting down
2011-07-08 22:06:25,640 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x924caec>
2011-07-08 22:06:27,527 DEBUG: reading modalias file /lib/modules/2.6.38-8-generic-pae/modules.alias
2011-07-08 22:06:27,639 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2011-07-08 22:06:27,639 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-07-08 22:06:27,678 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2011-07-08 22:06:27,697 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-07-08 22:06:27,702 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-07-08 22:06:27,729 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2011-07-08 22:06:27,730 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2011-07-08 22:06:27,730 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2011-07-08 22:06:27,739 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-07-08 22:06:27,739 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2011-07-08 22:06:27,739 DEBUG: fglrx.available: falling back to default
2011-07-08 22:06:27,830 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2011-07-08 22:06:27,830 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2011-07-08 22:06:27,856 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2011-07-08 22:06:27,870 DEBUG: Software modem not available
2011-07-08 22:06:27,870 DEBUG: loading custom handler /usr/share/jockey/handlers/nouveau3d.py
2011-07-08 22:06:27,897 DEBUG: Instantiated Handler subclass __builtin__.Nouveau3DHandler from name Nouveau3DHandler
2011-07-08 22:06:27,897 DEBUG: Experimental 3D support for NVIDIA cards not available
2011-07-08 22:06:27,898 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2011-07-08 22:06:27,902 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2011-07-08 22:06:27,902 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2011-07-08 22:06:27,924 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2011-07-08 22:06:27,924 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2011-07-08 22:06:27,953 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2011-07-08 22:06:27,954 DEBUG: Firmware for DVB cards not available
2011-07-08 22:06:27,954 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2011-07-08 22:06:27,959 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2011-07-08 22:06:27,960 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2011-07-08 22:06:27,960 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2011-07-08 22:06:27,960 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2011-07-08 22:06:27,967 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2011-07-08 22:06:27,968 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2011-07-08 22:06:27,968 DEBUG: nvidia.available: falling back to default
2011-07-08 22:06:27,990 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI xorg-video-abi-8 does not match X.org video ABI xorg-video-abi-10
2011-07-08 22:06:27,991 DEBUG: NVIDIA accelerated graphics driver not available
2011-07-08 22:06:27,995 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-07-08 22:06:27,996 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2011-07-08 22:06:27,996 DEBUG: nvidia.available: falling back to default
2011-07-08 22:06:28,038 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-07-08 22:06:28,038 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 947, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2011-07-08 22:06:28,043 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-07-08 22:06:28,043 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2011-07-08 22:06:28,044 DEBUG: nvidia.available: falling back to default
2011-07-08 22:06:28,087 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-07-08 22:06:28,087 DEBUG: all custom handlers loaded
2011-07-08 22:06:28,088 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x924caec> about HardwareID('modalias', 'pci:v00008086d00002937sv00001028sd000002BEbc0Csc03i00')
2011-07-08 22:06:28,387 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x924caec> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-07-08 22:06:28,460 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:06:28,461 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x924caec> about HardwareID('modalias', 'pci:v00001180d00000592sv00001028sd000002BEbc08sc80i00')
2011-07-08 22:06:28,465 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x924caec> about HardwareID('modalias', 'pci:v00001180d00000822sv00001028sd000002BEbc08sc05i01')
2011-07-08 22:06:28,465 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:06:28,466 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:06:28,466 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x924caec> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-07-08 22:06:28,466 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x924caec> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-07-08 22:06:28,466 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x924caec> about HardwareID('modalias', 'pci:v00008086d00002938sv00001028sd000002BEbc0Csc03i00')
2011-07-08 22:06:28,470 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x924caec> about HardwareID('modalias', 'platform:reg-dummy')
2011-07-08 22:06:28,470 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x924caec> about HardwareID('modalias', 'input:b0003v0C45p6416eA115-e0,1,kD4,ramlsfw')
2011-07-08 22:06:28,471 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:06:28,471 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x924caec> about HardwareID('modalias', 'platform:pcspkr')
2011-07-08 22:06:28,471 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:06:28,472 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:06:28,472 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x924caec> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2011-07-08 22:06:28,497 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x924caec> about HardwareID('modalias', 'pci:v00001180d00000852sv00001028sd000002BEbc08sc80i00')
2011-07-08 22:06:28,498 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r852', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:06:28,498 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x924caec> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,F0,ram4,l0,1,2,sfw')
2011-07-08 22:06:28,498 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:06:28,498 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x924caec> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2011-07-08 22:06:28,499 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x924caec> about HardwareID('modalias', 'pci:v00008086d00002919sv00001028sd000002BEbc06sc01i00')
2011-07-08 22:06:28,502 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:06:28,502 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x924caec> about HardwareID('modalias', 'platform:dell-laptop')
2011-07-08 22:06:28,502 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x924caec> about HardwareID('modalias', 'pci:v00008086d00002935sv00001028sd000002BEbc0Csc03i00')
2011-07-08 22:06:28,506 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x924caec> about HardwareID('modalias', 'platform:dcdbas')
2011-07-08 22:06:28,506 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x924caec> about HardwareID('modalias', 'wmi:A3776CE0-1E88-11DB-A98B-0800200C9A66')
2011-07-08 22:06:28,506 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x924caec> about HardwareID('modalias', 'pci:v00008086d00002A42sv00001028sd000002BEbc03sc00i00')
2011-07-08 22:06:28,510 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:06:28,510 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x924caec> about HardwareID('modalias', 'wmi:A80593CE-A997-11DA-B012-B622A1EF5492')
2011-07-08 22:06:28,510 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x924caec> about HardwareID('modalias', 'pci:v00008086d0000293Csv00001028sd000002BEbc0Csc03i20')
2011-07-08 22:06:28,513 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x924caec> about HardwareID('modalias', 'acpi:PNP0000:')
2011-07-08 22:06:28,513 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x924caec> about HardwareID('modalias', 'pci:v00008086d00002A43sv00001028sd000002BEbc03sc80i00')
2011-07-08 22:06:28,516 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x924caec> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-07-08 22:06:28,517 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x924caec> about HardwareID('modalias', 'pci:v00008086d0000293Esv00001028sd000002BEbc04sc03i00')
2011-07-08 22:06:28,520 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:06:28,520 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x924caec> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-07-08 22:06:28,520 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x924caec> about HardwareID('modalias', 'acpi:PNP0F13:')
2011-07-08 22:06:28,520 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x924caec> about HardwareID('modalias', 'pci:v00008086d00002930sv00001028sd000002BEbc0Csc05i00')
2011-07-08 22:06:28,524 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:06:28,524 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x924caec> about HardwareID('modalias', 'pci:v000014E4d00001698sv00001028sd000002BEbc02sc00i00')
2011-07-08 22:06:28,574 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'tg3', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:06:28,574 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x924caec> about HardwareID('modalias', 'pci:v00001180d00000832sv00001028sd000002BEbc0Csc00i10')
2011-07-08 22:06:28,575 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:06:28,575 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x924caec> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-07-08 22:06:28,575 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:06:28,575 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x924caec> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2011-07-08 22:06:28,575 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:06:28,575 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x924caec> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2011-07-08 22:06:28,576 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:06:28,576 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x924caec> about HardwareID('modalias', 'pci:v000014E4d00004315sv00001028sd0000000Cbc02sc80i00')
2011-07-08 22:06:28,580 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-07-08 22:06:28,581 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-07-08 22:06:28,581 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2011-07-08 22:06:28,582 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ssb', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:06:28,582 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'b43', 'jockey_handler': 'KernelModuleHandler', 'package': 'firmware-b43-lpphy-installer'}
2011-07-08 22:06:28,582 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x924caec> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA08:bd11/07/2009:svnDellInc.:pnStudio1555:pvrA08:rvnDellInc.:rn0D176M:rvrA08:cvnDellInc.:ct8:cvrA08:')
2011-07-08 22:06:28,600 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_laptop', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:06:28,600 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x924caec> about HardwareID('modalias', 'wmi:ABBC0F6C-8EA1-11D1-00A0-C90629100000')
2011-07-08 22:06:28,601 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x924caec> about HardwareID('modalias', 'acpi:PNP0100:')
2011-07-08 22:06:28,601 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x924caec> about HardwareID('modalias', 'wmi:ABBC0F6D-8EA1-11D1-00A0-C90629100000')
2011-07-08 22:06:28,601 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x924caec> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2011-07-08 22:06:28,601 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:06:28,601 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x924caec> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2011-07-08 22:06:28,602 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'option', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:06:28,602 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x924caec> about HardwareID('modalias', 'usb:v0C45p6416dA115dcEFdsc02dp01ic0Eisc01ip00')
2011-07-08 22:06:28,642 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:06:28,642 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x924caec> about HardwareID('modalias', 'pci:v00008086d00002939sv00001028sd000002BEbc0Csc03i00')
2011-07-08 22:06:28,646 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x924caec> about HardwareID('modalias', 'acpi:PNP0303:')
2011-07-08 22:06:28,646 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x924caec> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2011-07-08 22:06:28,649 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x924caec> about HardwareID('modalias', 'wmi:9DBB5994-A997-11DA-B012-B622A1EF5492')
2011-07-08 22:06:28,650 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_wmi', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:06:28,650 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x924caec> about HardwareID('modalias', 'pci:v00008086d0000293Asv00001028sd000002BEbc0Csc03i20')
2011-07-08 22:06:28,653 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x924caec> about HardwareID('modalias', 'pci:v00008086d00002934sv00001028sd000002BEbc0Csc03i00')
2011-07-08 22:06:28,656 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x924caec> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-07-08 22:06:28,657 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x924caec> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2011-07-08 22:06:28,657 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:06:28,657 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:06:28,657 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:06:28,657 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:06:28,658 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x924caec> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2011-07-08 22:06:28,658 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x924caec> about HardwareID('modalias', 'usb:v0C45p6416dA115dcEFdsc02dp01ic0Eisc02ip00')
2011-07-08 22:06:28,659 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x924caec> about HardwareID('modalias', 'wmi:8D9DDCBC-A997-11DA-B012-B622A1EF5492')
2011-07-08 22:06:28,659 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x924caec> about HardwareID('modalias', 'platform:eisa')
2011-07-08 22:06:28,659 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x924caec> about HardwareID('modalias', 'pci:v00008086d00002929sv00001028sd000002BEbc01sc06i01')
2011-07-08 22:06:28,663 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:06:28,663 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:06:28,663 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x924caec> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-07-08 22:06:28,673 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:06:28,673 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:06:28,673 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x924caec> about HardwareID('modalias', 'pci:v00008086d00002936sv00001028sd000002BEbc0Csc03i00')
2011-07-08 22:06:28,676 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x924caec> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,k94,95,A1,E0,E1,E3,EC,EE,F0,ram4,lsfw')
2011-07-08 22:06:28,677 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:06:28,677 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x924caec> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-07-08 22:06:28,677 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:06:28,677 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x924caec> about HardwareID('modalias', 'acpi:PNP0200:')
2011-07-08 22:06:28,677 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x925692c> about HardwareID('modalias', 'pci:v00008086d00002937sv00001028sd000002BEbc0Csc03i00')
2011-07-08 22:06:28,677 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x925692c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-07-08 22:06:28,678 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x925692c> about HardwareID('modalias', 'pci:v00001180d00000592sv00001028sd000002BEbc08sc80i00')
2011-07-08 22:06:28,678 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x925692c> about HardwareID('modalias', 'pci:v00001180d00000822sv00001028sd000002BEbc08sc05i01')
2011-07-08 22:06:28,678 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x925692c> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-07-08 22:06:28,678 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x925692c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-07-08 22:06:28,678 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x925692c> about HardwareID('modalias', 'pci:v00008086d00002938sv00001028sd000002BEbc0Csc03i00')
2011-07-08 22:06:28,678 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x925692c> about HardwareID('modalias', 'platform:reg-dummy')
2011-07-08 22:06:28,678 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x925692c> about HardwareID('modalias', 'input:b0003v0C45p6416eA115-e0,1,kD4,ramlsfw')
2011-07-08 22:06:28,678 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x925692c> about HardwareID('modalias', 'platform:pcspkr')
2011-07-08 22:06:28,678 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x925692c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2011-07-08 22:06:28,678 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x925692c> about HardwareID('modalias', 'pci:v00001180d00000852sv00001028sd000002BEbc08sc80i00')
2011-07-08 22:06:28,679 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x925692c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,F0,ram4,l0,1,2,sfw')
2011-07-08 22:06:28,679 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x925692c> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2011-07-08 22:06:28,679 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x925692c> about HardwareID('modalias', 'pci:v00008086d00002919sv00001028sd000002BEbc06sc01i00')
2011-07-08 22:06:28,679 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x925692c> about HardwareID('modalias', 'platform:dell-laptop')
2011-07-08 22:06:28,679 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x925692c> about HardwareID('modalias', 'pci:v00008086d00002935sv00001028sd000002BEbc0Csc03i00')
2011-07-08 22:06:28,679 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x925692c> about HardwareID('modalias', 'platform:dcdbas')
2011-07-08 22:06:28,679 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x925692c> about HardwareID('modalias', 'wmi:A3776CE0-1E88-11DB-A98B-0800200C9A66')
2011-07-08 22:06:28,679 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x925692c> about HardwareID('modalias', 'pci:v00008086d00002A42sv00001028sd000002BEbc03sc00i00')
2011-07-08 22:06:28,679 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x925692c> about HardwareID('modalias', 'wmi:A80593CE-A997-11DA-B012-B622A1EF5492')
2011-07-08 22:06:28,679 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x925692c> about HardwareID('modalias', 'pci:v00008086d0000293Csv00001028sd000002BEbc0Csc03i20')
2011-07-08 22:06:28,680 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x925692c> about HardwareID('modalias', 'acpi:PNP0000:')
2011-07-08 22:06:28,680 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x925692c> about HardwareID('modalias', 'pci:v00008086d00002A43sv00001028sd000002BEbc03sc80i00')
2011-07-08 22:06:28,680 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x925692c> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-07-08 22:06:28,680 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x925692c> about HardwareID('modalias', 'pci:v00008086d0000293Esv00001028sd000002BEbc04sc03i00')
2011-07-08 22:06:28,680 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x925692c> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-07-08 22:06:28,680 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x925692c> about HardwareID('modalias', 'acpi:PNP0F13:')
2011-07-08 22:06:28,680 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x925692c> about HardwareID('modalias', 'pci:v00008086d00002930sv00001028sd000002BEbc0Csc05i00')
2011-07-08 22:06:28,680 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x925692c> about HardwareID('modalias', 'pci:v000014E4d00001698sv00001028sd000002BEbc02sc00i00')
2011-07-08 22:06:28,680 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x925692c> about HardwareID('modalias', 'pci:v00001180d00000832sv00001028sd000002BEbc0Csc00i10')
2011-07-08 22:06:28,680 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x925692c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-07-08 22:06:28,681 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x925692c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2011-07-08 22:06:28,681 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x925692c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2011-07-08 22:06:28,681 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x925692c> about HardwareID('modalias', 'pci:v000014E4d00004315sv00001028sd0000000Cbc02sc80i00')
2011-07-08 22:06:28,681 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x925692c> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA08:bd11/07/2009:svnDellInc.:pnStudio1555:pvrA08:rvnDellInc.:rn0D176M:rvrA08:cvnDellInc.:ct8:cvrA08:')
2011-07-08 22:06:28,681 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x925692c> about HardwareID('modalias', 'wmi:ABBC0F6C-8EA1-11D1-00A0-C90629100000')
2011-07-08 22:06:28,681 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x925692c> about HardwareID('modalias', 'acpi:PNP0100:')
2011-07-08 22:06:28,681 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x925692c> about HardwareID('modalias', 'wmi:ABBC0F6D-8EA1-11D1-00A0-C90629100000')
2011-07-08 22:06:28,681 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x925692c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2011-07-08 22:06:28,681 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x925692c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2011-07-08 22:06:28,681 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x925692c> about HardwareID('modalias', 'usb:v0C45p6416dA115dcEFdsc02dp01ic0Eisc01ip00')
2011-07-08 22:06:28,681 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x925692c> about HardwareID('modalias', 'pci:v00008086d00002939sv00001028sd000002BEbc0Csc03i00')
2011-07-08 22:06:28,682 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x925692c> about HardwareID('modalias', 'acpi:PNP0303:')
2011-07-08 22:06:28,682 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x925692c> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2011-07-08 22:06:28,682 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x925692c> about HardwareID('modalias', 'wmi:9DBB5994-A997-11DA-B012-B622A1EF5492')
2011-07-08 22:06:28,682 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x925692c> about HardwareID('modalias', 'pci:v00008086d0000293Asv00001028sd000002BEbc0Csc03i20')
2011-07-08 22:06:28,682 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x925692c> about HardwareID('modalias', 'pci:v00008086d00002934sv00001028sd000002BEbc0Csc03i00')
2011-07-08 22:06:28,682 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x925692c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-07-08 22:06:28,682 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x925692c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2011-07-08 22:06:28,682 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x925692c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2011-07-08 22:06:28,682 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x925692c> about HardwareID('modalias', 'usb:v0C45p6416dA115dcEFdsc02dp01ic0Eisc02ip00')
2011-07-08 22:06:28,682 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x925692c> about HardwareID('modalias', 'wmi:8D9DDCBC-A997-11DA-B012-B622A1EF5492')
2011-07-08 22:06:28,683 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x925692c> about HardwareID('modalias', 'platform:eisa')
2011-07-08 22:06:28,683 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x925692c> about HardwareID('modalias', 'pci:v00008086d00002929sv00001028sd000002BEbc01sc06i01')
2011-07-08 22:06:28,683 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x925692c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-07-08 22:06:28,683 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x925692c> about HardwareID('modalias', 'pci:v00008086d00002936sv00001028sd000002BEbc0Csc03i00')
2011-07-08 22:06:28,683 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x925692c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,k94,95,A1,E0,E1,E3,EC,EE,F0,ram4,lsfw')
2011-07-08 22:06:28,683 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x925692c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-07-08 22:06:28,683 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x925692c> about HardwareID('modalias', 'acpi:PNP0200:')
2011-07-08 22:06:28,739 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-07-08 22:06:28,773 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-07-08 22:06:28,802 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-07-08 22:06:32,889 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-07-08 22:06:34,490 DEBUG: Shutting down
2011-07-08 22:17:58,755 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x9fadaec>
2011-07-08 22:18:00,558 DEBUG: reading modalias file /lib/modules/2.6.38-8-generic-pae/modules.alias
2011-07-08 22:18:00,673 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2011-07-08 22:18:00,674 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-07-08 22:18:00,709 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2011-07-08 22:18:00,728 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-07-08 22:18:00,733 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-07-08 22:18:00,754 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2011-07-08 22:18:00,754 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2011-07-08 22:18:00,754 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2011-07-08 22:18:00,761 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-07-08 22:18:00,761 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2011-07-08 22:18:00,761 DEBUG: fglrx.available: falling back to default
2011-07-08 22:18:00,850 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2011-07-08 22:18:00,850 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2011-07-08 22:18:00,875 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2011-07-08 22:18:00,889 DEBUG: Software modem not available
2011-07-08 22:18:00,890 DEBUG: loading custom handler /usr/share/jockey/handlers/nouveau3d.py
2011-07-08 22:18:00,918 DEBUG: Instantiated Handler subclass __builtin__.Nouveau3DHandler from name Nouveau3DHandler
2011-07-08 22:18:00,918 DEBUG: Experimental 3D support for NVIDIA cards not available
2011-07-08 22:18:00,918 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2011-07-08 22:18:00,923 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2011-07-08 22:18:00,923 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2011-07-08 22:18:00,945 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2011-07-08 22:18:00,945 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2011-07-08 22:18:00,971 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2011-07-08 22:18:00,972 DEBUG: Firmware for DVB cards not available
2011-07-08 22:18:00,972 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2011-07-08 22:18:00,977 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2011-07-08 22:18:00,977 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2011-07-08 22:18:00,978 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2011-07-08 22:18:00,978 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2011-07-08 22:18:00,984 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2011-07-08 22:18:00,985 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2011-07-08 22:18:00,985 DEBUG: nvidia.available: falling back to default
2011-07-08 22:18:01,008 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI xorg-video-abi-8 does not match X.org video ABI xorg-video-abi-10
2011-07-08 22:18:01,009 DEBUG: NVIDIA accelerated graphics driver not available
2011-07-08 22:18:01,013 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-07-08 22:18:01,013 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2011-07-08 22:18:01,013 DEBUG: nvidia.available: falling back to default
2011-07-08 22:18:01,066 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-07-08 22:18:01,066 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 947, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2011-07-08 22:18:01,070 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-07-08 22:18:01,071 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2011-07-08 22:18:01,071 DEBUG: nvidia.available: falling back to default
2011-07-08 22:18:01,113 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-07-08 22:18:01,114 DEBUG: all custom handlers loaded
2011-07-08 22:18:01,114 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9fadaec> about HardwareID('modalias', 'pci:v00008086d00002937sv00001028sd000002BEbc0Csc03i00')
2011-07-08 22:18:01,414 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9fadaec> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-07-08 22:18:01,489 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:18:01,489 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9fadaec> about HardwareID('modalias', 'pci:v00001180d00000592sv00001028sd000002BEbc08sc80i00')
2011-07-08 22:18:01,494 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9fadaec> about HardwareID('modalias', 'pci:v00001180d00000822sv00001028sd000002BEbc08sc05i01')
2011-07-08 22:18:01,494 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:18:01,494 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:18:01,495 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9fadaec> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-07-08 22:18:01,495 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9fadaec> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-07-08 22:18:01,495 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9fadaec> about HardwareID('modalias', 'pci:v00008086d00002938sv00001028sd000002BEbc0Csc03i00')
2011-07-08 22:18:01,498 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9fadaec> about HardwareID('modalias', 'platform:reg-dummy')
2011-07-08 22:18:01,499 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9fadaec> about HardwareID('modalias', 'input:b0003v0C45p6416eA115-e0,1,kD4,ramlsfw')
2011-07-08 22:18:01,499 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:18:01,499 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9fadaec> about HardwareID('modalias', 'platform:pcspkr')
2011-07-08 22:18:01,500 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:18:01,500 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:18:01,500 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9fadaec> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2011-07-08 22:18:01,526 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9fadaec> about HardwareID('modalias', 'pci:v00001180d00000852sv00001028sd000002BEbc08sc80i00')
2011-07-08 22:18:01,526 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r852', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:18:01,527 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9fadaec> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,F0,ram4,l0,1,2,sfw')
2011-07-08 22:18:01,527 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:18:01,527 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9fadaec> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2011-07-08 22:18:01,527 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9fadaec> about HardwareID('modalias', 'pci:v00008086d00002919sv00001028sd000002BEbc06sc01i00')
2011-07-08 22:18:01,530 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:18:01,530 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9fadaec> about HardwareID('modalias', 'platform:dell-laptop')
2011-07-08 22:18:01,531 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9fadaec> about HardwareID('modalias', 'pci:v00008086d00002935sv00001028sd000002BEbc0Csc03i00')
2011-07-08 22:18:01,534 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9fadaec> about HardwareID('modalias', 'platform:dcdbas')
2011-07-08 22:18:01,535 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9fadaec> about HardwareID('modalias', 'wmi:A3776CE0-1E88-11DB-A98B-0800200C9A66')
2011-07-08 22:18:01,535 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9fadaec> about HardwareID('modalias', 'pci:v00008086d00002A42sv00001028sd000002BEbc03sc00i00')
2011-07-08 22:18:01,538 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:18:01,538 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9fadaec> about HardwareID('modalias', 'wmi:A80593CE-A997-11DA-B012-B622A1EF5492')
2011-07-08 22:18:01,539 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9fadaec> about HardwareID('modalias', 'pci:v00008086d0000293Csv00001028sd000002BEbc0Csc03i20')
2011-07-08 22:18:01,542 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9fadaec> about HardwareID('modalias', 'acpi:PNP0000:')
2011-07-08 22:18:01,542 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9fadaec> about HardwareID('modalias', 'pci:v00008086d00002A43sv00001028sd000002BEbc03sc80i00')
2011-07-08 22:18:01,545 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9fadaec> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-07-08 22:18:01,545 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9fadaec> about HardwareID('modalias', 'pci:v00008086d0000293Esv00001028sd000002BEbc04sc03i00')
2011-07-08 22:18:01,548 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:18:01,549 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9fadaec> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-07-08 22:18:01,549 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9fadaec> about HardwareID('modalias', 'acpi:PNP0F13:')
2011-07-08 22:18:01,549 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9fadaec> about HardwareID('modalias', 'pci:v00008086d00002930sv00001028sd000002BEbc0Csc05i00')
2011-07-08 22:18:01,552 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:18:01,552 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9fadaec> about HardwareID('modalias', 'pci:v000014E4d00001698sv00001028sd000002BEbc02sc00i00')
2011-07-08 22:18:01,602 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'tg3', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:18:01,602 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9fadaec> about HardwareID('modalias', 'pci:v00001180d00000832sv00001028sd000002BEbc0Csc00i10')
2011-07-08 22:18:01,602 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:18:01,602 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9fadaec> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-07-08 22:18:01,602 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:18:01,603 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9fadaec> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2011-07-08 22:18:01,603 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:18:01,603 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9fadaec> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2011-07-08 22:18:01,603 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:18:01,603 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9fadaec> about HardwareID('modalias', 'pci:v000014E4d00004315sv00001028sd0000000Cbc02sc80i00')
2011-07-08 22:18:01,608 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-07-08 22:18:01,609 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-07-08 22:18:01,608 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2011-07-08 22:18:01,609 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ssb', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:18:01,609 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'b43', 'jockey_handler': 'KernelModuleHandler', 'package': 'firmware-b43-lpphy-installer'}
2011-07-08 22:18:01,609 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9fadaec> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA08:bd11/07/2009:svnDellInc.:pnStudio1555:pvrA08:rvnDellInc.:rn0D176M:rvrA08:cvnDellInc.:ct8:cvrA08:')
2011-07-08 22:18:01,626 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_laptop', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:18:01,626 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9fadaec> about HardwareID('modalias', 'wmi:ABBC0F6C-8EA1-11D1-00A0-C90629100000')
2011-07-08 22:18:01,626 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9fadaec> about HardwareID('modalias', 'acpi:PNP0100:')
2011-07-08 22:18:01,626 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9fadaec> about HardwareID('modalias', 'wmi:ABBC0F6D-8EA1-11D1-00A0-C90629100000')
2011-07-08 22:18:01,626 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9fadaec> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2011-07-08 22:18:01,627 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:18:01,627 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9fadaec> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2011-07-08 22:18:01,627 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'option', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:18:01,628 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9fadaec> about HardwareID('modalias', 'usb:v0C45p6416dA115dcEFdsc02dp01ic0Eisc01ip00')
2011-07-08 22:18:01,668 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:18:01,668 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9fadaec> about HardwareID('modalias', 'pci:v00008086d00002939sv00001028sd000002BEbc0Csc03i00')
2011-07-08 22:18:01,672 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9fadaec> about HardwareID('modalias', 'acpi:PNP0303:')
2011-07-08 22:18:01,672 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9fadaec> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2011-07-08 22:18:01,675 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9fadaec> about HardwareID('modalias', 'wmi:9DBB5994-A997-11DA-B012-B622A1EF5492')
2011-07-08 22:18:01,676 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_wmi', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:18:01,676 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9fadaec> about HardwareID('modalias', 'pci:v00008086d0000293Asv00001028sd000002BEbc0Csc03i20')
2011-07-08 22:18:01,679 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9fadaec> about HardwareID('modalias', 'pci:v00008086d00002934sv00001028sd000002BEbc0Csc03i00')
2011-07-08 22:18:01,682 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9fadaec> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-07-08 22:18:01,683 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9fadaec> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2011-07-08 22:18:01,683 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:18:01,683 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:18:01,684 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:18:01,684 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:18:01,684 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9fadaec> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2011-07-08 22:18:01,684 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9fadaec> about HardwareID('modalias', 'usb:v0C45p6416dA115dcEFdsc02dp01ic0Eisc02ip00')
2011-07-08 22:18:01,685 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9fadaec> about HardwareID('modalias', 'wmi:8D9DDCBC-A997-11DA-B012-B622A1EF5492')
2011-07-08 22:18:01,685 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9fadaec> about HardwareID('modalias', 'platform:eisa')
2011-07-08 22:18:01,685 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9fadaec> about HardwareID('modalias', 'pci:v00008086d00002929sv00001028sd000002BEbc01sc06i01')
2011-07-08 22:18:01,689 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:18:01,689 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:18:01,689 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9fadaec> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-07-08 22:18:01,699 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:18:01,699 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:18:01,699 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9fadaec> about HardwareID('modalias', 'pci:v00008086d00002936sv00001028sd000002BEbc0Csc03i00')
2011-07-08 22:18:01,702 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9fadaec> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,k94,95,A1,E0,E1,E3,EC,EE,F0,ram4,lsfw')
2011-07-08 22:18:01,703 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:18:01,703 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9fadaec> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-07-08 22:18:01,703 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:18:01,703 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9fadaec> about HardwareID('modalias', 'acpi:PNP0200:')
2011-07-08 22:18:01,703 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fb792c> about HardwareID('modalias', 'pci:v00008086d00002937sv00001028sd000002BEbc0Csc03i00')
2011-07-08 22:18:01,703 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fb792c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-07-08 22:18:01,704 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fb792c> about HardwareID('modalias', 'pci:v00001180d00000592sv00001028sd000002BEbc08sc80i00')
2011-07-08 22:18:01,704 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fb792c> about HardwareID('modalias', 'pci:v00001180d00000822sv00001028sd000002BEbc08sc05i01')
2011-07-08 22:18:01,704 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fb792c> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-07-08 22:18:01,704 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fb792c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-07-08 22:18:01,704 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fb792c> about HardwareID('modalias', 'pci:v00008086d00002938sv00001028sd000002BEbc0Csc03i00')
2011-07-08 22:18:01,704 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fb792c> about HardwareID('modalias', 'platform:reg-dummy')
2011-07-08 22:18:01,704 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fb792c> about HardwareID('modalias', 'input:b0003v0C45p6416eA115-e0,1,kD4,ramlsfw')
2011-07-08 22:18:01,704 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fb792c> about HardwareID('modalias', 'platform:pcspkr')
2011-07-08 22:18:01,704 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fb792c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2011-07-08 22:18:01,704 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fb792c> about HardwareID('modalias', 'pci:v00001180d00000852sv00001028sd000002BEbc08sc80i00')
2011-07-08 22:18:01,704 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fb792c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,F0,ram4,l0,1,2,sfw')
2011-07-08 22:18:01,705 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fb792c> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2011-07-08 22:18:01,705 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fb792c> about HardwareID('modalias', 'pci:v00008086d00002919sv00001028sd000002BEbc06sc01i00')
2011-07-08 22:18:01,705 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fb792c> about HardwareID('modalias', 'platform:dell-laptop')
2011-07-08 22:18:01,705 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fb792c> about HardwareID('modalias', 'pci:v00008086d00002935sv00001028sd000002BEbc0Csc03i00')
2011-07-08 22:18:01,705 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fb792c> about HardwareID('modalias', 'platform:dcdbas')
2011-07-08 22:18:01,705 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fb792c> about HardwareID('modalias', 'wmi:A3776CE0-1E88-11DB-A98B-0800200C9A66')
2011-07-08 22:18:01,705 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fb792c> about HardwareID('modalias', 'pci:v00008086d00002A42sv00001028sd000002BEbc03sc00i00')
2011-07-08 22:18:01,705 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fb792c> about HardwareID('modalias', 'wmi:A80593CE-A997-11DA-B012-B622A1EF5492')
2011-07-08 22:18:01,705 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fb792c> about HardwareID('modalias', 'pci:v00008086d0000293Csv00001028sd000002BEbc0Csc03i20')
2011-07-08 22:18:01,705 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fb792c> about HardwareID('modalias', 'acpi:PNP0000:')
2011-07-08 22:18:01,706 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fb792c> about HardwareID('modalias', 'pci:v00008086d00002A43sv00001028sd000002BEbc03sc80i00')
2011-07-08 22:18:01,706 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fb792c> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-07-08 22:18:01,706 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fb792c> about HardwareID('modalias', 'pci:v00008086d0000293Esv00001028sd000002BEbc04sc03i00')
2011-07-08 22:18:01,706 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fb792c> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-07-08 22:18:01,706 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fb792c> about HardwareID('modalias', 'acpi:PNP0F13:')
2011-07-08 22:18:01,706 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fb792c> about HardwareID('modalias', 'pci:v00008086d00002930sv00001028sd000002BEbc0Csc05i00')
2011-07-08 22:18:01,706 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fb792c> about HardwareID('modalias', 'pci:v000014E4d00001698sv00001028sd000002BEbc02sc00i00')
2011-07-08 22:18:01,706 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fb792c> about HardwareID('modalias', 'pci:v00001180d00000832sv00001028sd000002BEbc0Csc00i10')
2011-07-08 22:18:01,706 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fb792c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-07-08 22:18:01,706 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fb792c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2011-07-08 22:18:01,707 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fb792c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2011-07-08 22:18:01,707 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fb792c> about HardwareID('modalias', 'pci:v000014E4d00004315sv00001028sd0000000Cbc02sc80i00')
2011-07-08 22:18:01,707 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fb792c> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA08:bd11/07/2009:svnDellInc.:pnStudio1555:pvrA08:rvnDellInc.:rn0D176M:rvrA08:cvnDellInc.:ct8:cvrA08:')
2011-07-08 22:18:01,707 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fb792c> about HardwareID('modalias', 'wmi:ABBC0F6C-8EA1-11D1-00A0-C90629100000')
2011-07-08 22:18:01,707 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fb792c> about HardwareID('modalias', 'acpi:PNP0100:')
2011-07-08 22:18:01,707 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fb792c> about HardwareID('modalias', 'wmi:ABBC0F6D-8EA1-11D1-00A0-C90629100000')
2011-07-08 22:18:01,707 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fb792c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2011-07-08 22:18:01,707 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fb792c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2011-07-08 22:18:01,707 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fb792c> about HardwareID('modalias', 'usb:v0C45p6416dA115dcEFdsc02dp01ic0Eisc01ip00')
2011-07-08 22:18:01,707 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fb792c> about HardwareID('modalias', 'pci:v00008086d00002939sv00001028sd000002BEbc0Csc03i00')
2011-07-08 22:18:01,707 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fb792c> about HardwareID('modalias', 'acpi:PNP0303:')
2011-07-08 22:18:01,708 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fb792c> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2011-07-08 22:18:01,708 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fb792c> about HardwareID('modalias', 'wmi:9DBB5994-A997-11DA-B012-B622A1EF5492')
2011-07-08 22:18:01,708 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fb792c> about HardwareID('modalias', 'pci:v00008086d0000293Asv00001028sd000002BEbc0Csc03i20')
2011-07-08 22:18:01,708 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fb792c> about HardwareID('modalias', 'pci:v00008086d00002934sv00001028sd000002BEbc0Csc03i00')
2011-07-08 22:18:01,708 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fb792c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-07-08 22:18:01,708 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fb792c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2011-07-08 22:18:01,708 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fb792c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2011-07-08 22:18:01,708 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fb792c> about HardwareID('modalias', 'usb:v0C45p6416dA115dcEFdsc02dp01ic0Eisc02ip00')
2011-07-08 22:18:01,708 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fb792c> about HardwareID('modalias', 'wmi:8D9DDCBC-A997-11DA-B012-B622A1EF5492')
2011-07-08 22:18:01,708 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fb792c> about HardwareID('modalias', 'platform:eisa')
2011-07-08 22:18:01,709 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fb792c> about HardwareID('modalias', 'pci:v00008086d00002929sv00001028sd000002BEbc01sc06i01')
2011-07-08 22:18:01,709 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fb792c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-07-08 22:18:01,709 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fb792c> about HardwareID('modalias', 'pci:v00008086d00002936sv00001028sd000002BEbc0Csc03i00')
2011-07-08 22:18:01,709 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fb792c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,k94,95,A1,E0,E1,E3,EC,EE,F0,ram4,lsfw')
2011-07-08 22:18:01,709 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fb792c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-07-08 22:18:01,709 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9fb792c> about HardwareID('modalias', 'acpi:PNP0200:')
2011-07-08 22:18:01,760 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-07-08 22:18:01,795 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-07-08 22:18:01,824 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-07-08 22:18:17,328 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-07-08 22:18:23,801 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-07-08 22:18:23,801 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2011-07-08 22:18:23,850 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-07-08 22:24:47,322 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-07-08 22:24:47,341 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-07-08 22:24:47,372 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-07-08 22:51:52,079 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x941aaec>
2011-07-08 22:51:53,871 DEBUG: reading modalias file /lib/modules/2.6.38-8-generic-pae/modules.alias
2011-07-08 22:51:53,983 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2011-07-08 22:51:53,983 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-07-08 22:51:54,019 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2011-07-08 22:51:54,038 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-07-08 22:51:54,043 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-07-08 22:51:54,064 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2011-07-08 22:51:54,065 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2011-07-08 22:51:54,065 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2011-07-08 22:51:54,072 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-07-08 22:51:54,073 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2011-07-08 22:51:54,073 DEBUG: fglrx.available: falling back to default
2011-07-08 22:51:54,173 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2011-07-08 22:51:54,173 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2011-07-08 22:51:54,197 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2011-07-08 22:51:54,213 DEBUG: Software modem not available
2011-07-08 22:51:54,214 DEBUG: loading custom handler /usr/share/jockey/handlers/nouveau3d.py
2011-07-08 22:51:54,247 DEBUG: Instantiated Handler subclass __builtin__.Nouveau3DHandler from name Nouveau3DHandler
2011-07-08 22:51:54,248 DEBUG: Experimental 3D support for NVIDIA cards not available
2011-07-08 22:51:54,248 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2011-07-08 22:51:54,256 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2011-07-08 22:51:54,256 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2011-07-08 22:51:54,293 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2011-07-08 22:51:54,293 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2011-07-08 22:51:54,338 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2011-07-08 22:51:54,339 DEBUG: Firmware for DVB cards not available
2011-07-08 22:51:54,339 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2011-07-08 22:51:54,347 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2011-07-08 22:51:54,348 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2011-07-08 22:51:54,348 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2011-07-08 22:51:54,349 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2011-07-08 22:51:54,359 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2011-07-08 22:51:54,360 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2011-07-08 22:51:54,361 DEBUG: nvidia.available: falling back to default
2011-07-08 22:51:54,397 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI xorg-video-abi-8 does not match X.org video ABI xorg-video-abi-10
2011-07-08 22:51:54,398 DEBUG: NVIDIA accelerated graphics driver not available
2011-07-08 22:51:54,405 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-07-08 22:51:54,406 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2011-07-08 22:51:54,406 DEBUG: nvidia.available: falling back to default
2011-07-08 22:51:54,469 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-07-08 22:51:54,470 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 947, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2011-07-08 22:51:54,474 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-07-08 22:51:54,475 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2011-07-08 22:51:54,475 DEBUG: nvidia.available: falling back to default
2011-07-08 22:51:54,527 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-07-08 22:51:54,528 DEBUG: all custom handlers loaded
2011-07-08 22:51:54,528 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x941aaec> about HardwareID('modalias', 'pci:v00008086d00002937sv00001028sd000002BEbc0Csc03i00')
2011-07-08 22:51:54,830 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x941aaec> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-07-08 22:51:54,904 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:51:54,905 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x941aaec> about HardwareID('modalias', 'pci:v00001180d00000592sv00001028sd000002BEbc08sc80i00')
2011-07-08 22:51:54,909 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x941aaec> about HardwareID('modalias', 'pci:v00001180d00000822sv00001028sd000002BEbc08sc05i01')
2011-07-08 22:51:54,910 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:51:54,910 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:51:54,910 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x941aaec> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-07-08 22:51:54,910 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x941aaec> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-07-08 22:51:54,910 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x941aaec> about HardwareID('modalias', 'pci:v00008086d00002938sv00001028sd000002BEbc0Csc03i00')
2011-07-08 22:51:54,914 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x941aaec> about HardwareID('modalias', 'platform:reg-dummy')
2011-07-08 22:51:54,914 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x941aaec> about HardwareID('modalias', 'input:b0003v0C45p6416eA115-e0,1,kD4,ramlsfw')
2011-07-08 22:51:54,915 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:51:54,915 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x941aaec> about HardwareID('modalias', 'platform:pcspkr')
2011-07-08 22:51:54,915 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:51:54,916 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:51:54,916 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x941aaec> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2011-07-08 22:51:54,942 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x941aaec> about HardwareID('modalias', 'pci:v00001180d00000852sv00001028sd000002BEbc08sc80i00')
2011-07-08 22:51:54,942 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r852', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:51:54,942 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x941aaec> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,F0,ram4,l0,1,2,sfw')
2011-07-08 22:51:54,942 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:51:54,943 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x941aaec> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2011-07-08 22:51:54,943 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x941aaec> about HardwareID('modalias', 'pci:v00008086d00002919sv00001028sd000002BEbc06sc01i00')
2011-07-08 22:51:54,946 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:51:54,946 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x941aaec> about HardwareID('modalias', 'platform:dell-laptop')
2011-07-08 22:51:54,947 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x941aaec> about HardwareID('modalias', 'pci:v00008086d00002935sv00001028sd000002BEbc0Csc03i00')
2011-07-08 22:51:54,950 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x941aaec> about HardwareID('modalias', 'platform:dcdbas')
2011-07-08 22:51:54,950 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x941aaec> about HardwareID('modalias', 'wmi:A3776CE0-1E88-11DB-A98B-0800200C9A66')
2011-07-08 22:51:54,951 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x941aaec> about HardwareID('modalias', 'pci:v00008086d00002A42sv00001028sd000002BEbc03sc00i00')
2011-07-08 22:51:54,954 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:51:54,954 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x941aaec> about HardwareID('modalias', 'wmi:A80593CE-A997-11DA-B012-B622A1EF5492')
2011-07-08 22:51:54,954 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x941aaec> about HardwareID('modalias', 'pci:v00008086d0000293Csv00001028sd000002BEbc0Csc03i20')
2011-07-08 22:51:54,957 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x941aaec> about HardwareID('modalias', 'acpi:PNP0000:')
2011-07-08 22:51:54,957 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x941aaec> about HardwareID('modalias', 'pci:v00008086d00002A43sv00001028sd000002BEbc03sc80i00')
2011-07-08 22:51:54,961 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x941aaec> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-07-08 22:51:54,961 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x941aaec> about HardwareID('modalias', 'pci:v00008086d0000293Esv00001028sd000002BEbc04sc03i00')
2011-07-08 22:51:54,964 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:51:54,964 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x941aaec> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-07-08 22:51:54,964 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x941aaec> about HardwareID('modalias', 'acpi:PNP0F13:')
2011-07-08 22:51:54,964 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x941aaec> about HardwareID('modalias', 'pci:v00008086d00002930sv00001028sd000002BEbc0Csc05i00')
2011-07-08 22:51:54,968 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:51:54,968 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x941aaec> about HardwareID('modalias', 'pci:v000014E4d00001698sv00001028sd000002BEbc02sc00i00')
2011-07-08 22:51:55,019 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'tg3', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:51:55,019 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x941aaec> about HardwareID('modalias', 'pci:v00001180d00000832sv00001028sd000002BEbc0Csc00i10')
2011-07-08 22:51:55,019 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:51:55,019 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x941aaec> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-07-08 22:51:55,019 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:51:55,020 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x941aaec> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2011-07-08 22:51:55,020 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:51:55,020 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x941aaec> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2011-07-08 22:51:55,020 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:51:55,020 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x941aaec> about HardwareID('modalias', 'pci:v000014E4d00004315sv00001028sd0000000Cbc02sc80i00')
2011-07-08 22:51:55,025 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-07-08 22:51:55,026 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-07-08 22:51:55,026 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2011-07-08 22:51:55,026 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ssb', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:51:55,026 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'b43', 'jockey_handler': 'KernelModuleHandler', 'package': 'firmware-b43-lpphy-installer'}
2011-07-08 22:51:55,027 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x941aaec> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA08:bd11/07/2009:svnDellInc.:pnStudio1555:pvrA08:rvnDellInc.:rn0D176M:rvrA08:cvnDellInc.:ct8:cvrA08:')
2011-07-08 22:51:55,043 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_laptop', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:51:55,043 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x941aaec> about HardwareID('modalias', 'wmi:ABBC0F6C-8EA1-11D1-00A0-C90629100000')
2011-07-08 22:51:55,044 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x941aaec> about HardwareID('modalias', 'acpi:PNP0100:')
2011-07-08 22:51:55,044 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x941aaec> about HardwareID('modalias', 'wmi:ABBC0F6D-8EA1-11D1-00A0-C90629100000')
2011-07-08 22:51:55,044 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x941aaec> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2011-07-08 22:51:55,044 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:51:55,044 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x941aaec> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2011-07-08 22:51:55,045 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'option', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:51:55,045 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x941aaec> about HardwareID('modalias', 'usb:v0C45p6416dA115dcEFdsc02dp01ic0Eisc01ip00')
2011-07-08 22:51:55,085 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:51:55,085 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x941aaec> about HardwareID('modalias', 'pci:v00008086d00002939sv00001028sd000002BEbc0Csc03i00')
2011-07-08 22:51:55,089 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x941aaec> about HardwareID('modalias', 'acpi:PNP0303:')
2011-07-08 22:51:55,089 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x941aaec> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2011-07-08 22:51:55,093 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x941aaec> about HardwareID('modalias', 'wmi:9DBB5994-A997-11DA-B012-B622A1EF5492')
2011-07-08 22:51:55,093 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_wmi', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:51:55,093 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x941aaec> about HardwareID('modalias', 'pci:v00008086d0000293Asv00001028sd000002BEbc0Csc03i20')
2011-07-08 22:51:55,096 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x941aaec> about HardwareID('modalias', 'pci:v00008086d00002934sv00001028sd000002BEbc0Csc03i00')
2011-07-08 22:51:55,099 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x941aaec> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-07-08 22:51:55,100 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x941aaec> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2011-07-08 22:51:55,100 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:51:55,101 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:51:55,101 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:51:55,101 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:51:55,101 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x941aaec> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2011-07-08 22:51:55,101 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x941aaec> about HardwareID('modalias', 'usb:v0C45p6416dA115dcEFdsc02dp01ic0Eisc02ip00')
2011-07-08 22:51:55,102 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x941aaec> about HardwareID('modalias', 'wmi:8D9DDCBC-A997-11DA-B012-B622A1EF5492')
2011-07-08 22:51:55,102 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x941aaec> about HardwareID('modalias', 'platform:eisa')
2011-07-08 22:51:55,103 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x941aaec> about HardwareID('modalias', 'pci:v00008086d00002929sv00001028sd000002BEbc01sc06i01')
2011-07-08 22:51:55,106 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:51:55,106 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:51:55,106 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x941aaec> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-07-08 22:51:55,116 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:51:55,116 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:51:55,116 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x941aaec> about HardwareID('modalias', 'pci:v00008086d00002936sv00001028sd000002BEbc0Csc03i00')
2011-07-08 22:51:55,120 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x941aaec> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,k94,95,A1,E0,E1,E3,EC,EE,F0,ram4,lsfw')
2011-07-08 22:51:55,120 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:51:55,120 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x941aaec> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-07-08 22:51:55,121 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:51:55,121 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x941aaec> about HardwareID('modalias', 'acpi:PNP0200:')
2011-07-08 22:51:55,121 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x942492c> about HardwareID('modalias', 'pci:v00008086d00002937sv00001028sd000002BEbc0Csc03i00')
2011-07-08 22:51:55,121 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x942492c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-07-08 22:51:55,121 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x942492c> about HardwareID('modalias', 'pci:v00001180d00000592sv00001028sd000002BEbc08sc80i00')
2011-07-08 22:51:55,121 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x942492c> about HardwareID('modalias', 'pci:v00001180d00000822sv00001028sd000002BEbc08sc05i01')
2011-07-08 22:51:55,121 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x942492c> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-07-08 22:51:55,122 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x942492c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-07-08 22:51:55,122 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x942492c> about HardwareID('modalias', 'pci:v00008086d00002938sv00001028sd000002BEbc0Csc03i00')
2011-07-08 22:51:55,122 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x942492c> about HardwareID('modalias', 'platform:reg-dummy')
2011-07-08 22:51:55,122 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x942492c> about HardwareID('modalias', 'input:b0003v0C45p6416eA115-e0,1,kD4,ramlsfw')
2011-07-08 22:51:55,122 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x942492c> about HardwareID('modalias', 'platform:pcspkr')
2011-07-08 22:51:55,122 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x942492c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2011-07-08 22:51:55,122 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x942492c> about HardwareID('modalias', 'pci:v00001180d00000852sv00001028sd000002BEbc08sc80i00')
2011-07-08 22:51:55,122 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x942492c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,F0,ram4,l0,1,2,sfw')
2011-07-08 22:51:55,122 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x942492c> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2011-07-08 22:51:55,122 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x942492c> about HardwareID('modalias', 'pci:v00008086d00002919sv00001028sd000002BEbc06sc01i00')
2011-07-08 22:51:55,123 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x942492c> about HardwareID('modalias', 'platform:dell-laptop')
2011-07-08 22:51:55,123 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x942492c> about HardwareID('modalias', 'pci:v00008086d00002935sv00001028sd000002BEbc0Csc03i00')
2011-07-08 22:51:55,123 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x942492c> about HardwareID('modalias', 'platform:dcdbas')
2011-07-08 22:51:55,123 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x942492c> about HardwareID('modalias', 'wmi:A3776CE0-1E88-11DB-A98B-0800200C9A66')
2011-07-08 22:51:55,123 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x942492c> about HardwareID('modalias', 'pci:v00008086d00002A42sv00001028sd000002BEbc03sc00i00')
2011-07-08 22:51:55,123 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x942492c> about HardwareID('modalias', 'wmi:A80593CE-A997-11DA-B012-B622A1EF5492')
2011-07-08 22:51:55,123 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x942492c> about HardwareID('modalias', 'pci:v00008086d0000293Csv00001028sd000002BEbc0Csc03i20')
2011-07-08 22:51:55,123 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x942492c> about HardwareID('modalias', 'acpi:PNP0000:')
2011-07-08 22:51:55,123 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x942492c> about HardwareID('modalias', 'pci:v00008086d00002A43sv00001028sd000002BEbc03sc80i00')
2011-07-08 22:51:55,123 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x942492c> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-07-08 22:51:55,123 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x942492c> about HardwareID('modalias', 'pci:v00008086d0000293Esv00001028sd000002BEbc04sc03i00')
2011-07-08 22:51:55,124 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x942492c> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-07-08 22:51:55,124 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x942492c> about HardwareID('modalias', 'acpi:PNP0F13:')
2011-07-08 22:51:55,124 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x942492c> about HardwareID('modalias', 'pci:v00008086d00002930sv00001028sd000002BEbc0Csc05i00')
2011-07-08 22:51:55,124 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x942492c> about HardwareID('modalias', 'pci:v000014E4d00001698sv00001028sd000002BEbc02sc00i00')
2011-07-08 22:51:55,124 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x942492c> about HardwareID('modalias', 'pci:v00001180d00000832sv00001028sd000002BEbc0Csc00i10')
2011-07-08 22:51:55,124 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x942492c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-07-08 22:51:55,124 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x942492c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2011-07-08 22:51:55,124 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x942492c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2011-07-08 22:51:55,124 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x942492c> about HardwareID('modalias', 'pci:v000014E4d00004315sv00001028sd0000000Cbc02sc80i00')
2011-07-08 22:51:55,124 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x942492c> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA08:bd11/07/2009:svnDellInc.:pnStudio1555:pvrA08:rvnDellInc.:rn0D176M:rvrA08:cvnDellInc.:ct8:cvrA08:')
2011-07-08 22:51:55,125 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x942492c> about HardwareID('modalias', 'wmi:ABBC0F6C-8EA1-11D1-00A0-C90629100000')
2011-07-08 22:51:55,125 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x942492c> about HardwareID('modalias', 'acpi:PNP0100:')
2011-07-08 22:51:55,125 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x942492c> about HardwareID('modalias', 'wmi:ABBC0F6D-8EA1-11D1-00A0-C90629100000')
2011-07-08 22:51:55,125 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x942492c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2011-07-08 22:51:55,125 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x942492c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2011-07-08 22:51:55,125 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x942492c> about HardwareID('modalias', 'usb:v0C45p6416dA115dcEFdsc02dp01ic0Eisc01ip00')
2011-07-08 22:51:55,125 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x942492c> about HardwareID('modalias', 'pci:v00008086d00002939sv00001028sd000002BEbc0Csc03i00')
2011-07-08 22:51:55,125 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x942492c> about HardwareID('modalias', 'acpi:PNP0303:')
2011-07-08 22:51:55,125 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x942492c> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2011-07-08 22:51:55,125 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x942492c> about HardwareID('modalias', 'wmi:9DBB5994-A997-11DA-B012-B622A1EF5492')
2011-07-08 22:51:55,125 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x942492c> about HardwareID('modalias', 'pci:v00008086d0000293Asv00001028sd000002BEbc0Csc03i20')
2011-07-08 22:51:55,126 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x942492c> about HardwareID('modalias', 'pci:v00008086d00002934sv00001028sd000002BEbc0Csc03i00')
2011-07-08 22:51:55,126 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x942492c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-07-08 22:51:55,126 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x942492c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2011-07-08 22:51:55,126 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x942492c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2011-07-08 22:51:55,126 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x942492c> about HardwareID('modalias', 'usb:v0C45p6416dA115dcEFdsc02dp01ic0Eisc02ip00')
2011-07-08 22:51:55,126 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x942492c> about HardwareID('modalias', 'wmi:8D9DDCBC-A997-11DA-B012-B622A1EF5492')
2011-07-08 22:51:55,126 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x942492c> about HardwareID('modalias', 'platform:eisa')
2011-07-08 22:51:55,126 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x942492c> about HardwareID('modalias', 'pci:v00008086d00002929sv00001028sd000002BEbc01sc06i01')
2011-07-08 22:51:55,126 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x942492c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-07-08 22:51:55,126 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x942492c> about HardwareID('modalias', 'pci:v00008086d00002936sv00001028sd000002BEbc0Csc03i00')
2011-07-08 22:51:55,127 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x942492c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,k94,95,A1,E0,E1,E3,EC,EE,F0,ram4,lsfw')
2011-07-08 22:51:55,127 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x942492c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-07-08 22:51:55,127 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x942492c> about HardwareID('modalias', 'acpi:PNP0200:')
2011-07-08 22:51:55,155 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-07-08 22:52:00,286 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-07-08 22:52:00,286 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2011-07-08 22:52:00,315 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-07-08 22:52:01,974 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-07-08 22:52:02,000 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-07-08 22:52:02,032 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-07-08 22:52:03,016 DEBUG: Shutting down
2011-07-08 22:58:55,729 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x863faec>
2011-07-08 22:58:59,497 DEBUG: reading modalias file /lib/modules/2.6.38-8-generic-pae/modules.alias
2011-07-08 22:58:59,650 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2011-07-08 22:58:59,658 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-07-08 22:58:59,699 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2011-07-08 22:58:59,718 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-07-08 22:58:59,755 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-07-08 22:58:59,785 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2011-07-08 22:58:59,786 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2011-07-08 22:58:59,786 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2011-07-08 22:58:59,844 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-07-08 22:58:59,845 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2011-07-08 22:58:59,845 DEBUG: fglrx.available: falling back to default
2011-07-08 22:58:59,998 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2011-07-08 22:58:59,998 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2011-07-08 22:59:00,048 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2011-07-08 22:59:00,074 DEBUG: Software modem not available
2011-07-08 22:59:00,074 DEBUG: loading custom handler /usr/share/jockey/handlers/nouveau3d.py
2011-07-08 22:59:00,156 DEBUG: Instantiated Handler subclass __builtin__.Nouveau3DHandler from name Nouveau3DHandler
2011-07-08 22:59:00,157 DEBUG: Experimental 3D support for NVIDIA cards not available
2011-07-08 22:59:00,157 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2011-07-08 22:59:00,161 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2011-07-08 22:59:00,162 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2011-07-08 22:59:00,185 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2011-07-08 22:59:00,185 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2011-07-08 22:59:00,251 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2011-07-08 22:59:00,252 DEBUG: Firmware for DVB cards not available
2011-07-08 22:59:00,252 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2011-07-08 22:59:00,257 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2011-07-08 22:59:00,258 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2011-07-08 22:59:00,258 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2011-07-08 22:59:00,258 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2011-07-08 22:59:00,278 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2011-07-08 22:59:00,278 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2011-07-08 22:59:00,279 DEBUG: nvidia.available: falling back to default
2011-07-08 22:59:00,301 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI xorg-video-abi-8 does not match X.org video ABI xorg-video-abi-10
2011-07-08 22:59:00,301 DEBUG: NVIDIA accelerated graphics driver not available
2011-07-08 22:59:00,305 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-07-08 22:59:00,306 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2011-07-08 22:59:00,306 DEBUG: nvidia.available: falling back to default
2011-07-08 22:59:00,348 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-07-08 22:59:00,348 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 947, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2011-07-08 22:59:00,367 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-07-08 22:59:00,367 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2011-07-08 22:59:00,368 DEBUG: nvidia.available: falling back to default
2011-07-08 22:59:00,414 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-07-08 22:59:00,414 DEBUG: all custom handlers loaded
2011-07-08 22:59:00,414 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x863faec> about HardwareID('modalias', 'pci:v00008086d00002937sv00001028sd000002BEbc0Csc03i00')
2011-07-08 22:59:00,716 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x863faec> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-07-08 22:59:00,876 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:59:00,876 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x863faec> about HardwareID('modalias', 'pci:v00001180d00000592sv00001028sd000002BEbc08sc80i00')
2011-07-08 22:59:00,881 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x863faec> about HardwareID('modalias', 'pci:v00001180d00000822sv00001028sd000002BEbc08sc05i01')
2011-07-08 22:59:00,881 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:59:00,881 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:59:00,881 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x863faec> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-07-08 22:59:00,881 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x863faec> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-07-08 22:59:00,882 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x863faec> about HardwareID('modalias', 'pci:v00008086d00002938sv00001028sd000002BEbc0Csc03i00')
2011-07-08 22:59:00,885 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x863faec> about HardwareID('modalias', 'platform:reg-dummy')
2011-07-08 22:59:00,886 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x863faec> about HardwareID('modalias', 'input:b0003v0C45p6416eA115-e0,1,kD4,ramlsfw')
2011-07-08 22:59:00,886 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:59:00,886 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x863faec> about HardwareID('modalias', 'platform:pcspkr')
2011-07-08 22:59:00,887 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:59:00,887 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:59:00,887 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x863faec> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2011-07-08 22:59:00,913 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x863faec> about HardwareID('modalias', 'pci:v00001180d00000852sv00001028sd000002BEbc08sc80i00')
2011-07-08 22:59:00,914 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r852', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:59:00,914 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x863faec> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,F0,ram4,l0,1,2,sfw')
2011-07-08 22:59:00,914 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:59:00,914 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x863faec> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2011-07-08 22:59:00,914 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x863faec> about HardwareID('modalias', 'pci:v00008086d00002919sv00001028sd000002BEbc06sc01i00')
2011-07-08 22:59:00,917 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:59:00,918 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x863faec> about HardwareID('modalias', 'platform:dell-laptop')
2011-07-08 22:59:00,918 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x863faec> about HardwareID('modalias', 'pci:v00008086d00002935sv00001028sd000002BEbc0Csc03i00')
2011-07-08 22:59:00,921 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x863faec> about HardwareID('modalias', 'platform:dcdbas')
2011-07-08 22:59:00,922 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x863faec> about HardwareID('modalias', 'wmi:A3776CE0-1E88-11DB-A98B-0800200C9A66')
2011-07-08 22:59:00,922 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x863faec> about HardwareID('modalias', 'pci:v00008086d00002A42sv00001028sd000002BEbc03sc00i00')
2011-07-08 22:59:00,925 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:59:00,926 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x863faec> about HardwareID('modalias', 'wmi:A80593CE-A997-11DA-B012-B622A1EF5492')
2011-07-08 22:59:00,926 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x863faec> about HardwareID('modalias', 'pci:v00008086d0000293Csv00001028sd000002BEbc0Csc03i20')
2011-07-08 22:59:00,929 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x863faec> about HardwareID('modalias', 'acpi:PNP0000:')
2011-07-08 22:59:00,929 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x863faec> about HardwareID('modalias', 'pci:v00008086d00002A43sv00001028sd000002BEbc03sc80i00')
2011-07-08 22:59:00,932 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x863faec> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-07-08 22:59:00,932 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x863faec> about HardwareID('modalias', 'pci:v00008086d0000293Esv00001028sd000002BEbc04sc03i00')
2011-07-08 22:59:00,936 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:59:00,936 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x863faec> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-07-08 22:59:00,936 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x863faec> about HardwareID('modalias', 'acpi:PNP0F13:')
2011-07-08 22:59:00,936 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x863faec> about HardwareID('modalias', 'pci:v00008086d00002930sv00001028sd000002BEbc0Csc05i00')
2011-07-08 22:59:00,939 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:59:00,939 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x863faec> about HardwareID('modalias', 'pci:v000014E4d00001698sv00001028sd000002BEbc02sc00i00')
2011-07-08 22:59:00,990 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'tg3', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:59:00,990 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x863faec> about HardwareID('modalias', 'pci:v00001180d00000832sv00001028sd000002BEbc0Csc00i10')
2011-07-08 22:59:00,990 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:59:00,990 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x863faec> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-07-08 22:59:00,990 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:59:00,990 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x863faec> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2011-07-08 22:59:00,991 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:59:00,991 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x863faec> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2011-07-08 22:59:00,991 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:59:00,991 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x863faec> about HardwareID('modalias', 'pci:v000014E4d00004315sv00001028sd0000000Cbc02sc80i00')
2011-07-08 22:59:00,996 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-07-08 22:59:00,997 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-07-08 22:59:00,996 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2011-07-08 22:59:00,997 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ssb', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:59:00,997 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'b43', 'jockey_handler': 'KernelModuleHandler', 'package': 'firmware-b43-lpphy-installer'}
2011-07-08 22:59:00,997 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x863faec> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA08:bd11/07/2009:svnDellInc.:pnStudio1555:pvrA08:rvnDellInc.:rn0D176M:rvrA08:cvnDellInc.:ct8:cvrA08:')
2011-07-08 22:59:01,015 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_laptop', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:59:01,016 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x863faec> about HardwareID('modalias', 'wmi:ABBC0F6C-8EA1-11D1-00A0-C90629100000')
2011-07-08 22:59:01,016 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x863faec> about HardwareID('modalias', 'acpi:PNP0100:')
2011-07-08 22:59:01,016 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x863faec> about HardwareID('modalias', 'wmi:ABBC0F6D-8EA1-11D1-00A0-C90629100000')
2011-07-08 22:59:01,016 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x863faec> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2011-07-08 22:59:01,016 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:59:01,016 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x863faec> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2011-07-08 22:59:01,017 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'option', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:59:01,017 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x863faec> about HardwareID('modalias', 'usb:v0C45p6416dA115dcEFdsc02dp01ic0Eisc01ip00')
2011-07-08 22:59:01,058 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:59:01,058 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x863faec> about HardwareID('modalias', 'pci:v00008086d00002939sv00001028sd000002BEbc0Csc03i00')
2011-07-08 22:59:01,063 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x863faec> about HardwareID('modalias', 'acpi:PNP0303:')
2011-07-08 22:59:01,063 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x863faec> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2011-07-08 22:59:01,066 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x863faec> about HardwareID('modalias', 'wmi:9DBB5994-A997-11DA-B012-B622A1EF5492')
2011-07-08 22:59:01,067 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_wmi', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:59:01,067 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x863faec> about HardwareID('modalias', 'pci:v00008086d0000293Asv00001028sd000002BEbc0Csc03i20')
2011-07-08 22:59:01,070 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x863faec> about HardwareID('modalias', 'pci:v00008086d00002934sv00001028sd000002BEbc0Csc03i00')
2011-07-08 22:59:01,073 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x863faec> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-07-08 22:59:01,074 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x863faec> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2011-07-08 22:59:01,074 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:59:01,074 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:59:01,074 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:59:01,074 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:59:01,075 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x863faec> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2011-07-08 22:59:01,075 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x863faec> about HardwareID('modalias', 'usb:v0C45p6416dA115dcEFdsc02dp01ic0Eisc02ip00')
2011-07-08 22:59:01,076 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x863faec> about HardwareID('modalias', 'wmi:8D9DDCBC-A997-11DA-B012-B622A1EF5492')
2011-07-08 22:59:01,076 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x863faec> about HardwareID('modalias', 'platform:eisa')
2011-07-08 22:59:01,076 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x863faec> about HardwareID('modalias', 'pci:v00008086d00002929sv00001028sd000002BEbc01sc06i01')
2011-07-08 22:59:01,080 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:59:01,080 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:59:01,080 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x863faec> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-07-08 22:59:01,090 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:59:01,090 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:59:01,090 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x863faec> about HardwareID('modalias', 'pci:v00008086d00002936sv00001028sd000002BEbc0Csc03i00')
2011-07-08 22:59:01,093 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x863faec> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,k94,95,A1,E0,E1,E3,EC,EE,F0,ram4,lsfw')
2011-07-08 22:59:01,094 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:59:01,094 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x863faec> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-07-08 22:59:01,094 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-08 22:59:01,094 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x863faec> about HardwareID('modalias', 'acpi:PNP0200:')
2011-07-08 22:59:01,094 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x864992c> about HardwareID('modalias', 'pci:v00008086d00002937sv00001028sd000002BEbc0Csc03i00')
2011-07-08 22:59:01,094 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x864992c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-07-08 22:59:01,094 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x864992c> about HardwareID('modalias', 'pci:v00001180d00000592sv00001028sd000002BEbc08sc80i00')
2011-07-08 22:59:01,095 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x864992c> about HardwareID('modalias', 'pci:v00001180d00000822sv00001028sd000002BEbc08sc05i01')
2011-07-08 22:59:01,095 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x864992c> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-07-08 22:59:01,095 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x864992c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-07-08 22:59:01,095 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x864992c> about HardwareID('modalias', 'pci:v00008086d00002938sv00001028sd000002BEbc0Csc03i00')
2011-07-08 22:59:01,095 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x864992c> about HardwareID('modalias', 'platform:reg-dummy')
2011-07-08 22:59:01,095 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x864992c> about HardwareID('modalias', 'input:b0003v0C45p6416eA115-e0,1,kD4,ramlsfw')
2011-07-08 22:59:01,095 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x864992c> about HardwareID('modalias', 'platform:pcspkr')
2011-07-08 22:59:01,095 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x864992c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2011-07-08 22:59:01,095 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x864992c> about HardwareID('modalias', 'pci:v00001180d00000852sv00001028sd000002BEbc08sc80i00')
2011-07-08 22:59:01,095 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x864992c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,F0,ram4,l0,1,2,sfw')
2011-07-08 22:59:01,095 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x864992c> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2011-07-08 22:59:01,096 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x864992c> about HardwareID('modalias', 'pci:v00008086d00002919sv00001028sd000002BEbc06sc01i00')
2011-07-08 22:59:01,096 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x864992c> about HardwareID('modalias', 'platform:dell-laptop')
2011-07-08 22:59:01,096 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x864992c> about HardwareID('modalias', 'pci:v00008086d00002935sv00001028sd000002BEbc0Csc03i00')
2011-07-08 22:59:01,096 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x864992c> about HardwareID('modalias', 'platform:dcdbas')
2011-07-08 22:59:01,096 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x864992c> about HardwareID('modalias', 'wmi:A3776CE0-1E88-11DB-A98B-0800200C9A66')
2011-07-08 22:59:01,096 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x864992c> about HardwareID('modalias', 'pci:v00008086d00002A42sv00001028sd000002BEbc03sc00i00')
2011-07-08 22:59:01,096 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x864992c> about HardwareID('modalias', 'wmi:A80593CE-A997-11DA-B012-B622A1EF5492')
2011-07-08 22:59:01,096 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x864992c> about HardwareID('modalias', 'pci:v00008086d0000293Csv00001028sd000002BEbc0Csc03i20')
2011-07-08 22:59:01,096 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x864992c> about HardwareID('modalias', 'acpi:PNP0000:')
2011-07-08 22:59:01,096 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x864992c> about HardwareID('modalias', 'pci:v00008086d00002A43sv00001028sd000002BEbc03sc80i00')
2011-07-08 22:59:01,096 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x864992c> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-07-08 22:59:01,097 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x864992c> about HardwareID('modalias', 'pci:v00008086d0000293Esv00001028sd000002BEbc04sc03i00')
2011-07-08 22:59:01,097 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x864992c> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-07-08 22:59:01,097 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x864992c> about HardwareID('modalias', 'acpi:PNP0F13:')
2011-07-08 22:59:01,097 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x864992c> about HardwareID('modalias', 'pci:v00008086d00002930sv00001028sd000002BEbc0Csc05i00')
2011-07-08 22:59:01,097 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x864992c> about HardwareID('modalias', 'pci:v000014E4d00001698sv00001028sd000002BEbc02sc00i00')
2011-07-08 22:59:01,097 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x864992c> about HardwareID('modalias', 'pci:v00001180d00000832sv00001028sd000002BEbc0Csc00i10')
2011-07-08 22:59:01,097 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x864992c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-07-08 22:59:01,097 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x864992c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2011-07-08 22:59:01,097 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x864992c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2011-07-08 22:59:01,097 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x864992c> about HardwareID('modalias', 'pci:v000014E4d00004315sv00001028sd0000000Cbc02sc80i00')
2011-07-08 22:59:01,098 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x864992c> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA08:bd11/07/2009:svnDellInc.:pnStudio1555:pvrA08:rvnDellInc.:rn0D176M:rvrA08:cvnDellInc.:ct8:cvrA08:')
2011-07-08 22:59:01,098 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x864992c> about HardwareID('modalias', 'wmi:ABBC0F6C-8EA1-11D1-00A0-C90629100000')
2011-07-08 22:59:01,098 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x864992c> about HardwareID('modalias', 'acpi:PNP0100:')
2011-07-08 22:59:01,098 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x864992c> about HardwareID('modalias', 'wmi:ABBC0F6D-8EA1-11D1-00A0-C90629100000')
2011-07-08 22:59:01,098 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x864992c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2011-07-08 22:59:01,098 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x864992c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2011-07-08 22:59:01,098 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x864992c> about HardwareID('modalias', 'usb:v0C45p6416dA115dcEFdsc02dp01ic0Eisc01ip00')
2011-07-08 22:59:01,098 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x864992c> about HardwareID('modalias', 'pci:v00008086d00002939sv00001028sd000002BEbc0Csc03i00')
2011-07-08 22:59:01,098 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x864992c> about HardwareID('modalias', 'acpi:PNP0303:')
2011-07-08 22:59:01,098 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x864992c> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2011-07-08 22:59:01,098 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x864992c> about HardwareID('modalias', 'wmi:9DBB5994-A997-11DA-B012-B622A1EF5492')
2011-07-08 22:59:01,099 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x864992c> about HardwareID('modalias', 'pci:v00008086d0000293Asv00001028sd000002BEbc0Csc03i20')
2011-07-08 22:59:01,099 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x864992c> about HardwareID('modalias', 'pci:v00008086d00002934sv00001028sd000002BEbc0Csc03i00')
2011-07-08 22:59:01,099 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x864992c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-07-08 22:59:01,099 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x864992c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2011-07-08 22:59:01,099 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x864992c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2011-07-08 22:59:01,099 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x864992c> about HardwareID('modalias', 'usb:v0C45p6416dA115dcEFdsc02dp01ic0Eisc02ip00')
2011-07-08 22:59:01,099 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x864992c> about HardwareID('modalias', 'wmi:8D9DDCBC-A997-11DA-B012-B622A1EF5492')
2011-07-08 22:59:01,099 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x864992c> about HardwareID('modalias', 'platform:eisa')
2011-07-08 22:59:01,099 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x864992c> about HardwareID('modalias', 'pci:v00008086d00002929sv00001028sd000002BEbc01sc06i01')
2011-07-08 22:59:01,099 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x864992c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-07-08 22:59:01,099 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x864992c> about HardwareID('modalias', 'pci:v00008086d00002936sv00001028sd000002BEbc0Csc03i00')
2011-07-08 22:59:01,100 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x864992c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,k94,95,A1,E0,E1,E3,EC,EE,F0,ram4,lsfw')
2011-07-08 22:59:01,100 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x864992c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-07-08 22:59:01,100 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x864992c> about HardwareID('modalias', 'acpi:PNP0200:')
2011-07-08 22:59:01,148 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-07-08 22:59:01,265 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-07-08 22:59:01,292 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-07-08 22:59:04,517 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-07-08 22:59:10,803 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-07-08 22:59:10,804 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2011-07-08 22:59:10,900 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-07-08 22:59:12,991 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-07-08 22:59:13,017 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-07-08 22:59:13,047 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-07-08 23:03:26,849 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-07-08 23:03:27,016 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-07-08 23:03:29,292 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-07-08 23:03:29,606 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-07-08 23:03:29,606 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2011-07-08 23:03:29,659 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-07-08 23:03:31,065 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-07-08 23:03:31,085 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-07-08 23:03:31,127 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-07-08 23:03:33,662 DEBUG: Shutting down
```

---

### Post by Ravenlynn12 on 2011-07-09
Invariable Bump For View.

---

### Post by Ravenlynn12 on 2011-07-09
One final bump before I post to another forum.

---

### Post by nm_geo on 2011-07-09
We will need additional information..
In terminal copy and paste the following commands.

```
lspci -nn
```

```
rfkill list all
```

```
sudo lshw -C network
```

Copy and paste the result and someone will have enough information to start helping you.

---

### Post by boosted on 2011-07-09
I installed 11.04 on a laptop with broadcom a few weeks ago and found this link to be helpful.  It actually solved the issue.

[http://askubuntu.com/questions/38327/broadcom-bcm4311-wireless-not-working]("http://askubuntu.com/questions/38327/broadcom-bcm4311-wireless-not-working")

---

### Post by chili555 on 2011-07-09
@nm_geo--

Did I see dell-laptop in the log??

---

### Post by nm_geo on 2011-07-09
> **chili555 said:**
> @nm_geo--

Did I see dell-laptop in the log??

You know doctor chili I did not even review all the log.. 
But it would not surprise me at all.. I just reviewed the link that boosted dropped and people are still using that blacklist line incorrectly.. Oh well built a simple one for this problem.

```
cat /etc/modprobe.d/* | egrep 'b43|bcm|ssb|wl'

```It is strange some people who have tried the STA (wl) driver get their boxes working woithout clearing up the blacklist and others have comment out the b43 and ssb lines. Makes me want a cool one..

---

### Post by chili555 on 2011-07-09
> Makes me want a cool one.....or three!

I haven't yet seen a definitive list of what pci.ids work with b43/ssb or wl or brcm80211 or not at all. josephmills was compiling it, but I've been to busy (read: lazy) to check it over. You two should fine tune it so I can use it and take credit for your hard work.

I do know that there are a few pci.ids that are claimed by both ssb and wl per modinfo, a recipe for more hard work and heartache.

---

### Post by nm_geo on 2011-07-09
> **chili555 said:**
> ...or three!

I haven't yet seen a definitive list of what pci.ids work with b43/ssb or wl or brcm80211 or not at all. josephmills was compiling it, but I've been to busy (read: lazy) to check it over. You two should fine tune it so I can use it and take credit for your hard work.

I do know that there are a few pci.ids that are claimed by both ssb and wl per modinfo, a recipe for more hard work and heartache.

Ok we could do that for you LOL..  Yeah and most of the ones listed for the STA (wl) will work with the Maverick version, but not with Natty and Oneiric.  Ain't that sweet...
And now b43 is not listed as an Additional Driver in Maverick, Natty and Oneiric so users try the STA (wl) that generally will not work.

Well I can confirm b43 works on my bcm4312 card.. with all those flavors.

I think I will do a bug on that one :P

---

### Post by Ravenlynn12 on 2011-07-24
RESULT:
Sorry for the long response times.

                         > <!--         @page { margin: 0.79in }         PRE { font-family: &quot;Liberation Serif&quot; }         P { margin-bottom: 0.08in }     -->       elizabeth@elizabeth-Studio-1555:~$ lspci -nn 00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07) 00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07) 00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 07) 00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03) 00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03) 00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03) 00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03) 00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03) 00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03) 00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03) 00:1c.3 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 [8086:2946] (rev 03) 00:1c.5 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 [8086:294a] (rev 03) 00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03) 00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03) 00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03) 00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03) 00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93) 00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03) 00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03) 00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03) 04:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01) 08:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe [14e4:1698] (rev 10) 09:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05) 09:01.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22) 09:01.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12) 09:01.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 12) elizabeth@elizabeth-Studio-1555:~$ rfkill list all 0: dell-wifi: Wireless LAN     Soft blocked: yes     Hard blocked: yes elizabeth@elizabeth-Studio-1555:~$ sudo lshw -C network [sudo] password for elizabeth:    *-network UNCLAIMED

---

### Post by wildmanne39 on 2011-07-24
Hi, try this in a terminal please
```
Sudo rmmod -f dell-laptop
```
it may get your connected.

If your connection does not work please post the results back here.
Thank you

---

