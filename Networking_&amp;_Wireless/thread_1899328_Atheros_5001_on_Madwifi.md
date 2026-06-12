---
title: "Atheros 5001 on Madwifi"
date: 2011-12-23
forum: Networking &amp; Wireless
---

### Post by Katsu on 2011-12-23
Hello!

First of all if anyone is going to give some solution bare in mind that i am not experienced Linux user.

Ok,so here are mine troubles..

After reinstalling Ubuntu 10.04 wifi is not working.Wireless networks are just not recognized.And i know from prior usage there should be at least 5-6 of them.
Card is Atheros 5001,Madwifi is installed and "enable wireless" is checked.
Prior to this re-installation of Ubuntu,wireless was working flawlessly on Madwifi.
Have blacklisted other driver(Atheros?)
I am trying to fix this from morning and i am out of solutions.Have checked many threads and other resources,so please help!
Thnx in advance!

***[COLOR=Red]EDIT:[/COLOR]***
Have forgot to mention something..
When i go to System-Administration-Hardware driver, Madwifi is there but when i go "Activate" i got error;"You removed the configuration file /etc/modprobe.d/blacklist-ath_pci.conf"
Is this main issue?

---

### Post by praseodym on 2011-12-23
Yes it is. Here is my file on 10.04:

```
gksu gedit /etc/modprobe.d/blacklist-ath_pci.conf
```
and insert (adjusted to the use of the Madwifi driver, ath5k blacklisted)
```
# For some Atheros 5K RF MACs, the madwifi driver loads buts fails to
# correctly initialize the hardware, leaving it in a state from
# which ath5k cannot recover. To prevent this condition, stop
# madwifi from loading by default. Use Jockey to select one driver
# or the other. (Ubuntu: #315056, #323830)
# blacklist ath_pci
blacklist ath5k
```
Save, close the editor and reboot

---

### Post by Katsu on 2011-12-23
Thanx for reply.

Did as suggested,nothing happens.
gksu gedit /etc/modprobe.d/blacklist-ath_pci.conf
,opens blank gedit-like document.Copy-paste,save,reboot-no wireless networks detected.
Only difference is that under "Hardware drivers" error message is different.It asks for pass,after that download starts but is aborted with error msg:"Sorry, installation of this driver failed.Please have a look at the log file for details: /var/log/jockey.log"

Not sure which part of this log would be useful,if any..so will provide log of recent activity.

