---
title: "Trouble with BCM43228 driver on Thinkpad T430u and 12.04"
date: 2013-04-10
forum: Networking &amp; Wireless
---

### Post by nathockens on 2013-04-10
I give up. After digging through ndisgtk documentation and another afternoon of ndiswrapper documnetation, I click the "additional drivers" section in 12.04 and found that there's a proprietary license for the BCM43228 driver I have in this Thinkpad. Great. Click activate and the process borks.

jockey.log attached. Any ideas? My brain is explode. :(

> 
2013-04-10 13:28:03,372 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x89d9a0c>
2013-04-10 13:28:04,609 DEBUG: reading modalias file /lib/modules/3.5.0-23-generic/modules.alias
2013-04-10 13:28:04,711 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2013-04-10 13:28:04,712 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2013-04-10 13:28:04,763 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2013-04-10 13:28:04,771 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2013-04-10 13:28:04,797 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2013-04-10 13:28:04,798 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2013-04-10 13:28:04,798 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2013-04-10 13:28:04,806 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2013-04-10 13:28:04,808 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2013-04-10 13:28:04,808 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2013-04-10 13:28:04,808 DEBUG: loading custom handler /usr/share/jockey/handlers/cdv.py
2013-04-10 13:28:04,819 WARNING: modinfo for module cedarview_gfx failed: ERROR: modinfo: could not find module cedarview_gfx

2013-04-10 13:28:04,820 DEBUG: Instantiated Handler subclass __builtin__.CdvDriver from name CdvDriver
2013-04-10 13:28:04,820 DEBUG: cdv.available: falling back to default
2013-04-10 13:28:04,968 DEBUG: XorgDriverHandler(cedarview_gfx, cedarview-graphics-drivers, None): Disabling as package is not compatible with Q-LTS X.org
2013-04-10 13:28:04,968 DEBUG: Intel Cedarview graphics driver not available
2013-04-10 13:28:04,968 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2013-04-10 13:28:04,978 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2013-04-10 13:28:04,986 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2013-04-10 13:28:04,988 DEBUG: Disabling Nvidia driver on intel/hybrid system
2013-04-10 13:28:04,989 DEBUG: NVIDIA accelerated graphics driver not available
2013-04-10 13:28:04,994 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2013-04-10 13:28:05,000 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2013-04-10 13:28:05,001 DEBUG: Disabling Nvidia driver on intel/hybrid system
2013-04-10 13:28:05,002 DEBUG: NVIDIA accelerated graphics driver not available
2013-04-10 13:28:05,008 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2013-04-10 13:28:05,015 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2013-04-10 13:28:05,016 DEBUG: Disabling Nvidia driver on intel/hybrid system
2013-04-10 13:28:05,017 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2013-04-10 13:28:05,023 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2013-04-10 13:28:05,030 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2013-04-10 13:28:05,031 DEBUG: Disabling Nvidia driver on intel/hybrid system
2013-04-10 13:28:05,031 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2013-04-10 13:28:05,037 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2013-04-10 13:28:05,045 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2013-04-10 13:28:05,046 DEBUG: Disabling Nvidia driver on intel/hybrid system
2013-04-10 13:28:05,046 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2013-04-10 13:28:05,053 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2013-04-10 13:28:05,060 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2013-04-10 13:28:05,061 DEBUG: Disabling Nvidia driver on intel/hybrid system
2013-04-10 13:28:05,062 DEBUG: NVIDIA accelerated graphics driver not available
2013-04-10 13:28:05,068 WARNING: modinfo for module nvidia_experimental_310 failed: ERROR: modinfo: could not find module nvidia_experimental_310

2013-04-10 13:28:05,099 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverExperimental310 from name NvidiaDriverExperimental310
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 972, in get_handlers
    desc = inst.name()
  File "/usr/lib/python2.7/dist-packages/jockey/handlers.py", line 108, in name
    self._package_defaults()
  File "/usr/lib/python2.7/dist-packages/jockey/handlers.py", line 93, in _package_defaults
    (distro_name, distro_desc) = OSLib.inst.package_description(self.package)
  File "/usr/lib/python2.7/dist-packages/jockey/oslib.py", line 216, in package_description
    raise ValueError('package %s does not exist' % package)
ValueError: package nvidia-experimental-310 does not exist
2013-04-10 13:28:05,110 WARNING: modinfo for module nvidia_experimental_304 failed: ERROR: modinfo: could not find module nvidia_experimental_304

2013-04-10 13:28:05,139 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverExperimental304 from name NvidiaDriverExperimental304
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 972, in get_handlers
    desc = inst.name()
  File "/usr/lib/python2.7/dist-packages/jockey/handlers.py", line 108, in name
    self._package_defaults()
  File "/usr/lib/python2.7/dist-packages/jockey/handlers.py", line 93, in _package_defaults
    (distro_name, distro_desc) = OSLib.inst.package_description(self.package)
  File "/usr/lib/python2.7/dist-packages/jockey/oslib.py", line 216, in package_description
    raise ValueError('package %s does not exist' % package)
ValueError: package nvidia-experimental-304 does not exist
2013-04-10 13:28:05,140 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2013-04-10 13:28:05,161 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2013-04-10 13:28:05,178 DEBUG: Software modem not available
2013-04-10 13:28:05,179 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2013-04-10 13:28:05,186 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2013-04-10 13:28:05,193 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2013-04-10 13:28:05,341 DEBUG: XorgDriverHandler(omapdrm_pvr, pvr-omap4, None): Disabling as package is not compatible with Q-LTS X.org
2013-04-10 13:28:05,342 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2013-04-10 13:28:05,342 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2013-04-10 13:28:05,347 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2013-04-10 13:28:05,348 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2013-04-10 13:28:05,372 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2013-04-10 13:28:05,373 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2013-04-10 13:28:05,404 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2013-04-10 13:28:05,405 DEBUG: Firmware for DVB cards not available
2013-04-10 13:28:05,406 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2013-04-10 13:28:05,415 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2013-04-10 13:28:05,420 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2013-04-10 13:28:05,421 DEBUG: fglrx.available: falling back to default
2013-04-10 13:28:05,556 DEBUG: XorgDriverHandler(fglrx_updates, fglrx-updates, None): Disabling as package is not compatible with Q-LTS X.org
2013-04-10 13:28:05,557 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) not available
2013-04-10 13:28:05,563 WARNING: modinfo for module fglrx_experimental_9 failed: ERROR: modinfo: could not find module fglrx_experimental_9

2013-04-10 13:28:05,595 DEBUG: Could not instantiate Handler subclass __builtin__.FglrxDriverExperimental9 from name FglrxDriverExperimental9
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 972, in get_handlers
    desc = inst.name()
  File "/usr/lib/python2.7/dist-packages/jockey/handlers.py", line 108, in name
    self._package_defaults()
  File "/usr/lib/python2.7/dist-packages/jockey/handlers.py", line 93, in _package_defaults
    (distro_name, distro_desc) = OSLib.inst.package_description(self.package)
  File "/usr/lib/python2.7/dist-packages/jockey/oslib.py", line 216, in package_description
    raise ValueError('package %s does not exist' % package)
