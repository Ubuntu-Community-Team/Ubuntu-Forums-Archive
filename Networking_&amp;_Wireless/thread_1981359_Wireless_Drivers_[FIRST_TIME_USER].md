---
title: "Wireless Drivers [FIRST TIME USER]"
date: 2012-05-16
forum: Networking &amp; Wireless
---

### Post by Tyluur on 2012-05-16
This is my first time using Ubuntu, and I'm wanting to use Internet on it of course, but I'm getting errors. This is my jockey.log after trying to activate the Broadcom driver:

```
2012-05-16 17:57:49,265 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b31200>
2012-05-16 17:57:52,656 DEBUG: reading modalias file /lib/modules/3.2.0-23-generic/modules.alias
2012-05-16 17:57:52,805 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-05-16 17:57:52,805 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-05-16 17:57:52,902 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-05-16 17:57:52,973 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-05-16 17:57:52,985 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-05-16 17:57:52,988 DEBUG: nvidia.available: falling back to default
2012-05-16 17:57:53,102 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-05-16 17:57:53,102 DEBUG: NVIDIA accelerated graphics driver not available
2012-05-16 17:57:53,111 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-05-16 17:57:53,122 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-05-16 17:57:53,124 DEBUG: nvidia.available: falling back to default
2012-05-16 17:57:53,196 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-05-16 17:57:53,205 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-05-16 17:57:53,216 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2012-05-16 17:57:53,218 DEBUG: nvidia.available: falling back to default
2012-05-16 17:57:53,290 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-05-16 17:57:53,299 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2012-05-16 17:57:53,310 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2012-05-16 17:57:53,311 DEBUG: nvidia.available: falling back to default
2012-05-16 17:57:53,348 DEBUG: XorgDriverHandler(nvidia_173_updates, nvidia-173-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-05-16 17:57:53,348 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-05-16 17:57:53,445 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-05-16 17:57:53,456 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-05-16 17:57:53,458 DEBUG: nvidia.available: falling back to default
2012-05-16 17:57:53,494 DEBUG: XorgDriverHandler(nvidia_173, nvidia-173, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-05-16 17:57:53,494 DEBUG: NVIDIA accelerated graphics driver not available
2012-05-16 17:57:53,503 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2012-05-16 17:57:53,514 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2012-05-16 17:57:53,515 DEBUG: nvidia.available: falling back to default
2012-05-16 17:57:53,551 DEBUG: XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-05-16 17:57:53,552 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-05-16 17:57:53,552 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-05-16 17:57:53,638 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-05-16 17:57:53,664 DEBUG: Software modem not available
2012-05-16 17:57:53,665 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-05-16 17:57:53,678 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-05-16 17:57:53,689 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2012-05-16 17:57:53,689 DEBUG: fglrx.available: falling back to default
2012-05-16 17:57:53,762 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2012-05-16 17:57:53,771 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-05-16 17:57:53,782 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-05-16 17:57:53,782 DEBUG: fglrx.available: falling back to default
2012-05-16 17:57:53,855 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-05-16 17:57:53,856 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-05-16 17:57:53,903 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-05-16 17:57:53,904 DEBUG: Firmware for DVB cards not available
2012-05-16 17:57:53,904 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2012-05-16 17:57:53,914 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2012-05-16 17:57:53,914 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2012-05-16 17:57:53,950 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2012-05-16 17:57:53,951 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-05-16 17:57:53,962 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-05-16 17:57:53,998 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-05-16 17:57:53,999 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-05-16 17:57:53,999 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-05-16 17:57:54,010 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-05-16 17:57:54,011 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-05-16 17:57:54,012 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-05-16 17:57:54,012 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2012-05-16 17:57:54,025 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2012-05-16 17:57:54,037 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2012-05-16 17:57:54,103 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2012-05-16 17:57:54,104 DEBUG: all custom handlers loaded
2012-05-16 17:57:54,104 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b31200> about HardwareID('modalias', 'acpi:PNP0800:')
2012-05-16 17:57:54,105 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b31200> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-05-16 17:57:54,119 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-16 17:57:54,237 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-16 17:57:54,237 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b31200> about HardwareID('modalias', 'wmi:F75F5666-B8B3-4A5D-A91C-7488F62E5637')
2012-05-16 17:57:54,237 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b31200> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-05-16 17:57:54,238 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b31200> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-05-16 17:57:54,238 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b31200> about HardwareID('modalias', 'pci:v00001002d00001714sv00001025sd0000059Fbc04sc03i00')
2012-05-16 17:57:54,742 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-05-16 17:57:54,742 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-05-16 17:57:54,742 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b31200> about HardwareID('modalias', 'platform:pcspkr')
2012-05-16 17:57:54,743 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2012-05-16 17:57:54,743 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-05-16 17:57:54,743 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2012-05-16 17:57:54,744 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-05-16 17:57:54,744 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b31200> about HardwareID('modalias', 'pci:v000014E4d00004358sv0000105Bsd0000E040bc02sc80i00')
2012-05-16 17:57:54,812 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'wl', 'package': 'bcmwl-kernel-source'}
2012-05-16 17:57:54,813 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2012-05-16 17:57:54,813 DEBUG: found match in handler pool kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2012-05-16 17:57:54,821 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-05-16 17:57:54,822 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2012-05-16 17:57:54,822 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2012-05-16 17:57:54,823 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b31200> about HardwareID('modalias', 'wmi:83B9D139-CE71-45DB-A7A6-2628D3A65F4C')
2012-05-16 17:57:54,823 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b31200> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8D,8E,8F,94,95,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D9,E0,E1,E2,E3,EC,ED,EE,1A9,1B2,1B3,1D0,ram4,l0,1,2,sfw')
2012-05-16 17:57:54,824 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-16 17:57:54,824 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-16 17:57:54,824 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-05-16 17:57:54,825 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-05-16 17:57:54,825 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b31200> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-05-16 17:57:54,825 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b31200> about HardwareID('modalias', 'wmi:67C3371D-95A3-4C37-BB61-DD47B491DAAB')
2012-05-16 17:57:54,825 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'acer_wmi'}
2012-05-16 17:57:54,826 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'acer_wmi', 'jockey_handler': 'KernelModuleHandler'}
2012-05-16 17:57:54,826 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b31200> about HardwareID('modalias', 'platform:acer-wmi')
2012-05-16 17:57:54,828 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b31200> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-05-16 17:57:54,828 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-16 17:57:54,828 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-16 17:57:54,829 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b31200> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-05-16 17:57:54,830 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b31200> about HardwareID('modalias', 'wmi:6AF4F258-B401-42FD-BE91-3D4AC2D7C0D3')
2012-05-16 17:57:54,830 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'acer_wmi'}
2012-05-16 17:57:54,830 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'acer_wmi', 'jockey_handler': 'KernelModuleHandler'}
2012-05-16 17:57:54,831 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b31200> about HardwareID('modalias', 'pci:v00001022d00001705sv00001025sd0000059Fbc06sc00i00')
2012-05-16 17:57:54,854 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b31200> about HardwareID('modalias', 'pci:v000014E4d000016BFsv00001025sd00000605bc08sc80i00')
2012-05-16 17:57:54,855 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b31200> about HardwareID('modalias', 'wmi:CC1A61AC-4256-41A3-B9E0-05A445ADE2F5')
2012-05-16 17:57:54,855 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b31200> about HardwareID('modalias', 'wmi:95764E09-FB56-4E83-B31A-37761F60994A')
2012-05-16 17:57:54,856 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b31200> about HardwareID('modalias', 'acpi:PNP0000:')
2012-05-16 17:57:54,856 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b31200> about HardwareID('modalias', 'pci:v00001022d00001718sv00000000sd00000000bc06sc00i00')
2012-05-16 17:57:54,856 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b31200> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2012-05-16 17:57:54,856 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b31200> about HardwareID('modalias', 'wmi:61EF69EA-865C-4BC3-A502-A0DEBA0CB531')
2012-05-16 17:57:54,857 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b31200> about HardwareID('modalias', 'pci:v00001002d00009647sv00001025sd0000059Fbc03sc00i00')
2012-05-16 17:57:54,863 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2012-05-16 17:57:54,893 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-05-16 17:57:54,893 DEBUG: fglrx_updates is not the alternative in use
2012-05-16 17:57:54,863 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-05-16 17:57:54,902 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-05-16 17:57:54,913 DEBUG: fglrx.available: falling back to default
2012-05-16 17:57:54,988 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-05-16 17:57:54,989 DEBUG: fglrx_updates is not the alternative in use
2012-05-16 17:57:54,958 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-05-16 17:57:54,989 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2012-05-16 17:57:55,020 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-05-16 17:57:55,021 DEBUG: fglrx is not the alternative in use
2012-05-16 17:57:54,990 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-05-16 17:57:55,029 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-05-16 17:57:55,041 DEBUG: fglrx.available: falling back to default
2012-05-16 17:57:55,108 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-05-16 17:57:55,109 DEBUG: fglrx is not the alternative in use
2012-05-16 17:57:55,078 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-05-16 17:57:55,109 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2012-05-16 17:57:55,110 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2012-05-16 17:57:55,110 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b31200> about HardwareID('modalias', 'pci:v000014E4d000016BEsv00001025sd00000605bc08sc80i00')
2012-05-16 17:57:55,112 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b31200> about HardwareID('modalias', 'acpi:PNP0200:')
2012-05-16 17:57:55,112 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b31200> about HardwareID('modalias', 'pci:v00001022d00001716sv00000000sd00000000bc06sc00i00')
2012-05-16 17:57:55,113 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b31200> about HardwareID('modalias', 'pci:v00001022d00001700sv00000000sd00000000bc06sc00i00')
2012-05-16 17:57:55,114 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b31200> about HardwareID('modalias', 'pci:v00001022d0000780Dsv00001025sd0000059Fbc04sc03i00')
2012-05-16 17:57:55,115 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-05-16 17:57:55,115 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-05-16 17:57:55,115 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-05-16 17:57:55,116 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-05-16 17:57:55,116 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b31200> about HardwareID('modalias', 'pci:v00001022d00001703sv00000000sd00000000bc06sc00i00')
2012-05-16 17:57:55,117 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'k10temp'}
2012-05-16 17:57:55,117 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k10temp', 'jockey_handler': 'KernelModuleHandler'}
2012-05-16 17:57:55,117 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b31200> about HardwareID('modalias', 'usb:v04F2pB23Dd4853dcEFdsc02dp01ic0Eisc01ip00')
2012-05-16 17:57:55,149 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2012-05-16 17:57:55,149 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2012-05-16 17:57:55,149 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b31200> about HardwareID('modalias', 'wmi:40D1BF71-A82D-4E59-A168-3985E03B2E87')
2012-05-16 17:57:55,149 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b31200> about HardwareID('modalias', 'input:b0003v04F2pB23De4853-e0,1,kD4,ramlsfw')
2012-05-16 17:57:55,150 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-16 17:57:55,150 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-16 17:57:55,150 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-05-16 17:57:55,150 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-05-16 17:57:55,150 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b31200> about HardwareID('modalias', 'wmi:E78C4453-0227-4861-9EDE-F5600B4A3D39')
2012-05-16 17:57:55,150 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b31200> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2012-05-16 17:57:55,151 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-16 17:57:55,151 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-16 17:57:55,151 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b31200> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-05-16 17:57:55,164 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2012-05-16 17:57:55,164 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-05-16 17:57:55,164 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2012-05-16 17:57:55,164 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-05-16 17:57:55,164 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b31200> about HardwareID('modalias', 'acpi:ETD0500:PNP0F0B:PNP0F12:PNP0F03:PNP0F0E:PNP0F13:')
2012-05-16 17:57:55,165 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b31200> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-05-16 17:57:55,165 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b31200> about HardwareID('modalias', 'pci:v00001022d0000780Bsv00001025sd0000059Fbc0Csc05i00')
2012-05-16 17:57:55,165 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4'}
2012-05-16 17:57:55,165 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2012-05-16 17:57:55,165 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b31200> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-05-16 17:57:55,166 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-16 17:57:55,166 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-16 17:57:55,166 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-05-16 17:57:55,166 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-05-16 17:57:55,166 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b31200> about HardwareID('modalias', 'wmi:79772EC5-04B1-4BFD-843C-61E7F77B6CC9')
2012-05-16 17:57:55,167 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b31200> about HardwareID('modalias', 'wmi:676AA15E-6A47-4D9F-A2CC-1E6D18D14026')
2012-05-16 17:57:55,167 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'acer_wmi'}
2012-05-16 17:57:55,167 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'acer_wmi', 'jockey_handler': 'KernelModuleHandler'}
2012-05-16 17:57:55,167 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b31200> about HardwareID('modalias', 'pci:v00001022d00001719sv00000000sd00000000bc06sc00i00')
2012-05-16 17:57:55,168 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b31200> about HardwareID('modalias', 'dmi:bvnPhoenixTechnologiesLtd.:bvrV1.05:bd05/11/2011:svnAcer:pnAspire5560:pvr0.1:rvnAcer:rnAspire5560:rvrA11:cvnAcer:ct9:cvr0.1:')
2012-05-16 17:57:55,192 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b31200> about HardwareID('modalias', 'pci:v00001022d00001701sv00000000sd00000000bc06sc00i00')
2012-05-16 17:57:55,193 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b31200> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-05-16 17:57:55,193 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b31200> about HardwareID('modalias', 'pci:v00001022d0000780Esv00001025sd0000059Fbc06sc01i00')
2012-05-16 17:57:55,194 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b31200> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-05-16 17:57:55,194 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-16 17:57:55,194 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-16 17:57:55,194 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-05-16 17:57:55,194 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-05-16 17:57:55,195 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b31200> about HardwareID('modalias', 'usb:v090Cp1000d1100dc00dsc00dp00ic08isc06ip50')
2012-05-16 17:57:55,195 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uas'}
2012-05-16 17:57:55,195 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uas', 'jockey_handler': 'KernelModuleHandler'}
2012-05-16 17:57:55,196 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b31200> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2012-05-16 17:57:55,196 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b31200> about HardwareID('modalias', 'wmi:D9F41781-F633-4400-9355-601770BEC510')
2012-05-16 17:57:55,196 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b31200> about HardwareID('modalias', 'pci:v00001022d00001704sv00000000sd00000000bc06sc00i00')
2012-05-16 17:57:55,197 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b31200> about HardwareID('modalias', 'pci:v000014E4d000016B5sv00001025sd00000605bc02sc00i00')
2012-05-16 17:57:55,198 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'tg3'}
2012-05-16 17:57:55,198 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'tg3', 'jockey_handler': 'KernelModuleHandler'}
2012-05-16 17:57:55,198 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b31200> about HardwareID('modalias', 'pci:v00001022d00001702sv00000000sd00000000bc06sc00i00')
2012-05-16 17:57:55,198 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b31200> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2012-05-16 17:57:55,199 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-16 17:57:55,199 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-16 17:57:55,199 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-05-16 17:57:55,199 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-05-16 17:57:55,199 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b31200> about HardwareID('modalias', 'acpi:PNP0303:')
2012-05-16 17:57:55,200 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b31200> about HardwareID('modalias', 'wmi:FAAA1397-1188-448F-8516-9A07987DD38A')
2012-05-16 17:57:55,200 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b31200> about HardwareID('modalias', 'acpi:PNP0100:')
2012-05-16 17:57:55,200 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b31200> about HardwareID('modalias', 'usb:v04F2pB23Dd4853dcEFdsc02dp01ic0Eisc02ip00')
2012-05-16 17:57:55,200 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b31200> about HardwareID('modalias', 'input:b0011v0002p000Ee0000-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2012-05-16 17:57:55,201 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-16 17:57:55,201 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-16 17:57:55,201 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-05-16 17:57:55,201 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-05-16 17:57:55,201 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-05-16 17:57:55,202 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-05-16 17:57:55,202 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-05-16 17:57:55,202 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-05-16 17:57:55,202 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-05-16 17:57:55,202 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-05-16 17:57:55,202 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b31200> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-05-16 17:57:55,203 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b31200> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-05-16 17:57:55,203 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b31200> about HardwareID('modalias', 'wmi:AAE04F7B-B3C5-4865-95D6-9FAC7FF3E92B')
2012-05-16 17:57:55,203 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b31200> about HardwareID('modalias', 'pci:v00001022d0000780Fsv00000000sd00000000bc06sc04i01')
2012-05-16 17:57:55,204 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b31200> about HardwareID('modalias', 'wmi:431F16ED-0C2B-444C-B267-27DEB140CF9C')
2012-05-16 17:57:55,204 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b31200> about HardwareID('modalias', 'pci:v000014E4d000016BCsv00001025sd00000605bc08sc05i01')
2012-05-16 17:57:55,205 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci'}
2012-05-16 17:57:55,205 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2012-05-16 17:57:55,205 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b31200> about HardwareID('modalias', 'pci:v00001022d00007808sv00001025sd0000059Fbc0Csc03i20')
2012-05-16 17:57:55,206 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b31200> about HardwareID('modalias', 'wmi:5923DD45-0480-4ED5-B61A-C9EC6C90E26A')
2012-05-16 17:57:55,206 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b31200> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-05-16 17:57:55,206 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-16 17:57:55,206 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-16 17:57:55,206 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b31200> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,k94,95,BF,CA,CB,E3,ED,EE,F0,ram4,lsfw')
2012-05-16 17:57:55,207 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-05-16 17:57:55,207 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-05-16 17:57:55,207 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-05-16 17:57:55,207 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-05-16 17:57:55,207 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b31200> about HardwareID('modalias', 'pci:v00001022d00007804sv00001025sd0000059Fbc01sc06i01')
2012-05-16 17:57:55,208 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b31200> about HardwareID('modalias', 'wmi:CFF94C79-6C77-4AF7-AC56-7DD0CE01C997')
2012-05-16 17:57:55,208 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2b31200> about HardwareID('modalias', 'wmi:FE1DBBDA-3014-4856-870C-5B3A744BF341')
2012-05-16 17:57:55,208 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e9a950> about HardwareID('modalias', 'acpi:PNP0800:')
2012-05-16 17:57:55,208 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e9a950> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-05-16 17:57:55,209 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e9a950> about HardwareID('modalias', 'wmi:F75F5666-B8B3-4A5D-A91C-7488F62E5637')
2012-05-16 17:57:55,209 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e9a950> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-05-16 17:57:55,209 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e9a950> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-05-16 17:57:55,209 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e9a950> about HardwareID('modalias', 'pci:v00001002d00001714sv00001025sd0000059Fbc04sc03i00')
2012-05-16 17:57:55,209 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e9a950> about HardwareID('modalias', 'platform:pcspkr')
2012-05-16 17:57:55,209 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e9a950> about HardwareID('modalias', 'pci:v000014E4d00004358sv0000105Bsd0000E040bc02sc80i00')
2012-05-16 17:57:55,209 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e9a950> about HardwareID('modalias', 'wmi:83B9D139-CE71-45DB-A7A6-2628D3A65F4C')
2012-05-16 17:57:55,210 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e9a950> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8D,8E,8F,94,95,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D9,E0,E1,E2,E3,EC,ED,EE,1A9,1B2,1B3,1D0,ram4,l0,1,2,sfw')
2012-05-16 17:57:55,210 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e9a950> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-05-16 17:57:55,210 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e9a950> about HardwareID('modalias', 'wmi:67C3371D-95A3-4C37-BB61-DD47B491DAAB')
2012-05-16 17:57:55,210 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e9a950> about HardwareID('modalias', 'platform:acer-wmi')
2012-05-16 17:57:55,210 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e9a950> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-05-16 17:57:55,210 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e9a950> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-05-16 17:57:55,210 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e9a950> about HardwareID('modalias', 'wmi:6AF4F258-B401-42FD-BE91-3D4AC2D7C0D3')
2012-05-16 17:57:55,210 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e9a950> about HardwareID('modalias', 'pci:v00001022d00001705sv00001025sd0000059Fbc06sc00i00')
2012-05-16 17:57:55,211 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e9a950> about HardwareID('modalias', 'pci:v000014E4d000016BFsv00001025sd00000605bc08sc80i00')
2012-05-16 17:57:55,211 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e9a950> about HardwareID('modalias', 'wmi:CC1A61AC-4256-41A3-B9E0-05A445ADE2F5')
2012-05-16 17:57:55,211 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e9a950> about HardwareID('modalias', 'wmi:95764E09-FB56-4E83-B31A-37761F60994A')
2012-05-16 17:57:55,211 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e9a950> about HardwareID('modalias', 'acpi:PNP0000:')
2012-05-16 17:57:55,211 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e9a950> about HardwareID('modalias', 'pci:v00001022d00001718sv00000000sd00000000bc06sc00i00')
2012-05-16 17:57:55,211 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e9a950> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2012-05-16 17:57:55,211 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e9a950> about HardwareID('modalias', 'wmi:61EF69EA-865C-4BC3-A502-A0DEBA0CB531')
2012-05-16 17:57:55,212 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e9a950> about HardwareID('modalias', 'pci:v00001002d00009647sv00001025sd0000059Fbc03sc00i00')
2012-05-16 17:57:55,212 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e9a950> about HardwareID('modalias', 'pci:v000014E4d000016BEsv00001025sd00000605bc08sc80i00')
2012-05-16 17:57:55,212 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e9a950> about HardwareID('modalias', 'acpi:PNP0200:')
2012-05-16 17:57:55,212 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e9a950> about HardwareID('modalias', 'pci:v00001022d00001716sv00000000sd00000000bc06sc00i00')
2012-05-16 17:57:55,212 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e9a950> about HardwareID('modalias', 'pci:v00001022d00001700sv00000000sd00000000bc06sc00i00')
2012-05-16 17:57:55,212 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e9a950> about HardwareID('modalias', 'pci:v00001022d0000780Dsv00001025sd0000059Fbc04sc03i00')
2012-05-16 17:57:55,212 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e9a950> about HardwareID('modalias', 'pci:v00001022d00001703sv00000000sd00000000bc06sc00i00')
2012-05-16 17:57:55,213 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e9a950> about HardwareID('modalias', 'usb:v04F2pB23Dd4853dcEFdsc02dp01ic0Eisc01ip00')
2012-05-16 17:57:55,213 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e9a950> about HardwareID('modalias', 'wmi:40D1BF71-A82D-4E59-A168-3985E03B2E87')
2012-05-16 17:57:55,213 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e9a950> about HardwareID('modalias', 'input:b0003v04F2pB23De4853-e0,1,kD4,ramlsfw')
2012-05-16 17:57:55,213 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e9a950> about HardwareID('modalias', 'wmi:E78C4453-0227-4861-9EDE-F5600B4A3D39')
2012-05-16 17:57:55,213 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e9a950> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2012-05-16 17:57:55,213 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e9a950> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-05-16 17:57:55,213 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e9a950> about HardwareID('modalias', 'acpi:ETD0500:PNP0F0B:PNP0F12:PNP0F03:PNP0F0E:PNP0F13:')
2012-05-16 17:57:55,213 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e9a950> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-05-16 17:57:55,214 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e9a950> about HardwareID('modalias', 'pci:v00001022d0000780Bsv00001025sd0000059Fbc0Csc05i00')
2012-05-16 17:57:55,214 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e9a950> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-05-16 17:57:55,214 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e9a950> about HardwareID('modalias', 'wmi:79772EC5-04B1-4BFD-843C-61E7F77B6CC9')
2012-05-16 17:57:55,214 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e9a950> about HardwareID('modalias', 'wmi:676AA15E-6A47-4D9F-A2CC-1E6D18D14026')
2012-05-16 17:57:55,214 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e9a950> about HardwareID('modalias', 'pci:v00001022d00001719sv00000000sd00000000bc06sc00i00')
2012-05-16 17:57:55,214 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e9a950> about HardwareID('modalias', 'dmi:bvnPhoenixTechnologiesLtd.:bvrV1.05:bd05/11/2011:svnAcer:pnAspire5560:pvr0.1:rvnAcer:rnAspire5560:rvrA11:cvnAcer:ct9:cvr0.1:')
2012-05-16 17:57:55,215 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e9a950> about HardwareID('modalias', 'pci:v00001022d00001701sv00000000sd00000000bc06sc00i00')
2012-05-16 17:57:55,215 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e9a950> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-05-16 17:57:55,215 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e9a950> about HardwareID('modalias', 'pci:v00001022d0000780Esv00001025sd0000059Fbc06sc01i00')
2012-05-16 17:57:55,215 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e9a950> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-05-16 17:57:55,215 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e9a950> about HardwareID('modalias', 'usb:v090Cp1000d1100dc00dsc00dp00ic08isc06ip50')
2012-05-16 17:57:55,215 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e9a950> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2012-05-16 17:57:55,215 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e9a950> about HardwareID('modalias', 'wmi:D9F41781-F633-4400-9355-601770BEC510')
2012-05-16 17:57:55,216 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e9a950> about HardwareID('modalias', 'pci:v00001022d00001704sv00000000sd00000000bc06sc00i00')
2012-05-16 17:57:55,216 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e9a950> about HardwareID('modalias', 'pci:v000014E4d000016B5sv00001025sd00000605bc02sc00i00')
2012-05-16 17:57:55,216 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e9a950> about HardwareID('modalias', 'pci:v00001022d00001702sv00000000sd00000000bc06sc00i00')
2012-05-16 17:57:55,216 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e9a950> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2012-05-16 17:57:55,216 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e9a950> about HardwareID('modalias', 'acpi:PNP0303:')
2012-05-16 17:57:55,216 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e9a950> about HardwareID('modalias', 'wmi:FAAA1397-1188-448F-8516-9A07987DD38A')
2012-05-16 17:57:55,216 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e9a950> about HardwareID('modalias', 'acpi:PNP0100:')
2012-05-16 17:57:55,217 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e9a950> about HardwareID('modalias', 'usb:v04F2pB23Dd4853dcEFdsc02dp01ic0Eisc02ip00')
2012-05-16 17:57:55,217 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e9a950> about HardwareID('modalias', 'input:b0011v0002p000Ee0000-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2012-05-16 17:57:55,217 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e9a950> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-05-16 17:57:55,217 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e9a950> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-05-16 17:57:55,217 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e9a950> about HardwareID('modalias', 'wmi:AAE04F7B-B3C5-4865-95D6-9FAC7FF3E92B')
2012-05-16 17:57:55,217 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e9a950> about HardwareID('modalias', 'pci:v00001022d0000780Fsv00000000sd00000000bc06sc04i01')
2012-05-16 17:57:55,217 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e9a950> about HardwareID('modalias', 'wmi:431F16ED-0C2B-444C-B267-27DEB140CF9C')
2012-05-16 17:57:55,218 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e9a950> about HardwareID('modalias', 'pci:v000014E4d000016BCsv00001025sd00000605bc08sc05i01')
2012-05-16 17:57:55,218 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e9a950> about HardwareID('modalias', 'pci:v00001022d00007808sv00001025sd0000059Fbc0Csc03i20')
2012-05-16 17:57:55,218 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e9a950> about HardwareID('modalias', 'wmi:5923DD45-0480-4ED5-B61A-C9EC6C90E26A')
2012-05-16 17:57:55,218 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e9a950> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-05-16 17:57:55,218 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e9a950> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,k94,95,BF,CA,CB,E3,ED,EE,F0,ram4,lsfw')
2012-05-16 17:57:55,218 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e9a950> about HardwareID('modalias', 'pci:v00001022d00007804sv00001025sd0000059Fbc01sc06i01')
2012-05-16 17:57:55,219 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e9a950> about HardwareID('modalias', 'wmi:CFF94C79-6C77-4AF7-AC56-7DD0CE01C997')
2012-05-16 17:57:55,219 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2e9a950> about HardwareID('modalias', 'wmi:FE1DBBDA-3014-4856-870C-5B3A744BF341')
2012-05-16 17:57:55,340 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-05-16 17:57:55,340 DEBUG: fglrx_updates is not the alternative in use
2012-05-16 17:57:55,418 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2012-05-16 17:57:55,488 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-05-16 17:57:55,488 DEBUG: fglrx is not the alternative in use
2012-05-16 17:57:55,560 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-05-16 17:57:55,560 DEBUG: fglrx_updates is not the alternative in use
2012-05-16 17:57:55,664 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-05-16 17:57:55,664 DEBUG: fglrx_updates is not the alternative in use
2012-05-16 17:57:55,699 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2012-05-16 17:57:55,762 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-05-16 17:57:55,763 DEBUG: fglrx is not the alternative in use
2012-05-16 17:57:58,093 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2012-05-16 17:57:59,669 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2012-05-16 17:58:02,585 DEBUG: Installing package: bcmwl-kernel-source
2012-05-16 17:58:03,856 DEBUG: download progress <Package: name:'bcmwl-kernel-source' architecture='amd64' id:16878L> 0.000000
2012-05-16 17:58:03,858 DEBUG: download progress <Package: name:'bcmwl-kernel-source' architecture='amd64' id:16878L> 0.000000
2012-05-16 17:58:03,862 DEBUG: download progress <Package: name:'bcmwl-kernel-source' architecture='amd64' id:16878L> 0.000000
2012-05-16 17:58:03,899 ERROR: Package fetching failed: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/p/patch/patch_2.6.1-3_amd64.deb Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-1ubuntu3_all.deb Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.100.82.38+bdcom-0ubuntu6_amd64.deb Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/f/fakeroot/fakeroot_1.18.2-1_amd64.deb Could not resolve 'archive.ubuntu.com'

2012-05-16 17:58:04,180 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-05-16 17:58:04,181 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2012-05-16 17:58:04,305 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2012-05-16 17:58:06,926 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-05-16 17:58:06,926 DEBUG: fglrx_updates is not the alternative in use
2012-05-16 17:58:06,967 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2012-05-16 17:58:07,043 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-05-16 17:58:07,044 DEBUG: fglrx is not the alternative in use
2012-05-16 17:58:07,096 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2012-05-16 17:58:07,212 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-05-16 17:58:07,213 DEBUG: fglrx_updates is not the alternative in use
2012-05-16 17:58:07,247 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2012-05-16 17:58:07,319 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-05-16 17:58:07,319 DEBUG: fglrx is not the alternative in use
2012-05-16 17:58:09,722 DEBUG: Shutting down

```

