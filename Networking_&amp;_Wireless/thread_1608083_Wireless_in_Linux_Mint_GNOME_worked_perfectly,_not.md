---
title: "Wireless in Linux Mint GNOME worked perfectly, not working in Linux Mint 9 KDE!"
date: 2010-10-28
forum: Networking &amp; Wireless
---

### Post by Rytron on 2010-10-28
Hi.

I used to run Linux Mint GNOME on my laptop. There was never a problem. I'd connect my Desktop wireless adapter to it and then install the broadcom drivers with ease.

Today I decided to give KDE a try so I installed Linux Mint 9 KDE. All is fine except for the wireless drivers. I get this message in 'Hardware Drivers' window "[COLOR="Indigo"]Sorry, installation of this driver failed. Please have a look at the log file for details: /var/log/jockey.log[/COLOR]".
I have noticed that there are not as many Servers available in LM KDE as there are in Ubuntu. Could this be the problem? The drivers are actually not available to download?

Please can someone help.


Thank you.

---

### Post by Rytron on 2010-10-30
Here is the output of /var/log/jockey.log

```
2010-10-30 09:27:35,374 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f338ac>
2010-10-30 09:27:35,375 DEBUG: reading modalias file /lib/modules/2.6.32-21-generic/modules.alias
2010-10-30 09:27:35,545 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-10-30 09:27:35,556 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-10-30 09:27:35,592 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-10-30 09:27:35,605 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2010-10-30 09:27:35,608 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2010-10-30 09:27:35,624 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2010-10-30 09:27:35,628 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2010-10-30 09:27:35,971 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2010-10-30 09:27:36,046 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2010-10-30 09:27:36,046 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2010-10-30 09:27:36,065 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-10-30 09:27:36,068 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2010-10-30 09:27:36,069 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2010-10-30 09:27:36,078 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-10-30 09:27:36,079 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2010-10-30 09:27:36,091 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2010-10-30 09:27:36,091 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2010-10-30 09:27:36,100 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-10-30 09:27:36,100 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2010-10-30 09:27:36,116 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-10-30 09:27:36,116 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2010-10-30 09:27:36,130 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2010-10-30 09:27:36,130 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2010-10-30 09:27:36,134 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2010-10-30 09:27:36,135 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2010-10-30 09:27:36,135 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2010-10-30 09:27:36,135 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2010-10-30 09:27:36,186 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2010-10-30 09:27:36,187 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2010-10-30 09:27:36,191 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2010-10-30 09:27:36,192 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2010-10-30 09:27:36,192 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2010-10-30 09:27:36,202 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2010-10-30 09:27:36,223 DEBUG: Software modem not available
2010-10-30 09:27:36,223 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2010-10-30 09:27:36,242 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-10-30 09:27:36,266 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2010-10-30 09:27:36,266 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2010-10-30 09:27:36,267 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2010-10-30 09:27:36,337 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2010-10-30 09:27:36,338 DEBUG: Firmware for DVB cards not available
2010-10-30 09:27:36,338 DEBUG: all custom handlers loaded
2010-10-30 09:27:36,338 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f338ac> about HardwareID('modalias', 'pci:v00008086d00002A03sv00001025sd0000011Fbc03sc80i00')
2010-10-30 09:27:36,625 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f338ac> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-10-30 09:27:36,929 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 09:27:36,929 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f338ac> about HardwareID('modalias', 'pci:v0000104Cd0000803Asv00001025sd0000011Fbc0Csc00i10')
2010-10-30 09:27:36,946 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ohci1394', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 09:27:36,947 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 09:27:36,947 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f338ac> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-10-30 09:27:36,950 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f338ac> about HardwareID('modalias', 'acpi:PNP0200:')
2010-10-30 09:27:36,951 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f338ac> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-10-30 09:27:36,951 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f338ac> about HardwareID('modalias', 'pci:v00008086d00002834sv00001025sd0000011Fbc0Csc03i00')
2010-10-30 09:27:36,954 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f338ac> about HardwareID('modalias', 'input:b0001v10ECp0268e0001-e0,12,kramls1,2,fw')
2010-10-30 09:27:36,954 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 09:27:36,955 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f338ac> about HardwareID('modalias', 'platform:eisa')
2010-10-30 09:27:36,955 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f338ac> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-10-30 09:27:36,982 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f338ac> about HardwareID('modalias', 'pci:v0000104Cd0000803Bsv00001025sd0000011Fbc01sc80i00')
2010-10-30 09:27:36,983 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'tifm_7xx1', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 09:27:36,983 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f338ac> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-10-30 09:27:36,983 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 09:27:36,983 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f338ac> about HardwareID('modalias', 'acpi:INT0800:')
2010-10-30 09:27:36,984 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f338ac> about HardwareID('modalias', 'pci:v00008086d00002815sv00001025sd0000011Fbc06sc01i00')
2010-10-30 09:27:36,987 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 09:27:36,987 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f338ac> about HardwareID('modalias', 'platform:acer-wmi')
2010-10-30 09:27:36,988 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f338ac> about HardwareID('modalias', 'pci:v000014E4d00004311sv00001468sd00000422bc02sc80i00')
2010-10-30 09:27:37,041 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ssb', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 09:27:37,044 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-10-30 09:27:37,045 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-10-30 09:27:37,044 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2010-10-30 09:27:37,045 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f338ac> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-10-30 09:27:37,045 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f338ac> about HardwareID('modalias', 'pci:v0000104Cd00008039sv00001025sd0000011Fbc06sc07i00')
2010-10-30 09:27:37,046 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'yenta_socket', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 09:27:37,046 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'yenta_socket', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 09:27:37,046 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f338ac> about HardwareID('modalias', 'pci:v00008086d00002A00sv00001025sd0000011Fbc06sc00i00')
2010-10-30 09:27:37,050 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_agp', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 09:27:37,050 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f338ac> about HardwareID('modalias', 'acpi:PNP0100:')
2010-10-30 09:27:37,050 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f338ac> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2010-10-30 09:27:37,051 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f338ac> about HardwareID('modalias', 'pci:v00008086d00002A02sv00001025sd0000011Fbc03sc00i00')
2010-10-30 09:27:37,054 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 09:27:37,054 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'vga16fb', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 09:27:37,054 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f338ac> about HardwareID('modalias', 'acpi:device:')
2010-10-30 09:27:37,055 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f338ac> about HardwareID('modalias', 'acpi:NSC6001:')
2010-10-30 09:27:37,055 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f338ac> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-10-30 09:27:37,055 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f338ac> about HardwareID('printer_deviceid', 'MFG:Generic;MDL:CUPS-PDF Printer;DES:Generic CUPS-PDF Printer;CMD:POSTSCRIPT;')
2010-10-30 09:27:37,055 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f338ac> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-10-30 09:27:37,055 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f338ac> about HardwareID('modalias', 'pci:v00008086d0000283Esv00001025sd0000011Fbc0Csc05i00')
2010-10-30 09:27:37,059 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 09:27:37,059 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f338ac> about HardwareID('modalias', 'pci:v00008086d0000283Asv00001025sd0000011Fbc0Csc03i20')
2010-10-30 09:27:37,062 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f338ac> about HardwareID('modalias', 'pci:v00008086d00002836sv00001025sd0000011Fbc0Csc03i20')
2010-10-30 09:27:37,066 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f338ac> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-10-30 09:27:37,066 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 09:27:37,066 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f338ac> about HardwareID('modalias', 'input:b0011v0002p0007e12B1-e0,1,3,k100,101,102,103,110,111,112,145,14A,14D,14E,ra0,1,18,1C,mlsfw')
2010-10-30 09:27:37,066 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 09:27:37,067 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 09:27:37,067 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 09:27:37,067 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f338ac> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-10-30 09:27:37,067 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f338ac> about HardwareID('modalias', 'dmi:bvnPhoenixTechnologiesLTD:bvrV1.31:bd01/17/2008:svnAcer:pnExtensa5220:pvr0100:rvnAcer:rnColumbia:rvrRev:cvnAcer:ct10:cvrN/A:')
2010-10-30 09:27:37,082 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'acer_wmi', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 09:27:37,082 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f338ac> about HardwareID('modalias', 'acpi:PNP0000:')
2010-10-30 09:27:37,083 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f338ac> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-10-30 09:27:37,083 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 09:27:37,083 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f338ac> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-10-30 09:27:37,084 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f338ac> about HardwareID('modalias', 'pci:v0000104Cd0000803Csv00001025sd0000011Fbc08sc05i00')
2010-10-30 09:27:37,084 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 09:27:37,084 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f338ac> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-10-30 09:27:37,084 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f338ac> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-10-30 09:27:37,085 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f338ac> about HardwareID('modalias', 'pci:v00008086d00002832sv00001025sd0000011Fbc0Csc03i00')
2010-10-30 09:27:37,088 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f338ac> about HardwareID('modalias', 'pci:v00008086d00002835sv00001025sd0000011Fbc0Csc03i00')
2010-10-30 09:27:37,091 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f338ac> about HardwareID('modalias', 'pci:v00008086d00002831sv00001025sd0000011Fbc0Csc03i00')
2010-10-30 09:27:37,095 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f338ac> about HardwareID('modalias', 'pci:v00008086d0000284Bsv00001025sd0000011Fbc04sc03i00')
2010-10-30 09:27:37,098 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 09:27:37,099 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f338ac> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8D,8E,8F,94,95,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D9,E0,E1,E2,E3,EC,ED,EE,1A9,1B2,1B3,1D0,ram4,l0,1,2,sfw')
2010-10-30 09:27:37,099 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 09:27:37,099 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f338ac> about HardwareID('modalias', 'acpi:PNP0303:')
2010-10-30 09:27:37,099 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f338ac> about HardwareID('modalias', 'pci:v000014E4d00001693sv00001025sd0000011Cbc02sc00i00')
2010-10-30 09:27:37,100 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'tg3', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 09:27:37,100 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f338ac> about HardwareID('modalias', 'platform:pcspkr')
2010-10-30 09:27:37,101 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 09:27:37,101 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 09:27:37,101 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f338ac> about HardwareID('modalias', 'pci:v00008086d00002829sv00001025sd0000011Fbc01sc06i01')
2010-10-30 09:27:37,104 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 09:27:37,105 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 09:27:37,105 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f338ac> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-10-30 09:27:37,126 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 09:27:37,126 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 09:27:37,126 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f338ac> about HardwareID('modalias', 'pci:v00008086d00002830sv00001025sd0000011Fbc0Csc03i00')
2010-10-30 09:27:37,130 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f338ac> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-10-30 09:27:37,130 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 09:27:37,130 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f338ac> about HardwareID('modalias', 'acpi:SYN0302:SYN0300:SYN0002:PNP0F13:')
2010-10-30 09:27:37,130 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92cb8ec> about HardwareID('modalias', 'pci:v00008086d00002A03sv00001025sd0000011Fbc03sc80i00')
2010-10-30 09:27:37,130 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92cb8ec> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-10-30 09:27:37,130 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92cb8ec> about HardwareID('modalias', 'pci:v0000104Cd0000803Asv00001025sd0000011Fbc0Csc00i10')
2010-10-30 09:27:37,131 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92cb8ec> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-10-30 09:27:37,131 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92cb8ec> about HardwareID('modalias', 'acpi:PNP0200:')
2010-10-30 09:27:37,131 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92cb8ec> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-10-30 09:27:37,131 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92cb8ec> about HardwareID('modalias', 'pci:v00008086d00002834sv00001025sd0000011Fbc0Csc03i00')
2010-10-30 09:27:37,131 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92cb8ec> about HardwareID('modalias', 'input:b0001v10ECp0268e0001-e0,12,kramls1,2,fw')
2010-10-30 09:27:37,131 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92cb8ec> about HardwareID('modalias', 'platform:eisa')
2010-10-30 09:27:37,131 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92cb8ec> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-10-30 09:27:37,131 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92cb8ec> about HardwareID('modalias', 'pci:v0000104Cd0000803Bsv00001025sd0000011Fbc01sc80i00')
2010-10-30 09:27:37,132 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92cb8ec> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-10-30 09:27:37,132 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92cb8ec> about HardwareID('modalias', 'acpi:INT0800:')
2010-10-30 09:27:37,132 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92cb8ec> about HardwareID('modalias', 'pci:v00008086d00002815sv00001025sd0000011Fbc06sc01i00')
2010-10-30 09:27:37,132 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92cb8ec> about HardwareID('modalias', 'platform:acer-wmi')
2010-10-30 09:27:37,132 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92cb8ec> about HardwareID('modalias', 'pci:v000014E4d00004311sv00001468sd00000422bc02sc80i00')
2010-10-30 09:27:37,132 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92cb8ec> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-10-30 09:27:37,132 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92cb8ec> about HardwareID('modalias', 'pci:v0000104Cd00008039sv00001025sd0000011Fbc06sc07i00')
2010-10-30 09:27:37,133 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92cb8ec> about HardwareID('modalias', 'pci:v00008086d00002A00sv00001025sd0000011Fbc06sc00i00')
2010-10-30 09:27:37,133 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92cb8ec> about HardwareID('modalias', 'acpi:PNP0100:')
2010-10-30 09:27:37,133 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92cb8ec> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2010-10-30 09:27:37,133 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92cb8ec> about HardwareID('modalias', 'pci:v00008086d00002A02sv00001025sd0000011Fbc03sc00i00')
2010-10-30 09:27:37,133 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92cb8ec> about HardwareID('modalias', 'acpi:device:')
2010-10-30 09:27:37,133 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92cb8ec> about HardwareID('modalias', 'acpi:NSC6001:')
2010-10-30 09:27:37,133 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92cb8ec> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-10-30 09:27:37,133 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92cb8ec> about HardwareID('printer_deviceid', 'MFG:Generic;MDL:CUPS-PDF Printer;DES:Generic CUPS-PDF Printer;CMD:POSTSCRIPT;')
2010-10-30 09:27:37,134 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92cb8ec> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-10-30 09:27:37,134 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92cb8ec> about HardwareID('modalias', 'pci:v00008086d0000283Esv00001025sd0000011Fbc0Csc05i00')
2010-10-30 09:27:37,134 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92cb8ec> about HardwareID('modalias', 'pci:v00008086d0000283Asv00001025sd0000011Fbc0Csc03i20')
2010-10-30 09:27:37,134 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92cb8ec> about HardwareID('modalias', 'pci:v00008086d00002836sv00001025sd0000011Fbc0Csc03i20')
2010-10-30 09:27:37,134 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92cb8ec> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-10-30 09:27:37,134 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92cb8ec> about HardwareID('modalias', 'input:b0011v0002p0007e12B1-e0,1,3,k100,101,102,103,110,111,112,145,14A,14D,14E,ra0,1,18,1C,mlsfw')
2010-10-30 09:27:37,134 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92cb8ec> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-10-30 09:27:37,134 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92cb8ec> about HardwareID('modalias', 'dmi:bvnPhoenixTechnologiesLTD:bvrV1.31:bd01/17/2008:svnAcer:pnExtensa5220:pvr0100:rvnAcer:rnColumbia:rvrRev:cvnAcer:ct10:cvrN/A:')
2010-10-30 09:27:37,135 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92cb8ec> about HardwareID('modalias', 'acpi:PNP0000:')
2010-10-30 09:27:37,135 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92cb8ec> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-10-30 09:27:37,135 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92cb8ec> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-10-30 09:27:37,135 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92cb8ec> about HardwareID('modalias', 'pci:v0000104Cd0000803Csv00001025sd0000011Fbc08sc05i00')
2010-10-30 09:27:37,135 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92cb8ec> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-10-30 09:27:37,135 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92cb8ec> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-10-30 09:27:37,135 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92cb8ec> about HardwareID('modalias', 'pci:v00008086d00002832sv00001025sd0000011Fbc0Csc03i00')
2010-10-30 09:27:37,135 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92cb8ec> about HardwareID('modalias', 'pci:v00008086d00002835sv00001025sd0000011Fbc0Csc03i00')
2010-10-30 09:27:37,136 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92cb8ec> about HardwareID('modalias', 'pci:v00008086d00002831sv00001025sd0000011Fbc0Csc03i00')
2010-10-30 09:27:37,136 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92cb8ec> about HardwareID('modalias', 'pci:v00008086d0000284Bsv00001025sd0000011Fbc04sc03i00')
2010-10-30 09:27:37,136 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92cb8ec> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8D,8E,8F,94,95,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D9,E0,E1,E2,E3,EC,ED,EE,1A9,1B2,1B3,1D0,ram4,l0,1,2,sfw')
2010-10-30 09:27:37,136 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92cb8ec> about HardwareID('modalias', 'acpi:PNP0303:')
2010-10-30 09:27:37,136 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92cb8ec> about HardwareID('modalias', 'pci:v000014E4d00001693sv00001025sd0000011Cbc02sc00i00')
2010-10-30 09:27:37,136 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92cb8ec> about HardwareID('modalias', 'platform:pcspkr')
2010-10-30 09:27:37,136 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92cb8ec> about HardwareID('modalias', 'pci:v00008086d00002829sv00001025sd0000011Fbc01sc06i01')
2010-10-30 09:27:37,137 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92cb8ec> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-10-30 09:27:37,137 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92cb8ec> about HardwareID('modalias', 'pci:v00008086d00002830sv00001025sd0000011Fbc0Csc03i00')
2010-10-30 09:27:37,137 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92cb8ec> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-10-30 09:27:37,137 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x92cb8ec> about HardwareID('modalias', 'acpi:SYN0302:SYN0300:SYN0002:PNP0F13:')
2010-10-30 09:27:37,210 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-10-30 09:27:37,313 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-10-30 09:27:37,346 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-10-30 09:35:33,987 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x95798ec>
2010-10-30 09:35:34,013 DEBUG: reading modalias file /lib/modules/2.6.32-21-generic/modules.alias
2010-10-30 09:35:34,170 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-10-30 09:35:34,184 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-10-30 09:35:34,228 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-10-30 09:35:34,230 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2010-10-30 09:35:34,233 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2010-10-30 09:35:34,249 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2010-10-30 09:35:34,253 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2010-10-30 09:35:34,600 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2010-10-30 09:35:34,671 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2010-10-30 09:35:34,672 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2010-10-30 09:35:34,690 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-10-30 09:35:34,694 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2010-10-30 09:35:34,694 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2010-10-30 09:35:34,704 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-10-30 09:35:34,704 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2010-10-30 09:35:34,716 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2010-10-30 09:35:34,717 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2010-10-30 09:35:34,725 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-10-30 09:35:34,725 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2010-10-30 09:35:34,741 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-10-30 09:35:34,742 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2010-10-30 09:35:34,751 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2010-10-30 09:35:34,752 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2010-10-30 09:35:34,756 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2010-10-30 09:35:34,757 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2010-10-30 09:35:34,757 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2010-10-30 09:35:34,757 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2010-10-30 09:35:34,823 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2010-10-30 09:35:34,823 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2010-10-30 09:35:34,828 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2010-10-30 09:35:34,828 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2010-10-30 09:35:34,828 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2010-10-30 09:35:34,846 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2010-10-30 09:35:34,859 DEBUG: Software modem not available
2010-10-30 09:35:34,860 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2010-10-30 09:35:34,879 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-10-30 09:35:34,901 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2010-10-30 09:35:34,901 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2010-10-30 09:35:34,901 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2010-10-30 09:35:34,951 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2010-10-30 09:35:34,952 DEBUG: Firmware for DVB cards not available
2010-10-30 09:35:34,952 DEBUG: all custom handlers loaded
2010-10-30 09:35:34,952 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95798ec> about HardwareID('modalias', 'pci:v00008086d00002A03sv00001025sd0000011Fbc03sc80i00')
2010-10-30 09:35:35,251 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95798ec> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-10-30 09:35:35,534 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 09:35:35,534 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95798ec> about HardwareID('modalias', 'pci:v0000104Cd0000803Asv00001025sd0000011Fbc0Csc00i10')
2010-10-30 09:35:35,551 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ohci1394', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 09:35:35,551 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 09:35:35,552 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95798ec> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-10-30 09:35:35,555 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95798ec> about HardwareID('modalias', 'acpi:PNP0200:')
2010-10-30 09:35:35,555 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95798ec> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-10-30 09:35:35,556 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95798ec> about HardwareID('modalias', 'pci:v00008086d00002834sv00001025sd0000011Fbc0Csc03i00')
2010-10-30 09:35:35,559 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95798ec> about HardwareID('modalias', 'input:b0001v10ECp0268e0001-e0,12,kramls1,2,fw')
2010-10-30 09:35:35,559 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 09:35:35,559 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95798ec> about HardwareID('modalias', 'platform:regulatory')
2010-10-30 09:35:35,560 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95798ec> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-10-30 09:35:35,597 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95798ec> about HardwareID('modalias', 'pci:v0000104Cd0000803Bsv00001025sd0000011Fbc01sc80i00')
2010-10-30 09:35:35,598 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'tifm_7xx1', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 09:35:35,598 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95798ec> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-10-30 09:35:35,598 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 09:35:35,598 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95798ec> about HardwareID('modalias', 'acpi:INT0800:')
2010-10-30 09:35:35,598 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95798ec> about HardwareID('modalias', 'pci:v0000104Cd0000803Csv00001025sd0000011Fbc08sc05i00')
2010-10-30 09:35:35,599 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 09:35:35,599 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95798ec> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-10-30 09:35:35,599 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95798ec> about HardwareID('modalias', 'pci:v000014E4d00004311sv00001468sd00000422bc02sc80i00')
2010-10-30 09:35:35,653 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ssb', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 09:35:35,656 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-10-30 09:35:35,657 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-10-30 09:35:35,656 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2010-10-30 09:35:35,657 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95798ec> about HardwareID('modalias', 'platform:acer-wmi')
2010-10-30 09:35:35,658 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95798ec> about HardwareID('modalias', 'pci:v0000104Cd00008039sv00001025sd0000011Fbc06sc07i00')
2010-10-30 09:35:35,658 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'yenta_socket', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 09:35:35,658 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'yenta_socket', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 09:35:35,659 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95798ec> about HardwareID('modalias', 'pci:v00008086d00002A00sv00001025sd0000011Fbc06sc00i00')
2010-10-30 09:35:35,662 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_agp', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 09:35:35,663 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95798ec> about HardwareID('modalias', 'acpi:PNP0100:')
2010-10-30 09:35:35,663 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95798ec> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2010-10-30 09:35:35,663 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95798ec> about HardwareID('modalias', 'pci:v00008086d00002A02sv00001025sd0000011Fbc03sc00i00')
2010-10-30 09:35:35,666 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 09:35:35,667 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'vga16fb', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 09:35:35,667 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95798ec> about HardwareID('modalias', 'acpi:device:')
2010-10-30 09:35:35,667 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95798ec> about HardwareID('modalias', 'acpi:NSC6001:')
2010-10-30 09:35:35,667 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95798ec> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-10-30 09:35:35,667 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95798ec> about HardwareID('printer_deviceid', 'MFG:Generic;MDL:CUPS-PDF Printer;DES:Generic CUPS-PDF Printer;CMD:POSTSCRIPT;')
2010-10-30 09:35:35,667 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95798ec> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-10-30 09:35:35,667 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95798ec> about HardwareID('modalias', 'pci:v00008086d00002829sv00001025sd0000011Fbc01sc06i01')
2010-10-30 09:35:35,671 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 09:35:35,671 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 09:35:35,671 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95798ec> about HardwareID('modalias', 'pci:v00008086d0000283Asv00001025sd0000011Fbc0Csc03i20')
2010-10-30 09:35:35,675 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95798ec> about HardwareID('modalias', 'pci:v00008086d00002836sv00001025sd0000011Fbc0Csc03i20')
2010-10-30 09:35:35,678 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95798ec> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-10-30 09:35:35,678 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 09:35:35,679 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95798ec> about HardwareID('modalias', 'input:b0011v0002p0007e12B1-e0,1,3,k100,101,102,103,110,111,112,145,14A,14D,14E,ra0,1,18,1C,mlsfw')
2010-10-30 09:35:35,679 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 09:35:35,679 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 09:35:35,679 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 09:35:35,679 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95798ec> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-10-30 09:35:35,680 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95798ec> about HardwareID('modalias', 'dmi:bvnPhoenixTechnologiesLTD:bvrV1.31:bd01/17/2008:svnAcer:pnExtensa5220:pvr0100:rvnAcer:rnColumbia:rvrRev:cvnAcer:ct10:cvrN/A:')
2010-10-30 09:35:35,695 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'acer_wmi', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 09:35:35,695 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95798ec> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-10-30 09:35:35,695 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95798ec> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-10-30 09:35:35,696 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 09:35:35,696 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95798ec> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-10-30 09:35:35,696 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95798ec> about HardwareID('modalias', 'usb:v07D1p3C03d0001dc00dsc00dp00icFFiscFFipFF')
2010-10-30 09:35:35,707 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'rt73usb', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 09:35:35,707 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95798ec> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-10-30 09:35:35,707 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95798ec> about HardwareID('modalias', 'acpi:PNP0000:')
2010-10-30 09:35:35,707 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95798ec> about HardwareID('modalias', 'pci:v00008086d00002832sv00001025sd0000011Fbc0Csc03i00')
2010-10-30 09:35:35,711 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95798ec> about HardwareID('modalias', 'pci:v00008086d00002835sv00001025sd0000011Fbc0Csc03i00')
2010-10-30 09:35:35,714 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95798ec> about HardwareID('modalias', 'pci:v00008086d0000283Esv00001025sd0000011Fbc0Csc05i00')
2010-10-30 09:35:35,718 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 09:35:35,718 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95798ec> about HardwareID('modalias', 'pci:v00008086d00002831sv00001025sd0000011Fbc0Csc03i00')
2010-10-30 09:35:35,721 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95798ec> about HardwareID('modalias', 'pci:v00008086d0000284Bsv00001025sd0000011Fbc04sc03i00')
2010-10-30 09:35:35,725 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 09:35:35,725 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95798ec> about HardwareID('modalias', 'platform:pcspkr')
2010-10-30 09:35:35,725 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 09:35:35,726 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 09:35:35,726 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95798ec> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8D,8E,8F,94,95,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D9,E0,E1,E2,E3,EC,ED,EE,1A9,1B2,1B3,1D0,ram4,l0,1,2,sfw')
2010-10-30 09:35:35,726 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 09:35:35,726 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95798ec> about HardwareID('modalias', 'acpi:PNP0303:')
2010-10-30 09:35:35,726 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95798ec> about HardwareID('modalias', 'pci:v000014E4d00001693sv00001025sd0000011Cbc02sc00i00')
2010-10-30 09:35:35,727 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'tg3', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 09:35:35,727 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95798ec> about HardwareID('modalias', 'platform:eisa')
2010-10-30 09:35:35,728 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95798ec> about HardwareID('modalias', 'pci:v00008086d00002815sv00001025sd0000011Fbc06sc01i00')
2010-10-30 09:35:35,731 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 09:35:35,732 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95798ec> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-10-30 09:35:35,743 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 09:35:35,743 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 09:35:35,743 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95798ec> about HardwareID('modalias', 'pci:v00008086d00002830sv00001025sd0000011Fbc0Csc03i00')
2010-10-30 09:35:35,746 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95798ec> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-10-30 09:35:35,747 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 09:35:35,747 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x95798ec> about HardwareID('modalias', 'acpi:SYN0302:SYN0300:SYN0002:PNP0F13:')
2010-10-30 09:35:35,747 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x991192c> about HardwareID('modalias', 'pci:v00008086d00002A03sv00001025sd0000011Fbc03sc80i00')
2010-10-30 09:35:35,747 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x991192c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-10-30 09:35:35,747 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x991192c> about HardwareID('modalias', 'pci:v0000104Cd0000803Asv00001025sd0000011Fbc0Csc00i10')
2010-10-30 09:35:35,748 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x991192c> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-10-30 09:35:35,748 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x991192c> about HardwareID('modalias', 'acpi:PNP0200:')
2010-10-30 09:35:35,748 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x991192c> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-10-30 09:35:35,748 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x991192c> about HardwareID('modalias', 'pci:v00008086d00002834sv00001025sd0000011Fbc0Csc03i00')
2010-10-30 09:35:35,748 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x991192c> about HardwareID('modalias', 'input:b0001v10ECp0268e0001-e0,12,kramls1,2,fw')
2010-10-30 09:35:35,748 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x991192c> about HardwareID('modalias', 'platform:regulatory')
2010-10-30 09:35:35,748 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x991192c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-10-30 09:35:35,748 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x991192c> about HardwareID('modalias', 'pci:v0000104Cd0000803Bsv00001025sd0000011Fbc01sc80i00')
2010-10-30 09:35:35,749 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x991192c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-10-30 09:35:35,749 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x991192c> about HardwareID('modalias', 'acpi:INT0800:')
2010-10-30 09:35:35,749 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x991192c> about HardwareID('modalias', 'pci:v0000104Cd0000803Csv00001025sd0000011Fbc08sc05i00')
2010-10-30 09:35:35,749 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x991192c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-10-30 09:35:35,749 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x991192c> about HardwareID('modalias', 'pci:v000014E4d00004311sv00001468sd00000422bc02sc80i00')
2010-10-30 09:35:35,749 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x991192c> about HardwareID('modalias', 'platform:acer-wmi')
2010-10-30 09:35:35,749 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x991192c> about HardwareID('modalias', 'pci:v0000104Cd00008039sv00001025sd0000011Fbc06sc07i00')
2010-10-30 09:35:35,749 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x991192c> about HardwareID('modalias', 'pci:v00008086d00002A00sv00001025sd0000011Fbc06sc00i00')
2010-10-30 09:35:35,750 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x991192c> about HardwareID('modalias', 'acpi:PNP0100:')
2010-10-30 09:35:35,750 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x991192c> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2010-10-30 09:35:35,750 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x991192c> about HardwareID('modalias', 'pci:v00008086d00002A02sv00001025sd0000011Fbc03sc00i00')
2010-10-30 09:35:35,750 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x991192c> about HardwareID('modalias', 'acpi:device:')
2010-10-30 09:35:35,750 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x991192c> about HardwareID('modalias', 'acpi:NSC6001:')
2010-10-30 09:35:35,750 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x991192c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-10-30 09:35:35,750 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x991192c> about HardwareID('printer_deviceid', 'MFG:Generic;MDL:CUPS-PDF Printer;DES:Generic CUPS-PDF Printer;CMD:POSTSCRIPT;')
2010-10-30 09:35:35,751 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x991192c> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-10-30 09:35:35,751 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x991192c> about HardwareID('modalias', 'pci:v00008086d00002829sv00001025sd0000011Fbc01sc06i01')
2010-10-30 09:35:35,751 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x991192c> about HardwareID('modalias', 'pci:v00008086d0000283Asv00001025sd0000011Fbc0Csc03i20')
2010-10-30 09:35:35,751 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x991192c> about HardwareID('modalias', 'pci:v00008086d00002836sv00001025sd0000011Fbc0Csc03i20')
2010-10-30 09:35:35,751 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x991192c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-10-30 09:35:35,751 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x991192c> about HardwareID('modalias', 'input:b0011v0002p0007e12B1-e0,1,3,k100,101,102,103,110,111,112,145,14A,14D,14E,ra0,1,18,1C,mlsfw')
2010-10-30 09:35:35,751 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x991192c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-10-30 09:35:35,751 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x991192c> about HardwareID('modalias', 'dmi:bvnPhoenixTechnologiesLTD:bvrV1.31:bd01/17/2008:svnAcer:pnExtensa5220:pvr0100:rvnAcer:rnColumbia:rvrRev:cvnAcer:ct10:cvrN/A:')
2010-10-30 09:35:35,752 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x991192c> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-10-30 09:35:35,752 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x991192c> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-10-30 09:35:35,752 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x991192c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-10-30 09:35:35,752 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x991192c> about HardwareID('modalias', 'usb:v07D1p3C03d0001dc00dsc00dp00icFFiscFFipFF')
2010-10-30 09:35:35,752 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x991192c> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-10-30 09:35:35,752 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x991192c> about HardwareID('modalias', 'acpi:PNP0000:')
2010-10-30 09:35:35,752 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x991192c> about HardwareID('modalias', 'pci:v00008086d00002832sv00001025sd0000011Fbc0Csc03i00')
2010-10-30 09:35:35,752 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x991192c> about HardwareID('modalias', 'pci:v00008086d00002835sv00001025sd0000011Fbc0Csc03i00')
2010-10-30 09:35:35,753 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x991192c> about HardwareID('modalias', 'pci:v00008086d0000283Esv00001025sd0000011Fbc0Csc05i00')
2010-10-30 09:35:35,753 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x991192c> about HardwareID('modalias', 'pci:v00008086d00002831sv00001025sd0000011Fbc0Csc03i00')
2010-10-30 09:35:35,753 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x991192c> about HardwareID('modalias', 'pci:v00008086d0000284Bsv00001025sd0000011Fbc04sc03i00')
2010-10-30 09:35:35,753 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x991192c> about HardwareID('modalias', 'platform:pcspkr')
2010-10-30 09:35:35,753 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x991192c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8D,8E,8F,94,95,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D9,E0,E1,E2,E3,EC,ED,EE,1A9,1B2,1B3,1D0,ram4,l0,1,2,sfw')
2010-10-30 09:35:35,753 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x991192c> about HardwareID('modalias', 'acpi:PNP0303:')
2010-10-30 09:35:35,753 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x991192c> about HardwareID('modalias', 'pci:v000014E4d00001693sv00001025sd0000011Cbc02sc00i00')
2010-10-30 09:35:35,753 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x991192c> about HardwareID('modalias', 'platform:eisa')
2010-10-30 09:35:35,754 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x991192c> about HardwareID('modalias', 'pci:v00008086d00002815sv00001025sd0000011Fbc06sc01i00')
2010-10-30 09:35:35,754 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x991192c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-10-30 09:35:35,754 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x991192c> about HardwareID('modalias', 'pci:v00008086d00002830sv00001025sd0000011Fbc0Csc03i00')
2010-10-30 09:35:35,754 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x991192c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-10-30 09:35:35,754 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x991192c> about HardwareID('modalias', 'acpi:SYN0302:SYN0300:SYN0002:PNP0F13:')
2010-10-30 09:35:35,867 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-10-30 09:35:35,956 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-10-30 09:35:35,986 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-10-30 09:35:45,420 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-10-30 09:35:54,855 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-10-30 09:35:54,856 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2010-10-30 09:35:54,934 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-10-30 09:35:59,772 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-10-30 09:35:59,868 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-10-30 09:35:59,920 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-10-30 11:49:01,913 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x90019ec>
2010-10-30 11:49:01,937 DEBUG: reading modalias file /lib/modules/2.6.32-21-generic/modules.alias
2010-10-30 11:49:02,100 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-10-30 11:49:02,212 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-10-30 11:49:02,258 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-10-30 11:49:02,271 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2010-10-30 11:49:02,274 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2010-10-30 11:49:02,290 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2010-10-30 11:49:02,294 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2010-10-30 11:49:02,667 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2010-10-30 11:49:02,723 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2010-10-30 11:49:02,723 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2010-10-30 11:49:02,742 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-10-30 11:49:02,745 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2010-10-30 11:49:02,746 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2010-10-30 11:49:02,756 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-10-30 11:49:02,756 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2010-10-30 11:49:02,768 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2010-10-30 11:49:02,768 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2010-10-30 11:49:02,777 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-10-30 11:49:02,777 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2010-10-30 11:49:02,793 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-10-30 11:49:02,793 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2010-10-30 11:49:02,809 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2010-10-30 11:49:02,810 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2010-10-30 11:49:02,817 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2010-10-30 11:49:02,818 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2010-10-30 11:49:02,818 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2010-10-30 11:49:02,818 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2010-10-30 11:49:02,863 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2010-10-30 11:49:02,864 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2010-10-30 11:49:02,868 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2010-10-30 11:49:02,869 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2010-10-30 11:49:02,869 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2010-10-30 11:49:02,886 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2010-10-30 11:49:02,900 DEBUG: Software modem not available
2010-10-30 11:49:02,900 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2010-10-30 11:49:02,919 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-10-30 11:49:02,936 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2010-10-30 11:49:02,936 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2010-10-30 11:49:02,936 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2010-10-30 11:49:02,992 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2010-10-30 11:49:02,992 DEBUG: Firmware for DVB cards not available
2010-10-30 11:49:02,992 DEBUG: all custom handlers loaded
2010-10-30 11:49:02,992 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90019ec> about HardwareID('modalias', 'pci:v00008086d00002A03sv00001025sd0000011Fbc03sc80i00')
2010-10-30 11:49:03,298 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90019ec> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-10-30 11:49:03,575 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 11:49:03,575 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90019ec> about HardwareID('modalias', 'pci:v0000104Cd0000803Asv00001025sd0000011Fbc0Csc00i10')
2010-10-30 11:49:03,592 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ohci1394', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 11:49:03,592 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 11:49:03,592 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90019ec> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-10-30 11:49:03,596 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90019ec> about HardwareID('modalias', 'acpi:PNP0200:')
2010-10-30 11:49:03,596 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90019ec> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-10-30 11:49:03,596 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90019ec> about HardwareID('modalias', 'pci:v00008086d00002834sv00001025sd0000011Fbc0Csc03i00')
2010-10-30 11:49:03,605 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90019ec> about HardwareID('modalias', 'input:b0001v10ECp0268e0001-e0,12,kramls1,2,fw')
2010-10-30 11:49:03,605 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 11:49:03,605 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90019ec> about HardwareID('modalias', 'platform:regulatory')
2010-10-30 11:49:03,606 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90019ec> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-10-30 11:49:03,638 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90019ec> about HardwareID('modalias', 'pci:v0000104Cd0000803Bsv00001025sd0000011Fbc01sc80i00')
2010-10-30 11:49:03,639 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'tifm_7xx1', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 11:49:03,639 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90019ec> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-10-30 11:49:03,639 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 11:49:03,639 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90019ec> about HardwareID('modalias', 'acpi:INT0800:')
2010-10-30 11:49:03,640 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90019ec> about HardwareID('modalias', 'pci:v0000104Cd0000803Csv00001025sd0000011Fbc08sc05i00')
2010-10-30 11:49:03,640 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 11:49:03,640 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90019ec> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-10-30 11:49:03,641 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90019ec> about HardwareID('modalias', 'pci:v000014E4d00004311sv00001468sd00000422bc02sc80i00')
2010-10-30 11:49:03,695 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ssb', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 11:49:03,698 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-10-30 11:49:03,699 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-10-30 11:49:03,698 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2010-10-30 11:49:03,699 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90019ec> about HardwareID('modalias', 'platform:acer-wmi')
2010-10-30 11:49:03,700 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90019ec> about HardwareID('modalias', 'pci:v0000104Cd00008039sv00001025sd0000011Fbc06sc07i00')
2010-10-30 11:49:03,700 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'yenta_socket', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 11:49:03,700 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'yenta_socket', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 11:49:03,701 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90019ec> about HardwareID('modalias', 'pci:v00008086d00002A00sv00001025sd0000011Fbc06sc00i00')
2010-10-30 11:49:03,704 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_agp', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 11:49:03,704 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90019ec> about HardwareID('modalias', 'acpi:PNP0100:')
2010-10-30 11:49:03,705 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90019ec> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2010-10-30 11:49:03,705 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90019ec> about HardwareID('modalias', 'pci:v00008086d00002A02sv00001025sd0000011Fbc03sc00i00')
2010-10-30 11:49:03,708 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 11:49:03,708 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'vga16fb', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 11:49:03,709 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90019ec> about HardwareID('modalias', 'acpi:device:')
2010-10-30 11:49:03,709 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90019ec> about HardwareID('modalias', 'acpi:NSC6001:')
2010-10-30 11:49:03,709 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90019ec> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-10-30 11:49:03,709 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90019ec> about HardwareID('printer_deviceid', 'MFG:Generic;MDL:CUPS-PDF Printer;DES:Generic CUPS-PDF Printer;CMD:POSTSCRIPT;')
2010-10-30 11:49:03,709 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90019ec> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-10-30 11:49:03,709 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90019ec> about HardwareID('modalias', 'pci:v00008086d00002829sv00001025sd0000011Fbc01sc06i01')
2010-10-30 11:49:03,713 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 11:49:03,713 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 11:49:03,713 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90019ec> about HardwareID('modalias', 'pci:v00008086d0000283Asv00001025sd0000011Fbc0Csc03i20')
2010-10-30 11:49:03,717 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90019ec> about HardwareID('modalias', 'pci:v00008086d00002836sv00001025sd0000011Fbc0Csc03i20')
2010-10-30 11:49:03,720 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90019ec> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-10-30 11:49:03,720 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 11:49:03,721 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90019ec> about HardwareID('modalias', 'input:b0011v0002p0007e12B1-e0,1,3,k100,101,102,103,110,111,112,145,14A,14D,14E,ra0,1,18,1C,mlsfw')
2010-10-30 11:49:03,721 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 11:49:03,721 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 11:49:03,721 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 11:49:03,721 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90019ec> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-10-30 11:49:03,722 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90019ec> about HardwareID('modalias', 'dmi:bvnPhoenixTechnologiesLTD:bvrV1.31:bd01/17/2008:svnAcer:pnExtensa5220:pvr0100:rvnAcer:rnColumbia:rvrRev:cvnAcer:ct10:cvrN/A:')
2010-10-30 11:49:03,737 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'acer_wmi', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 11:49:03,737 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90019ec> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-10-30 11:49:03,737 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90019ec> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-10-30 11:49:03,737 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 11:49:03,738 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90019ec> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-10-30 11:49:03,738 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90019ec> about HardwareID('modalias', 'usb:v07D1p3C03d0001dc00dsc00dp00icFFiscFFipFF')
2010-10-30 11:49:03,749 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'rt73usb', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 11:49:03,749 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90019ec> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-10-30 11:49:03,749 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90019ec> about HardwareID('modalias', 'acpi:PNP0000:')
2010-10-30 11:49:03,749 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90019ec> about HardwareID('modalias', 'pci:v00008086d00002832sv00001025sd0000011Fbc0Csc03i00')
2010-10-30 11:49:03,753 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90019ec> about HardwareID('modalias', 'pci:v00008086d00002835sv00001025sd0000011Fbc0Csc03i00')
2010-10-30 11:49:03,756 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90019ec> about HardwareID('modalias', 'pci:v00008086d0000283Esv00001025sd0000011Fbc0Csc05i00')
2010-10-30 11:49:03,759 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 11:49:03,760 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90019ec> about HardwareID('modalias', 'pci:v00008086d00002831sv00001025sd0000011Fbc0Csc03i00')
2010-10-30 11:49:03,763 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90019ec> about HardwareID('modalias', 'pci:v00008086d0000284Bsv00001025sd0000011Fbc04sc03i00')
2010-10-30 11:49:03,767 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 11:49:03,767 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90019ec> about HardwareID('modalias', 'platform:pcspkr')
2010-10-30 11:49:03,767 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 11:49:03,768 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 11:49:03,768 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90019ec> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8D,8E,8F,94,95,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D9,E0,E1,E2,E3,EC,ED,EE,1A9,1B2,1B3,1D0,ram4,l0,1,2,sfw')
2010-10-30 11:49:03,768 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 11:49:03,768 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90019ec> about HardwareID('modalias', 'acpi:PNP0303:')
2010-10-30 11:49:03,768 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90019ec> about HardwareID('modalias', 'usb:v090Cp1000d1100dc00dsc00dp00ic08isc06ip50')
2010-10-30 11:49:03,770 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 11:49:03,770 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90019ec> about HardwareID('modalias', 'pci:v000014E4d00001693sv00001025sd0000011Cbc02sc00i00')
2010-10-30 11:49:03,771 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'tg3', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 11:49:03,771 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90019ec> about HardwareID('modalias', 'platform:eisa')
2010-10-30 11:49:03,771 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90019ec> about HardwareID('modalias', 'pci:v00008086d00002815sv00001025sd0000011Fbc06sc01i00')
2010-10-30 11:49:03,775 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 11:49:03,775 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90019ec> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-10-30 11:49:03,786 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 11:49:03,786 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 11:49:03,786 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90019ec> about HardwareID('modalias', 'pci:v00008086d00002830sv00001025sd0000011Fbc0Csc03i00')
2010-10-30 11:49:03,790 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90019ec> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-10-30 11:49:03,790 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 11:49:03,790 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x90019ec> about HardwareID('modalias', 'acpi:SYN0302:SYN0300:SYN0002:PNP0F13:')
2010-10-30 11:49:03,790 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x939894c> about HardwareID('modalias', 'pci:v00008086d00002A03sv00001025sd0000011Fbc03sc80i00')
2010-10-30 11:49:03,791 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x939894c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-10-30 11:49:03,791 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x939894c> about HardwareID('modalias', 'pci:v0000104Cd0000803Asv00001025sd0000011Fbc0Csc00i10')
2010-10-30 11:49:03,791 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x939894c> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-10-30 11:49:03,791 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x939894c> about HardwareID('modalias', 'acpi:PNP0200:')
2010-10-30 11:49:03,791 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x939894c> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-10-30 11:49:03,791 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x939894c> about HardwareID('modalias', 'pci:v00008086d00002834sv00001025sd0000011Fbc0Csc03i00')
2010-10-30 11:49:03,791 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x939894c> about HardwareID('modalias', 'input:b0001v10ECp0268e0001-e0,12,kramls1,2,fw')
2010-10-30 11:49:03,791 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x939894c> about HardwareID('modalias', 'platform:regulatory')
2010-10-30 11:49:03,792 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x939894c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-10-30 11:49:03,792 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x939894c> about HardwareID('modalias', 'pci:v0000104Cd0000803Bsv00001025sd0000011Fbc01sc80i00')
2010-10-30 11:49:03,792 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x939894c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-10-30 11:49:03,792 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x939894c> about HardwareID('modalias', 'acpi:INT0800:')
2010-10-30 11:49:03,792 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x939894c> about HardwareID('modalias', 'pci:v0000104Cd0000803Csv00001025sd0000011Fbc08sc05i00')
2010-10-30 11:49:03,792 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x939894c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-10-30 11:49:03,792 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x939894c> about HardwareID('modalias', 'pci:v000014E4d00004311sv00001468sd00000422bc02sc80i00')
2010-10-30 11:49:03,793 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x939894c> about HardwareID('modalias', 'platform:acer-wmi')
2010-10-30 11:49:03,793 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x939894c> about HardwareID('modalias', 'pci:v0000104Cd00008039sv00001025sd0000011Fbc06sc07i00')
2010-10-30 11:49:03,793 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x939894c> about HardwareID('modalias', 'pci:v00008086d00002A00sv00001025sd0000011Fbc06sc00i00')
2010-10-30 11:49:03,793 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x939894c> about HardwareID('modalias', 'acpi:PNP0100:')
2010-10-30 11:49:03,793 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x939894c> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2010-10-30 11:49:03,793 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x939894c> about HardwareID('modalias', 'pci:v00008086d00002A02sv00001025sd0000011Fbc03sc00i00')
2010-10-30 11:49:03,793 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x939894c> about HardwareID('modalias', 'acpi:device:')
2010-10-30 11:49:03,793 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x939894c> about HardwareID('modalias', 'acpi:NSC6001:')
2010-10-30 11:49:03,794 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x939894c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-10-30 11:49:03,794 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x939894c> about HardwareID('printer_deviceid', 'MFG:Generic;MDL:CUPS-PDF Printer;DES:Generic CUPS-PDF Printer;CMD:POSTSCRIPT;')
2010-10-30 11:49:03,794 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x939894c> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-10-30 11:49:03,794 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x939894c> about HardwareID('modalias', 'pci:v00008086d00002829sv00001025sd0000011Fbc01sc06i01')
2010-10-30 11:49:03,794 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x939894c> about HardwareID('modalias', 'pci:v00008086d0000283Asv00001025sd0000011Fbc0Csc03i20')
2010-10-30 11:49:03,794 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x939894c> about HardwareID('modalias', 'pci:v00008086d00002836sv00001025sd0000011Fbc0Csc03i20')
2010-10-30 11:49:03,794 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x939894c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-10-30 11:49:03,794 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x939894c> about HardwareID('modalias', 'input:b0011v0002p0007e12B1-e0,1,3,k100,101,102,103,110,111,112,145,14A,14D,14E,ra0,1,18,1C,mlsfw')
2010-10-30 11:49:03,795 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x939894c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-10-30 11:49:03,795 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x939894c> about HardwareID('modalias', 'dmi:bvnPhoenixTechnologiesLTD:bvrV1.31:bd01/17/2008:svnAcer:pnExtensa5220:pvr0100:rvnAcer:rnColumbia:rvrRev:cvnAcer:ct10:cvrN/A:')
2010-10-30 11:49:03,795 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x939894c> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-10-30 11:49:03,795 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x939894c> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-10-30 11:49:03,795 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x939894c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-10-30 11:49:03,795 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x939894c> about HardwareID('modalias', 'usb:v07D1p3C03d0001dc00dsc00dp00icFFiscFFipFF')
2010-10-30 11:49:03,795 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x939894c> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-10-30 11:49:03,796 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x939894c> about HardwareID('modalias', 'acpi:PNP0000:')
2010-10-30 11:49:03,796 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x939894c> about HardwareID('modalias', 'pci:v00008086d00002832sv00001025sd0000011Fbc0Csc03i00')
2010-10-30 11:49:03,796 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x939894c> about HardwareID('modalias', 'pci:v00008086d00002835sv00001025sd0000011Fbc0Csc03i00')
2010-10-30 11:49:03,796 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x939894c> about HardwareID('modalias', 'pci:v00008086d0000283Esv00001025sd0000011Fbc0Csc05i00')
2010-10-30 11:49:03,796 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x939894c> about HardwareID('modalias', 'pci:v00008086d00002831sv00001025sd0000011Fbc0Csc03i00')
2010-10-30 11:49:03,796 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x939894c> about HardwareID('modalias', 'pci:v00008086d0000284Bsv00001025sd0000011Fbc04sc03i00')
2010-10-30 11:49:03,796 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x939894c> about HardwareID('modalias', 'platform:pcspkr')
2010-10-30 11:49:03,796 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x939894c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8D,8E,8F,94,95,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D9,E0,E1,E2,E3,EC,ED,EE,1A9,1B2,1B3,1D0,ram4,l0,1,2,sfw')
2010-10-30 11:49:03,797 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x939894c> about HardwareID('modalias', 'acpi:PNP0303:')
2010-10-30 11:49:03,797 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x939894c> about HardwareID('modalias', 'usb:v090Cp1000d1100dc00dsc00dp00ic08isc06ip50')
2010-10-30 11:49:03,797 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x939894c> about HardwareID('modalias', 'pci:v000014E4d00001693sv00001025sd0000011Cbc02sc00i00')
2010-10-30 11:49:03,797 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x939894c> about HardwareID('modalias', 'platform:eisa')
2010-10-30 11:49:03,797 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x939894c> about HardwareID('modalias', 'pci:v00008086d00002815sv00001025sd0000011Fbc06sc01i00')
2010-10-30 11:49:03,797 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x939894c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-10-30 11:49:03,797 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x939894c> about HardwareID('modalias', 'pci:v00008086d00002830sv00001025sd0000011Fbc0Csc03i00')
2010-10-30 11:49:03,797 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x939894c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-10-30 11:49:03,798 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x939894c> about HardwareID('modalias', 'acpi:SYN0302:SYN0300:SYN0002:PNP0F13:')
2010-10-30 11:49:03,877 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-10-30 11:49:03,960 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-10-30 11:49:04,010 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-10-30 11:49:08,160 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-10-30 11:49:16,140 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-10-30 11:49:16,141 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2010-10-30 11:49:16,248 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-10-30 11:49:19,734 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-10-30 11:49:19,826 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-10-30 11:49:19,866 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-10-30 17:10:15,713 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ce09ec>
2010-10-30 17:10:15,732 DEBUG: reading modalias file /lib/modules/2.6.32-21-generic/modules.alias
2010-10-30 17:10:15,906 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-10-30 17:10:15,933 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-10-30 17:10:15,985 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-10-30 17:10:15,998 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2010-10-30 17:10:16,002 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2010-10-30 17:10:16,018 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2010-10-30 17:10:16,022 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2010-10-30 17:10:16,376 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2010-10-30 17:10:16,451 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2010-10-30 17:10:16,452 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2010-10-30 17:10:16,471 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-10-30 17:10:16,474 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2010-10-30 17:10:16,475 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2010-10-30 17:10:16,485 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-10-30 17:10:16,485 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2010-10-30 17:10:16,496 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2010-10-30 17:10:16,497 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2010-10-30 17:10:16,506 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-10-30 17:10:16,506 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2010-10-30 17:10:16,521 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-10-30 17:10:16,522 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2010-10-30 17:10:16,532 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2010-10-30 17:10:16,532 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2010-10-30 17:10:16,537 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2010-10-30 17:10:16,538 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2010-10-30 17:10:16,538 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2010-10-30 17:10:16,538 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2010-10-30 17:10:16,592 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2010-10-30 17:10:16,592 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2010-10-30 17:10:16,615 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2010-10-30 17:10:16,615 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2010-10-30 17:10:16,615 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2010-10-30 17:10:16,638 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2010-10-30 17:10:16,650 DEBUG: Software modem not available
2010-10-30 17:10:16,651 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2010-10-30 17:10:16,670 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-10-30 17:10:16,692 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2010-10-30 17:10:16,693 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2010-10-30 17:10:16,693 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2010-10-30 17:10:16,754 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2010-10-30 17:10:16,755 DEBUG: Firmware for DVB cards not available
2010-10-30 17:10:16,755 DEBUG: all custom handlers loaded
2010-10-30 17:10:16,755 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ce09ec> about HardwareID('modalias', 'pci:v00008086d00002A03sv00001025sd0000011Fbc03sc80i00')
2010-10-30 17:10:17,058 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ce09ec> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-10-30 17:10:17,248 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 17:10:17,248 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ce09ec> about HardwareID('modalias', 'pci:v0000104Cd0000803Asv00001025sd0000011Fbc0Csc00i10')
2010-10-30 17:10:17,265 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ohci1394', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 17:10:17,266 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 17:10:17,266 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ce09ec> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-10-30 17:10:17,270 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ce09ec> about HardwareID('modalias', 'acpi:PNP0200:')
2010-10-30 17:10:17,270 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ce09ec> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-10-30 17:10:17,270 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ce09ec> about HardwareID('modalias', 'pci:v00008086d00002834sv00001025sd0000011Fbc0Csc03i00')
2010-10-30 17:10:17,273 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ce09ec> about HardwareID('modalias', 'input:b0001v10ECp0268e0001-e0,12,kramls1,2,fw')
2010-10-30 17:10:17,274 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 17:10:17,274 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ce09ec> about HardwareID('modalias', 'platform:regulatory')
2010-10-30 17:10:17,274 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ce09ec> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-10-30 17:10:17,302 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ce09ec> about HardwareID('modalias', 'pci:v0000104Cd0000803Bsv00001025sd0000011Fbc01sc80i00')
2010-10-30 17:10:17,302 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'tifm_7xx1', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 17:10:17,303 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ce09ec> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-10-30 17:10:17,303 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 17:10:17,303 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ce09ec> about HardwareID('modalias', 'acpi:INT0800:')
2010-10-30 17:10:17,303 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ce09ec> about HardwareID('modalias', 'pci:v0000104Cd0000803Csv00001025sd0000011Fbc08sc05i00')
2010-10-30 17:10:17,304 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 17:10:17,304 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ce09ec> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-10-30 17:10:17,304 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ce09ec> about HardwareID('modalias', 'pci:v000014E4d00004311sv00001468sd00000422bc02sc80i00')
2010-10-30 17:10:17,366 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ssb', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 17:10:17,370 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-10-30 17:10:17,371 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-10-30 17:10:17,370 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2010-10-30 17:10:17,371 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ce09ec> about HardwareID('modalias', 'platform:acer-wmi')
2010-10-30 17:10:17,374 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ce09ec> about HardwareID('modalias', 'pci:v0000104Cd00008039sv00001025sd0000011Fbc06sc07i00')
2010-10-30 17:10:17,375 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'yenta_socket', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 17:10:17,375 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'yenta_socket', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 17:10:17,375 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ce09ec> about HardwareID('modalias', 'pci:v00008086d00002A00sv00001025sd0000011Fbc06sc00i00')
2010-10-30 17:10:17,380 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_agp', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 17:10:17,380 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ce09ec> about HardwareID('modalias', 'acpi:PNP0100:')
2010-10-30 17:10:17,380 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ce09ec> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2010-10-30 17:10:17,380 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ce09ec> about HardwareID('modalias', 'pci:v00008086d00002A02sv00001025sd0000011Fbc03sc00i00')
2010-10-30 17:10:17,385 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 17:10:17,385 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'vga16fb', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 17:10:17,385 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ce09ec> about HardwareID('modalias', 'acpi:device:')
2010-10-30 17:10:17,385 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ce09ec> about HardwareID('modalias', 'acpi:NSC6001:')
2010-10-30 17:10:17,386 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ce09ec> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-10-30 17:10:17,386 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ce09ec> about HardwareID('printer_deviceid', 'MFG:Generic;MDL:CUPS-PDF Printer;DES:Generic CUPS-PDF Printer;CMD:POSTSCRIPT;')
2010-10-30 17:10:17,386 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ce09ec> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-10-30 17:10:17,386 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ce09ec> about HardwareID('modalias', 'pci:v00008086d00002829sv00001025sd0000011Fbc01sc06i01')
2010-10-30 17:10:17,390 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 17:10:17,390 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 17:10:17,390 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ce09ec> about HardwareID('modalias', 'pci:v00008086d0000283Asv00001025sd0000011Fbc0Csc03i20')
2010-10-30 17:10:17,393 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ce09ec> about HardwareID('modalias', 'pci:v00008086d00002836sv00001025sd0000011Fbc0Csc03i20')
2010-10-30 17:10:17,397 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ce09ec> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-10-30 17:10:17,397 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 17:10:17,397 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ce09ec> about HardwareID('modalias', 'input:b0011v0002p0007e12B1-e0,1,3,k100,101,102,103,110,111,112,145,14A,14D,14E,ra0,1,18,1C,mlsfw')
2010-10-30 17:10:17,398 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 17:10:17,398 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 17:10:17,398 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 17:10:17,398 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ce09ec> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-10-30 17:10:17,398 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ce09ec> about HardwareID('modalias', 'dmi:bvnPhoenixTechnologiesLTD:bvrV1.31:bd01/17/2008:svnAcer:pnExtensa5220:pvr0100:rvnAcer:rnColumbia:rvrRev:cvnAcer:ct10:cvrN/A:')
2010-10-30 17:10:17,414 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'acer_wmi', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 17:10:17,414 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ce09ec> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-10-30 17:10:17,414 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ce09ec> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-10-30 17:10:17,415 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 17:10:17,415 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ce09ec> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-10-30 17:10:17,415 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ce09ec> about HardwareID('modalias', 'usb:v07D1p3C03d0001dc00dsc00dp00icFFiscFFipFF')
2010-10-30 17:10:17,426 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'rt73usb', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 17:10:17,426 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ce09ec> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-10-30 17:10:17,426 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ce09ec> about HardwareID('modalias', 'acpi:PNP0000:')
2010-10-30 17:10:17,427 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ce09ec> about HardwareID('modalias', 'pci:v00008086d00002832sv00001025sd0000011Fbc0Csc03i00')
2010-10-30 17:10:17,430 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ce09ec> about HardwareID('modalias', 'pci:v00008086d00002835sv00001025sd0000011Fbc0Csc03i00')
2010-10-30 17:10:17,433 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ce09ec> about HardwareID('modalias', 'pci:v00008086d0000283Esv00001025sd0000011Fbc0Csc05i00')
2010-10-30 17:10:17,437 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 17:10:17,438 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ce09ec> about HardwareID('modalias', 'pci:v00008086d00002831sv00001025sd0000011Fbc0Csc03i00')
2010-10-30 17:10:17,441 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ce09ec> about HardwareID('modalias', 'pci:v00008086d0000284Bsv00001025sd0000011Fbc04sc03i00')
2010-10-30 17:10:17,445 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 17:10:17,445 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ce09ec> about HardwareID('modalias', 'platform:pcspkr')
2010-10-30 17:10:17,446 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 17:10:17,446 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 17:10:17,446 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ce09ec> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8D,8E,8F,94,95,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D9,E0,E1,E2,E3,EC,ED,EE,1A9,1B2,1B3,1D0,ram4,l0,1,2,sfw')
2010-10-30 17:10:17,446 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 17:10:17,447 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ce09ec> about HardwareID('modalias', 'acpi:PNP0303:')
2010-10-30 17:10:17,447 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ce09ec> about HardwareID('modalias', 'usb:v090Cp1000d1100dc00dsc00dp00ic08isc06ip50')
2010-10-30 17:10:17,448 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 17:10:17,448 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ce09ec> about HardwareID('modalias', 'pci:v000014E4d00001693sv00001025sd0000011Cbc02sc00i00')
2010-10-30 17:10:17,449 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'tg3', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 17:10:17,449 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ce09ec> about HardwareID('modalias', 'platform:eisa')
2010-10-30 17:10:17,450 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ce09ec> about HardwareID('modalias', 'pci:v00008086d00002815sv00001025sd0000011Fbc06sc01i00')
2010-10-30 17:10:17,453 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 17:10:17,453 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ce09ec> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-10-30 17:10:17,465 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 17:10:17,465 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 17:10:17,465 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ce09ec> about HardwareID('modalias', 'pci:v00008086d00002830sv00001025sd0000011Fbc0Csc03i00')
2010-10-30 17:10:17,468 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ce09ec> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-10-30 17:10:17,469 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-10-30 17:10:17,469 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ce09ec> about HardwareID('modalias', 'acpi:SYN0302:SYN0300:SYN0002:PNP0F13:')
2010-10-30 17:10:17,469 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07894c> about HardwareID('modalias', 'pci:v00008086d00002A03sv00001025sd0000011Fbc03sc80i00')
2010-10-30 17:10:17,469 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07894c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-10-30 17:10:17,469 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07894c> about HardwareID('modalias', 'pci:v0000104Cd0000803Asv00001025sd0000011Fbc0Csc00i10')
2010-10-30 17:10:17,470 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07894c> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-10-30 17:10:17,470 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07894c> about HardwareID('modalias', 'acpi:PNP0200:')
2010-10-30 17:10:17,470 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07894c> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-10-30 17:10:17,470 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07894c> about HardwareID('modalias', 'pci:v00008086d00002834sv00001025sd0000011Fbc0Csc03i00')
2010-10-30 17:10:17,470 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07894c> about HardwareID('modalias', 'input:b0001v10ECp0268e0001-e0,12,kramls1,2,fw')
2010-10-30 17:10:17,470 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07894c> about HardwareID('modalias', 'platform:regulatory')
2010-10-30 17:10:17,470 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07894c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-10-30 17:10:17,471 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07894c> about HardwareID('modalias', 'pci:v0000104Cd0000803Bsv00001025sd0000011Fbc01sc80i00')
2010-10-30 17:10:17,471 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07894c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-10-30 17:10:17,471 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07894c> about HardwareID('modalias', 'acpi:INT0800:')
2010-10-30 17:10:17,471 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07894c> about HardwareID('modalias', 'pci:v0000104Cd0000803Csv00001025sd0000011Fbc08sc05i00')
2010-10-30 17:10:17,471 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07894c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-10-30 17:10:17,471 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07894c> about HardwareID('modalias', 'pci:v000014E4d00004311sv00001468sd00000422bc02sc80i00')
2010-10-30 17:10:17,471 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07894c> about HardwareID('modalias', 'platform:acer-wmi')
2010-10-30 17:10:17,472 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07894c> about HardwareID('modalias', 'pci:v0000104Cd00008039sv00001025sd0000011Fbc06sc07i00')
2010-10-30 17:10:17,472 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07894c> about HardwareID('modalias', 'pci:v00008086d00002A00sv00001025sd0000011Fbc06sc00i00')
2010-10-30 17:10:17,472 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07894c> about HardwareID('modalias', 'acpi:PNP0100:')
2010-10-30 17:10:17,472 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07894c> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2010-10-30 17:10:17,472 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07894c> about HardwareID('modalias', 'pci:v00008086d00002A02sv00001025sd0000011Fbc03sc00i00')
2010-10-30 17:10:17,472 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07894c> about HardwareID('modalias', 'acpi:device:')
2010-10-30 17:10:17,472 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07894c> about HardwareID('modalias', 'acpi:NSC6001:')
2010-10-30 17:10:17,473 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07894c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-10-30 17:10:17,473 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07894c> about HardwareID('printer_deviceid', 'MFG:Generic;MDL:CUPS-PDF Printer;DES:Generic CUPS-PDF Printer;CMD:POSTSCRIPT;')
2010-10-30 17:10:17,473 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07894c> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-10-30 17:10:17,473 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07894c> about HardwareID('modalias', 'pci:v00008086d00002829sv00001025sd0000011Fbc01sc06i01')
2010-10-30 17:10:17,473 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07894c> about HardwareID('modalias', 'pci:v00008086d0000283Asv00001025sd0000011Fbc0Csc03i20')
2010-10-30 17:10:17,473 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07894c> about HardwareID('modalias', 'pci:v00008086d00002836sv00001025sd0000011Fbc0Csc03i20')
2010-10-30 17:10:17,473 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07894c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-10-30 17:10:17,473 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07894c> about HardwareID('modalias', 'input:b0011v0002p0007e12B1-e0,1,3,k100,101,102,103,110,111,112,145,14A,14D,14E,ra0,1,18,1C,mlsfw')
2010-10-30 17:10:17,474 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07894c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-10-30 17:10:17,474 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07894c> about HardwareID('modalias', 'dmi:bvnPhoenixTechnologiesLTD:bvrV1.31:bd01/17/2008:svnAcer:pnExtensa5220:pvr0100:rvnAcer:rnColumbia:rvrRev:cvnAcer:ct10:cvrN/A:')
2010-10-30 17:10:17,474 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07894c> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-10-30 17:10:17,474 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07894c> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-10-30 17:10:17,474 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07894c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-10-30 17:10:17,474 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07894c> about HardwareID('modalias', 'usb:v07D1p3C03d0001dc00dsc00dp00icFFiscFFipFF')
2010-10-30 17:10:17,474 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07894c> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-10-30 17:10:17,475 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07894c> about HardwareID('modalias', 'acpi:PNP0000:')
2010-10-30 17:10:17,475 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07894c> about HardwareID('modalias', 'pci:v00008086d00002832sv00001025sd0000011Fbc0Csc03i00')
2010-10-30 17:10:17,475 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07894c> about HardwareID('modalias', 'pci:v00008086d00002835sv00001025sd0000011Fbc0Csc03i00')
2010-10-30 17:10:17,475 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07894c> about HardwareID('modalias', 'pci:v00008086d0000283Esv00001025sd0000011Fbc0Csc05i00')
2010-10-30 17:10:17,475 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07894c> about HardwareID('modalias', 'pci:v00008086d00002831sv00001025sd0000011Fbc0Csc03i00')
2010-10-30 17:10:17,475 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07894c> about HardwareID('modalias', 'pci:v00008086d0000284Bsv00001025sd0000011Fbc04sc03i00')
2010-10-30 17:10:17,475 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07894c> about HardwareID('modalias', 'platform:pcspkr')
2010-10-30 17:10:17,476 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07894c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8D,8E,8F,94,95,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D9,E0,E1,E2,E3,EC,ED,EE,1A9,1B2,1B3,1D0,ram4,l0,1,2,sfw')
2010-10-30 17:10:17,476 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07894c> about HardwareID('modalias', 'acpi:PNP0303:')
2010-10-30 17:10:17,476 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07894c> about HardwareID('modalias', 'usb:v090Cp1000d1100dc00dsc00dp00ic08isc06ip50')
2010-10-30 17:10:17,476 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07894c> about HardwareID('modalias', 'pci:v000014E4d00001693sv00001025sd0000011Cbc02sc00i00')
2010-10-30 17:10:17,476 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07894c> about HardwareID('modalias', 'platform:eisa')
2010-10-30 17:10:17,476 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07894c> about HardwareID('modalias', 'pci:v00008086d00002815sv00001025sd0000011Fbc06sc01i00')
2010-10-30 17:10:17,476 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07894c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-10-30 17:10:17,477 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07894c> about HardwareID('modalias', 'pci:v00008086d00002830sv00001025sd0000011Fbc0Csc03i00')
2010-10-30 17:10:17,477 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07894c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-10-30 17:10:17,477 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07894c> about HardwareID('modalias', 'acpi:SYN0302:SYN0300:SYN0002:PNP0F13:')
2010-10-30 17:10:17,603 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-10-30 17:10:17,692 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-10-30 17:10:17,744 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-10-30 17:10:34,897 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-10-30 17:10:41,862 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-10-30 17:10:41,863 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2010-10-30 17:10:41,956 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
```

---

### Post by Rytron on 2010-10-30
I also ran these:

~$ dpkg -l | grep broadcom
```
ii  broadcom-sta-common 5.10.91.9.3-3 Common files for the Broadcom STA Wireless driver
ii  broadcom-sta-source 5.10.91.9.3-3 Source for the Broadcom STA Wireless driver 
```

~$ uname -a
```
Linux acer-laptop 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux
```

~$ bash wirelessdetector.sh
Linux Wireless Chipset Detector - V1.1
```
Scanning for PCI Cards...
Found - Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311]
```

---

### Post by gregds on 2010-10-30
Hi.

I had a similar problem, but I followed the instructions on this Linux Mint forum and it all came right.

[http://forums.linuxmint.com/viewtopic.php?f=109&p=310366](http://forums.linuxmint.com/viewtopic.php?f=109&p=310366)

I have no idea why, but then it seems no one else has either. I guess it's a bug.

Greg

---

### Post by Rytron on 2010-10-31
Thank you gregds. I will follow that thread. Cheers. :)

Update: Awesome. That worked. Well done gregds & Carl (of Linux Mint Forums).

---

