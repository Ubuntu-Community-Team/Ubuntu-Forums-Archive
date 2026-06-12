---
title: "Broadcom wireless is not working on Acer Aspire 5720Z"
date: 2013-09-03
forum: Networking &amp; Wireless
---

### Post by protoss96 on 2013-09-03
Hi,

I opened additional drivers app and attempt to activate Broadcom 802.11 Linux STA wireless driver, but i get an error. It tells me that i have to read /var/log/jockey.log, and this is what i get.
```
2013-09-03 16:24:19,763 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x27be5a8>
2013-09-03 16:24:29,182 DEBUG: reading modalias file /lib/modules/3.10.9-031009-generic/modules.alias
2013-09-03 16:24:29,436 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2013-09-03 16:24:29,443 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2013-09-03 16:24:29,557 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2013-09-03 16:24:29,630 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2013-09-03 16:24:29,631 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2013-09-03 16:24:29,676 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2013-09-03 16:24:29,677 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2013-09-03 16:24:29,824 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2013-09-03 16:24:29,853 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2013-09-03 16:24:29,893 DEBUG: Disabling Nvidia driver on intel/hybrid system
2013-09-03 16:24:29,893 DEBUG: NVIDIA accelerated graphics driver not available
2013-09-03 16:24:29,905 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2013-09-03 16:24:29,920 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2013-09-03 16:24:29,922 DEBUG: Disabling Nvidia driver on intel/hybrid system
2013-09-03 16:24:29,923 DEBUG: NVIDIA accelerated graphics driver not available
2013-09-03 16:24:29,934 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2013-09-03 16:24:29,949 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2013-09-03 16:24:29,951 DEBUG: Disabling Nvidia driver on intel/hybrid system
2013-09-03 16:24:29,951 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2013-09-03 16:24:29,960 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2013-09-03 16:24:29,971 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2013-09-03 16:24:29,972 DEBUG: Disabling Nvidia driver on intel/hybrid system
2013-09-03 16:24:29,973 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2013-09-03 16:24:29,983 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2013-09-03 16:24:29,998 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2013-09-03 16:24:30,000 DEBUG: Disabling Nvidia driver on intel/hybrid system
2013-09-03 16:24:30,000 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2013-09-03 16:24:30,015 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2013-09-03 16:24:30,025 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2013-09-03 16:24:30,026 DEBUG: Disabling Nvidia driver on intel/hybrid system
2013-09-03 16:24:30,027 DEBUG: NVIDIA accelerated graphics driver not available
2013-09-03 16:24:30,035 WARNING: modinfo for module nvidia_experimental_310 failed: ERROR: modinfo: could not find module nvidia_experimental_310

2013-09-03 16:24:30,077 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverExperimental310 from name NvidiaDriverExperimental310
2013-09-03 16:24:30,078 DEBUG: Disabling Nvidia driver on intel/hybrid system
2013-09-03 16:24:30,079 DEBUG: NVIDIA accelerated graphics driver (**experimental** beta) not available
2013-09-03 16:24:30,089 WARNING: modinfo for module nvidia_experimental_304 failed: ERROR: modinfo: could not find module nvidia_experimental_304

2013-09-03 16:24:30,155 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverExperimental304 from name NvidiaDriverExperimental304
2013-09-03 16:24:30,157 DEBUG: Disabling Nvidia driver on intel/hybrid system
2013-09-03 16:24:30,158 DEBUG: NVIDIA accelerated graphics driver (**experimental** beta) not available
2013-09-03 16:24:30,158 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2013-09-03 16:24:30,188 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2013-09-03 16:24:30,189 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2013-09-03 16:24:30,189 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2013-09-03 16:24:30,189 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2013-09-03 16:24:30,226 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2013-09-03 16:24:30,541 DEBUG: Software modem not available
2013-09-03 16:24:30,542 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2013-09-03 16:24:30,568 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2013-09-03 16:24:30,615 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2013-09-03 16:24:30,615 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2013-09-03 16:24:30,616 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2013-09-03 16:24:30,628 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2013-09-03 16:24:30,638 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2013-09-03 16:24:31,248 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2013-09-03 16:24:31,248 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2013-09-03 16:24:31,414 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2013-09-03 16:24:31,415 DEBUG: Firmware for DVB cards not available
2013-09-03 16:24:31,415 DEBUG: loading custom handler /usr/share/jockey/handlers/cdv.py
2013-09-03 16:24:31,426 WARNING: modinfo for module cedarview_gfx failed: ERROR: modinfo: could not find module cedarview_gfx

2013-09-03 16:24:31,427 DEBUG: Instantiated Handler subclass __builtin__.CdvDriver from name CdvDriver
2013-09-03 16:24:31,427 DEBUG: cdv.available: falling back to default
2013-09-03 16:24:31,697 DEBUG: Intel Cedarview graphics driver availability undetermined, adding to pool
2013-09-03 16:24:31,697 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2013-09-03 16:24:31,723 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2013-09-03 16:24:31,733 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2013-09-03 16:24:31,733 DEBUG: fglrx.available: falling back to default
2013-09-03 16:24:32,018 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2013-09-03 16:24:32,027 WARNING: modinfo for module fglrx_experimental_9 failed: ERROR: modinfo: could not find module fglrx_experimental_9

2013-09-03 16:24:32,074 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverExperimental9 from name FglrxDriverExperimental9
2013-09-03 16:24:32,074 DEBUG: fglrx.available: falling back to default
2013-09-03 16:24:32,336 DEBUG: ATI/AMD proprietary FGLRX graphics driver (**experimental** beta) availability undetermined, adding to pool
2013-09-03 16:24:32,347 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2013-09-03 16:24:32,362 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2013-09-03 16:24:32,363 DEBUG: fglrx.available: falling back to default
2013-09-03 16:24:32,664 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2013-09-03 16:24:32,665 DEBUG: all custom handlers loaded
2013-09-03 16:24:32,665 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27be5a8> about HardwareID('modalias', 'pci:v00008086d00002A02sv00001025sd0000011Ebc03sc00i00')
2013-09-03 16:24:33,258 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'intelfb'}
2013-09-03 16:24:33,500 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intelfb', 'jockey_handler': 'KernelModuleHandler'}
2013-09-03 16:24:33,500 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i915'}
2013-09-03 16:24:33,501 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2013-09-03 16:24:33,501 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27be5a8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,1,4,14,k71,72,73,77,80,8E,A1,A4,A7,A8,AE,CF,D0,D2,D4,E0,E1,E2,160,164,166,16D,16E,170,171,172,174,175,179,181,182,183,185,188,189,18E,18F,190,191,192,193,197,19C,1A9,200,201,202,203,204,205,206,207,208,209,20A,20B,ram4,lsfw')
2013-09-03 16:24:33,509 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-09-03 16:24:33,509 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-09-03 16:24:33,509 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-09-03 16:24:33,510 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-09-03 16:24:33,510 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27be5a8> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2013-09-03 16:24:33,510 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27be5a8> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2013-09-03 16:24:33,510 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-09-03 16:24:33,510 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-09-03 16:24:33,511 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-09-03 16:24:33,511 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-09-03 16:24:33,511 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27be5a8> about HardwareID('modalias', 'acpi:PNP0B00:')
2013-09-03 16:24:33,511 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27be5a8> about HardwareID('modalias', 'pci:v00008086d00002831sv00001025sd0000011Ebc0Csc03i00')
2013-09-03 16:24:33,518 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27be5a8> about HardwareID('modalias', 'pci:v000014E4d00001693sv00001025sd0000011Ebc02sc00i00')
2013-09-03 16:24:33,594 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'tg3'}
2013-09-03 16:24:33,595 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'tg3', 'jockey_handler': 'KernelModuleHandler'}
2013-09-03 16:24:33,595 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27be5a8> about HardwareID('modalias', 'platform:microcode')
2013-09-03 16:24:33,596 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27be5a8> about HardwareID('modalias', 'usb:v1D6Bp0001d0310dc09dsc00dp00ic09isc00ip00in00')
2013-09-03 16:24:33,628 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27be5a8> about HardwareID('modalias', 'usb:v1BCFp0005d0013dc00dsc00dp00ic03isc01ip02in00')
2013-09-03 16:24:33,628 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2013-09-03 16:24:33,629 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2013-09-03 16:24:33,629 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-09-03 16:24:33,629 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-09-03 16:24:33,629 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27be5a8> about HardwareID('modalias', 'wmi:F28A9357-CF4B-4A1A-8893-BB1F58EEA1AF')
2013-09-03 16:24:33,629 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27be5a8> about HardwareID('modalias', 'input:b0003v1BCFp0005e0110-e0,1,2,4,k110,111,112,113,114,r0,1,6,8,am4,lsfw')
2013-09-03 16:24:33,630 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-09-03 16:24:33,630 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-09-03 16:24:33,630 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-09-03 16:24:33,630 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-09-03 16:24:33,630 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27be5a8> about HardwareID('modalias', 'platform:coretemp')
2013-09-03 16:24:33,632 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27be5a8> about HardwareID('modalias', 'acpi:PNP0000:')
2013-09-03 16:24:33,632 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27be5a8> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-09-03 16:24:33,632 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27be5a8> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2013-09-03 16:24:33,632 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-09-03 16:24:33,632 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-09-03 16:24:33,633 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-09-03 16:24:33,633 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-09-03 16:24:33,633 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27be5a8> about HardwareID('modalias', 'platform:acer-wmi')
2013-09-03 16:24:33,634 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27be5a8> about HardwareID('modalias', 'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2013-09-03 16:24:33,634 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-09-03 16:24:33,634 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-09-03 16:24:33,635 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-09-03 16:24:33,635 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-09-03 16:24:33,635 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27be5a8> about HardwareID('modalias', 'platform:iTCO_wdt')
2013-09-03 16:24:33,636 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt'}
2013-09-03 16:24:33,636 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2013-09-03 16:24:33,636 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27be5a8> about HardwareID('modalias', 'wmi:6AF4F258-B401-42FD-BE91-3D4AC2D7C0D3')
2013-09-03 16:24:33,637 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'acer_wmi'}
2013-09-03 16:24:33,637 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'acer_wmi', 'jockey_handler': 'KernelModuleHandler'}
2013-09-03 16:24:33,637 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27be5a8> about HardwareID('modalias', 'pci:v00008086d0000284Bsv00001025sd0000011Ebc04sc03i00')
2013-09-03 16:24:33,643 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-09-03 16:24:33,643 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-09-03 16:24:33,644 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-09-03 16:24:33,644 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-09-03 16:24:33,644 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27be5a8> about HardwareID('modalias', 'pci:v00001180d00000822sv00001025sd0000011Ebc08sc05i00')
2013-09-03 16:24:33,651 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci'}
2013-09-03 16:24:33,651 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2013-09-03 16:24:33,651 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci'}
2013-09-03 16:24:33,652 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2013-09-03 16:24:33,652 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27be5a8> about HardwareID('modalias', 'wmi:CFF94C79-6C77-4AF7-AC56-7DD0CE01C997')
2013-09-03 16:24:33,652 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27be5a8> about HardwareID('modalias', 'wmi:AAE04F7B-B3C5-4865-95D6-9FAC7FF3E92B')
2013-09-03 16:24:33,652 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27be5a8> about HardwareID('modalias', 'acpi:PNP0C02:')
2013-09-03 16:24:33,652 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27be5a8> about HardwareID('modalias', 'acpi:PNP0A08:PNP0A03:')
2013-09-03 16:24:33,652 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27be5a8> about HardwareID('modalias', 'wmi:95764E09-FB56-4E83-B31A-37761F60994A')
2013-09-03 16:24:33,653 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27be5a8> about HardwareID('modalias', 'pci:v00008086d00002835sv00001025sd0000011Ebc0Csc03i00')
2013-09-03 16:24:33,659 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27be5a8> about HardwareID('modalias', 'pci:v00008086d00002830sv00001025sd0000011Ebc0Csc03i00')
2013-09-03 16:24:33,665 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27be5a8> about HardwareID('modalias', 'acpi:PNP0303:')
2013-09-03 16:24:33,665 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27be5a8> about HardwareID('modalias', 'pci:v00008086d0000283Esv00001025sd0000011Ebc0Csc05i00')
2013-09-03 16:24:33,671 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801'}
2013-09-03 16:24:33,671 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2013-09-03 16:24:33,672 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27be5a8> about HardwareID('modalias', 'pci:v00008086d00002815sv00001025sd0000011Ebc06sc01i00')
2013-09-03 16:24:33,678 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'lpc_ich'}
2013-09-03 16:24:33,678 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'lpc_ich', 'jockey_handler': 'KernelModuleHandler'}
2013-09-03 16:24:33,678 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27be5a8> about HardwareID('modalias', 'x86cpu:vendor:0000:family:0006:model:000F:feature:,0000,0001,0002,0003,0004,0005,0006,0007,0008,0009,000B,000C,000D,000E,000F,0010,0011,0013,0015,0016,0017,0018,0019,001A,001B,001C,001D,001F,002B,0034,003D,0068,006B,006C,006D,006F,0070,0072,0074,007C,0080,0082,0083,0084,0087,0088,0089,008D,008E,008F,00C0,00E7')
2013-09-03 16:24:33,691 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'microcode'}
2013-09-03 16:24:33,692 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'microcode', 'jockey_handler': 'KernelModuleHandler'}
2013-09-03 16:24:33,692 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'coretemp'}
2013-09-03 16:24:33,692 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'coretemp', 'jockey_handler': 'KernelModuleHandler'}
2013-09-03 16:24:33,692 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27be5a8> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8D,8E,8F,94,95,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D9,E0,E1,E2,E3,EC,ED,EE,1A9,1B2,1B3,1D0,ram4,l0,1,2,sfw')
2013-09-03 16:24:33,693 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-09-03 16:24:33,693 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-09-03 16:24:33,693 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-09-03 16:24:33,693 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-09-03 16:24:33,693 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27be5a8> about HardwareID('modalias', 'wmi:A7C9A0B7-4C9D-4C72-83BB-53A3459171DF')
2013-09-03 16:24:33,694 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27be5a8> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2013-09-03 16:24:33,694 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27be5a8> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,3,kra0,1,2,mlsfw')
2013-09-03 16:24:33,694 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-09-03 16:24:33,694 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-09-03 16:24:33,694 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2013-09-03 16:24:33,695 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2013-09-03 16:24:33,695 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27be5a8> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2013-09-03 16:24:33,707 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2013-09-03 16:24:33,708 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2013-09-03 16:24:33,708 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2013-09-03 16:24:33,708 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2013-09-03 16:24:33,708 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27be5a8> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2013-09-03 16:24:33,708 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-09-03 16:24:33,709 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-09-03 16:24:33,709 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27be5a8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2013-09-03 16:24:33,709 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-09-03 16:24:33,709 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-09-03 16:24:33,709 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27be5a8> about HardwareID('modalias', 'acpi:PNP0F13:')
2013-09-03 16:24:33,710 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27be5a8> about HardwareID('modalias', 'pci:v00001180d00000852sv00001025sd0000011Ebc08sc80i00')
2013-09-03 16:24:33,710 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r852'}
2013-09-03 16:24:33,710 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r852', 'jockey_handler': 'KernelModuleHandler'}
2013-09-03 16:24:33,710 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27be5a8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2013-09-03 16:24:33,711 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-09-03 16:24:33,711 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-09-03 16:24:33,711 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27be5a8> about HardwareID('modalias', 'wmi:CC1A61AC-4256-41A3-B9E0-05A445ADE2F5')
2013-09-03 16:24:33,711 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27be5a8> about HardwareID('modalias', 'wmi:F6CB5C3C-9CAE-4EBD-B577-931EA32A2CC0')
2013-09-03 16:24:33,711 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mxm_wmi'}
2013-09-03 16:24:33,712 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mxm_wmi', 'jockey_handler': 'KernelModuleHandler'}
2013-09-03 16:24:33,712 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27be5a8> about HardwareID('modalias', 'dmi:bvnAcer:bvrV1.45:bd11/10/2008:svnAcer:pnAspire5720Z:pvrV1.45:rvnAcer:rnNettiling:rvrV1.45:cvnAcer:ct1:cvrV1.45:')
2013-09-03 16:24:33,732 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27be5a8> about HardwareID('modalias', 'acpi:PNP0C04:')
2013-09-03 16:24:33,733 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27be5a8> about HardwareID('modalias', 'pci:v00008086d00002850sv00001025sd0000011Ebc01sc01i8a')
2013-09-03 16:24:33,739 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pata_acpi'}
2013-09-03 16:24:33,739 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_acpi', 'jockey_handler': 'KernelModuleHandler'}
2013-09-03 16:24:33,739 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27be5a8> about HardwareID('modalias', 'pci:v000014E4d00004311sv00001468sd00000422bc02sc80i00')
2013-09-03 16:24:33,740 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ssb'}
2013-09-03 16:24:33,740 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ssb', 'jockey_handler': 'KernelModuleHandler'}
2013-09-03 16:24:33,741 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'wl', 'package': 'bcmwl-kernel-source'}
2013-09-03 16:24:33,741 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-09-03 16:24:33,741 DEBUG: found match in handler pool kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2013-09-03 16:24:33,750 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2013-09-03 16:24:33,751 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-09-03 16:24:33,751 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2013-09-03 16:24:33,751 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27be5a8> about HardwareID('modalias', 'usb:v1D6Bp0002d0310dc09dsc00dp00ic09isc00ip00in00')
2013-09-03 16:24:33,752 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27be5a8> about HardwareID('modalias', 'wmi:79772EC5-04B1-4BFD-843C-61E7F77B6CC9')
2013-09-03 16:24:33,752 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27be5a8> about HardwareID('modalias', 'pci:v00001180d00000832sv00001025sd0000011Ebc0Csc00i10')
2013-09-03 16:24:33,753 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci'}
2013-09-03 16:24:33,753 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2013-09-03 16:24:33,753 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27be5a8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,1,2,4,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8C,8E,96,98,9E,9F,A1,A3,A4,A5,A6,AD,B0,B1,B2,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,110,111,r0,1,am4,lsfw')
2013-09-03 16:24:33,753 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-09-03 16:24:33,754 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-09-03 16:24:33,754 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-09-03 16:24:33,754 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-09-03 16:24:33,754 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27be5a8> about HardwareID('modalias', 'acpi:INT0800:')
2013-09-03 16:24:33,754 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27be5a8> about HardwareID('modalias', 'pci:v00001180d00000592sv00001025sd0000011Ebc08sc80i00')
2013-09-03 16:24:33,755 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r592'}
2013-09-03 16:24:33,755 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r592', 'jockey_handler': 'KernelModuleHandler'}
2013-09-03 16:24:33,755 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27be5a8> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-09-03 16:24:33,755 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-09-03 16:24:33,756 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-09-03 16:24:33,756 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-09-03 16:24:33,756 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-09-03 16:24:33,756 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27be5a8> about HardwareID('modalias', 'acpi:PNP0C0F:')
2013-09-03 16:24:33,756 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27be5a8> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-09-03 16:24:33,758 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27be5a8> about HardwareID('modalias', 'acpi:PNP0100:')
2013-09-03 16:24:33,758 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27be5a8> about HardwareID('modalias', 'pci:v00008086d00002834sv00001025sd0000011Ebc0Csc03i00')
2013-09-03 16:24:33,765 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27be5a8> about HardwareID('modalias', 'hid:b0003g0001v00001BCFp00000005')
2013-09-03 16:24:33,844 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'hid_generic'}
2013-09-03 16:24:33,844 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'hid_generic', 'jockey_handler': 'KernelModuleHandler'}
2013-09-03 16:24:33,845 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27be5a8> about HardwareID('modalias', 'wmi:36916B91-1A64-4583-84D0-53830FB9108D')
2013-09-03 16:24:33,845 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27be5a8> about HardwareID('modalias', 'platform:pcspkr')
2013-09-03 16:24:33,846 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2013-09-03 16:24:33,846 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2013-09-03 16:24:33,847 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2013-09-03 16:24:33,847 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2013-09-03 16:24:33,847 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27be5a8> about HardwareID('modalias', 'pci:v00008086d00002829sv00001025sd0000011Ebc01sc06i01')
2013-09-03 16:24:33,854 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2013-09-03 16:24:33,854 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2013-09-03 16:24:33,854 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2013-09-03 16:24:33,854 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2013-09-03 16:24:33,854 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27be5a8> about HardwareID('modalias', 'acpi:PNP0200:')
2013-09-03 16:24:33,855 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27be5a8> about HardwareID('modalias', 'pci:v00008086d00002448sv00001025sd0000011Ebc06sc04i01')
2013-09-03 16:24:33,861 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27be5a8> about HardwareID('modalias', 'pci:v00008086d00002832sv00001025sd0000011Ebc0Csc03i00')
2013-09-03 16:24:33,867 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27be5a8> about HardwareID('modalias', 'wmi:653A064F-A23A-485F-B3D9-13F6532A0182')
2013-09-03 16:24:33,867 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27be5a8> about HardwareID('modalias', 'acpi:ENE0100:')
2013-09-03 16:24:33,868 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27be5a8> about HardwareID('modalias', 'input:b0011v0002p0008e0200-e0,1,3,k100,101,102,103,110,111,145,14A,ra0,1,18,mlsfw')
2013-09-03 16:24:33,868 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-09-03 16:24:33,868 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-09-03 16:24:33,868 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2013-09-03 16:24:33,868 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2013-09-03 16:24:33,869 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2013-09-03 16:24:33,869 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2013-09-03 16:24:33,869 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-09-03 16:24:33,869 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-09-03 16:24:33,869 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27be5a8> about HardwareID('modalias', 'acpi:PNP0103:')
2013-09-03 16:24:33,870 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27be5a8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2013-09-03 16:24:33,870 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-09-03 16:24:33,870 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-09-03 16:24:33,870 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27be5a8> about HardwareID('modalias', 'pci:v00008086d00002A03sv00001025sd0000011Ebc03sc80i00')
2013-09-03 16:24:33,876 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27be5a8> about HardwareID('modalias', 'wmi:DB85B1A7-069A-4ABB-A2B5-D186A21B80F1')
2013-09-03 16:24:33,876 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x27be5a8> about HardwareID('modalias', 'wmi:E78C4453-0227-4861-9EDE-F5600B4A3D39')
2013-09-03 16:24:33,877 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2c8b6c8> about HardwareID('modalias', 'pci:v00008086d00002A02sv00001025sd0000011Ebc03sc00i00')
2013-09-03 16:24:33,877 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2c8b6c8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,1,4,14,k71,72,73,77,80,8E,A1,A4,A7,A8,AE,CF,D0,D2,D4,E0,E1,E2,160,164,166,16D,16E,170,171,172,174,175,179,181,182,183,185,188,189,18E,18F,190,191,192,193,197,19C,1A9,200,201,202,203,204,205,206,207,208,209,20A,20B,ram4,lsfw')
2013-09-03 16:24:33,877 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2c8b6c8> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2013-09-03 16:24:33,877 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2c8b6c8> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2013-09-03 16:24:33,877 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2c8b6c8> about HardwareID('modalias', 'acpi:PNP0B00:')
2013-09-03 16:24:33,878 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2c8b6c8> about HardwareID('modalias', 'pci:v00008086d00002831sv00001025sd0000011Ebc0Csc03i00')
2013-09-03 16:24:33,878 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2c8b6c8> about HardwareID('modalias', 'pci:v000014E4d00001693sv00001025sd0000011Ebc02sc00i00')
2013-09-03 16:24:33,878 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2c8b6c8> about HardwareID('modalias', 'platform:microcode')
2013-09-03 16:24:33,878 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2c8b6c8> about HardwareID('modalias', 'usb:v1D6Bp0001d0310dc09dsc00dp00ic09isc00ip00in00')
2013-09-03 16:24:33,878 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2c8b6c8> about HardwareID('modalias', 'usb:v1BCFp0005d0013dc00dsc00dp00ic03isc01ip02in00')
2013-09-03 16:24:33,878 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2c8b6c8> about HardwareID('modalias', 'wmi:F28A9357-CF4B-4A1A-8893-BB1F58EEA1AF')
2013-09-03 16:24:33,878 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2c8b6c8> about HardwareID('modalias', 'input:b0003v1BCFp0005e0110-e0,1,2,4,k110,111,112,113,114,r0,1,6,8,am4,lsfw')
2013-09-03 16:24:33,879 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2c8b6c8> about HardwareID('modalias', 'platform:coretemp')
2013-09-03 16:24:33,879 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2c8b6c8> about HardwareID('modalias', 'acpi:PNP0000:')
2013-09-03 16:24:33,879 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2c8b6c8> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-09-03 16:24:33,879 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2c8b6c8> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2013-09-03 16:24:33,879 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2c8b6c8> about HardwareID('modalias', 'platform:acer-wmi')
2013-09-03 16:24:33,879 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2c8b6c8> about HardwareID('modalias', 'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2013-09-03 16:24:33,879 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2c8b6c8> about HardwareID('modalias', 'platform:iTCO_wdt')
2013-09-03 16:24:33,880 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2c8b6c8> about HardwareID('modalias', 'wmi:6AF4F258-B401-42FD-BE91-3D4AC2D7C0D3')
2013-09-03 16:24:33,880 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2c8b6c8> about HardwareID('modalias', 'pci:v00008086d0000284Bsv00001025sd0000011Ebc04sc03i00')
2013-09-03 16:24:33,880 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2c8b6c8> about HardwareID('modalias', 'pci:v00001180d00000822sv00001025sd0000011Ebc08sc05i00')
2013-09-03 16:24:33,880 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2c8b6c8> about HardwareID('modalias', 'wmi:CFF94C79-6C77-4AF7-AC56-7DD0CE01C997')
2013-09-03 16:24:33,880 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2c8b6c8> about HardwareID('modalias', 'wmi:AAE04F7B-B3C5-4865-95D6-9FAC7FF3E92B')
2013-09-03 16:24:33,880 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2c8b6c8> about HardwareID('modalias', 'acpi:PNP0C02:')
2013-09-03 16:24:33,880 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2c8b6c8> about HardwareID('modalias', 'acpi:PNP0A08:PNP0A03:')
2013-09-03 16:24:33,881 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2c8b6c8> about HardwareID('modalias', 'wmi:95764E09-FB56-4E83-B31A-37761F60994A')
2013-09-03 16:24:33,881 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2c8b6c8> about HardwareID('modalias', 'pci:v00008086d00002835sv00001025sd0000011Ebc0Csc03i00')
2013-09-03 16:24:33,881 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2c8b6c8> about HardwareID('modalias', 'pci:v00008086d00002830sv00001025sd0000011Ebc0Csc03i00')
2013-09-03 16:24:33,881 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2c8b6c8> about HardwareID('modalias', 'acpi:PNP0303:')
2013-09-03 16:24:33,881 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2c8b6c8> about HardwareID('modalias', 'pci:v00008086d0000283Esv00001025sd0000011Ebc0Csc05i00')
2013-09-03 16:24:33,881 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2c8b6c8> about HardwareID('modalias', 'pci:v00008086d00002815sv00001025sd0000011Ebc06sc01i00')
2013-09-03 16:24:33,881 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2c8b6c8> about HardwareID('modalias', 'x86cpu:vendor:0000:family:0006:model:000F:feature:,0000,0001,0002,0003,0004,0005,0006,0007,0008,0009,000B,000C,000D,000E,000F,0010,0011,0013,0015,0016,0017,0018,0019,001A,001B,001C,001D,001F,002B,0034,003D,0068,006B,006C,006D,006F,0070,0072,0074,007C,0080,0082,0083,0084,0087,0088,0089,008D,008E,008F,00C0,00E7')
2013-09-03 16:24:33,882 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2c8b6c8> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8D,8E,8F,94,95,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D9,E0,E1,E2,E3,EC,ED,EE,1A9,1B2,1B3,1D0,ram4,l0,1,2,sfw')
2013-09-03 16:24:33,882 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2c8b6c8> about HardwareID('modalias', 'wmi:A7C9A0B7-4C9D-4C72-83BB-53A3459171DF')
2013-09-03 16:24:33,882 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2c8b6c8> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2013-09-03 16:24:33,882 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2c8b6c8> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,3,kra0,1,2,mlsfw')
2013-09-03 16:24:33,882 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2c8b6c8> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2013-09-03 16:24:33,882 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2c8b6c8> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2013-09-03 16:24:33,882 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2c8b6c8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2013-09-03 16:24:33,883 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2c8b6c8> about HardwareID('modalias', 'acpi:PNP0F13:')
2013-09-03 16:24:33,883 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2c8b6c8> about HardwareID('modalias', 'pci:v00001180d00000852sv00001025sd0000011Ebc08sc80i00')
2013-09-03 16:24:33,883 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2c8b6c8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2013-09-03 16:24:33,883 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2c8b6c8> about HardwareID('modalias', 'wmi:CC1A61AC-4256-41A3-B9E0-05A445ADE2F5')
2013-09-03 16:24:33,883 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2c8b6c8> about HardwareID('modalias', 'wmi:F6CB5C3C-9CAE-4EBD-B577-931EA32A2CC0')
2013-09-03 16:24:33,883 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2c8b6c8> about HardwareID('modalias', 'dmi:bvnAcer:bvrV1.45:bd11/10/2008:svnAcer:pnAspire5720Z:pvrV1.45:rvnAcer:rnNettiling:rvrV1.45:cvnAcer:ct1:cvrV1.45:')
2013-09-03 16:24:33,883 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2c8b6c8> about HardwareID('modalias', 'acpi:PNP0C04:')
2013-09-03 16:24:33,884 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2c8b6c8> about HardwareID('modalias', 'pci:v00008086d00002850sv00001025sd0000011Ebc01sc01i8a')
2013-09-03 16:24:33,884 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2c8b6c8> about HardwareID('modalias', 'pci:v000014E4d00004311sv00001468sd00000422bc02sc80i00')
2013-09-03 16:24:33,884 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2c8b6c8> about HardwareID('modalias', 'usb:v1D6Bp0002d0310dc09dsc00dp00ic09isc00ip00in00')
2013-09-03 16:24:33,884 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2c8b6c8> about HardwareID('modalias', 'wmi:79772EC5-04B1-4BFD-843C-61E7F77B6CC9')
2013-09-03 16:24:33,884 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2c8b6c8> about HardwareID('modalias', 'pci:v00001180d00000832sv00001025sd0000011Ebc0Csc00i10')
2013-09-03 16:24:33,884 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2c8b6c8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,1,2,4,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8C,8E,96,98,9E,9F,A1,A3,A4,A5,A6,AD,B0,B1,B2,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,110,111,r0,1,am4,lsfw')
2013-09-03 16:24:33,884 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2c8b6c8> about HardwareID('modalias', 'acpi:INT0800:')
2013-09-03 16:24:33,885 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2c8b6c8> about HardwareID('modalias', 'pci:v00001180d00000592sv00001025sd0000011Ebc08sc80i00')
2013-09-03 16:24:33,885 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2c8b6c8> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-09-03 16:24:33,885 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2c8b6c8> about HardwareID('modalias', 'acpi:PNP0C0F:')
2013-09-03 16:24:33,885 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2c8b6c8> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-09-03 16:24:33,885 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2c8b6c8> about HardwareID('modalias', 'acpi:PNP0100:')
2013-09-03 16:24:33,885 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2c8b6c8> about HardwareID('modalias', 'pci:v00008086d00002834sv00001025sd0000011Ebc0Csc03i00')
2013-09-03 16:24:33,886 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2c8b6c8> about HardwareID('modalias', 'hid:b0003g0001v00001BCFp00000005')
2013-09-03 16:24:33,886 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2c8b6c8> about HardwareID('modalias', 'wmi:36916B91-1A64-4583-84D0-53830FB9108D')
2013-09-03 16:24:33,886 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2c8b6c8> about HardwareID('modalias', 'platform:pcspkr')
2013-09-03 16:24:33,886 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2c8b6c8> about HardwareID('modalias', 'pci:v00008086d00002829sv00001025sd0000011Ebc01sc06i01')
2013-09-03 16:24:33,886 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2c8b6c8> about HardwareID('modalias', 'acpi:PNP0200:')
2013-09-03 16:24:33,886 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2c8b6c8> about HardwareID('modalias', 'pci:v00008086d00002448sv00001025sd0000011Ebc06sc04i01')
2013-09-03 16:24:33,886 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2c8b6c8> about HardwareID('modalias', 'pci:v00008086d00002832sv00001025sd0000011Ebc0Csc03i00')
2013-09-03 16:24:33,886 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2c8b6c8> about HardwareID('modalias', 'wmi:653A064F-A23A-485F-B3D9-13F6532A0182')
2013-09-03 16:24:33,887 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2c8b6c8> about HardwareID('modalias', 'acpi:ENE0100:')
2013-09-03 16:24:33,887 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2c8b6c8> about HardwareID('modalias', 'input:b0011v0002p0008e0200-e0,1,3,k100,101,102,103,110,111,145,14A,ra0,1,18,mlsfw')
2013-09-03 16:24:33,887 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2c8b6c8> about HardwareID('modalias', 'acpi:PNP0103:')
2013-09-03 16:24:33,887 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2c8b6c8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2013-09-03 16:24:33,887 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2c8b6c8> about HardwareID('modalias', 'pci:v00008086d00002A03sv00001025sd0000011Ebc03sc80i00')
2013-09-03 16:24:33,887 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2c8b6c8> about HardwareID('modalias', 'wmi:DB85B1A7-069A-4ABB-A2B5-D186A21B80F1')
2013-09-03 16:24:33,888 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2c8b6c8> about HardwareID('modalias', 'wmi:E78C4453-0227-4861-9EDE-F5600B4A3D39')
2013-09-03 16:24:33,945 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-09-03 16:24:34,079 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-09-03 16:24:34,121 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-09-03 16:24:51,393 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-09-03 16:24:57,204 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2013-09-03 16:24:57,205 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2013-09-03 16:24:57,393 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-09-03 16:25:40,064 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-09-03 16:25:40,098 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-09-03 16:25:40,136 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-09-03 16:25:41,499 DEBUG: Shutting down
```