I got this error (errors were encountered while processing: ndisgtk) after doing sudo dpkg -i ndisgtk_*.deb from this installation guide [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper).

Please help me....

---

### Post by chili555 on 2012-05-16
We're here to help. First of all, you don't need ndiswrapper, so, depending on what's done so far. you can probably simply abandon that process. Second, the exact fix depends on the card you have. Please open the terminal and run and post:```
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

Do you have a temporary wired ethernet connection?

---

### Post by Tyluur on 2012-05-16
```
tyluur@ubuntu:~$ lspci -nn | grep 0280
02:00.0 Network controller [0280]: Broadcom Corporation BCM43227 802.11b/g/n [14e4:4358]

```

What do you mean by a temporary wired ethernet connection?

I connect to my internet on windows 7 by opening networking and choosing 'virus' (name of wireless router), then entering the password

---

### Post by chili555 on 2012-05-16
> What do you mean by a temporary wired ethernet connection?
I mean a connection by ethernet cable where you walk your computer over to the router and hook up a cable. You need a package called bcmwl-kernel-source that has quite a few dependencies. With an ethernet connection, you can instruct your Ubuntu system to grab it and it will do the hard work for you in about two minutes. If you want to download to Windows and move it over on a USB key, it will be pretty complex and may not go perfectly the first time.

