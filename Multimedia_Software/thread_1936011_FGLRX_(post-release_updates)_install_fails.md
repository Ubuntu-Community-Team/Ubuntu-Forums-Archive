---
title: "FGLRX (post-release updates) install fails"
date: 2012-03-05
forum: Multimedia Software
---

### Post by sombrancelha on 2012-03-05
Hi,

I have a AMD Radeon 6490M and I am trying to install the "ATI/AMD proprietary FGRLX graphics driver (post-release updates)". However, the installation fails. It says to have a look at /var/log/jockey.log, which is below.

```

2012-03-04 22:13:52,847 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xb728664c>
2012-03-04 22:13:54,135 DEBUG: reading modalias file /lib/modules/3.0.0-16-generic-pae/modules.alias
2012-03-04 22:13:54,250 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-03-04 22:13:54,256 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-03-04 22:13:54,285 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2012-03-04 22:13:54,296 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-03-04 22:13:54,310 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-03-04 22:13:54,325 DEBUG: Software modem not available
2012-03-04 22:13:54,325 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-03-04 22:13:54,371 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-03-04 22:13:54,371 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-03-04 22:13:54,371 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-03-04 22:13:54,372 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-03-04 22:13:54,417 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-03-04 22:13:54,419 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2012-03-04 22:13:54,420 DEBUG: fglrx.available: falling back to default
2012-03-04 22:13:54,579 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2012-03-04 22:13:54,583 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-03-04 22:13:54,585 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-03-04 22:13:54,585 DEBUG: fglrx.available: falling back to default
2012-03-04 22:13:54,611 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-03-04 22:13:54,611 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2012-03-04 22:13:54,613 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2012-03-04 22:13:54,614 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2012-03-04 22:13:54,625 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2012-03-04 22:13:54,625 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-03-04 22:13:54,630 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-03-04 22:13:54,632 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-03-04 22:13:54,632 DEBUG: nvidia.available: falling back to default
2012-03-04 22:13:54,656 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-03-04 22:13:54,658 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-03-04 22:13:54,660 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-03-04 22:13:54,661 DEBUG: nvidia.available: falling back to default
2012-03-04 22:13:54,687 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-03-04 22:13:54,690 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2012-03-04 22:13:54,693 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2012-03-04 22:13:54,693 DEBUG: nvidia.available: falling back to default
2012-03-04 22:13:54,719 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-03-04 22:13:54,719 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 962, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2012-03-04 22:13:54,731 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-03-04 22:13:54,733 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2012-03-04 22:13:54,733 DEBUG: nvidia.available: falling back to default
2012-03-04 22:13:54,757 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-03-04 22:13:54,760 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-03-04 22:13:54,762 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-03-04 22:13:54,762 DEBUG: nvidia.available: falling back to default
2012-03-04 22:13:54,784 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-03-04 22:13:54,786 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2012-03-04 22:13:54,788 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2012-03-04 22:13:54,789 DEBUG: nvidia.available: falling back to default
2012-03-04 22:13:54,812 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-03-04 22:13:54,812 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-03-04 22:13:54,848 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-03-04 22:13:54,848 DEBUG: Firmware for DVB cards not available
2012-03-04 22:13:54,849 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-03-04 22:13:54,852 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-03-04 22:13:54,864 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-03-04 22:13:54,865 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-03-04 22:13:54,865 DEBUG: all custom handlers loaded
2012-03-04 22:13:54,865 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb728664c> about HardwareID('modalias', 'pci:v00008086d00001C3Asv0000144Dsd0000C0B3bc07sc80i00')
2012-03-04 22:13:55,099 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mei'}
2012-03-04 22:13:55,192 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mei', 'jockey_handler': 'KernelModuleHandler'}
2012-03-04 22:13:55,192 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb728664c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2012-03-04 22:13:55,196 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-03-04 22:13:55,196 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-03-04 22:13:55,196 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb728664c> about HardwareID('modalias', 'acpi:PNP0103:')
2012-03-04 22:13:55,196 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb728664c> about HardwareID('modalias', 'acpi:PNP0000:')
2012-03-04 22:13:55,196 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb728664c> about HardwareID('modalias', 'pci:v00008086d00001C2Dsv0000144Dsd0000C0B3bc0Csc03i20')
2012-03-04 22:13:55,199 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb728664c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-03-04 22:13:55,200 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-03-04 22:13:55,200 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-03-04 22:13:55,200 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb728664c> about HardwareID('modalias', 'platform:eisa')
2012-03-04 22:13:55,200 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb728664c> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2012-03-04 22:13:55,217 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb728664c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,94,95,96,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,CA,D9,E0,E1,E2,E3,EC,EE,ram4,l0,1,2,sfw')
2012-03-04 22:13:55,217 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-03-04 22:13:55,217 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-03-04 22:13:55,217 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb728664c> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-03-04 22:13:55,217 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb728664c> about HardwareID('modalias', 'platform:pcspkr')
2012-03-04 22:13:55,218 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2012-03-04 22:13:55,218 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-03-04 22:13:55,218 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2012-03-04 22:13:55,218 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-03-04 22:13:55,218 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb728664c> about HardwareID('modalias', 'pci:v00008086d00001C26sv0000144Dsd0000C0B3bc0Csc03i20')
2012-03-04 22:13:55,221 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb728664c> about HardwareID('modalias', 'platform:regulatory')
2012-03-04 22:13:55,221 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb728664c> about HardwareID('modalias', 'pci:v00001002d00006760sv0000144Dsd0000C0B3bc03sc00i00')
2012-03-04 22:13:55,474 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2012-03-04 22:13:55,786 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-03-04 22:13:55,786 DEBUG: fglrx_updates is not the alternative in use
2012-03-04 22:13:55,474 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-03-04 22:13:55,788 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-03-04 22:13:55,791 DEBUG: fglrx.available: falling back to default
2012-03-04 22:13:55,818 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-03-04 22:13:55,819 DEBUG: fglrx_updates is not the alternative in use
2012-03-04 22:13:55,804 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-03-04 22:13:55,819 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2012-03-04 22:13:55,832 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-03-04 22:13:55,832 DEBUG: fglrx is not the alternative in use
2012-03-04 22:13:55,819 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-03-04 22:13:55,835 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-03-04 22:13:55,837 DEBUG: fglrx.available: falling back to default
2012-03-04 22:13:55,863 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-03-04 22:13:55,864 DEBUG: fglrx is not the alternative in use
2012-03-04 22:13:55,850 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-03-04 22:13:55,864 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2012-03-04 22:13:55,864 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2012-03-04 22:13:55,864 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb728664c> about HardwareID('modalias', 'acpi:ACPI0008:')
2012-03-04 22:13:55,864 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb728664c> about HardwareID('modalias', 'acpi:INT0800:')
2012-03-04 22:13:55,864 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb728664c> about HardwareID('modalias', 'pci:v00008086d00000116sv0000144Dsd0000C0B3bc03sc00i00')
2012-03-04 22:13:55,866 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i915'}
2012-03-04 22:13:55,866 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2012-03-04 22:13:55,866 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb728664c> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-03-04 22:13:55,867 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb728664c> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-03-04 22:13:55,867 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb728664c> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-03-04 22:13:55,867 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb728664c> about HardwareID('modalias', 'acpi:ETD0B00:SYN0002:PNP0F13:')
2012-03-04 22:13:55,867 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb728664c> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp01ic09isc00ip00')
2012-03-04 22:13:55,867 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb728664c> about HardwareID('modalias', 'pci:v00008086d00000091sv00008086sd00005201bc02sc80i00')
2012-03-04 22:13:55,870 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iwlagn'}
2012-03-04 22:13:55,870 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iwlagn', 'jockey_handler': 'KernelModuleHandler'}
2012-03-04 22:13:55,871 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb728664c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-03-04 22:13:55,871 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-03-04 22:13:55,871 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-03-04 22:13:55,871 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb728664c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-03-04 22:13:55,871 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-03-04 22:13:55,871 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-03-04 22:13:55,871 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb728664c> about HardwareID('modalias', 'usb:v8086p0189d6919dcE0dsc01dp01icE0isc01ip01')
2012-03-04 22:13:55,877 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2012-03-04 22:13:55,877 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2012-03-04 22:13:55,877 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb728664c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-03-04 22:13:55,877 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-03-04 22:13:55,877 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-03-04 22:13:55,877 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb728664c> about HardwareID('modalias', 'acpi:INT340E:PNP0C02:')
2012-03-04 22:13:55,878 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb728664c> about HardwareID('modalias', 'dmi:bvnPhoenixTechnologiesLtd.:bvr10FD:bd11/21/2011:svnSAMSUNGELECTRONICSCO.,LTD.:pn700Z3A/700Z4A/700Z5A/700Z5B:pvr0.1:rvnSAMSUNGELECTRONICSCO.,LTD.:rn700Z3A/700Z4A/700Z5A/700Z5B:rvrFAB1:cvnSAMSUNGELECTRONICSCO.,LTD.:ct9:cvr0.1:')
2012-03-04 22:13:55,888 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb728664c> about HardwareID('modalias', 'acpi:PNP0303:')
2012-03-04 22:13:55,888 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb728664c> about HardwareID('modalias', 'input:b0003v2232p1018e0001-e0,1,kD4,ramlsfw')
2012-03-04 22:13:55,888 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-03-04 22:13:55,888 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-03-04 22:13:55,888 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb728664c> about HardwareID('modalias', 'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2012-03-04 22:13:55,889 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb728664c> about HardwareID('modalias', 'usb:v2232p1018d0001dcEFdsc02dp01ic0Eisc01ip00')
2012-03-04 22:13:55,889 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2012-03-04 22:13:55,889 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2012-03-04 22:13:55,889 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb728664c> about HardwareID('modalias', 'acpi:PNP0100:')
2012-03-04 22:13:55,889 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb728664c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-03-04 22:13:55,889 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb728664c> about HardwareID('modalias', 'pci:v00008086d00001C22sv0000144Dsd0000C0B3bc0Csc05i00')
2012-03-04 22:13:55,891 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801'}
2012-03-04 22:13:55,891 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2012-03-04 22:13:55,892 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb728664c> about HardwareID('modalias', 'usb:v1D6Bp0003d0300dc09dsc00dp03ic09isc00ip00')
2012-03-04 22:13:55,892 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb728664c> about HardwareID('modalias', 'pci:v00008086d00001C20sv0000144Dsd0000C0B3bc04sc03i00')
2012-03-04 22:13:55,894 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-03-04 22:13:55,894 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-03-04 22:13:55,894 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-03-04 22:13:55,894 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-03-04 22:13:55,894 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb728664c> about HardwareID('modalias', 'pci:v00008086d00001C03sv0000144Dsd0000C0B3bc01sc06i01')
2012-03-04 22:13:55,897 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2012-03-04 22:13:55,897 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2012-03-04 22:13:55,898 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2012-03-04 22:13:55,898 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2012-03-04 22:13:55,898 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb728664c> about HardwareID('modalias', 'pci:v000010ECd00008168sv0000144Dsd0000C0B3bc02sc00i00')
2012-03-04 22:13:55,903 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2012-03-04 22:13:55,903 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2012-03-04 22:13:55,903 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb728664c> about HardwareID('modalias', 'platform:reg-dummy')
2012-03-04 22:13:55,904 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb728664c> about HardwareID('modalias', 'input:b0011v0002p0001e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2012-03-04 22:13:55,904 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-03-04 22:13:55,904 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-03-04 22:13:55,904 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb728664c> about HardwareID('modalias', 'acpi:PNP0200:')
2012-03-04 22:13:55,904 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb728664c> about HardwareID('modalias', 'usb:v2232p1018d0001dcEFdsc02dp01ic0Eisc02ip00')
2012-03-04 22:13:55,904 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb728664c> about HardwareID('modalias', 'pci:v00001B21d00001042sv0000144Dsd0000C0B3bc0Csc03i30')
2012-03-04 22:13:55,904 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'xhci_hcd'}
2012-03-04 22:13:55,904 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'xhci_hcd', 'jockey_handler': 'KernelModuleHandler'}
2012-03-04 22:13:55,904 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb728664c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-03-04 22:13:55,905 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb728664c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-03-04 22:13:55,911 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2012-03-04 22:13:55,911 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-03-04 22:13:55,911 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2012-03-04 22:13:55,911 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-03-04 22:13:55,911 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb728664c> about HardwareID('modalias', 'pci:v00008086d00001C49sv0000144Dsd0000C0B3bc06sc01i00')
2012-03-04 22:13:55,914 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt'}
2012-03-04 22:13:55,914 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2012-03-04 22:13:55,914 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb728664c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-03-04 22:13:55,914 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-03-04 22:13:55,914 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-03-04 22:13:55,914 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb728664c> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2012-03-04 22:13:55,914 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb697b68c> about HardwareID('modalias', 'pci:v00008086d00001C3Asv0000144Dsd0000C0B3bc07sc80i00')
2012-03-04 22:13:55,915 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb697b68c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2012-03-04 22:13:55,915 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb697b68c> about HardwareID('modalias', 'acpi:PNP0103:')
2012-03-04 22:13:55,915 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb697b68c> about HardwareID('modalias', 'acpi:PNP0000:')
2012-03-04 22:13:55,915 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb697b68c> about HardwareID('modalias', 'pci:v00008086d00001C2Dsv0000144Dsd0000C0B3bc0Csc03i20')
2012-03-04 22:13:55,915 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb697b68c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-03-04 22:13:55,915 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb697b68c> about HardwareID('modalias', 'platform:eisa')
2012-03-04 22:13:55,915 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb697b68c> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2012-03-04 22:13:55,915 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb697b68c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,94,95,96,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,CA,D9,E0,E1,E2,E3,EC,EE,ram4,l0,1,2,sfw')
2012-03-04 22:13:55,915 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb697b68c> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-03-04 22:13:55,915 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb697b68c> about HardwareID('modalias', 'platform:pcspkr')
2012-03-04 22:13:55,915 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb697b68c> about HardwareID('modalias', 'pci:v00008086d00001C26sv0000144Dsd0000C0B3bc0Csc03i20')
2012-03-04 22:13:55,915 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb697b68c> about HardwareID('modalias', 'platform:regulatory')
2012-03-04 22:13:55,915 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb697b68c> about HardwareID('modalias', 'pci:v00001002d00006760sv0000144Dsd0000C0B3bc03sc00i00')
2012-03-04 22:13:55,915 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb697b68c> about HardwareID('modalias', 'acpi:ACPI0008:')
2012-03-04 22:13:55,915 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb697b68c> about HardwareID('modalias', 'acpi:INT0800:')
2012-03-04 22:13:55,915 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb697b68c> about HardwareID('modalias', 'pci:v00008086d00000116sv0000144Dsd0000C0B3bc03sc00i00')
2012-03-04 22:13:55,915 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb697b68c> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-03-04 22:13:55,916 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb697b68c> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-03-04 22:13:55,916 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb697b68c> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-03-04 22:13:55,916 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb697b68c> about HardwareID('modalias', 'acpi:ETD0B00:SYN0002:PNP0F13:')
2012-03-04 22:13:55,916 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb697b68c> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp01ic09isc00ip00')
2012-03-04 22:13:55,916 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb697b68c> about HardwareID('modalias', 'pci:v00008086d00000091sv00008086sd00005201bc02sc80i00')
2012-03-04 22:13:55,916 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb697b68c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-03-04 22:13:55,916 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb697b68c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-03-04 22:13:55,916 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb697b68c> about HardwareID('modalias', 'usb:v8086p0189d6919dcE0dsc01dp01icE0isc01ip01')
2012-03-04 22:13:55,916 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb697b68c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-03-04 22:13:55,916 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb697b68c> about HardwareID('modalias', 'acpi:INT340E:PNP0C02:')
2012-03-04 22:13:55,916 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb697b68c> about HardwareID('modalias', 'dmi:bvnPhoenixTechnologiesLtd.:bvr10FD:bd11/21/2011:svnSAMSUNGELECTRONICSCO.,LTD.:pn700Z3A/700Z4A/700Z5A/700Z5B:pvr0.1:rvnSAMSUNGELECTRONICSCO.,LTD.:rn700Z3A/700Z4A/700Z5A/700Z5B:rvrFAB1:cvnSAMSUNGELECTRONICSCO.,LTD.:ct9:cvr0.1:')
2012-03-04 22:13:55,916 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb697b68c> about HardwareID('modalias', 'acpi:PNP0303:')
2012-03-04 22:13:55,916 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb697b68c> about HardwareID('modalias', 'input:b0003v2232p1018e0001-e0,1,kD4,ramlsfw')
2012-03-04 22:13:55,916 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb697b68c> about HardwareID('modalias', 'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2012-03-04 22:13:55,916 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb697b68c> about HardwareID('modalias', 'usb:v2232p1018d0001dcEFdsc02dp01ic0Eisc01ip00')
2012-03-04 22:13:55,916 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb697b68c> about HardwareID('modalias', 'acpi:PNP0100:')
2012-03-04 22:13:55,916 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb697b68c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-03-04 22:13:55,916 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb697b68c> about HardwareID('modalias', 'pci:v00008086d00001C22sv0000144Dsd0000C0B3bc0Csc05i00')
2012-03-04 22:13:55,916 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb697b68c> about HardwareID('modalias', 'usb:v1D6Bp0003d0300dc09dsc00dp03ic09isc00ip00')
2012-03-04 22:13:55,916 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb697b68c> about HardwareID('modalias', 'pci:v00008086d00001C20sv0000144Dsd0000C0B3bc04sc03i00')
2012-03-04 22:13:55,916 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb697b68c> about HardwareID('modalias', 'pci:v00008086d00001C03sv0000144Dsd0000C0B3bc01sc06i01')
2012-03-04 22:13:55,916 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb697b68c> about HardwareID('modalias', 'pci:v000010ECd00008168sv0000144Dsd0000C0B3bc02sc00i00')
2012-03-04 22:13:55,917 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb697b68c> about HardwareID('modalias', 'platform:reg-dummy')
2012-03-04 22:13:55,917 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb697b68c> about HardwareID('modalias', 'input:b0011v0002p0001e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2012-03-04 22:13:55,917 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb697b68c> about HardwareID('modalias', 'acpi:PNP0200:')
2012-03-04 22:13:55,917 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb697b68c> about HardwareID('modalias', 'usb:v2232p1018d0001dcEFdsc02dp01ic0Eisc02ip00')
2012-03-04 22:13:55,917 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb697b68c> about HardwareID('modalias', 'pci:v00001B21d00001042sv0000144Dsd0000C0B3bc0Csc03i30')
2012-03-04 22:13:55,917 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb697b68c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-03-04 22:13:55,917 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb697b68c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-03-04 22:13:55,917 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb697b68c> about HardwareID('modalias', 'pci:v00008086d00001C49sv0000144Dsd0000C0B3bc06sc01i00')
2012-03-04 22:13:55,917 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb697b68c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-03-04 22:13:55,917 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb697b68c> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2012-03-04 22:13:55,940 DEBUG: handler xorg:fglrx_updates previously unseen
2012-03-04 22:13:55,940 DEBUG: handler xorg:fglrx previously unseen
2012-03-04 22:13:55,941 DEBUG: writing back check cache /var/cache/jockey/check
2012-03-04 22:13:55,954 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-03-04 22:13:55,954 DEBUG: fglrx_updates is not the alternative in use
2012-03-04 22:13:55,969 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-03-04 22:13:55,969 DEBUG: fglrx is not the alternative in use
2012-03-04 22:13:55,995 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-03-04 22:13:55,995 DEBUG: fglrx_updates is not the alternative in use
2012-03-04 22:14:06,035 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-03-04 22:14:06,036 DEBUG: fglrx_updates is not the alternative in use
2012-03-04 22:14:06,158 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-03-04 22:14:06,159 DEBUG: fglrx is not the alternative in use
2012-03-04 22:14:06,252 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-03-04 22:14:06,253 DEBUG: fglrx_updates is not the alternative in use
2012-03-04 22:14:06,379 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-03-04 22:14:06,379 DEBUG: fglrx_updates is not the alternative in use
2012-03-04 22:14:06,463 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-03-04 22:14:06,463 DEBUG: fglrx is not the alternative in use
2012-03-04 22:14:48,762 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-03-04 22:14:48,762 DEBUG: fglrx_updates is not the alternative in use
2012-03-04 22:14:49,311 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-03-04 22:14:49,311 DEBUG: fglrx is not the alternative in use
2012-03-04 22:14:50,021 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-03-04 22:14:50,022 DEBUG: fglrx_updates is not the alternative in use
2012-03-04 22:14:51,421 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-03-04 22:14:51,422 DEBUG: fglrx is not the alternative in use
2012-03-04 22:14:51,887 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-03-04 22:14:51,888 DEBUG: fglrx_updates is not the alternative in use
2012-03-04 22:14:55,510 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-03-04 22:14:55,511 DEBUG: fglrx_updates is not the alternative in use
2012-03-04 22:15:00,995 DEBUG: Installing package: fglrx-updates
2012-03-04 22:15:01,226 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 0.000000
2012-03-04 22:15:01,227 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 0.000000
2012-03-04 22:15:01,230 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 0.000000
2012-03-04 22:15:01,309 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 0.000000
2012-03-04 22:15:01,392 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 0.006229
2012-03-04 22:15:01,816 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 0.221997
2012-03-04 22:15:01,817 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 0.226635
2012-03-04 22:15:01,924 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 0.407554
2012-03-04 22:15:01,925 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 0.407554
2012-03-04 22:15:01,927 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 0.407554
2012-03-04 22:15:02,023 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 0.616898
2012-03-04 22:15:02,024 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 0.621790
2012-03-04 22:15:02,525 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 1.780423
2012-03-04 22:15:03,026 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 2.763505
2012-03-04 22:15:03,528 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 3.764142
2012-03-04 22:15:04,029 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 4.771802
2012-03-04 22:15:04,530 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 5.782972
2012-03-04 22:15:05,031 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 6.618592
2012-03-04 22:15:05,533 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 7.482300
2012-03-04 22:15:06,034 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 8.412717
2012-03-04 22:15:06,535 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 9.427399
2012-03-04 22:15:07,037 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 10.452613
2012-03-04 22:15:07,538 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 11.442718
2012-03-04 22:15:08,039 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 12.608373
2012-03-04 22:15:08,540 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 13.752961
2012-03-04 22:15:09,042 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 14.876484
2012-03-04 22:15:09,543 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 15.585708
2012-03-04 22:15:10,044 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 16.558257
2012-03-04 22:15:10,545 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 17.534317
2012-03-04 22:15:11,046 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 18.538466
2012-03-04 22:15:11,548 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 19.549636
2012-03-04 22:15:12,049 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 20.673159
2012-03-04 22:15:12,550 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 21.810726
2012-03-04 22:15:13,051 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 22.972869
2012-03-04 22:15:13,552 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 24.061282
2012-03-04 22:15:14,054 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 24.974144
2012-03-04 22:15:14,555 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 25.964249
2012-03-04 22:15:15,056 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 26.954353
2012-03-04 22:15:15,558 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 27.860193
2012-03-04 22:15:16,059 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 28.583461
2012-03-04 22:15:16,560 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 29.464724
2012-03-04 22:15:17,062 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 30.419718
2012-03-04 22:15:17,563 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 31.353646
2012-03-04 22:15:18,064 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 32.006694
2012-03-04 22:15:18,566 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 32.751028
2012-03-04 22:15:19,067 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 33.523450
2012-03-04 22:15:19,569 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 34.201074
2012-03-04 22:15:20,070 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 34.664527
2012-03-04 22:15:20,571 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 35.156069
2012-03-04 22:15:21,072 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 35.745918
2012-03-04 22:15:21,574 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 36.391944
2012-03-04 22:15:22,075 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 37.013392
2012-03-04 22:15:22,577 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 37.641863
2012-03-04 22:15:23,078 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 38.273844
2012-03-04 22:15:23,579 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 38.884759
2012-03-04 22:15:24,080 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 39.576428
2012-03-04 22:15:24,582 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 40.275119
2012-03-04 22:15:25,083 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 40.966787
2012-03-04 22:15:25,584 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 41.314377
2012-03-04 22:15:26,086 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 41.812941
2012-03-04 22:15:26,587 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 42.494076
2012-03-04 22:15:27,088 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 43.231388
2012-03-04 22:15:27,590 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 43.947634
2012-03-04 22:15:28,091 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 44.611214
2012-03-04 22:15:28,592 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 45.327460
2012-03-04 22:15:29,094 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 46.033173
2012-03-04 22:15:29,595 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 46.714180
2012-03-04 22:15:30,096 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 47.416510
2012-03-04 22:15:30,598 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 48.066046
2012-03-04 22:15:31,099 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 48.750693
2012-03-04 22:15:31,600 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 49.445873
2012-03-04 22:15:32,102 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 49.961991
2012-03-04 22:15:32,603 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 50.562373
2012-03-04 22:15:33,104 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 51.117113
2012-03-04 22:15:33,605 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 51.721006
2012-03-04 22:15:34,107 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 52.275746
2012-03-04 22:15:34,608 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 52.819952
2012-03-04 22:15:35,110 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 53.343092
2012-03-04 22:15:35,611 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 53.950497
2012-03-04 22:15:36,112 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 54.578967
2012-03-04 22:15:36,614 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 55.200416
2012-03-04 22:15:37,115 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 55.758666
2012-03-04 22:15:37,617 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 56.397669
2012-03-04 22:15:38,118 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 57.012096
2012-03-04 22:15:38,619 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 57.647588
2012-03-04 22:15:39,120 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 58.254993
2012-03-04 22:15:39,622 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 58.718446
2012-03-04 22:15:40,123 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 59.350428
2012-03-04 22:15:40,624 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 59.992942
2012-03-04 22:15:41,126 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 60.649501
2012-03-04 22:15:41,627 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 61.337058
2012-03-04 22:15:42,129 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 62.001239
2012-03-04 22:15:42,630 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 62.499802
2012-03-04 22:15:43,131 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 63.026453
2012-03-04 22:15:43,633 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 63.661946
2012-03-04 22:15:44,134 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 64.318504
2012-03-04 22:15:44,635 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 65.006662
2012-03-04 22:15:45,136 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 65.687798
2012-03-04 22:15:45,638 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 66.249559
2012-03-04 22:15:46,139 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 66.723545
2012-03-04 22:15:46,640 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 67.306373
2012-03-04 22:15:47,142 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 67.945376
2012-03-04 22:15:47,643 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 68.633534
2012-03-04 22:15:48,144 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 69.016234
2012-03-04 22:15:48,645 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 69.574484
2012-03-04 22:15:49,147 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 70.016871
2012-03-04 22:15:49,648 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 70.455747
2012-03-04 22:15:50,149 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 70.936755
2012-03-04 22:15:50,651 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 71.393186
2012-03-04 22:15:51,152 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 71.884728
2012-03-04 22:15:51,653 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 72.390313
2012-03-04 22:15:52,154 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 72.913453
2012-03-04 22:15:52,656 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 73.468192
2012-03-04 22:15:53,157 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 73.942178
2012-03-04 22:15:53,658 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 74.374032
2012-03-04 22:15:54,160 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 74.890151
2012-03-04 22:15:54,661 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 75.423824
2012-03-04 22:15:55,162 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 75.996118
2012-03-04 22:15:55,664 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 76.561391
2012-03-04 22:15:56,165 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 77.147729
2012-03-04 22:15:56,666 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 77.695446
2012-03-04 22:15:57,168 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 78.225609
2012-03-04 22:15:57,669 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 78.811947
2012-03-04 22:15:58,170 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 79.394775
2012-03-04 22:15:58,672 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 80.026756
2012-03-04 22:15:59,173 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 80.750024
2012-03-04 22:15:59,674 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 81.532979
2012-03-04 22:16:00,176 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 82.438819
2012-03-04 22:16:00,677 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 83.390302
2012-03-04 22:16:01,178 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 84.545424
2012-03-04 22:16:01,337 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 84.938434
2012-03-04 22:16:01,338 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 84.941372
2012-03-04 22:16:01,839 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 86.335243
2012-03-04 22:16:02,340 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 87.837954
2012-03-04 22:16:02,842 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 89.231824
2012-03-04 22:16:03,343 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 90.801245
2012-03-04 22:16:03,844 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 92.303957
2012-03-04 22:16:04,346 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 93.813690
2012-03-04 22:16:04,847 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 95.316402
2012-03-04 22:16:05,348 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 96.829647
2012-03-04 22:16:05,850 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 98.332358
2012-03-04 22:16:06,351 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 99.842092
2012-03-04 22:16:06,404 DEBUG: download progress <Package: name:'fglrx-updates' architecture='i386' id:12098L> 100.000000
2012-03-04 22:16:07,906 DEBUG: install progress dpkg-exec 0.000000
2012-03-04 22:16:09,028 DEBUG: install progress patch 0.000000
2012-03-04 22:16:09,129 DEBUG: install progress patch 4.000000
2012-03-04 22:16:09,614 DEBUG: install progress patch 8.000000
2012-03-04 22:16:09,688 DEBUG: install progress patch 12.000000
2012-03-04 22:16:09,990 DEBUG: install progress dkms 12.000000
2012-03-04 22:16:09,990 DEBUG: install progress dkms 16.000000
2012-03-04 22:16:10,544 DEBUG: install progress dkms 20.000000
2012-03-04 22:16:10,608 DEBUG: install progress dkms 24.000000
2012-03-04 22:16:10,914 DEBUG: install progress fakeroot 24.000000
2012-03-04 22:16:11,014 DEBUG: install progress fakeroot 28.000000
2012-03-04 22:16:11,283 DEBUG: install progress fakeroot 32.000000
2012-03-04 22:16:11,347 DEBUG: install progress fakeroot 36.000000
2012-03-04 22:16:12,161 DEBUG: install progress fglrx-updates 36.000000
2012-03-04 22:16:12,162 DEBUG: install progress fglrx-updates 40.000000
2012-03-04 22:16:14,500 DEBUG: install progress fglrx-updates 44.000000
2012-03-04 22:16:14,564 DEBUG: install progress fglrx-updates 48.000000
2012-03-04 22:16:14,818 DEBUG: install progress fglrx-amdcccle-updates 48.000000
2012-03-04 22:16:14,919 DEBUG: install progress fglrx-amdcccle-updates 52.000000
2012-03-04 22:16:15,350 DEBUG: install progress fglrx-amdcccle-updates 56.000000
2012-03-04 22:16:15,413 DEBUG: install progress fglrx-amdcccle-updates 60.000000
2012-03-04 22:16:15,481 DEBUG: install progress man-db 60.000000
2012-03-04 22:16:18,020 DEBUG: install progress ureadahead 60.000000
2012-03-04 22:16:18,363 DEBUG: install progress dpkg-exec 60.000000
2012-03-04 22:16:18,395 DEBUG: install progress patch 60.000000
2012-03-04 22:16:18,500 DEBUG: install progress patch 64.000000
2012-03-04 22:16:18,589 DEBUG: install progress patch 68.000000
2012-03-04 22:16:18,678 DEBUG: install progress dkms 68.000000
2012-03-04 22:16:19,832 DEBUG: install progress dkms 72.000000
2012-03-04 22:16:19,916 DEBUG: install progress dkms 76.000000
2012-03-04 22:16:19,989 DEBUG: install progress fakeroot 76.000000
2012-03-04 22:16:20,067 DEBUG: install progress fakeroot 80.000000
2012-03-04 22:16:20,170 DEBUG: install progress fakeroot 84.000000
2012-03-04 22:16:20,246 DEBUG: install progress fglrx-updates 84.000000
2012-03-04 22:16:20,639 DEBUG: install progress fglrx-updates 88.000000
2012-03-04 22:16:46,970 DEBUG: install progress fglrx-updates 92.000000
2012-03-04 22:16:47,530 DEBUG: install progress bamfdaemon 92.000000
2012-03-04 22:16:47,698 DEBUG: install progress gnome-menus 92.000000
2012-03-04 22:16:47,921 DEBUG: install progress fglrx-amdcccle-updates 92.000000
2012-03-04 22:16:48,010 DEBUG: install progress fglrx-amdcccle-updates 96.000000
2012-03-04 22:16:48,088 DEBUG: install progress fglrx-amdcccle-updates 100.000000
2012-03-04 22:16:48,156 DEBUG: install progress initramfs-tools 100.000000
2012-03-04 22:17:02,888 DEBUG: install progress libc-bin 100.000000
2012-03-04 22:17:04,092 DEBUG: Selecting previously deselected package patch.
(Reading database ... 153195 files and directories currently installed.)
Unpacking patch (from .../patch_2.6.1-2_i386.deb) ...
Selecting previously deselected package dkms.
Unpacking dkms (from .../dkms_2.2.0.2-1ubuntu4_all.deb) ...
Selecting previously deselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.17-1_i386.deb) ...
Selecting previously deselected package fglrx-updates.
Unpacking fglrx-updates (from .../fglrx-updates_2%3a8.911-0ubuntu0.1_i386.deb) ...
Selecting previously deselected package fglrx-amdcccle-updates.
Unpacking fglrx-amdcccle-updates (from .../fglrx-amdcccle-updates_2%3a8.911-0ubuntu0.1_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up patch (2.6.1-2) ...
Setting up dkms (2.2.0.2-1ubuntu4) ...
Setting up fakeroot (1.17-1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode.
Setting up fglrx-updates (2:8.911-0ubuntu0.1) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl64.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl64.icd (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalcl.so because associated file /usr/lib32/fglrx/libaticalcl.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalrt.so because associated file /usr/lib32/fglrx/libaticalrt.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: using /usr/lib/fglrx/alt_ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
Loading new fglrx-updates-8.911 DKMS files...
First Installation: checking all kernels...
Building only for 3.0.0-16-generic-pae
Building for architecture i686
Building initial module for 3.0.0-16-generic-pae
Done.

fglrx_updates:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.0.0-16-generic-pae/updates/dkms/

depmod......

DKMS: install Completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Setting up fglrx-amdcccle-updates (2:8.911-0ubuntu0.1) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.0.0-16-generic-pae
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

2012-03-04 22:17:04,271 WARNING: /sys/module/fglrx_updates/drivers does not exist, cannot rebind fglrx_updates driver
2012-03-04 22:17:04,349 ERROR: xorg:fglrx_updates: get_alternative_by_name(fglrx-updates) returned nothing
2012-03-04 22:17:04,461 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-04 22:17:04,462 DEBUG: fglrx_updates is not the alternative in use
2012-03-04 22:17:04,517 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-04 22:17:04,517 DEBUG: fglrx_updates is not the alternative in use
2012-03-04 22:18:06,475 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-04 22:18:06,476 DEBUG: fglrx_updates is not the alternative in use
2012-03-04 22:18:06,530 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-04 22:18:06,531 DEBUG: fglrx_updates is not the alternative in use
2012-03-04 22:18:06,628 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-04 22:18:06,629 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-03-04 22:18:06,730 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-04 22:18:06,730 DEBUG: fglrx_updates is not the alternative in use
2012-03-04 22:18:06,784 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-04 22:18:06,785 DEBUG: fglrx_updates is not the alternative in use
2012-03-04 22:18:06,896 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-04 22:18:06,897 DEBUG: fglrx_updates is not the alternative in use
2012-03-04 22:18:06,949 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-04 22:18:06,950 DEBUG: fglrx_updates is not the alternative in use
2012-03-04 22:18:07,040 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-04 22:18:07,040 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-03-04 22:18:08,795 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-04 22:18:08,796 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-03-04 22:18:10,794 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-04 22:18:10,795 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-03-04 22:18:10,955 DEBUG: Installing package: fglrx
2012-03-04 22:18:11,207 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 0.000000
2012-03-04 22:18:11,207 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 0.000000
2012-03-04 22:18:11,210 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 0.000000
2012-03-04 22:18:11,290 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 0.000000
2012-03-04 22:18:11,373 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 0.008484
2012-03-04 22:18:11,874 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 0.511635
2012-03-04 22:18:12,375 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 1.987545
2012-03-04 22:18:12,877 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 3.233442
2012-03-04 22:18:13,379 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 4.445797
2012-03-04 22:18:13,880 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 5.768365
2012-03-04 22:18:14,382 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 7.062182
2012-03-04 22:18:14,883 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 8.413502
2012-03-04 22:18:15,384 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 9.779198
2012-03-04 22:18:15,885 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 11.461160
2012-03-04 22:18:16,387 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 12.467462
2012-03-04 22:18:16,888 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 13.818782
2012-03-04 22:18:17,389 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 15.261148
2012-03-04 22:18:17,891 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 16.866440
2012-03-04 22:18:18,392 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 18.557985
2012-03-04 22:18:18,893 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 20.302242
2012-03-04 22:18:19,395 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 22.056083
2012-03-04 22:18:19,896 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 23.805132
2012-03-04 22:18:20,397 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 25.554181
2012-03-04 22:18:20,899 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 27.331981
2012-03-04 22:18:21,400 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 28.692885
2012-03-04 22:18:21,901 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 30.379639
2012-03-04 22:18:22,403 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 31.754918
2012-03-04 22:18:22,904 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 33.321874
2012-03-04 22:18:23,405 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 34.999044
2012-03-04 22:18:23,907 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 36.690590
2012-03-04 22:18:24,408 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 38.430055
2012-03-04 22:18:24,910 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 40.183896
2012-03-04 22:18:25,411 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 41.966488
2012-03-04 22:18:25,912 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 43.720329
2012-03-04 22:18:26,414 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 45.474170
2012-03-04 22:18:26,915 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 47.199259
2012-03-04 22:18:27,416 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 48.981851
2012-03-04 22:18:27,918 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 50.802779
2012-03-04 22:18:28,419 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 52.666834
2012-03-04 22:18:28,920 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 54.597975
2012-03-04 22:18:29,422 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 56.624955
2012-03-04 22:18:29,923 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 58.680686
2012-03-04 22:18:30,424 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 60.736418
2012-03-04 22:18:30,925 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 62.796941
2012-03-04 22:18:31,427 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 64.852672
2012-03-04 22:18:31,928 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 66.870068
2012-03-04 22:18:32,429 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 68.925800
2012-03-04 22:18:32,930 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 70.981531
2012-03-04 22:18:33,432 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 73.037263
2012-03-04 22:18:33,933 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 75.088202
2012-03-04 22:18:34,434 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 77.143933
2012-03-04 22:18:34,935 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 79.199665
2012-03-04 22:18:35,233 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 80.423204
2012-03-04 22:18:35,234 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 80.425309
2012-03-04 22:18:35,735 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 82.483615
2012-03-04 22:18:36,237 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 84.534554
2012-03-04 22:18:36,738 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 85.435434
2012-03-04 22:18:37,239 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 85.478562
2012-03-04 22:18:37,741 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 86.671748
2012-03-04 22:18:38,242 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 88.641225
2012-03-04 22:18:38,743 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 90.409442
2012-03-04 22:18:39,245 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 91.760762
2012-03-04 22:18:39,746 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 93.452308
2012-03-04 22:18:40,247 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 95.234900
2012-03-04 22:18:40,749 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 97.103746
2012-03-04 22:18:41,250 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 98.986969
2012-03-04 22:18:41,511 DEBUG: download progress <Package: name:'fglrx' architecture='i386' id:4381L> 100.000000
2012-03-04 22:18:41,698 DEBUG: install progress dpkg-exec 0.000000
2012-03-04 22:18:41,916 DEBUG: install progress fglrx-amdcccle-updates 0.000000
2012-03-04 22:18:41,978 DEBUG: install progress fglrx-amdcccle-updates 6.250000
2012-03-04 22:18:41,978 DEBUG: install progress fglrx-amdcccle-updates 12.500000
2012-03-04 22:18:42,126 DEBUG: install progress fglrx-amdcccle-updates 18.750000
2012-03-04 22:18:42,540 DEBUG: install progress fglrx-updates 18.750000
2012-03-04 22:18:42,540 DEBUG: install progress fglrx-updates 25.000000
2012-03-04 22:18:46,564 DEBUG: install progress fglrx-updates 31.250000
2012-03-04 22:18:47,162 DEBUG: install progress fglrx-updates 37.500000
2012-03-04 22:18:47,363 DEBUG: install progress bamfdaemon 37.500000
2012-03-04 22:18:47,520 DEBUG: install progress gnome-menus 37.500000
2012-03-04 22:18:47,654 DEBUG: install progress ureadahead 37.500000
2012-03-04 22:18:47,788 DEBUG: install progress initramfs-tools 37.500000
2012-03-04 22:18:59,512 DEBUG: install progress libc-bin 37.500000
2012-03-04 22:18:59,921 DEBUG: install progress dpkg-exec 37.500000
2012-03-04 22:19:00,392 DEBUG: install progress fglrx 37.500000
2012-03-04 22:19:00,493 DEBUG: install progress fglrx 43.750000
2012-03-04 22:19:02,379 DEBUG: install progress fglrx 50.000000
2012-03-04 22:19:02,457 DEBUG: install progress fglrx 56.250000
2012-03-04 22:19:02,665 DEBUG: install progress fglrx-amdcccle 56.250000
2012-03-04 22:19:02,766 DEBUG: install progress fglrx-amdcccle 62.500000
2012-03-04 22:19:03,162 DEBUG: install progress fglrx-amdcccle 68.750000
2012-03-04 22:19:03,228 DEBUG: install progress fglrx-amdcccle 75.000000
2012-03-04 22:19:03,296 DEBUG: install progress ureadahead 75.000000
2012-03-04 22:19:03,579 DEBUG: install progress dpkg-exec 75.000000
2012-03-04 22:19:03,603 DEBUG: install progress fglrx 75.000000
2012-03-04 22:19:03,947 DEBUG: install progress fglrx 81.250000
2012-03-04 22:19:20,711 DEBUG: install progress fglrx 87.500000
2012-03-04 22:19:21,146 DEBUG: install progress bamfdaemon 87.500000
2012-03-04 22:19:21,291 DEBUG: install progress gnome-menus 87.500000
2012-03-04 22:19:21,537 DEBUG: install progress fglrx-amdcccle 87.500000
2012-03-04 22:19:21,615 DEBUG: install progress fglrx-amdcccle 93.750000
2012-03-04 22:19:21,694 DEBUG: install progress fglrx-amdcccle 100.000000
2012-03-04 22:19:21,772 DEBUG: install progress initramfs-tools 100.000000
2012-03-04 22:19:32,933 DEBUG: install progress libc-bin 100.000000
2012-03-04 22:19:33,936 DEBUG: (Reading database ... 155081 files and directories currently installed.)
Removing fglrx-amdcccle-updates ...
Removing fglrx-updates ...
Removing all DKMS Modules
Done.
update-alternatives: using /usr/lib/pxpress/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: skip creation of /usr/bin/amdcccle because associated file /usr/lib/fglrx/bin/amdcccle (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdcccle.desktop because associated file /usr/share/fglrx/amdcccle.desktop (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdccclesu.desktop because associated file /usr/share/fglrx/amdccclesu.desktop (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl64.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl64.icd (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/bin/amdupdaterandrconfig because associated file /usr/lib/fglrx/bin/amdupdaterandrconfig (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/bin/amdxdg-su because associated file /usr/lib/fglrx/bin/amdxdg-su (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalcl.so because associated file /usr/lib32/fglrx/libaticalcl.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalrt.so because associated file /usr/lib32/fglrx/libaticalrt.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: using /usr/lib/pxpress/alt_ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: using /usr/lib/i386-linux-gnu/mesa/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for ureadahead ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.0.0-16-generic-pae
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Selecting previously deselected package fglrx.
(Reading database ... 154846 files and directories currently installed.)
Unpacking fglrx (from .../fglrx_2%3a8.881-0ubuntu4.1_i386.deb) ...
Selecting previously deselected package fglrx-amdcccle.
Unpacking fglrx-amdcccle (from .../fglrx-amdcccle_2%3a8.881-0ubuntu4.1_i386.deb) ...
Processing triggers for ureadahead ...
Setting up fglrx (2:8.881-0ubuntu4.1) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: skip creation of /usr/lib32/libaticalcl.so because associated file /usr/lib32/fglrx/libaticalcl.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalrt.so because associated file /usr/lib32/fglrx/libaticalrt.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group i386-linux-gnu_gl_conf is broken.
update-alternatives: warning: skip creation of /usr/lib32/libaticalcl.so because associated file /usr/lib32/fglrx/libaticalcl.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalrt.so because associated file /usr/lib32/fglrx/libaticalrt.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: using /usr/lib/fglrx/alt_ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
Loading new fglrx-8.881 DKMS files...
First Installation: checking all kernels...
Building only for 3.0.0-16-generic-pae
Building for architecture i686
Building initial module for 3.0.0-16-generic-pae
Done.

fglrx:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.0.0-16-generic-pae/updates/dkms/

depmod....

DKMS: install Completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Setting up fglrx-amdcccle (2:8.881-0ubuntu4.1) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.0.0-16-generic-pae
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

2012-03-04 22:19:58,514 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-04 22:19:58,515 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-03-04 22:19:58,617 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-04 22:19:58,617 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-03-04 22:19:58,806 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-04 22:19:58,807 DEBUG: fglrx_updates is not the alternative in use
2012-03-04 22:19:58,863 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-04 22:19:58,863 DEBUG: fglrx_updates is not the alternative in use
2012-03-04 22:19:58,993 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-04 22:19:58,993 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-03-04 22:19:59,095 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-04 22:19:59,095 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-03-04 22:19:59,271 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-04 22:19:59,272 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-03-04 22:19:59,370 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-04 22:19:59,370 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-03-04 22:19:59,570 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-04 22:19:59,571 DEBUG: fglrx_updates is not the alternative in use
2012-03-04 22:19:59,627 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-04 22:19:59,628 DEBUG: fglrx_updates is not the alternative in use
2012-03-04 22:19:59,721 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-04 22:19:59,721 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-03-04 22:19:59,826 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-04 22:19:59,826 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-03-05 09:25:21,796 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72c464c>
2012-03-05 09:25:23,502 DEBUG: reading modalias file /lib/modules/3.0.0-16-generic-pae/modules.alias
2012-03-05 09:25:23,616 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-03-05 09:25:23,623 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-03-05 09:25:23,650 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2012-03-05 09:25:23,665 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-03-05 09:25:23,682 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-03-05 09:25:23,710 DEBUG: Software modem not available
2012-03-05 09:25:23,710 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-03-05 09:25:23,749 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-03-05 09:25:23,750 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-03-05 09:25:23,750 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-03-05 09:25:23,750 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-03-05 09:25:23,796 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-03-05 09:25:23,803 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2012-03-05 09:25:23,803 DEBUG: fglrx.available: falling back to default
2012-03-05 09:25:23,941 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2012-03-05 09:25:23,952 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-03-05 09:25:23,953 DEBUG: fglrx.available: falling back to default
2012-03-05 09:25:24,011 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-03-05 09:25:24,011 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2012-03-05 09:25:24,016 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2012-03-05 09:25:24,016 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2012-03-05 09:25:24,050 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2012-03-05 09:25:24,051 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-03-05 09:25:24,062 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-03-05 09:25:24,068 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-03-05 09:25:24,069 DEBUG: nvidia.available: falling back to default
2012-03-05 09:25:24,118 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-03-05 09:25:24,124 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-03-05 09:25:24,128 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-03-05 09:25:24,129 DEBUG: nvidia.available: falling back to default
2012-03-05 09:25:24,177 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-03-05 09:25:24,183 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2012-03-05 09:25:24,188 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2012-03-05 09:25:24,189 DEBUG: nvidia.available: falling back to default
2012-03-05 09:25:24,237 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-03-05 09:25:24,238 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 962, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2012-03-05 09:25:24,254 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-03-05 09:25:24,261 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2012-03-05 09:25:24,261 DEBUG: nvidia.available: falling back to default
2012-03-05 09:25:24,311 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-03-05 09:25:24,316 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-03-05 09:25:24,321 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-03-05 09:25:24,322 DEBUG: nvidia.available: falling back to default
2012-03-05 09:25:24,369 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-03-05 09:25:24,375 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2012-03-05 09:25:24,380 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2012-03-05 09:25:24,381 DEBUG: nvidia.available: falling back to default
2012-03-05 09:25:24,429 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-03-05 09:25:24,430 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-03-05 09:25:24,482 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-03-05 09:25:24,483 DEBUG: Firmware for DVB cards not available
2012-03-05 09:25:24,483 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-03-05 09:25:24,492 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-03-05 09:25:24,528 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-03-05 09:25:24,528 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-03-05 09:25:24,529 DEBUG: all custom handlers loaded
2012-03-05 09:25:24,529 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72c464c> about HardwareID('modalias', 'pci:v00008086d00001C3Asv0000144Dsd0000C0B3bc07sc80i00')
2012-03-05 09:25:24,789 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mei'}
2012-03-05 09:25:24,888 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mei', 'jockey_handler': 'KernelModuleHandler'}
2012-03-05 09:25:24,888 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72c464c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2012-03-05 09:25:24,892 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-03-05 09:25:24,892 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-03-05 09:25:24,892 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72c464c> about HardwareID('modalias', 'acpi:PNP0103:')
2012-03-05 09:25:24,892 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72c464c> about HardwareID('modalias', 'acpi:PNP0000:')
2012-03-05 09:25:24,893 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72c464c> about HardwareID('modalias', 'pci:v00008086d00001C2Dsv0000144Dsd0000C0B3bc0Csc03i20')
2012-03-05 09:25:24,896 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72c464c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-03-05 09:25:24,896 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-03-05 09:25:24,896 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-03-05 09:25:24,896 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72c464c> about HardwareID('modalias', 'platform:eisa')
2012-03-05 09:25:24,897 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72c464c> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2012-03-05 09:25:24,914 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72c464c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,94,95,96,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,CA,D9,E0,E1,E2,E3,EC,EE,ram4,l0,1,2,sfw')
2012-03-05 09:25:24,915 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-03-05 09:25:24,915 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-03-05 09:25:24,915 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72c464c> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-03-05 09:25:24,915 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72c464c> about HardwareID('modalias', 'platform:pcspkr')
2012-03-05 09:25:24,915 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2012-03-05 09:25:24,915 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-03-05 09:25:24,915 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2012-03-05 09:25:24,915 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-03-05 09:25:24,916 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72c464c> about HardwareID('modalias', 'pci:v00008086d00001C26sv0000144Dsd0000C0B3bc0Csc03i20')
2012-03-05 09:25:24,918 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72c464c> about HardwareID('modalias', 'platform:regulatory')
2012-03-05 09:25:24,919 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72c464c> about HardwareID('modalias', 'pci:v00001002d00006760sv0000144Dsd0000C0B3bc03sc00i00')
2012-03-05 09:25:25,196 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2012-03-05 09:25:25,658 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-05 09:25:25,658 DEBUG: fglrx_updates is not the alternative in use
2012-03-05 09:25:25,196 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-03-05 09:25:25,663 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-03-05 09:25:25,668 DEBUG: fglrx.available: falling back to default
2012-03-05 09:25:25,741 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-05 09:25:25,741 DEBUG: fglrx_updates is not the alternative in use
2012-03-05 09:25:25,689 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-03-05 09:25:25,742 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2012-03-05 09:25:25,795 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-05 09:25:25,796 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-03-05 09:25:25,742 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2012-03-05 09:25:25,917 DEBUG: fglrx.available: falling back to default
2012-03-05 09:25:25,988 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-05 09:25:25,988 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-03-05 09:25:25,942 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2012-03-05 09:25:26,062 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2012-03-05 09:25:26,063 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2012-03-05 09:25:26,063 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx'}
2012-03-05 09:25:26,112 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-05 09:25:26,112 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-03-05 09:25:26,063 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2012-03-05 09:25:26,189 DEBUG: fglrx.available: falling back to default
2012-03-05 09:25:26,264 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-05 09:25:26,265 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-03-05 09:25:26,215 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2012-03-05 09:25:26,339 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72c464c> about HardwareID('modalias', 'acpi:ACPI0008:')
2012-03-05 09:25:26,339 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72c464c> about HardwareID('modalias', 'acpi:INT0800:')
2012-03-05 09:25:26,340 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72c464c> about HardwareID('modalias', 'pci:v00008086d00000116sv0000144Dsd0000C0B3bc03sc00i00')
2012-03-05 09:25:26,349 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i915'}
2012-03-05 09:25:26,349 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2012-03-05 09:25:26,349 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72c464c> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-03-05 09:25:26,349 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72c464c> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-03-05 09:25:26,350 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72c464c> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-03-05 09:25:26,350 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72c464c> about HardwareID('modalias', 'acpi:ETD0B00:SYN0002:PNP0F13:')
2012-03-05 09:25:26,350 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72c464c> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp01ic09isc00ip00')
2012-03-05 09:25:26,351 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72c464c> about HardwareID('modalias', 'pci:v00008086d00000091sv00008086sd00005201bc02sc80i00')
2012-03-05 09:25:26,356 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iwlagn'}
2012-03-05 09:25:26,356 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iwlagn', 'jockey_handler': 'KernelModuleHandler'}
2012-03-05 09:25:26,356 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72c464c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-03-05 09:25:26,356 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-03-05 09:25:26,356 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-03-05 09:25:26,356 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72c464c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-03-05 09:25:26,356 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-03-05 09:25:26,356 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-03-05 09:25:26,356 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72c464c> about HardwareID('modalias', 'usb:v8086p0189d6919dcE0dsc01dp01icE0isc01ip01')
2012-03-05 09:25:26,363 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2012-03-05 09:25:26,363 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2012-03-05 09:25:26,363 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72c464c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-03-05 09:25:26,363 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-03-05 09:25:26,363 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-03-05 09:25:26,364 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72c464c> about HardwareID('modalias', 'acpi:INT340E:PNP0C02:')
2012-03-05 09:25:26,364 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72c464c> about HardwareID('modalias', 'dmi:bvnPhoenixTechnologiesLtd.:bvr10FD:bd11/21/2011:svnSAMSUNGELECTRONICSCO.,LTD.:pn700Z3A/700Z4A/700Z5A/700Z5B:pvr0.1:rvnSAMSUNGELECTRONICSCO.,LTD.:rn700Z3A/700Z4A/700Z5A/700Z5B:rvrFAB1:cvnSAMSUNGELECTRONICSCO.,LTD.:ct9:cvr0.1:')
2012-03-05 09:25:26,376 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72c464c> about HardwareID('modalias', 'acpi:PNP0303:')
2012-03-05 09:25:26,376 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72c464c> about HardwareID('modalias', 'input:b0003v2232p1018e0001-e0,1,kD4,ramlsfw')
2012-03-05 09:25:26,376 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-03-05 09:25:26,376 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-03-05 09:25:26,376 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72c464c> about HardwareID('modalias', 'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2012-03-05 09:25:26,376 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72c464c> about HardwareID('modalias', 'usb:v2232p1018d0001dcEFdsc02dp01ic0Eisc01ip00')
2012-03-05 09:25:26,377 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2012-03-05 09:25:26,377 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2012-03-05 09:25:26,377 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72c464c> about HardwareID('modalias', 'acpi:PNP0100:')
2012-03-05 09:25:26,377 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72c464c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-03-05 09:25:26,377 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72c464c> about HardwareID('modalias', 'pci:v00008086d00001C22sv0000144Dsd0000C0B3bc0Csc05i00')
2012-03-05 09:25:26,380 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801'}
2012-03-05 09:25:26,380 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2012-03-05 09:25:26,380 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72c464c> about HardwareID('modalias', 'usb:v1D6Bp0003d0300dc09dsc00dp03ic09isc00ip00')
2012-03-05 09:25:26,380 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72c464c> about HardwareID('modalias', 'pci:v00008086d00001C20sv0000144Dsd0000C0B3bc04sc03i00')
2012-03-05 09:25:26,383 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-03-05 09:25:26,383 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-03-05 09:25:26,383 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-03-05 09:25:26,383 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-03-05 09:25:26,383 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72c464c> about HardwareID('modalias', 'pci:v00008086d00001C03sv0000144Dsd0000C0B3bc01sc06i01')
2012-03-05 09:25:26,386 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2012-03-05 09:25:26,386 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2012-03-05 09:25:26,386 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2012-03-05 09:25:26,386 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2012-03-05 09:25:26,386 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72c464c> about HardwareID('modalias', 'pci:v000010ECd00008168sv0000144Dsd0000C0B3bc02sc00i00')
2012-03-05 09:25:26,394 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2012-03-05 09:25:26,394 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2012-03-05 09:25:26,394 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72c464c> about HardwareID('modalias', 'platform:reg-dummy')
2012-03-05 09:25:26,394 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72c464c> about HardwareID('modalias', 'input:b0011v0002p0001e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2012-03-05 09:25:26,394 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-03-05 09:25:26,394 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-03-05 09:25:26,394 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72c464c> about HardwareID('modalias', 'acpi:PNP0200:')
2012-03-05 09:25:26,395 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72c464c> about HardwareID('modalias', 'usb:v2232p1018d0001dcEFdsc02dp01ic0Eisc02ip00')
2012-03-05 09:25:26,395 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72c464c> about HardwareID('modalias', 'pci:v00001B21d00001042sv0000144Dsd0000C0B3bc0Csc03i30')
2012-03-05 09:25:26,395 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'xhci_hcd'}
2012-03-05 09:25:26,395 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'xhci_hcd', 'jockey_handler': 'KernelModuleHandler'}
2012-03-05 09:25:26,395 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72c464c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-03-05 09:25:26,396 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72c464c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-03-05 09:25:26,402 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2012-03-05 09:25:26,403 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-03-05 09:25:26,403 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2012-03-05 09:25:26,403 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-03-05 09:25:26,403 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72c464c> about HardwareID('modalias', 'pci:v00008086d00001C49sv0000144Dsd0000C0B3bc06sc01i00')
2012-03-05 09:25:26,406 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt'}
2012-03-05 09:25:26,406 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2012-03-05 09:25:26,406 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72c464c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-03-05 09:25:26,406 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-03-05 09:25:26,406 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-03-05 09:25:26,406 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb72c464c> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2012-03-05 09:25:26,406 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69c06ac> about HardwareID('modalias', 'pci:v00008086d00001C3Asv0000144Dsd0000C0B3bc07sc80i00')
2012-03-05 09:25:26,406 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69c06ac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2012-03-05 09:25:26,406 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69c06ac> about HardwareID('modalias', 'acpi:PNP0103:')
2012-03-05 09:25:26,406 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69c06ac> about HardwareID('modalias', 'acpi:PNP0000:')
2012-03-05 09:25:26,406 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69c06ac> about HardwareID('modalias', 'pci:v00008086d00001C2Dsv0000144Dsd0000C0B3bc0Csc03i20')
2012-03-05 09:25:26,406 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69c06ac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-03-05 09:25:26,407 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69c06ac> about HardwareID('modalias', 'platform:eisa')
2012-03-05 09:25:26,407 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69c06ac> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2012-03-05 09:25:26,407 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69c06ac> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,94,95,96,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,CA,D9,E0,E1,E2,E3,EC,EE,ram4,l0,1,2,sfw')
2012-03-05 09:25:26,407 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69c06ac> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-03-05 09:25:26,407 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69c06ac> about HardwareID('modalias', 'platform:pcspkr')
2012-03-05 09:25:26,407 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69c06ac> about HardwareID('modalias', 'pci:v00008086d00001C26sv0000144Dsd0000C0B3bc0Csc03i20')
2012-03-05 09:25:26,407 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69c06ac> about HardwareID('modalias', 'platform:regulatory')
2012-03-05 09:25:26,407 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69c06ac> about HardwareID('modalias', 'pci:v00001002d00006760sv0000144Dsd0000C0B3bc03sc00i00')
2012-03-05 09:25:26,407 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69c06ac> about HardwareID('modalias', 'acpi:ACPI0008:')
2012-03-05 09:25:26,407 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69c06ac> about HardwareID('modalias', 'acpi:INT0800:')
2012-03-05 09:25:26,407 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69c06ac> about HardwareID('modalias', 'pci:v00008086d00000116sv0000144Dsd0000C0B3bc03sc00i00')
2012-03-05 09:25:26,407 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69c06ac> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-03-05 09:25:26,407 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69c06ac> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-03-05 09:25:26,407 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69c06ac> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-03-05 09:25:26,407 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69c06ac> about HardwareID('modalias', 'acpi:ETD0B00:SYN0002:PNP0F13:')
2012-03-05 09:25:26,407 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69c06ac> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp01ic09isc00ip00')
2012-03-05 09:25:26,408 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69c06ac> about HardwareID('modalias', 'pci:v00008086d00000091sv00008086sd00005201bc02sc80i00')
2012-03-05 09:25:26,408 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69c06ac> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-03-05 09:25:26,408 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69c06ac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-03-05 09:25:26,408 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69c06ac> about HardwareID('modalias', 'usb:v8086p0189d6919dcE0dsc01dp01icE0isc01ip01')
2012-03-05 09:25:26,408 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69c06ac> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-03-05 09:25:26,408 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69c06ac> about HardwareID('modalias', 'acpi:INT340E:PNP0C02:')
2012-03-05 09:25:26,408 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69c06ac> about HardwareID('modalias', 'dmi:bvnPhoenixTechnologiesLtd.:bvr10FD:bd11/21/2011:svnSAMSUNGELECTRONICSCO.,LTD.:pn700Z3A/700Z4A/700Z5A/700Z5B:pvr0.1:rvnSAMSUNGELECTRONICSCO.,LTD.:rn700Z3A/700Z4A/700Z5A/700Z5B:rvrFAB1:cvnSAMSUNGELECTRONICSCO.,LTD.:ct9:cvr0.1:')
2012-03-05 09:25:26,408 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69c06ac> about HardwareID('modalias', 'acpi:PNP0303:')
2012-03-05 09:25:26,408 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69c06ac> about HardwareID('modalias', 'input:b0003v2232p1018e0001-e0,1,kD4,ramlsfw')
2012-03-05 09:25:26,408 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69c06ac> about HardwareID('modalias', 'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2012-03-05 09:25:26,408 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69c06ac> about HardwareID('modalias', 'usb:v2232p1018d0001dcEFdsc02dp01ic0Eisc01ip00')
2012-03-05 09:25:26,408 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69c06ac> about HardwareID('modalias', 'acpi:PNP0100:')
2012-03-05 09:25:26,408 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69c06ac> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-03-05 09:25:26,408 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69c06ac> about HardwareID('modalias', 'pci:v00008086d00001C22sv0000144Dsd0000C0B3bc0Csc05i00')
2012-03-05 09:25:26,408 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69c06ac> about HardwareID('modalias', 'usb:v1D6Bp0003d0300dc09dsc00dp03ic09isc00ip00')
2012-03-05 09:25:26,408 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69c06ac> about HardwareID('modalias', 'pci:v00008086d00001C20sv0000144Dsd0000C0B3bc04sc03i00')
2012-03-05 09:25:26,408 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69c06ac> about HardwareID('modalias', 'pci:v00008086d00001C03sv0000144Dsd0000C0B3bc01sc06i01')
2012-03-05 09:25:26,409 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69c06ac> about HardwareID('modalias', 'pci:v000010ECd00008168sv0000144Dsd0000C0B3bc02sc00i00')
2012-03-05 09:25:26,409 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69c06ac> about HardwareID('modalias', 'platform:reg-dummy')
2012-03-05 09:25:26,409 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69c06ac> about HardwareID('modalias', 'input:b0011v0002p0001e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2012-03-05 09:25:26,409 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69c06ac> about HardwareID('modalias', 'acpi:PNP0200:')
2012-03-05 09:25:26,409 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69c06ac> about HardwareID('modalias', 'usb:v2232p1018d0001dcEFdsc02dp01ic0Eisc02ip00')
2012-03-05 09:25:26,409 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69c06ac> about HardwareID('modalias', 'pci:v00001B21d00001042sv0000144Dsd0000C0B3bc0Csc03i30')
2012-03-05 09:25:26,409 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69c06ac> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-03-05 09:25:26,409 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69c06ac> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-03-05 09:25:26,409 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69c06ac> about HardwareID('modalias', 'pci:v00008086d00001C49sv0000144Dsd0000C0B3bc06sc01i00')
2012-03-05 09:25:26,409 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69c06ac> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-03-05 09:25:26,409 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb69c06ac> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2012-03-05 09:25:26,540 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-05 09:25:26,541 DEBUG: fglrx_updates is not the alternative in use
2012-03-05 09:25:26,676 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-05 09:25:26,676 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-03-05 09:25:26,946 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-05 09:25:26,946 DEBUG: fglrx_updates is not the alternative in use
2012-03-05 09:25:27,074 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-05 09:25:27,074 DEBUG: fglrx_updates is not the alternative in use
2012-03-05 09:25:27,164 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-05 09:25:27,164 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-03-05 09:25:33,185 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-05 09:25:33,185 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-03-05 09:25:34,661 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-05 09:25:34,662 DEBUG: fglrx_updates is not the alternative in use
2012-03-05 09:25:36,895 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-05 09:25:36,896 DEBUG: fglrx_updates is not the alternative in use
2012-03-05 09:25:42,389 DEBUG: Installing package: fglrx-updates
2012-03-05 09:25:43,824 DEBUG: install progress dpkg-exec 0.000000
2012-03-05 09:25:45,306 DEBUG: install progress fglrx-amdcccle 0.000000
2012-03-05 09:25:45,394 DEBUG: install progress fglrx-amdcccle 6.250000
2012-03-05 09:25:45,394 DEBUG: install progress fglrx-amdcccle 12.500000
2012-03-05 09:25:45,851 DEBUG: install progress fglrx-amdcccle 18.750000
2012-03-05 09:25:46,269 DEBUG: install progress fglrx 18.750000
2012-03-05 09:25:46,369 DEBUG: install progress fglrx 25.000000
2012-03-05 09:25:56,963 DEBUG: install progress fglrx 31.250000
2012-03-05 09:25:57,705 DEBUG: install progress fglrx 37.500000
2012-03-05 09:25:57,884 DEBUG: install progress bamfdaemon 37.500000
2012-03-05 09:25:58,063 DEBUG: install progress gnome-menus 37.500000
2012-03-05 09:25:58,231 DEBUG: install progress ureadahead 37.500000
2012-03-05 09:25:58,388 DEBUG: install progress initramfs-tools 37.500000
2012-03-05 09:26:12,852 DEBUG: install progress libc-bin 37.500000
2012-03-05 09:26:13,195 DEBUG: install progress dpkg-exec 37.500000
2012-03-05 09:26:13,756 DEBUG: install progress fglrx-updates 37.500000
2012-03-05 09:26:13,756 DEBUG: install progress fglrx-updates 43.750000
2012-03-05 09:26:17,199 DEBUG: install progress fglrx-updates 50.000000
2012-03-05 09:26:17,278 DEBUG: install progress fglrx-updates 56.250000
2012-03-05 09:26:17,481 DEBUG: install progress fglrx-amdcccle-updates 56.250000
2012-03-05 09:26:17,582 DEBUG: install progress fglrx-amdcccle-updates 62.500000
2012-03-05 09:26:18,130 DEBUG: install progress fglrx-amdcccle-updates 68.750000
2012-03-05 09:26:18,193 DEBUG: install progress fglrx-amdcccle-updates 75.000000
2012-03-05 09:26:18,278 DEBUG: install progress ureadahead 75.000000
2012-03-05 09:26:18,582 DEBUG: install progress dpkg-exec 75.000000
2012-03-05 09:26:18,617 DEBUG: install progress fglrx-updates 75.000000
2012-03-05 09:26:18,956 DEBUG: install progress fglrx-updates 81.250000
2012-03-05 09:26:38,755 DEBUG: install progress fglrx-updates 87.500000
2012-03-05 09:26:39,236 DEBUG: install progress bamfdaemon 87.500000
2012-03-05 09:26:39,371 DEBUG: install progress gnome-menus 87.500000
2012-03-05 09:26:39,552 DEBUG: install progress fglrx-amdcccle-updates 87.500000
2012-03-05 09:26:39,619 DEBUG: install progress fglrx-amdcccle-updates 93.750000
2012-03-05 09:26:39,686 DEBUG: install progress fglrx-amdcccle-updates 100.000000
2012-03-05 09:26:39,753 DEBUG: install progress initramfs-tools 100.000000
2012-03-05 09:26:54,428 DEBUG: install progress libc-bin 100.000000
2012-03-05 09:26:55,933 DEBUG: (Reading database ... 180646 files and directories currently installed.)
Removing fglrx-amdcccle ...
Removing fglrx ...
Removing all DKMS Modules
Done.
update-alternatives: removing manually selected alternative - switching i386-linux-gnu_gl_conf to auto mode
update-alternatives: using /usr/lib/pxpress/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: skip creation of /usr/bin/amdcccle because associated file /usr/lib/fglrx/bin/amdcccle (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdcccle.desktop because associated file /usr/share/fglrx/amdcccle.desktop (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdccclesu.desktop because associated file /usr/share/fglrx/amdccclesu.desktop (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/bin/amdupdaterandrconfig because associated file /usr/lib/fglrx/bin/amdupdaterandrconfig (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/bin/amdxdg-su because associated file /usr/lib/fglrx/bin/amdxdg-su (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalcl.so because associated file /usr/lib32/fglrx/libaticalcl.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalrt.so because associated file /usr/lib32/fglrx/libaticalrt.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: not replacing /usr/lib/i386-linux-gnu/xorg/extra-modules with a link.
update-alternatives: removing manually selected alternative - switching x86_64-linux-gnu_gl_conf to auto mode
update-alternatives: using /usr/lib/pxpress/alt_ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: using /usr/lib/i386-linux-gnu/mesa/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: not replacing /usr/lib/i386-linux-gnu/xorg/extra-modules with a link.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.0.0-16-generic-pae
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Selecting previously deselected package fglrx-updates.
(Reading database ... 180424 files and directories currently installed.)
Unpacking fglrx-updates (from .../fglrx-updates_2%3a8.911-0ubuntu0.1_i386.deb) ...
Selecting previously deselected package fglrx-amdcccle-updates.
Unpacking fglrx-amdcccle-updates (from .../fglrx-amdcccle-updates_2%3a8.911-0ubuntu0.1_i386.deb) ...
Processing triggers for ureadahead ...
Setting up fglrx-updates (2:8.911-0ubuntu0.1) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl64.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl64.icd (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalcl.so because associated file /usr/lib32/fglrx/libaticalcl.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalrt.so because associated file /usr/lib32/fglrx/libaticalrt.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group i386-linux-gnu_gl_conf is broken.
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl64.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl64.icd (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalcl.so because associated file /usr/lib32/fglrx/libaticalcl.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalrt.so because associated file /usr/lib32/fglrx/libaticalrt.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: using /usr/lib/fglrx/alt_ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
Loading new fglrx-updates-8.911 DKMS files...
Building only for 3.0.0-16-generic-pae
Building for architecture i686
Building initial module for 3.0.0-16-generic-pae
Done.

fglrx_updates:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.0.0-16-generic-pae/updates/dkms/

depmod....

DKMS: install Completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Setting up fglrx-amdcccle-updates (2:8.911-0ubuntu0.1) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.0.0-16-generic-pae
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

2012-03-05 09:26:56,261 WARNING: /sys/module/fglrx_updates/drivers does not exist, cannot rebind fglrx_updates driver
2012-03-05 09:26:56,352 ERROR: xorg:fglrx_updates: get_alternative_by_name(fglrx-updates) returned nothing
2012-03-05 09:26:56,496 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-05 09:26:56,496 DEBUG: fglrx_updates is not the alternative in use
2012-03-05 09:26:56,554 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-03-05 09:26:56,555 DEBUG: fglrx_updates is not the alternative in use

```

---

### Post by 2F4U on 2012-03-05
I got the same error messages during the installation. However, after I rebooted the machine I found that the driver was installed and worked fine.

---

### Post by sombrancelha on 2012-03-05
> **2F4U said:**
> I got the same error messages during the installation. However, after I rebooted the machine I found that the driver was installed and worked fine.

When I rebooted, the driver was not installed. I was however able to install the "regular" driver (that is, the non-"post release updates" one). I was hoping to get the post-release updates driver.

---

### Post by ratcheer on 2012-03-05
If you want the latest fglrx (Catalyst) driver, it is best to download it from AMD and install it, manually. Several threads have the instructions. My favorite is post #4 in this thread:

[http://ubuntuforums.org/showthread.php?t=1873072](http://ubuntuforums.org/showthread.php?t=1873072)

One small change is required, now. The name of the file you download is different, but everything else in that post is still correct.

Tim

---