I am currently using Linux Kernel 3.10.9-031009-generic, Ubuntu 12.04 LTS 64-Bit, everything is working fine but only wireless tricks me. Thanks for every helpful reply.

---

### Post by chili555 on 2013-09-03
May we please verify your exact wireless device?```
lspci -nn | grep 0280
```

---

### Post by protoss96 on 2013-09-03
This is the output:

06:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)

---

### Post by chili555 on 2013-09-03
The Broadcom STA driver is incorrect for your device 14e4:4311. With a temporary ethernet connection, please do:```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
sudo modprobe -r b43 && sudo modprobe b43
```Your wireless should now be working.

---

### Post by protoss96 on 2013-09-04
Thank you so much my friend, this is working i have searched for help about 2 weeks on net, and this is solution, many thanks to you!

---

### Post by chili555 on 2013-09-04
Very happy to help. I'm glad it's working. Please mark the thread solved: [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

For the benefit of the searchers, the PCI ID is everything, in this case: Broadcom Corporation BCM4311 802.11b/g WLAN [[COLOR="#FF0000"]14e4:4311[/COLOR]]. If this is your device, the above is your solution. If not, find out your ID and keep searching. Most of all, do not implement a solution blindly. Look for your device ID, your Ubuntu version; 12.04, 13.04, etc., and the magic word SOLVED.

---