ValueError: package fglrx-experimental-9 does not exist
2013-04-10 13:28:05,601 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2013-04-10 13:28:05,609 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2013-04-10 13:28:05,609 DEBUG: fglrx.available: falling back to default
2013-04-10 13:28:05,750 DEBUG: XorgDriverHandler(fglrx, fglrx, None): Disabling as package is not compatible with Q-LTS X.org
2013-04-10 13:28:05,750 DEBUG: ATI/AMD proprietary FGLRX graphics driver not available
2013-04-10 13:28:05,751 DEBUG: all custom handlers loaded
2013-04-10 13:28:05,751 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89d9a0c> about HardwareID('modalias', 'pci:v00008086d00001E3Asv000017AAsd0000500Cbc07sc80i00')
2013-04-10 13:28:05,961 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mei'}
2013-04-10 13:28:06,025 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mei', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:28:06,026 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89d9a0c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,145,148,14A,14D,14E,14F,ra0,1,18,1C,2F,35,36,39,3A,mlsfw')
2013-04-10 13:28:06,029 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-10 13:28:06,029 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:28:06,029 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2013-04-10 13:28:06,029 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:28:06,029 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2013-04-10 13:28:06,029 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:28:06,029 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2013-04-10 13:28:06,029 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:28:06,029 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-04-10 13:28:06,030 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:28:06,030 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89d9a0c> about HardwareID('modalias', 'acpi:PNP0200:')
2013-04-10 13:28:06,030 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89d9a0c> about HardwareID('modalias', 'acpi:PNP0103:')
2013-04-10 13:28:06,030 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89d9a0c> about HardwareID('modalias', 'acpi:PNP0303:PNP0303:')
2013-04-10 13:28:06,030 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89d9a0c> about HardwareID('modalias', 'pci:v00008086d00000154sv000017AAsd0000500Cbc06sc00i00')
2013-04-10 13:28:06,032 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89d9a0c> about HardwareID('modalias', 'pci:v00008086d00001E31sv000017AAsd0000500Cbc0Csc03i30')
2013-04-10 13:28:06,034 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89d9a0c> about HardwareID('modalias', 'platform:thinkpad_hwmon')
2013-04-10 13:28:06,035 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89d9a0c> about HardwareID('modalias', 'input:b0019v17AAp5054e4101-e0,1,4,5,k71,72,73,8E,94,98,BF,C2,CD,D4,E0,E1,E3,E4,EC,EE,F0,F8,174,1D2,1DB,1DC,ram4,lsfw1,3,')
2013-04-10 13:28:06,035 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-10 13:28:06,035 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:28:06,035 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-04-10 13:28:06,035 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:28:06,035 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89d9a0c> about HardwareID('modalias', 'usb:v1D6Bp0002d0305dc09dsc00dp01ic09isc00ip00')
2013-04-10 13:28:06,045 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89d9a0c> about HardwareID('modalias', 'usb:v1D6Bp0003d0305dc09dsc00dp03ic09isc00ip00')
2013-04-10 13:28:06,045 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89d9a0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2013-04-10 13:28:06,045 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-10 13:28:06,045 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:28:06,045 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89d9a0c> about HardwareID('modalias', 'platform:microcode')
2013-04-10 13:28:06,045 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89d9a0c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2013-04-10 13:28:06,045 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89d9a0c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-04-10 13:28:06,046 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89d9a0c> about HardwareID('modalias', 'platform:thinkpad_acpi')
2013-04-10 13:28:06,046 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89d9a0c> about HardwareID('modalias', 'acpi:LEN0051:PNP0F13:')
2013-04-10 13:28:06,046 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89d9a0c> about HardwareID('modalias', 'platform:eisa')
2013-04-10 13:28:06,046 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89d9a0c> about HardwareID('modalias', 'wmi:7FF47003-3B6C-4E5E-A227-E979824A85D1')
2013-04-10 13:28:06,046 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89d9a0c> about HardwareID('modalias', 'pci:v00008086d00001E26sv000017AAsd0000500Cbc0Csc03i20')
2013-04-10 13:28:06,049 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89d9a0c> about HardwareID('modalias', 'wmi:6A4B54EF-A5ED-4D33-9455-B0D9B48DF4B3')
2013-04-10 13:28:06,049 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89d9a0c> about HardwareID('modalias', 'usb:v0A5Cp21F3d0112dcFFdsc01dp01icFEisc01ip01')
2013-04-10 13:28:06,050 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89d9a0c> about HardwareID('modalias', 'serio:ty05pr00id00ex00')
2013-04-10 13:28:06,056 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2013-04-10 13:28:06,056 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:28:06,056 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89d9a0c> about HardwareID('modalias', 'pci:v00008086d00001E58sv000017AAsd0000500Cbc06sc01i00')
2013-04-10 13:28:06,058 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'lpc_ich'}
2013-04-10 13:28:06,058 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'lpc_ich', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:28:06,058 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89d9a0c> about HardwareID('modalias', 'pci:v00008086d00001E03sv000017AAsd0000500Cbc01sc06i01')
2013-04-10 13:28:06,060 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89d9a0c> about HardwareID('modalias', 'pci:v00008086d00001E2Dsv000017AAsd0000500Cbc0Csc03i20')
2013-04-10 13:28:06,062 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89d9a0c> about HardwareID('modalias', 'acpi:INT3392:PNP0C02:')
2013-04-10 13:28:06,062 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89d9a0c> about HardwareID('modalias', 'pci:v00008086d00001E22sv000017AAsd0000500Cbc0Csc05i00')
2013-04-10 13:28:06,065 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801'}
2013-04-10 13:28:06,065 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:28:06,065 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89d9a0c> about HardwareID('modalias', 'acpi:PNP0B00:')
2013-04-10 13:28:06,065 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89d9a0c> about HardwareID('modalias', 'pci:v000014E4d00004359sv000014E4sd00000607bc02sc80i00')
2013-04-10 13:28:06,095 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'wl', 'package': 'bcmwl-kernel-source'}
2013-04-10 13:28:06,095 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-04-10 13:28:06,095 DEBUG: found match in handler pool kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2013-04-10 13:28:06,100 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2013-04-10 13:28:06,101 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-04-10 13:28:06,101 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2013-04-10 13:28:06,101 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89d9a0c> about HardwareID('modalias', 'usb:v1D6Bp0002d0305dc09dsc00dp00ic09isc00ip00')
2013-04-10 13:28:06,101 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89d9a0c> about HardwareID('modalias', 'acpi:PNP0C04:')
2013-04-10 13:28:06,101 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89d9a0c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2013-04-10 13:28:06,101 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2013-04-10 13:28:06,101 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:28:06,101 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2013-04-10 13:28:06,102 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:28:06,102 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89d9a0c> about HardwareID('modalias', 'acpi:PNP0100:')
2013-04-10 13:28:06,102 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89d9a0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2013-04-10 13:28:06,102 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-10 13:28:06,102 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:28:06,102 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89d9a0c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2013-04-10 13:28:06,102 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-10 13:28:06,102 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:28:06,102 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-04-10 13:28:06,102 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:28:06,102 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89d9a0c> about HardwareID('modalias', 'usb:v0A5Cp21F3d0112dcFFdsc01dp01icFFiscFFipFF')
2013-04-10 13:28:06,102 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89d9a0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2013-04-10 13:28:06,102 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-10 13:28:06,103 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:28:06,103 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89d9a0c> about HardwareID('modalias', 'wmi:E2BE5EE3-42DA-49DB-8378-1F5247388202')
2013-04-10 13:28:06,103 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89d9a0c> about HardwareID('modalias', 'acpi:PNP0C02:')
2013-04-10 13:28:06,103 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89d9a0c> about HardwareID('modalias', 'dmi:bvnLENOVO:bvrH6ET90WW(2.08):bd01/11/2013:svnLENOVO:pn3351CTO:pvrThinkPadT430u:rvnLENOVO:rn3351CTO:rvrNotDefined:cvnLENOVO:ct10:cvrNotAvailable:')
2013-04-10 13:28:06,112 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89d9a0c> about HardwareID('modalias', 'wmi:FCB424F1-075A-4E0E-BFC4-62F3E71771FA')
2013-04-10 13:28:06,112 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89d9a0c> about HardwareID('modalias', 'pci:v000010ECd00008168sv000017AAsd0000500Cbc02sc00i00')
2013-04-10 13:28:06,118 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2013-04-10 13:28:06,118 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:28:06,118 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89d9a0c> about HardwareID('modalias', 'wmi:7430019A-DCE9-4548-BAB0-9FDE0935CAFF')
2013-04-10 13:28:06,118 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89d9a0c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2013-04-10 13:28:06,118 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-10 13:28:06,118 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:28:06,118 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-04-10 13:28:06,119 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:28:06,119 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89d9a0c> about HardwareID('modalias', 'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2013-04-10 13:28:06,119 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89d9a0c> about HardwareID('modalias', 'usb:v5986p0523d1402dcEFdsc02dp01ic0Eisc02ip00')
2013-04-10 13:28:06,119 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89d9a0c> about HardwareID('modalias', 'pci:v00008086d00000166sv000017AAsd0000500Cbc03sc00i00')
2013-04-10 13:28:06,121 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i915'}
2013-04-10 13:28:06,122 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:28:06,122 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89d9a0c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2013-04-10 13:28:06,122 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-10 13:28:06,122 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:28:06,122 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-04-10 13:28:06,122 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:28:06,122 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89d9a0c> about HardwareID('modalias', 'pci:v000010ECd00005209sv000010ECsd00005209bc08sc05i00')
2013-04-10 13:28:06,122 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci'}
2013-04-10 13:28:06,122 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:28:06,122 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89d9a0c> about HardwareID('modalias', 'acpi:PNP0000:')
2013-04-10 13:28:06,122 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89d9a0c> about HardwareID('modalias', 'usb:v0A5Cp21F3d0112dcFFdsc01dp01icFFisc01ip01')
2013-04-10 13:28:06,122 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2013-04-10 13:28:06,123 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:28:06,123 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89d9a0c> about HardwareID('modalias', 'wmi:8ADB159E-1E32-455C-BC93-308A7ED98246')
2013-04-10 13:28:06,123 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89d9a0c> about HardwareID('modalias', 'pci:v00008086d00001E20sv000017AAsd0000500Cbc04sc03i00')
2013-04-10 13:28:06,125 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-04-10 13:28:06,125 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:28:06,125 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-04-10 13:28:06,125 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:28:06,125 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89d9a0c> about HardwareID('modalias', 'acpi:INT0800:')
2013-04-10 13:28:06,125 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89d9a0c> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2013-04-10 13:28:06,125 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89d9a0c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-04-10 13:28:06,125 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89d9a0c> about HardwareID('modalias', 'wmi:7EEF04FF-4328-447C-B5BB-D449925D538D')
2013-04-10 13:28:06,126 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89d9a0c> about HardwareID('modalias', 'pci:v000010ECd00005209sv000010ECsd00005209bcFFsc00i00')
2013-04-10 13:28:06,126 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'rts_pstor'}
2013-04-10 13:28:06,126 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'rts_pstor', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:28:06,126 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89d9a0c> about HardwareID('modalias', 'wmi:51F5230E-9677-46CD-A1CF-C0B23EE34DB7')
2013-04-10 13:28:06,126 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89d9a0c> about HardwareID('modalias', 'usb:v5986p0523d1402dcEFdsc02dp01ic0Eisc01ip00')
2013-04-10 13:28:06,126 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2013-04-10 13:28:06,126 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:28:06,126 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89d9a0c> about HardwareID('modalias', 'wmi:2651D9FD-911C-4B69-B94E-D0DED5963BD7')
2013-04-10 13:28:06,126 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89d9a0c> about HardwareID('modalias', 'platform:pcspkr')
2013-04-10 13:28:06,127 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2013-04-10 13:28:06,127 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:28:06,127 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2013-04-10 13:28:06,127 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:28:06,127 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89d9a0c> about HardwareID('modalias', 'platform:coretemp')
2013-04-10 13:28:06,127 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89d9a0c> about HardwareID('modalias', 'x86cpu:vendor:0000:family:0006:model:003A:feature:,0000,0001,0002,0003,0004,0005,0006,0007,0008,0009,000B,000C,000D,000E,000F,0010,0011,0013,0015,0016,0017,0018,0019,001A,001B,001C,001D,001F,0034,003B,003D,0066,0068,006B,006C,006D,0072,0076,0078,007C,0080,0081,0082,0083,0084,0085,0086,0087,0088,0089,008D,008E,008F,0091,0093,0094,0095,0097,0098,0099,009A,009B,009C,009D,009E,00C0,00E0,00E1,00E3,00E4,00E5,00E6,00E7,0100,0101,0102,0103,0104,0120,0127,0129')
2013-04-10 13:28:06,131 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'aesni_intel'}
2013-04-10 13:28:06,132 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'aesni_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:28:06,132 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'kvm_intel'}
2013-04-10 13:28:06,132 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'kvm_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:28:06,132 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'microcode'}
2013-04-10 13:28:06,132 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'microcode', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:28:06,132 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'coretemp'}
2013-04-10 13:28:06,132 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'coretemp', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:28:06,132 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89d9a0c> about HardwareID('modalias', 'wmi:98479A64-33F5-4E33-A707-8E251EBBC3A1')
2013-04-10 13:28:06,132 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89d9a0c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2013-04-10 13:28:06,132 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-10 13:28:06,132 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:28:06,132 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89d9a0c> about HardwareID('modalias', 'wmi:74F1EBB6-927A-4C7D-95DF-698E21E80EB5')
2013-04-10 13:28:06,132 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89d9a0c> about HardwareID('modalias', 'acpi:SMO1200:PNP0C31:')
2013-04-10 13:28:06,132 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89d9a0c> about HardwareID('modalias', 'input:b0003v5986p0523e1402-e0,1,kD4,ramlsfw')
2013-04-10 13:28:06,132 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-10 13:28:06,133 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:28:06,133 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-04-10 13:28:06,133 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:28:06,133 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89d9a0c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-04-10 13:28:06,133 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-10 13:28:06,133 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:28:06,133 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-04-10 13:28:06,133 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:28:06,133 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89d9a0c> about HardwareID('modalias', 'wmi:7364651A-132F-4FE7-ADAA-40C6C7EE2E3B')
2013-04-10 13:28:06,133 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c716ac> about HardwareID('modalias', 'pci:v00008086d00001E3Asv000017AAsd0000500Cbc07sc80i00')
2013-04-10 13:28:06,133 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c716ac> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,145,148,14A,14D,14E,14F,ra0,1,18,1C,2F,35,36,39,3A,mlsfw')
2013-04-10 13:28:06,133 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c716ac> about HardwareID('modalias', 'acpi:PNP0200:')
2013-04-10 13:28:06,133 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c716ac> about HardwareID('modalias', 'acpi:PNP0103:')
2013-04-10 13:28:06,133 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c716ac> about HardwareID('modalias', 'acpi:PNP0303:PNP0303:')
2013-04-10 13:28:06,133 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c716ac> about HardwareID('modalias', 'pci:v00008086d00000154sv000017AAsd0000500Cbc06sc00i00')
2013-04-10 13:28:06,133 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c716ac> about HardwareID('modalias', 'pci:v00008086d00001E31sv000017AAsd0000500Cbc0Csc03i30')
2013-04-10 13:28:06,133 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c716ac> about HardwareID('modalias', 'platform:thinkpad_hwmon')
2013-04-10 13:28:06,133 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c716ac> about HardwareID('modalias', 'input:b0019v17AAp5054e4101-e0,1,4,5,k71,72,73,8E,94,98,BF,C2,CD,D4,E0,E1,E3,E4,EC,EE,F0,F8,174,1D2,1DB,1DC,ram4,lsfw1,3,')
2013-04-10 13:28:06,133 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c716ac> about HardwareID('modalias', 'usb:v1D6Bp0002d0305dc09dsc00dp01ic09isc00ip00')
2013-04-10 13:28:06,134 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c716ac> about HardwareID('modalias', 'usb:v1D6Bp0003d0305dc09dsc00dp03ic09isc00ip00')
2013-04-10 13:28:06,134 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c716ac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2013-04-10 13:28:06,134 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c716ac> about HardwareID('modalias', 'platform:microcode')
2013-04-10 13:28:06,134 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c716ac> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2013-04-10 13:28:06,134 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c716ac> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-04-10 13:28:06,134 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c716ac> about HardwareID('modalias', 'platform:thinkpad_acpi')
2013-04-10 13:28:06,134 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c716ac> about HardwareID('modalias', 'acpi:LEN0051:PNP0F13:')
2013-04-10 13:28:06,134 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c716ac> about HardwareID('modalias', 'platform:eisa')
2013-04-10 13:28:06,134 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c716ac> about HardwareID('modalias', 'wmi:7FF47003-3B6C-4E5E-A227-E979824A85D1')
2013-04-10 13:28:06,134 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c716ac> about HardwareID('modalias', 'pci:v00008086d00001E26sv000017AAsd0000500Cbc0Csc03i20')
2013-04-10 13:28:06,134 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c716ac> about HardwareID('modalias', 'wmi:6A4B54EF-A5ED-4D33-9455-B0D9B48DF4B3')
2013-04-10 13:28:06,134 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c716ac> about HardwareID('modalias', 'usb:v0A5Cp21F3d0112dcFFdsc01dp01icFEisc01ip01')
2013-04-10 13:28:06,134 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c716ac> about HardwareID('modalias', 'serio:ty05pr00id00ex00')
2013-04-10 13:28:06,134 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c716ac> about HardwareID('modalias', 'pci:v00008086d00001E58sv000017AAsd0000500Cbc06sc01i00')
2013-04-10 13:28:06,134 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c716ac> about HardwareID('modalias', 'pci:v00008086d00001E03sv000017AAsd0000500Cbc01sc06i01')
2013-04-10 13:28:06,134 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c716ac> about HardwareID('modalias', 'pci:v00008086d00001E2Dsv000017AAsd0000500Cbc0Csc03i20')
2013-04-10 13:28:06,134 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c716ac> about HardwareID('modalias', 'acpi:INT3392:PNP0C02:')
2013-04-10 13:28:06,134 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c716ac> about HardwareID('modalias', 'pci:v00008086d00001E22sv000017AAsd0000500Cbc0Csc05i00')
2013-04-10 13:28:06,134 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c716ac> about HardwareID('modalias', 'acpi:PNP0B00:')
2013-04-10 13:28:06,134 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c716ac> about HardwareID('modalias', 'pci:v000014E4d00004359sv000014E4sd00000607bc02sc80i00')
2013-04-10 13:28:06,134 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c716ac> about HardwareID('modalias', 'usb:v1D6Bp0002d0305dc09dsc00dp00ic09isc00ip00')
2013-04-10 13:28:06,134 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c716ac> about HardwareID('modalias', 'acpi:PNP0C04:')
2013-04-10 13:28:06,135 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c716ac> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2013-04-10 13:28:06,135 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c716ac> about HardwareID('modalias', 'acpi:PNP0100:')
2013-04-10 13:28:06,135 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c716ac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2013-04-10 13:28:06,135 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c716ac> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2013-04-10 13:28:06,135 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c716ac> about HardwareID('modalias', 'usb:v0A5Cp21F3d0112dcFFdsc01dp01icFFiscFFipFF')
2013-04-10 13:28:06,135 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c716ac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2013-04-10 13:28:06,135 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c716ac> about HardwareID('modalias', 'wmi:E2BE5EE3-42DA-49DB-8378-1F5247388202')
2013-04-10 13:28:06,135 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c716ac> about HardwareID('modalias', 'acpi:PNP0C02:')
2013-04-10 13:28:06,135 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c716ac> about HardwareID('modalias', 'dmi:bvnLENOVO:bvrH6ET90WW(2.08):bd01/11/2013:svnLENOVO:pn3351CTO:pvrThinkPadT430u:rvnLENOVO:rn3351CTO:rvrNotDefined:cvnLENOVO:ct10:cvrNotAvailable:')
2013-04-10 13:28:06,135 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c716ac> about HardwareID('modalias', 'wmi:FCB424F1-075A-4E0E-BFC4-62F3E71771FA')
2013-04-10 13:28:06,135 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c716ac> about HardwareID('modalias', 'pci:v000010ECd00008168sv000017AAsd0000500Cbc02sc00i00')
2013-04-10 13:28:06,135 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c716ac> about HardwareID('modalias', 'wmi:7430019A-DCE9-4548-BAB0-9FDE0935CAFF')
2013-04-10 13:28:06,135 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c716ac> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2013-04-10 13:28:06,135 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c716ac> about HardwareID('modalias', 'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2013-04-10 13:28:06,135 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c716ac> about HardwareID('modalias', 'usb:v5986p0523d1402dcEFdsc02dp01ic0Eisc02ip00')
2013-04-10 13:28:06,135 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c716ac> about HardwareID('modalias', 'pci:v00008086d00000166sv000017AAsd0000500Cbc03sc00i00')
2013-04-10 13:28:06,135 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c716ac> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2013-04-10 13:28:06,135 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c716ac> about HardwareID('modalias', 'pci:v000010ECd00005209sv000010ECsd00005209bc08sc05i00')
2013-04-10 13:28:06,135 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c716ac> about HardwareID('modalias', 'acpi:PNP0000:')
2013-04-10 13:28:06,135 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c716ac> about HardwareID('modalias', 'usb:v0A5Cp21F3d0112dcFFdsc01dp01icFFisc01ip01')
2013-04-10 13:28:06,135 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c716ac> about HardwareID('modalias', 'wmi:8ADB159E-1E32-455C-BC93-308A7ED98246')
2013-04-10 13:28:06,135 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c716ac> about HardwareID('modalias', 'pci:v00008086d00001E20sv000017AAsd0000500Cbc04sc03i00')
2013-04-10 13:28:06,135 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c716ac> about HardwareID('modalias', 'acpi:INT0800:')
2013-04-10 13:28:06,136 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c716ac> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2013-04-10 13:28:06,136 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c716ac> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-04-10 13:28:06,136 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c716ac> about HardwareID('modalias', 'wmi:7EEF04FF-4328-447C-B5BB-D449925D538D')
2013-04-10 13:28:06,136 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c716ac> about HardwareID('modalias', 'pci:v000010ECd00005209sv000010ECsd00005209bcFFsc00i00')
2013-04-10 13:28:06,136 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c716ac> about HardwareID('modalias', 'wmi:51F5230E-9677-46CD-A1CF-C0B23EE34DB7')
2013-04-10 13:28:06,136 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c716ac> about HardwareID('modalias', 'usb:v5986p0523d1402dcEFdsc02dp01ic0Eisc01ip00')
2013-04-10 13:28:06,136 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c716ac> about HardwareID('modalias', 'wmi:2651D9FD-911C-4B69-B94E-D0DED5963BD7')
2013-04-10 13:28:06,136 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c716ac> about HardwareID('modalias', 'platform:pcspkr')
2013-04-10 13:28:06,136 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c716ac> about HardwareID('modalias', 'platform:coretemp')
2013-04-10 13:28:06,136 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c716ac> about HardwareID('modalias', 'x86cpu:vendor:0000:family:0006:model:003A:feature:,0000,0001,0002,0003,0004,0005,0006,0007,0008,0009,000B,000C,000D,000E,000F,0010,0011,0013,0015,0016,0017,0018,0019,001A,001B,001C,001D,001F,0034,003B,003D,0066,0068,006B,006C,006D,0072,0076,0078,007C,0080,0081,0082,0083,0084,0085,0086,0087,0088,0089,008D,008E,008F,0091,0093,0094,0095,0097,0098,0099,009A,009B,009C,009D,009E,00C0,00E0,00E1,00E3,00E4,00E5,00E6,00E7,0100,0101,0102,0103,0104,0120,0127,0129')
2013-04-10 13:28:06,136 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c716ac> about HardwareID('modalias', 'wmi:98479A64-33F5-4E33-A707-8E251EBBC3A1')
2013-04-10 13:28:06,136 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c716ac> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2013-04-10 13:28:06,136 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c716ac> about HardwareID('modalias', 'wmi:74F1EBB6-927A-4C7D-95DF-698E21E80EB5')
2013-04-10 13:28:06,136 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c716ac> about HardwareID('modalias', 'acpi:SMO1200:PNP0C31:')
2013-04-10 13:28:06,136 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c716ac> about HardwareID('modalias', 'input:b0003v5986p0523e1402-e0,1,kD4,ramlsfw')
2013-04-10 13:28:06,136 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c716ac> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-04-10 13:28:06,136 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8c716ac> about HardwareID('modalias', 'wmi:7364651A-132F-4FE7-ADAA-40C6C7EE2E3B')
2013-04-10 13:28:06,170 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-04-10 13:28:06,180 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-04-10 13:28:06,198 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-04-10 13:28:06,202 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-04-10 13:28:06,238 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-04-10 13:28:06,242 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-04-10 13:28:12,921 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-04-10 13:28:16,482 DEBUG: Installing package: linux-headers-generic
2013-04-10 13:28:16,793 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-10 13:28:16,794 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-10 13:28:16,808 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-10 13:28:16,847 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.000000
2013-04-10 13:28:16,895 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 0.274682
2013-04-10 13:28:17,397 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 67.615081
2013-04-10 13:28:17,568 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 99.737210
2013-04-10 13:28:17,568 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='i386' id:1638L> 100.000000
2013-04-10 13:28:17,765 DEBUG: install progress dpkg-exec 0.000000
2013-04-10 13:28:17,941 DEBUG: install progress linux-headers-3.2.0-23-generic 0.000000
2013-04-10 13:28:18,042 DEBUG: install progress linux-headers-3.2.0-23-generic 10.000000
2013-04-10 13:28:19,753 DEBUG: install progress linux-headers-3.2.0-23-generic 20.000000
2013-04-10 13:28:19,788 DEBUG: install progress linux-headers-3.2.0-23-generic 30.000000
2013-04-10 13:28:19,854 DEBUG: install progress linux-headers-generic 30.000000
2013-04-10 13:28:19,916 DEBUG: install progress linux-headers-generic 40.000000
2013-04-10 13:28:19,916 DEBUG: install progress linux-headers-generic 50.000000
2013-04-10 13:28:19,925 DEBUG: install progress linux-headers-generic 60.000000
2013-04-10 13:28:20,000 DEBUG: install progress dpkg-exec 60.000000
2013-04-10 13:28:20,031 DEBUG: install progress linux-headers-3.2.0-23-generic 60.000000
2013-04-10 13:28:20,046 DEBUG: install progress linux-headers-3.2.0-23-generic 70.000000
2013-04-10 13:28:38,558 DEBUG: install progress linux-headers-3.2.0-23-generic 80.000000
2013-04-10 13:28:38,568 DEBUG: install progress linux-headers-generic 80.000000
2013-04-10 13:28:38,577 DEBUG: install progress linux-headers-generic 90.000000
2013-04-10 13:28:38,586 DEBUG: install progress linux-headers-generic 100.000000
2013-04-10 13:28:38,888 DEBUG: Selecting previously unselected package linux-headers-3.2.0-23-generic.
(Reading database ... 177492 files and directories currently installed.)
Unpacking linux-headers-3.2.0-23-generic (from .../linux-headers-3.2.0-23-generic_3.2.0-23.36_i386.deb) ...
Selecting previously unselected package linux-headers-generic.
Unpacking linux-headers-generic (from .../linux-headers-generic_3.2.0.23.25_i386.deb) ...
Setting up linux-headers-3.2.0-23-generic (3.2.0-23.36) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.2.0-23-generic /boot/vmlinuz-3.2.0-23-generic
Setting up linux-headers-generic (3.2.0.23.25) ...

2013-04-10 13:28:39,017 DEBUG: Installing package: bcmwl-kernel-source
2013-04-10 13:28:39,338 DEBUG: download progress <Package: name:'bcmwl-kernel-source' architecture='i386' id:12317L> 0.000000
2013-04-10 13:28:39,339 DEBUG: download progress <Package: name:'bcmwl-kernel-source' architecture='i386' id:12317L> 0.000000
2013-04-10 13:28:39,355 DEBUG: download progress <Package: name:'bcmwl-kernel-source' architecture='i386' id:12317L> 0.000000
2013-04-10 13:28:39,394 DEBUG: download progress <Package: name:'bcmwl-kernel-source' architecture='i386' id:12317L> 0.000000
2013-04-10 13:28:39,439 DEBUG: download progress <Package: name:'bcmwl-kernel-source' architecture='i386' id:12317L> 0.455799
2013-04-10 13:28:39,940 DEBUG: download progress <Package: name:'bcmwl-kernel-source' architecture='i386' id:12317L> 83.060832
2013-04-10 13:28:40,010 DEBUG: download progress <Package: name:'bcmwl-kernel-source' architecture='i386' id:12317L> 100.000000
2013-04-10 13:28:40,187 DEBUG: install progress dpkg-exec 0.000000
2013-04-10 13:28:40,383 DEBUG: install progress bcmwl-kernel-source 0.000000
2013-04-10 13:28:40,484 DEBUG: install progress bcmwl-kernel-source 20.000000
2013-04-10 13:28:40,501 DEBUG: install progress bcmwl-kernel-source 40.000000
2013-04-10 13:28:40,510 DEBUG: install progress bcmwl-kernel-source 60.000000
2013-04-10 13:28:40,594 DEBUG: install progress dpkg-exec 60.000000
2013-04-10 13:28:40,626 DEBUG: install progress bcmwl-kernel-source 60.000000
2013-04-10 13:28:40,649 DEBUG: install progress bcmwl-kernel-source 80.000000
2013-04-10 13:28:47,957 DEBUG: install progress bcmwl-kernel-source 100.000000
2013-04-10 13:28:47,996 DEBUG: install progress initramfs-tools 100.000000
2013-04-10 13:29:01,331 DEBUG: Selecting previously unselected package bcmwl-kernel-source.
(Reading database ... 185898 files and directories currently installed.)
Unpacking bcmwl-kernel-source (from .../bcmwl-kernel-source_5.100.82.38+bdcom-0ubuntu6_i386.deb) ...
Setting up bcmwl-kernel-source (5.100.82.38+bdcom-0ubuntu6) ...
Loading new bcmwl-5.100.82.38+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 3.5.0-23-generic
Building for architecture i686
Building initial module for 3.5.0-23-generic
ERROR (dkms apport): kernel package linux-headers-3.5.0-23-generic is not supported
Error! Bad return status for module build on kernel: 3.5.0-23-generic (i686)
Consult /var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/make.log for more information.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.5.0-23-generic

2013-04-10 13:29:01,469 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2013-04-10 13:29:01,471 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2013-04-10 13:29:01,507 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-04-10 13:30:37,075 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-04-10 13:30:37,103 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-04-10 13:30:37,147 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-04-10 13:30:41,992 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-04-10 13:30:44,574 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-04-10 13:30:44,819 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2013-04-10 13:30:44,819 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2013-04-10 13:30:44,845 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-04-10 13:31:35,897 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-04-10 13:31:35,929 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-04-10 13:31:35,981 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-04-10 13:31:38,468 DEBUG: Shutting down
2013-04-10 13:31:39,723 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xa23da0c>
2013-04-10 13:31:40,928 DEBUG: reading modalias file /lib/modules/3.5.0-23-generic/modules.alias
2013-04-10 13:31:40,995 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2013-04-10 13:31:40,996 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2013-04-10 13:31:41,042 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2013-04-10 13:31:41,049 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2013-04-10 13:31:41,076 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2013-04-10 13:31:41,077 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2013-04-10 13:31:41,077 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2013-04-10 13:31:41,085 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2013-04-10 13:31:41,086 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2013-04-10 13:31:41,086 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2013-04-10 13:31:41,086 DEBUG: loading custom handler /usr/share/jockey/handlers/cdv.py
2013-04-10 13:31:41,096 WARNING: modinfo for module cedarview_gfx failed: ERROR: modinfo: could not find module cedarview_gfx

2013-04-10 13:31:41,097 DEBUG: Instantiated Handler subclass __builtin__.CdvDriver from name CdvDriver
2013-04-10 13:31:41,097 DEBUG: cdv.available: falling back to default
2013-04-10 13:31:41,245 DEBUG: XorgDriverHandler(cedarview_gfx, cedarview-graphics-drivers, None): Disabling as package is not compatible with Q-LTS X.org
2013-04-10 13:31:41,245 DEBUG: Intel Cedarview graphics driver not available
2013-04-10 13:31:41,246 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2013-04-10 13:31:41,258 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2013-04-10 13:31:41,266 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2013-04-10 13:31:41,268 DEBUG: Disabling Nvidia driver on intel/hybrid system
2013-04-10 13:31:41,269 DEBUG: NVIDIA accelerated graphics driver not available
2013-04-10 13:31:41,275 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2013-04-10 13:31:41,282 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2013-04-10 13:31:41,284 DEBUG: Disabling Nvidia driver on intel/hybrid system
2013-04-10 13:31:41,284 DEBUG: NVIDIA accelerated graphics driver not available
2013-04-10 13:31:41,290 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2013-04-10 13:31:41,297 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2013-04-10 13:31:41,299 DEBUG: Disabling Nvidia driver on intel/hybrid system
2013-04-10 13:31:41,299 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2013-04-10 13:31:41,305 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2013-04-10 13:31:41,312 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2013-04-10 13:31:41,314 DEBUG: Disabling Nvidia driver on intel/hybrid system
2013-04-10 13:31:41,314 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2013-04-10 13:31:41,320 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2013-04-10 13:31:41,328 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2013-04-10 13:31:41,329 DEBUG: Disabling Nvidia driver on intel/hybrid system
2013-04-10 13:31:41,330 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2013-04-10 13:31:41,336 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2013-04-10 13:31:41,343 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2013-04-10 13:31:41,345 DEBUG: Disabling Nvidia driver on intel/hybrid system
2013-04-10 13:31:41,345 DEBUG: NVIDIA accelerated graphics driver not available
2013-04-10 13:31:41,351 WARNING: modinfo for module nvidia_experimental_310 failed: ERROR: modinfo: could not find module nvidia_experimental_310

2013-04-10 13:31:41,383 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverExperimental310 from name NvidiaDriverExperimental310
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 972, in get_handlers
    desc = inst.name()
  File "/usr/lib/python2.7/dist-packages/jockey/handlers.py", line 108, in name
    self._package_defaults()
  File "/usr/lib/python2.7/dist-packages/jockey/handlers.py", line 93, in _package_defaults
    (distro_name, distro_desc) = OSLib.inst.package_description(self.package)
  File "/usr/lib/python2.7/dist-packages/jockey/oslib.py", line 216, in package_description
    raise ValueError('package %s does not exist' % package)
ValueError: package nvidia-experimental-310 does not exist
2013-04-10 13:31:41,392 WARNING: modinfo for module nvidia_experimental_304 failed: ERROR: modinfo: could not find module nvidia_experimental_304

2013-04-10 13:31:41,424 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverExperimental304 from name NvidiaDriverExperimental304
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 972, in get_handlers
    desc = inst.name()
  File "/usr/lib/python2.7/dist-packages/jockey/handlers.py", line 108, in name
    self._package_defaults()
  File "/usr/lib/python2.7/dist-packages/jockey/handlers.py", line 93, in _package_defaults
    (distro_name, distro_desc) = OSLib.inst.package_description(self.package)
  File "/usr/lib/python2.7/dist-packages/jockey/oslib.py", line 216, in package_description
    raise ValueError('package %s does not exist' % package)
ValueError: package nvidia-experimental-304 does not exist
2013-04-10 13:31:41,425 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2013-04-10 13:31:41,452 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2013-04-10 13:31:41,467 DEBUG: Software modem not available
2013-04-10 13:31:41,467 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2013-04-10 13:31:41,477 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2013-04-10 13:31:41,482 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2013-04-10 13:31:41,627 DEBUG: XorgDriverHandler(omapdrm_pvr, pvr-omap4, None): Disabling as package is not compatible with Q-LTS X.org
2013-04-10 13:31:41,627 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2013-04-10 13:31:41,627 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2013-04-10 13:31:41,630 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2013-04-10 13:31:41,630 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2013-04-10 13:31:41,641 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2013-04-10 13:31:41,642 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2013-04-10 13:31:41,661 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2013-04-10 13:31:41,662 DEBUG: Firmware for DVB cards not available
2013-04-10 13:31:41,662 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2013-04-10 13:31:41,671 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2013-04-10 13:31:41,679 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2013-04-10 13:31:41,679 DEBUG: fglrx.available: falling back to default
2013-04-10 13:31:41,819 DEBUG: XorgDriverHandler(fglrx_updates, fglrx-updates, None): Disabling as package is not compatible with Q-LTS X.org
2013-04-10 13:31:41,820 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) not available
2013-04-10 13:31:41,822 WARNING: modinfo for module fglrx_experimental_9 failed: ERROR: modinfo: could not find module fglrx_experimental_9