If you *can* get a temporary wired ethernet connection, open a terminal and do:```
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```Detach the cable and you're done.

---

### Post by Tyluur on 2012-05-16
> **chili555 said:**
> I mean a connection by ethernet cable where you walk your computer over to the router and hook up a cable. You need a package called bcmwl-kernel-source that has quite a few dependencies. With an ethernet connection, you can instruct your Ubuntu system to grab it and it will do the hard work for you in about two minutes. If you want to download to Windows and move it over on a USB key, it will be pretty complex and may not go perfectly the first time.

If you *can* get a temporary wired ethernet connection, open a terminal and do:```
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```Detach the cable and you're done.

I can't get a temporary wired ethernet connection, what files should I put in a USB and do afterwards?

---

### Post by chili555 on 2012-05-16
There is one other possibility. Do you have your install disk? Can you browse the CD in Ubuntu and go to pool > restricted > b > bcmwl-kernel-source? If so, right-click it and select *Open with Ubuntu Software Center*. It ought to install it.

Please see attached.

---

### Post by Tyluur on 2012-05-16
I installed Ubuntu from [www.ubuntu.com](www.ubuntu.com) with Windows Desktop installation. :$

---

### Post by chili555 on 2012-05-16
To install it, didn't you download an iso file and burn it to a CD? That's the CD you need to put back in the drive and browse as I explained.

