---
title: "Broadcom Sta on 11.10"
date: 2011-12-07
forum: Networking &amp; Wireless
---

### Post by danipo on 2011-12-07
I just upgraded to 11.10 and now my wireless is not working.  I went into additional drivers since the problem is usually the broadcom sta driver is not activated.  It wasn't so when I click on activate it says "sorry installation of this driver failed.  Please have a look at the log file for details: /var/log/jockey.log"
So here is the output of that log file

```
2011-12-07 17:31:36,056 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a464c>
2011-12-07 17:31:37,852 DEBUG: reading modalias file /lib/modules/3.0.0-13-generic-pae/modules.alias
2011-12-07 17:31:37,986 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2011-12-07 17:31:37,986 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-12-07 17:31:38,022 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2011-12-07 17:31:38,032 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2011-12-07 17:31:38,035 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2011-12-07 17:31:38,048 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2011-12-07 17:31:38,068 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2011-12-07 17:31:38,110 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2011-12-07 17:31:38,110 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2011-12-07 17:31:38,126 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2011-12-07 17:31:38,126 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2011-12-07 17:31:38,164 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2011-12-07 17:31:38,165 DEBUG: Firmware for DVB cards not available
2011-12-07 17:31:38,165 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2011-12-07 17:31:38,216 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2011-12-07 17:31:38,219 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2011-12-07 17:31:38,219 DEBUG: nvidia.available: falling back to default
2011-12-07 17:31:38,359 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-12-07 17:31:38,362 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-12-07 17:31:38,366 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2011-12-07 17:31:38,366 DEBUG: nvidia.available: falling back to default
2011-12-07 17:31:38,399 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-12-07 17:31:38,402 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2011-12-07 17:31:38,406 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2011-12-07 17:31:38,406 DEBUG: nvidia.available: falling back to default
2011-12-07 17:31:38,440 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-12-07 17:31:38,441 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 962, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2011-12-07 17:31:38,445 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2011-12-07 17:31:38,449 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2011-12-07 17:31:38,449 DEBUG: nvidia.available: falling back to default
2011-12-07 17:31:38,482 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-12-07 17:31:38,485 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-12-07 17:31:38,489 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2011-12-07 17:31:38,489 DEBUG: nvidia.available: falling back to default
2011-12-07 17:31:38,520 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-12-07 17:31:38,523 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2011-12-07 17:31:38,527 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2011-12-07 17:31:38,527 DEBUG: nvidia.available: falling back to default
2011-12-07 17:31:38,564 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-12-07 17:31:38,564 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2011-12-07 17:31:38,571 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2011-12-07 17:31:38,575 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2011-12-07 17:31:38,575 DEBUG: fglrx.available: falling back to default
2011-12-07 17:31:38,614 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2011-12-07 17:31:38,617 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-12-07 17:31:38,621 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2011-12-07 17:31:38,621 DEBUG: fglrx.available: falling back to default
2011-12-07 17:31:38,657 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2011-12-07 17:31:38,657 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2011-12-07 17:31:38,662 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2011-12-07 17:31:38,662 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2011-12-07 17:31:38,662 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2011-12-07 17:31:38,662 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2011-12-07 17:31:38,683 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2011-12-07 17:31:38,700 DEBUG: Software modem not available
2011-12-07 17:31:38,701 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-12-07 17:31:38,705 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-12-07 17:31:38,722 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2011-12-07 17:31:38,722 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2011-12-07 17:31:38,722 DEBUG: all custom handlers loaded
2011-12-07 17:31:38,722 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a464c> about HardwareID('modalias', 'pci:v00008086d00002834sv00000000sd00000000bc0Csc03i00')
2011-12-07 17:31:39,020 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a464c> about HardwareID('modalias', 'input:b0003v05ACp0229e0111-e0,1,4,11,14,k71,72,73,75,77,78,7D,7E,7F,A3,A4,A5,CC,E0,E1,E3,E4,E5,E6,1D0,ram4,l0,1,2,3,4,sfw')
2011-12-07 17:31:39,024 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-07 17:31:39,155 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:31:39,156 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a464c> about HardwareID('modalias', 'pci:v00008086d00002828sv0000106Bsd000000A1bc01sc01i8f')
2011-12-07 17:31:39,159 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a464c> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2011-12-07 17:31:39,160 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a464c> about HardwareID('modalias', 'acpi:APP0003:SMC-SMS:')
2011-12-07 17:31:39,160 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a464c> about HardwareID('modalias', 'pci:v00008086d00002835sv0000106Bsd000000A1bc0Csc03i00')
2011-12-07 17:31:39,163 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a464c> about HardwareID('modalias', 'input:b0003v05ACp0229e0009-e0,1,3,k110,145,14A,14D,14E,ra0,1,18,mlsfw')
2011-12-07 17:31:39,163 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-07 17:31:39,163 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:31:39,163 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-12-07 17:31:39,164 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:31:39,164 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-12-07 17:31:39,164 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:31:39,164 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a464c> about HardwareID('modalias', 'platform:eisa')
2011-12-07 17:31:39,164 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a464c> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2011-12-07 17:31:39,186 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a464c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2011-12-07 17:31:39,187 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-07 17:31:39,187 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:31:39,187 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a464c> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-12-07 17:31:39,187 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a464c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-12-07 17:31:39,187 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a464c> about HardwareID('modalias', 'pci:v00008086d00002836sv0000106Bsd000000A1bc0Csc03i20')
2011-12-07 17:31:39,191 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a464c> about HardwareID('modalias', 'platform:pcspkr')
2011-12-07 17:31:39,191 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2011-12-07 17:31:39,191 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:31:39,191 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2011-12-07 17:31:39,191 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:31:39,192 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a464c> about HardwareID('modalias', 'pci:v00008086d0000283Esv0000106Bsd000000A1bc0Csc05i00')
2011-12-07 17:31:39,195 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801'}
2011-12-07 17:31:39,195 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:31:39,195 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a464c> about HardwareID('modalias', 'pci:v00008086d00002A02sv0000106Bsd000000A1bc03sc00i00')
2011-12-07 17:31:39,198 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'intelfb'}
2011-12-07 17:31:39,198 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intelfb', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:31:39,198 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i915'}
2011-12-07 17:31:39,198 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:31:39,198 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a464c> about HardwareID('modalias', 'usb:v05ACp0229d0009dc00dsc00dp00ic03isc01ip02')
2011-12-07 17:31:39,222 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'appletouch'}
2011-12-07 17:31:39,222 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'appletouch', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:31:39,222 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-12-07 17:31:39,222 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:31:39,222 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2011-12-07 17:31:39,222 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:31:39,223 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a464c> about HardwareID('modalias', 'pci:v00008086d0000284Bsv0000106Bsd000000A1bc04sc03i00')
2011-12-07 17:31:39,226 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-12-07 17:31:39,226 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:31:39,226 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a464c> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-12-07 17:31:39,226 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a464c> about HardwareID('modalias', 'pci:v00008086d00002A03sv0000106Bsd000000A1bc03sc80i00')
2011-12-07 17:31:39,229 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a464c> about HardwareID('modalias', 'acpi:APP0001:SMC-SANTAROSA:')
2011-12-07 17:31:39,229 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a464c> about HardwareID('modalias', 'pci:v000014E4d00004328sv0000106Bsd00000088bc02sc80i00')
2011-12-07 17:31:39,272 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'wl', 'package': 'bcmwl-kernel-source'}
2011-12-07 17:31:39,272 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-12-07 17:31:39,272 DEBUG: found match in handler pool kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2011-12-07 17:31:39,275 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-12-07 17:31:39,276 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-12-07 17:31:39,276 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2011-12-07 17:31:39,276 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ssb'}
2011-12-07 17:31:39,276 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ssb', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:31:39,276 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a464c> about HardwareID('modalias', 'acpi:PNP0000:')
2011-12-07 17:31:39,276 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a464c> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-12-07 17:31:39,276 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a464c> about HardwareID('modalias', 'usb:v045Ep0039d0300dc00dsc00dp00ic03isc01ip02')
2011-12-07 17:31:39,335 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-12-07 17:31:39,335 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:31:39,335 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2011-12-07 17:31:39,335 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:31:39,335 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a464c> about HardwareID('modalias', 'pci:v00008086d00002830sv0000106Bsd000000A1bc0Csc03i00')
2011-12-07 17:31:39,339 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a464c> about HardwareID('modalias', 'pci:v00008086d00002850sv0000106Bsd000000A1bc01sc01i8a')
2011-12-07 17:31:39,342 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a464c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-12-07 17:31:39,342 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-07 17:31:39,342 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:31:39,343 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a464c> about HardwareID('modalias', 'input:b0003v05ACp0229e0111-e0,1,4,kA1,ram4,lsfw')
2011-12-07 17:31:39,343 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-07 17:31:39,343 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:31:39,343 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a464c> about HardwareID('modalias', 'usb:v05ACp0229d0009dc00dsc00dp00ic03isc01ip01')
2011-12-07 17:31:39,344 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-12-07 17:31:39,344 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:31:39,344 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2011-12-07 17:31:39,344 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:31:39,344 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a464c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,3,kra0,1,mlsfw')
2011-12-07 17:31:39,344 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-07 17:31:39,344 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:31:39,344 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-12-07 17:31:39,344 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:31:39,344 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a464c> about HardwareID('modalias', 'pci:v000011ABd0000436Asv000011ABsd000000BAbc02sc00i00')
2011-12-07 17:31:39,368 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sky2'}
2011-12-07 17:31:39,368 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sky2', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:31:39,369 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a464c> about HardwareID('modalias', 'dmi:bvnAppleInc.:bvrMB31.88Z.008E.B02.0803051832:bd03/05/08:svnAppleInc.:pnMacBook3,1:pvr1.0:rvnAppleInc.:rnMac-F22788C8:rvrPVT:cvnAppleInc.:ct2:cvrMac-F22788C8:')
2011-12-07 17:31:39,383 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a464c> about HardwareID('modalias', 'usb:v05ACp8503d0188dcEFdsc02dp01ic0Eisc02ip00')
2011-12-07 17:31:39,384 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a464c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-12-07 17:31:39,384 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a464c> about HardwareID('modalias', 'usb:v05ACp8503d0188dcEFdsc02dp01ic0Eisc01ip00')
2011-12-07 17:31:39,384 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2011-12-07 17:31:39,384 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:31:39,384 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a464c> about HardwareID('modalias', 'input:b0003v045Ep0039e0110-e0,1,2,4,k110,111,112,113,114,r0,1,8,am4,lsfw')
2011-12-07 17:31:39,385 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-07 17:31:39,385 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:31:39,385 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a464c> about HardwareID('modalias', 'usb:v05ACp8205d1965dcE0dsc01dp01icE0isc01ip01')
2011-12-07 17:31:39,385 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2011-12-07 17:31:39,386 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:31:39,386 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a464c> about HardwareID('modalias', 'usb:v05ACp8205d1965dcE0dsc01dp01icFEisc01ip00')
2011-12-07 17:31:39,386 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2011-12-07 17:31:39,386 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:31:39,386 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a464c> about HardwareID('modalias', 'acpi:MEDIA-NOTIFY:')
2011-12-07 17:31:39,386 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a464c> about HardwareID('modalias', 'acpi:PNP0100:')
2011-12-07 17:31:39,387 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a464c> about HardwareID('modalias', 'pci:v00008086d00002815sv0000106Bsd000000A1bc06sc01i00')
2011-12-07 17:31:39,390 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt'}
2011-12-07 17:31:39,390 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:31:39,390 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a464c> about HardwareID('modalias', 'usb:v05ACp8242d0016dc00dsc00dp00ic03isc00ip00')
2011-12-07 17:31:39,391 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-12-07 17:31:39,391 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:31:39,391 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a464c> about HardwareID('modalias', 'pci:v00008086d0000283Asv0000106Bsd000000A1bc0Csc03i20')
2011-12-07 17:31:39,394 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a464c> about HardwareID('modalias', 'pci:v000011C1d00005811sv000011C1sd00005811bc0Csc00i10')
2011-12-07 17:31:39,395 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci'}
2011-12-07 17:31:39,395 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:31:39,395 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a464c> about HardwareID('modalias', 'pci:v00008086d00002831sv0000106Bsd000000A1bc0Csc03i00')
2011-12-07 17:31:39,398 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a464c> about HardwareID('modalias', 'platform:reg-dummy')
2011-12-07 17:31:39,399 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a464c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-12-07 17:31:39,399 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-07 17:31:39,399 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:31:39,399 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a464c> about HardwareID('modalias', 'acpi:PNP0200:')
2011-12-07 17:31:39,399 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a464c> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-12-07 17:31:39,399 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a464c> about HardwareID('modalias', 'pci:v00008086d00002832sv0000106Bsd000000A1bc0Csc03i00')
2011-12-07 17:31:39,403 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a464c> about HardwareID('modalias', 'platform:applesmc')
2011-12-07 17:31:39,403 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a464c> about HardwareID('modalias', 'usb:v05ACp0229d0009dc00dsc00dp00ic03isc00ip00')
2011-12-07 17:31:39,404 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-12-07 17:31:39,404 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:31:39,404 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a464c> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2011-12-07 17:31:39,407 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a464c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2011-12-07 17:31:39,407 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-07 17:31:39,407 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:31:39,407 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a464c> about HardwareID('modalias', 'input:b0003v05ACp8503e0188-e0,1,kD4,ramlsfw')
2011-12-07 17:31:39,407 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-07 17:31:39,408 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:31:39,408 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73a464c> about HardwareID('modalias', 'acpi:INT0800:')
2011-12-07 17:31:39,408 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9baec> about HardwareID('modalias', 'pci:v00008086d00002834sv00000000sd00000000bc0Csc03i00')
2011-12-07 17:31:39,408 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9baec> about HardwareID('modalias', 'input:b0003v05ACp0229e0111-e0,1,4,11,14,k71,72,73,75,77,78,7D,7E,7F,A3,A4,A5,CC,E0,E1,E3,E4,E5,E6,1D0,ram4,l0,1,2,3,4,sfw')
2011-12-07 17:31:39,408 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9baec> about HardwareID('modalias', 'pci:v00008086d00002828sv0000106Bsd000000A1bc01sc01i8f')
2011-12-07 17:31:39,408 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9baec> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2011-12-07 17:31:39,408 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9baec> about HardwareID('modalias', 'acpi:APP0003:SMC-SMS:')
2011-12-07 17:31:39,408 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9baec> about HardwareID('modalias', 'pci:v00008086d00002835sv0000106Bsd000000A1bc0Csc03i00')
2011-12-07 17:31:39,408 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9baec> about HardwareID('modalias', 'input:b0003v05ACp0229e0009-e0,1,3,k110,145,14A,14D,14E,ra0,1,18,mlsfw')
2011-12-07 17:31:39,408 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9baec> about HardwareID('modalias', 'platform:eisa')
2011-12-07 17:31:39,408 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9baec> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2011-12-07 17:31:39,408 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9baec> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2011-12-07 17:31:39,409 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9baec> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-12-07 17:31:39,409 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9baec> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-12-07 17:31:39,409 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9baec> about HardwareID('modalias', 'pci:v00008086d00002836sv0000106Bsd000000A1bc0Csc03i20')
2011-12-07 17:31:39,409 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9baec> about HardwareID('modalias', 'platform:pcspkr')
2011-12-07 17:31:39,409 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9baec> about HardwareID('modalias', 'pci:v00008086d0000283Esv0000106Bsd000000A1bc0Csc05i00')
2011-12-07 17:31:39,409 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9baec> about HardwareID('modalias', 'pci:v00008086d00002A02sv0000106Bsd000000A1bc03sc00i00')
2011-12-07 17:31:39,409 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9baec> about HardwareID('modalias', 'usb:v05ACp0229d0009dc00dsc00dp00ic03isc01ip02')
2011-12-07 17:31:39,409 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9baec> about HardwareID('modalias', 'pci:v00008086d0000284Bsv0000106Bsd000000A1bc04sc03i00')
2011-12-07 17:31:39,409 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9baec> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-12-07 17:31:39,409 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9baec> about HardwareID('modalias', 'pci:v00008086d00002A03sv0000106Bsd000000A1bc03sc80i00')
2011-12-07 17:31:39,409 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9baec> about HardwareID('modalias', 'acpi:APP0001:SMC-SANTAROSA:')
2011-12-07 17:31:39,409 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9baec> about HardwareID('modalias', 'pci:v000014E4d00004328sv0000106Bsd00000088bc02sc80i00')
2011-12-07 17:31:39,409 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9baec> about HardwareID('modalias', 'acpi:PNP0000:')
2011-12-07 17:31:39,410 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9baec> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-12-07 17:31:39,410 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9baec> about HardwareID('modalias', 'usb:v045Ep0039d0300dc00dsc00dp00ic03isc01ip02')
2011-12-07 17:31:39,410 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9baec> about HardwareID('modalias', 'pci:v00008086d00002830sv0000106Bsd000000A1bc0Csc03i00')
2011-12-07 17:31:39,410 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9baec> about HardwareID('modalias', 'pci:v00008086d00002850sv0000106Bsd000000A1bc01sc01i8a')
2011-12-07 17:31:39,410 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9baec> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-12-07 17:31:39,410 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9baec> about HardwareID('modalias', 'input:b0003v05ACp0229e0111-e0,1,4,kA1,ram4,lsfw')
2011-12-07 17:31:39,410 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9baec> about HardwareID('modalias', 'usb:v05ACp0229d0009dc00dsc00dp00ic03isc01ip01')
2011-12-07 17:31:39,410 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9baec> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,3,kra0,1,mlsfw')
2011-12-07 17:31:39,410 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9baec> about HardwareID('modalias', 'pci:v000011ABd0000436Asv000011ABsd000000BAbc02sc00i00')
2011-12-07 17:31:39,410 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9baec> about HardwareID('modalias', 'dmi:bvnAppleInc.:bvrMB31.88Z.008E.B02.0803051832:bd03/05/08:svnAppleInc.:pnMacBook3,1:pvr1.0:rvnAppleInc.:rnMac-F22788C8:rvrPVT:cvnAppleInc.:ct2:cvrMac-F22788C8:')
2011-12-07 17:31:39,410 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9baec> about HardwareID('modalias', 'usb:v05ACp8503d0188dcEFdsc02dp01ic0Eisc02ip00')
2011-12-07 17:31:39,410 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9baec> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-12-07 17:31:39,411 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9baec> about HardwareID('modalias', 'usb:v05ACp8503d0188dcEFdsc02dp01ic0Eisc01ip00')
2011-12-07 17:31:39,411 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9baec> about HardwareID('modalias', 'input:b0003v045Ep0039e0110-e0,1,2,4,k110,111,112,113,114,r0,1,8,am4,lsfw')
2011-12-07 17:31:39,411 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9baec> about HardwareID('modalias', 'usb:v05ACp8205d1965dcE0dsc01dp01icE0isc01ip01')
2011-12-07 17:31:39,411 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9baec> about HardwareID('modalias', 'usb:v05ACp8205d1965dcE0dsc01dp01icFEisc01ip00')
2011-12-07 17:31:39,411 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9baec> about HardwareID('modalias', 'acpi:MEDIA-NOTIFY:')
2011-12-07 17:31:39,411 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9baec> about HardwareID('modalias', 'acpi:PNP0100:')
2011-12-07 17:31:39,411 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9baec> about HardwareID('modalias', 'pci:v00008086d00002815sv0000106Bsd000000A1bc06sc01i00')
2011-12-07 17:31:39,411 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9baec> about HardwareID('modalias', 'usb:v05ACp8242d0016dc00dsc00dp00ic03isc00ip00')
2011-12-07 17:31:39,411 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9baec> about HardwareID('modalias', 'pci:v00008086d0000283Asv0000106Bsd000000A1bc0Csc03i20')
2011-12-07 17:31:39,411 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9baec> about HardwareID('modalias', 'pci:v000011C1d00005811sv000011C1sd00005811bc0Csc00i10')
2011-12-07 17:31:39,411 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9baec> about HardwareID('modalias', 'pci:v00008086d00002831sv0000106Bsd000000A1bc0Csc03i00')
2011-12-07 17:31:39,411 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9baec> about HardwareID('modalias', 'platform:reg-dummy')
2011-12-07 17:31:39,411 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9baec> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-12-07 17:31:39,412 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9baec> about HardwareID('modalias', 'acpi:PNP0200:')
2011-12-07 17:31:39,412 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9baec> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-12-07 17:31:39,412 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9baec> about HardwareID('modalias', 'pci:v00008086d00002832sv0000106Bsd000000A1bc0Csc03i00')
2011-12-07 17:31:39,412 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9baec> about HardwareID('modalias', 'platform:applesmc')
2011-12-07 17:31:39,412 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9baec> about HardwareID('modalias', 'usb:v05ACp0229d0009dc00dsc00dp00ic03isc00ip00')
2011-12-07 17:31:39,412 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9baec> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2011-12-07 17:31:39,412 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9baec> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2011-12-07 17:31:39,412 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9baec> about HardwareID('modalias', 'input:b0003v05ACp8503e0188-e0,1,kD4,ramlsfw')
2011-12-07 17:31:39,412 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a9baec> about HardwareID('modalias', 'acpi:INT0800:')
2011-12-07 17:31:39,446 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-12-07 17:31:39,504 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-12-07 17:31:39,536 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-12-07 17:31:43,799 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-12-07 17:31:50,203 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-12-07 17:31:50,203 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2011-12-07 17:31:50,309 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-12-07 17:31:56,043 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-12-07 17:31:56,091 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-12-07 17:31:56,170 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-12-07 17:34:32,967 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-12-07 17:34:33,335 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-12-07 17:34:33,335 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2011-12-07 17:34:33,434 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-12-07 17:35:25,851 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-12-07 17:35:25,874 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-12-07 17:35:25,912 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-12-07 17:35:31,014 DEBUG: Shutting down
2011-12-07 17:35:41,065 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71fa64c>
2011-12-07 17:35:42,868 DEBUG: reading modalias file /lib/modules/3.0.0-13-generic-pae/modules.alias
2011-12-07 17:35:42,974 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2011-12-07 17:35:42,974 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-12-07 17:35:43,009 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2011-12-07 17:35:43,010 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2011-12-07 17:35:43,012 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2011-12-07 17:35:43,014 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2011-12-07 17:35:43,029 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2011-12-07 17:35:43,033 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2011-12-07 17:35:43,033 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2011-12-07 17:35:43,048 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2011-12-07 17:35:43,049 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2011-12-07 17:35:43,068 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2011-12-07 17:35:43,069 DEBUG: Firmware for DVB cards not available
2011-12-07 17:35:43,069 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2011-12-07 17:35:43,075 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2011-12-07 17:35:43,079 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2011-12-07 17:35:43,079 DEBUG: nvidia.available: falling back to default
2011-12-07 17:35:43,163 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-12-07 17:35:43,166 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-12-07 17:35:43,169 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2011-12-07 17:35:43,170 DEBUG: nvidia.available: falling back to default
2011-12-07 17:35:43,201 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-12-07 17:35:43,205 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2011-12-07 17:35:43,209 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2011-12-07 17:35:43,209 DEBUG: nvidia.available: falling back to default
2011-12-07 17:35:43,244 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-12-07 17:35:43,244 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 962, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2011-12-07 17:35:43,248 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2011-12-07 17:35:43,251 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2011-12-07 17:35:43,251 DEBUG: nvidia.available: falling back to default
2011-12-07 17:35:43,285 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-12-07 17:35:43,288 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-12-07 17:35:43,291 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2011-12-07 17:35:43,292 DEBUG: nvidia.available: falling back to default
2011-12-07 17:35:43,326 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-12-07 17:35:43,330 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2011-12-07 17:35:43,335 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2011-12-07 17:35:43,335 DEBUG: nvidia.available: falling back to default
2011-12-07 17:35:43,368 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-12-07 17:35:43,369 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2011-12-07 17:35:43,374 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2011-12-07 17:35:43,378 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2011-12-07 17:35:43,378 DEBUG: fglrx.available: falling back to default
2011-12-07 17:35:43,415 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2011-12-07 17:35:43,418 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-12-07 17:35:43,422 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2011-12-07 17:35:43,422 DEBUG: fglrx.available: falling back to default
2011-12-07 17:35:43,464 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2011-12-07 17:35:43,464 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2011-12-07 17:35:43,468 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2011-12-07 17:35:43,469 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2011-12-07 17:35:43,469 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2011-12-07 17:35:43,469 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2011-12-07 17:35:43,487 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2011-12-07 17:35:43,494 DEBUG: Software modem not available
2011-12-07 17:35:43,495 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-12-07 17:35:43,498 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-12-07 17:35:43,514 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2011-12-07 17:35:43,514 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2011-12-07 17:35:43,515 DEBUG: all custom handlers loaded
2011-12-07 17:35:43,515 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71fa64c> about HardwareID('modalias', 'pci:v00008086d00002834sv00000000sd00000000bc0Csc03i00')
2011-12-07 17:35:43,817 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71fa64c> about HardwareID('modalias', 'input:b0003v05ACp0229e0111-e0,1,4,11,14,k71,72,73,75,77,78,7D,7E,7F,A3,A4,A5,CC,E0,E1,E3,E4,E5,E6,1D0,ram4,l0,1,2,3,4,sfw')
2011-12-07 17:35:43,822 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-07 17:35:43,902 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:35:43,903 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71fa64c> about HardwareID('modalias', 'pci:v00008086d00002828sv0000106Bsd000000A1bc01sc01i8f')
2011-12-07 17:35:43,906 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71fa64c> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2011-12-07 17:35:43,907 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71fa64c> about HardwareID('modalias', 'acpi:APP0003:SMC-SMS:')
2011-12-07 17:35:43,907 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71fa64c> about HardwareID('modalias', 'pci:v00008086d00002835sv0000106Bsd000000A1bc0Csc03i00')
2011-12-07 17:35:43,910 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71fa64c> about HardwareID('modalias', 'input:b0003v05ACp0229e0009-e0,1,3,k110,145,14A,14D,14E,ra0,1,18,mlsfw')
2011-12-07 17:35:43,910 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-07 17:35:43,910 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:35:43,910 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-12-07 17:35:43,910 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:35:43,910 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-12-07 17:35:43,910 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:35:43,911 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71fa64c> about HardwareID('modalias', 'platform:eisa')
2011-12-07 17:35:43,911 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71fa64c> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2011-12-07 17:35:43,933 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71fa64c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2011-12-07 17:35:43,933 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-07 17:35:43,933 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:35:43,934 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71fa64c> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-12-07 17:35:43,934 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71fa64c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-12-07 17:35:43,934 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71fa64c> about HardwareID('modalias', 'pci:v00008086d00002836sv0000106Bsd000000A1bc0Csc03i20')
2011-12-07 17:35:43,938 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71fa64c> about HardwareID('modalias', 'platform:pcspkr')
2011-12-07 17:35:43,938 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2011-12-07 17:35:43,938 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:35:43,938 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2011-12-07 17:35:43,938 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:35:43,939 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71fa64c> about HardwareID('modalias', 'pci:v00008086d0000283Esv0000106Bsd000000A1bc0Csc05i00')
2011-12-07 17:35:43,942 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801'}
2011-12-07 17:35:43,942 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:35:43,942 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71fa64c> about HardwareID('modalias', 'pci:v00008086d00002A02sv0000106Bsd000000A1bc03sc00i00')
2011-12-07 17:35:43,946 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'intelfb'}
2011-12-07 17:35:43,946 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intelfb', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:35:43,946 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i915'}
2011-12-07 17:35:43,946 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:35:43,946 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71fa64c> about HardwareID('modalias', 'usb:v05ACp0229d0009dc00dsc00dp00ic03isc01ip02')
2011-12-07 17:35:43,970 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'appletouch'}
2011-12-07 17:35:43,970 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'appletouch', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:35:43,971 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-12-07 17:35:43,971 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:35:43,971 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2011-12-07 17:35:43,971 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:35:43,971 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71fa64c> about HardwareID('modalias', 'pci:v00008086d0000284Bsv0000106Bsd000000A1bc04sc03i00')
2011-12-07 17:35:43,974 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-12-07 17:35:43,974 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:35:43,975 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71fa64c> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-12-07 17:35:43,975 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71fa64c> about HardwareID('modalias', 'pci:v00008086d00002A03sv0000106Bsd000000A1bc03sc80i00')
2011-12-07 17:35:43,978 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71fa64c> about HardwareID('modalias', 'acpi:APP0001:SMC-SANTAROSA:')
2011-12-07 17:35:43,978 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71fa64c> about HardwareID('modalias', 'pci:v000014E4d00004328sv0000106Bsd00000088bc02sc80i00')
2011-12-07 17:35:44,021 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'wl', 'package': 'bcmwl-kernel-source'}
2011-12-07 17:35:44,021 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-12-07 17:35:44,021 DEBUG: found match in handler pool kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2011-12-07 17:35:44,025 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-12-07 17:35:44,025 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-12-07 17:35:44,025 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2011-12-07 17:35:44,025 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ssb'}
2011-12-07 17:35:44,026 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ssb', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:35:44,026 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71fa64c> about HardwareID('modalias', 'acpi:PNP0000:')
2011-12-07 17:35:44,026 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71fa64c> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-12-07 17:35:44,026 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71fa64c> about HardwareID('modalias', 'usb:v045Ep0039d0300dc00dsc00dp00ic03isc01ip02')
2011-12-07 17:35:44,083 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-12-07 17:35:44,083 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:35:44,083 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2011-12-07 17:35:44,084 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:35:44,084 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71fa64c> about HardwareID('modalias', 'pci:v00008086d00002830sv0000106Bsd000000A1bc0Csc03i00')
2011-12-07 17:35:44,087 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71fa64c> about HardwareID('modalias', 'pci:v00008086d00002850sv0000106Bsd000000A1bc01sc01i8a')
2011-12-07 17:35:44,091 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71fa64c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-12-07 17:35:44,091 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-07 17:35:44,091 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:35:44,091 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71fa64c> about HardwareID('modalias', 'input:b0003v05ACp0229e0111-e0,1,4,kA1,ram4,lsfw')
2011-12-07 17:35:44,091 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-07 17:35:44,092 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:35:44,092 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71fa64c> about HardwareID('modalias', 'usb:v05ACp0229d0009dc00dsc00dp00ic03isc01ip01')
2011-12-07 17:35:44,092 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-12-07 17:35:44,092 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:35:44,093 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2011-12-07 17:35:44,093 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:35:44,093 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71fa64c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,3,kra0,1,mlsfw')
2011-12-07 17:35:44,093 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-07 17:35:44,093 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:35:44,093 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-12-07 17:35:44,093 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:35:44,093 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71fa64c> about HardwareID('modalias', 'pci:v000011ABd0000436Asv000011ABsd000000BAbc02sc00i00')
2011-12-07 17:35:44,117 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sky2'}
2011-12-07 17:35:44,118 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sky2', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:35:44,118 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71fa64c> about HardwareID('modalias', 'dmi:bvnAppleInc.:bvrMB31.88Z.008E.B02.0803051832:bd03/05/08:svnAppleInc.:pnMacBook3,1:pvr1.0:rvnAppleInc.:rnMac-F22788C8:rvrPVT:cvnAppleInc.:ct2:cvrMac-F22788C8:')
2011-12-07 17:35:44,133 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71fa64c> about HardwareID('modalias', 'usb:v05ACp8503d0188dcEFdsc02dp01ic0Eisc02ip00')
2011-12-07 17:35:44,133 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71fa64c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-12-07 17:35:44,133 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71fa64c> about HardwareID('modalias', 'usb:v05ACp8503d0188dcEFdsc02dp01ic0Eisc01ip00')
2011-12-07 17:35:44,134 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2011-12-07 17:35:44,134 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:35:44,134 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71fa64c> about HardwareID('modalias', 'input:b0003v045Ep0039e0110-e0,1,2,4,k110,111,112,113,114,r0,1,8,am4,lsfw')
2011-12-07 17:35:44,134 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-07 17:35:44,134 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:35:44,134 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71fa64c> about HardwareID('modalias', 'usb:v05ACp8205d1965dcE0dsc01dp01icE0isc01ip01')
2011-12-07 17:35:44,135 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2011-12-07 17:35:44,135 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:35:44,135 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71fa64c> about HardwareID('modalias', 'usb:v05ACp8205d1965dcE0dsc01dp01icFEisc01ip00')
2011-12-07 17:35:44,136 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2011-12-07 17:35:44,136 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:35:44,136 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71fa64c> about HardwareID('modalias', 'acpi:MEDIA-NOTIFY:')
2011-12-07 17:35:44,136 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71fa64c> about HardwareID('modalias', 'acpi:PNP0100:')
2011-12-07 17:35:44,136 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71fa64c> about HardwareID('modalias', 'pci:v00008086d00002815sv0000106Bsd000000A1bc06sc01i00')
2011-12-07 17:35:44,139 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt'}
2011-12-07 17:35:44,140 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:35:44,140 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71fa64c> about HardwareID('modalias', 'usb:v05ACp8242d0016dc00dsc00dp00ic03isc00ip00')
2011-12-07 17:35:44,140 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-12-07 17:35:44,140 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:35:44,140 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71fa64c> about HardwareID('modalias', 'pci:v00008086d0000283Asv0000106Bsd000000A1bc0Csc03i20')
2011-12-07 17:35:44,143 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71fa64c> about HardwareID('modalias', 'pci:v000011C1d00005811sv000011C1sd00005811bc0Csc00i10')
2011-12-07 17:35:44,145 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci'}
2011-12-07 17:35:44,145 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:35:44,145 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71fa64c> about HardwareID('modalias', 'pci:v00008086d00002831sv0000106Bsd000000A1bc0Csc03i00')
2011-12-07 17:35:44,148 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71fa64c> about HardwareID('modalias', 'platform:reg-dummy')
2011-12-07 17:35:44,148 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71fa64c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-12-07 17:35:44,148 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-07 17:35:44,149 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:35:44,149 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71fa64c> about HardwareID('modalias', 'acpi:PNP0200:')
2011-12-07 17:35:44,149 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71fa64c> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-12-07 17:35:44,149 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71fa64c> about HardwareID('modalias', 'pci:v00008086d00002832sv0000106Bsd000000A1bc0Csc03i00')
2011-12-07 17:35:44,152 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71fa64c> about HardwareID('modalias', 'platform:applesmc')
2011-12-07 17:35:44,153 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71fa64c> about HardwareID('modalias', 'usb:v05ACp0229d0009dc00dsc00dp00ic03isc00ip00')
2011-12-07 17:35:44,153 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-12-07 17:35:44,153 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:35:44,154 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71fa64c> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2011-12-07 17:35:44,157 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71fa64c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2011-12-07 17:35:44,157 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-07 17:35:44,157 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:35:44,157 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71fa64c> about HardwareID('modalias', 'input:b0003v05ACp8503e0188-e0,1,kD4,ramlsfw')
2011-12-07 17:35:44,157 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-07 17:35:44,157 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:35:44,157 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71fa64c> about HardwareID('modalias', 'acpi:INT0800:')
2011-12-07 17:35:44,157 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f1aec> about HardwareID('modalias', 'pci:v00008086d00002834sv00000000sd00000000bc0Csc03i00')
2011-12-07 17:35:44,157 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f1aec> about HardwareID('modalias', 'input:b0003v05ACp0229e0111-e0,1,4,11,14,k71,72,73,75,77,78,7D,7E,7F,A3,A4,A5,CC,E0,E1,E3,E4,E5,E6,1D0,ram4,l0,1,2,3,4,sfw')
2011-12-07 17:35:44,158 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f1aec> about HardwareID('modalias', 'pci:v00008086d00002828sv0000106Bsd000000A1bc01sc01i8f')
2011-12-07 17:35:44,158 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f1aec> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2011-12-07 17:35:44,158 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f1aec> about HardwareID('modalias', 'acpi:APP0003:SMC-SMS:')
2011-12-07 17:35:44,158 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f1aec> about HardwareID('modalias', 'pci:v00008086d00002835sv0000106Bsd000000A1bc0Csc03i00')
2011-12-07 17:35:44,158 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f1aec> about HardwareID('modalias', 'input:b0003v05ACp0229e0009-e0,1,3,k110,145,14A,14D,14E,ra0,1,18,mlsfw')
2011-12-07 17:35:44,158 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f1aec> about HardwareID('modalias', 'platform:eisa')
2011-12-07 17:35:44,158 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f1aec> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2011-12-07 17:35:44,158 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f1aec> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2011-12-07 17:35:44,158 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f1aec> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-12-07 17:35:44,158 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f1aec> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-12-07 17:35:44,158 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f1aec> about HardwareID('modalias', 'pci:v00008086d00002836sv0000106Bsd000000A1bc0Csc03i20')
2011-12-07 17:35:44,158 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f1aec> about HardwareID('modalias', 'platform:pcspkr')
2011-12-07 17:35:44,159 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f1aec> about HardwareID('modalias', 'pci:v00008086d0000283Esv0000106Bsd000000A1bc0Csc05i00')
2011-12-07 17:35:44,159 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f1aec> about HardwareID('modalias', 'pci:v00008086d00002A02sv0000106Bsd000000A1bc03sc00i00')
2011-12-07 17:35:44,159 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f1aec> about HardwareID('modalias', 'usb:v05ACp0229d0009dc00dsc00dp00ic03isc01ip02')
2011-12-07 17:35:44,159 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f1aec> about HardwareID('modalias', 'pci:v00008086d0000284Bsv0000106Bsd000000A1bc04sc03i00')
2011-12-07 17:35:44,159 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f1aec> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-12-07 17:35:44,159 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f1aec> about HardwareID('modalias', 'pci:v00008086d00002A03sv0000106Bsd000000A1bc03sc80i00')
2011-12-07 17:35:44,159 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f1aec> about HardwareID('modalias', 'acpi:APP0001:SMC-SANTAROSA:')
2011-12-07 17:35:44,159 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f1aec> about HardwareID('modalias', 'pci:v000014E4d00004328sv0000106Bsd00000088bc02sc80i00')
2011-12-07 17:35:44,159 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f1aec> about HardwareID('modalias', 'acpi:PNP0000:')
2011-12-07 17:35:44,159 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f1aec> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-12-07 17:35:44,159 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f1aec> about HardwareID('modalias', 'usb:v045Ep0039d0300dc00dsc00dp00ic03isc01ip02')
2011-12-07 17:35:44,159 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f1aec> about HardwareID('modalias', 'pci:v00008086d00002830sv0000106Bsd000000A1bc0Csc03i00')
2011-12-07 17:35:44,159 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f1aec> about HardwareID('modalias', 'pci:v00008086d00002850sv0000106Bsd000000A1bc01sc01i8a')
2011-12-07 17:35:44,160 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f1aec> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-12-07 17:35:44,160 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f1aec> about HardwareID('modalias', 'input:b0003v05ACp0229e0111-e0,1,4,kA1,ram4,lsfw')
2011-12-07 17:35:44,160 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f1aec> about HardwareID('modalias', 'usb:v05ACp0229d0009dc00dsc00dp00ic03isc01ip01')
2011-12-07 17:35:44,160 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f1aec> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,3,kra0,1,mlsfw')
2011-12-07 17:35:44,160 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f1aec> about HardwareID('modalias', 'pci:v000011ABd0000436Asv000011ABsd000000BAbc02sc00i00')
2011-12-07 17:35:44,160 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f1aec> about HardwareID('modalias', 'dmi:bvnAppleInc.:bvrMB31.88Z.008E.B02.0803051832:bd03/05/08:svnAppleInc.:pnMacBook3,1:pvr1.0:rvnAppleInc.:rnMac-F22788C8:rvrPVT:cvnAppleInc.:ct2:cvrMac-F22788C8:')
2011-12-07 17:35:44,160 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f1aec> about HardwareID('modalias', 'usb:v05ACp8503d0188dcEFdsc02dp01ic0Eisc02ip00')
2011-12-07 17:35:44,160 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f1aec> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-12-07 17:35:44,160 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f1aec> about HardwareID('modalias', 'usb:v05ACp8503d0188dcEFdsc02dp01ic0Eisc01ip00')
2011-12-07 17:35:44,160 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f1aec> about HardwareID('modalias', 'input:b0003v045Ep0039e0110-e0,1,2,4,k110,111,112,113,114,r0,1,8,am4,lsfw')
2011-12-07 17:35:44,160 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f1aec> about HardwareID('modalias', 'usb:v05ACp8205d1965dcE0dsc01dp01icE0isc01ip01')
2011-12-07 17:35:44,160 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f1aec> about HardwareID('modalias', 'usb:v05ACp8205d1965dcE0dsc01dp01icFEisc01ip00')
2011-12-07 17:35:44,161 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f1aec> about HardwareID('modalias', 'acpi:MEDIA-NOTIFY:')
2011-12-07 17:35:44,161 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f1aec> about HardwareID('modalias', 'acpi:PNP0100:')
2011-12-07 17:35:44,161 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f1aec> about HardwareID('modalias', 'pci:v00008086d00002815sv0000106Bsd000000A1bc06sc01i00')
2011-12-07 17:35:44,161 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f1aec> about HardwareID('modalias', 'usb:v05ACp8242d0016dc00dsc00dp00ic03isc00ip00')
2011-12-07 17:35:44,161 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f1aec> about HardwareID('modalias', 'pci:v00008086d0000283Asv0000106Bsd000000A1bc0Csc03i20')
2011-12-07 17:35:44,161 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f1aec> about HardwareID('modalias', 'pci:v000011C1d00005811sv000011C1sd00005811bc0Csc00i10')
2011-12-07 17:35:44,161 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f1aec> about HardwareID('modalias', 'pci:v00008086d00002831sv0000106Bsd000000A1bc0Csc03i00')
2011-12-07 17:35:44,161 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f1aec> about HardwareID('modalias', 'platform:reg-dummy')
2011-12-07 17:35:44,161 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f1aec> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-12-07 17:35:44,161 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f1aec> about HardwareID('modalias', 'acpi:PNP0200:')
2011-12-07 17:35:44,161 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f1aec> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-12-07 17:35:44,161 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f1aec> about HardwareID('modalias', 'pci:v00008086d00002832sv0000106Bsd000000A1bc0Csc03i00')
2011-12-07 17:35:44,161 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f1aec> about HardwareID('modalias', 'platform:applesmc')
2011-12-07 17:35:44,162 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f1aec> about HardwareID('modalias', 'usb:v05ACp0229d0009dc00dsc00dp00ic03isc00ip00')
2011-12-07 17:35:44,162 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f1aec> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2011-12-07 17:35:44,162 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f1aec> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2011-12-07 17:35:44,162 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f1aec> about HardwareID('modalias', 'input:b0003v05ACp8503e0188-e0,1,kD4,ramlsfw')
2011-12-07 17:35:44,162 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68f1aec> about HardwareID('modalias', 'acpi:INT0800:')
2011-12-07 17:35:44,207 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-12-07 17:35:44,229 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-12-07 17:35:44,270 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-12-07 17:35:47,081 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-12-07 17:35:51,517 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-12-07 17:35:51,518 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2011-12-07 17:35:51,574 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-12-07 17:39:35,321 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-12-07 17:39:35,370 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-12-07 17:39:35,449 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-12-07 17:39:37,313 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-12-07 17:39:37,686 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-12-07 17:39:37,686 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2011-12-07 17:39:37,775 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-12-07 17:39:38,997 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-12-07 17:39:39,016 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-12-07 17:39:39,058 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-12-07 17:39:41,884 DEBUG: Shutting down
2011-12-07 17:39:47,526 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71e464c>
2011-12-07 17:39:49,344 DEBUG: reading modalias file /lib/modules/3.0.0-13-generic-pae/modules.alias
2011-12-07 17:39:49,455 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2011-12-07 17:39:49,455 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-12-07 17:39:49,492 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2011-12-07 17:39:49,493 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2011-12-07 17:39:49,495 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2011-12-07 17:39:49,496 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2011-12-07 17:39:49,512 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2011-12-07 17:39:49,516 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2011-12-07 17:39:49,516 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2011-12-07 17:39:49,532 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2011-12-07 17:39:49,533 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2011-12-07 17:39:49,555 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2011-12-07 17:39:49,556 DEBUG: Firmware for DVB cards not available
2011-12-07 17:39:49,556 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2011-12-07 17:39:49,564 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2011-12-07 17:39:49,568 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2011-12-07 17:39:49,569 DEBUG: nvidia.available: falling back to default
2011-12-07 17:39:49,657 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-12-07 17:39:49,661 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-12-07 17:39:49,664 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2011-12-07 17:39:49,665 DEBUG: nvidia.available: falling back to default
2011-12-07 17:39:49,698 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-12-07 17:39:49,701 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2011-12-07 17:39:49,705 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2011-12-07 17:39:49,705 DEBUG: nvidia.available: falling back to default
2011-12-07 17:39:49,741 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-12-07 17:39:49,742 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 962, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2011-12-07 17:39:49,746 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2011-12-07 17:39:49,749 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2011-12-07 17:39:49,750 DEBUG: nvidia.available: falling back to default
2011-12-07 17:39:49,783 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-12-07 17:39:49,786 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-12-07 17:39:49,790 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2011-12-07 17:39:49,790 DEBUG: nvidia.available: falling back to default
2011-12-07 17:39:49,824 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-12-07 17:39:49,827 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2011-12-07 17:39:49,831 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2011-12-07 17:39:49,831 DEBUG: nvidia.available: falling back to default
2011-12-07 17:39:49,865 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-12-07 17:39:49,866 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2011-12-07 17:39:49,871 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2011-12-07 17:39:49,875 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2011-12-07 17:39:49,876 DEBUG: fglrx.available: falling back to default
2011-12-07 17:39:49,919 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2011-12-07 17:39:49,924 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-12-07 17:39:49,928 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2011-12-07 17:39:49,929 DEBUG: fglrx.available: falling back to default
2011-12-07 17:39:49,967 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2011-12-07 17:39:49,967 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2011-12-07 17:39:49,971 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2011-12-07 17:39:49,972 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2011-12-07 17:39:49,972 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2011-12-07 17:39:49,972 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2011-12-07 17:39:49,994 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2011-12-07 17:39:50,001 DEBUG: Software modem not available
2011-12-07 17:39:50,001 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-12-07 17:39:50,005 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-12-07 17:39:50,024 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2011-12-07 17:39:50,024 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2011-12-07 17:39:50,024 DEBUG: all custom handlers loaded
2011-12-07 17:39:50,025 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71e464c> about HardwareID('modalias', 'pci:v00008086d00002834sv00000000sd00000000bc0Csc03i00')
2011-12-07 17:39:50,330 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71e464c> about HardwareID('modalias', 'input:b0003v05ACp0229e0111-e0,1,4,11,14,k71,72,73,75,77,78,7D,7E,7F,A3,A4,A5,CC,E0,E1,E3,E4,E5,E6,1D0,ram4,l0,1,2,3,4,sfw')
2011-12-07 17:39:50,334 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-07 17:39:50,412 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:39:50,413 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71e464c> about HardwareID('modalias', 'pci:v00008086d00002828sv0000106Bsd000000A1bc01sc01i8f')
2011-12-07 17:39:50,416 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71e464c> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2011-12-07 17:39:50,417 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71e464c> about HardwareID('modalias', 'acpi:APP0003:SMC-SMS:')
2011-12-07 17:39:50,417 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71e464c> about HardwareID('modalias', 'pci:v00008086d00002835sv0000106Bsd000000A1bc0Csc03i00')
2011-12-07 17:39:50,420 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71e464c> about HardwareID('modalias', 'input:b0003v05ACp0229e0009-e0,1,3,k110,145,14A,14D,14E,ra0,1,18,mlsfw')
2011-12-07 17:39:50,420 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-07 17:39:50,420 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:39:50,420 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-12-07 17:39:50,420 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:39:50,420 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-12-07 17:39:50,420 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:39:50,420 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71e464c> about HardwareID('modalias', 'platform:eisa')
2011-12-07 17:39:50,421 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71e464c> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2011-12-07 17:39:50,443 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71e464c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2011-12-07 17:39:50,443 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-07 17:39:50,443 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:39:50,443 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71e464c> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-12-07 17:39:50,443 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71e464c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-12-07 17:39:50,444 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71e464c> about HardwareID('modalias', 'pci:v00008086d00002836sv0000106Bsd000000A1bc0Csc03i20')
2011-12-07 17:39:50,447 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71e464c> about HardwareID('modalias', 'platform:pcspkr')
2011-12-07 17:39:50,447 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2011-12-07 17:39:50,448 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:39:50,448 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2011-12-07 17:39:50,448 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:39:50,448 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71e464c> about HardwareID('modalias', 'pci:v00008086d0000283Esv0000106Bsd000000A1bc0Csc05i00')
2011-12-07 17:39:50,451 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801'}
2011-12-07 17:39:50,451 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:39:50,451 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71e464c> about HardwareID('modalias', 'pci:v00008086d00002A02sv0000106Bsd000000A1bc03sc00i00')
2011-12-07 17:39:50,454 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'intelfb'}
2011-12-07 17:39:50,454 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intelfb', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:39:50,454 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i915'}
2011-12-07 17:39:50,455 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:39:50,455 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71e464c> about HardwareID('modalias', 'usb:v05ACp0229d0009dc00dsc00dp00ic03isc01ip02')
2011-12-07 17:39:50,479 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'appletouch'}
2011-12-07 17:39:50,479 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'appletouch', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:39:50,479 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-12-07 17:39:50,479 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:39:50,479 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2011-12-07 17:39:50,479 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:39:50,479 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71e464c> about HardwareID('modalias', 'pci:v00008086d0000284Bsv0000106Bsd000000A1bc04sc03i00')
2011-12-07 17:39:50,483 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-12-07 17:39:50,483 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:39:50,483 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71e464c> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-12-07 17:39:50,483 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71e464c> about HardwareID('modalias', 'pci:v00008086d00002A03sv0000106Bsd000000A1bc03sc80i00')
2011-12-07 17:39:50,486 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71e464c> about HardwareID('modalias', 'acpi:APP0001:SMC-SANTAROSA:')
2011-12-07 17:39:50,486 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71e464c> about HardwareID('modalias', 'pci:v000014E4d00004328sv0000106Bsd00000088bc02sc80i00')
2011-12-07 17:39:50,529 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'wl', 'package': 'bcmwl-kernel-source'}
2011-12-07 17:39:50,530 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-12-07 17:39:50,530 DEBUG: found match in handler pool kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2011-12-07 17:39:50,533 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-12-07 17:39:50,534 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-12-07 17:39:50,534 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2011-12-07 17:39:50,534 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ssb'}
2011-12-07 17:39:50,534 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ssb', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:39:50,534 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71e464c> about HardwareID('modalias', 'acpi:PNP0000:')
2011-12-07 17:39:50,534 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71e464c> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-12-07 17:39:50,534 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71e464c> about HardwareID('modalias', 'usb:v045Ep0039d0300dc00dsc00dp00ic03isc01ip02')
2011-12-07 17:39:50,592 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-12-07 17:39:50,592 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:39:50,592 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2011-12-07 17:39:50,592 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:39:50,592 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71e464c> about HardwareID('modalias', 'pci:v00008086d00002830sv0000106Bsd000000A1bc0Csc03i00')
2011-12-07 17:39:50,596 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71e464c> about HardwareID('modalias', 'pci:v00008086d00002850sv0000106Bsd000000A1bc01sc01i8a')
2011-12-07 17:39:50,599 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71e464c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-12-07 17:39:50,599 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-07 17:39:50,599 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:39:50,599 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71e464c> about HardwareID('modalias', 'input:b0003v05ACp0229e0111-e0,1,4,kA1,ram4,lsfw')
2011-12-07 17:39:50,600 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-07 17:39:50,600 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:39:50,600 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71e464c> about HardwareID('modalias', 'usb:v05ACp0229d0009dc00dsc00dp00ic03isc01ip01')
2011-12-07 17:39:50,600 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-12-07 17:39:50,601 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:39:50,601 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2011-12-07 17:39:50,601 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:39:50,601 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71e464c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,3,kra0,1,mlsfw')
2011-12-07 17:39:50,601 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-07 17:39:50,601 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:39:50,601 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-12-07 17:39:50,601 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:39:50,601 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71e464c> about HardwareID('modalias', 'pci:v000011ABd0000436Asv000011ABsd000000BAbc02sc00i00')
2011-12-07 17:39:50,625 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sky2'}
2011-12-07 17:39:50,625 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sky2', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:39:50,625 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71e464c> about HardwareID('modalias', 'dmi:bvnAppleInc.:bvrMB31.88Z.008E.B02.0803051832:bd03/05/08:svnAppleInc.:pnMacBook3,1:pvr1.0:rvnAppleInc.:rnMac-F22788C8:rvrPVT:cvnAppleInc.:ct2:cvrMac-F22788C8:')
2011-12-07 17:39:50,640 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71e464c> about HardwareID('modalias', 'usb:v05ACp8503d0188dcEFdsc02dp01ic0Eisc02ip00')
2011-12-07 17:39:50,640 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71e464c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-12-07 17:39:50,640 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71e464c> about HardwareID('modalias', 'usb:v05ACp8503d0188dcEFdsc02dp01ic0Eisc01ip00')
2011-12-07 17:39:50,641 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2011-12-07 17:39:50,641 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:39:50,641 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71e464c> about HardwareID('modalias', 'input:b0003v045Ep0039e0110-e0,1,2,4,k110,111,112,113,114,r0,1,8,am4,lsfw')
2011-12-07 17:39:50,641 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-07 17:39:50,642 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:39:50,642 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71e464c> about HardwareID('modalias', 'usb:v05ACp8205d1965dcE0dsc01dp01icE0isc01ip01')
2011-12-07 17:39:50,642 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2011-12-07 17:39:50,642 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:39:50,642 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71e464c> about HardwareID('modalias', 'usb:v05ACp8205d1965dcE0dsc01dp01icFEisc01ip00')
2011-12-07 17:39:50,643 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2011-12-07 17:39:50,643 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:39:50,643 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71e464c> about HardwareID('modalias', 'acpi:MEDIA-NOTIFY:')
2011-12-07 17:39:50,643 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71e464c> about HardwareID('modalias', 'acpi:PNP0100:')
2011-12-07 17:39:50,643 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71e464c> about HardwareID('modalias', 'pci:v00008086d00002815sv0000106Bsd000000A1bc06sc01i00')
2011-12-07 17:39:50,647 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt'}
2011-12-07 17:39:50,647 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:39:50,647 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71e464c> about HardwareID('modalias', 'usb:v05ACp8242d0016dc00dsc00dp00ic03isc00ip00')
2011-12-07 17:39:50,648 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-12-07 17:39:50,648 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:39:50,648 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71e464c> about HardwareID('modalias', 'pci:v00008086d0000283Asv0000106Bsd000000A1bc0Csc03i20')
2011-12-07 17:39:50,651 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71e464c> about HardwareID('modalias', 'pci:v000011C1d00005811sv000011C1sd00005811bc0Csc00i10')
2011-12-07 17:39:50,652 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci'}
2011-12-07 17:39:50,653 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:39:50,653 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71e464c> about HardwareID('modalias', 'pci:v00008086d00002831sv0000106Bsd000000A1bc0Csc03i00')
2011-12-07 17:39:50,656 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71e464c> about HardwareID('modalias', 'platform:reg-dummy')
2011-12-07 17:39:50,656 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71e464c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-12-07 17:39:50,656 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-07 17:39:50,656 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:39:50,657 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71e464c> about HardwareID('modalias', 'acpi:PNP0200:')
2011-12-07 17:39:50,657 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71e464c> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-12-07 17:39:50,657 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71e464c> about HardwareID('modalias', 'pci:v00008086d00002832sv0000106Bsd000000A1bc0Csc03i00')
2011-12-07 17:39:50,660 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71e464c> about HardwareID('modalias', 'platform:applesmc')
2011-12-07 17:39:50,661 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71e464c> about HardwareID('modalias', 'usb:v05ACp0229d0009dc00dsc00dp00ic03isc00ip00')
2011-12-07 17:39:50,661 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-12-07 17:39:50,661 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:39:50,661 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71e464c> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2011-12-07 17:39:50,664 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71e464c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2011-12-07 17:39:50,664 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-07 17:39:50,665 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:39:50,665 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71e464c> about HardwareID('modalias', 'input:b0003v05ACp8503e0188-e0,1,kD4,ramlsfw')
2011-12-07 17:39:50,665 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-07 17:39:50,665 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:39:50,665 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71e464c> about HardwareID('modalias', 'acpi:INT0800:')
2011-12-07 17:39:50,665 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68dbaec> about HardwareID('modalias', 'pci:v00008086d00002834sv00000000sd00000000bc0Csc03i00')
2011-12-07 17:39:50,665 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68dbaec> about HardwareID('modalias', 'input:b0003v05ACp0229e0111-e0,1,4,11,14,k71,72,73,75,77,78,7D,7E,7F,A3,A4,A5,CC,E0,E1,E3,E4,E5,E6,1D0,ram4,l0,1,2,3,4,sfw')
2011-12-07 17:39:50,665 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68dbaec> about HardwareID('modalias', 'pci:v00008086d00002828sv0000106Bsd000000A1bc01sc01i8f')
2011-12-07 17:39:50,665 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68dbaec> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2011-12-07 17:39:50,666 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68dbaec> about HardwareID('modalias', 'acpi:APP0003:SMC-SMS:')
2011-12-07 17:39:50,666 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68dbaec> about HardwareID('modalias', 'pci:v00008086d00002835sv0000106Bsd000000A1bc0Csc03i00')
2011-12-07 17:39:50,666 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68dbaec> about HardwareID('modalias', 'input:b0003v05ACp0229e0009-e0,1,3,k110,145,14A,14D,14E,ra0,1,18,mlsfw')
2011-12-07 17:39:50,666 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68dbaec> about HardwareID('modalias', 'platform:eisa')
2011-12-07 17:39:50,666 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68dbaec> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2011-12-07 17:39:50,666 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68dbaec> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2011-12-07 17:39:50,666 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68dbaec> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-12-07 17:39:50,666 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68dbaec> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-12-07 17:39:50,666 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68dbaec> about HardwareID('modalias', 'pci:v00008086d00002836sv0000106Bsd000000A1bc0Csc03i20')
2011-12-07 17:39:50,666 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68dbaec> about HardwareID('modalias', 'platform:pcspkr')
2011-12-07 17:39:50,666 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68dbaec> about HardwareID('modalias', 'pci:v00008086d0000283Esv0000106Bsd000000A1bc0Csc05i00')
2011-12-07 17:39:50,666 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68dbaec> about HardwareID('modalias', 'pci:v00008086d00002A02sv0000106Bsd000000A1bc03sc00i00')
2011-12-07 17:39:50,667 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68dbaec> about HardwareID('modalias', 'usb:v05ACp0229d0009dc00dsc00dp00ic03isc01ip02')
2011-12-07 17:39:50,667 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68dbaec> about HardwareID('modalias', 'pci:v00008086d0000284Bsv0000106Bsd000000A1bc04sc03i00')
2011-12-07 17:39:50,667 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68dbaec> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-12-07 17:39:50,667 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68dbaec> about HardwareID('modalias', 'pci:v00008086d00002A03sv0000106Bsd000000A1bc03sc80i00')
2011-12-07 17:39:50,667 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68dbaec> about HardwareID('modalias', 'acpi:APP0001:SMC-SANTAROSA:')
2011-12-07 17:39:50,667 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68dbaec> about HardwareID('modalias', 'pci:v000014E4d00004328sv0000106Bsd00000088bc02sc80i00')
2011-12-07 17:39:50,667 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68dbaec> about HardwareID('modalias', 'acpi:PNP0000:')
2011-12-07 17:39:50,667 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68dbaec> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-12-07 17:39:50,667 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68dbaec> about HardwareID('modalias', 'usb:v045Ep0039d0300dc00dsc00dp00ic03isc01ip02')
2011-12-07 17:39:50,667 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68dbaec> about HardwareID('modalias', 'pci:v00008086d00002830sv0000106Bsd000000A1bc0Csc03i00')
2011-12-07 17:39:50,667 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68dbaec> about HardwareID('modalias', 'pci:v00008086d00002850sv0000106Bsd000000A1bc01sc01i8a')
2011-12-07 17:39:50,667 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68dbaec> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-12-07 17:39:50,667 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68dbaec> about HardwareID('modalias', 'input:b0003v05ACp0229e0111-e0,1,4,kA1,ram4,lsfw')
2011-12-07 17:39:50,668 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68dbaec> about HardwareID('modalias', 'usb:v05ACp0229d0009dc00dsc00dp00ic03isc01ip01')
2011-12-07 17:39:50,668 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68dbaec> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,3,kra0,1,mlsfw')
2011-12-07 17:39:50,668 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68dbaec> about HardwareID('modalias', 'pci:v000011ABd0000436Asv000011ABsd000000BAbc02sc00i00')
2011-12-07 17:39:50,668 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68dbaec> about HardwareID('modalias', 'dmi:bvnAppleInc.:bvrMB31.88Z.008E.B02.0803051832:bd03/05/08:svnAppleInc.:pnMacBook3,1:pvr1.0:rvnAppleInc.:rnMac-F22788C8:rvrPVT:cvnAppleInc.:ct2:cvrMac-F22788C8:')
2011-12-07 17:39:50,668 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68dbaec> about HardwareID('modalias', 'usb:v05ACp8503d0188dcEFdsc02dp01ic0Eisc02ip00')
2011-12-07 17:39:50,668 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68dbaec> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-12-07 17:39:50,668 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68dbaec> about HardwareID('modalias', 'usb:v05ACp8503d0188dcEFdsc02dp01ic0Eisc01ip00')
2011-12-07 17:39:50,668 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68dbaec> about HardwareID('modalias', 'input:b0003v045Ep0039e0110-e0,1,2,4,k110,111,112,113,114,r0,1,8,am4,lsfw')
2011-12-07 17:39:50,668 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68dbaec> about HardwareID('modalias', 'usb:v05ACp8205d1965dcE0dsc01dp01icE0isc01ip01')
2011-12-07 17:39:50,668 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68dbaec> about HardwareID('modalias', 'usb:v05ACp8205d1965dcE0dsc01dp01icFEisc01ip00')
2011-12-07 17:39:50,668 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68dbaec> about HardwareID('modalias', 'acpi:MEDIA-NOTIFY:')
2011-12-07 17:39:50,668 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68dbaec> about HardwareID('modalias', 'acpi:PNP0100:')
2011-12-07 17:39:50,669 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68dbaec> about HardwareID('modalias', 'pci:v00008086d00002815sv0000106Bsd000000A1bc06sc01i00')
2011-12-07 17:39:50,669 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68dbaec> about HardwareID('modalias', 'usb:v05ACp8242d0016dc00dsc00dp00ic03isc00ip00')
2011-12-07 17:39:50,669 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68dbaec> about HardwareID('modalias', 'pci:v00008086d0000283Asv0000106Bsd000000A1bc0Csc03i20')
2011-12-07 17:39:50,669 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68dbaec> about HardwareID('modalias', 'pci:v000011C1d00005811sv000011C1sd00005811bc0Csc00i10')
2011-12-07 17:39:50,669 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68dbaec> about HardwareID('modalias', 'pci:v00008086d00002831sv0000106Bsd000000A1bc0Csc03i00')
2011-12-07 17:39:50,669 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68dbaec> about HardwareID('modalias', 'platform:reg-dummy')
2011-12-07 17:39:50,669 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68dbaec> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-12-07 17:39:50,669 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68dbaec> about HardwareID('modalias', 'acpi:PNP0200:')
2011-12-07 17:39:50,669 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68dbaec> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-12-07 17:39:50,669 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68dbaec> about HardwareID('modalias', 'pci:v00008086d00002832sv0000106Bsd000000A1bc0Csc03i00')
2011-12-07 17:39:50,669 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68dbaec> about HardwareID('modalias', 'platform:applesmc')
2011-12-07 17:39:50,669 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68dbaec> about HardwareID('modalias', 'usb:v05ACp0229d0009dc00dsc00dp00ic03isc00ip00')
2011-12-07 17:39:50,670 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68dbaec> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2011-12-07 17:39:50,670 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68dbaec> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2011-12-07 17:39:50,670 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68dbaec> about HardwareID('modalias', 'input:b0003v05ACp8503e0188-e0,1,kD4,ramlsfw')
2011-12-07 17:39:50,670 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68dbaec> about HardwareID('modalias', 'acpi:INT0800:')
2011-12-07 17:39:50,714 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-12-07 17:39:50,737 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-12-07 17:39:50,785 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-12-07 17:39:56,015 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-12-07 17:40:00,228 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-12-07 17:40:00,228 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2011-12-07 17:40:00,283 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-12-07 17:43:10,226 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-12-07 17:43:10,245 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-12-07 17:43:10,285 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-12-07 17:43:11,856 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-12-07 17:43:12,223 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-12-07 17:43:12,224 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2011-12-07 17:43:12,300 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-12-07 17:43:14,328 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-12-07 17:43:14,348 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-12-07 17:43:14,381 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-12-07 17:43:15,222 DEBUG: Shutting down
2011-12-07 17:43:21,118 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xb729b64c>
2011-12-07 17:43:22,930 DEBUG: reading modalias file /lib/modules/3.0.0-13-generic-pae/modules.alias
2011-12-07 17:43:23,034 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2011-12-07 17:43:23,035 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-12-07 17:43:23,068 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2011-12-07 17:43:23,069 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2011-12-07 17:43:23,071 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2011-12-07 17:43:23,072 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2011-12-07 17:43:23,087 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2011-12-07 17:43:23,091 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2011-12-07 17:43:23,091 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2011-12-07 17:43:23,107 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2011-12-07 17:43:23,107 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2011-12-07 17:43:23,128 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2011-12-07 17:43:23,128 DEBUG: Firmware for DVB cards not available
2011-12-07 17:43:23,128 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2011-12-07 17:43:23,135 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2011-12-07 17:43:23,139 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2011-12-07 17:43:23,139 DEBUG: nvidia.available: falling back to default
2011-12-07 17:43:23,223 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-12-07 17:43:23,227 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-12-07 17:43:23,230 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2011-12-07 17:43:23,231 DEBUG: nvidia.available: falling back to default
2011-12-07 17:43:23,264 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-12-07 17:43:23,270 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2011-12-07 17:43:23,274 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2011-12-07 17:43:23,274 DEBUG: nvidia.available: falling back to default
2011-12-07 17:43:23,306 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-12-07 17:43:23,306 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 962, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2011-12-07 17:43:23,310 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2011-12-07 17:43:23,313 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2011-12-07 17:43:23,314 DEBUG: nvidia.available: falling back to default
2011-12-07 17:43:23,358 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-12-07 17:43:23,362 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-12-07 17:43:23,366 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2011-12-07 17:43:23,366 DEBUG: nvidia.available: falling back to default
2011-12-07 17:43:23,404 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-12-07 17:43:23,409 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2011-12-07 17:43:23,413 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2011-12-07 17:43:23,413 DEBUG: nvidia.available: falling back to default
2011-12-07 17:43:23,459 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-12-07 17:43:23,460 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2011-12-07 17:43:23,469 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2011-12-07 17:43:23,472 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2011-12-07 17:43:23,473 DEBUG: fglrx.available: falling back to default
2011-12-07 17:43:23,509 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2011-12-07 17:43:23,513 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-12-07 17:43:23,516 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2011-12-07 17:43:23,516 DEBUG: fglrx.available: falling back to default
2011-12-07 17:43:23,553 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2011-12-07 17:43:23,554 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2011-12-07 17:43:23,558 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2011-12-07 17:43:23,558 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2011-12-07 17:43:23,558 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2011-12-07 17:43:23,558 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2011-12-07 17:43:23,575 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2011-12-07 17:43:23,583 DEBUG: Software modem not available
2011-12-07 17:43:23,583 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-12-07 17:43:23,587 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-12-07 17:43:23,603 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2011-12-07 17:43:23,603 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2011-12-07 17:43:23,603 DEBUG: all custom handlers loaded
2011-12-07 17:43:23,603 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb729b64c> about HardwareID('modalias', 'pci:v00008086d00002834sv00000000sd00000000bc0Csc03i00')
2011-12-07 17:43:23,907 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb729b64c> about HardwareID('modalias', 'input:b0003v05ACp0229e0111-e0,1,4,11,14,k71,72,73,75,77,78,7D,7E,7F,A3,A4,A5,CC,E0,E1,E3,E4,E5,E6,1D0,ram4,l0,1,2,3,4,sfw')
2011-12-07 17:43:23,912 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-07 17:43:23,990 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:43:23,990 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb729b64c> about HardwareID('modalias', 'pci:v00008086d00002828sv0000106Bsd000000A1bc01sc01i8f')
2011-12-07 17:43:23,994 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb729b64c> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2011-12-07 17:43:23,994 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb729b64c> about HardwareID('modalias', 'acpi:APP0003:SMC-SMS:')
2011-12-07 17:43:23,994 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb729b64c> about HardwareID('modalias', 'pci:v00008086d00002835sv0000106Bsd000000A1bc0Csc03i00')
2011-12-07 17:43:23,997 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb729b64c> about HardwareID('modalias', 'input:b0003v05ACp0229e0009-e0,1,3,k110,145,14A,14D,14E,ra0,1,18,mlsfw')
2011-12-07 17:43:23,997 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-07 17:43:23,997 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:43:23,997 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-12-07 17:43:23,997 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:43:23,997 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-12-07 17:43:23,998 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:43:23,998 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb729b64c> about HardwareID('modalias', 'platform:eisa')
2011-12-07 17:43:23,998 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb729b64c> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2011-12-07 17:43:24,021 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb729b64c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2011-12-07 17:43:24,021 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-07 17:43:24,021 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:43:24,021 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb729b64c> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-12-07 17:43:24,021 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb729b64c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-12-07 17:43:24,022 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb729b64c> about HardwareID('modalias', 'pci:v00008086d00002836sv0000106Bsd000000A1bc0Csc03i20')
2011-12-07 17:43:24,025 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb729b64c> about HardwareID('modalias', 'platform:pcspkr')
2011-12-07 17:43:24,026 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2011-12-07 17:43:24,026 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:43:24,026 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2011-12-07 17:43:24,026 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:43:24,026 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb729b64c> about HardwareID('modalias', 'pci:v00008086d0000283Esv0000106Bsd000000A1bc0Csc05i00')
2011-12-07 17:43:24,029 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801'}
2011-12-07 17:43:24,029 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:43:24,030 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb729b64c> about HardwareID('modalias', 'pci:v00008086d00002A02sv0000106Bsd000000A1bc03sc00i00')
2011-12-07 17:43:24,033 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'intelfb'}
2011-12-07 17:43:24,033 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intelfb', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:43:24,033 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i915'}
2011-12-07 17:43:24,033 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:43:24,033 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb729b64c> about HardwareID('modalias', 'usb:v05ACp0229d0009dc00dsc00dp00ic03isc01ip02')
2011-12-07 17:43:24,057 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'appletouch'}
2011-12-07 17:43:24,058 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'appletouch', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:43:24,058 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-12-07 17:43:24,058 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:43:24,058 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2011-12-07 17:43:24,058 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:43:24,058 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb729b64c> about HardwareID('modalias', 'pci:v00008086d0000284Bsv0000106Bsd000000A1bc04sc03i00')
2011-12-07 17:43:24,061 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-12-07 17:43:24,062 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:43:24,062 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb729b64c> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-12-07 17:43:24,062 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb729b64c> about HardwareID('modalias', 'pci:v00008086d00002A03sv0000106Bsd000000A1bc03sc80i00')
2011-12-07 17:43:24,065 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb729b64c> about HardwareID('modalias', 'acpi:APP0001:SMC-SANTAROSA:')
2011-12-07 17:43:24,065 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb729b64c> about HardwareID('modalias', 'pci:v000014E4d00004328sv0000106Bsd00000088bc02sc80i00')
2011-12-07 17:43:24,108 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'wl', 'package': 'bcmwl-kernel-source'}
2011-12-07 17:43:24,109 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-12-07 17:43:24,109 DEBUG: found match in handler pool kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2011-12-07 17:43:24,113 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-12-07 17:43:24,113 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-12-07 17:43:24,113 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2011-12-07 17:43:24,113 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ssb'}
2011-12-07 17:43:24,113 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ssb', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:43:24,114 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb729b64c> about HardwareID('modalias', 'acpi:PNP0000:')
2011-12-07 17:43:24,114 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb729b64c> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-12-07 17:43:24,114 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb729b64c> about HardwareID('modalias', 'usb:v045Ep0039d0300dc00dsc00dp00ic03isc01ip02')
2011-12-07 17:43:24,171 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-12-07 17:43:24,171 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:43:24,171 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2011-12-07 17:43:24,172 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:43:24,172 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb729b64c> about HardwareID('modalias', 'pci:v00008086d00002830sv0000106Bsd000000A1bc0Csc03i00')
2011-12-07 17:43:24,175 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb729b64c> about HardwareID('modalias', 'pci:v00008086d00002850sv0000106Bsd000000A1bc01sc01i8a')
2011-12-07 17:43:24,179 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb729b64c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-12-07 17:43:24,179 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-07 17:43:24,179 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:43:24,179 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb729b64c> about HardwareID('modalias', 'input:b0003v05ACp0229e0111-e0,1,4,kA1,ram4,lsfw')
2011-12-07 17:43:24,179 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-07 17:43:24,179 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:43:24,179 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb729b64c> about HardwareID('modalias', 'usb:v05ACp0229d0009dc00dsc00dp00ic03isc01ip01')
2011-12-07 17:43:24,180 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-12-07 17:43:24,180 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:43:24,180 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2011-12-07 17:43:24,180 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:43:24,180 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb729b64c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,3,kra0,1,mlsfw')
2011-12-07 17:43:24,181 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-07 17:43:24,181 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:43:24,181 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-12-07 17:43:24,181 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:43:24,181 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb729b64c> about HardwareID('modalias', 'pci:v000011ABd0000436Asv000011ABsd000000BAbc02sc00i00')
2011-12-07 17:43:24,205 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sky2'}
2011-12-07 17:43:24,205 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sky2', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:43:24,205 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb729b64c> about HardwareID('modalias', 'dmi:bvnAppleInc.:bvrMB31.88Z.008E.B02.0803051832:bd03/05/08:svnAppleInc.:pnMacBook3,1:pvr1.0:rvnAppleInc.:rnMac-F22788C8:rvrPVT:cvnAppleInc.:ct2:cvrMac-F22788C8:')
2011-12-07 17:43:24,220 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb729b64c> about HardwareID('modalias', 'usb:v05ACp8503d0188dcEFdsc02dp01ic0Eisc02ip00')
2011-12-07 17:43:24,221 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb729b64c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-12-07 17:43:24,221 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb729b64c> about HardwareID('modalias', 'usb:v05ACp8503d0188dcEFdsc02dp01ic0Eisc01ip00')
2011-12-07 17:43:24,221 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2011-12-07 17:43:24,221 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:43:24,221 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb729b64c> about HardwareID('modalias', 'input:b0003v045Ep0039e0110-e0,1,2,4,k110,111,112,113,114,r0,1,8,am4,lsfw')
2011-12-07 17:43:24,222 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-07 17:43:24,222 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:43:24,222 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb729b64c> about HardwareID('modalias', 'usb:v05ACp8205d1965dcE0dsc01dp01icE0isc01ip01')
2011-12-07 17:43:24,222 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2011-12-07 17:43:24,223 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:43:24,223 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb729b64c> about HardwareID('modalias', 'usb:v05ACp8205d1965dcE0dsc01dp01icFEisc01ip00')
2011-12-07 17:43:24,223 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2011-12-07 17:43:24,223 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:43:24,223 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb729b64c> about HardwareID('modalias', 'acpi:MEDIA-NOTIFY:')
2011-12-07 17:43:24,223 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb729b64c> about HardwareID('modalias', 'acpi:PNP0100:')
2011-12-07 17:43:24,224 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb729b64c> about HardwareID('modalias', 'pci:v00008086d00002815sv0000106Bsd000000A1bc06sc01i00')
2011-12-07 17:43:24,227 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt'}
2011-12-07 17:43:24,227 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:43:24,227 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb729b64c> about HardwareID('modalias', 'usb:v05ACp8242d0016dc00dsc00dp00ic03isc00ip00')
2011-12-07 17:43:24,227 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-12-07 17:43:24,228 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:43:24,228 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb729b64c> about HardwareID('modalias', 'pci:v00008086d0000283Asv0000106Bsd000000A1bc0Csc03i20')
2011-12-07 17:43:24,231 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb729b64c> about HardwareID('modalias', 'pci:v000011C1d00005811sv000011C1sd00005811bc0Csc00i10')
2011-12-07 17:43:24,232 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci'}
2011-12-07 17:43:24,232 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:43:24,232 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb729b64c> about HardwareID('modalias', 'pci:v00008086d00002831sv0000106Bsd000000A1bc0Csc03i00')
2011-12-07 17:43:24,235 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb729b64c> about HardwareID('modalias', 'platform:reg-dummy')
2011-12-07 17:43:24,236 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb729b64c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-12-07 17:43:24,236 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-07 17:43:24,236 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:43:24,236 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb729b64c> about HardwareID('modalias', 'acpi:PNP0200:')
2011-12-07 17:43:24,236 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb729b64c> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-12-07 17:43:24,236 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb729b64c> about HardwareID('modalias', 'pci:v00008086d00002832sv0000106Bsd000000A1bc0Csc03i00')
2011-12-07 17:43:24,239 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb729b64c> about HardwareID('modalias', 'platform:applesmc')
2011-12-07 17:43:24,240 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb729b64c> about HardwareID('modalias', 'usb:v05ACp0229d0009dc00dsc00dp00ic03isc00ip00')
2011-12-07 17:43:24,241 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-12-07 17:43:24,241 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:43:24,241 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb729b64c> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2011-12-07 17:43:24,244 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb729b64c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2011-12-07 17:43:24,244 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-07 17:43:24,244 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:43:24,244 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb729b64c> about HardwareID('modalias', 'input:b0003v05ACp8503e0188-e0,1,kD4,ramlsfw')
2011-12-07 17:43:24,245 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-07 17:43:24,245 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:43:24,245 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb729b64c> about HardwareID('modalias', 'acpi:INT0800:')
2011-12-07 17:43:24,245 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6992aec> about HardwareID('modalias', 'pci:v00008086d00002834sv00000000sd00000000bc0Csc03i00')
2011-12-07 17:43:24,245 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6992aec> about HardwareID('modalias', 'input:b0003v05ACp0229e0111-e0,1,4,11,14,k71,72,73,75,77,78,7D,7E,7F,A3,A4,A5,CC,E0,E1,E3,E4,E5,E6,1D0,ram4,l0,1,2,3,4,sfw')
2011-12-07 17:43:24,245 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6992aec> about HardwareID('modalias', 'pci:v00008086d00002828sv0000106Bsd000000A1bc01sc01i8f')
2011-12-07 17:43:24,245 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6992aec> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2011-12-07 17:43:24,245 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6992aec> about HardwareID('modalias', 'acpi:APP0003:SMC-SMS:')
2011-12-07 17:43:24,245 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6992aec> about HardwareID('modalias', 'pci:v00008086d00002835sv0000106Bsd000000A1bc0Csc03i00')
2011-12-07 17:43:24,245 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6992aec> about HardwareID('modalias', 'input:b0003v05ACp0229e0009-e0,1,3,k110,145,14A,14D,14E,ra0,1,18,mlsfw')
2011-12-07 17:43:24,245 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6992aec> about HardwareID('modalias', 'platform:eisa')
2011-12-07 17:43:24,246 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6992aec> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2011-12-07 17:43:24,246 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6992aec> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2011-12-07 17:43:24,246 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6992aec> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-12-07 17:43:24,246 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6992aec> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-12-07 17:43:24,246 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6992aec> about HardwareID('modalias', 'pci:v00008086d00002836sv0000106Bsd000000A1bc0Csc03i20')
2011-12-07 17:43:24,246 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6992aec> about HardwareID('modalias', 'platform:pcspkr')
2011-12-07 17:43:24,246 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6992aec> about HardwareID('modalias', 'pci:v00008086d0000283Esv0000106Bsd000000A1bc0Csc05i00')
2011-12-07 17:43:24,246 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6992aec> about HardwareID('modalias', 'pci:v00008086d00002A02sv0000106Bsd000000A1bc03sc00i00')
2011-12-07 17:43:24,246 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6992aec> about HardwareID('modalias', 'usb:v05ACp0229d0009dc00dsc00dp00ic03isc01ip02')
2011-12-07 17:43:24,246 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6992aec> about HardwareID('modalias', 'pci:v00008086d0000284Bsv0000106Bsd000000A1bc04sc03i00')
2011-12-07 17:43:24,246 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6992aec> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-12-07 17:43:24,246 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6992aec> about HardwareID('modalias', 'pci:v00008086d00002A03sv0000106Bsd000000A1bc03sc80i00')
2011-12-07 17:43:24,247 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6992aec> about HardwareID('modalias', 'acpi:APP0001:SMC-SANTAROSA:')
2011-12-07 17:43:24,247 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6992aec> about HardwareID('modalias', 'pci:v000014E4d00004328sv0000106Bsd00000088bc02sc80i00')
2011-12-07 17:43:24,247 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6992aec> about HardwareID('modalias', 'acpi:PNP0000:')
2011-12-07 17:43:24,247 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6992aec> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-12-07 17:43:24,247 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6992aec> about HardwareID('modalias', 'usb:v045Ep0039d0300dc00dsc00dp00ic03isc01ip02')
2011-12-07 17:43:24,247 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6992aec> about HardwareID('modalias', 'pci:v00008086d00002830sv0000106Bsd000000A1bc0Csc03i00')
2011-12-07 17:43:24,247 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6992aec> about HardwareID('modalias', 'pci:v00008086d00002850sv0000106Bsd000000A1bc01sc01i8a')
2011-12-07 17:43:24,247 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6992aec> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-12-07 17:43:24,247 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6992aec> about HardwareID('modalias', 'input:b0003v05ACp0229e0111-e0,1,4,kA1,ram4,lsfw')
2011-12-07 17:43:24,247 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6992aec> about HardwareID('modalias', 'usb:v05ACp0229d0009dc00dsc00dp00ic03isc01ip01')
2011-12-07 17:43:24,247 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6992aec> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,3,kra0,1,mlsfw')
2011-12-07 17:43:24,247 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6992aec> about HardwareID('modalias', 'pci:v000011ABd0000436Asv000011ABsd000000BAbc02sc00i00')
2011-12-07 17:43:24,247 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6992aec> about HardwareID('modalias', 'dmi:bvnAppleInc.:bvrMB31.88Z.008E.B02.0803051832:bd03/05/08:svnAppleInc.:pnMacBook3,1:pvr1.0:rvnAppleInc.:rnMac-F22788C8:rvrPVT:cvnAppleInc.:ct2:cvrMac-F22788C8:')
2011-12-07 17:43:24,248 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6992aec> about HardwareID('modalias', 'usb:v05ACp8503d0188dcEFdsc02dp01ic0Eisc02ip00')
2011-12-07 17:43:24,248 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6992aec> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-12-07 17:43:24,248 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6992aec> about HardwareID('modalias', 'usb:v05ACp8503d0188dcEFdsc02dp01ic0Eisc01ip00')
2011-12-07 17:43:24,248 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6992aec> about HardwareID('modalias', 'input:b0003v045Ep0039e0110-e0,1,2,4,k110,111,112,113,114,r0,1,8,am4,lsfw')
2011-12-07 17:43:24,248 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6992aec> about HardwareID('modalias', 'usb:v05ACp8205d1965dcE0dsc01dp01icE0isc01ip01')
2011-12-07 17:43:24,248 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6992aec> about HardwareID('modalias', 'usb:v05ACp8205d1965dcE0dsc01dp01icFEisc01ip00')
2011-12-07 17:43:24,248 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6992aec> about HardwareID('modalias', 'acpi:MEDIA-NOTIFY:')
2011-12-07 17:43:24,248 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6992aec> about HardwareID('modalias', 'acpi:PNP0100:')
2011-12-07 17:43:24,248 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6992aec> about HardwareID('modalias', 'pci:v00008086d00002815sv0000106Bsd000000A1bc06sc01i00')
2011-12-07 17:43:24,248 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6992aec> about HardwareID('modalias', 'usb:v05ACp8242d0016dc00dsc00dp00ic03isc00ip00')
2011-12-07 17:43:24,248 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6992aec> about HardwareID('modalias', 'pci:v00008086d0000283Asv0000106Bsd000000A1bc0Csc03i20')
2011-12-07 17:43:24,248 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6992aec> about HardwareID('modalias', 'pci:v000011C1d00005811sv000011C1sd00005811bc0Csc00i10')
2011-12-07 17:43:24,249 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6992aec> about HardwareID('modalias', 'pci:v00008086d00002831sv0000106Bsd000000A1bc0Csc03i00')
2011-12-07 17:43:24,249 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6992aec> about HardwareID('modalias', 'platform:reg-dummy')
2011-12-07 17:43:24,249 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6992aec> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-12-07 17:43:24,249 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6992aec> about HardwareID('modalias', 'acpi:PNP0200:')
2011-12-07 17:43:24,249 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6992aec> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-12-07 17:43:24,249 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6992aec> about HardwareID('modalias', 'pci:v00008086d00002832sv0000106Bsd000000A1bc0Csc03i00')
2011-12-07 17:43:24,249 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6992aec> about HardwareID('modalias', 'platform:applesmc')
2011-12-07 17:43:24,249 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6992aec> about HardwareID('modalias', 'usb:v05ACp0229d0009dc00dsc00dp00ic03isc00ip00')
2011-12-07 17:43:24,249 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6992aec> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2011-12-07 17:43:24,249 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6992aec> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2011-12-07 17:43:24,249 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6992aec> about HardwareID('modalias', 'input:b0003v05ACp8503e0188-e0,1,kD4,ramlsfw')
2011-12-07 17:43:24,249 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6992aec> about HardwareID('modalias', 'acpi:INT0800:')
2011-12-07 17:43:24,301 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-12-07 17:43:24,328 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-12-07 17:43:24,371 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-12-07 17:43:26,350 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-12-07 17:43:30,040 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-12-07 17:43:30,041 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2011-12-07 17:43:30,101 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-12-07 17:48:12,658 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71d664c>
2011-12-07 17:48:15,328 DEBUG: reading modalias file /lib/modules/3.0.0-13-generic-pae/modules.alias
2011-12-07 17:48:15,574 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2011-12-07 17:48:15,616 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-12-07 17:48:15,674 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2011-12-07 17:48:15,710 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2011-12-07 17:48:15,842 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2011-12-07 17:48:15,897 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2011-12-07 17:48:15,937 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2011-12-07 17:48:16,763 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2011-12-07 17:48:16,763 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2011-12-07 17:48:16,779 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2011-12-07 17:48:16,779 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2011-12-07 17:48:17,305 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2011-12-07 17:48:17,306 DEBUG: Firmware for DVB cards not available
2011-12-07 17:48:17,306 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2011-12-07 17:48:17,767 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2011-12-07 17:48:17,771 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2011-12-07 17:48:17,771 DEBUG: nvidia.available: falling back to default
2011-12-07 17:48:18,546 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-12-07 17:48:18,549 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-12-07 17:48:18,553 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2011-12-07 17:48:18,554 DEBUG: nvidia.available: falling back to default
2011-12-07 17:48:18,586 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-12-07 17:48:18,590 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2011-12-07 17:48:18,594 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2011-12-07 17:48:18,594 DEBUG: nvidia.available: falling back to default
2011-12-07 17:48:18,626 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-12-07 17:48:18,626 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 962, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2011-12-07 17:48:18,664 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2011-12-07 17:48:18,668 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2011-12-07 17:48:18,668 DEBUG: nvidia.available: falling back to default
2011-12-07 17:48:18,700 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-12-07 17:48:18,703 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-12-07 17:48:18,707 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2011-12-07 17:48:18,707 DEBUG: nvidia.available: falling back to default
2011-12-07 17:48:18,743 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-12-07 17:48:18,747 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2011-12-07 17:48:18,751 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2011-12-07 17:48:18,751 DEBUG: nvidia.available: falling back to default
2011-12-07 17:48:18,784 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-12-07 17:48:18,784 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2011-12-07 17:48:18,790 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2011-12-07 17:48:18,794 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2011-12-07 17:48:18,794 DEBUG: fglrx.available: falling back to default
2011-12-07 17:48:18,831 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2011-12-07 17:48:18,835 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-12-07 17:48:18,839 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2011-12-07 17:48:18,839 DEBUG: fglrx.available: falling back to default
2011-12-07 17:48:18,894 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2011-12-07 17:48:18,894 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2011-12-07 17:48:18,910 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2011-12-07 17:48:18,911 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2011-12-07 17:48:18,911 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2011-12-07 17:48:18,911 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2011-12-07 17:48:18,932 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2011-12-07 17:48:18,958 DEBUG: Software modem not available
2011-12-07 17:48:18,958 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-12-07 17:48:18,970 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-12-07 17:48:18,987 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2011-12-07 17:48:18,987 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2011-12-07 17:48:18,987 DEBUG: all custom handlers loaded
2011-12-07 17:48:18,987 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71d664c> about HardwareID('modalias', 'pci:v00008086d00002834sv00000000sd00000000bc0Csc03i00')
2011-12-07 17:48:19,307 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71d664c> about HardwareID('modalias', 'input:b0003v05ACp0229e0111-e0,1,4,11,14,k71,72,73,75,77,78,7D,7E,7F,A3,A4,A5,CC,E0,E1,E3,E4,E5,E6,1D0,ram4,l0,1,2,3,4,sfw')
2011-12-07 17:48:19,313 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-07 17:48:19,436 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:48:19,437 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71d664c> about HardwareID('modalias', 'pci:v00008086d00002828sv0000106Bsd000000A1bc01sc01i8f')
2011-12-07 17:48:19,441 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71d664c> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2011-12-07 17:48:19,441 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71d664c> about HardwareID('modalias', 'acpi:APP0003:SMC-SMS:')
2011-12-07 17:48:19,441 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71d664c> about HardwareID('modalias', 'pci:v00008086d00002835sv0000106Bsd000000A1bc0Csc03i00')
2011-12-07 17:48:19,445 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71d664c> about HardwareID('modalias', 'input:b0003v05ACp0229e0009-e0,1,3,k110,145,14A,14D,14E,ra0,1,18,mlsfw')
2011-12-07 17:48:19,445 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-07 17:48:19,445 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:48:19,445 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-12-07 17:48:19,445 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:48:19,445 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-12-07 17:48:19,446 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:48:19,446 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71d664c> about HardwareID('modalias', 'platform:eisa')
2011-12-07 17:48:19,446 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71d664c> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2011-12-07 17:48:19,469 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71d664c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2011-12-07 17:48:19,469 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-07 17:48:19,469 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:48:19,469 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71d664c> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-12-07 17:48:19,469 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71d664c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-12-07 17:48:19,470 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71d664c> about HardwareID('modalias', 'pci:v00008086d00002836sv0000106Bsd000000A1bc0Csc03i20')
2011-12-07 17:48:19,473 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71d664c> about HardwareID('modalias', 'platform:pcspkr')
2011-12-07 17:48:19,474 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2011-12-07 17:48:19,474 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:48:19,474 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2011-12-07 17:48:19,474 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:48:19,474 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71d664c> about HardwareID('modalias', 'pci:v00008086d0000283Esv0000106Bsd000000A1bc0Csc05i00')
2011-12-07 17:48:19,478 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801'}
2011-12-07 17:48:19,478 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:48:19,478 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71d664c> about HardwareID('modalias', 'pci:v00008086d00002A02sv0000106Bsd000000A1bc03sc00i00')
2011-12-07 17:48:19,481 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'intelfb'}
2011-12-07 17:48:19,481 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intelfb', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:48:19,482 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i915'}
2011-12-07 17:48:19,482 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:48:19,482 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71d664c> about HardwareID('modalias', 'usb:v05ACp0229d0009dc00dsc00dp00ic03isc01ip02')
2011-12-07 17:48:19,506 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'appletouch'}
2011-12-07 17:48:19,507 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'appletouch', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:48:19,507 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-12-07 17:48:19,507 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:48:19,507 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2011-12-07 17:48:19,507 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:48:19,507 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71d664c> about HardwareID('modalias', 'pci:v00008086d0000284Bsv0000106Bsd000000A1bc04sc03i00')
2011-12-07 17:48:19,510 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-12-07 17:48:19,511 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:48:19,511 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71d664c> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-12-07 17:48:19,511 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71d664c> about HardwareID('modalias', 'pci:v00008086d00002A03sv0000106Bsd000000A1bc03sc80i00')
2011-12-07 17:48:19,514 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71d664c> about HardwareID('modalias', 'acpi:APP0001:SMC-SANTAROSA:')
2011-12-07 17:48:19,514 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71d664c> about HardwareID('modalias', 'pci:v000014E4d00004328sv0000106Bsd00000088bc02sc80i00')
2011-12-07 17:48:19,558 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'wl', 'package': 'bcmwl-kernel-source'}
2011-12-07 17:48:19,559 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-12-07 17:48:19,558 DEBUG: found match in handler pool kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2011-12-07 17:48:19,563 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-12-07 17:48:19,563 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-12-07 17:48:19,563 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2011-12-07 17:48:19,563 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ssb'}
2011-12-07 17:48:19,563 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ssb', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:48:19,563 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71d664c> about HardwareID('modalias', 'acpi:PNP0000:')
2011-12-07 17:48:19,564 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71d664c> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-12-07 17:48:19,564 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71d664c> about HardwareID('modalias', 'usb:v045Ep0039d0300dc00dsc00dp00ic03isc01ip02')
2011-12-07 17:48:19,622 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-12-07 17:48:19,623 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:48:19,623 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2011-12-07 17:48:19,623 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:48:19,623 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71d664c> about HardwareID('modalias', 'pci:v00008086d00002830sv0000106Bsd000000A1bc0Csc03i00')
2011-12-07 17:48:19,627 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71d664c> about HardwareID('modalias', 'pci:v00008086d00002850sv0000106Bsd000000A1bc01sc01i8a')
2011-12-07 17:48:19,630 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71d664c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-12-07 17:48:19,630 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-07 17:48:19,630 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:48:19,631 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71d664c> about HardwareID('modalias', 'input:b0003v05ACp0229e0111-e0,1,4,kA1,ram4,lsfw')
2011-12-07 17:48:19,631 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-07 17:48:19,631 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:48:19,631 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71d664c> about HardwareID('modalias', 'usb:v05ACp0229d0009dc00dsc00dp00ic03isc01ip01')
2011-12-07 17:48:19,632 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-12-07 17:48:19,632 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:48:19,632 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2011-12-07 17:48:19,632 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:48:19,632 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71d664c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,3,kra0,1,mlsfw')
2011-12-07 17:48:19,632 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-07 17:48:19,632 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:48:19,632 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-12-07 17:48:19,632 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:48:19,633 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71d664c> about HardwareID('modalias', 'pci:v000011ABd0000436Asv000011ABsd000000BAbc02sc00i00')
2011-12-07 17:48:19,658 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sky2'}
2011-12-07 17:48:19,658 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sky2', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:48:19,659 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71d664c> about HardwareID('modalias', 'dmi:bvnAppleInc.:bvrMB31.88Z.008E.B02.0803051832:bd03/05/08:svnAppleInc.:pnMacBook3,1:pvr1.0:rvnAppleInc.:rnMac-F22788C8:rvrPVT:cvnAppleInc.:ct2:cvrMac-F22788C8:')
2011-12-07 17:48:19,673 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71d664c> about HardwareID('modalias', 'usb:v05ACp8503d0188dcEFdsc02dp01ic0Eisc02ip00')
2011-12-07 17:48:19,674 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71d664c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-12-07 17:48:19,674 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71d664c> about HardwareID('modalias', 'usb:v05ACp8503d0188dcEFdsc02dp01ic0Eisc01ip00')
2011-12-07 17:48:19,674 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2011-12-07 17:48:19,675 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:48:19,675 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71d664c> about HardwareID('modalias', 'input:b0003v045Ep0039e0110-e0,1,2,4,k110,111,112,113,114,r0,1,8,am4,lsfw')
2011-12-07 17:48:19,675 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-07 17:48:19,675 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:48:19,675 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71d664c> about HardwareID('modalias', 'usb:v05ACp8205d1965dcE0dsc01dp01icE0isc01ip01')
2011-12-07 17:48:19,676 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2011-12-07 17:48:19,676 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:48:19,676 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71d664c> about HardwareID('modalias', 'usb:v05ACp8205d1965dcE0dsc01dp01icFEisc01ip00')
2011-12-07 17:48:19,676 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2011-12-07 17:48:19,677 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:48:19,677 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71d664c> about HardwareID('modalias', 'acpi:MEDIA-NOTIFY:')
2011-12-07 17:48:19,677 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71d664c> about HardwareID('modalias', 'acpi:PNP0100:')
2011-12-07 17:48:19,677 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71d664c> about HardwareID('modalias', 'pci:v00008086d00002815sv0000106Bsd000000A1bc06sc01i00')
2011-12-07 17:48:19,680 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt'}
2011-12-07 17:48:19,680 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:48:19,680 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71d664c> about HardwareID('modalias', 'usb:v05ACp8242d0016dc00dsc00dp00ic03isc00ip00')
2011-12-07 17:48:19,681 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-12-07 17:48:19,681 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:48:19,681 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71d664c> about HardwareID('modalias', 'pci:v00008086d0000283Asv0000106Bsd000000A1bc0Csc03i20')
2011-12-07 17:48:19,684 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71d664c> about HardwareID('modalias', 'pci:v000011C1d00005811sv000011C1sd00005811bc0Csc00i10')
2011-12-07 17:48:19,686 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci'}
2011-12-07 17:48:19,686 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:48:19,686 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71d664c> about HardwareID('modalias', 'pci:v00008086d00002831sv0000106Bsd000000A1bc0Csc03i00')
2011-12-07 17:48:19,689 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71d664c> about HardwareID('modalias', 'platform:reg-dummy')
2011-12-07 17:48:19,690 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71d664c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-12-07 17:48:19,690 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-07 17:48:19,690 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:48:19,690 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71d664c> about HardwareID('modalias', 'acpi:PNP0200:')
2011-12-07 17:48:19,690 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71d664c> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-12-07 17:48:19,690 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71d664c> about HardwareID('modalias', 'pci:v00008086d00002832sv0000106Bsd000000A1bc0Csc03i00')
2011-12-07 17:48:19,694 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71d664c> about HardwareID('modalias', 'platform:applesmc')
2011-12-07 17:48:19,694 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71d664c> about HardwareID('modalias', 'usb:v05ACp0229d0009dc00dsc00dp00ic03isc00ip00')
2011-12-07 17:48:19,695 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-12-07 17:48:19,695 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:48:19,695 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71d664c> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2011-12-07 17:48:19,698 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71d664c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2011-12-07 17:48:19,698 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-07 17:48:19,699 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:48:19,699 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71d664c> about HardwareID('modalias', 'input:b0003v05ACp8503e0188-e0,1,kD4,ramlsfw')
2011-12-07 17:48:19,699 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-07 17:48:19,699 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 17:48:19,699 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb71d664c> about HardwareID('modalias', 'acpi:INT0800:')
2011-12-07 17:48:19,699 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68cdb0c> about HardwareID('modalias', 'pci:v00008086d00002834sv00000000sd00000000bc0Csc03i00')
2011-12-07 17:48:19,699 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68cdb0c> about HardwareID('modalias', 'input:b0003v05ACp0229e0111-e0,1,4,11,14,k71,72,73,75,77,78,7D,7E,7F,A3,A4,A5,CC,E0,E1,E3,E4,E5,E6,1D0,ram4,l0,1,2,3,4,sfw')
2011-12-07 17:48:19,699 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68cdb0c> about HardwareID('modalias', 'pci:v00008086d00002828sv0000106Bsd000000A1bc01sc01i8f')
2011-12-07 17:48:19,699 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68cdb0c> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2011-12-07 17:48:19,700 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68cdb0c> about HardwareID('modalias', 'acpi:APP0003:SMC-SMS:')
2011-12-07 17:48:19,700 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68cdb0c> about HardwareID('modalias', 'pci:v00008086d00002835sv0000106Bsd000000A1bc0Csc03i00')
2011-12-07 17:48:19,700 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68cdb0c> about HardwareID('modalias', 'input:b0003v05ACp0229e0009-e0,1,3,k110,145,14A,14D,14E,ra0,1,18,mlsfw')
2011-12-07 17:48:19,700 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68cdb0c> about HardwareID('modalias', 'platform:eisa')
2011-12-07 17:48:19,700 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68cdb0c> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2011-12-07 17:48:19,700 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68cdb0c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2011-12-07 17:48:19,700 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68cdb0c> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-12-07 17:48:19,700 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68cdb0c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-12-07 17:48:19,700 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68cdb0c> about HardwareID('modalias', 'pci:v00008086d00002836sv0000106Bsd000000A1bc0Csc03i20')
2011-12-07 17:48:19,700 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68cdb0c> about HardwareID('modalias', 'platform:pcspkr')
2011-12-07 17:48:19,700 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68cdb0c> about HardwareID('modalias', 'pci:v00008086d0000283Esv0000106Bsd000000A1bc0Csc05i00')
2011-12-07 17:48:19,700 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68cdb0c> about HardwareID('modalias', 'pci:v00008086d00002A02sv0000106Bsd000000A1bc03sc00i00')
2011-12-07 17:48:19,700 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68cdb0c> about HardwareID('modalias', 'usb:v05ACp0229d0009dc00dsc00dp00ic03isc01ip02')
2011-12-07 17:48:19,701 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68cdb0c> about HardwareID('modalias', 'pci:v00008086d0000284Bsv0000106Bsd000000A1bc04sc03i00')
2011-12-07 17:48:19,701 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68cdb0c> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-12-07 17:48:19,701 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68cdb0c> about HardwareID('modalias', 'pci:v00008086d00002A03sv0000106Bsd000000A1bc03sc80i00')
2011-12-07 17:48:19,701 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68cdb0c> about HardwareID('modalias', 'acpi:APP0001:SMC-SANTAROSA:')
2011-12-07 17:48:19,701 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68cdb0c> about HardwareID('modalias', 'pci:v000014E4d00004328sv0000106Bsd00000088bc02sc80i00')
2011-12-07 17:48:19,701 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68cdb0c> about HardwareID('modalias', 'acpi:PNP0000:')
2011-12-07 17:48:19,701 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68cdb0c> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-12-07 17:48:19,701 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68cdb0c> about HardwareID('modalias', 'usb:v045Ep0039d0300dc00dsc00dp00ic03isc01ip02')
2011-12-07 17:48:19,701 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68cdb0c> about HardwareID('modalias', 'pci:v00008086d00002830sv0000106Bsd000000A1bc0Csc03i00')
2011-12-07 17:48:19,701 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68cdb0c> about HardwareID('modalias', 'pci:v00008086d00002850sv0000106Bsd000000A1bc01sc01i8a')
2011-12-07 17:48:19,701 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68cdb0c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-12-07 17:48:19,701 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68cdb0c> about HardwareID('modalias', 'input:b0003v05ACp0229e0111-e0,1,4,kA1,ram4,lsfw')
2011-12-07 17:48:19,702 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68cdb0c> about HardwareID('modalias', 'usb:v05ACp0229d0009dc00dsc00dp00ic03isc01ip01')
2011-12-07 17:48:19,702 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68cdb0c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,3,kra0,1,mlsfw')
2011-12-07 17:48:19,702 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68cdb0c> about HardwareID('modalias', 'pci:v000011ABd0000436Asv000011ABsd000000BAbc02sc00i00')
2011-12-07 17:48:19,702 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68cdb0c> about HardwareID('modalias', 'dmi:bvnAppleInc.:bvrMB31.88Z.008E.B02.0803051832:bd03/05/08:svnAppleInc.:pnMacBook3,1:pvr1.0:rvnAppleInc.:rnMac-F22788C8:rvrPVT:cvnAppleInc.:ct2:cvrMac-F22788C8:')
2011-12-07 17:48:19,702 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68cdb0c> about HardwareID('modalias', 'usb:v05ACp8503d0188dcEFdsc02dp01ic0Eisc02ip00')
2011-12-07 17:48:19,702 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68cdb0c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-12-07 17:48:19,702 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68cdb0c> about HardwareID('modalias', 'usb:v05ACp8503d0188dcEFdsc02dp01ic0Eisc01ip00')
2011-12-07 17:48:19,702 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68cdb0c> about HardwareID('modalias', 'input:b0003v045Ep0039e0110-e0,1,2,4,k110,111,112,113,114,r0,1,8,am4,lsfw')
2011-12-07 17:48:19,702 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68cdb0c> about HardwareID('modalias', 'usb:v05ACp8205d1965dcE0dsc01dp01icE0isc01ip01')
2011-12-07 17:48:19,702 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68cdb0c> about HardwareID('modalias', 'usb:v05ACp8205d1965dcE0dsc01dp01icFEisc01ip00')
2011-12-07 17:48:19,702 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68cdb0c> about HardwareID('modalias', 'acpi:MEDIA-NOTIFY:')
2011-12-07 17:48:19,702 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68cdb0c> about HardwareID('modalias', 'acpi:PNP0100:')
2011-12-07 17:48:19,703 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68cdb0c> about HardwareID('modalias', 'pci:v00008086d00002815sv0000106Bsd000000A1bc06sc01i00')
2011-12-07 17:48:19,703 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68cdb0c> about HardwareID('modalias', 'usb:v05ACp8242d0016dc00dsc00dp00ic03isc00ip00')
2011-12-07 17:48:19,703 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68cdb0c> about HardwareID('modalias', 'pci:v00008086d0000283Asv0000106Bsd000000A1bc0Csc03i20')
2011-12-07 17:48:19,703 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68cdb0c> about HardwareID('modalias', 'pci:v000011C1d00005811sv000011C1sd00005811bc0Csc00i10')
2011-12-07 17:48:19,703 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68cdb0c> about HardwareID('modalias', 'pci:v00008086d00002831sv0000106Bsd000000A1bc0Csc03i00')
2011-12-07 17:48:19,703 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68cdb0c> about HardwareID('modalias', 'platform:reg-dummy')
2011-12-07 17:48:19,703 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68cdb0c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-12-07 17:48:19,703 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68cdb0c> about HardwareID('modalias', 'acpi:PNP0200:')
2011-12-07 17:48:19,703 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68cdb0c> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-12-07 17:48:19,703 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68cdb0c> about HardwareID('modalias', 'pci:v00008086d00002832sv0000106Bsd000000A1bc0Csc03i00')
2011-12-07 17:48:19,703 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68cdb0c> about HardwareID('modalias', 'platform:applesmc')
2011-12-07 17:48:19,703 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68cdb0c> about HardwareID('modalias', 'usb:v05ACp0229d0009dc00dsc00dp00ic03isc00ip00')
2011-12-07 17:48:19,703 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68cdb0c> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2011-12-07 17:48:19,704 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68cdb0c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2011-12-07 17:48:19,704 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68cdb0c> about HardwareID('modalias', 'input:b0003v05ACp8503e0188-e0,1,kD4,ramlsfw')
2011-12-07 17:48:19,704 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68cdb0c> about HardwareID('modalias', 'acpi:INT0800:')
2011-12-07 17:48:19,764 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-12-07 17:48:19,819 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-12-07 17:48:19,853 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-12-07 17:48:22,463 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-12-07 17:48:26,467 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-12-07 17:48:26,468 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2011-12-07 17:48:26,535 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-12-07 17:48:30,102 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-12-07 17:48:30,121 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-12-07 17:48:30,153 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-12-07 17:48:32,200 DEBUG: Shutting down
2011-12-07 18:01:42,609 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73c564c>
2011-12-07 18:01:44,437 DEBUG: reading modalias file /lib/modules/3.0.0-13-generic-pae/modules.alias
2011-12-07 18:01:44,542 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2011-12-07 18:01:44,542 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-12-07 18:01:44,575 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2011-12-07 18:01:44,576 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2011-12-07 18:01:44,578 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2011-12-07 18:01:44,579 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2011-12-07 18:01:44,595 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2011-12-07 18:01:44,601 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2011-12-07 18:01:44,601 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2011-12-07 18:01:44,617 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2011-12-07 18:01:44,617 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2011-12-07 18:01:44,640 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2011-12-07 18:01:44,640 DEBUG: Firmware for DVB cards not available
2011-12-07 18:01:44,640 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2011-12-07 18:01:44,649 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2011-12-07 18:01:44,652 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2011-12-07 18:01:44,653 DEBUG: nvidia.available: falling back to default
2011-12-07 18:01:44,743 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-12-07 18:01:44,746 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-12-07 18:01:44,749 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2011-12-07 18:01:44,749 DEBUG: nvidia.available: falling back to default
2011-12-07 18:01:44,783 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-12-07 18:01:44,787 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2011-12-07 18:01:44,791 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2011-12-07 18:01:44,792 DEBUG: nvidia.available: falling back to default
2011-12-07 18:01:44,834 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-12-07 18:01:44,835 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 962, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2011-12-07 18:01:44,838 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2011-12-07 18:01:44,842 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2011-12-07 18:01:44,842 DEBUG: nvidia.available: falling back to default
2011-12-07 18:01:44,877 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-12-07 18:01:44,881 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-12-07 18:01:44,884 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2011-12-07 18:01:44,884 DEBUG: nvidia.available: falling back to default
2011-12-07 18:01:44,917 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-12-07 18:01:44,920 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2011-12-07 18:01:44,924 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2011-12-07 18:01:44,924 DEBUG: nvidia.available: falling back to default
2011-12-07 18:01:44,958 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-12-07 18:01:44,959 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2011-12-07 18:01:44,966 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2011-12-07 18:01:44,970 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2011-12-07 18:01:44,970 DEBUG: fglrx.available: falling back to default
2011-12-07 18:01:45,008 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2011-12-07 18:01:45,012 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-12-07 18:01:45,015 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2011-12-07 18:01:45,015 DEBUG: fglrx.available: falling back to default
2011-12-07 18:01:45,056 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2011-12-07 18:01:45,056 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2011-12-07 18:01:45,060 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2011-12-07 18:01:45,061 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2011-12-07 18:01:45,061 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2011-12-07 18:01:45,061 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2011-12-07 18:01:45,079 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2011-12-07 18:01:45,087 DEBUG: Software modem not available
2011-12-07 18:01:45,087 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-12-07 18:01:45,091 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-12-07 18:01:45,111 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2011-12-07 18:01:45,111 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2011-12-07 18:01:45,111 DEBUG: all custom handlers loaded
2011-12-07 18:01:45,111 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73c564c> about HardwareID('modalias', 'pci:v00008086d00002834sv00000000sd00000000bc0Csc03i00')
2011-12-07 18:01:45,421 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73c564c> about HardwareID('modalias', 'input:b0003v05ACp0229e0111-e0,1,4,11,14,k71,72,73,75,77,78,7D,7E,7F,A3,A4,A5,CC,E0,E1,E3,E4,E5,E6,1D0,ram4,l0,1,2,3,4,sfw')
2011-12-07 18:01:45,425 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-07 18:01:45,500 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 18:01:45,500 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73c564c> about HardwareID('modalias', 'pci:v00008086d00002828sv0000106Bsd000000A1bc01sc01i8f')
2011-12-07 18:01:45,504 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73c564c> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2011-12-07 18:01:45,504 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73c564c> about HardwareID('modalias', 'acpi:APP0003:SMC-SMS:')
2011-12-07 18:01:45,504 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73c564c> about HardwareID('modalias', 'pci:v00008086d00002835sv0000106Bsd000000A1bc0Csc03i00')
2011-12-07 18:01:45,507 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73c564c> about HardwareID('modalias', 'input:b0003v05ACp0229e0009-e0,1,3,k110,145,14A,14D,14E,ra0,1,18,mlsfw')
2011-12-07 18:01:45,507 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-07 18:01:45,507 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 18:01:45,507 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-12-07 18:01:45,508 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 18:01:45,508 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-12-07 18:01:45,508 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 18:01:45,508 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73c564c> about HardwareID('modalias', 'platform:eisa')
2011-12-07 18:01:45,508 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73c564c> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2011-12-07 18:01:45,530 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73c564c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2011-12-07 18:01:45,531 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-07 18:01:45,531 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 18:01:45,531 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73c564c> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-12-07 18:01:45,531 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73c564c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-12-07 18:01:45,531 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73c564c> about HardwareID('modalias', 'pci:v00008086d00002836sv0000106Bsd000000A1bc0Csc03i20')
2011-12-07 18:01:45,535 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73c564c> about HardwareID('modalias', 'platform:pcspkr')
2011-12-07 18:01:45,535 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2011-12-07 18:01:45,535 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 18:01:45,535 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2011-12-07 18:01:45,536 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 18:01:45,536 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73c564c> about HardwareID('modalias', 'pci:v00008086d0000283Esv0000106Bsd000000A1bc0Csc05i00')
2011-12-07 18:01:45,539 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801'}
2011-12-07 18:01:45,539 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 18:01:45,539 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73c564c> about HardwareID('modalias', 'pci:v00008086d00002A02sv0000106Bsd000000A1bc03sc00i00')
2011-12-07 18:01:45,542 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'intelfb'}
2011-12-07 18:01:45,542 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intelfb', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 18:01:45,542 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i915'}
2011-12-07 18:01:45,542 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 18:01:45,542 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73c564c> about HardwareID('modalias', 'usb:v05ACp0229d0009dc00dsc00dp00ic03isc01ip02')
2011-12-07 18:01:45,566 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'appletouch'}
2011-12-07 18:01:45,566 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'appletouch', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 18:01:45,566 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-12-07 18:01:45,566 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 18:01:45,567 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2011-12-07 18:01:45,567 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 18:01:45,567 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73c564c> about HardwareID('modalias', 'pci:v00008086d0000284Bsv0000106Bsd000000A1bc04sc03i00')
2011-12-07 18:01:45,570 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-12-07 18:01:45,570 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 18:01:45,570 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73c564c> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-12-07 18:01:45,570 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73c564c> about HardwareID('modalias', 'pci:v00008086d00002A03sv0000106Bsd000000A1bc03sc80i00')
2011-12-07 18:01:45,573 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73c564c> about HardwareID('modalias', 'acpi:APP0001:SMC-SANTAROSA:')
2011-12-07 18:01:45,573 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73c564c> about HardwareID('modalias', 'pci:v000014E4d00004328sv0000106Bsd00000088bc02sc80i00')
2011-12-07 18:01:45,616 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'wl', 'package': 'bcmwl-kernel-source'}
2011-12-07 18:01:45,616 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-12-07 18:01:45,616 DEBUG: found match in handler pool kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2011-12-07 18:01:45,620 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-12-07 18:01:45,620 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-12-07 18:01:45,620 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2011-12-07 18:01:45,620 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ssb'}
2011-12-07 18:01:45,620 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ssb', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 18:01:45,621 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73c564c> about HardwareID('modalias', 'acpi:PNP0000:')
2011-12-07 18:01:45,621 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73c564c> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-12-07 18:01:45,621 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73c564c> about HardwareID('modalias', 'usb:v045Ep0039d0300dc00dsc00dp00ic03isc01ip02')
2011-12-07 18:01:45,680 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-12-07 18:01:45,681 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 18:01:45,681 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2011-12-07 18:01:45,681 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 18:01:45,681 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73c564c> about HardwareID('modalias', 'pci:v00008086d00002830sv0000106Bsd000000A1bc0Csc03i00')
2011-12-07 18:01:45,685 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73c564c> about HardwareID('modalias', 'pci:v00008086d00002850sv0000106Bsd000000A1bc01sc01i8a')
2011-12-07 18:01:45,688 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73c564c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-12-07 18:01:45,688 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-07 18:01:45,688 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 18:01:45,688 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73c564c> about HardwareID('modalias', 'input:b0003v05ACp0229e0111-e0,1,4,kA1,ram4,lsfw')
2011-12-07 18:01:45,688 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-07 18:01:45,688 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 18:01:45,688 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73c564c> about HardwareID('modalias', 'usb:v05ACp0229d0009dc00dsc00dp00ic03isc01ip01')
2011-12-07 18:01:45,689 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-12-07 18:01:45,689 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 18:01:45,689 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2011-12-07 18:01:45,689 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 18:01:45,689 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73c564c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,3,kra0,1,mlsfw')
2011-12-07 18:01:45,690 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-07 18:01:45,690 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 18:01:45,690 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-12-07 18:01:45,690 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 18:01:45,690 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73c564c> about HardwareID('modalias', 'pci:v000011ABd0000436Asv000011ABsd000000BAbc02sc00i00')
2011-12-07 18:01:45,714 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sky2'}
2011-12-07 18:01:45,714 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sky2', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 18:01:45,714 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73c564c> about HardwareID('modalias', 'dmi:bvnAppleInc.:bvrMB31.88Z.008E.B02.0803051832:bd03/05/08:svnAppleInc.:pnMacBook3,1:pvr1.0:rvnAppleInc.:rnMac-F22788C8:rvrPVT:cvnAppleInc.:ct2:cvrMac-F22788C8:')
2011-12-07 18:01:45,729 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73c564c> about HardwareID('modalias', 'usb:v05ACp8503d0188dcEFdsc02dp01ic0Eisc02ip00')
2011-12-07 18:01:45,729 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73c564c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-12-07 18:01:45,729 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73c564c> about HardwareID('modalias', 'usb:v05ACp8503d0188dcEFdsc02dp01ic0Eisc01ip00')
2011-12-07 18:01:45,730 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2011-12-07 18:01:45,730 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 18:01:45,730 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73c564c> about HardwareID('modalias', 'input:b0003v045Ep0039e0110-e0,1,2,4,k110,111,112,113,114,r0,1,8,am4,lsfw')
2011-12-07 18:01:45,730 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-07 18:01:45,730 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 18:01:45,731 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73c564c> about HardwareID('modalias', 'usb:v05ACp8205d1965dcE0dsc01dp01icE0isc01ip01')
2011-12-07 18:01:45,731 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2011-12-07 18:01:45,731 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 18:01:45,731 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73c564c> about HardwareID('modalias', 'usb:v05ACp8205d1965dcE0dsc01dp01icFEisc01ip00')
2011-12-07 18:01:45,732 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2011-12-07 18:01:45,732 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 18:01:45,732 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73c564c> about HardwareID('modalias', 'acpi:MEDIA-NOTIFY:')
2011-12-07 18:01:45,732 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73c564c> about HardwareID('modalias', 'acpi:PNP0100:')
2011-12-07 18:01:45,732 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73c564c> about HardwareID('modalias', 'pci:v00008086d00002815sv0000106Bsd000000A1bc06sc01i00')
2011-12-07 18:01:45,736 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt'}
2011-12-07 18:01:45,736 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 18:01:45,736 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73c564c> about HardwareID('modalias', 'usb:v05ACp8242d0016dc00dsc00dp00ic03isc00ip00')
2011-12-07 18:01:45,736 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-12-07 18:01:45,737 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 18:01:45,737 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73c564c> about HardwareID('modalias', 'pci:v00008086d0000283Asv0000106Bsd000000A1bc0Csc03i20')
2011-12-07 18:01:45,740 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73c564c> about HardwareID('modalias', 'pci:v000011C1d00005811sv000011C1sd00005811bc0Csc00i10')
2011-12-07 18:01:45,741 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci'}
2011-12-07 18:01:45,741 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 18:01:45,741 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73c564c> about HardwareID('modalias', 'pci:v00008086d00002831sv0000106Bsd000000A1bc0Csc03i00')
2011-12-07 18:01:45,744 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73c564c> about HardwareID('modalias', 'platform:reg-dummy')
2011-12-07 18:01:45,745 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73c564c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-12-07 18:01:45,745 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-07 18:01:45,745 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 18:01:45,745 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73c564c> about HardwareID('modalias', 'acpi:PNP0200:')
2011-12-07 18:01:45,745 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73c564c> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-12-07 18:01:45,746 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73c564c> about HardwareID('modalias', 'pci:v00008086d00002832sv0000106Bsd000000A1bc0Csc03i00')
2011-12-07 18:01:45,749 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73c564c> about HardwareID('modalias', 'platform:applesmc')
2011-12-07 18:01:45,749 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73c564c> about HardwareID('modalias', 'usb:v05ACp0229d0009dc00dsc00dp00ic03isc00ip00')
2011-12-07 18:01:45,750 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-12-07 18:01:45,750 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 18:01:45,750 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73c564c> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2011-12-07 18:01:45,753 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73c564c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2011-12-07 18:01:45,753 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-07 18:01:45,753 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 18:01:45,753 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73c564c> about HardwareID('modalias', 'input:b0003v05ACp8503e0188-e0,1,kD4,ramlsfw')
2011-12-07 18:01:45,753 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-12-07 18:01:45,754 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-07 18:01:45,754 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb73c564c> about HardwareID('modalias', 'acpi:INT0800:')
2011-12-07 18:01:45,754 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6abcaec> about HardwareID('modalias', 'pci:v00008086d00002834sv00000000sd00000000bc0Csc03i00')
2011-12-07 18:01:45,754 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6abcaec> about HardwareID('modalias', 'input:b0003v05ACp0229e0111-e0,1,4,11,14,k71,72,73,75,77,78,7D,7E,7F,A3,A4,A5,CC,E0,E1,E3,E4,E5,E6,1D0,ram4,l0,1,2,3,4,sfw')
2011-12-07 18:01:45,754 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6abcaec> about HardwareID('modalias', 'pci:v00008086d00002828sv0000106Bsd000000A1bc01sc01i8f')
2011-12-07 18:01:45,754 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6abcaec> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2011-12-07 18:01:45,754 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6abcaec> about HardwareID('modalias', 'acpi:APP0003:SMC-SMS:')
2011-12-07 18:01:45,754 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6abcaec> about HardwareID('modalias', 'pci:v00008086d00002835sv0000106Bsd000000A1bc0Csc03i00')
2011-12-07 18:01:45,754 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6abcaec> about HardwareID('modalias', 'input:b0003v05ACp0229e0009-e0,1,3,k110,145,14A,14D,14E,ra0,1,18,mlsfw')
2011-12-07 18:01:45,754 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6abcaec> about HardwareID('modalias', 'platform:eisa')
2011-12-07 18:01:45,754 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6abcaec> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2011-12-07 18:01:45,755 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6abcaec> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2011-12-07 18:01:45,755 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6abcaec> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-12-07 18:01:45,755 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6abcaec> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-12-07 18:01:45,755 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6abcaec> about HardwareID('modalias', 'pci:v00008086d00002836sv0000106Bsd000000A1bc0Csc03i20')
2011-12-07 18:01:45,755 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6abcaec> about HardwareID('modalias', 'platform:pcspkr')
2011-12-07 18:01:45,755 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6abcaec> about HardwareID('modalias', 'pci:v00008086d0000283Esv0000106Bsd000000A1bc0Csc05i00')
2011-12-07 18:01:45,755 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6abcaec> about HardwareID('modalias', 'pci:v00008086d00002A02sv0000106Bsd000000A1bc03sc00i00')
2011-12-07 18:01:45,755 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6abcaec> about HardwareID('modalias', 'usb:v05ACp0229d0009dc00dsc00dp00ic03isc01ip02')
2011-12-07 18:01:45,755 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6abcaec> about HardwareID('modalias', 'pci:v00008086d0000284Bsv0000106Bsd000000A1bc04sc03i00')
2011-12-07 18:01:45,755 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6abcaec> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-12-07 18:01:45,755 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6abcaec> about HardwareID('modalias', 'pci:v00008086d00002A03sv0000106Bsd000000A1bc03sc80i00')
2011-12-07 18:01:45,755 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6abcaec> about HardwareID('modalias', 'acpi:APP0001:SMC-SANTAROSA:')
2011-12-07 18:01:45,756 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6abcaec> about HardwareID('modalias', 'pci:v000014E4d00004328sv0000106Bsd00000088bc02sc80i00')
2011-12-07 18:01:45,756 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6abcaec> about HardwareID('modalias', 'acpi:PNP0000:')
2011-12-07 18:01:45,756 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6abcaec> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-12-07 18:01:45,756 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6abcaec> about HardwareID('modalias', 'usb:v045Ep0039d0300dc00dsc00dp00ic03isc01ip02')
2011-12-07 18:01:45,756 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6abcaec> about HardwareID('modalias', 'pci:v00008086d00002830sv0000106Bsd000000A1bc0Csc03i00')
2011-12-07 18:01:45,756 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6abcaec> about HardwareID('modalias', 'pci:v00008086d00002850sv0000106Bsd000000A1bc01sc01i8a')
2011-12-07 18:01:45,756 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6abcaec> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-12-07 18:01:45,756 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6abcaec> about HardwareID('modalias', 'input:b0003v05ACp0229e0111-e0,1,4,kA1,ram4,lsfw')
2011-12-07 18:01:45,756 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6abcaec> about HardwareID('modalias', 'usb:v05ACp0229d0009dc00dsc00dp00ic03isc01ip01')
2011-12-07 18:01:45,756 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6abcaec> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,3,kra0,1,mlsfw')
2011-12-07 18:01:45,756 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6abcaec> about HardwareID('modalias', 'pci:v000011ABd0000436Asv000011ABsd000000BAbc02sc00i00')
2011-12-07 18:01:45,756 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6abcaec> about HardwareID('modalias', 'dmi:bvnAppleInc.:bvrMB31.88Z.008E.B02.0803051832:bd03/05/08:svnAppleInc.:pnMacBook3,1:pvr1.0:rvnAppleInc.:rnMac-F22788C8:rvrPVT:cvnAppleInc.:ct2:cvrMac-F22788C8:')
2011-12-07 18:01:45,757 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6abcaec> about HardwareID('modalias', 'usb:v05ACp8503d0188dcEFdsc02dp01ic0Eisc02ip00')
2011-12-07 18:01:45,757 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6abcaec> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-12-07 18:01:45,757 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6abcaec> about HardwareID('modalias', 'usb:v05ACp8503d0188dcEFdsc02dp01ic0Eisc01ip00')
2011-12-07 18:01:45,757 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6abcaec> about HardwareID('modalias', 'input:b0003v045Ep0039e0110-e0,1,2,4,k110,111,112,113,114,r0,1,8,am4,lsfw')
2011-12-07 18:01:45,757 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6abcaec> about HardwareID('modalias', 'usb:v05ACp8205d1965dcE0dsc01dp01icE0isc01ip01')
2011-12-07 18:01:45,757 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6abcaec> about HardwareID('modalias', 'usb:v05ACp8205d1965dcE0dsc01dp01icFEisc01ip00')
2011-12-07 18:01:45,757 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6abcaec> about HardwareID('modalias', 'acpi:MEDIA-NOTIFY:')
2011-12-07 18:01:45,757 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6abcaec> about HardwareID('modalias', 'acpi:PNP0100:')
2011-12-07 18:01:45,757 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6abcaec> about HardwareID('modalias', 'pci:v00008086d00002815sv0000106Bsd000000A1bc06sc01i00')
2011-12-07 18:01:45,757 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6abcaec> about HardwareID('modalias', 'usb:v05ACp8242d0016dc00dsc00dp00ic03isc00ip00')
2011-12-07 18:01:45,757 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6abcaec> about HardwareID('modalias', 'pci:v00008086d0000283Asv0000106Bsd000000A1bc0Csc03i20')
2011-12-07 18:01:45,757 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6abcaec> about HardwareID('modalias', 'pci:v000011C1d00005811sv000011C1sd00005811bc0Csc00i10')
2011-12-07 18:01:45,758 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6abcaec> about HardwareID('modalias', 'pci:v00008086d00002831sv0000106Bsd000000A1bc0Csc03i00')
2011-12-07 18:01:45,758 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6abcaec> about HardwareID('modalias', 'platform:reg-dummy')
2011-12-07 18:01:45,758 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6abcaec> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-12-07 18:01:45,758 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6abcaec> about HardwareID('modalias', 'acpi:PNP0200:')
2011-12-07 18:01:45,758 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6abcaec> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-12-07 18:01:45,758 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6abcaec> about HardwareID('modalias', 'pci:v00008086d00002832sv0000106Bsd000000A1bc0Csc03i00')
2011-12-07 18:01:45,758 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6abcaec> about HardwareID('modalias', 'platform:applesmc')
2011-12-07 18:01:45,758 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6abcaec> about HardwareID('modalias', 'usb:v05ACp0229d0009dc00dsc00dp00ic03isc00ip00')
2011-12-07 18:01:45,758 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6abcaec> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2011-12-07 18:01:45,758 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6abcaec> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2011-12-07 18:01:45,758 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6abcaec> about HardwareID('modalias', 'input:b0003v05ACp8503e0188-e0,1,kD4,ramlsfw')
2011-12-07 18:01:45,758 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6abcaec> about HardwareID('modalias', 'acpi:INT0800:')
2011-12-07 18:01:45,842 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-12-07 18:01:45,865 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-12-07 18:01:45,911 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-12-07 18:01:48,891 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-12-07 18:01:52,090 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-12-07 18:01:52,091 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2011-12-07 18:01:52,151 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
```