2013-04-10 13:31:41,839 DEBUG: Could not instantiate Handler subclass __builtin__.FglrxDriverExperimental9 from name FglrxDriverExperimental9
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 972, in get_handlers
    desc = inst.name()
  File "/usr/lib/python2.7/dist-packages/jockey/handlers.py", line 108, in name
    self._package_defaults()
  File "/usr/lib/python2.7/dist-packages/jockey/handlers.py", line 93, in _package_defaults
    (distro_name, distro_desc) = OSLib.inst.package_description(self.package)
  File "/usr/lib/python2.7/dist-packages/jockey/oslib.py", line 216, in package_description
    raise ValueError('package %s does not exist' % package)
ValueError: package fglrx-experimental-9 does not exist
2013-04-10 13:31:41,846 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2013-04-10 13:31:41,849 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2013-04-10 13:31:41,850 DEBUG: fglrx.available: falling back to default
2013-04-10 13:31:41,970 DEBUG: XorgDriverHandler(fglrx, fglrx, None): Disabling as package is not compatible with Q-LTS X.org
2013-04-10 13:31:41,970 DEBUG: ATI/AMD proprietary FGLRX graphics driver not available
2013-04-10 13:31:41,971 DEBUG: all custom handlers loaded
2013-04-10 13:31:41,971 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa23da0c> about HardwareID('modalias', 'pci:v00008086d00001E3Asv000017AAsd0000500Cbc07sc80i00')
2013-04-10 13:31:42,188 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mei'}
2013-04-10 13:31:42,254 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mei', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:31:42,254 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa23da0c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,145,148,14A,14D,14E,14F,ra0,1,18,1C,2F,35,36,39,3A,mlsfw')
2013-04-10 13:31:42,258 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-10 13:31:42,258 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:31:42,258 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2013-04-10 13:31:42,258 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:31:42,258 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2013-04-10 13:31:42,258 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:31:42,258 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2013-04-10 13:31:42,258 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:31:42,258 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-04-10 13:31:42,258 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:31:42,258 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa23da0c> about HardwareID('modalias', 'acpi:PNP0200:')
2013-04-10 13:31:42,259 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa23da0c> about HardwareID('modalias', 'acpi:PNP0103:')
2013-04-10 13:31:42,259 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa23da0c> about HardwareID('modalias', 'acpi:PNP0303:PNP0303:')
2013-04-10 13:31:42,259 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa23da0c> about HardwareID('modalias', 'pci:v00008086d00000154sv000017AAsd0000500Cbc06sc00i00')
2013-04-10 13:31:42,261 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa23da0c> about HardwareID('modalias', 'pci:v00008086d00001E31sv000017AAsd0000500Cbc0Csc03i30')
2013-04-10 13:31:42,263 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa23da0c> about HardwareID('modalias', 'platform:thinkpad_hwmon')
2013-04-10 13:31:42,264 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa23da0c> about HardwareID('modalias', 'input:b0019v17AAp5054e4101-e0,1,4,5,k71,72,73,8E,94,98,BF,C2,CD,D4,E0,E1,E3,E4,EC,EE,F0,F8,174,1D2,1DB,1DC,ram4,lsfw1,3,')
2013-04-10 13:31:42,264 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-10 13:31:42,264 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:31:42,264 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-04-10 13:31:42,264 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:31:42,264 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa23da0c> about HardwareID('modalias', 'usb:v1D6Bp0002d0305dc09dsc00dp01ic09isc00ip00')
2013-04-10 13:31:42,274 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa23da0c> about HardwareID('modalias', 'usb:v1D6Bp0003d0305dc09dsc00dp03ic09isc00ip00')
2013-04-10 13:31:42,274 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa23da0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2013-04-10 13:31:42,274 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-10 13:31:42,274 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:31:42,274 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa23da0c> about HardwareID('modalias', 'platform:microcode')
2013-04-10 13:31:42,274 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa23da0c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2013-04-10 13:31:42,274 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa23da0c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-04-10 13:31:42,274 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa23da0c> about HardwareID('modalias', 'platform:thinkpad_acpi')
2013-04-10 13:31:42,275 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa23da0c> about HardwareID('modalias', 'acpi:LEN0051:PNP0F13:')
2013-04-10 13:31:42,275 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa23da0c> about HardwareID('modalias', 'platform:eisa')
2013-04-10 13:31:42,275 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa23da0c> about HardwareID('modalias', 'wmi:7FF47003-3B6C-4E5E-A227-E979824A85D1')
2013-04-10 13:31:42,275 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa23da0c> about HardwareID('modalias', 'pci:v00008086d00001E26sv000017AAsd0000500Cbc0Csc03i20')
2013-04-10 13:31:42,277 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa23da0c> about HardwareID('modalias', 'wmi:6A4B54EF-A5ED-4D33-9455-B0D9B48DF4B3')
2013-04-10 13:31:42,277 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa23da0c> about HardwareID('modalias', 'usb:v0A5Cp21F3d0112dcFFdsc01dp01icFEisc01ip01')
2013-04-10 13:31:42,279 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa23da0c> about HardwareID('modalias', 'serio:ty05pr00id00ex00')
2013-04-10 13:31:42,284 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2013-04-10 13:31:42,285 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:31:42,285 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa23da0c> about HardwareID('modalias', 'pci:v00008086d00001E58sv000017AAsd0000500Cbc06sc01i00')
2013-04-10 13:31:42,287 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'lpc_ich'}
2013-04-10 13:31:42,287 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'lpc_ich', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:31:42,287 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa23da0c> about HardwareID('modalias', 'pci:v00008086d00001E03sv000017AAsd0000500Cbc01sc06i01')
2013-04-10 13:31:42,289 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa23da0c> about HardwareID('modalias', 'pci:v00008086d00001E2Dsv000017AAsd0000500Cbc0Csc03i20')
2013-04-10 13:31:42,291 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa23da0c> about HardwareID('modalias', 'acpi:INT3392:PNP0C02:')
2013-04-10 13:31:42,291 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa23da0c> about HardwareID('modalias', 'pci:v00008086d00001E22sv000017AAsd0000500Cbc0Csc05i00')
2013-04-10 13:31:42,293 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801'}
2013-04-10 13:31:42,293 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:31:42,293 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa23da0c> about HardwareID('modalias', 'acpi:PNP0B00:')
2013-04-10 13:31:42,294 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa23da0c> about HardwareID('modalias', 'pci:v000014E4d00004359sv000014E4sd00000607bc02sc80i00')
2013-04-10 13:31:42,325 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'wl', 'package': 'bcmwl-kernel-source'}
2013-04-10 13:31:42,325 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-04-10 13:31:42,325 DEBUG: found match in handler pool kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2013-04-10 13:31:42,330 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2013-04-10 13:31:42,331 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-04-10 13:31:42,331 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2013-04-10 13:31:42,331 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa23da0c> about HardwareID('modalias', 'usb:v1D6Bp0002d0305dc09dsc00dp00ic09isc00ip00')
2013-04-10 13:31:42,331 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa23da0c> about HardwareID('modalias', 'acpi:PNP0C04:')
2013-04-10 13:31:42,331 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa23da0c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2013-04-10 13:31:42,332 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2013-04-10 13:31:42,332 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:31:42,332 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2013-04-10 13:31:42,332 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:31:42,332 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa23da0c> about HardwareID('modalias', 'acpi:PNP0100:')
2013-04-10 13:31:42,332 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa23da0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2013-04-10 13:31:42,332 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-10 13:31:42,332 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:31:42,332 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa23da0c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2013-04-10 13:31:42,332 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-10 13:31:42,332 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:31:42,332 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-04-10 13:31:42,332 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:31:42,332 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa23da0c> about HardwareID('modalias', 'usb:v0A5Cp21F3d0112dcFFdsc01dp01icFFiscFFipFF')
2013-04-10 13:31:42,333 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa23da0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2013-04-10 13:31:42,333 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-10 13:31:42,333 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:31:42,333 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa23da0c> about HardwareID('modalias', 'wmi:E2BE5EE3-42DA-49DB-8378-1F5247388202')
2013-04-10 13:31:42,333 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa23da0c> about HardwareID('modalias', 'acpi:PNP0C02:')
2013-04-10 13:31:42,333 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa23da0c> about HardwareID('modalias', 'dmi:bvnLENOVO:bvrH6ET90WW(2.08):bd01/11/2013:svnLENOVO:pn3351CTO:pvrThinkPadT430u:rvnLENOVO:rn3351CTO:rvrNotDefined:cvnLENOVO:ct10:cvrNotAvailable:')
2013-04-10 13:31:42,342 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa23da0c> about HardwareID('modalias', 'wmi:FCB424F1-075A-4E0E-BFC4-62F3E71771FA')
2013-04-10 13:31:42,342 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa23da0c> about HardwareID('modalias', 'pci:v000010ECd00008168sv000017AAsd0000500Cbc02sc00i00')
2013-04-10 13:31:42,348 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2013-04-10 13:31:42,349 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:31:42,349 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa23da0c> about HardwareID('modalias', 'wmi:7430019A-DCE9-4548-BAB0-9FDE0935CAFF')
2013-04-10 13:31:42,349 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa23da0c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2013-04-10 13:31:42,349 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-10 13:31:42,349 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:31:42,349 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-04-10 13:31:42,349 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:31:42,349 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa23da0c> about HardwareID('modalias', 'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2013-04-10 13:31:42,349 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa23da0c> about HardwareID('modalias', 'usb:v5986p0523d1402dcEFdsc02dp01ic0Eisc02ip00')
2013-04-10 13:31:42,350 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa23da0c> about HardwareID('modalias', 'pci:v00008086d00000166sv000017AAsd0000500Cbc03sc00i00')
2013-04-10 13:31:42,352 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i915'}
2013-04-10 13:31:42,352 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:31:42,352 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa23da0c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2013-04-10 13:31:42,352 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-10 13:31:42,352 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:31:42,353 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-04-10 13:31:42,353 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:31:42,353 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa23da0c> about HardwareID('modalias', 'pci:v000010ECd00005209sv000010ECsd00005209bc08sc05i00')
2013-04-10 13:31:42,353 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci'}
2013-04-10 13:31:42,353 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:31:42,353 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa23da0c> about HardwareID('modalias', 'acpi:PNP0000:')
2013-04-10 13:31:42,353 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa23da0c> about HardwareID('modalias', 'usb:v0A5Cp21F3d0112dcFFdsc01dp01icFFisc01ip01')
2013-04-10 13:31:42,353 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2013-04-10 13:31:42,353 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:31:42,353 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa23da0c> about HardwareID('modalias', 'wmi:8ADB159E-1E32-455C-BC93-308A7ED98246')
2013-04-10 13:31:42,353 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa23da0c> about HardwareID('modalias', 'pci:v00008086d00001E20sv000017AAsd0000500Cbc04sc03i00')
2013-04-10 13:31:42,356 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-04-10 13:31:42,356 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:31:42,356 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-04-10 13:31:42,356 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:31:42,356 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa23da0c> about HardwareID('modalias', 'acpi:INT0800:')
2013-04-10 13:31:42,356 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa23da0c> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2013-04-10 13:31:42,356 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa23da0c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-04-10 13:31:42,356 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa23da0c> about HardwareID('modalias', 'wmi:7EEF04FF-4328-447C-B5BB-D449925D538D')
2013-04-10 13:31:42,356 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa23da0c> about HardwareID('modalias', 'pci:v000010ECd00005209sv000010ECsd00005209bcFFsc00i00')
2013-04-10 13:31:42,357 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'rts_pstor'}
2013-04-10 13:31:42,357 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'rts_pstor', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:31:42,357 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa23da0c> about HardwareID('modalias', 'wmi:51F5230E-9677-46CD-A1CF-C0B23EE34DB7')
2013-04-10 13:31:42,357 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa23da0c> about HardwareID('modalias', 'usb:v5986p0523d1402dcEFdsc02dp01ic0Eisc01ip00')
2013-04-10 13:31:42,357 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2013-04-10 13:31:42,357 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:31:42,357 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa23da0c> about HardwareID('modalias', 'wmi:2651D9FD-911C-4B69-B94E-D0DED5963BD7')
2013-04-10 13:31:42,357 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa23da0c> about HardwareID('modalias', 'platform:pcspkr')
2013-04-10 13:31:42,357 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2013-04-10 13:31:42,358 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:31:42,358 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2013-04-10 13:31:42,358 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:31:42,358 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa23da0c> about HardwareID('modalias', 'platform:coretemp')
2013-04-10 13:31:42,358 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa23da0c> about HardwareID('modalias', 'x86cpu:vendor:0000:family:0006:model:003A:feature:,0000,0001,0002,0003,0004,0005,0006,0007,0008,0009,000B,000C,000D,000E,000F,0010,0011,0013,0015,0016,0017,0018,0019,001A,001B,001C,001D,001F,0034,003B,003D,0066,0068,006B,006C,006D,0072,0076,0078,007C,0080,0081,0082,0083,0084,0085,0086,0087,0088,0089,008D,008E,008F,0091,0093,0094,0095,0097,0098,0099,009A,009B,009C,009D,009E,00C0,00E0,00E1,00E3,00E4,00E5,00E6,00E7,0100,0101,0102,0103,0104,0120,0127,0129')
2013-04-10 13:31:42,362 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'aesni_intel'}
2013-04-10 13:31:42,362 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'aesni_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:31:42,362 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'kvm_intel'}
2013-04-10 13:31:42,363 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'kvm_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:31:42,363 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'microcode'}
2013-04-10 13:31:42,363 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'microcode', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:31:42,363 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'coretemp'}
2013-04-10 13:31:42,363 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'coretemp', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:31:42,363 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa23da0c> about HardwareID('modalias', 'wmi:98479A64-33F5-4E33-A707-8E251EBBC3A1')
2013-04-10 13:31:42,363 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa23da0c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2013-04-10 13:31:42,363 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-10 13:31:42,363 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:31:42,363 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa23da0c> about HardwareID('modalias', 'wmi:74F1EBB6-927A-4C7D-95DF-698E21E80EB5')
2013-04-10 13:31:42,363 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa23da0c> about HardwareID('modalias', 'acpi:SMO1200:PNP0C31:')
2013-04-10 13:31:42,363 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa23da0c> about HardwareID('modalias', 'input:b0003v5986p0523e1402-e0,1,kD4,ramlsfw')
2013-04-10 13:31:42,364 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-10 13:31:42,364 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:31:42,364 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-04-10 13:31:42,364 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:31:42,364 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa23da0c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-04-10 13:31:42,364 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-10 13:31:42,364 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:31:42,364 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-04-10 13:31:42,364 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:31:42,364 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa23da0c> about HardwareID('modalias', 'wmi:7364651A-132F-4FE7-ADAA-40C6C7EE2E3B')
2013-04-10 13:31:42,364 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa4d5aec> about HardwareID('modalias', 'pci:v00008086d00001E3Asv000017AAsd0000500Cbc07sc80i00')
2013-04-10 13:31:42,364 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa4d5aec> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,145,148,14A,14D,14E,14F,ra0,1,18,1C,2F,35,36,39,3A,mlsfw')
2013-04-10 13:31:42,364 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa4d5aec> about HardwareID('modalias', 'acpi:PNP0200:')
2013-04-10 13:31:42,364 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa4d5aec> about HardwareID('modalias', 'acpi:PNP0103:')
2013-04-10 13:31:42,364 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa4d5aec> about HardwareID('modalias', 'acpi:PNP0303:PNP0303:')
2013-04-10 13:31:42,364 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa4d5aec> about HardwareID('modalias', 'pci:v00008086d00000154sv000017AAsd0000500Cbc06sc00i00')
2013-04-10 13:31:42,364 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa4d5aec> about HardwareID('modalias', 'pci:v00008086d00001E31sv000017AAsd0000500Cbc0Csc03i30')
2013-04-10 13:31:42,365 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa4d5aec> about HardwareID('modalias', 'platform:thinkpad_hwmon')
2013-04-10 13:31:42,365 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa4d5aec> about HardwareID('modalias', 'input:b0019v17AAp5054e4101-e0,1,4,5,k71,72,73,8E,94,98,BF,C2,CD,D4,E0,E1,E3,E4,EC,EE,F0,F8,174,1D2,1DB,1DC,ram4,lsfw1,3,')
2013-04-10 13:31:42,365 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa4d5aec> about HardwareID('modalias', 'usb:v1D6Bp0002d0305dc09dsc00dp01ic09isc00ip00')
2013-04-10 13:31:42,365 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa4d5aec> about HardwareID('modalias', 'usb:v1D6Bp0003d0305dc09dsc00dp03ic09isc00ip00')
2013-04-10 13:31:42,365 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa4d5aec> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2013-04-10 13:31:42,365 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa4d5aec> about HardwareID('modalias', 'platform:microcode')
2013-04-10 13:31:42,365 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa4d5aec> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2013-04-10 13:31:42,365 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa4d5aec> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-04-10 13:31:42,365 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa4d5aec> about HardwareID('modalias', 'platform:thinkpad_acpi')
2013-04-10 13:31:42,365 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa4d5aec> about HardwareID('modalias', 'acpi:LEN0051:PNP0F13:')
2013-04-10 13:31:42,365 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa4d5aec> about HardwareID('modalias', 'platform:eisa')
2013-04-10 13:31:42,365 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa4d5aec> about HardwareID('modalias', 'wmi:7FF47003-3B6C-4E5E-A227-E979824A85D1')
2013-04-10 13:31:42,365 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa4d5aec> about HardwareID('modalias', 'pci:v00008086d00001E26sv000017AAsd0000500Cbc0Csc03i20')
2013-04-10 13:31:42,365 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa4d5aec> about HardwareID('modalias', 'wmi:6A4B54EF-A5ED-4D33-9455-B0D9B48DF4B3')
2013-04-10 13:31:42,365 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa4d5aec> about HardwareID('modalias', 'usb:v0A5Cp21F3d0112dcFFdsc01dp01icFEisc01ip01')
2013-04-10 13:31:42,365 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa4d5aec> about HardwareID('modalias', 'serio:ty05pr00id00ex00')
2013-04-10 13:31:42,365 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa4d5aec> about HardwareID('modalias', 'pci:v00008086d00001E58sv000017AAsd0000500Cbc06sc01i00')
2013-04-10 13:31:42,365 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa4d5aec> about HardwareID('modalias', 'pci:v00008086d00001E03sv000017AAsd0000500Cbc01sc06i01')
2013-04-10 13:31:42,365 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa4d5aec> about HardwareID('modalias', 'pci:v00008086d00001E2Dsv000017AAsd0000500Cbc0Csc03i20')
2013-04-10 13:31:42,365 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa4d5aec> about HardwareID('modalias', 'acpi:INT3392:PNP0C02:')
2013-04-10 13:31:42,365 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa4d5aec> about HardwareID('modalias', 'pci:v00008086d00001E22sv000017AAsd0000500Cbc0Csc05i00')
2013-04-10 13:31:42,366 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa4d5aec> about HardwareID('modalias', 'acpi:PNP0B00:')
2013-04-10 13:31:42,366 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa4d5aec> about HardwareID('modalias', 'pci:v000014E4d00004359sv000014E4sd00000607bc02sc80i00')
2013-04-10 13:31:42,366 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa4d5aec> about HardwareID('modalias', 'usb:v1D6Bp0002d0305dc09dsc00dp00ic09isc00ip00')
2013-04-10 13:31:42,366 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa4d5aec> about HardwareID('modalias', 'acpi:PNP0C04:')
2013-04-10 13:31:42,366 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa4d5aec> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2013-04-10 13:31:42,366 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa4d5aec> about HardwareID('modalias', 'acpi:PNP0100:')
2013-04-10 13:31:42,366 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa4d5aec> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2013-04-10 13:31:42,366 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa4d5aec> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2013-04-10 13:31:42,366 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa4d5aec> about HardwareID('modalias', 'usb:v0A5Cp21F3d0112dcFFdsc01dp01icFFiscFFipFF')
2013-04-10 13:31:42,366 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa4d5aec> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2013-04-10 13:31:42,366 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa4d5aec> about HardwareID('modalias', 'wmi:E2BE5EE3-42DA-49DB-8378-1F5247388202')
2013-04-10 13:31:42,366 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa4d5aec> about HardwareID('modalias', 'acpi:PNP0C02:')
2013-04-10 13:31:42,366 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa4d5aec> about HardwareID('modalias', 'dmi:bvnLENOVO:bvrH6ET90WW(2.08):bd01/11/2013:svnLENOVO:pn3351CTO:pvrThinkPadT430u:rvnLENOVO:rn3351CTO:rvrNotDefined:cvnLENOVO:ct10:cvrNotAvailable:')
2013-04-10 13:31:42,366 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa4d5aec> about HardwareID('modalias', 'wmi:FCB424F1-075A-4E0E-BFC4-62F3E71771FA')
2013-04-10 13:31:42,366 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa4d5aec> about HardwareID('modalias', 'pci:v000010ECd00008168sv000017AAsd0000500Cbc02sc00i00')
2013-04-10 13:31:42,366 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa4d5aec> about HardwareID('modalias', 'wmi:7430019A-DCE9-4548-BAB0-9FDE0935CAFF')
2013-04-10 13:31:42,366 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa4d5aec> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2013-04-10 13:31:42,366 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa4d5aec> about HardwareID('modalias', 'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2013-04-10 13:31:42,366 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa4d5aec> about HardwareID('modalias', 'usb:v5986p0523d1402dcEFdsc02dp01ic0Eisc02ip00')
2013-04-10 13:31:42,366 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa4d5aec> about HardwareID('modalias', 'pci:v00008086d00000166sv000017AAsd0000500Cbc03sc00i00')
2013-04-10 13:31:42,366 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa4d5aec> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2013-04-10 13:31:42,367 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa4d5aec> about HardwareID('modalias', 'pci:v000010ECd00005209sv000010ECsd00005209bc08sc05i00')
2013-04-10 13:31:42,367 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa4d5aec> about HardwareID('modalias', 'acpi:PNP0000:')
2013-04-10 13:31:42,367 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa4d5aec> about HardwareID('modalias', 'usb:v0A5Cp21F3d0112dcFFdsc01dp01icFFisc01ip01')
2013-04-10 13:31:42,367 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa4d5aec> about HardwareID('modalias', 'wmi:8ADB159E-1E32-455C-BC93-308A7ED98246')
2013-04-10 13:31:42,367 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa4d5aec> about HardwareID('modalias', 'pci:v00008086d00001E20sv000017AAsd0000500Cbc04sc03i00')
2013-04-10 13:31:42,367 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa4d5aec> about HardwareID('modalias', 'acpi:INT0800:')
2013-04-10 13:31:42,367 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa4d5aec> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2013-04-10 13:31:42,367 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa4d5aec> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-04-10 13:31:42,367 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa4d5aec> about HardwareID('modalias', 'wmi:7EEF04FF-4328-447C-B5BB-D449925D538D')
2013-04-10 13:31:42,367 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa4d5aec> about HardwareID('modalias', 'pci:v000010ECd00005209sv000010ECsd00005209bcFFsc00i00')
2013-04-10 13:31:42,367 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa4d5aec> about HardwareID('modalias', 'wmi:51F5230E-9677-46CD-A1CF-C0B23EE34DB7')
2013-04-10 13:31:42,367 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa4d5aec> about HardwareID('modalias', 'usb:v5986p0523d1402dcEFdsc02dp01ic0Eisc01ip00')
2013-04-10 13:31:42,367 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa4d5aec> about HardwareID('modalias', 'wmi:2651D9FD-911C-4B69-B94E-D0DED5963BD7')
2013-04-10 13:31:42,367 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa4d5aec> about HardwareID('modalias', 'platform:pcspkr')
2013-04-10 13:31:42,367 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa4d5aec> about HardwareID('modalias', 'platform:coretemp')
2013-04-10 13:31:42,367 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa4d5aec> about HardwareID('modalias', 'x86cpu:vendor:0000:family:0006:model:003A:feature:,0000,0001,0002,0003,0004,0005,0006,0007,0008,0009,000B,000C,000D,000E,000F,0010,0011,0013,0015,0016,0017,0018,0019,001A,001B,001C,001D,001F,0034,003B,003D,0066,0068,006B,006C,006D,0072,0076,0078,007C,0080,0081,0082,0083,0084,0085,0086,0087,0088,0089,008D,008E,008F,0091,0093,0094,0095,0097,0098,0099,009A,009B,009C,009D,009E,00C0,00E0,00E1,00E3,00E4,00E5,00E6,00E7,0100,0101,0102,0103,0104,0120,0127,0129')
2013-04-10 13:31:42,367 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa4d5aec> about HardwareID('modalias', 'wmi:98479A64-33F5-4E33-A707-8E251EBBC3A1')
2013-04-10 13:31:42,367 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa4d5aec> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2013-04-10 13:31:42,367 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa4d5aec> about HardwareID('modalias', 'wmi:74F1EBB6-927A-4C7D-95DF-698E21E80EB5')
2013-04-10 13:31:42,367 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa4d5aec> about HardwareID('modalias', 'acpi:SMO1200:PNP0C31:')
2013-04-10 13:31:42,367 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa4d5aec> about HardwareID('modalias', 'input:b0003v5986p0523e1402-e0,1,kD4,ramlsfw')
2013-04-10 13:31:42,368 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa4d5aec> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-04-10 13:31:42,368 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa4d5aec> about HardwareID('modalias', 'wmi:7364651A-132F-4FE7-ADAA-40C6C7EE2E3B')
2013-04-10 13:31:42,416 DEBUG: Shutting down
2013-04-10 13:32:48,787 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d24a0c>
2013-04-10 13:32:50,036 DEBUG: reading modalias file /lib/modules/3.5.0-23-generic/modules.alias
2013-04-10 13:32:50,106 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2013-04-10 13:32:50,106 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2013-04-10 13:32:50,141 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2013-04-10 13:32:50,146 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2013-04-10 13:32:50,154 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2013-04-10 13:32:50,154 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2013-04-10 13:32:50,154 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2013-04-10 13:32:50,157 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2013-04-10 13:32:50,158 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2013-04-10 13:32:50,158 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2013-04-10 13:32:50,158 DEBUG: loading custom handler /usr/share/jockey/handlers/cdv.py
2013-04-10 13:32:50,162 WARNING: modinfo for module cedarview_gfx failed: ERROR: modinfo: could not find module cedarview_gfx

2013-04-10 13:32:50,162 DEBUG: Instantiated Handler subclass __builtin__.CdvDriver from name CdvDriver
2013-04-10 13:32:50,162 DEBUG: cdv.available: falling back to default
2013-04-10 13:32:50,261 DEBUG: XorgDriverHandler(cedarview_gfx, cedarview-graphics-drivers, None): Disabling as package is not compatible with Q-LTS X.org
2013-04-10 13:32:50,261 DEBUG: Intel Cedarview graphics driver not available
2013-04-10 13:32:50,261 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2013-04-10 13:32:50,265 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2013-04-10 13:32:50,268 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2013-04-10 13:32:50,269 DEBUG: Disabling Nvidia driver on intel/hybrid system
2013-04-10 13:32:50,269 DEBUG: NVIDIA accelerated graphics driver not available
2013-04-10 13:32:50,271 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2013-04-10 13:32:50,273 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2013-04-10 13:32:50,273 DEBUG: Disabling Nvidia driver on intel/hybrid system
2013-04-10 13:32:50,273 DEBUG: NVIDIA accelerated graphics driver not available
2013-04-10 13:32:50,275 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2013-04-10 13:32:50,277 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2013-04-10 13:32:50,278 DEBUG: Disabling Nvidia driver on intel/hybrid system
2013-04-10 13:32:50,278 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2013-04-10 13:32:50,280 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2013-04-10 13:32:50,282 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2013-04-10 13:32:50,282 DEBUG: Disabling Nvidia driver on intel/hybrid system
2013-04-10 13:32:50,283 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2013-04-10 13:32:50,284 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2013-04-10 13:32:50,287 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2013-04-10 13:32:50,287 DEBUG: Disabling Nvidia driver on intel/hybrid system
2013-04-10 13:32:50,287 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2013-04-10 13:32:50,289 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2013-04-10 13:32:50,292 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2013-04-10 13:32:50,292 DEBUG: Disabling Nvidia driver on intel/hybrid system
2013-04-10 13:32:50,292 DEBUG: NVIDIA accelerated graphics driver not available
2013-04-10 13:32:50,294 WARNING: modinfo for module nvidia_experimental_310 failed: ERROR: modinfo: could not find module nvidia_experimental_310

2013-04-10 13:32:50,304 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverExperimental310 from name NvidiaDriverExperimental310
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 972, in get_handlers
    desc = inst.name()
  File "/usr/lib/python2.7/dist-packages/jockey/handlers.py", line 108, in name
    self._package_defaults()
  File "/usr/lib/python2.7/dist-packages/jockey/handlers.py", line 93, in _package_defaults
    (distro_name, distro_desc) = OSLib.inst.package_description(self.package)
  File "/usr/lib/python2.7/dist-packages/jockey/oslib.py", line 216, in package_description
    raise ValueError('package %s does not exist' % package)
ValueError: package nvidia-experimental-310 does not exist
2013-04-10 13:32:50,308 WARNING: modinfo for module nvidia_experimental_304 failed: ERROR: modinfo: could not find module nvidia_experimental_304

2013-04-10 13:32:50,318 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverExperimental304 from name NvidiaDriverExperimental304
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 972, in get_handlers
    desc = inst.name()
  File "/usr/lib/python2.7/dist-packages/jockey/handlers.py", line 108, in name
    self._package_defaults()
  File "/usr/lib/python2.7/dist-packages/jockey/handlers.py", line 93, in _package_defaults
    (distro_name, distro_desc) = OSLib.inst.package_description(self.package)
  File "/usr/lib/python2.7/dist-packages/jockey/oslib.py", line 216, in package_description
    raise ValueError('package %s does not exist' % package)
ValueError: package nvidia-experimental-304 does not exist
2013-04-10 13:32:50,318 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2013-04-10 13:32:50,328 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2013-04-10 13:32:50,334 DEBUG: Software modem not available
2013-04-10 13:32:50,334 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2013-04-10 13:32:50,338 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2013-04-10 13:32:50,340 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2013-04-10 13:32:50,433 DEBUG: XorgDriverHandler(omapdrm_pvr, pvr-omap4, None): Disabling as package is not compatible with Q-LTS X.org
2013-04-10 13:32:50,433 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2013-04-10 13:32:50,433 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2013-04-10 13:32:50,436 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2013-04-10 13:32:50,436 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2013-04-10 13:32:50,445 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2013-04-10 13:32:50,445 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2013-04-10 13:32:50,457 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2013-04-10 13:32:50,457 DEBUG: Firmware for DVB cards not available
2013-04-10 13:32:50,457 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2013-04-10 13:32:50,461 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2013-04-10 13:32:50,463 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2013-04-10 13:32:50,463 DEBUG: fglrx.available: falling back to default
2013-04-10 13:32:50,556 DEBUG: XorgDriverHandler(fglrx_updates, fglrx-updates, None): Disabling as package is not compatible with Q-LTS X.org
2013-04-10 13:32:50,556 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) not available
2013-04-10 13:32:50,558 WARNING: modinfo for module fglrx_experimental_9 failed: ERROR: modinfo: could not find module fglrx_experimental_9