```
2011-12-23 16:48:15,830 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a20aac>
2011-12-23 16:48:15,919 DEBUG: reading modalias file /lib/modules/2.6.32-37-generic/modules.alias
2011-12-23 16:48:16,088 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2011-12-23 16:48:16,100 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-12-23 16:48:16,151 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2011-12-23 16:48:16,163 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2011-12-23 16:48:16,192 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2011-12-23 16:48:16,207 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2011-12-23 16:48:16,230 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2011-12-23 16:48:16,608 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2011-12-23 16:48:16,654 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-12-23 16:48:16,655 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2011-12-23 16:48:16,699 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2011-12-23 16:48:16,700 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-12-23 16:48:16,704 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-12-23 16:48:16,714 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2011-12-23 16:48:16,714 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2011-12-23 16:48:16,715 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2011-12-23 16:48:16,765 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2011-12-23 16:48:16,765 DEBUG: Firmware for DVB cards not available
2011-12-23 16:48:16,765 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2011-12-23 16:48:16,844 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2011-12-23 16:48:16,845 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2011-12-23 16:48:16,862 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2011-12-23 16:48:16,862 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2011-12-23 16:48:16,862 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2011-12-23 16:48:16,874 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2011-12-23 16:48:16,918 DEBUG: Software modem not available
2011-12-23 16:48:16,918 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2011-12-23 16:48:16,923 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2011-12-23 16:48:16,923 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2011-12-23 16:48:16,924 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2011-12-23 16:48:16,937 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2011-12-23 16:48:16,938 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2011-12-23 16:48:16,949 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-12-23 16:48:16,953 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-12-23 16:48:16,953 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2011-12-23 16:48:16,965 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-12-23 16:48:16,965 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2011-12-23 16:48:16,999 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-12-23 16:48:16,999 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2011-12-23 16:48:17,009 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-12-23 16:48:17,009 DEBUG: all custom handlers loaded
2011-12-23 16:48:17,010 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a20aac> about HardwareID('modalias', 'pci:v00008086d00002A03sv00001734sd00001123bc03sc80i00')
2011-12-23 16:48:17,339 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a20aac> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-12-23 16:48:17,685 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-23 16:48:17,685 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a20aac> about HardwareID('modalias', 'pci:v00008086d00002815sv00001734sd00001123bc06sc01i00')
2011-12-23 16:48:17,690 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2011-12-23 16:48:17,690 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a20aac> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2011-12-23 16:48:17,690 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a20aac> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-12-23 16:48:17,690 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a20aac> about HardwareID('modalias', 'pci:v00008086d00002834sv00001734sd00001123bc0Csc03i00')
2011-12-23 16:48:17,694 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a20aac> about HardwareID('modalias', 'input:b0001v10ECp0268e0001-e0,12,kramls1,2,fw')
2011-12-23 16:48:17,694 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-23 16:48:17,694 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a20aac> about HardwareID('modalias', 'platform:pcspkr')
2011-12-23 16:48:17,695 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2011-12-23 16:48:17,695 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2011-12-23 16:48:17,695 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a20aac> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2011-12-23 16:48:17,725 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a20aac> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-12-23 16:48:17,725 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-23 16:48:17,725 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a20aac> about HardwareID('modalias', 'acpi:PNP0000:')
2011-12-23 16:48:17,725 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a20aac> about HardwareID('modalias', 'platform:eisa')
2011-12-23 16:48:17,726 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a20aac> about HardwareID('modalias', 'pci:v00008086d00002830sv00001734sd00001123bc0Csc03i00')
2011-12-23 16:48:17,730 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a20aac> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-12-23 16:48:17,730 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a20aac> about HardwareID('modalias', 'pci:v00008086d0000283Esv00001734sd00001123bc0Csc05i00')
2011-12-23 16:48:17,734 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2011-12-23 16:48:17,734 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a20aac> about HardwareID('modalias', 'pci:v00008086d00002A00sv00001734sd00001123bc06sc00i00')
2011-12-23 16:48:17,738 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_agp', 'jockey_handler': 'KernelModuleHandler'}
2011-12-23 16:48:17,738 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a20aac> about HardwareID('modalias', 'acpi:SYN0310:SYN0300:SYN0002:PNP0F13:')
2011-12-23 16:48:17,738 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a20aac> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-12-23 16:48:17,738 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a20aac> about HardwareID('modalias', 'pci:v00008086d00002A02sv00001734sd00001123bc03sc00i00')
2011-12-23 16:48:17,742 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2011-12-23 16:48:17,742 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'vga16fb', 'jockey_handler': 'KernelModuleHandler'}
2011-12-23 16:48:17,742 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a20aac> about HardwareID('modalias', 'acpi:device:')
2011-12-23 16:48:17,742 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a20aac> about HardwareID('modalias', 'acpi:LNXTHERM:')
2011-12-23 16:48:17,742 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a20aac> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-12-23 16:48:17,743 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a20aac> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2011-12-23 16:48:17,743 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a20aac> about HardwareID('modalias', 'pci:v00008086d0000284Bsv00001734sd00001123bc04sc03i00')
2011-12-23 16:48:17,746 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-12-23 16:48:17,747 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a20aac> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2011-12-23 16:48:17,750 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a20aac> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2011-12-23 16:48:17,751 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-23 16:48:17,751 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a20aac> about HardwareID('modalias', 'input:b0003v0458p003Ae0111-e0,1,2,4,k110,111,112,r0,1,8,am4,lsfw')
2011-12-23 16:48:17,751 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-23 16:48:17,751 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a20aac> about HardwareID('modalias', 'input:b0011v0002p0007e12B1-e0,1,3,k100,101,102,103,110,111,112,145,14A,14D,14E,ra0,1,18,1C,mlsfw')
2011-12-23 16:48:17,751 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-12-23 16:48:17,752 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-12-23 16:48:17,752 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-23 16:48:17,752 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a20aac> about HardwareID('modalias', 'pci:v00008086d0000283Asv00001734sd00001123bc0Csc03i20')
2011-12-23 16:48:17,756 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a20aac> about HardwareID('modalias', 'dmi:bvnPhoenixTechnologiesLTD:bvrV1.06:bd12/04/2007:svnFUJITSUSIEMENS:pnAMILOLi2727:pvr20:rvnFUJITSUSIEMENS:rnLV1:rvr1C:cvnFUJITSUSIEMENS:ct10:cvrA2040:')
2011-12-23 16:48:17,771 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a20aac> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-12-23 16:48:17,771 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a20aac> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2011-12-23 16:48:17,771 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-23 16:48:17,771 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a20aac> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2011-12-23 16:48:17,772 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a20aac> about HardwareID('modalias', 'usb:v0458p003Ad0100dc00dsc00dp00ic03isc01ip02')
2011-12-23 16:48:17,778 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-12-23 16:48:17,778 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a20aac> about HardwareID('modalias', 'acpi:PNP0303:')
2011-12-23 16:48:17,779 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a20aac> about HardwareID('modalias', 'acpi:PNP0100:')
2011-12-23 16:48:17,779 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a20aac> about HardwareID('modalias', 'pci:v00008086d00002836sv00001734sd00001123bc0Csc03i20')
2011-12-23 16:48:17,782 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a20aac> about HardwareID('modalias', 'pci:v00008086d00002835sv00001734sd00001123bc0Csc03i00')
2011-12-23 16:48:17,786 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a20aac> about HardwareID('modalias', 'pci:v00008086d00002832sv00001734sd00001123bc0Csc03i00')
2011-12-23 16:48:17,790 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a20aac> about HardwareID('modalias', 'pci:v000010ECd00008136sv00001734sd00001123bc02sc00i00')
2011-12-23 16:48:17,811 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2011-12-23 16:48:17,811 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a20aac> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2011-12-23 16:48:17,812 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-23 16:48:17,812 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a20aac> about HardwareID('modalias', 'acpi:PNP0200:')
2011-12-23 16:48:17,812 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a20aac> about HardwareID('modalias', 'pci:v0000168Cd0000001Csv0000168Csd00003067bc02sc00i00')
2011-12-23 16:48:17,826 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ath5k', 'jockey_handler': 'KernelModuleHandler'}
2011-12-23 16:48:17,826 DEBUG: got handler kmod:ath_pci([MadwifiHandler, nonfree, disabled] Alternate Atheros "madwifi" driver)
2011-12-23 16:48:17,827 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a20aac> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-12-23 16:48:17,837 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2011-12-23 16:48:17,837 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-12-23 16:48:17,837 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a20aac> about HardwareID('modalias', 'pci:v00008086d00002831sv00001734sd00001123bc0Csc03i00')
2011-12-23 16:48:17,841 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a20aac> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2011-12-23 16:48:17,841 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-23 16:48:17,841 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8a20aac> about HardwareID('modalias', 'acpi:INT0800:')
2011-12-23 16:48:17,842 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e4c7ec> about HardwareID('modalias', 'pci:v00008086d00002A03sv00001734sd00001123bc03sc80i00')
2011-12-23 16:48:17,842 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e4c7ec> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-12-23 16:48:17,842 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e4c7ec> about HardwareID('modalias', 'pci:v00008086d00002815sv00001734sd00001123bc06sc01i00')
2011-12-23 16:48:17,842 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e4c7ec> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2011-12-23 16:48:17,842 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e4c7ec> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-12-23 16:48:17,842 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e4c7ec> about HardwareID('modalias', 'pci:v00008086d00002834sv00001734sd00001123bc0Csc03i00')
2011-12-23 16:48:17,842 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e4c7ec> about HardwareID('modalias', 'input:b0001v10ECp0268e0001-e0,12,kramls1,2,fw')
2011-12-23 16:48:17,843 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e4c7ec> about HardwareID('modalias', 'platform:pcspkr')
2011-12-23 16:48:17,843 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e4c7ec> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2011-12-23 16:48:17,843 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e4c7ec> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-12-23 16:48:17,843 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e4c7ec> about HardwareID('modalias', 'acpi:PNP0000:')
2011-12-23 16:48:17,843 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e4c7ec> about HardwareID('modalias', 'platform:eisa')
2011-12-23 16:48:17,843 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e4c7ec> about HardwareID('modalias', 'pci:v00008086d00002830sv00001734sd00001123bc0Csc03i00')
2011-12-23 16:48:17,843 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e4c7ec> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-12-23 16:48:17,843 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e4c7ec> about HardwareID('modalias', 'pci:v00008086d0000283Esv00001734sd00001123bc0Csc05i00')
2011-12-23 16:48:17,844 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e4c7ec> about HardwareID('modalias', 'pci:v00008086d00002A00sv00001734sd00001123bc06sc00i00')
2011-12-23 16:48:17,844 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e4c7ec> about HardwareID('modalias', 'acpi:SYN0310:SYN0300:SYN0002:PNP0F13:')
2011-12-23 16:48:17,844 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e4c7ec> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-12-23 16:48:17,844 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e4c7ec> about HardwareID('modalias', 'pci:v00008086d00002A02sv00001734sd00001123bc03sc00i00')
2011-12-23 16:48:17,844 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e4c7ec> about HardwareID('modalias', 'acpi:device:')
2011-12-23 16:48:17,844 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e4c7ec> about HardwareID('modalias', 'acpi:LNXTHERM:')
2011-12-23 16:48:17,844 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e4c7ec> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-12-23 16:48:17,844 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e4c7ec> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2011-12-23 16:48:17,844 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e4c7ec> about HardwareID('modalias', 'pci:v00008086d0000284Bsv00001734sd00001123bc04sc03i00')
2011-12-23 16:48:17,845 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e4c7ec> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2011-12-23 16:48:17,845 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e4c7ec> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2011-12-23 16:48:17,845 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e4c7ec> about HardwareID('modalias', 'input:b0003v0458p003Ae0111-e0,1,2,4,k110,111,112,r0,1,8,am4,lsfw')
2011-12-23 16:48:17,845 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e4c7ec> about HardwareID('modalias', 'input:b0011v0002p0007e12B1-e0,1,3,k100,101,102,103,110,111,112,145,14A,14D,14E,ra0,1,18,1C,mlsfw')
2011-12-23 16:48:17,845 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e4c7ec> about HardwareID('modalias', 'pci:v00008086d0000283Asv00001734sd00001123bc0Csc03i20')
2011-12-23 16:48:17,845 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e4c7ec> about HardwareID('modalias', 'dmi:bvnPhoenixTechnologiesLTD:bvrV1.06:bd12/04/2007:svnFUJITSUSIEMENS:pnAMILOLi2727:pvr20:rvnFUJITSUSIEMENS:rnLV1:rvr1C:cvnFUJITSUSIEMENS:ct10:cvrA2040:')
2011-12-23 16:48:17,845 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e4c7ec> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-12-23 16:48:17,845 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e4c7ec> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2011-12-23 16:48:17,846 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e4c7ec> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2011-12-23 16:48:17,846 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e4c7ec> about HardwareID('modalias', 'usb:v0458p003Ad0100dc00dsc00dp00ic03isc01ip02')
2011-12-23 16:48:17,846 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e4c7ec> about HardwareID('modalias', 'acpi:PNP0303:')
2011-12-23 16:48:17,846 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e4c7ec> about HardwareID('modalias', 'acpi:PNP0100:')
2011-12-23 16:48:17,846 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e4c7ec> about HardwareID('modalias', 'pci:v00008086d00002836sv00001734sd00001123bc0Csc03i20')
2011-12-23 16:48:17,846 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e4c7ec> about HardwareID('modalias', 'pci:v00008086d00002835sv00001734sd00001123bc0Csc03i00')
2011-12-23 16:48:17,846 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e4c7ec> about HardwareID('modalias', 'pci:v00008086d00002832sv00001734sd00001123bc0Csc03i00')
2011-12-23 16:48:17,846 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e4c7ec> about HardwareID('modalias', 'pci:v000010ECd00008136sv00001734sd00001123bc02sc00i00')
2011-12-23 16:48:17,847 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e4c7ec> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2011-12-23 16:48:17,847 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e4c7ec> about HardwareID('modalias', 'acpi:PNP0200:')
2011-12-23 16:48:17,847 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e4c7ec> about HardwareID('modalias', 'pci:v0000168Cd0000001Csv0000168Csd00003067bc02sc00i00')
2011-12-23 16:48:17,847 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e4c7ec> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-12-23 16:48:17,847 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e4c7ec> about HardwareID('modalias', 'pci:v00008086d00002831sv00001734sd00001123bc0Csc03i00')
2011-12-23 16:48:17,847 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e4c7ec> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2011-12-23 16:48:17,847 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e4c7ec> about HardwareID('modalias', 'acpi:INT0800:')
2011-12-23 16:48:27,625 DEBUG: MadwifiHandler._update_blacklist(ath5k)
2011-12-23 16:48:27,641 DEBUG: unbind/rebind on driver /sys/module/ath_pci/drivers/pci:ath_pci: device 0000:08:00.0
2011-12-23 16:52:50,347 DEBUG: MadwifiHandler._update_blacklist(ath5k)
2011-12-23 16:52:50,353 DEBUG: unbind/rebind on driver /sys/module/ath_pci/drivers/pci:ath_pci: device 0000:08:00.0
2011-12-23 16:53:09,502 DEBUG: Shutting down
2011-12-23 16:54:28,721 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ef7aac>
2011-12-23 16:54:28,769 DEBUG: reading modalias file /lib/modules/2.6.32-37-generic/modules.alias
2011-12-23 16:54:28,938 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2011-12-23 16:54:28,950 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-12-23 16:54:29,002 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2011-12-23 16:54:29,013 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2011-12-23 16:54:29,031 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2011-12-23 16:54:29,035 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2011-12-23 16:54:29,058 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2011-12-23 16:54:29,436 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2011-12-23 16:54:29,482 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-12-23 16:54:29,483 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2011-12-23 16:54:29,527 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2011-12-23 16:54:29,528 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-12-23 16:54:29,532 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-12-23 16:54:29,542 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2011-12-23 16:54:29,542 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2011-12-23 16:54:29,542 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2011-12-23 16:54:29,592 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2011-12-23 16:54:29,593 DEBUG: Firmware for DVB cards not available
2011-12-23 16:54:29,593 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2011-12-23 16:54:29,661 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2011-12-23 16:54:29,662 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2011-12-23 16:54:29,678 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2011-12-23 16:54:29,679 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2011-12-23 16:54:29,679 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2011-12-23 16:54:29,690 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2011-12-23 16:54:29,745 DEBUG: Software modem not available
2011-12-23 16:54:29,746 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2011-12-23 16:54:29,751 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2011-12-23 16:54:29,751 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2011-12-23 16:54:29,751 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2011-12-23 16:54:29,765 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2011-12-23 16:54:29,766 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2011-12-23 16:54:29,777 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-12-23 16:54:29,781 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-12-23 16:54:29,781 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2011-12-23 16:54:29,793 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-12-23 16:54:29,793 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2011-12-23 16:54:29,813 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-12-23 16:54:29,813 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2011-12-23 16:54:29,823 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-12-23 16:54:29,824 DEBUG: all custom handlers loaded
2011-12-23 16:54:29,824 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ef7aac> about HardwareID('modalias', 'pci:v00008086d00002A03sv00001734sd00001123bc03sc80i00')
2011-12-23 16:54:30,162 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ef7aac> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-12-23 16:54:30,500 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-23 16:54:30,500 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ef7aac> about HardwareID('modalias', 'pci:v00008086d00002815sv00001734sd00001123bc06sc01i00')
2011-12-23 16:54:30,504 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2011-12-23 16:54:30,504 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ef7aac> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2011-12-23 16:54:30,505 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ef7aac> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-12-23 16:54:30,505 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ef7aac> about HardwareID('modalias', 'pci:v00008086d00002834sv00001734sd00001123bc0Csc03i00')
2011-12-23 16:54:30,508 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ef7aac> about HardwareID('modalias', 'input:b0001v10ECp0268e0001-e0,12,kramls1,2,fw')
2011-12-23 16:54:30,509 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-23 16:54:30,509 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ef7aac> about HardwareID('modalias', 'platform:pcspkr')
2011-12-23 16:54:30,509 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2011-12-23 16:54:30,510 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2011-12-23 16:54:30,510 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ef7aac> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2011-12-23 16:54:30,550 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ef7aac> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-12-23 16:54:30,550 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-23 16:54:30,550 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ef7aac> about HardwareID('modalias', 'acpi:PNP0000:')
2011-12-23 16:54:30,550 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ef7aac> about HardwareID('modalias', 'platform:eisa')
2011-12-23 16:54:30,551 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ef7aac> about HardwareID('modalias', 'pci:v00008086d00002830sv00001734sd00001123bc0Csc03i00')
2011-12-23 16:54:30,554 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ef7aac> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-12-23 16:54:30,555 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ef7aac> about HardwareID('modalias', 'pci:v00008086d0000283Esv00001734sd00001123bc0Csc05i00')
2011-12-23 16:54:30,559 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2011-12-23 16:54:30,559 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ef7aac> about HardwareID('modalias', 'pci:v00008086d00002A00sv00001734sd00001123bc06sc00i00')
2011-12-23 16:54:30,563 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_agp', 'jockey_handler': 'KernelModuleHandler'}
2011-12-23 16:54:30,563 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ef7aac> about HardwareID('modalias', 'acpi:SYN0310:SYN0300:SYN0002:PNP0F13:')
2011-12-23 16:54:30,563 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ef7aac> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-12-23 16:54:30,563 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ef7aac> about HardwareID('modalias', 'pci:v00008086d00002A02sv00001734sd00001123bc03sc00i00')
2011-12-23 16:54:30,567 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2011-12-23 16:54:30,567 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'vga16fb', 'jockey_handler': 'KernelModuleHandler'}
2011-12-23 16:54:30,567 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ef7aac> about HardwareID('modalias', 'acpi:device:')
2011-12-23 16:54:30,567 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ef7aac> about HardwareID('modalias', 'acpi:LNXTHERM:')
2011-12-23 16:54:30,568 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ef7aac> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-12-23 16:54:30,568 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ef7aac> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2011-12-23 16:54:30,568 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ef7aac> about HardwareID('modalias', 'pci:v00008086d0000284Bsv00001734sd00001123bc04sc03i00')
2011-12-23 16:54:30,572 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-12-23 16:54:30,572 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ef7aac> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2011-12-23 16:54:30,575 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ef7aac> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2011-12-23 16:54:30,576 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-23 16:54:30,576 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ef7aac> about HardwareID('modalias', 'input:b0003v0458p003Ae0111-e0,1,2,4,k110,111,112,r0,1,8,am4,lsfw')
2011-12-23 16:54:30,576 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-23 16:54:30,576 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ef7aac> about HardwareID('modalias', 'input:b0011v0002p0007e12B1-e0,1,3,k100,101,102,103,110,111,112,145,14A,14D,14E,ra0,1,18,1C,mlsfw')
2011-12-23 16:54:30,577 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-12-23 16:54:30,577 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-12-23 16:54:30,577 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-23 16:54:30,577 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ef7aac> about HardwareID('modalias', 'pci:v00008086d0000283Asv00001734sd00001123bc0Csc03i20')
2011-12-23 16:54:30,581 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ef7aac> about HardwareID('modalias', 'dmi:bvnPhoenixTechnologiesLTD:bvrV1.06:bd12/04/2007:svnFUJITSUSIEMENS:pnAMILOLi2727:pvr20:rvnFUJITSUSIEMENS:rnLV1:rvr1C:cvnFUJITSUSIEMENS:ct10:cvrA2040:')
2011-12-23 16:54:30,596 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ef7aac> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-12-23 16:54:30,596 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ef7aac> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2011-12-23 16:54:30,596 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-23 16:54:30,596 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ef7aac> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2011-12-23 16:54:30,597 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ef7aac> about HardwareID('modalias', 'usb:v0458p003Ad0100dc00dsc00dp00ic03isc01ip02')
2011-12-23 16:54:30,603 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-12-23 16:54:30,603 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ef7aac> about HardwareID('modalias', 'acpi:PNP0303:')
2011-12-23 16:54:30,604 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ef7aac> about HardwareID('modalias', 'acpi:PNP0100:')
2011-12-23 16:54:30,604 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ef7aac> about HardwareID('modalias', 'pci:v00008086d00002836sv00001734sd00001123bc0Csc03i20')
2011-12-23 16:54:30,607 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ef7aac> about HardwareID('modalias', 'pci:v00008086d00002835sv00001734sd00001123bc0Csc03i00')
2011-12-23 16:54:30,611 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ef7aac> about HardwareID('modalias', 'pci:v00008086d00002832sv00001734sd00001123bc0Csc03i00')
2011-12-23 16:54:30,615 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ef7aac> about HardwareID('modalias', 'pci:v000010ECd00008136sv00001734sd00001123bc02sc00i00')
2011-12-23 16:54:30,626 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2011-12-23 16:54:30,626 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ef7aac> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2011-12-23 16:54:30,627 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-23 16:54:30,627 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ef7aac> about HardwareID('modalias', 'acpi:PNP0200:')
2011-12-23 16:54:30,627 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ef7aac> about HardwareID('modalias', 'pci:v0000168Cd0000001Csv0000168Csd00003067bc02sc00i00')
2011-12-23 16:54:30,640 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ath5k', 'jockey_handler': 'KernelModuleHandler'}
2011-12-23 16:54:30,640 DEBUG: got handler kmod:ath_pci([MadwifiHandler, nonfree, disabled] Alternate Atheros "madwifi" driver)
2011-12-23 16:54:30,640 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ef7aac> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-12-23 16:54:30,651 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2011-12-23 16:54:30,651 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-12-23 16:54:30,651 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ef7aac> about HardwareID('modalias', 'pci:v00008086d00002831sv00001734sd00001123bc0Csc03i00')
2011-12-23 16:54:30,655 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ef7aac> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2011-12-23 16:54:30,655 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-12-23 16:54:30,655 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9ef7aac> about HardwareID('modalias', 'acpi:INT0800:')
2011-12-23 16:54:30,655 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa3237ec> about HardwareID('modalias', 'pci:v00008086d00002A03sv00001734sd00001123bc03sc80i00')
2011-12-23 16:54:30,656 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa3237ec> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-12-23 16:54:30,656 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa3237ec> about HardwareID('modalias', 'pci:v00008086d00002815sv00001734sd00001123bc06sc01i00')
2011-12-23 16:54:30,656 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa3237ec> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2011-12-23 16:54:30,656 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa3237ec> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-12-23 16:54:30,656 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa3237ec> about HardwareID('modalias', 'pci:v00008086d00002834sv00001734sd00001123bc0Csc03i00')
2011-12-23 16:54:30,656 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa3237ec> about HardwareID('modalias', 'input:b0001v10ECp0268e0001-e0,12,kramls1,2,fw')
2011-12-23 16:54:30,656 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa3237ec> about HardwareID('modalias', 'platform:pcspkr')
2011-12-23 16:54:30,656 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa3237ec> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2011-12-23 16:54:30,657 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa3237ec> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-12-23 16:54:30,657 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa3237ec> about HardwareID('modalias', 'acpi:PNP0000:')
2011-12-23 16:54:30,657 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa3237ec> about HardwareID('modalias', 'platform:eisa')
2011-12-23 16:54:30,657 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa3237ec> about HardwareID('modalias', 'pci:v00008086d00002830sv00001734sd00001123bc0Csc03i00')
2011-12-23 16:54:30,657 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa3237ec> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-12-23 16:54:30,657 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa3237ec> about HardwareID('modalias', 'pci:v00008086d0000283Esv00001734sd00001123bc0Csc05i00')
2011-12-23 16:54:30,657 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa3237ec> about HardwareID('modalias', 'pci:v00008086d00002A00sv00001734sd00001123bc06sc00i00')
2011-12-23 16:54:30,657 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa3237ec> about HardwareID('modalias', 'acpi:SYN0310:SYN0300:SYN0002:PNP0F13:')
2011-12-23 16:54:30,658 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa3237ec> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-12-23 16:54:30,658 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa3237ec> about HardwareID('modalias', 'pci:v00008086d00002A02sv00001734sd00001123bc03sc00i00')
2011-12-23 16:54:30,658 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa3237ec> about HardwareID('modalias', 'acpi:device:')
2011-12-23 16:54:30,658 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa3237ec> about HardwareID('modalias', 'acpi:LNXTHERM:')
2011-12-23 16:54:30,658 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa3237ec> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-12-23 16:54:30,658 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa3237ec> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2011-12-23 16:54:30,658 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa3237ec> about HardwareID('modalias', 'pci:v00008086d0000284Bsv00001734sd00001123bc04sc03i00')
2011-12-23 16:54:30,658 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa3237ec> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2011-12-23 16:54:30,659 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa3237ec> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2011-12-23 16:54:30,659 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa3237ec> about HardwareID('modalias', 'input:b0003v0458p003Ae0111-e0,1,2,4,k110,111,112,r0,1,8,am4,lsfw')
2011-12-23 16:54:30,659 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa3237ec> about HardwareID('modalias', 'input:b0011v0002p0007e12B1-e0,1,3,k100,101,102,103,110,111,112,145,14A,14D,14E,ra0,1,18,1C,mlsfw')
2011-12-23 16:54:30,659 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa3237ec> about HardwareID('modalias', 'pci:v00008086d0000283Asv00001734sd00001123bc0Csc03i20')
2011-12-23 16:54:30,659 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa3237ec> about HardwareID('modalias', 'dmi:bvnPhoenixTechnologiesLTD:bvrV1.06:bd12/04/2007:svnFUJITSUSIEMENS:pnAMILOLi2727:pvr20:rvnFUJITSUSIEMENS:rnLV1:rvr1C:cvnFUJITSUSIEMENS:ct10:cvrA2040:')
2011-12-23 16:54:30,659 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa3237ec> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-12-23 16:54:30,659 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa3237ec> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2011-12-23 16:54:30,659 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa3237ec> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2011-12-23 16:54:30,660 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa3237ec> about HardwareID('modalias', 'usb:v0458p003Ad0100dc00dsc00dp00ic03isc01ip02')
2011-12-23 16:54:30,660 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa3237ec> about HardwareID('modalias', 'acpi:PNP0303:')
2011-12-23 16:54:30,660 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa3237ec> about HardwareID('modalias', 'acpi:PNP0100:')
2011-12-23 16:54:30,660 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa3237ec> about HardwareID('modalias', 'pci:v00008086d00002836sv00001734sd00001123bc0Csc03i20')
2011-12-23 16:54:30,660 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa3237ec> about HardwareID('modalias', 'pci:v00008086d00002835sv00001734sd00001123bc0Csc03i00')
2011-12-23 16:54:30,660 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa3237ec> about HardwareID('modalias', 'pci:v00008086d00002832sv00001734sd00001123bc0Csc03i00')
2011-12-23 16:54:30,660 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa3237ec> about HardwareID('modalias', 'pci:v000010ECd00008136sv00001734sd00001123bc02sc00i00')
2011-12-23 16:54:30,660 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa3237ec> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2011-12-23 16:54:30,661 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa3237ec> about HardwareID('modalias', 'acpi:PNP0200:')
2011-12-23 16:54:30,661 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa3237ec> about HardwareID('modalias', 'pci:v0000168Cd0000001Csv0000168Csd00003067bc02sc00i00')
2011-12-23 16:54:30,661 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa3237ec> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-12-23 16:54:30,661 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa3237ec> about HardwareID('modalias', 'pci:v00008086d00002831sv00001734sd00001123bc0Csc03i00')
2011-12-23 16:54:30,661 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa3237ec> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2011-12-23 16:54:30,661 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa3237ec> about HardwareID('modalias', 'acpi:INT0800:')
2011-12-23 16:55:35,481 DEBUG: MadwifiHandler._update_blacklist(ath5k)
2011-12-23 16:55:35,493 DEBUG: unbind/rebind on driver /sys/module/ath_pci/drivers/pci:ath_pci: device 0000:08:00.0
2011-12-23 16:56:23,891 DEBUG: Shutting down
```