If anyone can make sense of this log file it would be appreciated.  Thanks!

---

### Post by danipo on 2012-01-23
Bump.

Mods, Perhaps the people looking around in the Ubuntu on Mac forums really have no idea how to solve this one.  Any chance we can move the thread to a generic networking section?  I have a feeling this problem is more specific to just the chip and not the macbook itself.  Thanks!

---

### Post by varunendra on 2012-01-25
Hi denipo,

I have never handled or even closely observed a mac related problem, but I guess anyone willing to handle yours would require outputs of some or all of the following:
```
uname -rm
ifconfig -a
iwconfig
lshw -C network
lsmod
rfkill list all
cat /etc/modprobe.d/blacklist.conf | grep -iE 'bcm | b43'
ls /etc/modprobe.d/blacklist*
```Please post the outputs in separate 'code' tags.

---

### Post by coffeecat on 2012-01-25
> **danipo said:**
> Any chance we can move the thread to a generic networking section?  I have a feeling this problem is more specific to just the chip and not the macbook itself.  Thanks!

@danipo, I just happened to notice your post. If you ever need to ask for a thread to be moved, then click on [img]http://ubuntuforums.org/images/buttons/report.gif[/img] in your post to send a request to the staff area. Don't worry that it says "abuse". It's quite OK to use this to communicate with staff about a thread/post which needs any form of staff action.

So... *Thread moved to **Networking & Wireless**.*

---