---

### Post by Tyluur on 2012-05-16
I downloaded the ISO, extracted it to a directory and installed it there.

---

### Post by chili555 on 2012-05-16
What's in that directory now? pool > restricted > b > bcmwl-kernel-source among many other things?

---

### Post by Tyluur on 2012-05-16
Yes.

---

### Post by Tyluur on 2012-05-16
I did your steps after getting pool - > restricted - > b - > broadcom etc... and then I received this error:

Items cannot be installed or removed until the package catalog is repared. Do you want to repair it now?

I pressed repair and I got this:

Failed to download package files, check your internet connection.

Details -> Failed to fetch [http://archive.ubuntu.com/etc](http://archive.ubuntu.com/etc)...

---

### Post by chili555 on 2012-05-16
> Failed to download package files, check your internet connection.

Details -> Failed to fetch [http://archive.ubuntu.com/etc](http://archive.ubuntu.com/etc)... It's trying to go on line; you can't do that yet.

You'll need to copy it to a USB key or similar along with all the dependencies here: [http://packages.ubuntu.com/precise/bcmwl-kernel-source](http://packages.ubuntu.com/precise/bcmwl-kernel-source)

That assumes you have the latest Ubuntu version 12.04. If not, look on the site and match your version. Find out with the terminal command:```
lsb_release -a
```Also, be sure to get the correct package for your architecture; either 32- or 64-bit; referred to as i386 or amd64. Some of the packages may also be in your directory you referred to above.

The dependencies are all the items with red dots. Once you have them all copied over, we'll proceed.

Post back if you get stuck.

---

### Post by Tyluur on 2012-05-16
When I open the downloaded ([http://packages.ubuntu.com/precise/amd64/bcmwl-kernel-source/download](http://packages.ubuntu.com/precise/amd64/bcmwl-kernel-source/download)) file, I get the **Items cannot be installed or removed until the package catalog is repaired** error in the software center, and it stops me from installing if I press cancel.

Upon pressing cancel, the install button is shaded out and I cannot click it. If I press repair I get the cannot connect to internet error.

This is very troublesome :(.

---

### Post by chili555 on 2012-05-16
We are not going to install the packages with Software Center. Copy the files to your Ubuntu desktop. Open a terminal and change directories to the desktop:```
cd Desktop
```Now install the .deb files like this:```
sudo dpkg -i bcmwl*.deb
```If it says it can't because it needs a dependency, it will no doubt be one of the other packages you downloaded; install it first:```
sudo dpkg -i some_package*.deb
```Keep going till they're all done.

---

### Post by Tyluur on 2012-05-16
Which packages is it that I'm installing? Sorry, I'm very new to this...

---

### Post by chili555 on 2012-05-16
See post #13. Go here: [http://packages.ubuntu.com/precise/bcmwl-kernel-source](http://packages.ubuntu.com/precise/bcmwl-kernel-source)

Copy the bcmwl-kernel-source that you already have to a USB key. Grab all its dependencies with the red dots: > **dkms**
    Dynamic Kernel Module Support Framework 

**libc6-dev**
    Embedded GNU C Library: Development Libraries and Header Files 

linux-headers-generic [amd64]
    Generic Linux kernel headers 
or **linux-headers**
    virtual package provided by linux-headers-3.2.0-23, **linux-headers-3.2.0-23-generic**, linux-headers-3.2.0-23-generic-pae, linux-headers-3.2.0-23-lowlatency, linux-headers-3.2.0-23-lowlatency-pae, linux-headers-3.2.0-23-virtual 

linux-headers-generic-pae [i386]
    Generic Linux kernel headers 
or linux-headers
    virtual package provided by linux-headers-3.2.0-23, linux-headers-3.2.0-23-generic, linux-headers-3.2.0-23-generic-pae, linux-headers-3.2.0-23-lowlatency, linux-headers-3.2.0-23-lowlatency-pae, linux-headers-3.2.0-23-virtual 

**linux-libc-dev**
    Linux Kernel Headers for development 

Copy them to the USB drive, too. Make sure the linux-headers match your kernel:```
uname -r
```For example:> chili@Think60:~$ uname -r
[COLOR="Red"]3.2.0-24-generic-pae[/COLOR]So if I were installing linux-headers, I'd need lunux-headers-generic and linux-headers-[COLOR="Red"]3.2.0-24-generic-pae[/COLOR].

Once you have them all on your Ubuntu desktop, install as I outlined above.

---

### Post by Tyluur on 2012-05-16
Thank you very much for your help thus far. I have downloaded the following:

[img]http://i.imgur.com/0FUee.png[/img] because I am on 64-bit. I then did

```
sudo dpkg -i dkms_2.2.0.3-1*.deb
```. I received this error afterwards:

```
Errors were encountered while processing:
   dkms
```

Thank you very much for your help again.

---

### Post by chili555 on 2012-05-16
> Errors were encountered while processing:
   dkmsWe need to know *what* error. Dependencies? Version? Architecture? Or...?? Also, you can shorten up the commands with:```
sudo dpkg -i dkms*.deb
```

---

### Post by Tyluur on 2012-05-16
The errors start here...
```
dpkg: dependency problems prevent configuration of dkms:
 dkms depend on patch; however:
Package patch is noot installed.
Errors were encountered while processing: 
 dkms
```

---

### Post by chili555 on 2012-05-16
> dkms depend on patch; however:
Package patch is noot installed.That just means you also need to go get *patch* and install it, too. The same for any others that fail because of dependencies.

---

### Post by Tyluur on 2012-05-16
Where do I get patch from?

---

### Post by chili555 on 2012-05-16
Same as everything else. Can you search for it?  [http://packages.ubuntu.com/precise/patch](http://packages.ubuntu.com/precise/patch)

---

### Post by Tyluur on 2012-05-16
I have installed everything including bcmwl-kernel, and the last message was
Warning: No support for locale: en_US.utf8.

How do I continue the process for getting wireless to work?

Thank you for working with me thus far.

EDIT: RAN sudo modprobe wl and it worked! Thank you very much for your patience & help.

---

### Post by chili555 on 2012-05-17
Excellent! Glad to hear it's working. Please use thread tools at the top to Mark Solved.

---