2013-04-10 13:32:50,568 DEBUG: Could not instantiate Handler subclass __builtin__.FglrxDriverExperimental9 from name FglrxDriverExperimental9
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 972, in get_handlers
    desc = inst.name()
  File "/usr/lib/python2.7/dist-packages/jockey/handlers.py", line 108, in name
    self._package_defaults()
  File "/usr/lib/python2.7/dist-packages/jockey/handlers.py", line 93, in _package_defaults
    (distro_name, distro_desc) = OSLib.inst.package_description(self.package)
  File "/usr/lib/python2.7/dist-packages/jockey/oslib.py", line 216, in package_description
    raise ValueError('package %s does not exist' % package)
ValueError: package fglrx-experimental-9 does not exist
2013-04-10 13:32:50,570 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2013-04-10 13:32:50,572 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2013-04-10 13:32:50,573 DEBUG: fglrx.available: falling back to default
2013-04-10 13:32:50,665 DEBUG: XorgDriverHandler(fglrx, fglrx, None): Disabling as package is not compatible with Q-LTS X.org
2013-04-10 13:32:50,665 DEBUG: ATI/AMD proprietary FGLRX graphics driver not available
2013-04-10 13:32:50,665 DEBUG: all custom handlers loaded
2013-04-10 13:32:50,665 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d24a0c> about HardwareID('modalias', 'pci:v00008086d00001E3Asv000017AAsd0000500Cbc07sc80i00')
2013-04-10 13:32:50,873 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mei'}
2013-04-10 13:32:50,919 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mei', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:32:50,919 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d24a0c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,145,148,14A,14D,14E,14F,ra0,1,18,1C,2F,35,36,39,3A,mlsfw')
2013-04-10 13:32:50,923 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-10 13:32:50,923 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:32:50,923 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2013-04-10 13:32:50,923 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:32:50,923 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2013-04-10 13:32:50,923 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:32:50,923 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2013-04-10 13:32:50,923 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:32:50,923 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-04-10 13:32:50,923 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:32:50,923 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d24a0c> about HardwareID('modalias', 'acpi:PNP0200:')
2013-04-10 13:32:50,923 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d24a0c> about HardwareID('modalias', 'acpi:PNP0103:')
2013-04-10 13:32:50,923 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d24a0c> about HardwareID('modalias', 'acpi:PNP0303:PNP0303:')
2013-04-10 13:32:50,924 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d24a0c> about HardwareID('modalias', 'pci:v00008086d00000154sv000017AAsd0000500Cbc06sc00i00')
2013-04-10 13:32:50,926 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d24a0c> about HardwareID('modalias', 'pci:v00008086d00001E31sv000017AAsd0000500Cbc0Csc03i30')
2013-04-10 13:32:50,928 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d24a0c> about HardwareID('modalias', 'platform:thinkpad_hwmon')
2013-04-10 13:32:50,929 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d24a0c> about HardwareID('modalias', 'input:b0011v0002p000Ae0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2013-04-10 13:32:50,929 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-10 13:32:50,929 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:32:50,929 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-04-10 13:32:50,929 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:32:50,929 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d24a0c> about HardwareID('modalias', 'usb:v1D6Bp0002d0305dc09dsc00dp01ic09isc00ip00')
2013-04-10 13:32:50,938 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d24a0c> about HardwareID('modalias', 'usb:v1D6Bp0003d0305dc09dsc00dp03ic09isc00ip00')
2013-04-10 13:32:50,938 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d24a0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2013-04-10 13:32:50,939 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-10 13:32:50,939 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:32:50,939 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d24a0c> about HardwareID('modalias', 'platform:microcode')
2013-04-10 13:32:50,939 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d24a0c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2013-04-10 13:32:50,939 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d24a0c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-04-10 13:32:50,939 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d24a0c> about HardwareID('modalias', 'platform:thinkpad_acpi')
2013-04-10 13:32:50,939 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d24a0c> about HardwareID('modalias', 'acpi:LEN0051:PNP0F13:')
2013-04-10 13:32:50,940 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d24a0c> about HardwareID('modalias', 'platform:eisa')
2013-04-10 13:32:50,940 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d24a0c> about HardwareID('modalias', 'wmi:7FF47003-3B6C-4E5E-A227-E979824A85D1')
2013-04-10 13:32:50,940 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d24a0c> about HardwareID('modalias', 'pci:v00008086d00001E26sv000017AAsd0000500Cbc0Csc03i20')
2013-04-10 13:32:50,943 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d24a0c> about HardwareID('modalias', 'wmi:6A4B54EF-A5ED-4D33-9455-B0D9B48DF4B3')
2013-04-10 13:32:50,943 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d24a0c> about HardwareID('modalias', 'usb:v0A5Cp21F3d0112dcFFdsc01dp01icFEisc01ip01')
2013-04-10 13:32:50,945 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d24a0c> about HardwareID('modalias', 'serio:ty05pr00id00ex00')
2013-04-10 13:32:50,950 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2013-04-10 13:32:50,950 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:32:50,950 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d24a0c> about HardwareID('modalias', 'pci:v00008086d00001E58sv000017AAsd0000500Cbc06sc01i00')
2013-04-10 13:32:50,953 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'lpc_ich'}
2013-04-10 13:32:50,953 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'lpc_ich', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:32:50,953 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d24a0c> about HardwareID('modalias', 'pci:v00008086d00001E03sv000017AAsd0000500Cbc01sc06i01')
2013-04-10 13:32:50,955 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d24a0c> about HardwareID('modalias', 'pci:v00008086d00001E2Dsv000017AAsd0000500Cbc0Csc03i20')
2013-04-10 13:32:50,957 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d24a0c> about HardwareID('modalias', 'acpi:INT3392:PNP0C02:')
2013-04-10 13:32:50,957 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d24a0c> about HardwareID('modalias', 'pci:v00008086d00001E22sv000017AAsd0000500Cbc0Csc05i00')
2013-04-10 13:32:50,959 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801'}
2013-04-10 13:32:50,959 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:32:50,960 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d24a0c> about HardwareID('modalias', 'acpi:PNP0B00:')
2013-04-10 13:32:50,960 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d24a0c> about HardwareID('modalias', 'pci:v000014E4d00004359sv000014E4sd00000607bc02sc80i00')
2013-04-10 13:32:50,990 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'wl', 'package': 'bcmwl-kernel-source'}
2013-04-10 13:32:50,991 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-04-10 13:32:50,990 DEBUG: found match in handler pool kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2013-04-10 13:32:50,993 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2013-04-10 13:32:50,993 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-04-10 13:32:50,993 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2013-04-10 13:32:50,993 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d24a0c> about HardwareID('modalias', 'usb:v1D6Bp0002d0305dc09dsc00dp00ic09isc00ip00')
2013-04-10 13:32:50,993 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d24a0c> about HardwareID('modalias', 'acpi:PNP0C04:')
2013-04-10 13:32:50,993 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d24a0c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2013-04-10 13:32:50,994 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2013-04-10 13:32:50,994 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:32:50,994 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2013-04-10 13:32:50,994 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:32:50,994 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d24a0c> about HardwareID('modalias', 'acpi:PNP0100:')
2013-04-10 13:32:50,994 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d24a0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2013-04-10 13:32:50,994 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-10 13:32:50,994 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:32:50,994 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d24a0c> about HardwareID('modalias', 'input:b0019v17AAp5054e4101-e0,1,4,5,k71,72,73,8E,94,98,BF,C2,CD,D4,E0,E1,E3,E4,EC,EE,F0,F8,174,1D2,1DB,1DC,ram4,lsfw1,3,')
2013-04-10 13:32:50,994 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-10 13:32:50,994 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:32:50,994 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-04-10 13:32:50,994 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:32:50,995 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d24a0c> about HardwareID('modalias', 'usb:v0A5Cp21F3d0112dcFFdsc01dp01icFFiscFFipFF')
2013-04-10 13:32:50,995 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d24a0c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2013-04-10 13:32:50,995 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-10 13:32:50,995 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:32:50,995 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-04-10 13:32:50,995 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:32:50,995 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d24a0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2013-04-10 13:32:50,995 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-10 13:32:50,995 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:32:50,995 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d24a0c> about HardwareID('modalias', 'wmi:E2BE5EE3-42DA-49DB-8378-1F5247388202')
2013-04-10 13:32:50,995 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d24a0c> about HardwareID('modalias', 'acpi:PNP0C02:')
2013-04-10 13:32:50,995 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d24a0c> about HardwareID('modalias', 'dmi:bvnLENOVO:bvrH6ET90WW(2.08):bd01/11/2013:svnLENOVO:pn3351CTO:pvrThinkPadT430u:rvnLENOVO:rn3351CTO:rvrNotDefined:cvnLENOVO:ct10:cvrNotAvailable:')
2013-04-10 13:32:51,004 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d24a0c> about HardwareID('modalias', 'wmi:FCB424F1-075A-4E0E-BFC4-62F3E71771FA')
2013-04-10 13:32:51,004 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d24a0c> about HardwareID('modalias', 'pci:v000010ECd00008168sv000017AAsd0000500Cbc02sc00i00')
2013-04-10 13:32:51,010 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2013-04-10 13:32:51,010 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:32:51,010 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d24a0c> about HardwareID('modalias', 'wmi:7430019A-DCE9-4548-BAB0-9FDE0935CAFF')
2013-04-10 13:32:51,010 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d24a0c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2013-04-10 13:32:51,010 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-10 13:32:51,010 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:32:51,010 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-04-10 13:32:51,011 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:32:51,011 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d24a0c> about HardwareID('modalias', 'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2013-04-10 13:32:51,011 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d24a0c> about HardwareID('modalias', 'usb:v5986p0523d1402dcEFdsc02dp01ic0Eisc02ip00')
2013-04-10 13:32:51,011 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d24a0c> about HardwareID('modalias', 'pci:v00008086d00000166sv000017AAsd0000500Cbc03sc00i00')
2013-04-10 13:32:51,013 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i915'}
2013-04-10 13:32:51,014 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:32:51,014 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d24a0c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2013-04-10 13:32:51,014 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-10 13:32:51,014 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:32:51,014 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d24a0c> about HardwareID('modalias', 'pci:v000010ECd00005209sv000010ECsd00005209bc08sc05i00')
2013-04-10 13:32:51,014 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci'}
2013-04-10 13:32:51,014 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:32:51,014 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d24a0c> about HardwareID('modalias', 'acpi:PNP0000:')
2013-04-10 13:32:51,014 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d24a0c> about HardwareID('modalias', 'usb:v0A5Cp21F3d0112dcFFdsc01dp01icFFisc01ip01')
2013-04-10 13:32:51,014 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2013-04-10 13:32:51,014 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:32:51,014 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d24a0c> about HardwareID('modalias', 'wmi:8ADB159E-1E32-455C-BC93-308A7ED98246')
2013-04-10 13:32:51,014 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d24a0c> about HardwareID('modalias', 'pci:v00008086d00001E20sv000017AAsd0000500Cbc04sc03i00')
2013-04-10 13:32:51,017 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-04-10 13:32:51,017 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:32:51,017 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-04-10 13:32:51,017 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:32:51,017 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d24a0c> about HardwareID('modalias', 'acpi:INT0800:')
2013-04-10 13:32:51,017 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d24a0c> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2013-04-10 13:32:51,017 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d24a0c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-04-10 13:32:51,017 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d24a0c> about HardwareID('modalias', 'wmi:7EEF04FF-4328-447C-B5BB-D449925D538D')
2013-04-10 13:32:51,017 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d24a0c> about HardwareID('modalias', 'pci:v000010ECd00005209sv000010ECsd00005209bcFFsc00i00')
2013-04-10 13:32:51,018 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'rts_pstor'}
2013-04-10 13:32:51,018 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'rts_pstor', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:32:51,018 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d24a0c> about HardwareID('modalias', 'wmi:51F5230E-9677-46CD-A1CF-C0B23EE34DB7')
2013-04-10 13:32:51,018 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d24a0c> about HardwareID('modalias', 'usb:v5986p0523d1402dcEFdsc02dp01ic0Eisc01ip00')
2013-04-10 13:32:51,018 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2013-04-10 13:32:51,018 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:32:51,018 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d24a0c> about HardwareID('modalias', 'wmi:2651D9FD-911C-4B69-B94E-D0DED5963BD7')
2013-04-10 13:32:51,018 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d24a0c> about HardwareID('modalias', 'platform:pcspkr')
2013-04-10 13:32:51,018 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2013-04-10 13:32:51,018 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:32:51,019 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2013-04-10 13:32:51,019 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:32:51,019 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d24a0c> about HardwareID('modalias', 'platform:coretemp')
2013-04-10 13:32:51,019 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d24a0c> about HardwareID('modalias', 'x86cpu:vendor:0000:family:0006:model:003A:feature:,0000,0001,0002,0003,0004,0005,0006,0007,0008,0009,000B,000C,000D,000E,000F,0010,0011,0013,0015,0016,0017,0018,0019,001A,001B,001C,001D,001F,0034,003B,003D,0066,0068,006B,006C,006D,0072,0076,0078,007C,0080,0081,0082,0083,0084,0085,0086,0087,0088,0089,008D,008E,008F,0091,0093,0094,0095,0097,0098,0099,009A,009B,009C,009D,009E,00C0,00E0,00E1,00E3,00E4,00E5,00E6,00E7,0100,0101,0102,0103,0104,0120,0127,0129')
2013-04-10 13:32:51,023 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'aesni_intel'}
2013-04-10 13:32:51,023 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'aesni_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:32:51,023 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'kvm_intel'}
2013-04-10 13:32:51,023 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'kvm_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:32:51,023 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'microcode'}
2013-04-10 13:32:51,023 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'microcode', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:32:51,023 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'coretemp'}
2013-04-10 13:32:51,023 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'coretemp', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:32:51,024 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d24a0c> about HardwareID('modalias', 'wmi:98479A64-33F5-4E33-A707-8E251EBBC3A1')
2013-04-10 13:32:51,024 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d24a0c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-04-10 13:32:51,024 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-10 13:32:51,024 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:32:51,024 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-04-10 13:32:51,024 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:32:51,024 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d24a0c> about HardwareID('modalias', 'wmi:74F1EBB6-927A-4C7D-95DF-698E21E80EB5')
2013-04-10 13:32:51,024 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d24a0c> about HardwareID('modalias', 'acpi:SMO1200:PNP0C31:')
2013-04-10 13:32:51,024 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d24a0c> about HardwareID('modalias', 'input:b0003v5986p0523e1402-e0,1,kD4,ramlsfw')
2013-04-10 13:32:51,024 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-10 13:32:51,024 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:32:51,024 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-04-10 13:32:51,024 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:32:51,024 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d24a0c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2013-04-10 13:32:51,024 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-10 13:32:51,025 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:32:51,025 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-04-10 13:32:51,025 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:32:51,025 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8d24a0c> about HardwareID('modalias', 'wmi:7364651A-132F-4FE7-ADAA-40C6C7EE2E3B')
2013-04-10 13:32:51,025 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fbc6cc> about HardwareID('modalias', 'pci:v00008086d00001E3Asv000017AAsd0000500Cbc07sc80i00')
2013-04-10 13:32:51,025 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fbc6cc> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,145,148,14A,14D,14E,14F,ra0,1,18,1C,2F,35,36,39,3A,mlsfw')
2013-04-10 13:32:51,025 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fbc6cc> about HardwareID('modalias', 'acpi:PNP0200:')
2013-04-10 13:32:51,025 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fbc6cc> about HardwareID('modalias', 'acpi:PNP0103:')
2013-04-10 13:32:51,025 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fbc6cc> about HardwareID('modalias', 'acpi:PNP0303:PNP0303:')
2013-04-10 13:32:51,025 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fbc6cc> about HardwareID('modalias', 'pci:v00008086d00000154sv000017AAsd0000500Cbc06sc00i00')
2013-04-10 13:32:51,025 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fbc6cc> about HardwareID('modalias', 'pci:v00008086d00001E31sv000017AAsd0000500Cbc0Csc03i30')
2013-04-10 13:32:51,025 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fbc6cc> about HardwareID('modalias', 'platform:thinkpad_hwmon')
2013-04-10 13:32:51,025 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fbc6cc> about HardwareID('modalias', 'input:b0011v0002p000Ae0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2013-04-10 13:32:51,025 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fbc6cc> about HardwareID('modalias', 'usb:v1D6Bp0002d0305dc09dsc00dp01ic09isc00ip00')
2013-04-10 13:32:51,025 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fbc6cc> about HardwareID('modalias', 'usb:v1D6Bp0003d0305dc09dsc00dp03ic09isc00ip00')
2013-04-10 13:32:51,025 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fbc6cc> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2013-04-10 13:32:51,025 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fbc6cc> about HardwareID('modalias', 'platform:microcode')
2013-04-10 13:32:51,025 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fbc6cc> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2013-04-10 13:32:51,025 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fbc6cc> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-04-10 13:32:51,025 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fbc6cc> about HardwareID('modalias', 'platform:thinkpad_acpi')
2013-04-10 13:32:51,025 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fbc6cc> about HardwareID('modalias', 'acpi:LEN0051:PNP0F13:')
2013-04-10 13:32:51,026 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fbc6cc> about HardwareID('modalias', 'platform:eisa')
2013-04-10 13:32:51,026 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fbc6cc> about HardwareID('modalias', 'wmi:7FF47003-3B6C-4E5E-A227-E979824A85D1')
2013-04-10 13:32:51,026 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fbc6cc> about HardwareID('modalias', 'pci:v00008086d00001E26sv000017AAsd0000500Cbc0Csc03i20')
2013-04-10 13:32:51,026 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fbc6cc> about HardwareID('modalias', 'wmi:6A4B54EF-A5ED-4D33-9455-B0D9B48DF4B3')
2013-04-10 13:32:51,026 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fbc6cc> about HardwareID('modalias', 'usb:v0A5Cp21F3d0112dcFFdsc01dp01icFEisc01ip01')
2013-04-10 13:32:51,026 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fbc6cc> about HardwareID('modalias', 'serio:ty05pr00id00ex00')
2013-04-10 13:32:51,026 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fbc6cc> about HardwareID('modalias', 'pci:v00008086d00001E58sv000017AAsd0000500Cbc06sc01i00')
2013-04-10 13:32:51,026 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fbc6cc> about HardwareID('modalias', 'pci:v00008086d00001E03sv000017AAsd0000500Cbc01sc06i01')
2013-04-10 13:32:51,026 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fbc6cc> about HardwareID('modalias', 'pci:v00008086d00001E2Dsv000017AAsd0000500Cbc0Csc03i20')
2013-04-10 13:32:51,026 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fbc6cc> about HardwareID('modalias', 'acpi:INT3392:PNP0C02:')
2013-04-10 13:32:51,026 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fbc6cc> about HardwareID('modalias', 'pci:v00008086d00001E22sv000017AAsd0000500Cbc0Csc05i00')
2013-04-10 13:32:51,026 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fbc6cc> about HardwareID('modalias', 'acpi:PNP0B00:')
2013-04-10 13:32:51,026 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fbc6cc> about HardwareID('modalias', 'pci:v000014E4d00004359sv000014E4sd00000607bc02sc80i00')
2013-04-10 13:32:51,026 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fbc6cc> about HardwareID('modalias', 'usb:v1D6Bp0002d0305dc09dsc00dp00ic09isc00ip00')
2013-04-10 13:32:51,026 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fbc6cc> about HardwareID('modalias', 'acpi:PNP0C04:')
2013-04-10 13:32:51,026 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fbc6cc> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2013-04-10 13:32:51,026 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fbc6cc> about HardwareID('modalias', 'acpi:PNP0100:')
2013-04-10 13:32:51,026 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fbc6cc> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2013-04-10 13:32:51,026 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fbc6cc> about HardwareID('modalias', 'input:b0019v17AAp5054e4101-e0,1,4,5,k71,72,73,8E,94,98,BF,C2,CD,D4,E0,E1,E3,E4,EC,EE,F0,F8,174,1D2,1DB,1DC,ram4,lsfw1,3,')
2013-04-10 13:32:51,026 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fbc6cc> about HardwareID('modalias', 'usb:v0A5Cp21F3d0112dcFFdsc01dp01icFFiscFFipFF')
2013-04-10 13:32:51,026 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fbc6cc> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2013-04-10 13:32:51,026 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fbc6cc> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2013-04-10 13:32:51,026 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fbc6cc> about HardwareID('modalias', 'wmi:E2BE5EE3-42DA-49DB-8378-1F5247388202')
2013-04-10 13:32:51,027 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fbc6cc> about HardwareID('modalias', 'acpi:PNP0C02:')
2013-04-10 13:32:51,027 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fbc6cc> about HardwareID('modalias', 'dmi:bvnLENOVO:bvrH6ET90WW(2.08):bd01/11/2013:svnLENOVO:pn3351CTO:pvrThinkPadT430u:rvnLENOVO:rn3351CTO:rvrNotDefined:cvnLENOVO:ct10:cvrNotAvailable:')
2013-04-10 13:32:51,027 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fbc6cc> about HardwareID('modalias', 'wmi:FCB424F1-075A-4E0E-BFC4-62F3E71771FA')
2013-04-10 13:32:51,027 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fbc6cc> about HardwareID('modalias', 'pci:v000010ECd00008168sv000017AAsd0000500Cbc02sc00i00')
2013-04-10 13:32:51,027 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fbc6cc> about HardwareID('modalias', 'wmi:7430019A-DCE9-4548-BAB0-9FDE0935CAFF')
2013-04-10 13:32:51,027 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fbc6cc> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2013-04-10 13:32:51,027 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fbc6cc> about HardwareID('modalias', 'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2013-04-10 13:32:51,027 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fbc6cc> about HardwareID('modalias', 'usb:v5986p0523d1402dcEFdsc02dp01ic0Eisc02ip00')
2013-04-10 13:32:51,027 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fbc6cc> about HardwareID('modalias', 'pci:v00008086d00000166sv000017AAsd0000500Cbc03sc00i00')
2013-04-10 13:32:51,027 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fbc6cc> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2013-04-10 13:32:51,027 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fbc6cc> about HardwareID('modalias', 'pci:v000010ECd00005209sv000010ECsd00005209bc08sc05i00')
2013-04-10 13:32:51,027 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fbc6cc> about HardwareID('modalias', 'acpi:PNP0000:')
2013-04-10 13:32:51,027 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fbc6cc> about HardwareID('modalias', 'usb:v0A5Cp21F3d0112dcFFdsc01dp01icFFisc01ip01')
2013-04-10 13:32:51,027 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fbc6cc> about HardwareID('modalias', 'wmi:8ADB159E-1E32-455C-BC93-308A7ED98246')
2013-04-10 13:32:51,027 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fbc6cc> about HardwareID('modalias', 'pci:v00008086d00001E20sv000017AAsd0000500Cbc04sc03i00')
2013-04-10 13:32:51,027 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fbc6cc> about HardwareID('modalias', 'acpi:INT0800:')
2013-04-10 13:32:51,027 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fbc6cc> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2013-04-10 13:32:51,027 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fbc6cc> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-04-10 13:32:51,027 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fbc6cc> about HardwareID('modalias', 'wmi:7EEF04FF-4328-447C-B5BB-D449925D538D')
2013-04-10 13:32:51,027 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fbc6cc> about HardwareID('modalias', 'pci:v000010ECd00005209sv000010ECsd00005209bcFFsc00i00')
2013-04-10 13:32:51,027 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fbc6cc> about HardwareID('modalias', 'wmi:51F5230E-9677-46CD-A1CF-C0B23EE34DB7')
2013-04-10 13:32:51,027 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fbc6cc> about HardwareID('modalias', 'usb:v5986p0523d1402dcEFdsc02dp01ic0Eisc01ip00')
2013-04-10 13:32:51,027 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fbc6cc> about HardwareID('modalias', 'wmi:2651D9FD-911C-4B69-B94E-D0DED5963BD7')
2013-04-10 13:32:51,028 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fbc6cc> about HardwareID('modalias', 'platform:pcspkr')
2013-04-10 13:32:51,028 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fbc6cc> about HardwareID('modalias', 'platform:coretemp')
2013-04-10 13:32:51,028 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fbc6cc> about HardwareID('modalias', 'x86cpu:vendor:0000:family:0006:model:003A:feature:,0000,0001,0002,0003,0004,0005,0006,0007,0008,0009,000B,000C,000D,000E,000F,0010,0011,0013,0015,0016,0017,0018,0019,001A,001B,001C,001D,001F,0034,003B,003D,0066,0068,006B,006C,006D,0072,0076,0078,007C,0080,0081,0082,0083,0084,0085,0086,0087,0088,0089,008D,008E,008F,0091,0093,0094,0095,0097,0098,0099,009A,009B,009C,009D,009E,00C0,00E0,00E1,00E3,00E4,00E5,00E6,00E7,0100,0101,0102,0103,0104,0120,0127,0129')
2013-04-10 13:32:51,028 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fbc6cc> about HardwareID('modalias', 'wmi:98479A64-33F5-4E33-A707-8E251EBBC3A1')
2013-04-10 13:32:51,028 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fbc6cc> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-04-10 13:32:51,028 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fbc6cc> about HardwareID('modalias', 'wmi:74F1EBB6-927A-4C7D-95DF-698E21E80EB5')
2013-04-10 13:32:51,028 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fbc6cc> about HardwareID('modalias', 'acpi:SMO1200:PNP0C31:')
2013-04-10 13:32:51,028 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fbc6cc> about HardwareID('modalias', 'input:b0003v5986p0523e1402-e0,1,kD4,ramlsfw')
2013-04-10 13:32:51,028 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fbc6cc> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2013-04-10 13:32:51,028 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8fbc6cc> about HardwareID('modalias', 'wmi:7364651A-132F-4FE7-ADAA-40C6C7EE2E3B')
2013-04-10 13:32:51,068 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-04-10 13:32:51,085 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-04-10 13:32:51,096 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-04-10 13:32:51,115 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-04-10 13:32:51,120 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-04-10 13:32:51,140 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-04-10 13:32:59,826 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-04-10 13:33:01,420 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-04-10 13:33:04,720 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2013-04-10 13:33:04,720 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2013-04-10 13:33:04,754 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-04-10 13:37:05,425 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x9111a0c>
2013-04-10 13:37:06,719 DEBUG: reading modalias file /lib/modules/3.5.0-23-generic/modules.alias
2013-04-10 13:37:06,796 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2013-04-10 13:37:06,796 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2013-04-10 13:37:06,843 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2013-04-10 13:37:06,851 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2013-04-10 13:37:06,877 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2013-04-10 13:37:06,878 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2013-04-10 13:37:06,878 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2013-04-10 13:37:06,886 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2013-04-10 13:37:06,887 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2013-04-10 13:37:06,888 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2013-04-10 13:37:06,888 DEBUG: loading custom handler /usr/share/jockey/handlers/cdv.py
2013-04-10 13:37:06,899 WARNING: modinfo for module cedarview_gfx failed: ERROR: modinfo: could not find module cedarview_gfx

2013-04-10 13:37:06,899 DEBUG: Instantiated Handler subclass __builtin__.CdvDriver from name CdvDriver
2013-04-10 13:37:06,900 DEBUG: cdv.available: falling back to default
2013-04-10 13:37:07,059 DEBUG: XorgDriverHandler(cedarview_gfx, cedarview-graphics-drivers, None): Disabling as package is not compatible with Q-LTS X.org
2013-04-10 13:37:07,060 DEBUG: Intel Cedarview graphics driver not available
2013-04-10 13:37:07,060 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2013-04-10 13:37:07,073 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2013-04-10 13:37:07,080 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2013-04-10 13:37:07,083 DEBUG: Disabling Nvidia driver on intel/hybrid system
2013-04-10 13:37:07,083 DEBUG: NVIDIA accelerated graphics driver not available
2013-04-10 13:37:07,089 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2013-04-10 13:37:07,097 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2013-04-10 13:37:07,098 DEBUG: Disabling Nvidia driver on intel/hybrid system
2013-04-10 13:37:07,098 DEBUG: NVIDIA accelerated graphics driver not available
2013-04-10 13:37:07,104 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2013-04-10 13:37:07,112 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2013-04-10 13:37:07,113 DEBUG: Disabling Nvidia driver on intel/hybrid system
2013-04-10 13:37:07,113 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2013-04-10 13:37:07,119 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2013-04-10 13:37:07,126 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2013-04-10 13:37:07,128 DEBUG: Disabling Nvidia driver on intel/hybrid system
2013-04-10 13:37:07,128 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2013-04-10 13:37:07,134 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2013-04-10 13:37:07,142 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2013-04-10 13:37:07,144 DEBUG: Disabling Nvidia driver on intel/hybrid system
2013-04-10 13:37:07,144 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2013-04-10 13:37:07,150 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2013-04-10 13:37:07,157 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2013-04-10 13:37:07,159 DEBUG: Disabling Nvidia driver on intel/hybrid system
2013-04-10 13:37:07,159 DEBUG: NVIDIA accelerated graphics driver not available
2013-04-10 13:37:07,165 WARNING: modinfo for module nvidia_experimental_310 failed: ERROR: modinfo: could not find module nvidia_experimental_310

2013-04-10 13:37:07,192 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverExperimental310 from name NvidiaDriverExperimental310
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 972, in get_handlers
    desc = inst.name()
  File "/usr/lib/python2.7/dist-packages/jockey/handlers.py", line 108, in name
    self._package_defaults()
  File "/usr/lib/python2.7/dist-packages/jockey/handlers.py", line 93, in _package_defaults
    (distro_name, distro_desc) = OSLib.inst.package_description(self.package)
  File "/usr/lib/python2.7/dist-packages/jockey/oslib.py", line 216, in package_description
    raise ValueError('package %s does not exist' % package)
ValueError: package nvidia-experimental-310 does not exist
2013-04-10 13:37:07,200 WARNING: modinfo for module nvidia_experimental_304 failed: ERROR: modinfo: could not find module nvidia_experimental_304

2013-04-10 13:37:07,231 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverExperimental304 from name NvidiaDriverExperimental304
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 972, in get_handlers
    desc = inst.name()
  File "/usr/lib/python2.7/dist-packages/jockey/handlers.py", line 108, in name
    self._package_defaults()
  File "/usr/lib/python2.7/dist-packages/jockey/handlers.py", line 93, in _package_defaults
    (distro_name, distro_desc) = OSLib.inst.package_description(self.package)
  File "/usr/lib/python2.7/dist-packages/jockey/oslib.py", line 216, in package_description
    raise ValueError('package %s does not exist' % package)
ValueError: package nvidia-experimental-304 does not exist
2013-04-10 13:37:07,232 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2013-04-10 13:37:07,261 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2013-04-10 13:37:07,278 DEBUG: Software modem not available
2013-04-10 13:37:07,278 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2013-04-10 13:37:07,288 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2013-04-10 13:37:07,295 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2013-04-10 13:37:07,440 DEBUG: XorgDriverHandler(omapdrm_pvr, pvr-omap4, None): Disabling as package is not compatible with Q-LTS X.org
2013-04-10 13:37:07,440 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2013-04-10 13:37:07,440 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2013-04-10 13:37:07,448 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2013-04-10 13:37:07,448 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2013-04-10 13:37:07,470 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2013-04-10 13:37:07,471 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2013-04-10 13:37:07,505 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2013-04-10 13:37:07,506 DEBUG: Firmware for DVB cards not available
2013-04-10 13:37:07,506 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2013-04-10 13:37:07,516 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2013-04-10 13:37:07,524 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2013-04-10 13:37:07,524 DEBUG: fglrx.available: falling back to default
2013-04-10 13:37:07,668 DEBUG: XorgDriverHandler(fglrx_updates, fglrx-updates, None): Disabling as package is not compatible with Q-LTS X.org
2013-04-10 13:37:07,669 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) not available
2013-04-10 13:37:07,675 WARNING: modinfo for module fglrx_experimental_9 failed: ERROR: modinfo: could not find module fglrx_experimental_9

2013-04-10 13:37:07,706 DEBUG: Could not instantiate Handler subclass __builtin__.FglrxDriverExperimental9 from name FglrxDriverExperimental9
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 972, in get_handlers
    desc = inst.name()
  File "/usr/lib/python2.7/dist-packages/jockey/handlers.py", line 108, in name
    self._package_defaults()
  File "/usr/lib/python2.7/dist-packages/jockey/handlers.py", line 93, in _package_defaults
    (distro_name, distro_desc) = OSLib.inst.package_description(self.package)
  File "/usr/lib/python2.7/dist-packages/jockey/oslib.py", line 216, in package_description
    raise ValueError('package %s does not exist' % package)
ValueError: package fglrx-experimental-9 does not exist
2013-04-10 13:37:07,713 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2013-04-10 13:37:07,720 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2013-04-10 13:37:07,721 DEBUG: fglrx.available: falling back to default
2013-04-10 13:37:07,874 DEBUG: XorgDriverHandler(fglrx, fglrx, None): Disabling as package is not compatible with Q-LTS X.org
2013-04-10 13:37:07,874 DEBUG: ATI/AMD proprietary FGLRX graphics driver not available
2013-04-10 13:37:07,875 DEBUG: all custom handlers loaded
2013-04-10 13:37:07,875 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9111a0c> about HardwareID('modalias', 'pci:v00008086d00001E3Asv000017AAsd0000500Cbc07sc80i00')
2013-04-10 13:37:08,094 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mei'}
2013-04-10 13:37:08,163 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mei', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:37:08,164 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9111a0c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,145,148,14A,14D,14E,14F,ra0,1,18,1C,2F,35,36,39,3A,mlsfw')
2013-04-10 13:37:08,167 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-10 13:37:08,167 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:37:08,167 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2013-04-10 13:37:08,167 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:37:08,167 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2013-04-10 13:37:08,167 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:37:08,167 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2013-04-10 13:37:08,167 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:37:08,167 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-04-10 13:37:08,168 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:37:08,168 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9111a0c> about HardwareID('modalias', 'acpi:PNP0200:')
2013-04-10 13:37:08,168 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9111a0c> about HardwareID('modalias', 'acpi:PNP0103:')
2013-04-10 13:37:08,168 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9111a0c> about HardwareID('modalias', 'acpi:PNP0303:PNP0303:')
2013-04-10 13:37:08,168 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9111a0c> about HardwareID('modalias', 'pci:v00008086d00000154sv000017AAsd0000500Cbc06sc00i00')
2013-04-10 13:37:08,170 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9111a0c> about HardwareID('modalias', 'pci:v00008086d00001E31sv000017AAsd0000500Cbc0Csc03i30')
2013-04-10 13:37:08,172 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9111a0c> about HardwareID('modalias', 'platform:thinkpad_hwmon')
2013-04-10 13:37:08,173 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9111a0c> about HardwareID('modalias', 'input:b0011v0002p000Ae0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2013-04-10 13:37:08,173 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-10 13:37:08,173 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:37:08,173 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-04-10 13:37:08,173 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:37:08,173 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9111a0c> about HardwareID('modalias', 'usb:v1D6Bp0002d0305dc09dsc00dp01ic09isc00ip00')
2013-04-10 13:37:08,183 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9111a0c> about HardwareID('modalias', 'usb:v1D6Bp0003d0305dc09dsc00dp03ic09isc00ip00')
2013-04-10 13:37:08,183 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9111a0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2013-04-10 13:37:08,183 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-10 13:37:08,183 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:37:08,183 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9111a0c> about HardwareID('modalias', 'platform:microcode')
2013-04-10 13:37:08,183 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9111a0c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2013-04-10 13:37:08,183 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9111a0c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-04-10 13:37:08,184 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9111a0c> about HardwareID('modalias', 'platform:thinkpad_acpi')
2013-04-10 13:37:08,184 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9111a0c> about HardwareID('modalias', 'acpi:LEN0051:PNP0F13:')
2013-04-10 13:37:08,184 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9111a0c> about HardwareID('modalias', 'platform:eisa')
2013-04-10 13:37:08,184 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9111a0c> about HardwareID('modalias', 'wmi:7FF47003-3B6C-4E5E-A227-E979824A85D1')
2013-04-10 13:37:08,184 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9111a0c> about HardwareID('modalias', 'pci:v00008086d00001E26sv000017AAsd0000500Cbc0Csc03i20')
2013-04-10 13:37:08,186 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9111a0c> about HardwareID('modalias', 'wmi:6A4B54EF-A5ED-4D33-9455-B0D9B48DF4B3')
2013-04-10 13:37:08,187 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9111a0c> about HardwareID('modalias', 'usb:v0A5Cp21F3d0112dcFFdsc01dp01icFEisc01ip01')
2013-04-10 13:37:08,188 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9111a0c> about HardwareID('modalias', 'serio:ty05pr00id00ex00')
2013-04-10 13:37:08,194 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2013-04-10 13:37:08,194 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:37:08,194 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9111a0c> about HardwareID('modalias', 'pci:v00008086d00001E58sv000017AAsd0000500Cbc06sc01i00')
2013-04-10 13:37:08,196 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'lpc_ich'}
2013-04-10 13:37:08,196 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'lpc_ich', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:37:08,196 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9111a0c> about HardwareID('modalias', 'pci:v00008086d00001E03sv000017AAsd0000500Cbc01sc06i01')
2013-04-10 13:37:08,198 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9111a0c> about HardwareID('modalias', 'pci:v00008086d00001E2Dsv000017AAsd0000500Cbc0Csc03i20')
2013-04-10 13:37:08,200 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9111a0c> about HardwareID('modalias', 'acpi:INT3392:PNP0C02:')
2013-04-10 13:37:08,200 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9111a0c> about HardwareID('modalias', 'pci:v00008086d00001E22sv000017AAsd0000500Cbc0Csc05i00')
2013-04-10 13:37:08,202 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801'}
2013-04-10 13:37:08,202 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:37:08,202 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9111a0c> about HardwareID('modalias', 'acpi:PNP0B00:')
2013-04-10 13:37:08,203 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9111a0c> about HardwareID('modalias', 'pci:v000014E4d00004359sv000014E4sd00000607bc02sc80i00')
2013-04-10 13:37:08,233 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'wl', 'package': 'bcmwl-kernel-source'}
2013-04-10 13:37:08,233 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-04-10 13:37:08,233 DEBUG: found match in handler pool kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2013-04-10 13:37:08,235 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2013-04-10 13:37:08,236 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-04-10 13:37:08,236 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2013-04-10 13:37:08,237 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9111a0c> about HardwareID('modalias', 'usb:v1D6Bp0002d0305dc09dsc00dp00ic09isc00ip00')
2013-04-10 13:37:08,237 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9111a0c> about HardwareID('modalias', 'acpi:PNP0C04:')
2013-04-10 13:37:08,238 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9111a0c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2013-04-10 13:37:08,238 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2013-04-10 13:37:08,239 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:37:08,239 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2013-04-10 13:37:08,239 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:37:08,239 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9111a0c> about HardwareID('modalias', 'acpi:PNP0100:')
2013-04-10 13:37:08,239 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9111a0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2013-04-10 13:37:08,239 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-10 13:37:08,239 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:37:08,239 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9111a0c> about HardwareID('modalias', 'input:b0019v17AAp5054e4101-e0,1,4,5,k71,72,73,8E,94,98,BF,C2,CD,D4,E0,E1,E3,E4,EC,EE,F0,F8,174,1D2,1DB,1DC,ram4,lsfw1,3,')
2013-04-10 13:37:08,239 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-10 13:37:08,239 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:37:08,239 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-04-10 13:37:08,239 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:37:08,239 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9111a0c> about HardwareID('modalias', 'usb:v0A5Cp21F3d0112dcFFdsc01dp01icFFiscFFipFF')
2013-04-10 13:37:08,240 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9111a0c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2013-04-10 13:37:08,240 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-10 13:37:08,240 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:37:08,240 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-04-10 13:37:08,240 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:37:08,240 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9111a0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2013-04-10 13:37:08,240 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-10 13:37:08,240 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:37:08,240 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9111a0c> about HardwareID('modalias', 'wmi:E2BE5EE3-42DA-49DB-8378-1F5247388202')
2013-04-10 13:37:08,240 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9111a0c> about HardwareID('modalias', 'acpi:PNP0C02:')
2013-04-10 13:37:08,240 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9111a0c> about HardwareID('modalias', 'dmi:bvnLENOVO:bvrH6ET90WW(2.08):bd01/11/2013:svnLENOVO:pn3351CTO:pvrThinkPadT430u:rvnLENOVO:rn3351CTO:rvrNotDefined:cvnLENOVO:ct10:cvrNotAvailable:')
2013-04-10 13:37:08,249 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9111a0c> about HardwareID('modalias', 'wmi:FCB424F1-075A-4E0E-BFC4-62F3E71771FA')
2013-04-10 13:37:08,249 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9111a0c> about HardwareID('modalias', 'pci:v000010ECd00008168sv000017AAsd0000500Cbc02sc00i00')
2013-04-10 13:37:08,255 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2013-04-10 13:37:08,255 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:37:08,255 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9111a0c> about HardwareID('modalias', 'wmi:7430019A-DCE9-4548-BAB0-9FDE0935CAFF')
2013-04-10 13:37:08,255 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9111a0c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2013-04-10 13:37:08,255 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-10 13:37:08,255 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:37:08,255 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-04-10 13:37:08,255 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:37:08,256 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9111a0c> about HardwareID('modalias', 'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2013-04-10 13:37:08,256 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9111a0c> about HardwareID('modalias', 'usb:v5986p0523d1402dcEFdsc02dp01ic0Eisc02ip00')
2013-04-10 13:37:08,256 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9111a0c> about HardwareID('modalias', 'pci:v00008086d00000166sv000017AAsd0000500Cbc03sc00i00')
2013-04-10 13:37:08,258 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i915'}
2013-04-10 13:37:08,258 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:37:08,258 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9111a0c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2013-04-10 13:37:08,259 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-10 13:37:08,259 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:37:08,259 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9111a0c> about HardwareID('modalias', 'pci:v000010ECd00005209sv000010ECsd00005209bc08sc05i00')
2013-04-10 13:37:08,259 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci'}
2013-04-10 13:37:08,259 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:37:08,259 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9111a0c> about HardwareID('modalias', 'acpi:PNP0000:')
2013-04-10 13:37:08,259 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9111a0c> about HardwareID('modalias', 'usb:v0A5Cp21F3d0112dcFFdsc01dp01icFFisc01ip01')
2013-04-10 13:37:08,259 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2013-04-10 13:37:08,259 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:37:08,259 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9111a0c> about HardwareID('modalias', 'wmi:8ADB159E-1E32-455C-BC93-308A7ED98246')
2013-04-10 13:37:08,259 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9111a0c> about HardwareID('modalias', 'pci:v00008086d00001E20sv000017AAsd0000500Cbc04sc03i00')
2013-04-10 13:37:08,262 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-04-10 13:37:08,262 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:37:08,262 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-04-10 13:37:08,262 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:37:08,262 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9111a0c> about HardwareID('modalias', 'acpi:INT0800:')
2013-04-10 13:37:08,262 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9111a0c> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2013-04-10 13:37:08,262 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9111a0c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-04-10 13:37:08,262 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9111a0c> about HardwareID('modalias', 'wmi:7EEF04FF-4328-447C-B5BB-D449925D538D')
2013-04-10 13:37:08,262 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9111a0c> about HardwareID('modalias', 'pci:v000010ECd00005209sv000010ECsd00005209bcFFsc00i00')
2013-04-10 13:37:08,263 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'rts_pstor'}
2013-04-10 13:37:08,263 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'rts_pstor', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:37:08,263 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9111a0c> about HardwareID('modalias', 'wmi:51F5230E-9677-46CD-A1CF-C0B23EE34DB7')
2013-04-10 13:37:08,263 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9111a0c> about HardwareID('modalias', 'usb:v5986p0523d1402dcEFdsc02dp01ic0Eisc01ip00')
2013-04-10 13:37:08,263 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2013-04-10 13:37:08,263 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:37:08,263 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9111a0c> about HardwareID('modalias', 'wmi:2651D9FD-911C-4B69-B94E-D0DED5963BD7')
2013-04-10 13:37:08,263 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9111a0c> about HardwareID('modalias', 'platform:pcspkr')
2013-04-10 13:37:08,263 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2013-04-10 13:37:08,264 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:37:08,264 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2013-04-10 13:37:08,264 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:37:08,264 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9111a0c> about HardwareID('modalias', 'platform:coretemp')
2013-04-10 13:37:08,264 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9111a0c> about HardwareID('modalias', 'x86cpu:vendor:0000:family:0006:model:003A:feature:,0000,0001,0002,0003,0004,0005,0006,0007,0008,0009,000B,000C,000D,000E,000F,0010,0011,0013,0015,0016,0017,0018,0019,001A,001B,001C,001D,001F,0034,003B,003D,0066,0068,006B,006C,006D,0072,0076,0078,007C,0080,0081,0082,0083,0084,0085,0086,0087,0088,0089,008D,008E,008F,0091,0093,0094,0095,0097,0098,0099,009A,009B,009C,009D,009E,00C0,00E0,00E1,00E3,00E4,00E5,00E6,00E7,0100,0101,0102,0103,0104,0120,0127,0129')
2013-04-10 13:37:08,268 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'aesni_intel'}
2013-04-10 13:37:08,268 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'aesni_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:37:08,268 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'kvm_intel'}
2013-04-10 13:37:08,268 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'kvm_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:37:08,268 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'microcode'}
2013-04-10 13:37:08,268 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'microcode', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:37:08,268 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'coretemp'}
2013-04-10 13:37:08,269 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'coretemp', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:37:08,269 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9111a0c> about HardwareID('modalias', 'wmi:98479A64-33F5-4E33-A707-8E251EBBC3A1')
2013-04-10 13:37:08,269 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9111a0c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-04-10 13:37:08,269 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-10 13:37:08,269 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:37:08,269 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-04-10 13:37:08,269 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:37:08,269 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9111a0c> about HardwareID('modalias', 'wmi:74F1EBB6-927A-4C7D-95DF-698E21E80EB5')
2013-04-10 13:37:08,269 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9111a0c> about HardwareID('modalias', 'acpi:SMO1200:PNP0C31:')
2013-04-10 13:37:08,269 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9111a0c> about HardwareID('modalias', 'input:b0003v5986p0523e1402-e0,1,kD4,ramlsfw')
2013-04-10 13:37:08,269 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-10 13:37:08,269 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:37:08,269 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-04-10 13:37:08,269 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:37:08,269 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9111a0c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2013-04-10 13:37:08,269 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-10 13:37:08,270 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:37:08,270 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-04-10 13:37:08,270 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:37:08,270 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9111a0c> about HardwareID('modalias', 'wmi:7364651A-132F-4FE7-ADAA-40C6C7EE2E3B')
2013-04-10 13:37:08,270 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x93a96cc> about HardwareID('modalias', 'pci:v00008086d00001E3Asv000017AAsd0000500Cbc07sc80i00')
2013-04-10 13:37:08,270 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x93a96cc> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,145,148,14A,14D,14E,14F,ra0,1,18,1C,2F,35,36,39,3A,mlsfw')
2013-04-10 13:37:08,270 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x93a96cc> about HardwareID('modalias', 'acpi:PNP0200:')
2013-04-10 13:37:08,270 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x93a96cc> about HardwareID('modalias', 'acpi:PNP0103:')
2013-04-10 13:37:08,270 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x93a96cc> about HardwareID('modalias', 'acpi:PNP0303:PNP0303:')
2013-04-10 13:37:08,270 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x93a96cc> about HardwareID('modalias', 'pci:v00008086d00000154sv000017AAsd0000500Cbc06sc00i00')
2013-04-10 13:37:08,270 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x93a96cc> about HardwareID('modalias', 'pci:v00008086d00001E31sv000017AAsd0000500Cbc0Csc03i30')
2013-04-10 13:37:08,270 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x93a96cc> about HardwareID('modalias', 'platform:thinkpad_hwmon')
2013-04-10 13:37:08,270 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x93a96cc> about HardwareID('modalias', 'input:b0011v0002p000Ae0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2013-04-10 13:37:08,270 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x93a96cc> about HardwareID('modalias', 'usb:v1D6Bp0002d0305dc09dsc00dp01ic09isc00ip00')
2013-04-10 13:37:08,270 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x93a96cc> about HardwareID('modalias', 'usb:v1D6Bp0003d0305dc09dsc00dp03ic09isc00ip00')
2013-04-10 13:37:08,270 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x93a96cc> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2013-04-10 13:37:08,270 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x93a96cc> about HardwareID('modalias', 'platform:microcode')
2013-04-10 13:37:08,270 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x93a96cc> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2013-04-10 13:37:08,270 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x93a96cc> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-04-10 13:37:08,270 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x93a96cc> about HardwareID('modalias', 'platform:thinkpad_acpi')
2013-04-10 13:37:08,270 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x93a96cc> about HardwareID('modalias', 'acpi:LEN0051:PNP0F13:')
2013-04-10 13:37:08,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x93a96cc> about HardwareID('modalias', 'platform:eisa')
2013-04-10 13:37:08,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x93a96cc> about HardwareID('modalias', 'wmi:7FF47003-3B6C-4E5E-A227-E979824A85D1')
2013-04-10 13:37:08,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x93a96cc> about HardwareID('modalias', 'pci:v00008086d00001E26sv000017AAsd0000500Cbc0Csc03i20')
2013-04-10 13:37:08,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x93a96cc> about HardwareID('modalias', 'wmi:6A4B54EF-A5ED-4D33-9455-B0D9B48DF4B3')
2013-04-10 13:37:08,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x93a96cc> about HardwareID('modalias', 'usb:v0A5Cp21F3d0112dcFFdsc01dp01icFEisc01ip01')
2013-04-10 13:37:08,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x93a96cc> about HardwareID('modalias', 'serio:ty05pr00id00ex00')
2013-04-10 13:37:08,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x93a96cc> about HardwareID('modalias', 'pci:v00008086d00001E58sv000017AAsd0000500Cbc06sc01i00')
2013-04-10 13:37:08,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x93a96cc> about HardwareID('modalias', 'pci:v00008086d00001E03sv000017AAsd0000500Cbc01sc06i01')
2013-04-10 13:37:08,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x93a96cc> about HardwareID('modalias', 'pci:v00008086d00001E2Dsv000017AAsd0000500Cbc0Csc03i20')
2013-04-10 13:37:08,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x93a96cc> about HardwareID('modalias', 'acpi:INT3392:PNP0C02:')
2013-04-10 13:37:08,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x93a96cc> about HardwareID('modalias', 'pci:v00008086d00001E22sv000017AAsd0000500Cbc0Csc05i00')
2013-04-10 13:37:08,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x93a96cc> about HardwareID('modalias', 'acpi:PNP0B00:')
2013-04-10 13:37:08,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x93a96cc> about HardwareID('modalias', 'pci:v000014E4d00004359sv000014E4sd00000607bc02sc80i00')
2013-04-10 13:37:08,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x93a96cc> about HardwareID('modalias', 'usb:v1D6Bp0002d0305dc09dsc00dp00ic09isc00ip00')
2013-04-10 13:37:08,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x93a96cc> about HardwareID('modalias', 'acpi:PNP0C04:')
2013-04-10 13:37:08,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x93a96cc> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2013-04-10 13:37:08,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x93a96cc> about HardwareID('modalias', 'acpi:PNP0100:')
2013-04-10 13:37:08,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x93a96cc> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2013-04-10 13:37:08,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x93a96cc> about HardwareID('modalias', 'input:b0019v17AAp5054e4101-e0,1,4,5,k71,72,73,8E,94,98,BF,C2,CD,D4,E0,E1,E3,E4,EC,EE,F0,F8,174,1D2,1DB,1DC,ram4,lsfw1,3,')
2013-04-10 13:37:08,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x93a96cc> about HardwareID('modalias', 'usb:v0A5Cp21F3d0112dcFFdsc01dp01icFFiscFFipFF')
2013-04-10 13:37:08,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x93a96cc> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2013-04-10 13:37:08,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x93a96cc> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2013-04-10 13:37:08,272 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x93a96cc> about HardwareID('modalias', 'wmi:E2BE5EE3-42DA-49DB-8378-1F5247388202')
2013-04-10 13:37:08,272 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x93a96cc> about HardwareID('modalias', 'acpi:PNP0C02:')
2013-04-10 13:37:08,272 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x93a96cc> about HardwareID('modalias', 'dmi:bvnLENOVO:bvrH6ET90WW(2.08):bd01/11/2013:svnLENOVO:pn3351CTO:pvrThinkPadT430u:rvnLENOVO:rn3351CTO:rvrNotDefined:cvnLENOVO:ct10:cvrNotAvailable:')
2013-04-10 13:37:08,272 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x93a96cc> about HardwareID('modalias', 'wmi:FCB424F1-075A-4E0E-BFC4-62F3E71771FA')
2013-04-10 13:37:08,272 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x93a96cc> about HardwareID('modalias', 'pci:v000010ECd00008168sv000017AAsd0000500Cbc02sc00i00')
2013-04-10 13:37:08,272 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x93a96cc> about HardwareID('modalias', 'wmi:7430019A-DCE9-4548-BAB0-9FDE0935CAFF')
2013-04-10 13:37:08,272 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x93a96cc> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2013-04-10 13:37:08,272 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x93a96cc> about HardwareID('modalias', 'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2013-04-10 13:37:08,272 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x93a96cc> about HardwareID('modalias', 'usb:v5986p0523d1402dcEFdsc02dp01ic0Eisc02ip00')
2013-04-10 13:37:08,272 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x93a96cc> about HardwareID('modalias', 'pci:v00008086d00000166sv000017AAsd0000500Cbc03sc00i00')
2013-04-10 13:37:08,272 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x93a96cc> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2013-04-10 13:37:08,272 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x93a96cc> about HardwareID('modalias', 'pci:v000010ECd00005209sv000010ECsd00005209bc08sc05i00')
2013-04-10 13:37:08,272 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x93a96cc> about HardwareID('modalias', 'acpi:PNP0000:')
2013-04-10 13:37:08,272 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x93a96cc> about HardwareID('modalias', 'usb:v0A5Cp21F3d0112dcFFdsc01dp01icFFisc01ip01')
2013-04-10 13:37:08,272 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x93a96cc> about HardwareID('modalias', 'wmi:8ADB159E-1E32-455C-BC93-308A7ED98246')
2013-04-10 13:37:08,272 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x93a96cc> about HardwareID('modalias', 'pci:v00008086d00001E20sv000017AAsd0000500Cbc04sc03i00')
2013-04-10 13:37:08,272 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x93a96cc> about HardwareID('modalias', 'acpi:INT0800:')
2013-04-10 13:37:08,272 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x93a96cc> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2013-04-10 13:37:08,272 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x93a96cc> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-04-10 13:37:08,272 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x93a96cc> about HardwareID('modalias', 'wmi:7EEF04FF-4328-447C-B5BB-D449925D538D')
2013-04-10 13:37:08,272 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x93a96cc> about HardwareID('modalias', 'pci:v000010ECd00005209sv000010ECsd00005209bcFFsc00i00')
2013-04-10 13:37:08,272 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x93a96cc> about HardwareID('modalias', 'wmi:51F5230E-9677-46CD-A1CF-C0B23EE34DB7')
2013-04-10 13:37:08,272 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x93a96cc> about HardwareID('modalias', 'usb:v5986p0523d1402dcEFdsc02dp01ic0Eisc01ip00')
2013-04-10 13:37:08,273 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x93a96cc> about HardwareID('modalias', 'wmi:2651D9FD-911C-4B69-B94E-D0DED5963BD7')
2013-04-10 13:37:08,273 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x93a96cc> about HardwareID('modalias', 'platform:pcspkr')
2013-04-10 13:37:08,273 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x93a96cc> about HardwareID('modalias', 'platform:coretemp')
2013-04-10 13:37:08,273 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x93a96cc> about HardwareID('modalias', 'x86cpu:vendor:0000:family:0006:model:003A:feature:,0000,0001,0002,0003,0004,0005,0006,0007,0008,0009,000B,000C,000D,000E,000F,0010,0011,0013,0015,0016,0017,0018,0019,001A,001B,001C,001D,001F,0034,003B,003D,0066,0068,006B,006C,006D,0072,0076,0078,007C,0080,0081,0082,0083,0084,0085,0086,0087,0088,0089,008D,008E,008F,0091,0093,0094,0095,0097,0098,0099,009A,009B,009C,009D,009E,00C0,00E0,00E1,00E3,00E4,00E5,00E6,00E7,0100,0101,0102,0103,0104,0120,0127,0129')
2013-04-10 13:37:08,273 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x93a96cc> about HardwareID('modalias', 'wmi:98479A64-33F5-4E33-A707-8E251EBBC3A1')
2013-04-10 13:37:08,273 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x93a96cc> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-04-10 13:37:08,273 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x93a96cc> about HardwareID('modalias', 'wmi:74F1EBB6-927A-4C7D-95DF-698E21E80EB5')
2013-04-10 13:37:08,273 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x93a96cc> about HardwareID('modalias', 'acpi:SMO1200:PNP0C31:')
2013-04-10 13:37:08,273 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x93a96cc> about HardwareID('modalias', 'input:b0003v5986p0523e1402-e0,1,kD4,ramlsfw')
2013-04-10 13:37:08,273 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x93a96cc> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2013-04-10 13:37:08,273 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x93a96cc> about HardwareID('modalias', 'wmi:7364651A-132F-4FE7-ADAA-40C6C7EE2E3B')
2013-04-10 13:37:08,339 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-04-10 13:37:08,355 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-04-10 13:37:08,363 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-04-10 13:37:08,389 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-04-10 13:37:08,397 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-04-10 13:37:08,404 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-04-10 13:37:08,455 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-04-10 13:37:08,458 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-04-10 13:37:08,462 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-04-10 13:37:16,046 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-04-10 13:37:22,407 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2013-04-10 13:37:22,407 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2013-04-10 13:37:22,436 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-04-10 13:49:50,243 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-04-10 13:49:53,251 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2013-04-10 13:49:53,252 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2013-04-10 13:49:53,269 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-04-10 13:49:54,763 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-04-10 13:49:54,793 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-04-10 13:49:54,827 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-04-10 13:50:41,059 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-04-10 13:50:41,304 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2013-04-10 13:50:41,305 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2013-04-10 13:50:41,332 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-04-10 13:50:42,543 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-04-10 13:50:42,578 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-04-10 13:50:42,628 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-04-10 13:50:43,537 DEBUG: Shutting down
2013-04-10 13:51:51,412 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x8af4a0c>
2013-04-10 13:51:52,738 DEBUG: reading modalias file /lib/modules/3.5.0-23-generic/modules.alias
2013-04-10 13:51:52,806 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2013-04-10 13:51:52,807 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2013-04-10 13:51:52,841 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2013-04-10 13:51:52,846 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2013-04-10 13:51:52,854 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2013-04-10 13:51:52,854 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2013-04-10 13:51:52,854 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2013-04-10 13:51:52,857 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2013-04-10 13:51:52,857 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2013-04-10 13:51:52,857 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2013-04-10 13:51:52,858 DEBUG: loading custom handler /usr/share/jockey/handlers/cdv.py
2013-04-10 13:51:52,862 WARNING: modinfo for module cedarview_gfx failed: ERROR: modinfo: could not find module cedarview_gfx

2013-04-10 13:51:52,862 DEBUG: Instantiated Handler subclass __builtin__.CdvDriver from name CdvDriver
2013-04-10 13:51:52,862 DEBUG: cdv.available: falling back to default
2013-04-10 13:51:52,964 DEBUG: XorgDriverHandler(cedarview_gfx, cedarview-graphics-drivers, None): Disabling as package is not compatible with Q-LTS X.org
2013-04-10 13:51:52,964 DEBUG: Intel Cedarview graphics driver not available
2013-04-10 13:51:52,964 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2013-04-10 13:51:52,969 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2013-04-10 13:51:52,971 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2013-04-10 13:51:52,972 DEBUG: Disabling Nvidia driver on intel/hybrid system
2013-04-10 13:51:52,972 DEBUG: NVIDIA accelerated graphics driver not available
2013-04-10 13:51:52,974 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2013-04-10 13:51:52,976 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2013-04-10 13:51:52,976 DEBUG: Disabling Nvidia driver on intel/hybrid system
2013-04-10 13:51:52,976 DEBUG: NVIDIA accelerated graphics driver not available
2013-04-10 13:51:52,978 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2013-04-10 13:51:52,981 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2013-04-10 13:51:52,981 DEBUG: Disabling Nvidia driver on intel/hybrid system
2013-04-10 13:51:52,981 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2013-04-10 13:51:52,983 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2013-04-10 13:51:52,985 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2013-04-10 13:51:52,985 DEBUG: Disabling Nvidia driver on intel/hybrid system
2013-04-10 13:51:52,986 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2013-04-10 13:51:52,987 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2013-04-10 13:51:52,990 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2013-04-10 13:51:52,990 DEBUG: Disabling Nvidia driver on intel/hybrid system
2013-04-10 13:51:52,990 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2013-04-10 13:51:52,992 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2013-04-10 13:51:52,994 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2013-04-10 13:51:52,995 DEBUG: Disabling Nvidia driver on intel/hybrid system
2013-04-10 13:51:52,995 DEBUG: NVIDIA accelerated graphics driver not available
2013-04-10 13:51:52,997 WARNING: modinfo for module nvidia_experimental_310 failed: ERROR: modinfo: could not find module nvidia_experimental_310

2013-04-10 13:51:53,007 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverExperimental310 from name NvidiaDriverExperimental310
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 972, in get_handlers
    desc = inst.name()
  File "/usr/lib/python2.7/dist-packages/jockey/handlers.py", line 108, in name
    self._package_defaults()
  File "/usr/lib/python2.7/dist-packages/jockey/handlers.py", line 93, in _package_defaults
    (distro_name, distro_desc) = OSLib.inst.package_description(self.package)
  File "/usr/lib/python2.7/dist-packages/jockey/oslib.py", line 216, in package_description
    raise ValueError('package %s does not exist' % package)
ValueError: package nvidia-experimental-310 does not exist
2013-04-10 13:51:53,012 WARNING: modinfo for module nvidia_experimental_304 failed: ERROR: modinfo: could not find module nvidia_experimental_304

2013-04-10 13:51:53,022 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverExperimental304 from name NvidiaDriverExperimental304
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 972, in get_handlers
    desc = inst.name()
  File "/usr/lib/python2.7/dist-packages/jockey/handlers.py", line 108, in name
    self._package_defaults()
  File "/usr/lib/python2.7/dist-packages/jockey/handlers.py", line 93, in _package_defaults
    (distro_name, distro_desc) = OSLib.inst.package_description(self.package)
  File "/usr/lib/python2.7/dist-packages/jockey/oslib.py", line 216, in package_description
    raise ValueError('package %s does not exist' % package)
ValueError: package nvidia-experimental-304 does not exist
2013-04-10 13:51:53,022 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2013-04-10 13:51:53,032 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2013-04-10 13:51:53,038 DEBUG: Software modem not available
2013-04-10 13:51:53,038 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2013-04-10 13:51:53,041 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2013-04-10 13:51:53,044 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2013-04-10 13:51:53,138 DEBUG: XorgDriverHandler(omapdrm_pvr, pvr-omap4, None): Disabling as package is not compatible with Q-LTS X.org
2013-04-10 13:51:53,138 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2013-04-10 13:51:53,138 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2013-04-10 13:51:53,141 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2013-04-10 13:51:53,141 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2013-04-10 13:51:53,150 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2013-04-10 13:51:53,151 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2013-04-10 13:51:53,163 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2013-04-10 13:51:53,163 DEBUG: Firmware for DVB cards not available
2013-04-10 13:51:53,163 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2013-04-10 13:51:53,167 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2013-04-10 13:51:53,169 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2013-04-10 13:51:53,169 DEBUG: fglrx.available: falling back to default
2013-04-10 13:51:53,265 DEBUG: XorgDriverHandler(fglrx_updates, fglrx-updates, None): Disabling as package is not compatible with Q-LTS X.org
2013-04-10 13:51:53,265 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) not available
2013-04-10 13:51:53,267 WARNING: modinfo for module fglrx_experimental_9 failed: ERROR: modinfo: could not find module fglrx_experimental_9

2013-04-10 13:51:53,277 DEBUG: Could not instantiate Handler subclass __builtin__.FglrxDriverExperimental9 from name FglrxDriverExperimental9
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 972, in get_handlers
    desc = inst.name()
  File "/usr/lib/python2.7/dist-packages/jockey/handlers.py", line 108, in name
    self._package_defaults()
  File "/usr/lib/python2.7/dist-packages/jockey/handlers.py", line 93, in _package_defaults
    (distro_name, distro_desc) = OSLib.inst.package_description(self.package)
  File "/usr/lib/python2.7/dist-packages/jockey/oslib.py", line 216, in package_description
    raise ValueError('package %s does not exist' % package)
ValueError: package fglrx-experimental-9 does not exist
2013-04-10 13:51:53,279 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2013-04-10 13:51:53,282 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2013-04-10 13:51:53,282 DEBUG: fglrx.available: falling back to default
2013-04-10 13:51:53,376 DEBUG: XorgDriverHandler(fglrx, fglrx, None): Disabling as package is not compatible with Q-LTS X.org
2013-04-10 13:51:53,377 DEBUG: ATI/AMD proprietary FGLRX graphics driver not available
2013-04-10 13:51:53,377 DEBUG: all custom handlers loaded
2013-04-10 13:51:53,377 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8af4a0c> about HardwareID('modalias', 'pci:v00008086d00001E3Asv000017AAsd0000500Cbc07sc80i00')
2013-04-10 13:51:53,586 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mei'}
2013-04-10 13:51:53,632 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mei', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:51:53,632 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8af4a0c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,145,148,14A,14D,14E,14F,ra0,1,18,1C,2F,35,36,39,3A,mlsfw')
2013-04-10 13:51:53,635 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-10 13:51:53,635 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:51:53,636 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2013-04-10 13:51:53,636 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:51:53,636 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2013-04-10 13:51:53,636 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:51:53,636 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2013-04-10 13:51:53,636 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:51:53,636 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-04-10 13:51:53,636 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:51:53,636 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8af4a0c> about HardwareID('modalias', 'acpi:PNP0200:')
2013-04-10 13:51:53,636 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8af4a0c> about HardwareID('modalias', 'acpi:PNP0103:')
2013-04-10 13:51:53,636 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8af4a0c> about HardwareID('modalias', 'acpi:PNP0303:PNP0303:')
2013-04-10 13:51:53,636 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8af4a0c> about HardwareID('modalias', 'pci:v00008086d00000154sv000017AAsd0000500Cbc06sc00i00')
2013-04-10 13:51:53,639 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8af4a0c> about HardwareID('modalias', 'pci:v00008086d00001E31sv000017AAsd0000500Cbc0Csc03i30')
2013-04-10 13:51:53,641 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8af4a0c> about HardwareID('modalias', 'platform:thinkpad_hwmon')
2013-04-10 13:51:53,641 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8af4a0c> about HardwareID('modalias', 'input:b0011v0002p000Ae0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2013-04-10 13:51:53,641 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-10 13:51:53,642 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:51:53,642 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-04-10 13:51:53,642 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:51:53,642 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8af4a0c> about HardwareID('modalias', 'usb:v1D6Bp0002d0305dc09dsc00dp01ic09isc00ip00')
2013-04-10 13:51:53,652 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8af4a0c> about HardwareID('modalias', 'usb:v1D6Bp0003d0305dc09dsc00dp03ic09isc00ip00')
2013-04-10 13:51:53,652 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8af4a0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2013-04-10 13:51:53,652 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-10 13:51:53,652 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:51:53,652 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8af4a0c> about HardwareID('modalias', 'platform:microcode')
2013-04-10 13:51:53,652 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8af4a0c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2013-04-10 13:51:53,653 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8af4a0c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-04-10 13:51:53,653 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8af4a0c> about HardwareID('modalias', 'platform:thinkpad_acpi')
2013-04-10 13:51:53,653 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8af4a0c> about HardwareID('modalias', 'acpi:LEN0051:PNP0F13:')
2013-04-10 13:51:53,653 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8af4a0c> about HardwareID('modalias', 'platform:eisa')
2013-04-10 13:51:53,653 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8af4a0c> about HardwareID('modalias', 'wmi:7FF47003-3B6C-4E5E-A227-E979824A85D1')
2013-04-10 13:51:53,653 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8af4a0c> about HardwareID('modalias', 'pci:v00008086d00001E26sv000017AAsd0000500Cbc0Csc03i20')
2013-04-10 13:51:53,656 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8af4a0c> about HardwareID('modalias', 'wmi:6A4B54EF-A5ED-4D33-9455-B0D9B48DF4B3')
2013-04-10 13:51:53,656 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8af4a0c> about HardwareID('modalias', 'usb:v0A5Cp21F3d0112dcFFdsc01dp01icFEisc01ip01')
2013-04-10 13:51:53,657 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8af4a0c> about HardwareID('modalias', 'serio:ty05pr00id00ex00')
2013-04-10 13:51:53,663 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2013-04-10 13:51:53,663 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:51:53,663 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8af4a0c> about HardwareID('modalias', 'pci:v00008086d00001E58sv000017AAsd0000500Cbc06sc01i00')
2013-04-10 13:51:53,665 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'lpc_ich'}
2013-04-10 13:51:53,665 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'lpc_ich', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:51:53,665 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8af4a0c> about HardwareID('modalias', 'pci:v00008086d00001E03sv000017AAsd0000500Cbc01sc06i01')
2013-04-10 13:51:53,668 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8af4a0c> about HardwareID('modalias', 'pci:v00008086d00001E2Dsv000017AAsd0000500Cbc0Csc03i20')
2013-04-10 13:51:53,670 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8af4a0c> about HardwareID('modalias', 'acpi:INT3392:PNP0C02:')
2013-04-10 13:51:53,670 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8af4a0c> about HardwareID('modalias', 'pci:v00008086d00001E22sv000017AAsd0000500Cbc0Csc05i00')
2013-04-10 13:51:53,672 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801'}
2013-04-10 13:51:53,672 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:51:53,672 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8af4a0c> about HardwareID('modalias', 'acpi:PNP0B00:')
2013-04-10 13:51:53,672 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8af4a0c> about HardwareID('modalias', 'pci:v000014E4d00004359sv000014E4sd00000607bc02sc80i00')
2013-04-10 13:51:53,702 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'wl', 'package': 'bcmwl-kernel-source'}
2013-04-10 13:51:53,703 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-04-10 13:51:53,702 DEBUG: found match in handler pool kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2013-04-10 13:51:53,705 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2013-04-10 13:51:53,705 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-04-10 13:51:53,705 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2013-04-10 13:51:53,705 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8af4a0c> about HardwareID('modalias', 'usb:v1D6Bp0002d0305dc09dsc00dp00ic09isc00ip00')
2013-04-10 13:51:53,705 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8af4a0c> about HardwareID('modalias', 'acpi:PNP0C04:')
2013-04-10 13:51:53,705 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8af4a0c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2013-04-10 13:51:53,706 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2013-04-10 13:51:53,706 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:51:53,706 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2013-04-10 13:51:53,706 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:51:53,706 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8af4a0c> about HardwareID('modalias', 'acpi:PNP0100:')
2013-04-10 13:51:53,706 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8af4a0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2013-04-10 13:51:53,706 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-10 13:51:53,706 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:51:53,706 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8af4a0c> about HardwareID('modalias', 'input:b0019v17AAp5054e4101-e0,1,4,5,k71,72,73,8E,94,98,BF,C2,CD,D4,E0,E1,E3,E4,EC,EE,F0,F8,174,1D2,1DB,1DC,ram4,lsfw1,3,')
2013-04-10 13:51:53,706 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-10 13:51:53,706 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:51:53,706 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-04-10 13:51:53,706 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:51:53,707 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8af4a0c> about HardwareID('modalias', 'usb:v0A5Cp21F3d0112dcFFdsc01dp01icFFiscFFipFF')
2013-04-10 13:51:53,707 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8af4a0c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2013-04-10 13:51:53,707 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-10 13:51:53,707 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:51:53,707 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-04-10 13:51:53,707 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:51:53,707 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8af4a0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2013-04-10 13:51:53,707 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-10 13:51:53,707 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:51:53,707 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8af4a0c> about HardwareID('modalias', 'wmi:E2BE5EE3-42DA-49DB-8378-1F5247388202')
2013-04-10 13:51:53,707 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8af4a0c> about HardwareID('modalias', 'acpi:PNP0C02:')
2013-04-10 13:51:53,707 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8af4a0c> about HardwareID('modalias', 'dmi:bvnLENOVO:bvrH6ET90WW(2.08):bd01/11/2013:svnLENOVO:pn3351CTO:pvrThinkPadT430u:rvnLENOVO:rn3351CTO:rvrNotDefined:cvnLENOVO:ct10:cvrNotAvailable:')
2013-04-10 13:51:53,716 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8af4a0c> about HardwareID('modalias', 'wmi:FCB424F1-075A-4E0E-BFC4-62F3E71771FA')
2013-04-10 13:51:53,716 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8af4a0c> about HardwareID('modalias', 'pci:v000010ECd00008168sv000017AAsd0000500Cbc02sc00i00')
2013-04-10 13:51:53,722 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2013-04-10 13:51:53,722 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:51:53,722 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8af4a0c> about HardwareID('modalias', 'wmi:7430019A-DCE9-4548-BAB0-9FDE0935CAFF')
2013-04-10 13:51:53,722 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8af4a0c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2013-04-10 13:51:53,722 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-10 13:51:53,722 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:51:53,722 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-04-10 13:51:53,723 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:51:53,723 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8af4a0c> about HardwareID('modalias', 'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2013-04-10 13:51:53,723 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8af4a0c> about HardwareID('modalias', 'usb:v5986p0523d1402dcEFdsc02dp01ic0Eisc02ip00')
2013-04-10 13:51:53,723 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8af4a0c> about HardwareID('modalias', 'pci:v00008086d00000166sv000017AAsd0000500Cbc03sc00i00')
2013-04-10 13:51:53,725 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i915'}
2013-04-10 13:51:53,725 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:51:53,726 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8af4a0c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2013-04-10 13:51:53,726 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-10 13:51:53,726 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:51:53,726 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8af4a0c> about HardwareID('modalias', 'pci:v000010ECd00005209sv000010ECsd00005209bc08sc05i00')
2013-04-10 13:51:53,726 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci'}
2013-04-10 13:51:53,726 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:51:53,726 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8af4a0c> about HardwareID('modalias', 'acpi:PNP0000:')
2013-04-10 13:51:53,726 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8af4a0c> about HardwareID('modalias', 'usb:v0A5Cp21F3d0112dcFFdsc01dp01icFFisc01ip01')
2013-04-10 13:51:53,726 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2013-04-10 13:51:53,726 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:51:53,726 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8af4a0c> about HardwareID('modalias', 'wmi:8ADB159E-1E32-455C-BC93-308A7ED98246')
2013-04-10 13:51:53,726 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8af4a0c> about HardwareID('modalias', 'pci:v00008086d00001E20sv000017AAsd0000500Cbc04sc03i00')
2013-04-10 13:51:53,729 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-04-10 13:51:53,729 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:51:53,729 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-04-10 13:51:53,729 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:51:53,729 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8af4a0c> about HardwareID('modalias', 'acpi:INT0800:')
2013-04-10 13:51:53,729 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8af4a0c> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2013-04-10 13:51:53,729 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8af4a0c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-04-10 13:51:53,730 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8af4a0c> about HardwareID('modalias', 'wmi:7EEF04FF-4328-447C-B5BB-D449925D538D')
2013-04-10 13:51:53,730 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8af4a0c> about HardwareID('modalias', 'pci:v000010ECd00005209sv000010ECsd00005209bcFFsc00i00')
2013-04-10 13:51:53,730 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'rts_pstor'}
2013-04-10 13:51:53,730 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'rts_pstor', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:51:53,730 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8af4a0c> about HardwareID('modalias', 'wmi:51F5230E-9677-46CD-A1CF-C0B23EE34DB7')
2013-04-10 13:51:53,730 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8af4a0c> about HardwareID('modalias', 'usb:v5986p0523d1402dcEFdsc02dp01ic0Eisc01ip00')
2013-04-10 13:51:53,731 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2013-04-10 13:51:53,731 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:51:53,731 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8af4a0c> about HardwareID('modalias', 'wmi:2651D9FD-911C-4B69-B94E-D0DED5963BD7')
2013-04-10 13:51:53,731 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8af4a0c> about HardwareID('modalias', 'platform:pcspkr')
2013-04-10 13:51:53,731 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2013-04-10 13:51:53,731 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:51:53,731 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2013-04-10 13:51:53,731 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:51:53,731 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8af4a0c> about HardwareID('modalias', 'platform:coretemp')
2013-04-10 13:51:53,732 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8af4a0c> about HardwareID('modalias', 'x86cpu:vendor:0000:family:0006:model:003A:feature:,0000,0001,0002,0003,0004,0005,0006,0007,0008,0009,000B,000C,000D,000E,000F,0010,0011,0013,0015,0016,0017,0018,0019,001A,001B,001C,001D,001F,0034,003B,003D,0066,0068,006B,006C,006D,0072,0076,0078,007C,0080,0081,0082,0083,0084,0085,0086,0087,0088,0089,008D,008E,008F,0091,0093,0094,0095,0097,0098,0099,009A,009B,009C,009D,009E,00C0,00E0,00E1,00E3,00E4,00E5,00E6,00E7,0100,0101,0102,0103,0104,0120,0127,0129')
2013-04-10 13:51:53,736 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'aesni_intel'}
2013-04-10 13:51:53,736 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'aesni_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:51:53,736 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'kvm_intel'}
2013-04-10 13:51:53,736 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'kvm_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:51:53,736 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'microcode'}
2013-04-10 13:51:53,736 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'microcode', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:51:53,736 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'coretemp'}
2013-04-10 13:51:53,736 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'coretemp', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:51:53,737 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8af4a0c> about HardwareID('modalias', 'wmi:98479A64-33F5-4E33-A707-8E251EBBC3A1')
2013-04-10 13:51:53,737 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8af4a0c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-04-10 13:51:53,737 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-10 13:51:53,737 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:51:53,737 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-04-10 13:51:53,737 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:51:53,737 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8af4a0c> about HardwareID('modalias', 'wmi:74F1EBB6-927A-4C7D-95DF-698E21E80EB5')
2013-04-10 13:51:53,737 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8af4a0c> about HardwareID('modalias', 'acpi:SMO1200:PNP0C31:')
2013-04-10 13:51:53,737 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8af4a0c> about HardwareID('modalias', 'input:b0003v5986p0523e1402-e0,1,kD4,ramlsfw')
2013-04-10 13:51:53,737 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-10 13:51:53,737 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:51:53,737 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-04-10 13:51:53,737 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:51:53,737 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8af4a0c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2013-04-10 13:51:53,737 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-10 13:51:53,738 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:51:53,738 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-04-10 13:51:53,738 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-10 13:51:53,738 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8af4a0c> about HardwareID('modalias', 'wmi:7364651A-132F-4FE7-ADAA-40C6C7EE2E3B')
2013-04-10 13:51:53,738 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d8c6ac> about HardwareID('modalias', 'pci:v00008086d00001E3Asv000017AAsd0000500Cbc07sc80i00')
2013-04-10 13:51:53,738 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d8c6ac> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,145,148,14A,14D,14E,14F,ra0,1,18,1C,2F,35,36,39,3A,mlsfw')
2013-04-10 13:51:53,738 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d8c6ac> about HardwareID('modalias', 'acpi:PNP0200:')
2013-04-10 13:51:53,738 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d8c6ac> about HardwareID('modalias', 'acpi:PNP0103:')
2013-04-10 13:51:53,738 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d8c6ac> about HardwareID('modalias', 'acpi:PNP0303:PNP0303:')
2013-04-10 13:51:53,738 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d8c6ac> about HardwareID('modalias', 'pci:v00008086d00000154sv000017AAsd0000500Cbc06sc00i00')
2013-04-10 13:51:53,738 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d8c6ac> about HardwareID('modalias', 'pci:v00008086d00001E31sv000017AAsd0000500Cbc0Csc03i30')
2013-04-10 13:51:53,738 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d8c6ac> about HardwareID('modalias', 'platform:thinkpad_hwmon')
2013-04-10 13:51:53,738 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d8c6ac> about HardwareID('modalias', 'input:b0011v0002p000Ae0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2013-04-10 13:51:53,738 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d8c6ac> about HardwareID('modalias', 'usb:v1D6Bp0002d0305dc09dsc00dp01ic09isc00ip00')
2013-04-10 13:51:53,738 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d8c6ac> about HardwareID('modalias', 'usb:v1D6Bp0003d0305dc09dsc00dp03ic09isc00ip00')
2013-04-10 13:51:53,738 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d8c6ac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2013-04-10 13:51:53,738 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d8c6ac> about HardwareID('modalias', 'platform:microcode')
2013-04-10 13:51:53,738 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d8c6ac> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2013-04-10 13:51:53,738 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d8c6ac> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-04-10 13:51:53,738 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d8c6ac> about HardwareID('modalias', 'platform:thinkpad_acpi')
2013-04-10 13:51:53,738 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d8c6ac> about HardwareID('modalias', 'acpi:LEN0051:PNP0F13:')
2013-04-10 13:51:53,738 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d8c6ac> about HardwareID('modalias', 'platform:eisa')
2013-04-10 13:51:53,739 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d8c6ac> about HardwareID('modalias', 'wmi:7FF47003-3B6C-4E5E-A227-E979824A85D1')
2013-04-10 13:51:53,739 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d8c6ac> about HardwareID('modalias', 'pci:v00008086d00001E26sv000017AAsd0000500Cbc0Csc03i20')
2013-04-10 13:51:53,739 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d8c6ac> about HardwareID('modalias', 'wmi:6A4B54EF-A5ED-4D33-9455-B0D9B48DF4B3')
2013-04-10 13:51:53,739 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d8c6ac> about HardwareID('modalias', 'usb:v0A5Cp21F3d0112dcFFdsc01dp01icFEisc01ip01')
2013-04-10 13:51:53,739 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d8c6ac> about HardwareID('modalias', 'serio:ty05pr00id00ex00')
2013-04-10 13:51:53,739 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d8c6ac> about HardwareID('modalias', 'pci:v00008086d00001E58sv000017AAsd0000500Cbc06sc01i00')
2013-04-10 13:51:53,739 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d8c6ac> about HardwareID('modalias', 'pci:v00008086d00001E03sv000017AAsd0000500Cbc01sc06i01')
2013-04-10 13:51:53,739 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d8c6ac> about HardwareID('modalias', 'pci:v00008086d00001E2Dsv000017AAsd0000500Cbc0Csc03i20')
2013-04-10 13:51:53,739 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d8c6ac> about HardwareID('modalias', 'acpi:INT3392:PNP0C02:')
2013-04-10 13:51:53,739 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d8c6ac> about HardwareID('modalias', 'pci:v00008086d00001E22sv000017AAsd0000500Cbc0Csc05i00')
2013-04-10 13:51:53,739 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d8c6ac> about HardwareID('modalias', 'acpi:PNP0B00:')
2013-04-10 13:51:53,739 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d8c6ac> about HardwareID('modalias', 'pci:v000014E4d00004359sv000014E4sd00000607bc02sc80i00')
2013-04-10 13:51:53,739 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d8c6ac> about HardwareID('modalias', 'usb:v1D6Bp0002d0305dc09dsc00dp00ic09isc00ip00')
2013-04-10 13:51:53,739 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d8c6ac> about HardwareID('modalias', 'acpi:PNP0C04:')
2013-04-10 13:51:53,739 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d8c6ac> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2013-04-10 13:51:53,739 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d8c6ac> about HardwareID('modalias', 'acpi:PNP0100:')
2013-04-10 13:51:53,739 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d8c6ac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2013-04-10 13:51:53,739 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d8c6ac> about HardwareID('modalias', 'input:b0019v17AAp5054e4101-e0,1,4,5,k71,72,73,8E,94,98,BF,C2,CD,D4,E0,E1,E3,E4,EC,EE,F0,F8,174,1D2,1DB,1DC,ram4,lsfw1,3,')
2013-04-10 13:51:53,739 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d8c6ac> about HardwareID('modalias', 'usb:v0A5Cp21F3d0112dcFFdsc01dp01icFFiscFFipFF')
2013-04-10 13:51:53,739 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d8c6ac> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2013-04-10 13:51:53,739 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d8c6ac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2013-04-10 13:51:53,739 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d8c6ac> about HardwareID('modalias', 'wmi:E2BE5EE3-42DA-49DB-8378-1F5247388202')
2013-04-10 13:51:53,739 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d8c6ac> about HardwareID('modalias', 'acpi:PNP0C02:')
2013-04-10 13:51:53,740 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d8c6ac> about HardwareID('modalias', 'dmi:bvnLENOVO:bvrH6ET90WW(2.08):bd01/11/2013:svnLENOVO:pn3351CTO:pvrThinkPadT430u:rvnLENOVO:rn3351CTO:rvrNotDefined:cvnLENOVO:ct10:cvrNotAvailable:')
2013-04-10 13:51:53,740 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d8c6ac> about HardwareID('modalias', 'wmi:FCB424F1-075A-4E0E-BFC4-62F3E71771FA')
2013-04-10 13:51:53,740 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d8c6ac> about HardwareID('modalias', 'pci:v000010ECd00008168sv000017AAsd0000500Cbc02sc00i00')
2013-04-10 13:51:53,740 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d8c6ac> about HardwareID('modalias', 'wmi:7430019A-DCE9-4548-BAB0-9FDE0935CAFF')
2013-04-10 13:51:53,740 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d8c6ac> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2013-04-10 13:51:53,740 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d8c6ac> about HardwareID('modalias', 'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2013-04-10 13:51:53,740 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d8c6ac> about HardwareID('modalias', 'usb:v5986p0523d1402dcEFdsc02dp01ic0Eisc02ip00')
2013-04-10 13:51:53,740 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d8c6ac> about HardwareID('modalias', 'pci:v00008086d00000166sv000017AAsd0000500Cbc03sc00i00')
2013-04-10 13:51:53,740 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d8c6ac> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2013-04-10 13:51:53,740 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d8c6ac> about HardwareID('modalias', 'pci:v000010ECd00005209sv000010ECsd00005209bc08sc05i00')
2013-04-10 13:51:53,740 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d8c6ac> about HardwareID('modalias', 'acpi:PNP0000:')
2013-04-10 13:51:53,740 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d8c6ac> about HardwareID('modalias', 'usb:v0A5Cp21F3d0112dcFFdsc01dp01icFFisc01ip01')
2013-04-10 13:51:53,740 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d8c6ac> about HardwareID('modalias', 'wmi:8ADB159E-1E32-455C-BC93-308A7ED98246')
2013-04-10 13:51:53,740 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d8c6ac> about HardwareID('modalias', 'pci:v00008086d00001E20sv000017AAsd0000500Cbc04sc03i00')
2013-04-10 13:51:53,740 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d8c6ac> about HardwareID('modalias', 'acpi:INT0800:')
2013-04-10 13:51:53,740 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d8c6ac> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2013-04-10 13:51:53,740 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d8c6ac> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-04-10 13:51:53,740 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d8c6ac> about HardwareID('modalias', 'wmi:7EEF04FF-4328-447C-B5BB-D449925D538D')
2013-04-10 13:51:53,740 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d8c6ac> about HardwareID('modalias', 'pci:v000010ECd00005209sv000010ECsd00005209bcFFsc00i00')
2013-04-10 13:51:53,740 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d8c6ac> about HardwareID('modalias', 'wmi:51F5230E-9677-46CD-A1CF-C0B23EE34DB7')
2013-04-10 13:51:53,740 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d8c6ac> about HardwareID('modalias', 'usb:v5986p0523d1402dcEFdsc02dp01ic0Eisc01ip00')
2013-04-10 13:51:53,740 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d8c6ac> about HardwareID('modalias', 'wmi:2651D9FD-911C-4B69-B94E-D0DED5963BD7')
2013-04-10 13:51:53,741 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d8c6ac> about HardwareID('modalias', 'platform:pcspkr')
2013-04-10 13:51:53,741 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d8c6ac> about HardwareID('modalias', 'platform:coretemp')
2013-04-10 13:51:53,741 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d8c6ac> about HardwareID('modalias', 'x86cpu:vendor:0000:family:0006:model:003A:feature:,0000,0001,0002,0003,0004,0005,0006,0007,0008,0009,000B,000C,000D,000E,000F,0010,0011,0013,0015,0016,0017,0018,0019,001A,001B,001C,001D,001F,0034,003B,003D,0066,0068,006B,006C,006D,0072,0076,0078,007C,0080,0081,0082,0083,0084,0085,0086,0087,0088,0089,008D,008E,008F,0091,0093,0094,0095,0097,0098,0099,009A,009B,009C,009D,009E,00C0,00E0,00E1,00E3,00E4,00E5,00E6,00E7,0100,0101,0102,0103,0104,0120,0127,0129')
2013-04-10 13:51:53,741 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d8c6ac> about HardwareID('modalias', 'wmi:98479A64-33F5-4E33-A707-8E251EBBC3A1')
2013-04-10 13:51:53,741 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d8c6ac> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-04-10 13:51:53,741 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d8c6ac> about HardwareID('modalias', 'wmi:74F1EBB6-927A-4C7D-95DF-698E21E80EB5')
2013-04-10 13:51:53,741 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d8c6ac> about HardwareID('modalias', 'acpi:SMO1200:PNP0C31:')
2013-04-10 13:51:53,741 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d8c6ac> about HardwareID('modalias', 'input:b0003v5986p0523e1402-e0,1,kD4,ramlsfw')
2013-04-10 13:51:53,741 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d8c6ac> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2013-04-10 13:51:53,741 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8d8c6ac> about HardwareID('modalias', 'wmi:7364651A-132F-4FE7-ADAA-40C6C7EE2E3B')
2013-04-10 13:51:53,766 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-04-10 13:51:53,771 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-04-10 13:51:53,783 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-04-10 13:51:53,788 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-04-10 13:51:53,816 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-04-10 13:51:53,821 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-04-10 13:51:58,366 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-04-10 13:52:02,091 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2013-04-10 13:52:02,091 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2013-04-10 13:52:02,121 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-04-10 13:52:03,740 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-04-10 13:52:03,752 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-04-10 13:52:03,766 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted



Here is the balacnce of blacklist.conf

[INDENT]
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
[/INDENT]


Thanks for the help...

---

### Post by nathockens on 2013-04-10
Update:

Via synaptic, installed the b43 driver (LP-PHY version) -- Still no dice. :(

---