Any ideas what to do next?

---

### Post by praseodym on 2011-12-23
Maybe the ath5k needs to be active for replacing it? Change the blacklist file to

```
blacklist ath_pci
# blacklist ath5k
```
reboot and try it again

---

### Post by Katsu on 2011-12-23
Nope..same error msg,no wireless network detected...
Maybe totally removing all wifi drivers and reinstalling would help?
If so could someone write down how to remove those?
Thnx in advance!

---

### Post by praseodym on 2011-12-23
```
sudo apt-get install linux-headers-$(uname -r) build-essential
wget http://snapshots.madwifi-project.org/madwifi-0.9.4-current.tar.gz
tar xvf madwifi-0.9.4-current.tar.gz
cd madwifi-0.9.4-r*
make
sudo make uninstall
sudo make install 
```
Blacklist ath5k again and reboot. Check:

```
uname -a
iwconfig
lsmod
dmesg | grep ath
sudo iwlist scan
```

---

### Post by Katsu on 2011-12-23
Madwifi removed,installed again,ath5k blacklisted,rebooted..still not working...

i assume that you would like to see results which i got after running commands under "Check" so;

```
luka1@Luka:~$ uname -a
Linux Luka 2.6.32-37-generic #81-Ubuntu SMP Fri Dec 2 20:35:14 UTC 2011 i686 GNU/Linux
luka1@Luka:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"LUX"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

luka1@Luka:~$ lsmod
Module                  Size  Used by
wlan_wep                5141  0 
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_realtek   203440  1 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
joydev                  8740  0 
wlan_scan_sta          11842  1 
ath_rate_sample        11476  1 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19130  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i915                  289715  3 
drm_kms_helper         29329  1 i915
ath_pci               193293  0 
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wlan                  222924  5 wlan_wep,wlan_scan_sta,ath_rate_sample,ath_pci
drm                   163747  4 i915,drm_kms_helper
intel_agp              24375  2 i915
psmouse                63677  0 
serio_raw               3978  0 
ath_hal               398604  3 ath_rate_sample,ath_pci
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
i2c_algo_bit            5028  1 i915
video                  17375  1 i915
output                  1871  1 video
agpgart                31724  2 drm,intel_agp
lp                      7028  0 
parport                32635  2 ppdev,lp
usbhid                 36110  0 
hid                    67288  1 usbhid
r8169                  34140  0 
mii                     4381  1 r8169
luka1@Luka:~$ dmesg | grep ath
[    0.560879] device-mapper: multipath: version 1.1.0 loaded
[    0.560882] device-mapper: multipath round-robin: version 1.0.0 loaded
[   14.205809] ath_pci 0000:08:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   14.205824] ath_pci 0000:08:00.0: setting latency timer to 64
[   15.616507] MadWifi: ath_attach: Switching rfkill capability off.
[   15.628322] ath_pci: wifi0: Atheros 5424/2424: mem=0xfa000000, irq=18
[   26.520018] ath0: no IPv6 routers present
[   36.563321] ath0: unknown SIOCSIWAUTH flag 12
[   87.548043] ath_pci 0000:08:00.0: PCI INT A disabled
[   87.548220] ath_pci 0000:08:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   87.548236] ath_pci 0000:08:00.0: setting latency timer to 64
[   88.045746] MadWifi: ath_attach: Switching rfkill capability off.
[   88.052212] ath_pci: wifi0: Atheros 5424/2424: mem=0xfa000000, irq=18
[   88.398373] ath0: unknown SIOCSIWAUTH flag 12
[   98.403995] ath0: unknown SIOCSIWAUTH flag 12
[   98.488018] ath0: no IPv6 routers present
[  108.421608] ath0: unknown SIOCSIWAUTH flag 12
[  118.432074] ath0: unknown SIOCSIWAUTH flag 12
[  119.116740] ath0: unknown SIOCSIWAUTH flag 12
[  129.117956] ath0: unknown SIOCSIWAUTH flag 12
[  139.128406] ath0: unknown SIOCSIWAUTH flag 12
luka1@Luka:~$ sudo iwlist scan
[sudo] password for luka1: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      No scan results



```

I got tough love with Linux...:lolflag:

---

### Post by praseodym on 2011-12-23
Remove the current wireless profile and create a new one, because the interface name changed to ath0. Also check the country code settings for this module:

```
echo "options ath_pci countrycode=[COLOR="Red"]276[/COLOR]" | sudo tee /etc/modprobe.d/ath_pci.conf
sudo modprobe -rfv ath_pci
sudo modprobe -v ath_pci
```
276 is for Germany, check your countrys code here:

[http://www.davros.org/misc/iso3166.html#existing](http://www.davros.org/misc/iso3166.html#existing)

---

