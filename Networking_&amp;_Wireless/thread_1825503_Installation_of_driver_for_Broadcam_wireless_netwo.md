---
title: "Installation of driver for Broadcam wireless network card"
date: 2011-08-15
forum: Networking &amp; Wireless
---

### Post by apandersen on 2011-08-15
At Additional drivere I would install Broadcom STA wireless driver, that match to my Broadcom wireless network card. But when I click on Activate I get the error message:

Sorry installation of this driver failed
Please have a look at the log file for details: /var/log/jockey.log

In this log it says:

[HTML]2011-08-15 16:01:06,211 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x896eb6c>
2011-08-15 16:01:08,232 DEBUG: reading modalias file /lib/modules/2.6.35-30-generic/modules.alias
2011-08-15 16:01:08,392 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2011-08-15 16:01:08,408 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-08-15 16:01:08,461 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2011-08-15 16:01:08,493 DEBUG: loading custom handler /usr/share/jockey/handlers/nouveau3d.py
2011-08-15 16:01:08,587 DEBUG: Instantiated Handler subclass __builtin__.Nouveau3DHandler from name Nouveau3DHandler
2011-08-15 16:01:08,587 DEBUG: Experimental 3D support for NVIDIA cards not available
2011-08-15 16:01:08,588 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2011-08-15 16:01:08,593 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2011-08-15 16:01:08,593 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2011-08-15 16:01:08,618 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2011-08-15 16:01:08,618 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2011-08-15 16:01:08,644 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-08-15 16:01:08,645 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2011-08-15 16:01:08,645 DEBUG: fglrx.available: falling back to default
2011-08-15 16:01:08,758 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2011-08-15 16:01:08,759 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2011-08-15 16:01:08,788 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2011-08-15 16:01:08,812 DEBUG: Software modem not available
2011-08-15 16:01:08,812 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2011-08-15 16:01:08,819 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2011-08-15 16:01:08,820 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2011-08-15 16:01:08,820 DEBUG: nvidia.available: falling back to default
2011-08-15 16:01:08,856 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI xorg-video-abi-8 does not match X.org video ABI xorg-video-abi-10
2011-08-15 16:01:08,856 DEBUG: NVIDIA accelerated graphics driver not available
2011-08-15 16:01:08,862 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-08-15 16:01:08,863 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2011-08-15 16:01:08,863 DEBUG: nvidia.available: falling back to default
2011-08-15 16:01:08,923 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-08-15 16:01:08,923 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 947, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2011-08-15 16:01:08,928 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-08-15 16:01:08,929 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2011-08-15 16:01:08,929 DEBUG: nvidia.available: falling back to default
2011-08-15 16:01:08,986 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-08-15 16:01:08,987 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2011-08-15 16:01:08,995 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2011-08-15 16:01:08,996 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2011-08-15 16:01:08,996 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2011-08-15 16:01:08,996 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-08-15 16:01:09,004 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-08-15 16:01:09,043 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2011-08-15 16:01:09,044 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2011-08-15 16:01:09,044 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2011-08-15 16:01:09,103 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2011-08-15 16:01:09,104 DEBUG: Firmware for DVB cards not available
2011-08-15 16:01:09,104 DEBUG: all custom handlers loaded
2011-08-15 16:01:09,104 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x896eb6c> about HardwareID('modalias', 'pci:v00008086d00002A43sv00001025sd00000212bc03sc80i00')
2011-08-15 16:01:09,415 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x896eb6c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2011-08-15 16:01:09,508 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-08-15 16:01:09,509 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x896eb6c> about HardwareID('modalias', 'pci:v00008086d00002936sv00001025sd00000212bc0Csc03i00')
2011-08-15 16:01:09,513 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x896eb6c> about HardwareID('modalias', 'pci:v00008086d00002935sv00001025sd00000212bc0Csc03i00')
2011-08-15 16:01:09,516 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x896eb6c> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-08-15 16:01:09,516 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x896eb6c> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2011-08-15 16:01:09,516 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x896eb6c> about HardwareID('modalias', 'pci:v00008086d00002937sv00001025sd00000212bc0Csc03i00')
2011-08-15 16:01:09,520 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x896eb6c> about HardwareID('modalias', 'input:b0003v064EpA103e0500-e0,1,kD4,ramlsfw')
2011-08-15 16:01:09,520 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-08-15 16:01:09,520 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x896eb6c> about HardwareID('modalias', 'platform:pcspkr')
2011-08-15 16:01:09,521 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2011-08-15 16:01:09,521 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2011-08-15 16:01:09,521 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x896eb6c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2011-08-15 16:01:09,547 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x896eb6c> about HardwareID('modalias', 'pci:v00008086d00002939sv00001025sd00000212bc0Csc03i00')
2011-08-15 16:01:09,550 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x896eb6c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2011-08-15 16:01:09,550 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-08-15 16:01:09,551 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x896eb6c> about HardwareID('modalias', 'wmi:AAE04F7B-B3C5-4865-95D6-9FAC7FF3E92B')
2011-08-15 16:01:09,551 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x896eb6c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-08-15 16:01:09,551 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x896eb6c> about HardwareID('modalias', 'pci:v00008086d00002448sv00001025sd00000212bc06sc04i01')
2011-08-15 16:01:09,554 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x896eb6c> about HardwareID('modalias', 'platform:eisa')
2011-08-15 16:01:09,555 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x896eb6c> about HardwareID('modalias', 'pci:v00008086d0000293Csv00001025sd00000212bc0Csc03i20')
2011-08-15 16:01:09,558 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x896eb6c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-08-15 16:01:09,559 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x896eb6c> about HardwareID('modalias', 'wmi:CC1A61AC-4256-41A3-B9E0-05A445ADE2F5')
2011-08-15 16:01:09,559 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x896eb6c> about HardwareID('modalias', 'pci:v00008086d00002A40sv00001025sd00000212bc06sc00i00')
2011-08-15 16:01:09,563 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_agp', 'jockey_handler': 'KernelModuleHandler'}
2011-08-15 16:01:09,563 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x896eb6c> about HardwareID('modalias', 'wmi:A7C9A0B7-4C9D-4C72-83BB-53A3459171DF')
2011-08-15 16:01:09,563 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x896eb6c> about HardwareID('modalias', 'acpi:PNP0100:')
2011-08-15 16:01:09,563 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x896eb6c> about HardwareID('modalias', 'acpi:device:')
2011-08-15 16:01:09,563 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x896eb6c> about HardwareID('modalias', 'pci:v00008086d00002A42sv00001025sd00000212bc03sc00i00')
2011-08-15 16:01:09,567 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2011-08-15 16:01:09,567 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x896eb6c> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2011-08-15 16:01:09,567 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x896eb6c> about HardwareID('modalias', 'acpi:INT0800:')
2011-08-15 16:01:09,567 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x896eb6c> about HardwareID('modalias', 'acpi:PNP0200:')
2011-08-15 16:01:09,567 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x896eb6c> about HardwareID('modalias', 'acpi:PNP0000:')
2011-08-15 16:01:09,567 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x896eb6c> about HardwareID('modalias', 'usb:v064EpA103d0500dcEFdsc02dp01ic0Eisc02ip00')
2011-08-15 16:01:09,568 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x896eb6c> about HardwareID('modalias', 'pci:v00008086d00002929sv00001025sd00000212bc01sc06i01')
2011-08-15 16:01:09,571 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-08-15 16:01:09,571 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-08-15 16:01:09,572 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x896eb6c> about HardwareID('modalias', 'acpi:SYN1B1D:SYN1B00:SYN0002:PNP0F13:')
2011-08-15 16:01:09,572 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x896eb6c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-08-15 16:01:09,582 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2011-08-15 16:01:09,582 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-08-15 16:01:09,583 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x896eb6c> about HardwareID('modalias', 'pci:v00008086d00002934sv00001025sd00000212bc0Csc03i00')
2011-08-15 16:01:09,586 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x896eb6c> about HardwareID('modalias', 'wmi:F28A9357-CF4B-4A1A-8893-BB1F58EEA1AF')
2011-08-15 16:01:09,586 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x896eb6c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-08-15 16:01:09,586 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-08-15 16:01:09,586 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x896eb6c> about HardwareID('modalias', 'wmi:F6CB5C3C-9CAE-4EBD-B577-931EA32A2CC0')
2011-08-15 16:01:09,587 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x896eb6c> about HardwareID('modalias', 'acpi:PNP0303:')
2011-08-15 16:01:09,587 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x896eb6c> about HardwareID('modalias', 'dmi:bvneMachines:bvrV1.03:bd03/11/2009:svneMachines:pneMachinesE725:pvrV1.03:rvneMachines:rneMachinesE725:rvrV1.03:cvneMachines:ct1:cvrV1.03:')
2011-08-15 16:01:09,603 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x896eb6c> about HardwareID('modalias', 'wmi:36916B91-1A64-4583-84D0-53830FB9108D')
2011-08-15 16:01:09,604 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x896eb6c> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-08-15 16:01:09,604 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x896eb6c> about HardwareID('modalias', 'wmi:CFF94C79-6C77-4AF7-AC56-7DD0CE01C997')
2011-08-15 16:01:09,604 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x896eb6c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-08-15 16:01:09,604 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-08-15 16:01:09,604 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x896eb6c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2011-08-15 16:01:09,605 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'option', 'jockey_handler': 'KernelModuleHandler'}
2011-08-15 16:01:09,605 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x896eb6c> about HardwareID('modalias', 'pci:v00008086d0000293Asv00001025sd00000212bc0Csc03i20')
2011-08-15 16:01:09,608 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x896eb6c> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-08-15 16:01:09,608 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x896eb6c> about HardwareID('modalias', 'acpi:PNP0103:')
2011-08-15 16:01:09,609 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x896eb6c> about HardwareID('modalias', 'pci:v00001969d00001062sv00001025sd00000212bc02sc00i00')
2011-08-15 16:01:09,613 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'atl1c', 'jockey_handler': 'KernelModuleHandler'}
2011-08-15 16:01:09,613 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x896eb6c> about HardwareID('modalias', 'wmi:E78C4453-0227-4861-9EDE-F5600B4A3D39')
2011-08-15 16:01:09,613 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x896eb6c> about HardwareID('modalias', 'wmi:79772EC5-04B1-4BFD-843C-61E7F77B6CC9')
2011-08-15 16:01:09,613 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x896eb6c> about HardwareID('modalias', 'pci:v00008086d00002930sv00001025sd00000212bc0Csc05i00')
2011-08-15 16:01:09,617 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2011-08-15 16:01:09,617 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x896eb6c> about HardwareID('modalias', 'pci:v000014E4d00004315sv0000105Bsd0000E003bc02sc80i00')
2011-08-15 16:01:09,676 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-08-15 16:01:09,676 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-08-15 16:01:09,676 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2011-08-15 16:01:09,677 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ssb', 'jockey_handler': 'KernelModuleHandler'}
2011-08-15 16:01:09,677 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'b43', 'jockey_handler': 'KernelModuleHandler', 'package': 'firmware-b43-lpphy-installer'}
2011-08-15 16:01:09,677 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x896eb6c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2011-08-15 16:01:09,677 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x896eb6c> about HardwareID('modalias', 'wmi:95764E09-FB56-4E83-B31A-37761F60994A')
2011-08-15 16:01:09,677 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x896eb6c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,ra0,1,18,1C,mlsfw')
2011-08-15 16:01:09,678 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-08-15 16:01:09,678 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-08-15 16:01:09,678 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-08-15 16:01:09,678 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x896eb6c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2011-08-15 16:01:09,678 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x896eb6c> about HardwareID('modalias', 'usb:v064EpA103d0500dcEFdsc02dp01ic0Eisc01ip00')
2011-08-15 16:01:09,679 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2011-08-15 16:01:09,679 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x896eb6c> about HardwareID('modalias', 'wmi:DB85B1A7-069A-4ABB-A2B5-D186A21B80F1')
2011-08-15 16:01:09,679 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x896eb6c> about HardwareID('modalias', 'pci:v00008086d00002919sv00001025sd00000212bc06sc01i00')
2011-08-15 16:01:09,683 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2011-08-15 16:01:09,683 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x896eb6c> about HardwareID('modalias', 'wmi:653A064F-A23A-485F-B3D9-13F6532A0182')
2011-08-15 16:01:09,683 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x896eb6c> about HardwareID('modalias', 'wmi:5923DD45-0480-4ED5-B61A-C9EC6C90E26A')
2011-08-15 16:01:09,683 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x896eb6c> about HardwareID('modalias', 'pci:v00008086d0000293Esv00001025sd00000212bc04sc03i00')
2011-08-15 16:01:09,688 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-08-15 16:01:09,688 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x896eb6c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2011-08-15 16:01:09,688 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-08-15 16:01:09,688 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x896eb6c> about HardwareID('modalias', 'wmi:6AF4F258-B401-42FD-BE91-3D4AC2D7C0D3')
2011-08-15 16:01:09,689 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x897b04c> about HardwareID('modalias', 'pci:v00008086d00002A43sv00001025sd00000212bc03sc80i00')
2011-08-15 16:01:09,689 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x897b04c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2011-08-15 16:01:09,689 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x897b04c> about HardwareID('modalias', 'pci:v00008086d00002936sv00001025sd00000212bc0Csc03i00')
2011-08-15 16:01:09,689 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x897b04c> about HardwareID('modalias', 'pci:v00008086d00002935sv00001025sd00000212bc0Csc03i00')
2011-08-15 16:01:09,689 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x897b04c> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-08-15 16:01:09,689 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x897b04c> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2011-08-15 16:01:09,689 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x897b04c> about HardwareID('modalias', 'pci:v00008086d00002937sv00001025sd00000212bc0Csc03i00')
2011-08-15 16:01:09,690 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x897b04c> about HardwareID('modalias', 'input:b0003v064EpA103e0500-e0,1,kD4,ramlsfw')
2011-08-15 16:01:09,690 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x897b04c> about HardwareID('modalias', 'platform:pcspkr')
2011-08-15 16:01:09,690 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x897b04c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2011-08-15 16:01:09,690 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x897b04c> about HardwareID('modalias', 'pci:v00008086d00002939sv00001025sd00000212bc0Csc03i00')
2011-08-15 16:01:09,690 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x897b04c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2011-08-15 16:01:09,690 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x897b04c> about HardwareID('modalias', 'wmi:AAE04F7B-B3C5-4865-95D6-9FAC7FF3E92B')
2011-08-15 16:01:09,690 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x897b04c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-08-15 16:01:09,690 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x897b04c> about HardwareID('modalias', 'pci:v00008086d00002448sv00001025sd00000212bc06sc04i01')
2011-08-15 16:01:09,690 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x897b04c> about HardwareID('modalias', 'platform:eisa')
2011-08-15 16:01:09,690 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x897b04c> about HardwareID('modalias', 'pci:v00008086d0000293Csv00001025sd00000212bc0Csc03i20')
2011-08-15 16:01:09,690 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x897b04c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-08-15 16:01:09,691 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x897b04c> about HardwareID('modalias', 'wmi:CC1A61AC-4256-41A3-B9E0-05A445ADE2F5')
2011-08-15 16:01:09,691 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x897b04c> about HardwareID('modalias', 'pci:v00008086d00002A40sv00001025sd00000212bc06sc00i00')
2011-08-15 16:01:09,691 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x897b04c> about HardwareID('modalias', 'wmi:A7C9A0B7-4C9D-4C72-83BB-53A3459171DF')
2011-08-15 16:01:09,691 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x897b04c> about HardwareID('modalias', 'acpi:PNP0100:')
2011-08-15 16:01:09,691 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x897b04c> about HardwareID('modalias', 'acpi:device:')
2011-08-15 16:01:09,691 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x897b04c> about HardwareID('modalias', 'pci:v00008086d00002A42sv00001025sd00000212bc03sc00i00')
2011-08-15 16:01:09,691 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x897b04c> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2011-08-15 16:01:09,691 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x897b04c> about HardwareID('modalias', 'acpi:INT0800:')
2011-08-15 16:01:09,691 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x897b04c> about HardwareID('modalias', 'acpi:PNP0200:')
2011-08-15 16:01:09,691 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x897b04c> about HardwareID('modalias', 'acpi:PNP0000:')
2011-08-15 16:01:09,691 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x897b04c> about HardwareID('modalias', 'usb:v064EpA103d0500dcEFdsc02dp01ic0Eisc02ip00')
2011-08-15 16:01:09,692 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x897b04c> about HardwareID('modalias', 'pci:v00008086d00002929sv00001025sd00000212bc01sc06i01')
2011-08-15 16:01:09,692 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x897b04c> about HardwareID('modalias', 'acpi:SYN1B1D:SYN1B00:SYN0002:PNP0F13:')
2011-08-15 16:01:09,692 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x897b04c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-08-15 16:01:09,692 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x897b04c> about HardwareID('modalias', 'pci:v00008086d00002934sv00001025sd00000212bc0Csc03i00')
2011-08-15 16:01:09,692 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x897b04c> about HardwareID('modalias', 'wmi:F28A9357-CF4B-4A1A-8893-BB1F58EEA1AF')
2011-08-15 16:01:09,692 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x897b04c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-08-15 16:01:09,692 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x897b04c> about HardwareID('modalias', 'wmi:F6CB5C3C-9CAE-4EBD-B577-931EA32A2CC0')
2011-08-15 16:01:09,692 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x897b04c> about HardwareID('modalias', 'acpi:PNP0303:')
2011-08-15 16:01:09,692 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x897b04c> about HardwareID('modalias', 'dmi:bvneMachines:bvrV1.03:bd03/11/2009:svneMachines:pneMachinesE725:pvrV1.03:rvneMachines:rneMachinesE725:rvrV1.03:cvneMachines:ct1:cvrV1.03:')
2011-08-15 16:01:09,692 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x897b04c> about HardwareID('modalias', 'wmi:36916B91-1A64-4583-84D0-53830FB9108D')
2011-08-15 16:01:09,693 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x897b04c> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-08-15 16:01:09,693 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x897b04c> about HardwareID('modalias', 'wmi:CFF94C79-6C77-4AF7-AC56-7DD0CE01C997')
2011-08-15 16:01:09,693 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x897b04c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-08-15 16:01:09,693 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x897b04c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2011-08-15 16:01:09,693 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x897b04c> about HardwareID('modalias', 'pci:v00008086d0000293Asv00001025sd00000212bc0Csc03i20')
2011-08-15 16:01:09,693 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x897b04c> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-08-15 16:01:09,693 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x897b04c> about HardwareID('modalias', 'acpi:PNP0103:')
2011-08-15 16:01:09,693 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x897b04c> about HardwareID('modalias', 'pci:v00001969d00001062sv00001025sd00000212bc02sc00i00')
2011-08-15 16:01:09,693 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x897b04c> about HardwareID('modalias', 'wmi:E78C4453-0227-4861-9EDE-F5600B4A3D39')
2011-08-15 16:01:09,693 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x897b04c> about HardwareID('modalias', 'wmi:79772EC5-04B1-4BFD-843C-61E7F77B6CC9')
2011-08-15 16:01:09,693 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x897b04c> about HardwareID('modalias', 'pci:v00008086d00002930sv00001025sd00000212bc0Csc05i00')
2011-08-15 16:01:09,694 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x897b04c> about HardwareID('modalias', 'pci:v000014E4d00004315sv0000105Bsd0000E003bc02sc80i00')
2011-08-15 16:01:09,694 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x897b04c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2011-08-15 16:01:09,694 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x897b04c> about HardwareID('modalias', 'wmi:95764E09-FB56-4E83-B31A-37761F60994A')
2011-08-15 16:01:09,694 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x897b04c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,ra0,1,18,1C,mlsfw')
2011-08-15 16:01:09,694 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x897b04c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2011-08-15 16:01:09,694 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x897b04c> about HardwareID('modalias', 'usb:v064EpA103d0500dcEFdsc02dp01ic0Eisc01ip00')
2011-08-15 16:01:09,694 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x897b04c> about HardwareID('modalias', 'wmi:DB85B1A7-069A-4ABB-A2B5-D186A21B80F1')
2011-08-15 16:01:09,694 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x897b04c> about HardwareID('modalias', 'pci:v00008086d00002919sv00001025sd00000212bc06sc01i00')
2011-08-15 16:01:09,694 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x897b04c> about HardwareID('modalias', 'wmi:653A064F-A23A-485F-B3D9-13F6532A0182')
2011-08-15 16:01:09,694 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x897b04c> about HardwareID('modalias', 'wmi:5923DD45-0480-4ED5-B61A-C9EC6C90E26A')
2011-08-15 16:01:09,694 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x897b04c> about HardwareID('modalias', 'pci:v00008086d0000293Esv00001025sd00000212bc04sc03i00')
2011-08-15 16:01:09,695 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x897b04c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2011-08-15 16:01:09,695 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x897b04c> about HardwareID('modalias', 'wmi:6AF4F258-B401-42FD-BE91-3D4AC2D7C0D3')
2011-08-15 16:01:09,746 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-08-15 16:01:09,847 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-08-15 16:01:09,880 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-08-15 16:01:26,762 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-08-15 16:01:31,137 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-08-15 16:01:31,138 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2011-08-15 16:01:31,239 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-08-15 16:01:45,874 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-08-15 16:01:45,890 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-08-15 16:01:45,921 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-08-15 16:04:21,058 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-08-15 16:04:21,490 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-08-15 16:04:21,491 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2011-08-15 16:04:21,511 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted[/HTML]

Any solution to this?

---

