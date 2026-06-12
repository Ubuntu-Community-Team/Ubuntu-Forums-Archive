---
title: "Broadcom BCM4321"
date: 2013-02-23
forum: Networking &amp; Wireless
---

### Post by tomster2300 on 2013-02-23
Hi all, 

I'm really a Linux noob and need some guidance with a wifi issue.  I've tried a number of things from other posts but nothing really seems to be working.  

I've done a fresh install of Ubuntu 12.04 64 bit and have reinstalled bcmwl-kernel-source via the following commands: 

```
 
sudo apt-get - - purge remove bcmwl-kernel-source
sudo apt-get update
sudo apt-get - - reinstall install bcmwl-kernel-source

```This allows me to get the wireless options in my network panel dropdown to appear, but it is greyed out and says disconnected.  

At one point I uninstalled the above and installed drivers that allowed my wireless network to be found, but I could never complete the password authentication on it.  To be honest, I wasn't really sure what I was doing and can no longer find that specific thread.

Here are the results of lspci:

06:01.0 Network controller [0280]: Broadcom Corporation BCM4321 802.11b/g/n [14e4:4329] (rev 01)

Please help me get this fixed!  Thanks!

---

### Post by westie457 on 2013-02-23
Hi, lets get this started.

Firstly go to here and follow the suggestion. [http://ubuntuforums.org/showpost.php?p=12520783&postcount=2](http://ubuntuforums.org/showpost.php?p=12520783&postcount=2)

Further help will come after the 'netinfo.txt' file has been looked at.

Thank you.

---

### Post by tomster2300 on 2013-02-23
Thank you!  This script is kind of awesome btw.  

File attached.

---

### Post by westie457 on 2013-02-23
That must be a record for posting the netinfo file.

Post the output of this please ```
apt-cache showpkg bcmwl-kernel-source
```

Thank you.

---

### Post by Bucky Ball on 2013-02-23
*Thread moved to **Networking & Wireless**.*

---

### Post by tomster2300 on 2013-02-23
> **westie457 said:**
> That must be a record for posting the netinfo file.

Post the output of this please ```
apt-cache showpkg bcmwl-kernel-source
```

Thank you.

I'm just ready to get this fixed, so I'm extremely happy that you responded to me so quickly :)

I've attached the output of your command in a txt file (please let me know if you would rather me paste it directly into my post instead).

Thanks!

---

### Post by westie457 on 2013-02-23
For the last one code tags would have been better, however the information is there.

This suggestion may or may not work because it is for a different chip. It won't hurt to try it.

Work through the advice in this link please. [http://askubuntu.com/questions/250858/broadcom-wireless-bcm4313-on-12-04-lts/250896#250896](http://askubuntu.com/questions/250858/broadcom-wireless-bcm4313-on-12-04-lts/250896#250896)

Let us know what happens.

Thank you.

---

### Post by tomster2300 on 2013-02-23
I tried the apt-get route and then tried downloading the file and installing via the software center, but each time I received the error seen in the attached screenshot.

---

### Post by tomster2300 on 2013-02-23
> **tomster2300 said:**
> I tried the apt-get route and then tried downloading the file and installing via the software center, but each time I received the error seen in the attached screenshot.

So I purged / removed bcmwl-kernel-source again (to make sure the failed installation was completely gone), rebooted and tried manually installing the 64 bit package again.  I still got the error this time, but when I clicked cancel it paused for a minute and now says that it was successfully installed.  I rebooted the machine but it did not add wireless options to my network dropdown menu (that got removed when I uninstalled bcmwl-kernel-source).

EDIT: 

I take that back...I went into additional drivers and attempted to activate the STA driver, only to get the attached screenshot...

Here is my jockey.log as well:

```

2013-02-23 15:43:36,365 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8>
2013-02-23 15:43:38,609 DEBUG: reading modalias file /lib/modules/3.5.0-23-generic/modules.alias
2013-02-23 15:43:38,692 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2013-02-23 15:43:38,692 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2013-02-23 15:43:38,735 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2013-02-23 15:43:38,759 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2013-02-23 15:43:38,759 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2013-02-23 15:43:38,760 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2013-02-23 15:43:38,765 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2013-02-23 15:43:38,770 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2013-02-23 15:43:38,913 DEBUG: XorgDriverHandler(omapdrm_pvr, pvr-omap4, None): Disabling as package is not compatible with Q-LTS X.org
2013-02-23 15:43:38,914 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2013-02-23 15:43:38,914 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2013-02-23 15:43:38,921 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2013-02-23 15:43:38,925 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2013-02-23 15:43:38,925 DEBUG: fglrx.available: falling back to default
2013-02-23 15:43:39,073 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2013-02-23 15:43:39,077 WARNING: modinfo for module fglrx_experimental_9 failed: ERROR: modinfo: could not find module fglrx_experimental_9

2013-02-23 15:43:39,096 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverExperimental9 from name FglrxDriverExperimental9
2013-02-23 15:43:39,096 DEBUG: fglrx.available: falling back to default
2013-02-23 15:43:39,226 DEBUG: ATI/AMD proprietary FGLRX graphics driver (**experimental** beta) availability undetermined, adding to pool
2013-02-23 15:43:39,229 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2013-02-23 15:43:39,233 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2013-02-23 15:43:39,233 DEBUG: fglrx.available: falling back to default
2013-02-23 15:43:39,366 DEBUG: XorgDriverHandler(fglrx, fglrx, None): Disabling as package is not compatible with Q-LTS X.org
2013-02-23 15:43:39,366 DEBUG: ATI/AMD proprietary FGLRX graphics driver not available
2013-02-23 15:43:39,366 DEBUG: loading custom handler /usr/share/jockey/handlers/cdv.py
2013-02-23 15:43:39,371 WARNING: modinfo for module cedarview_gfx failed: ERROR: modinfo: could not find module cedarview_gfx

2013-02-23 15:43:39,371 DEBUG: Instantiated Handler subclass __builtin__.CdvDriver from name CdvDriver
2013-02-23 15:43:39,371 DEBUG: cdv.available: falling back to default
2013-02-23 15:43:39,498 DEBUG: XorgDriverHandler(cedarview_gfx, cedarview-graphics-drivers, None): Disabling as package is not compatible with Q-LTS X.org
2013-02-23 15:43:39,498 DEBUG: Intel Cedarview graphics driver not available
2013-02-23 15:43:39,498 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2013-02-23 15:43:39,513 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2013-02-23 15:43:39,521 DEBUG: Software modem not available
2013-02-23 15:43:39,521 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2013-02-23 15:43:39,526 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2013-02-23 15:43:39,530 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2013-02-23 15:43:39,531 DEBUG: nvidia.available: falling back to default
2013-02-23 15:43:39,657 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package is not compatible with Q-LTS X.org
2013-02-23 15:43:39,657 DEBUG: NVIDIA accelerated graphics driver not available
2013-02-23 15:43:39,660 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2013-02-23 15:43:39,664 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2013-02-23 15:43:39,665 DEBUG: nvidia.available: falling back to default
2013-02-23 15:43:39,782 DEBUG: XorgDriverHandler(nvidia_current, nvidia-current, None): Disabling as package is not compatible with Q-LTS X.org
2013-02-23 15:43:39,782 DEBUG: NVIDIA accelerated graphics driver not available
2013-02-23 15:43:39,784 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2013-02-23 15:43:39,787 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2013-02-23 15:43:39,787 DEBUG: nvidia.available: falling back to default
2013-02-23 15:43:39,944 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2013-02-23 15:43:39,946 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2013-02-23 15:43:39,950 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2013-02-23 15:43:39,951 DEBUG: nvidia.available: falling back to default
2013-02-23 15:43:40,073 DEBUG: XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling as package is not compatible with Q-LTS X.org
2013-02-23 15:43:40,073 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2013-02-23 15:43:40,076 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2013-02-23 15:43:40,080 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2013-02-23 15:43:40,081 DEBUG: nvidia.available: falling back to default
2013-02-23 15:43:40,227 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2013-02-23 15:43:40,231 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2013-02-23 15:43:40,235 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2013-02-23 15:43:40,235 DEBUG: nvidia.available: falling back to default
2013-02-23 15:43:40,359 DEBUG: XorgDriverHandler(nvidia_173, nvidia-173, None): Disabling as package is not compatible with Q-LTS X.org
2013-02-23 15:43:40,359 DEBUG: NVIDIA accelerated graphics driver not available
2013-02-23 15:43:40,362 WARNING: modinfo for module nvidia_experimental_310 failed: ERROR: modinfo: could not find module nvidia_experimental_310

2013-02-23 15:43:40,381 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverExperimental310 from name NvidiaDriverExperimental310
2013-02-23 15:43:40,382 DEBUG: nvidia.available: falling back to default
2013-02-23 15:43:40,520 DEBUG: NVIDIA accelerated graphics driver (**experimental** beta) availability undetermined, adding to pool
2013-02-23 15:43:40,523 WARNING: modinfo for module nvidia_experimental_304 failed: ERROR: modinfo: could not find module nvidia_experimental_304

2013-02-23 15:43:40,540 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverExperimental304 from name NvidiaDriverExperimental304
2013-02-23 15:43:40,541 DEBUG: nvidia.available: falling back to default
2013-02-23 15:43:40,662 DEBUG: XorgDriverHandler(nvidia_experimental_304, nvidia-experimental-304, None): Disabling as package is not compatible with Q-LTS X.org
2013-02-23 15:43:40,663 DEBUG: NVIDIA accelerated graphics driver (**experimental** beta) not available
2013-02-23 15:43:40,663 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2013-02-23 15:43:40,666 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2013-02-23 15:43:40,667 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2013-02-23 15:43:40,682 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2013-02-23 15:43:40,682 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2013-02-23 15:43:40,705 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2013-02-23 15:43:40,705 DEBUG: Firmware for DVB cards not available
2013-02-23 15:43:40,705 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2013-02-23 15:43:40,710 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2013-02-23 15:43:40,711 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2013-02-23 15:43:40,711 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2013-02-23 15:43:40,711 DEBUG: all custom handlers loaded
2013-02-23 15:43:40,711 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'acpi:PNP0C02:')
2013-02-23 15:43:40,711 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-02-23 15:43:40,712 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc00ip00')
2013-02-23 15:43:40,750 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-02-23 15:43:40,813 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:43:40,813 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'usb:v1D6Bp0001d0305dc09dsc00dp00ic09isc00ip00')
2013-02-23 15:43:40,814 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'pci:v00008086d00002822sv00001458sd0000B000bc01sc04i00')
2013-02-23 15:43:41,054 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'pci:v00008086d00002C2Asv00001458sd00005000bc06sc00i00')
2013-02-23 15:43:41,057 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'dmi:bvnAwardSoftwareInternational,Inc.:bvrF11:bd03/11/2010:svnGigabyteTechnologyCo.,Ltd.:pnEX58-UD3R:pvr:rvnGigabyteTechnologyCo.,Ltd.:rnEX58-UD3R:rvrx.x:cvnGigabyteTechnologyCo.,Ltd.:ct3:cvr:')
2013-02-23 15:43:41,067 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'usb:v05ACp0220d0069dc00dsc00dp00ic03isc01ip01')
2013-02-23 15:43:41,086 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-02-23 15:43:41,087 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:43:41,087 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2013-02-23 15:43:41,087 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:43:41,087 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'usb:v05ACp0220d0069dc00dsc00dp00ic03isc00ip00')
2013-02-23 15:43:41,087 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-02-23 15:43:41,087 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:43:41,087 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'pci:v00008086d0000342Fsv00000000sd00000000bc08sc00i20')
2013-02-23 15:43:41,090 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'acpi:PNP0200:')
2013-02-23 15:43:41,090 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'platform:regulatory')
2013-02-23 15:43:41,090 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2013-02-23 15:43:41,094 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-23 15:43:41,094 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:43:41,094 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'pci:v00008086d00003A37sv00001458sd00005004bc0Csc03i00')
2013-02-23 15:43:41,097 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'x86cpu:vendor:0000:family:0006:model:001A:feature:,0000,0001,0002,0003,0004,0005,0006,0007,0008,0009,000B,000C,000D,000E,000F,0010,0011,0013,0015,0016,0017,0018,0019,001A,001B,001C,001D,001F,002B,0034,003B,003D,0068,006B,006C,006D,006F,0070,0072,0074,0076,0078,007C,0080,0082,0083,0084,0085,0087,0088,0089,008D,008E,008F,0093,0094,0097,00C0,00E7,0100,0101,0102,0103,0104')
2013-02-23 15:43:41,100 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'kvm_intel'}
2013-02-23 15:43:41,100 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'kvm_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:43:41,100 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'microcode'}
2013-02-23 15:43:41,100 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'microcode', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:43:41,100 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'coretemp'}
2013-02-23 15:43:41,101 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'coretemp', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:43:41,101 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2013-02-23 15:43:41,107 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2013-02-23 15:43:41,107 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:43:41,107 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'acpi:PNP0103:')
2013-02-23 15:43:41,107 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'pci:v00008086d00002C11sv00001458sd00005000bc06sc00i00')
2013-02-23 15:43:41,110 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'acpi:PNP0700:')
2013-02-23 15:43:41,110 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'pci:v00008086d00003427sv00000000sd00000000bc08sc00i00')
2013-02-23 15:43:41,112 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'pci:v00008086d0000342Dsv00000000sd00000000bc08sc00i20')
2013-02-23 15:43:41,115 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'pci:v00008086d00002C23sv00001458sd00005000bc06sc00i00')
2013-02-23 15:43:41,117 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'platform:pcspkr')
2013-02-23 15:43:41,117 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2013-02-23 15:43:41,117 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:43:41,118 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2013-02-23 15:43:41,118 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:43:41,118 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'pci:v00008086d0000244Esv00001458sd00005000bc06sc04i01')
2013-02-23 15:43:41,120 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'pci:v00008086d00002C41sv00001458sd00005000bc06sc00i00')
2013-02-23 15:43:41,123 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'acpi:PNP0B00:')
2013-02-23 15:43:41,123 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'pci:v00008086d00002C20sv00001458sd00005000bc06sc00i00')
2013-02-23 15:43:41,125 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'pci:v00001002d0000AAB0sv00001787sd0000AAB0bc04sc03i00')
2013-02-23 15:43:41,409 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-02-23 15:43:41,409 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:43:41,409 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-02-23 15:43:41,409 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:43:41,409 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'pci:v00008086d00003A16sv00001458sd00005001bc06sc01i00')
2013-02-23 15:43:41,412 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'lpc_ich'}
2013-02-23 15:43:41,412 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'lpc_ich', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:43:41,412 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'pci:v00001002d00006819sv00001787sd00002320bc03sc00i00')
2013-02-23 15:43:41,415 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2013-02-23 15:43:41,415 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:43:41,415 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_experimental_9', 'package': 'fglrx-experimental-9'}
2013-02-23 15:43:41,427 DEBUG: fglrx.enabled(fglrx_experimental_9): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-02-23 15:43:41,427 DEBUG: fglrx_experimental_9 is not the alternative in use
2013-02-23 15:43:41,415 DEBUG: found match in handler pool xorg:fglrx_experimental_9([FglrxDriverExperimental9, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (**experimental** beta))
2013-02-23 15:43:41,431 WARNING: modinfo for module fglrx_experimental_9 failed: ERROR: modinfo: could not find module fglrx_experimental_9

2013-02-23 15:43:41,435 DEBUG: fglrx.available: falling back to default
2013-02-23 15:43:41,577 DEBUG: fglrx.enabled(fglrx_experimental_9): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-02-23 15:43:41,577 DEBUG: fglrx_experimental_9 is not the alternative in use
2013-02-23 15:43:41,565 DEBUG: got handler xorg:fglrx_experimental_9([FglrxDriverExperimental9, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (**experimental** beta))
2013-02-23 15:43:41,577 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2013-02-23 15:43:41,589 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-02-23 15:43:41,589 DEBUG: fglrx_updates is not the alternative in use
2013-02-23 15:43:41,577 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2013-02-23 15:43:41,593 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2013-02-23 15:43:41,598 DEBUG: fglrx.available: falling back to default
2013-02-23 15:43:41,730 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-02-23 15:43:41,730 DEBUG: fglrx_updates is not the alternative in use
2013-02-23 15:43:41,722 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2013-02-23 15:43:41,731 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2013-02-23 15:43:41,739 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-02-23 15:43:41,739 DEBUG: fglrx is not the alternative in use
2013-02-23 15:43:41,731 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2013-02-23 15:43:41,742 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2013-02-23 15:43:41,747 DEBUG: fglrx.available: falling back to default
2013-02-23 15:43:41,888 DEBUG: XorgDriverHandler(fglrx, fglrx, None): Disabling as package is not compatible with Q-LTS X.org
2013-02-23 15:43:41,901 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-02-23 15:43:41,901 DEBUG: fglrx is not the alternative in use
2013-02-23 15:43:41,889 DEBUG: ignoring unavailable handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2013-02-23 15:43:41,901 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'pci:v00008086d00003A3Csv00001458sd00005006bc0Csc03i20')
2013-02-23 15:43:41,906 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2013-02-23 15:43:41,906 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2013-02-23 15:43:41,906 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:43:41,906 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2013-02-23 15:43:41,907 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:43:41,907 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'pci:v00008086d00003A35sv00001458sd00005004bc0Csc03i00')
2013-02-23 15:43:41,910 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'pci:v00008086d00003A3Asv00001458sd00005006bc0Csc03i20')
2013-02-23 15:43:41,915 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'pci:v000014E4d00004329sv00001385sd00007D00bc02sc80i00')
2013-02-23 15:43:41,949 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ssb'}
2013-02-23 15:43:41,949 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ssb', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:43:41,949 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'wl', 'package': 'bcmwl-kernel-source'}
2013-02-23 15:43:42,012 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-02-23 15:43:41,950 DEBUG: found match in handler pool kmod:wl([BroadcomWLHandler, nonfree, enabled] Broadcom STA wireless driver)
2013-02-23 15:43:42,074 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-02-23 15:43:42,012 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, enabled] Broadcom STA wireless driver)
2013-02-23 15:43:42,075 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'wl'}
2013-02-23 15:43:42,136 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-02-23 15:43:42,075 DEBUG: found match in handler pool kmod:wl([BroadcomWLHandler, nonfree, enabled] Broadcom STA wireless driver)
2013-02-23 15:43:42,196 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-02-23 15:43:42,137 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, enabled] Broadcom STA wireless driver)
2013-02-23 15:43:42,196 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'usb:v18E3p9101d0000dc00dsc00dp00ic08isc06ip50')
2013-02-23 15:43:42,197 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uas'}
2013-02-23 15:43:42,197 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uas', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:43:42,197 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'acpi:INT0800:')
2013-02-23 15:43:42,197 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'pci:v00008086d00002C32sv00001458sd00005000bc06sc00i00')
2013-02-23 15:43:42,200 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'pci:v00008086d00003A36sv00001458sd00005004bc0Csc03i00')
2013-02-23 15:43:42,203 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'usb:v05ACp1006d9615dc09dsc00dp01ic09isc00ip00')
2013-02-23 15:43:42,204 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'pci:v00008086d00002C30sv00001458sd00005000bc06sc00i00')
2013-02-23 15:43:42,207 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'acpi:PNP0800:')
2013-02-23 15:43:42,207 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'pci:v00008086d00002C29sv00001458sd00005000bc06sc00i00')
2013-02-23 15:43:42,209 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'pci:v00008086d00003A39sv00001458sd00005004bc0Csc03i00')
2013-02-23 15:43:42,212 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'pci:v00008086d00002C22sv00001458sd00005000bc06sc00i00')
2013-02-23 15:43:42,214 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'pci:v00008086d00003423sv00000000sd00000000bc08sc00i00')
2013-02-23 15:43:42,217 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'pci:v00008086d0000342Esv00000000sd00000000bc08sc00i00')
2013-02-23 15:43:42,220 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i7core_edac'}
2013-02-23 15:43:42,220 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i7core_edac', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:43:42,220 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-02-23 15:43:42,220 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-23 15:43:42,220 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:43:42,220 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-02-23 15:43:42,220 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:43:42,220 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'pci:v00008086d00003426sv00000000sd00000000bc08sc00i00')
2013-02-23 15:43:42,223 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'pci:v00008086d00002C19sv00001458sd00005000bc06sc00i00')
2013-02-23 15:43:42,225 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'platform:gpio_ich')
2013-02-23 15:43:42,226 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'gpio_ich'}
2013-02-23 15:43:42,226 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'gpio_ich', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:43:42,226 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'pci:v00008086d00002C01sv00001458sd00005000bc06sc00i00')
2013-02-23 15:43:42,228 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2013-02-23 15:43:42,228 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-23 15:43:42,228 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:43:42,229 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'platform:microcode')
2013-02-23 15:43:42,229 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'wmi:F6CB5C3C-9CAE-4EBD-B577-931EA32A2CC0')
2013-02-23 15:43:42,229 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mxm_wmi'}
2013-02-23 15:43:42,229 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mxm_wmi', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:43:42,229 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'pci:v00008086d00003405sv00001458sd00005000bc06sc00i00')
2013-02-23 15:43:42,232 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'pci:v00008086d00002C1Csv00001458sd00005000bc06sc00i00')
2013-02-23 15:43:42,235 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'pci:v00008086d00002C31sv00001458sd00005000bc06sc00i00')
2013-02-23 15:43:42,238 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'acpi:PNP0C04:')
2013-02-23 15:43:42,238 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'pci:v00008086d00002C33sv00001458sd00005000bc06sc00i00')
2013-02-23 15:43:42,240 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip01')
2013-02-23 15:43:42,241 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-02-23 15:43:42,241 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:43:42,241 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2013-02-23 15:43:42,241 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:43:42,241 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,2,4,k110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,r0,1,6,8,am4,lsfw')
2013-02-23 15:43:42,241 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-23 15:43:42,241 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:43:42,241 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-02-23 15:43:42,241 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:43:42,241 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'acpi:PNP0C01:')
2013-02-23 15:43:42,242 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2013-02-23 15:43:42,242 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-23 15:43:42,242 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:43:42,242 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'pci:v00008086d00003A34sv00001458sd00005004bc0Csc03i00')
2013-02-23 15:43:42,244 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001458sd0000E000bc02sc00i00')
2013-02-23 15:43:42,251 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2013-02-23 15:43:42,251 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:43:42,251 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2013-02-23 15:43:42,251 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-23 15:43:42,252 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:43:42,252 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'pci:v00008086d00003428sv00000000sd00000000bc08sc00i00')
2013-02-23 15:43:42,254 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'pci:v00008086d00002C2Bsv00001458sd00005000bc06sc00i00')
2013-02-23 15:43:42,257 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'platform:coretemp')
2013-02-23 15:43:42,258 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'hid:b0003g0000v0000046Dp0000C52B')
2013-02-23 15:43:42,294 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'hid_logitech_dj'}
2013-02-23 15:43:42,294 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'hid_logitech_dj', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:43:42,294 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'hid:b0003g0000v000005ACp00000220')
2013-02-23 15:43:42,295 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'hid_apple'}
2013-02-23 15:43:42,296 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'hid_apple', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:43:42,296 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-02-23 15:43:42,296 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'input:b0003v05ACp0220e0111-e0,1,4,k71,72,73,A1,A3,A4,A5,ram4,lsfw')
2013-02-23 15:43:42,296 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-23 15:43:42,296 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:43:42,296 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-02-23 15:43:42,296 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:43:42,296 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'acpi:PNP0000:')
2013-02-23 15:43:42,296 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'acpi:PNP0100:')
2013-02-23 15:43:42,296 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'pci:v00008086d00003422sv00000000sd00000000bc08sc00i00')
2013-02-23 15:43:42,299 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mce_xeon75xx'}
2013-02-23 15:43:42,299 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mce_xeon75xx', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:43:42,299 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'pci:v00008086d00002C10sv00001458sd00005000bc06sc00i00')
2013-02-23 15:43:42,301 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'input:b0003v05ACp0220e0111-e0,1,4,11,14,k71,72,73,74,75,77,78,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8C,8E,96,98,9E,9F,A1,A3,A4,A5,A6,AD,B0,B1,B2,B3,B4,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,CC,E0,E1,E3,E4,E5,E6,F0,1D0,ram4,l0,1,2,3,4,sfw')
2013-02-23 15:43:42,302 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-23 15:43:42,302 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:43:42,302 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-02-23 15:43:42,302 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:43:42,302 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'pci:v00008086d00002C28sv00001458sd00005000bc06sc00i00')
2013-02-23 15:43:42,304 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'pci:v00008086d00003A38sv00001458sd00005004bc0Csc03i00')
2013-02-23 15:43:42,307 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'pci:v00008086d00003A3Esv00001458sd0000A002bc04sc03i00')
2013-02-23 15:43:42,309 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-02-23 15:43:42,309 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:43:42,309 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-02-23 15:43:42,309 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:43:42,309 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'acpi:PNP0501:')
2013-02-23 15:43:42,310 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip02')
2013-02-23 15:43:42,310 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-02-23 15:43:42,310 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:43:42,310 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2013-02-23 15:43:42,310 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:43:42,310 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'pci:v00008086d00002C18sv00001458sd00005000bc06sc00i00')
2013-02-23 15:43:42,313 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'pci:v00008086d00002C21sv00001458sd00005000bc06sc00i00')
2013-02-23 15:43:42,316 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'pci:v00008086d00003A30sv00001458sd00005001bc0Csc05i00')
2013-02-23 15:43:42,318 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801'}
2013-02-23 15:43:42,318 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:43:42,319 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'usb:v1D6Bp0002d0305dc09dsc00dp00ic09isc00ip00')
2013-02-23 15:43:42,319 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'pci:v00008086d00003425sv00000000sd00000000bc08sc00i00')
2013-02-23 15:43:42,321 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2013-02-23 15:43:42,321 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-23 15:43:42,321 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:43:42,321 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1577ab8> about HardwareID('modalias', 'pci:v0000104Cd00008024sv00001458sd00001000bc0Csc00i10')
2013-02-23 15:43:42,331 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci'}
2013-02-23 15:43:42,331 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:43:42,331 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'acpi:PNP0C02:')
2013-02-23 15:43:42,331 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-02-23 15:43:42,331 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc00ip00')
2013-02-23 15:43:42,331 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'usb:v1D6Bp0001d0305dc09dsc00dp00ic09isc00ip00')
2013-02-23 15:43:42,331 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'pci:v00008086d00002822sv00001458sd0000B000bc01sc04i00')
2013-02-23 15:43:42,331 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'pci:v00008086d00002C2Asv00001458sd00005000bc06sc00i00')
2013-02-23 15:43:42,331 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'dmi:bvnAwardSoftwareInternational,Inc.:bvrF11:bd03/11/2010:svnGigabyteTechnologyCo.,Ltd.:pnEX58-UD3R:pvr:rvnGigabyteTechnologyCo.,Ltd.:rnEX58-UD3R:rvrx.x:cvnGigabyteTechnologyCo.,Ltd.:ct3:cvr:')
2013-02-23 15:43:42,332 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'usb:v05ACp0220d0069dc00dsc00dp00ic03isc01ip01')
2013-02-23 15:43:42,332 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'usb:v05ACp0220d0069dc00dsc00dp00ic03isc00ip00')
2013-02-23 15:43:42,332 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'pci:v00008086d0000342Fsv00000000sd00000000bc08sc00i20')
2013-02-23 15:43:42,332 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'acpi:PNP0200:')
2013-02-23 15:43:42,332 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'platform:regulatory')
2013-02-23 15:43:42,332 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2013-02-23 15:43:42,332 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'pci:v00008086d00003A37sv00001458sd00005004bc0Csc03i00')
2013-02-23 15:43:42,332 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'x86cpu:vendor:0000:family:0006:model:001A:feature:,0000,0001,0002,0003,0004,0005,0006,0007,0008,0009,000B,000C,000D,000E,000F,0010,0011,0013,0015,0016,0017,0018,0019,001A,001B,001C,001D,001F,002B,0034,003B,003D,0068,006B,006C,006D,006F,0070,0072,0074,0076,0078,007C,0080,0082,0083,0084,0085,0087,0088,0089,008D,008E,008F,0093,0094,0097,00C0,00E7,0100,0101,0102,0103,0104')
2013-02-23 15:43:42,332 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2013-02-23 15:43:42,332 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'acpi:PNP0103:')
2013-02-23 15:43:42,332 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'pci:v00008086d00002C11sv00001458sd00005000bc06sc00i00')
2013-02-23 15:43:42,332 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'acpi:PNP0700:')
2013-02-23 15:43:42,332 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'pci:v00008086d00003427sv00000000sd00000000bc08sc00i00')
2013-02-23 15:43:42,332 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'pci:v00008086d0000342Dsv00000000sd00000000bc08sc00i20')
2013-02-23 15:43:42,332 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'pci:v00008086d00002C23sv00001458sd00005000bc06sc00i00')
2013-02-23 15:43:42,332 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'platform:pcspkr')
2013-02-23 15:43:42,333 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'pci:v00008086d0000244Esv00001458sd00005000bc06sc04i01')
2013-02-23 15:43:42,333 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'pci:v00008086d00002C41sv00001458sd00005000bc06sc00i00')
2013-02-23 15:43:42,333 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'acpi:PNP0B00:')
2013-02-23 15:43:42,333 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'pci:v00008086d00002C20sv00001458sd00005000bc06sc00i00')
2013-02-23 15:43:42,333 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'pci:v00001002d0000AAB0sv00001787sd0000AAB0bc04sc03i00')
2013-02-23 15:43:42,333 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'pci:v00008086d00003A16sv00001458sd00005001bc06sc01i00')
2013-02-23 15:43:42,333 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'pci:v00001002d00006819sv00001787sd00002320bc03sc00i00')
2013-02-23 15:43:42,333 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'pci:v00008086d00003A3Csv00001458sd00005006bc0Csc03i20')
2013-02-23 15:43:42,333 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2013-02-23 15:43:42,333 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'pci:v00008086d00003A35sv00001458sd00005004bc0Csc03i00')
2013-02-23 15:43:42,333 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'pci:v00008086d00003A3Asv00001458sd00005006bc0Csc03i20')
2013-02-23 15:43:42,333 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'pci:v000014E4d00004329sv00001385sd00007D00bc02sc80i00')
2013-02-23 15:43:42,333 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'usb:v18E3p9101d0000dc00dsc00dp00ic08isc06ip50')
2013-02-23 15:43:42,333 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'acpi:INT0800:')
2013-02-23 15:43:42,333 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'pci:v00008086d00002C32sv00001458sd00005000bc06sc00i00')
2013-02-23 15:43:42,333 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'pci:v00008086d00003A36sv00001458sd00005004bc0Csc03i00')
2013-02-23 15:43:42,333 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'usb:v05ACp1006d9615dc09dsc00dp01ic09isc00ip00')
2013-02-23 15:43:42,334 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'pci:v00008086d00002C30sv00001458sd00005000bc06sc00i00')
2013-02-23 15:43:42,334 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'acpi:PNP0800:')
2013-02-23 15:43:42,334 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'pci:v00008086d00002C29sv00001458sd00005000bc06sc00i00')
2013-02-23 15:43:42,334 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'pci:v00008086d00003A39sv00001458sd00005004bc0Csc03i00')
2013-02-23 15:43:42,334 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'pci:v00008086d00002C22sv00001458sd00005000bc06sc00i00')
2013-02-23 15:43:42,334 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'pci:v00008086d00003423sv00000000sd00000000bc08sc00i00')
2013-02-23 15:43:42,334 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'pci:v00008086d0000342Esv00000000sd00000000bc08sc00i00')
2013-02-23 15:43:42,334 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-02-23 15:43:42,334 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'pci:v00008086d00003426sv00000000sd00000000bc08sc00i00')
2013-02-23 15:43:42,334 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'pci:v00008086d00002C19sv00001458sd00005000bc06sc00i00')
2013-02-23 15:43:42,334 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'platform:gpio_ich')
2013-02-23 15:43:42,334 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'pci:v00008086d00002C01sv00001458sd00005000bc06sc00i00')
2013-02-23 15:43:42,334 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2013-02-23 15:43:42,334 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'platform:microcode')
2013-02-23 15:43:42,334 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'wmi:F6CB5C3C-9CAE-4EBD-B577-931EA32A2CC0')
2013-02-23 15:43:42,334 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'pci:v00008086d00003405sv00001458sd00005000bc06sc00i00')
2013-02-23 15:43:42,335 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'pci:v00008086d00002C1Csv00001458sd00005000bc06sc00i00')
2013-02-23 15:43:42,335 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'pci:v00008086d00002C31sv00001458sd00005000bc06sc00i00')
2013-02-23 15:43:42,335 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'acpi:PNP0C04:')
2013-02-23 15:43:42,335 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'pci:v00008086d00002C33sv00001458sd00005000bc06sc00i00')
2013-02-23 15:43:42,335 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip01')
2013-02-23 15:43:42,335 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,2,4,k110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,r0,1,6,8,am4,lsfw')
2013-02-23 15:43:42,335 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'acpi:PNP0C01:')
2013-02-23 15:43:42,335 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2013-02-23 15:43:42,335 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'pci:v00008086d00003A34sv00001458sd00005004bc0Csc03i00')
2013-02-23 15:43:42,335 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001458sd0000E000bc02sc00i00')
2013-02-23 15:43:42,335 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2013-02-23 15:43:42,335 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'pci:v00008086d00003428sv00000000sd00000000bc08sc00i00')
2013-02-23 15:43:42,335 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'pci:v00008086d00002C2Bsv00001458sd00005000bc06sc00i00')
2013-02-23 15:43:42,335 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'platform:coretemp')
2013-02-23 15:43:42,335 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'hid:b0003g0000v0000046Dp0000C52B')
2013-02-23 15:43:42,335 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'hid:b0003g0000v000005ACp00000220')
2013-02-23 15:43:42,336 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-02-23 15:43:42,336 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'input:b0003v05ACp0220e0111-e0,1,4,k71,72,73,A1,A3,A4,A5,ram4,lsfw')
2013-02-23 15:43:42,336 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'acpi:PNP0000:')
2013-02-23 15:43:42,336 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'acpi:PNP0100:')
2013-02-23 15:43:42,336 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'pci:v00008086d00003422sv00000000sd00000000bc08sc00i00')
2013-02-23 15:43:42,336 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'pci:v00008086d00002C10sv00001458sd00005000bc06sc00i00')
2013-02-23 15:43:42,336 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'input:b0003v05ACp0220e0111-e0,1,4,11,14,k71,72,73,74,75,77,78,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8C,8E,96,98,9E,9F,A1,A3,A4,A5,A6,AD,B0,B1,B2,B3,B4,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,CC,E0,E1,E3,E4,E5,E6,F0,1D0,ram4,l0,1,2,3,4,sfw')
2013-02-23 15:43:42,336 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'pci:v00008086d00002C28sv00001458sd00005000bc06sc00i00')
2013-02-23 15:43:42,336 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'pci:v00008086d00003A38sv00001458sd00005004bc0Csc03i00')
2013-02-23 15:43:42,336 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'pci:v00008086d00003A3Esv00001458sd0000A002bc04sc03i00')
2013-02-23 15:43:42,336 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'acpi:PNP0501:')
2013-02-23 15:43:42,336 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip02')
2013-02-23 15:43:42,336 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'pci:v00008086d00002C18sv00001458sd00005000bc06sc00i00')
2013-02-23 15:43:42,336 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'pci:v00008086d00002C21sv00001458sd00005000bc06sc00i00')
2013-02-23 15:43:42,336 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'pci:v00008086d00003A30sv00001458sd00005001bc0Csc05i00')
2013-02-23 15:43:42,336 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'usb:v1D6Bp0002d0305dc09dsc00dp00ic09isc00ip00')
2013-02-23 15:43:42,337 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'pci:v00008086d00003425sv00000000sd00000000bc08sc00i00')
2013-02-23 15:43:42,337 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2013-02-23 15:43:42,337 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1979ef0> about HardwareID('modalias', 'pci:v0000104Cd00008024sv00001458sd00001000bc0Csc00i10')
2013-02-23 15:43:42,363 DEBUG: handler xorg:fglrx_updates previously unseen
2013-02-23 15:43:42,363 DEBUG: handler kmod:wl previously unseen
2013-02-23 15:43:42,485 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-02-23 15:43:42,485 DEBUG: handler kmod:wl previously unused
2013-02-23 15:43:42,485 DEBUG: handler xorg:fglrx_experimental_9 previously unseen
2013-02-23 15:43:42,485 DEBUG: writing back check cache /var/cache/jockey/check
2013-02-23 15:43:42,497 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-02-23 15:43:42,497 DEBUG: fglrx_updates is not the alternative in use
2013-02-23 15:43:42,561 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-02-23 15:43:42,561 DEBUG: kmod:wl is already enabled or not available, not announcing
2013-02-23 15:43:42,572 DEBUG: fglrx.enabled(fglrx_experimental_9): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-02-23 15:43:42,572 DEBUG: fglrx_experimental_9 is not the alternative in use
2013-02-23 15:43:42,593 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-02-23 15:43:42,593 DEBUG: fglrx_updates is not the alternative in use
2013-02-23 15:43:42,664 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-02-23 15:43:42,791 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-02-23 15:44:28,729 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-02-23 15:44:28,850 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-02-23 15:44:28,877 DEBUG: fglrx.enabled(fglrx_experimental_9): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-02-23 15:44:28,878 DEBUG: fglrx_experimental_9 is not the alternative in use
2013-02-23 15:44:28,904 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-02-23 15:44:28,904 DEBUG: fglrx_updates is not the alternative in use
2013-02-23 15:44:28,980 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-02-23 15:44:29,104 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-02-23 15:44:29,186 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-02-23 15:44:29,308 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-02-23 15:44:33,441 DEBUG: Shutting down
2013-02-23 15:49:46,704 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8>
2013-02-23 15:49:48,510 DEBUG: reading modalias file /lib/modules/3.5.0-25-generic/modules.alias
2013-02-23 15:49:48,595 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2013-02-23 15:49:48,595 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2013-02-23 15:49:48,638 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2013-02-23 15:49:48,661 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2013-02-23 15:49:48,661 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2013-02-23 15:49:48,661 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2013-02-23 15:49:48,667 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2013-02-23 15:49:48,671 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2013-02-23 15:49:48,815 DEBUG: XorgDriverHandler(omapdrm_pvr, pvr-omap4, None): Disabling as package is not compatible with Q-LTS X.org
2013-02-23 15:49:48,815 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2013-02-23 15:49:48,815 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2013-02-23 15:49:48,821 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2013-02-23 15:49:48,825 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2013-02-23 15:49:48,825 DEBUG: fglrx.available: falling back to default
2013-02-23 15:49:48,974 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2013-02-23 15:49:48,977 WARNING: modinfo for module fglrx_experimental_9 failed: ERROR: modinfo: could not find module fglrx_experimental_9

2013-02-23 15:49:48,996 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverExperimental9 from name FglrxDriverExperimental9
2013-02-23 15:49:48,996 DEBUG: fglrx.available: falling back to default
2013-02-23 15:49:49,120 DEBUG: ATI/AMD proprietary FGLRX graphics driver (**experimental** beta) availability undetermined, adding to pool
2013-02-23 15:49:49,123 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2013-02-23 15:49:49,127 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2013-02-23 15:49:49,127 DEBUG: fglrx.available: falling back to default
2013-02-23 15:49:49,257 DEBUG: XorgDriverHandler(fglrx, fglrx, None): Disabling as package is not compatible with Q-LTS X.org
2013-02-23 15:49:49,257 DEBUG: ATI/AMD proprietary FGLRX graphics driver not available
2013-02-23 15:49:49,257 DEBUG: loading custom handler /usr/share/jockey/handlers/cdv.py
2013-02-23 15:49:49,262 WARNING: modinfo for module cedarview_gfx failed: ERROR: modinfo: could not find module cedarview_gfx

2013-02-23 15:49:49,262 DEBUG: Instantiated Handler subclass __builtin__.CdvDriver from name CdvDriver
2013-02-23 15:49:49,262 DEBUG: cdv.available: falling back to default
2013-02-23 15:49:49,393 DEBUG: XorgDriverHandler(cedarview_gfx, cedarview-graphics-drivers, None): Disabling as package is not compatible with Q-LTS X.org
2013-02-23 15:49:49,393 DEBUG: Intel Cedarview graphics driver not available
2013-02-23 15:49:49,393 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2013-02-23 15:49:49,410 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2013-02-23 15:49:49,419 DEBUG: Software modem not available
2013-02-23 15:49:49,419 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2013-02-23 15:49:49,427 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2013-02-23 15:49:49,430 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2013-02-23 15:49:49,432 DEBUG: nvidia.available: falling back to default
2013-02-23 15:49:49,564 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package is not compatible with Q-LTS X.org
2013-02-23 15:49:49,565 DEBUG: NVIDIA accelerated graphics driver not available
2013-02-23 15:49:49,568 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2013-02-23 15:49:49,572 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2013-02-23 15:49:49,572 DEBUG: nvidia.available: falling back to default
2013-02-23 15:49:49,704 DEBUG: XorgDriverHandler(nvidia_current, nvidia-current, None): Disabling as package is not compatible with Q-LTS X.org
2013-02-23 15:49:49,704 DEBUG: NVIDIA accelerated graphics driver not available
2013-02-23 15:49:49,708 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2013-02-23 15:49:49,711 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2013-02-23 15:49:49,712 DEBUG: nvidia.available: falling back to default
2013-02-23 15:49:49,864 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2013-02-23 15:49:49,867 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2013-02-23 15:49:49,871 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2013-02-23 15:49:49,872 DEBUG: nvidia.available: falling back to default
2013-02-23 15:49:50,005 DEBUG: XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling as package is not compatible with Q-LTS X.org
2013-02-23 15:49:50,005 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2013-02-23 15:49:50,008 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2013-02-23 15:49:50,012 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2013-02-23 15:49:50,013 DEBUG: nvidia.available: falling back to default
2013-02-23 15:49:50,165 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2013-02-23 15:49:50,168 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2013-02-23 15:49:50,172 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2013-02-23 15:49:50,173 DEBUG: nvidia.available: falling back to default
2013-02-23 15:49:50,302 DEBUG: XorgDriverHandler(nvidia_173, nvidia-173, None): Disabling as package is not compatible with Q-LTS X.org
2013-02-23 15:49:50,302 DEBUG: NVIDIA accelerated graphics driver not available
2013-02-23 15:49:50,305 WARNING: modinfo for module nvidia_experimental_310 failed: ERROR: modinfo: could not find module nvidia_experimental_310

2013-02-23 15:49:50,324 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverExperimental310 from name NvidiaDriverExperimental310
2013-02-23 15:49:50,325 DEBUG: nvidia.available: falling back to default
2013-02-23 15:49:50,453 DEBUG: NVIDIA accelerated graphics driver (**experimental** beta) availability undetermined, adding to pool
2013-02-23 15:49:50,456 WARNING: modinfo for module nvidia_experimental_304 failed: ERROR: modinfo: could not find module nvidia_experimental_304

2013-02-23 15:49:50,474 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverExperimental304 from name NvidiaDriverExperimental304
2013-02-23 15:49:50,475 DEBUG: nvidia.available: falling back to default
2013-02-23 15:49:50,599 DEBUG: XorgDriverHandler(nvidia_experimental_304, nvidia-experimental-304, None): Disabling as package is not compatible with Q-LTS X.org
2013-02-23 15:49:50,599 DEBUG: NVIDIA accelerated graphics driver (**experimental** beta) not available
2013-02-23 15:49:50,599 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2013-02-23 15:49:50,603 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2013-02-23 15:49:50,603 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2013-02-23 15:49:50,618 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2013-02-23 15:49:50,619 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2013-02-23 15:49:50,641 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2013-02-23 15:49:50,642 DEBUG: Firmware for DVB cards not available
2013-02-23 15:49:50,642 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2013-02-23 15:49:50,646 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2013-02-23 15:49:50,647 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2013-02-23 15:49:50,647 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2013-02-23 15:49:50,647 DEBUG: all custom handlers loaded
2013-02-23 15:49:50,647 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'acpi:PNP0B00:')
2013-02-23 15:49:50,647 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-02-23 15:49:50,648 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc00ip00')
2013-02-23 15:49:50,686 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-02-23 15:49:50,744 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:49:50,744 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'usb:v1D6Bp0001d0305dc09dsc00dp00ic09isc00ip00')
2013-02-23 15:49:50,745 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'pci:v00008086d00002822sv00001458sd0000B000bc01sc04i00')
2013-02-23 15:49:50,983 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'pci:v00008086d00002C2Asv00001458sd00005000bc06sc00i00')
2013-02-23 15:49:50,985 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'acpi:INT0800:')
2013-02-23 15:49:50,986 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'dmi:bvnAwardSoftwareInternational,Inc.:bvrF11:bd03/11/2010:svnGigabyteTechnologyCo.,Ltd.:pnEX58-UD3R:pvr:rvnGigabyteTechnologyCo.,Ltd.:rnEX58-UD3R:rvrx.x:cvnGigabyteTechnologyCo.,Ltd.:ct3:cvr:')
2013-02-23 15:49:50,996 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'usb:v05ACp0220d0069dc00dsc00dp00ic03isc01ip01')
2013-02-23 15:49:51,015 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-02-23 15:49:51,015 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:49:51,016 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2013-02-23 15:49:51,016 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:49:51,016 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'usb:v05ACp0220d0069dc00dsc00dp00ic03isc00ip00')
2013-02-23 15:49:51,016 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-02-23 15:49:51,016 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:49:51,016 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'pci:v00008086d0000342Fsv00000000sd00000000bc08sc00i20')
2013-02-23 15:49:51,019 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'acpi:PNP0103:')
2013-02-23 15:49:51,019 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'platform:regulatory')
2013-02-23 15:49:51,019 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2013-02-23 15:49:51,023 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-23 15:49:51,023 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:49:51,023 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'pci:v00008086d00003A37sv00001458sd00005004bc0Csc03i00')
2013-02-23 15:49:51,025 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'x86cpu:vendor:0000:family:0006:model:001A:feature:,0000,0001,0002,0003,0004,0005,0006,0007,0008,0009,000B,000C,000D,000E,000F,0010,0011,0013,0015,0016,0017,0018,0019,001A,001B,001C,001D,001F,002B,0034,003B,003D,0068,006B,006C,006D,006F,0070,0072,0074,0076,0078,007C,0080,0082,0083,0084,0085,0087,0088,0089,008D,008E,008F,0093,0094,0097,00C0,00E7,0100,0101,0102,0103,0104')
2013-02-23 15:49:51,029 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'kvm_intel'}
2013-02-23 15:49:51,029 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'kvm_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:49:51,029 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'microcode'}
2013-02-23 15:49:51,029 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'microcode', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:49:51,029 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'coretemp'}
2013-02-23 15:49:51,029 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'coretemp', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:49:51,030 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2013-02-23 15:49:51,036 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2013-02-23 15:49:51,036 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:49:51,036 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'acpi:PNP0100:')
2013-02-23 15:49:51,036 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'pci:v00008086d00002C11sv00001458sd00005000bc06sc00i00')
2013-02-23 15:49:51,039 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'acpi:PNP0501:')
2013-02-23 15:49:51,039 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'pci:v00008086d00003427sv00000000sd00000000bc08sc00i00')
2013-02-23 15:49:51,041 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'pci:v00008086d0000342Dsv00000000sd00000000bc08sc00i20')
2013-02-23 15:49:51,044 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'pci:v00008086d00002C23sv00001458sd00005000bc06sc00i00')
2013-02-23 15:49:51,046 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'platform:pcspkr')
2013-02-23 15:49:51,046 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2013-02-23 15:49:51,046 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:49:51,047 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2013-02-23 15:49:51,047 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:49:51,047 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'pci:v00008086d0000244Esv00001458sd00005000bc06sc04i01')
2013-02-23 15:49:51,049 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'pci:v00008086d00002C41sv00001458sd00005000bc06sc00i00')
2013-02-23 15:49:51,052 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'acpi:PNP0800:')
2013-02-23 15:49:51,052 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'pci:v00008086d00002C20sv00001458sd00005000bc06sc00i00')
2013-02-23 15:49:51,054 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'pci:v00001002d0000AAB0sv00001787sd0000AAB0bc04sc03i00')
2013-02-23 15:49:51,334 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-02-23 15:49:51,334 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:49:51,334 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-02-23 15:49:51,335 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:49:51,335 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'pci:v00008086d00003A16sv00001458sd00005001bc06sc01i00')
2013-02-23 15:49:51,337 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'lpc_ich'}
2013-02-23 15:49:51,337 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'lpc_ich', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:49:51,337 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'pci:v00001002d00006819sv00001787sd00002320bc03sc00i00')
2013-02-23 15:49:51,340 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2013-02-23 15:49:51,340 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:49:51,340 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_experimental_9', 'package': 'fglrx-experimental-9'}
2013-02-23 15:49:51,352 DEBUG: fglrx.enabled(fglrx_experimental_9): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-02-23 15:49:51,352 DEBUG: fglrx_experimental_9 is not the alternative in use
2013-02-23 15:49:51,341 DEBUG: found match in handler pool xorg:fglrx_experimental_9([FglrxDriverExperimental9, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (**experimental** beta))
2013-02-23 15:49:51,355 WARNING: modinfo for module fglrx_experimental_9 failed: ERROR: modinfo: could not find module fglrx_experimental_9

2013-02-23 15:49:51,359 DEBUG: fglrx.available: falling back to default
2013-02-23 15:49:51,500 DEBUG: fglrx.enabled(fglrx_experimental_9): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-02-23 15:49:51,500 DEBUG: fglrx_experimental_9 is not the alternative in use
2013-02-23 15:49:51,488 DEBUG: got handler xorg:fglrx_experimental_9([FglrxDriverExperimental9, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (**experimental** beta))
2013-02-23 15:49:51,500 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2013-02-23 15:49:51,512 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-02-23 15:49:51,512 DEBUG: fglrx_updates is not the alternative in use
2013-02-23 15:49:51,501 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2013-02-23 15:49:51,515 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2013-02-23 15:49:51,519 DEBUG: fglrx.available: falling back to default
2013-02-23 15:49:51,658 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-02-23 15:49:51,659 DEBUG: fglrx_updates is not the alternative in use
2013-02-23 15:49:51,648 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2013-02-23 15:49:51,659 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2013-02-23 15:49:51,670 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-02-23 15:49:51,670 DEBUG: fglrx is not the alternative in use
2013-02-23 15:49:51,659 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2013-02-23 15:49:51,674 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2013-02-23 15:49:51,678 DEBUG: fglrx.available: falling back to default
2013-02-23 15:49:51,812 DEBUG: XorgDriverHandler(fglrx, fglrx, None): Disabling as package is not compatible with Q-LTS X.org
2013-02-23 15:49:51,824 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-02-23 15:49:51,824 DEBUG: fglrx is not the alternative in use
2013-02-23 15:49:51,813 DEBUG: ignoring unavailable handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2013-02-23 15:49:51,824 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'pci:v00008086d00003A3Csv00001458sd00005006bc0Csc03i20')
2013-02-23 15:49:51,829 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2013-02-23 15:49:51,829 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2013-02-23 15:49:51,829 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:49:51,830 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2013-02-23 15:49:51,830 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:49:51,830 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'pci:v00008086d00003A35sv00001458sd00005004bc0Csc03i00')
2013-02-23 15:49:51,838 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'pci:v00008086d00003A3Asv00001458sd00005006bc0Csc03i20')
2013-02-23 15:49:51,842 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'pci:v000014E4d00004329sv00001385sd00007D00bc02sc80i00')
2013-02-23 15:49:51,876 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ssb'}
2013-02-23 15:49:51,876 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ssb', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:49:51,876 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'wl', 'package': 'bcmwl-kernel-source'}
2013-02-23 15:49:51,938 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-02-23 15:49:51,876 DEBUG: found match in handler pool kmod:wl([BroadcomWLHandler, nonfree, enabled] Broadcom STA wireless driver)
2013-02-23 15:49:52,003 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-02-23 15:49:51,939 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, enabled] Broadcom STA wireless driver)
2013-02-23 15:49:52,003 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'wl'}
2013-02-23 15:49:52,063 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-02-23 15:49:52,003 DEBUG: found match in handler pool kmod:wl([BroadcomWLHandler, nonfree, enabled] Broadcom STA wireless driver)
2013-02-23 15:49:52,124 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-02-23 15:49:52,063 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, enabled] Broadcom STA wireless driver)
2013-02-23 15:49:52,124 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'usb:v18E3p9101d0000dc00dsc00dp00ic08isc06ip50')
2013-02-23 15:49:52,124 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'acpi:PNP0C01:')
2013-02-23 15:49:52,124 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'pci:v00008086d00002C32sv00001458sd00005000bc06sc00i00')
2013-02-23 15:49:52,127 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'pci:v00008086d00003A36sv00001458sd00005004bc0Csc03i00')
2013-02-23 15:49:52,131 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'usb:v05ACp1006d9615dc09dsc00dp01ic09isc00ip00')
2013-02-23 15:49:52,132 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'pci:v00008086d00002C30sv00001458sd00005000bc06sc00i00')
2013-02-23 15:49:52,134 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'acpi:PNP0700:')
2013-02-23 15:49:52,134 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'pci:v00008086d00002C29sv00001458sd00005000bc06sc00i00')
2013-02-23 15:49:52,137 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'pci:v00008086d00003A39sv00001458sd00005004bc0Csc03i00')
2013-02-23 15:49:52,139 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'pci:v00008086d00002C22sv00001458sd00005000bc06sc00i00')
2013-02-23 15:49:52,141 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'pci:v00008086d00003423sv00000000sd00000000bc08sc00i00')
2013-02-23 15:49:52,144 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'pci:v00008086d0000342Esv00000000sd00000000bc08sc00i00')
2013-02-23 15:49:52,146 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i7core_edac'}
2013-02-23 15:49:52,146 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i7core_edac', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:49:52,147 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-02-23 15:49:52,147 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-23 15:49:52,147 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:49:52,147 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-02-23 15:49:52,147 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:49:52,147 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'pci:v00008086d00003426sv00000000sd00000000bc08sc00i00')
2013-02-23 15:49:52,149 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'pci:v00008086d00002C19sv00001458sd00005000bc06sc00i00')
2013-02-23 15:49:52,152 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'platform:gpio_ich')
2013-02-23 15:49:52,152 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'gpio_ich'}
2013-02-23 15:49:52,152 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'gpio_ich', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:49:52,153 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'pci:v00008086d00002C01sv00001458sd00005000bc06sc00i00')
2013-02-23 15:49:52,155 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2013-02-23 15:49:52,155 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-23 15:49:52,155 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:49:52,155 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'platform:microcode')
2013-02-23 15:49:52,156 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'wmi:F6CB5C3C-9CAE-4EBD-B577-931EA32A2CC0')
2013-02-23 15:49:52,156 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mxm_wmi'}
2013-02-23 15:49:52,156 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mxm_wmi', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:49:52,156 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'pci:v00008086d00003405sv00001458sd00005000bc06sc00i00')
2013-02-23 15:49:52,158 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'pci:v00008086d00002C1Csv00001458sd00005000bc06sc00i00')
2013-02-23 15:49:52,161 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'pci:v00008086d00002C31sv00001458sd00005000bc06sc00i00')
2013-02-23 15:49:52,163 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'acpi:PNP0C02:')
2013-02-23 15:49:52,163 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'pci:v00008086d00002C33sv00001458sd00005000bc06sc00i00')
2013-02-23 15:49:52,166 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip01')
2013-02-23 15:49:52,166 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-02-23 15:49:52,166 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:49:52,166 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2013-02-23 15:49:52,166 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:49:52,167 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,2,4,k110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,r0,1,6,8,am4,lsfw')
2013-02-23 15:49:52,167 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-23 15:49:52,167 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:49:52,167 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-02-23 15:49:52,167 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:49:52,167 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'acpi:PNP0200:')
2013-02-23 15:49:52,167 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2013-02-23 15:49:52,167 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-23 15:49:52,167 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:49:52,167 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'pci:v00008086d00003A34sv00001458sd00005004bc0Csc03i00')
2013-02-23 15:49:52,170 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001458sd0000E000bc02sc00i00')
2013-02-23 15:49:52,177 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2013-02-23 15:49:52,177 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:49:52,177 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2013-02-23 15:49:52,178 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-23 15:49:52,178 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:49:52,178 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'pci:v00008086d00003428sv00000000sd00000000bc08sc00i00')
2013-02-23 15:49:52,180 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'pci:v00008086d00002C2Bsv00001458sd00005000bc06sc00i00')
2013-02-23 15:49:52,183 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'platform:coretemp')
2013-02-23 15:49:52,183 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'hid:b0003g0000v0000046Dp0000C52B')
2013-02-23 15:49:52,219 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'hid_logitech_dj'}
2013-02-23 15:49:52,219 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'hid_logitech_dj', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:49:52,219 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'hid:b0003g0000v000005ACp00000220')
2013-02-23 15:49:52,220 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'hid_apple'}
2013-02-23 15:49:52,220 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'hid_apple', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:49:52,220 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-02-23 15:49:52,220 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'input:b0003v05ACp0220e0111-e0,1,4,k71,72,73,A1,A3,A4,A5,ram4,lsfw')
2013-02-23 15:49:52,220 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-23 15:49:52,220 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:49:52,220 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-02-23 15:49:52,220 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:49:52,220 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'acpi:PNP0C04:')
2013-02-23 15:49:52,220 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'acpi:PNP0000:')
2013-02-23 15:49:52,220 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'pci:v00008086d00003422sv00000000sd00000000bc08sc00i00')
2013-02-23 15:49:52,223 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mce_xeon75xx'}
2013-02-23 15:49:52,223 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mce_xeon75xx', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:49:52,223 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'pci:v00008086d00002C10sv00001458sd00005000bc06sc00i00')
2013-02-23 15:49:52,225 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'input:b0003v05ACp0220e0111-e0,1,4,11,14,k71,72,73,74,75,77,78,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8C,8E,96,98,9E,9F,A1,A3,A4,A5,A6,AD,B0,B1,B2,B3,B4,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,CC,E0,E1,E3,E4,E5,E6,F0,1D0,ram4,l0,1,2,3,4,sfw')
2013-02-23 15:49:52,226 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-23 15:49:52,226 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:49:52,226 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-02-23 15:49:52,226 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:49:52,226 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'pci:v00008086d00002C28sv00001458sd00005000bc06sc00i00')
2013-02-23 15:49:52,228 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'pci:v00008086d00003A38sv00001458sd00005004bc0Csc03i00')
2013-02-23 15:49:52,231 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'pci:v00008086d00003A3Esv00001458sd0000A002bc04sc03i00')
2013-02-23 15:49:52,233 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-02-23 15:49:52,233 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:49:52,233 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-02-23 15:49:52,233 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:49:52,234 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2013-02-23 15:49:52,234 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip02')
2013-02-23 15:49:52,234 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-02-23 15:49:52,234 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:49:52,234 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2013-02-23 15:49:52,234 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:49:52,234 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'pci:v00008086d00002C18sv00001458sd00005000bc06sc00i00')
2013-02-23 15:49:52,237 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'pci:v00008086d00002C21sv00001458sd00005000bc06sc00i00')
2013-02-23 15:49:52,239 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'pci:v00008086d00003A30sv00001458sd00005001bc0Csc05i00')
2013-02-23 15:49:52,242 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801'}
2013-02-23 15:49:52,242 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:49:52,242 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'usb:v1D6Bp0002d0305dc09dsc00dp00ic09isc00ip00')
2013-02-23 15:49:52,242 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'pci:v00008086d00003425sv00000000sd00000000bc08sc00i00')
2013-02-23 15:49:52,245 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2013-02-23 15:49:52,245 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-23 15:49:52,245 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:49:52,245 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x119eab8> about HardwareID('modalias', 'pci:v0000104Cd00008024sv00001458sd00001000bc0Csc00i10')
2013-02-23 15:49:52,254 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci'}
2013-02-23 15:49:52,254 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:49:52,254 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'acpi:PNP0B00:')
2013-02-23 15:49:52,254 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-02-23 15:49:52,254 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc00ip00')
2013-02-23 15:49:52,254 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'usb:v1D6Bp0001d0305dc09dsc00dp00ic09isc00ip00')
2013-02-23 15:49:52,254 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'pci:v00008086d00002822sv00001458sd0000B000bc01sc04i00')
2013-02-23 15:49:52,254 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'pci:v00008086d00002C2Asv00001458sd00005000bc06sc00i00')
2013-02-23 15:49:52,255 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'acpi:INT0800:')
2013-02-23 15:49:52,255 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'dmi:bvnAwardSoftwareInternational,Inc.:bvrF11:bd03/11/2010:svnGigabyteTechnologyCo.,Ltd.:pnEX58-UD3R:pvr:rvnGigabyteTechnologyCo.,Ltd.:rnEX58-UD3R:rvrx.x:cvnGigabyteTechnologyCo.,Ltd.:ct3:cvr:')
2013-02-23 15:49:52,255 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'usb:v05ACp0220d0069dc00dsc00dp00ic03isc01ip01')
2013-02-23 15:49:52,255 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'usb:v05ACp0220d0069dc00dsc00dp00ic03isc00ip00')
2013-02-23 15:49:52,255 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'pci:v00008086d0000342Fsv00000000sd00000000bc08sc00i20')
2013-02-23 15:49:52,255 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'acpi:PNP0103:')
2013-02-23 15:49:52,255 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'platform:regulatory')
2013-02-23 15:49:52,255 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2013-02-23 15:49:52,255 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'pci:v00008086d00003A37sv00001458sd00005004bc0Csc03i00')
2013-02-23 15:49:52,255 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'x86cpu:vendor:0000:family:0006:model:001A:feature:,0000,0001,0002,0003,0004,0005,0006,0007,0008,0009,000B,000C,000D,000E,000F,0010,0011,0013,0015,0016,0017,0018,0019,001A,001B,001C,001D,001F,002B,0034,003B,003D,0068,006B,006C,006D,006F,0070,0072,0074,0076,0078,007C,0080,0082,0083,0084,0085,0087,0088,0089,008D,008E,008F,0093,0094,0097,00C0,00E7,0100,0101,0102,0103,0104')
2013-02-23 15:49:52,255 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2013-02-23 15:49:52,255 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'acpi:PNP0100:')
2013-02-23 15:49:52,255 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'pci:v00008086d00002C11sv00001458sd00005000bc06sc00i00')
2013-02-23 15:49:52,255 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'acpi:PNP0501:')
2013-02-23 15:49:52,255 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'pci:v00008086d00003427sv00000000sd00000000bc08sc00i00')
2013-02-23 15:49:52,256 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'pci:v00008086d0000342Dsv00000000sd00000000bc08sc00i20')
2013-02-23 15:49:52,256 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'pci:v00008086d00002C23sv00001458sd00005000bc06sc00i00')
2013-02-23 15:49:52,256 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'platform:pcspkr')
2013-02-23 15:49:52,256 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'pci:v00008086d0000244Esv00001458sd00005000bc06sc04i01')
2013-02-23 15:49:52,256 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'pci:v00008086d00002C41sv00001458sd00005000bc06sc00i00')
2013-02-23 15:49:52,256 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'acpi:PNP0800:')
2013-02-23 15:49:52,256 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'pci:v00008086d00002C20sv00001458sd00005000bc06sc00i00')
2013-02-23 15:49:52,256 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'pci:v00001002d0000AAB0sv00001787sd0000AAB0bc04sc03i00')
2013-02-23 15:49:52,256 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'pci:v00008086d00003A16sv00001458sd00005001bc06sc01i00')
2013-02-23 15:49:52,256 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'pci:v00001002d00006819sv00001787sd00002320bc03sc00i00')
2013-02-23 15:49:52,256 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'pci:v00008086d00003A3Csv00001458sd00005006bc0Csc03i20')
2013-02-23 15:49:52,256 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2013-02-23 15:49:52,256 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'pci:v00008086d00003A35sv00001458sd00005004bc0Csc03i00')
2013-02-23 15:49:52,256 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'pci:v00008086d00003A3Asv00001458sd00005006bc0Csc03i20')
2013-02-23 15:49:52,256 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'pci:v000014E4d00004329sv00001385sd00007D00bc02sc80i00')
2013-02-23 15:49:52,256 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'usb:v18E3p9101d0000dc00dsc00dp00ic08isc06ip50')
2013-02-23 15:49:52,256 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'acpi:PNP0C01:')
2013-02-23 15:49:52,257 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'pci:v00008086d00002C32sv00001458sd00005000bc06sc00i00')
2013-02-23 15:49:52,257 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'pci:v00008086d00003A36sv00001458sd00005004bc0Csc03i00')
2013-02-23 15:49:52,257 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'usb:v05ACp1006d9615dc09dsc00dp01ic09isc00ip00')
2013-02-23 15:49:52,257 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'pci:v00008086d00002C30sv00001458sd00005000bc06sc00i00')
2013-02-23 15:49:52,257 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'acpi:PNP0700:')
2013-02-23 15:49:52,257 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'pci:v00008086d00002C29sv00001458sd00005000bc06sc00i00')
2013-02-23 15:49:52,257 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'pci:v00008086d00003A39sv00001458sd00005004bc0Csc03i00')
2013-02-23 15:49:52,257 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'pci:v00008086d00002C22sv00001458sd00005000bc06sc00i00')
2013-02-23 15:49:52,257 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'pci:v00008086d00003423sv00000000sd00000000bc08sc00i00')
2013-02-23 15:49:52,257 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'pci:v00008086d0000342Esv00000000sd00000000bc08sc00i00')
2013-02-23 15:49:52,257 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-02-23 15:49:52,257 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'pci:v00008086d00003426sv00000000sd00000000bc08sc00i00')
2013-02-23 15:49:52,257 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'pci:v00008086d00002C19sv00001458sd00005000bc06sc00i00')
2013-02-23 15:49:52,257 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'platform:gpio_ich')
2013-02-23 15:49:52,257 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'pci:v00008086d00002C01sv00001458sd00005000bc06sc00i00')
2013-02-23 15:49:52,257 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2013-02-23 15:49:52,257 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'platform:microcode')
2013-02-23 15:49:52,258 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'wmi:F6CB5C3C-9CAE-4EBD-B577-931EA32A2CC0')
2013-02-23 15:49:52,258 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'pci:v00008086d00003405sv00001458sd00005000bc06sc00i00')
2013-02-23 15:49:52,258 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'pci:v00008086d00002C1Csv00001458sd00005000bc06sc00i00')
2013-02-23 15:49:52,258 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'pci:v00008086d00002C31sv00001458sd00005000bc06sc00i00')
2013-02-23 15:49:52,258 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'acpi:PNP0C02:')
2013-02-23 15:49:52,258 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'pci:v00008086d00002C33sv00001458sd00005000bc06sc00i00')
2013-02-23 15:49:52,258 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip01')
2013-02-23 15:49:52,258 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,2,4,k110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,r0,1,6,8,am4,lsfw')
2013-02-23 15:49:52,258 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'acpi:PNP0200:')
2013-02-23 15:49:52,258 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2013-02-23 15:49:52,258 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'pci:v00008086d00003A34sv00001458sd00005004bc0Csc03i00')
2013-02-23 15:49:52,258 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001458sd0000E000bc02sc00i00')
2013-02-23 15:49:52,258 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2013-02-23 15:49:52,258 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'pci:v00008086d00003428sv00000000sd00000000bc08sc00i00')
2013-02-23 15:49:52,258 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'pci:v00008086d00002C2Bsv00001458sd00005000bc06sc00i00')
2013-02-23 15:49:52,258 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'platform:coretemp')
2013-02-23 15:49:52,259 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'hid:b0003g0000v0000046Dp0000C52B')
2013-02-23 15:49:52,259 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'hid:b0003g0000v000005ACp00000220')
2013-02-23 15:49:52,259 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-02-23 15:49:52,259 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'input:b0003v05ACp0220e0111-e0,1,4,k71,72,73,A1,A3,A4,A5,ram4,lsfw')
2013-02-23 15:49:52,259 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'acpi:PNP0C04:')
2013-02-23 15:49:52,259 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'acpi:PNP0000:')
2013-02-23 15:49:52,259 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'pci:v00008086d00003422sv00000000sd00000000bc08sc00i00')
2013-02-23 15:49:52,259 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'pci:v00008086d00002C10sv00001458sd00005000bc06sc00i00')
2013-02-23 15:49:52,259 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'input:b0003v05ACp0220e0111-e0,1,4,11,14,k71,72,73,74,75,77,78,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8C,8E,96,98,9E,9F,A1,A3,A4,A5,A6,AD,B0,B1,B2,B3,B4,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,CC,E0,E1,E3,E4,E5,E6,F0,1D0,ram4,l0,1,2,3,4,sfw')
2013-02-23 15:49:52,259 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'pci:v00008086d00002C28sv00001458sd00005000bc06sc00i00')
2013-02-23 15:49:52,259 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'pci:v00008086d00003A38sv00001458sd00005004bc0Csc03i00')
2013-02-23 15:49:52,259 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'pci:v00008086d00003A3Esv00001458sd0000A002bc04sc03i00')
2013-02-23 15:49:52,259 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2013-02-23 15:49:52,259 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip02')
2013-02-23 15:49:52,259 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'pci:v00008086d00002C18sv00001458sd00005000bc06sc00i00')
2013-02-23 15:49:52,259 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'pci:v00008086d00002C21sv00001458sd00005000bc06sc00i00')
2013-02-23 15:49:52,260 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'pci:v00008086d00003A30sv00001458sd00005001bc0Csc05i00')
2013-02-23 15:49:52,260 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'usb:v1D6Bp0002d0305dc09dsc00dp00ic09isc00ip00')
2013-02-23 15:49:52,260 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'pci:v00008086d00003425sv00000000sd00000000bc08sc00i00')
2013-02-23 15:49:52,260 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2013-02-23 15:49:52,260 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x15a2440> about HardwareID('modalias', 'pci:v0000104Cd00008024sv00001458sd00001000bc0Csc00i10')
2013-02-23 15:49:52,370 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-02-23 15:49:52,495 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-02-23 15:49:52,520 DEBUG: fglrx.enabled(fglrx_experimental_9): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-02-23 15:49:52,520 DEBUG: fglrx_experimental_9 is not the alternative in use
2013-02-23 15:49:52,546 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-02-23 15:49:52,546 DEBUG: fglrx_updates is not the alternative in use
2013-02-23 15:49:52,622 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-02-23 15:49:52,748 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-02-23 15:49:52,834 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-02-23 15:49:52,952 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-02-23 15:50:00,859 DEBUG: Shutting down
2013-02-23 15:58:38,195 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8>
2013-02-23 15:58:39,977 DEBUG: reading modalias file /lib/modules/3.5.0-25-generic/modules.alias
2013-02-23 15:58:40,059 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2013-02-23 15:58:40,060 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2013-02-23 15:58:40,101 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2013-02-23 15:58:40,115 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2013-02-23 15:58:40,115 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2013-02-23 15:58:40,115 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2013-02-23 15:58:40,118 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2013-02-23 15:58:40,121 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2013-02-23 15:58:40,229 DEBUG: XorgDriverHandler(omapdrm_pvr, pvr-omap4, None): Disabling as package is not compatible with Q-LTS X.org
2013-02-23 15:58:40,229 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2013-02-23 15:58:40,229 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2013-02-23 15:58:40,233 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2013-02-23 15:58:40,236 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2013-02-23 15:58:40,236 DEBUG: fglrx.available: falling back to default
2013-02-23 15:58:40,361 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2013-02-23 15:58:40,363 WARNING: modinfo for module fglrx_experimental_9 failed: ERROR: modinfo: could not find module fglrx_experimental_9

2013-02-23 15:58:40,376 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverExperimental9 from name FglrxDriverExperimental9
2013-02-23 15:58:40,376 DEBUG: fglrx.available: falling back to default
2013-02-23 15:58:40,487 DEBUG: ATI/AMD proprietary FGLRX graphics driver (**experimental** beta) availability undetermined, adding to pool
2013-02-23 15:58:40,490 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2013-02-23 15:58:40,492 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2013-02-23 15:58:40,492 DEBUG: fglrx.available: falling back to default
2013-02-23 15:58:40,602 DEBUG: XorgDriverHandler(fglrx, fglrx, None): Disabling as package is not compatible with Q-LTS X.org
2013-02-23 15:58:40,602 DEBUG: ATI/AMD proprietary FGLRX graphics driver not available
2013-02-23 15:58:40,602 DEBUG: loading custom handler /usr/share/jockey/handlers/cdv.py
2013-02-23 15:58:40,605 WARNING: modinfo for module cedarview_gfx failed: ERROR: modinfo: could not find module cedarview_gfx

2013-02-23 15:58:40,605 DEBUG: Instantiated Handler subclass __builtin__.CdvDriver from name CdvDriver
2013-02-23 15:58:40,605 DEBUG: cdv.available: falling back to default
2013-02-23 15:58:40,718 DEBUG: XorgDriverHandler(cedarview_gfx, cedarview-graphics-drivers, None): Disabling as package is not compatible with Q-LTS X.org
2013-02-23 15:58:40,718 DEBUG: Intel Cedarview graphics driver not available
2013-02-23 15:58:40,719 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2013-02-23 15:58:40,736 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2013-02-23 15:58:40,744 DEBUG: Software modem not available
2013-02-23 15:58:40,744 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2013-02-23 15:58:40,749 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2013-02-23 15:58:40,752 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2013-02-23 15:58:40,752 DEBUG: nvidia.available: falling back to default
2013-02-23 15:58:40,877 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package is not compatible with Q-LTS X.org
2013-02-23 15:58:40,877 DEBUG: NVIDIA accelerated graphics driver not available
2013-02-23 15:58:40,880 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2013-02-23 15:58:40,882 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2013-02-23 15:58:40,883 DEBUG: nvidia.available: falling back to default
2013-02-23 15:58:40,997 DEBUG: XorgDriverHandler(nvidia_current, nvidia-current, None): Disabling as package is not compatible with Q-LTS X.org
2013-02-23 15:58:40,997 DEBUG: NVIDIA accelerated graphics driver not available
2013-02-23 15:58:41,000 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2013-02-23 15:58:41,002 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2013-02-23 15:58:41,003 DEBUG: nvidia.available: falling back to default
2013-02-23 15:58:41,130 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2013-02-23 15:58:41,132 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2013-02-23 15:58:41,134 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2013-02-23 15:58:41,135 DEBUG: nvidia.available: falling back to default
2013-02-23 15:58:41,251 DEBUG: XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling as package is not compatible with Q-LTS X.org
2013-02-23 15:58:41,251 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2013-02-23 15:58:41,254 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2013-02-23 15:58:41,256 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2013-02-23 15:58:41,257 DEBUG: nvidia.available: falling back to default
2013-02-23 15:58:41,380 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2013-02-23 15:58:41,382 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2013-02-23 15:58:41,384 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2013-02-23 15:58:41,385 DEBUG: nvidia.available: falling back to default
2013-02-23 15:58:41,497 DEBUG: XorgDriverHandler(nvidia_173, nvidia-173, None): Disabling as package is not compatible with Q-LTS X.org
2013-02-23 15:58:41,497 DEBUG: NVIDIA accelerated graphics driver not available
2013-02-23 15:58:41,499 WARNING: modinfo for module nvidia_experimental_310 failed: ERROR: modinfo: could not find module nvidia_experimental_310

2013-02-23 15:58:41,511 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverExperimental310 from name NvidiaDriverExperimental310
2013-02-23 15:58:41,512 DEBUG: nvidia.available: falling back to default
2013-02-23 15:58:41,627 DEBUG: NVIDIA accelerated graphics driver (**experimental** beta) availability undetermined, adding to pool
2013-02-23 15:58:41,631 WARNING: modinfo for module nvidia_experimental_304 failed: ERROR: modinfo: could not find module nvidia_experimental_304

2013-02-23 15:58:41,649 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverExperimental304 from name NvidiaDriverExperimental304
2013-02-23 15:58:41,650 DEBUG: nvidia.available: falling back to default
2013-02-23 15:58:41,777 DEBUG: XorgDriverHandler(nvidia_experimental_304, nvidia-experimental-304, None): Disabling as package is not compatible with Q-LTS X.org
2013-02-23 15:58:41,778 DEBUG: NVIDIA accelerated graphics driver (**experimental** beta) not available
2013-02-23 15:58:41,778 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2013-02-23 15:58:41,781 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2013-02-23 15:58:41,782 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2013-02-23 15:58:41,797 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2013-02-23 15:58:41,797 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2013-02-23 15:58:41,817 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2013-02-23 15:58:41,817 DEBUG: Firmware for DVB cards not available
2013-02-23 15:58:41,817 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2013-02-23 15:58:41,821 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2013-02-23 15:58:41,822 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2013-02-23 15:58:41,822 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2013-02-23 15:58:41,822 DEBUG: all custom handlers loaded
2013-02-23 15:58:41,822 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'acpi:PNP0B00:')
2013-02-23 15:58:41,822 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-02-23 15:58:41,823 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc00ip00')
2013-02-23 15:58:41,859 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-02-23 15:58:41,913 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:58:41,913 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'usb:v1D6Bp0001d0305dc09dsc00dp00ic09isc00ip00')
2013-02-23 15:58:41,913 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'pci:v00008086d00002822sv00001458sd0000B000bc01sc04i00')
2013-02-23 15:58:42,153 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'pci:v00008086d00002C2Asv00001458sd00005000bc06sc00i00')
2013-02-23 15:58:42,156 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'acpi:INT0800:')
2013-02-23 15:58:42,156 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'dmi:bvnAwardSoftwareInternational,Inc.:bvrF11:bd03/11/2010:svnGigabyteTechnologyCo.,Ltd.:pnEX58-UD3R:pvr:rvnGigabyteTechnologyCo.,Ltd.:rnEX58-UD3R:rvrx.x:cvnGigabyteTechnologyCo.,Ltd.:ct3:cvr:')
2013-02-23 15:58:42,166 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'usb:v05ACp0220d0069dc00dsc00dp00ic03isc01ip01')
2013-02-23 15:58:42,186 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-02-23 15:58:42,186 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:58:42,186 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2013-02-23 15:58:42,186 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:58:42,186 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'usb:v05ACp0220d0069dc00dsc00dp00ic03isc00ip00')
2013-02-23 15:58:42,186 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-02-23 15:58:42,186 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:58:42,186 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'pci:v00008086d0000342Fsv00000000sd00000000bc08sc00i20')
2013-02-23 15:58:42,189 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'acpi:PNP0103:')
2013-02-23 15:58:42,189 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'platform:regulatory')
2013-02-23 15:58:42,190 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2013-02-23 15:58:42,193 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-23 15:58:42,193 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:58:42,193 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'pci:v00008086d00003A37sv00001458sd00005004bc0Csc03i00')
2013-02-23 15:58:42,196 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'x86cpu:vendor:0000:family:0006:model:001A:feature:,0000,0001,0002,0003,0004,0005,0006,0007,0008,0009,000B,000C,000D,000E,000F,0010,0011,0013,0015,0016,0017,0018,0019,001A,001B,001C,001D,001F,002B,0034,003B,003D,0068,006B,006C,006D,006F,0070,0072,0074,0076,0078,007C,0080,0082,0083,0084,0085,0087,0088,0089,008D,008E,008F,0093,0094,0097,00C0,00E7,0100,0101,0102,0103,0104')
2013-02-23 15:58:42,199 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'kvm_intel'}
2013-02-23 15:58:42,200 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'kvm_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:58:42,200 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'microcode'}
2013-02-23 15:58:42,200 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'microcode', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:58:42,200 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'coretemp'}
2013-02-23 15:58:42,200 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'coretemp', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:58:42,200 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2013-02-23 15:58:42,206 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2013-02-23 15:58:42,206 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:58:42,206 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'acpi:PNP0100:')
2013-02-23 15:58:42,207 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'pci:v00008086d00002C11sv00001458sd00005000bc06sc00i00')
2013-02-23 15:58:42,209 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'acpi:PNP0501:')
2013-02-23 15:58:42,209 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'pci:v00008086d00003427sv00000000sd00000000bc08sc00i00')
2013-02-23 15:58:42,212 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'pci:v00008086d0000342Dsv00000000sd00000000bc08sc00i20')
2013-02-23 15:58:42,214 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'pci:v00008086d00002C23sv00001458sd00005000bc06sc00i00')
2013-02-23 15:58:42,216 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'platform:pcspkr')
2013-02-23 15:58:42,217 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2013-02-23 15:58:42,217 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:58:42,217 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2013-02-23 15:58:42,217 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:58:42,217 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'pci:v00008086d0000244Esv00001458sd00005000bc06sc04i01')
2013-02-23 15:58:42,220 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'pci:v00008086d00002C41sv00001458sd00005000bc06sc00i00')
2013-02-23 15:58:42,222 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'acpi:PNP0800:')
2013-02-23 15:58:42,222 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'pci:v00008086d00002C20sv00001458sd00005000bc06sc00i00')
2013-02-23 15:58:42,225 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'pci:v00001002d0000AAB0sv00001787sd0000AAB0bc04sc03i00')
2013-02-23 15:58:42,504 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-02-23 15:58:42,505 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:58:42,505 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-02-23 15:58:42,505 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:58:42,505 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'pci:v00008086d00003A16sv00001458sd00005001bc06sc01i00')
2013-02-23 15:58:42,507 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'lpc_ich'}
2013-02-23 15:58:42,508 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'lpc_ich', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:58:42,508 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'pci:v00001002d00006819sv00001787sd00002320bc03sc00i00')
2013-02-23 15:58:42,511 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2013-02-23 15:58:42,511 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:58:42,511 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_experimental_9', 'package': 'fglrx-experimental-9'}
2013-02-23 15:58:42,522 DEBUG: fglrx.enabled(fglrx_experimental_9): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-02-23 15:58:42,522 DEBUG: fglrx_experimental_9 is not the alternative in use
2013-02-23 15:58:42,511 DEBUG: found match in handler pool xorg:fglrx_experimental_9([FglrxDriverExperimental9, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (**experimental** beta))
2013-02-23 15:58:42,526 WARNING: modinfo for module fglrx_experimental_9 failed: ERROR: modinfo: could not find module fglrx_experimental_9

2013-02-23 15:58:42,529 DEBUG: fglrx.available: falling back to default
2013-02-23 15:58:42,670 DEBUG: fglrx.enabled(fglrx_experimental_9): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-02-23 15:58:42,670 DEBUG: fglrx_experimental_9 is not the alternative in use
2013-02-23 15:58:42,659 DEBUG: got handler xorg:fglrx_experimental_9([FglrxDriverExperimental9, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (**experimental** beta))
2013-02-23 15:58:42,671 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2013-02-23 15:58:42,682 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-02-23 15:58:42,682 DEBUG: fglrx_updates is not the alternative in use
2013-02-23 15:58:42,671 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2013-02-23 15:58:42,686 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2013-02-23 15:58:42,689 DEBUG: fglrx.available: falling back to default
2013-02-23 15:58:42,826 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-02-23 15:58:42,826 DEBUG: fglrx_updates is not the alternative in use
2013-02-23 15:58:42,815 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2013-02-23 15:58:42,827 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2013-02-23 15:58:42,838 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-02-23 15:58:42,838 DEBUG: fglrx is not the alternative in use
2013-02-23 15:58:42,827 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2013-02-23 15:58:42,841 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2013-02-23 15:58:42,845 DEBUG: fglrx.available: falling back to default
2013-02-23 15:58:42,979 DEBUG: XorgDriverHandler(fglrx, fglrx, None): Disabling as package is not compatible with Q-LTS X.org
2013-02-23 15:58:42,991 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-02-23 15:58:42,991 DEBUG: fglrx is not the alternative in use
2013-02-23 15:58:42,980 DEBUG: ignoring unavailable handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2013-02-23 15:58:42,991 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'pci:v00008086d00003A3Csv00001458sd00005006bc0Csc03i20')
2013-02-23 15:58:42,996 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2013-02-23 15:58:42,996 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2013-02-23 15:58:42,996 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:58:42,996 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2013-02-23 15:58:42,996 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:58:42,997 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'pci:v00008086d00003A35sv00001458sd00005004bc0Csc03i00')
2013-02-23 15:58:43,000 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'pci:v00008086d00003A3Asv00001458sd00005006bc0Csc03i20')
2013-02-23 15:58:43,004 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'pci:v000014E4d00004329sv00001385sd00007D00bc02sc80i00')
2013-02-23 15:58:43,040 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ssb'}
2013-02-23 15:58:43,040 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ssb', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:58:43,040 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'wl', 'package': 'bcmwl-kernel-source'}
2013-02-23 15:58:43,100 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-02-23 15:58:43,040 DEBUG: found match in handler pool kmod:wl([BroadcomWLHandler, nonfree, enabled] Broadcom STA wireless driver)
2013-02-23 15:58:43,163 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-02-23 15:58:43,101 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, enabled] Broadcom STA wireless driver)
2013-02-23 15:58:43,163 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'wl'}
2013-02-23 15:58:43,229 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-02-23 15:58:43,163 DEBUG: found match in handler pool kmod:wl([BroadcomWLHandler, nonfree, enabled] Broadcom STA wireless driver)
2013-02-23 15:58:43,291 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-02-23 15:58:43,230 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, enabled] Broadcom STA wireless driver)
2013-02-23 15:58:43,292 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'usb:v18E3p9101d0000dc00dsc00dp00ic08isc06ip50')
2013-02-23 15:58:43,292 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'acpi:PNP0C01:')
2013-02-23 15:58:43,292 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'pci:v00008086d00002C32sv00001458sd00005000bc06sc00i00')
2013-02-23 15:58:43,297 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'pci:v00008086d00003A36sv00001458sd00005004bc0Csc03i00')
2013-02-23 15:58:43,300 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'usb:v05ACp1006d9615dc09dsc00dp01ic09isc00ip00')
2013-02-23 15:58:43,301 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'pci:v00008086d00002C30sv00001458sd00005000bc06sc00i00')
2013-02-23 15:58:43,303 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'acpi:PNP0700:')
2013-02-23 15:58:43,303 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'pci:v00008086d00002C29sv00001458sd00005000bc06sc00i00')
2013-02-23 15:58:43,306 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'pci:v00008086d00003A39sv00001458sd00005004bc0Csc03i00')
2013-02-23 15:58:43,308 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'pci:v00008086d00002C22sv00001458sd00005000bc06sc00i00')
2013-02-23 15:58:43,310 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'pci:v00008086d00003423sv00000000sd00000000bc08sc00i00')
2013-02-23 15:58:43,313 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'pci:v00008086d0000342Esv00000000sd00000000bc08sc00i00')
2013-02-23 15:58:43,315 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i7core_edac'}
2013-02-23 15:58:43,316 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i7core_edac', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:58:43,316 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-02-23 15:58:43,316 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-23 15:58:43,316 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:58:43,316 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-02-23 15:58:43,316 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:58:43,316 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'pci:v00008086d00003426sv00000000sd00000000bc08sc00i00')
2013-02-23 15:58:43,319 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'pci:v00008086d00002C19sv00001458sd00005000bc06sc00i00')
2013-02-23 15:58:43,321 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'platform:gpio_ich')
2013-02-23 15:58:43,321 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'gpio_ich'}
2013-02-23 15:58:43,322 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'gpio_ich', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:58:43,322 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'pci:v00008086d00002C01sv00001458sd00005000bc06sc00i00')
2013-02-23 15:58:43,324 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2013-02-23 15:58:43,324 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-23 15:58:43,324 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:58:43,324 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'platform:microcode')
2013-02-23 15:58:43,325 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'wmi:F6CB5C3C-9CAE-4EBD-B577-931EA32A2CC0')
2013-02-23 15:58:43,325 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mxm_wmi'}
2013-02-23 15:58:43,325 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mxm_wmi', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:58:43,325 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'pci:v00008086d00003405sv00001458sd00005000bc06sc00i00')
2013-02-23 15:58:43,327 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'pci:v00008086d00002C1Csv00001458sd00005000bc06sc00i00')
2013-02-23 15:58:43,330 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'pci:v00008086d00002C31sv00001458sd00005000bc06sc00i00')
2013-02-23 15:58:43,332 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'acpi:PNP0C02:')
2013-02-23 15:58:43,332 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'pci:v00008086d00002C33sv00001458sd00005000bc06sc00i00')
2013-02-23 15:58:43,335 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip01')
2013-02-23 15:58:43,335 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-02-23 15:58:43,335 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:58:43,335 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2013-02-23 15:58:43,336 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:58:43,336 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,2,4,k110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,r0,1,6,8,am4,lsfw')
2013-02-23 15:58:43,336 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-23 15:58:43,336 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:58:43,336 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-02-23 15:58:43,336 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:58:43,336 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'acpi:PNP0200:')
2013-02-23 15:58:43,336 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2013-02-23 15:58:43,336 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-23 15:58:43,336 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:58:43,336 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'pci:v00008086d00003A34sv00001458sd00005004bc0Csc03i00')
2013-02-23 15:58:43,339 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001458sd0000E000bc02sc00i00')
2013-02-23 15:58:43,346 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2013-02-23 15:58:43,346 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:58:43,346 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2013-02-23 15:58:43,346 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-23 15:58:43,347 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:58:43,347 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'pci:v00008086d00003428sv00000000sd00000000bc08sc00i00')
2013-02-23 15:58:43,349 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'pci:v00008086d00002C2Bsv00001458sd00005000bc06sc00i00')
2013-02-23 15:58:43,352 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'platform:coretemp')
2013-02-23 15:58:43,352 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'hid:b0003g0000v0000046Dp0000C52B')
2013-02-23 15:58:43,388 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'hid_logitech_dj'}
2013-02-23 15:58:43,388 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'hid_logitech_dj', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:58:43,388 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'hid:b0003g0000v000005ACp00000220')
2013-02-23 15:58:43,389 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'hid_apple'}
2013-02-23 15:58:43,389 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'hid_apple', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:58:43,389 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-02-23 15:58:43,389 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'input:b0003v05ACp0220e0111-e0,1,4,k71,72,73,A1,A3,A4,A5,ram4,lsfw')
2013-02-23 15:58:43,389 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-23 15:58:43,389 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:58:43,389 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-02-23 15:58:43,389 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:58:43,389 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'acpi:PNP0C04:')
2013-02-23 15:58:43,389 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'acpi:PNP0000:')
2013-02-23 15:58:43,389 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'pci:v00008086d00003422sv00000000sd00000000bc08sc00i00')
2013-02-23 15:58:43,392 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mce_xeon75xx'}
2013-02-23 15:58:43,392 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mce_xeon75xx', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:58:43,392 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'pci:v00008086d00002C10sv00001458sd00005000bc06sc00i00')
2013-02-23 15:58:43,395 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'input:b0003v05ACp0220e0111-e0,1,4,11,14,k71,72,73,74,75,77,78,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8C,8E,96,98,9E,9F,A1,A3,A4,A5,A6,AD,B0,B1,B2,B3,B4,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,CC,E0,E1,E3,E4,E5,E6,F0,1D0,ram4,l0,1,2,3,4,sfw')
2013-02-23 15:58:43,395 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-23 15:58:43,395 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:58:43,395 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-02-23 15:58:43,395 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:58:43,395 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'pci:v00008086d00002C28sv00001458sd00005000bc06sc00i00')
2013-02-23 15:58:43,397 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'pci:v00008086d00003A38sv00001458sd00005004bc0Csc03i00')
2013-02-23 15:58:43,400 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'pci:v00008086d00003A3Esv00001458sd0000A002bc04sc03i00')
2013-02-23 15:58:43,402 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-02-23 15:58:43,402 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:58:43,402 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-02-23 15:58:43,403 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:58:43,403 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2013-02-23 15:58:43,403 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip02')
2013-02-23 15:58:43,403 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-02-23 15:58:43,403 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:58:43,403 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2013-02-23 15:58:43,403 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:58:43,403 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'pci:v00008086d00002C18sv00001458sd00005000bc06sc00i00')
2013-02-23 15:58:43,406 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'pci:v00008086d00002C21sv00001458sd00005000bc06sc00i00')
2013-02-23 15:58:43,408 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'pci:v00008086d00003A30sv00001458sd00005001bc0Csc05i00')
2013-02-23 15:58:43,411 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801'}
2013-02-23 15:58:43,411 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:58:43,411 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'usb:v1D6Bp0002d0305dc09dsc00dp00ic09isc00ip00')
2013-02-23 15:58:43,411 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'pci:v00008086d00003425sv00000000sd00000000bc08sc00i00')
2013-02-23 15:58:43,414 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2013-02-23 15:58:43,414 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-23 15:58:43,414 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:58:43,414 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ddcab8> about HardwareID('modalias', 'pci:v0000104Cd00008024sv00001458sd00001000bc0Csc00i10')
2013-02-23 15:58:43,423 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci'}
2013-02-23 15:58:43,423 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 15:58:43,423 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'acpi:PNP0B00:')
2013-02-23 15:58:43,423 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-02-23 15:58:43,423 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc00ip00')
2013-02-23 15:58:43,424 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'usb:v1D6Bp0001d0305dc09dsc00dp00ic09isc00ip00')
2013-02-23 15:58:43,424 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'pci:v00008086d00002822sv00001458sd0000B000bc01sc04i00')
2013-02-23 15:58:43,424 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'pci:v00008086d00002C2Asv00001458sd00005000bc06sc00i00')
2013-02-23 15:58:43,424 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'acpi:INT0800:')
2013-02-23 15:58:43,424 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'dmi:bvnAwardSoftwareInternational,Inc.:bvrF11:bd03/11/2010:svnGigabyteTechnologyCo.,Ltd.:pnEX58-UD3R:pvr:rvnGigabyteTechnologyCo.,Ltd.:rnEX58-UD3R:rvrx.x:cvnGigabyteTechnologyCo.,Ltd.:ct3:cvr:')
2013-02-23 15:58:43,424 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'usb:v05ACp0220d0069dc00dsc00dp00ic03isc01ip01')
2013-02-23 15:58:43,424 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'usb:v05ACp0220d0069dc00dsc00dp00ic03isc00ip00')
2013-02-23 15:58:43,424 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'pci:v00008086d0000342Fsv00000000sd00000000bc08sc00i20')
2013-02-23 15:58:43,424 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'acpi:PNP0103:')
2013-02-23 15:58:43,424 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'platform:regulatory')
2013-02-23 15:58:43,424 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2013-02-23 15:58:43,424 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'pci:v00008086d00003A37sv00001458sd00005004bc0Csc03i00')
2013-02-23 15:58:43,424 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'x86cpu:vendor:0000:family:0006:model:001A:feature:,0000,0001,0002,0003,0004,0005,0006,0007,0008,0009,000B,000C,000D,000E,000F,0010,0011,0013,0015,0016,0017,0018,0019,001A,001B,001C,001D,001F,002B,0034,003B,003D,0068,006B,006C,006D,006F,0070,0072,0074,0076,0078,007C,0080,0082,0083,0084,0085,0087,0088,0089,008D,008E,008F,0093,0094,0097,00C0,00E7,0100,0101,0102,0103,0104')
2013-02-23 15:58:43,424 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2013-02-23 15:58:43,424 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'acpi:PNP0100:')
2013-02-23 15:58:43,424 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'pci:v00008086d00002C11sv00001458sd00005000bc06sc00i00')
2013-02-23 15:58:43,425 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'acpi:PNP0501:')
2013-02-23 15:58:43,425 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'pci:v00008086d00003427sv00000000sd00000000bc08sc00i00')
2013-02-23 15:58:43,425 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'pci:v00008086d0000342Dsv00000000sd00000000bc08sc00i20')
2013-02-23 15:58:43,425 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'pci:v00008086d00002C23sv00001458sd00005000bc06sc00i00')
2013-02-23 15:58:43,425 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'platform:pcspkr')
2013-02-23 15:58:43,425 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'pci:v00008086d0000244Esv00001458sd00005000bc06sc04i01')
2013-02-23 15:58:43,425 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'pci:v00008086d00002C41sv00001458sd00005000bc06sc00i00')
2013-02-23 15:58:43,425 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'acpi:PNP0800:')
2013-02-23 15:58:43,425 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'pci:v00008086d00002C20sv00001458sd00005000bc06sc00i00')
2013-02-23 15:58:43,425 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'pci:v00001002d0000AAB0sv00001787sd0000AAB0bc04sc03i00')
2013-02-23 15:58:43,425 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'pci:v00008086d00003A16sv00001458sd00005001bc06sc01i00')
2013-02-23 15:58:43,425 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'pci:v00001002d00006819sv00001787sd00002320bc03sc00i00')
2013-02-23 15:58:43,425 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'pci:v00008086d00003A3Csv00001458sd00005006bc0Csc03i20')
2013-02-23 15:58:43,425 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2013-02-23 15:58:43,425 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'pci:v00008086d00003A35sv00001458sd00005004bc0Csc03i00')
2013-02-23 15:58:43,425 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'pci:v00008086d00003A3Asv00001458sd00005006bc0Csc03i20')
2013-02-23 15:58:43,426 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'pci:v000014E4d00004329sv00001385sd00007D00bc02sc80i00')
2013-02-23 15:58:43,426 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'usb:v18E3p9101d0000dc00dsc00dp00ic08isc06ip50')
2013-02-23 15:58:43,426 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'acpi:PNP0C01:')
2013-02-23 15:58:43,426 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'pci:v00008086d00002C32sv00001458sd00005000bc06sc00i00')
2013-02-23 15:58:43,426 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'pci:v00008086d00003A36sv00001458sd00005004bc0Csc03i00')
2013-02-23 15:58:43,426 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'usb:v05ACp1006d9615dc09dsc00dp01ic09isc00ip00')
2013-02-23 15:58:43,426 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'pci:v00008086d00002C30sv00001458sd00005000bc06sc00i00')
2013-02-23 15:58:43,426 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'acpi:PNP0700:')
2013-02-23 15:58:43,426 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'pci:v00008086d00002C29sv00001458sd00005000bc06sc00i00')
2013-02-23 15:58:43,426 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'pci:v00008086d00003A39sv00001458sd00005004bc0Csc03i00')
2013-02-23 15:58:43,426 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'pci:v00008086d00002C22sv00001458sd00005000bc06sc00i00')
2013-02-23 15:58:43,426 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'pci:v00008086d00003423sv00000000sd00000000bc08sc00i00')
2013-02-23 15:58:43,426 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'pci:v00008086d0000342Esv00000000sd00000000bc08sc00i00')
2013-02-23 15:58:43,426 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-02-23 15:58:43,426 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'pci:v00008086d00003426sv00000000sd00000000bc08sc00i00')
2013-02-23 15:58:43,426 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'pci:v00008086d00002C19sv00001458sd00005000bc06sc00i00')
2013-02-23 15:58:43,426 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'platform:gpio_ich')
2013-02-23 15:58:43,427 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'pci:v00008086d00002C01sv00001458sd00005000bc06sc00i00')
2013-02-23 15:58:43,427 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2013-02-23 15:58:43,427 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'platform:microcode')
2013-02-23 15:58:43,427 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'wmi:F6CB5C3C-9CAE-4EBD-B577-931EA32A2CC0')
2013-02-23 15:58:43,427 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'pci:v00008086d00003405sv00001458sd00005000bc06sc00i00')
2013-02-23 15:58:43,427 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'pci:v00008086d00002C1Csv00001458sd00005000bc06sc00i00')
2013-02-23 15:58:43,427 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'pci:v00008086d00002C31sv00001458sd00005000bc06sc00i00')
2013-02-23 15:58:43,427 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'acpi:PNP0C02:')
2013-02-23 15:58:43,427 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'pci:v00008086d00002C33sv00001458sd00005000bc06sc00i00')
2013-02-23 15:58:43,427 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip01')
2013-02-23 15:58:43,427 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,2,4,k110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,r0,1,6,8,am4,lsfw')
2013-02-23 15:58:43,427 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'acpi:PNP0200:')
2013-02-23 15:58:43,427 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2013-02-23 15:58:43,427 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'pci:v00008086d00003A34sv00001458sd00005004bc0Csc03i00')
2013-02-23 15:58:43,427 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001458sd0000E000bc02sc00i00')
2013-02-23 15:58:43,427 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2013-02-23 15:58:43,428 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'pci:v00008086d00003428sv00000000sd00000000bc08sc00i00')
2013-02-23 15:58:43,428 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'pci:v00008086d00002C2Bsv00001458sd00005000bc06sc00i00')
2013-02-23 15:58:43,428 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'platform:coretemp')
2013-02-23 15:58:43,428 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'hid:b0003g0000v0000046Dp0000C52B')
2013-02-23 15:58:43,428 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'hid:b0003g0000v000005ACp00000220')
2013-02-23 15:58:43,428 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-02-23 15:58:43,428 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'input:b0003v05ACp0220e0111-e0,1,4,k71,72,73,A1,A3,A4,A5,ram4,lsfw')
2013-02-23 15:58:43,428 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'acpi:PNP0C04:')
2013-02-23 15:58:43,428 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'acpi:PNP0000:')
2013-02-23 15:58:43,428 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'pci:v00008086d00003422sv00000000sd00000000bc08sc00i00')
2013-02-23 15:58:43,428 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'pci:v00008086d00002C10sv00001458sd00005000bc06sc00i00')
2013-02-23 15:58:43,428 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'input:b0003v05ACp0220e0111-e0,1,4,11,14,k71,72,73,74,75,77,78,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8C,8E,96,98,9E,9F,A1,A3,A4,A5,A6,AD,B0,B1,B2,B3,B4,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,CC,E0,E1,E3,E4,E5,E6,F0,1D0,ram4,l0,1,2,3,4,sfw')
2013-02-23 15:58:43,428 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'pci:v00008086d00002C28sv00001458sd00005000bc06sc00i00')
2013-02-23 15:58:43,428 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'pci:v00008086d00003A38sv00001458sd00005004bc0Csc03i00')
2013-02-23 15:58:43,428 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'pci:v00008086d00003A3Esv00001458sd0000A002bc04sc03i00')
2013-02-23 15:58:43,428 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2013-02-23 15:58:43,429 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip02')
2013-02-23 15:58:43,429 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'pci:v00008086d00002C18sv00001458sd00005000bc06sc00i00')
2013-02-23 15:58:43,429 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'pci:v00008086d00002C21sv00001458sd00005000bc06sc00i00')
2013-02-23 15:58:43,429 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'pci:v00008086d00003A30sv00001458sd00005001bc0Csc05i00')
2013-02-23 15:58:43,429 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'usb:v1D6Bp0002d0305dc09dsc00dp00ic09isc00ip00')
2013-02-23 15:58:43,429 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'pci:v00008086d00003425sv00000000sd00000000bc08sc00i00')
2013-02-23 15:58:43,429 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2013-02-23 15:58:43,429 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21e0440> about HardwareID('modalias', 'pci:v0000104Cd00008024sv00001458sd00001000bc0Csc00i10')
2013-02-23 15:58:43,525 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-02-23 15:58:43,648 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-02-23 15:58:43,673 DEBUG: fglrx.enabled(fglrx_experimental_9): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-02-23 15:58:43,673 DEBUG: fglrx_experimental_9 is not the alternative in use
2013-02-23 15:58:43,697 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-02-23 15:58:43,697 DEBUG: fglrx_updates is not the alternative in use
2013-02-23 15:58:43,771 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-02-23 15:58:43,892 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-02-23 15:58:43,975 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-02-23 15:58:44,095 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-02-23 15:58:47,806 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-02-23 15:58:47,807 DEBUG: fglrx_updates is not the alternative in use
2013-02-23 15:58:49,194 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2013-02-23 15:58:49,194 DEBUG: fglrx_updates is not the alternative in use
2013-02-23 15:58:54,016 DEBUG: Installing package: linux-headers-generic
2013-02-23 15:58:54,519 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='amd64' id:2064L> 0.000000
2013-02-23 15:58:54,519 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='amd64' id:2064L> 0.000000
2013-02-23 15:58:54,551 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='amd64' id:2064L> 0.000000
2013-02-23 15:58:54,586 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='amd64' id:2064L> 0.000000
2013-02-23 15:58:54,625 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='amd64' id:2064L> 0.020358
2013-02-23 15:58:55,126 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='amd64' id:2064L> 4.423854
2013-02-23 15:58:55,626 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='amd64' id:2064L> 13.139581
2013-02-23 15:58:56,127 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='amd64' id:2064L> 21.821084
2013-02-23 15:58:56,628 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='amd64' id:2064L> 30.445547
2013-02-23 15:58:57,129 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='amd64' id:2064L> 36.457573
2013-02-23 15:58:57,630 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='amd64' id:2064L> 41.739487
2013-02-23 15:58:58,131 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='amd64' id:2064L> 50.067341
2013-02-23 15:58:58,631 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='amd64' id:2064L> 58.942781
2013-02-23 15:58:59,132 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='amd64' id:2064L> 65.388312
2013-02-23 15:58:59,633 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='amd64' id:2064L> 69.791808
2013-02-23 15:59:00,134 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='amd64' id:2064L> 77.902910
2013-02-23 15:59:00,635 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='amd64' id:2064L> 85.169818
2013-02-23 15:59:01,136 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='amd64' id:2064L> 91.991814
2013-02-23 15:59:01,154 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='amd64' id:2064L> 92.217446
2013-02-23 15:59:01,154 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='amd64' id:2064L> 92.263188
2013-02-23 15:59:01,627 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='amd64' id:2064L> 99.979540
2013-02-23 15:59:01,628 DEBUG: download progress <Package: name:'linux-headers-generic' architecture='amd64' id:2064L> 100.000000
2013-02-23 15:59:01,842 DEBUG: install progress dpkg-exec 0.000000
2013-02-23 15:59:02,343 DEBUG: install progress linux-headers-3.2.0-38 0.000000
2013-02-23 15:59:02,443 DEBUG: install progress linux-headers-3.2.0-38 6.666670
2013-02-23 15:59:06,051 DEBUG: install progress linux-headers-3.2.0-38 13.333300
2013-02-23 15:59:06,081 DEBUG: install progress linux-headers-3.2.0-38 20.000000
2013-02-23 15:59:06,162 DEBUG: install progress linux-headers-3.2.0-38-generic 20.000000
2013-02-23 15:59:06,262 DEBUG: install progress linux-headers-3.2.0-38-generic 26.666700
2013-02-23 15:59:07,721 DEBUG: install progress linux-headers-3.2.0-38-generic 33.333300
2013-02-23 15:59:07,737 DEBUG: install progress linux-headers-3.2.0-38-generic 40.000000
2013-02-23 15:59:07,794 DEBUG: install progress linux-headers-generic 40.000000
2013-02-23 15:59:07,828 DEBUG: install progress linux-headers-generic 46.666700
2013-02-23 15:59:07,828 DEBUG: install progress linux-headers-generic 53.333300
2013-02-23 15:59:07,836 DEBUG: install progress linux-headers-generic 60.000000
2013-02-23 15:59:07,901 DEBUG: install progress dpkg-exec 60.000000
2013-02-23 15:59:07,930 DEBUG: install progress linux-headers-3.2.0-38 60.000000
2013-02-23 15:59:07,945 DEBUG: install progress linux-headers-3.2.0-38 66.666700
2013-02-23 15:59:07,961 DEBUG: install progress linux-headers-3.2.0-38 73.333300
2013-02-23 15:59:07,969 DEBUG: install progress linux-headers-3.2.0-38-generic 73.333300
2013-02-23 15:59:07,977 DEBUG: install progress linux-headers-3.2.0-38-generic 80.000000
2013-02-23 15:59:20,327 DEBUG: install progress linux-headers-3.2.0-38-generic 86.666700
2013-02-23 15:59:20,343 DEBUG: install progress linux-headers-generic 86.666700
2013-02-23 15:59:20,352 DEBUG: install progress linux-headers-generic 93.333300
2013-02-23 15:59:20,361 DEBUG: install progress linux-headers-generic 100.000000
2013-02-23 15:59:20,762 DEBUG: Selecting previously unselected package linux-headers-3.2.0-38.
(Reading database ... 169709 files and directories currently installed.)
Unpacking linux-headers-3.2.0-38 (from .../linux-headers-3.2.0-38_3.2.0-38.61_all.deb) ...
Selecting previously unselected package linux-headers-3.2.0-38-generic.
Unpacking linux-headers-3.2.0-38-generic (from .../linux-headers-3.2.0-38-generic_3.2.0-38.61_amd64.deb) ...
Selecting previously unselected package linux-headers-generic.
Unpacking linux-headers-generic (from .../linux-headers-generic_3.2.0.38.46_amd64.deb) ...
Setting up linux-headers-3.2.0-38 (3.2.0-38.61) ...
Setting up linux-headers-3.2.0-38-generic (3.2.0-38.61) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.2.0-38-generic /boot/vmlinuz-3.2.0-38-generic
Setting up linux-headers-generic (3.2.0.38.46) ...

2013-02-23 15:59:20,891 DEBUG: Installing package: fglrx-updates
2013-02-23 15:59:21,405 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 0.000000
2013-02-23 15:59:21,406 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 0.000000
2013-02-23 15:59:21,408 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 0.000000
2013-02-23 15:59:21,409 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 0.000000
2013-02-23 15:59:21,409 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 0.000000
2013-02-23 15:59:21,446 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 0.000000
2013-02-23 15:59:21,486 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 0.002902
2013-02-23 15:59:21,600 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 0.060625
2013-02-23 15:59:21,600 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 0.062617
2013-02-23 15:59:22,101 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 0.547995
2013-02-23 15:59:22,602 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 1.297976
2013-02-23 15:59:23,103 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 2.489505
2013-02-23 15:59:23,604 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 3.398574
2013-02-23 15:59:24,105 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 4.250826
2013-02-23 15:59:24,605 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 4.877434
2013-02-23 15:59:25,106 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 5.405018
2013-02-23 15:59:25,607 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 5.939096
2013-02-23 15:59:26,108 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 6.604664
2013-02-23 15:59:26,609 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 7.124131
2013-02-23 15:59:27,110 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 7.940670
2013-02-23 15:59:27,611 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 8.687405
2013-02-23 15:59:28,111 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 9.534786
2013-02-23 15:59:28,612 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 10.192238
2013-02-23 15:59:29,113 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 10.776639
2013-02-23 15:59:29,614 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 11.310716
2013-02-23 15:59:30,115 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 11.953558
2013-02-23 15:59:30,616 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 12.237642
2013-02-23 15:59:31,117 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 12.550946
2013-02-23 15:59:31,617 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 12.861003
2013-02-23 15:59:32,118 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 13.161320
2013-02-23 15:59:32,619 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 13.479494
2013-02-23 15:59:33,120 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 13.823642
2013-02-23 15:59:33,621 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 14.132075
2013-02-23 15:59:34,122 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 14.481093
2013-02-23 15:59:34,622 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 14.847967
2013-02-23 15:59:35,123 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 15.221334
2013-02-23 15:59:35,624 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 15.580092
2013-02-23 15:59:36,125 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 15.932356
2013-02-23 15:59:36,626 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 16.383643
2013-02-23 15:59:37,126 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 16.985901
2013-02-23 15:59:37,627 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 17.464785
2013-02-23 15:59:38,128 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 17.935553
2013-02-23 15:59:38,629 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 18.373854
2013-02-23 15:59:39,129 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 18.789428
2013-02-23 15:59:39,630 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 19.193639
2013-02-23 15:59:40,131 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 19.584863
2013-02-23 15:59:40,632 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 20.019917
2013-02-23 15:59:41,132 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 20.492308
2013-02-23 15:59:41,632 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 20.977686
2013-02-23 15:59:42,133 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 21.385143
2013-02-23 15:59:42,634 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 21.756887
2013-02-23 15:59:43,135 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 22.156228
2013-02-23 15:59:43,636 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 22.625372
2013-02-23 15:59:44,136 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 23.097763
2013-02-23 15:59:44,637 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 23.594504
2013-02-23 15:59:45,138 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 24.014949
2013-02-23 15:59:45,639 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 24.518183
2013-02-23 15:59:46,139 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 25.143168
2013-02-23 15:59:46,640 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 25.662635
2013-02-23 15:59:47,141 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 26.070093
2013-02-23 15:59:47,642 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 26.523004
2013-02-23 15:59:48,143 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 27.018121
2013-02-23 15:59:48,643 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 27.420709
2013-02-23 15:59:49,144 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 27.808686
2013-02-23 15:59:49,645 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 28.324907
2013-02-23 15:59:50,146 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 28.863855
2013-02-23 15:59:50,647 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 29.503450
2013-02-23 15:59:51,147 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 29.988827
2013-02-23 15:59:51,648 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 30.459595
2013-02-23 15:59:52,149 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 30.897896
2013-02-23 15:59:52,650 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 31.383273
2013-02-23 15:59:53,151 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 31.944948
2013-02-23 15:59:53,652 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 32.592659
2013-02-23 15:59:54,152 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 33.203034
2013-02-23 15:59:54,653 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 33.740358
2013-02-23 15:59:55,154 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 34.271189
2013-02-23 15:59:55,655 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 34.720853
2013-02-23 15:59:56,156 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 35.136428
2013-02-23 15:59:56,657 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 35.581222
2013-02-23 15:59:57,157 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 36.051989
2013-02-23 15:59:57,658 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 36.496784
2013-02-23 15:59:58,159 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 36.962681
2013-02-23 15:59:58,660 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 37.456176
2013-02-23 15:59:59,161 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 37.853893
2013-02-23 15:59:59,661 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 38.253234
2013-02-23 16:00:00,162 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 38.647705
2013-02-23 16:00:00,663 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 38.996722
2013-02-23 16:00:01,164 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 39.435023
2013-02-23 16:00:01,665 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 40.016177
2013-02-23 16:00:02,166 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 40.568112
2013-02-23 16:00:02,666 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 40.907389
2013-02-23 16:00:03,167 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 41.227186
2013-02-23 16:00:03,668 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 41.447960
2013-02-23 16:00:04,169 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 41.649254
2013-02-23 16:00:04,670 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 41.860288
2013-02-23 16:00:05,171 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 42.102165
2013-02-23 16:00:05,671 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 42.321315
2013-02-23 16:00:06,172 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 42.499882
2013-02-23 16:00:06,673 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 42.618386
2013-02-23 16:00:07,174 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 42.753123
2013-02-23 16:00:07,675 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 42.879743
2013-02-23 16:00:08,176 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 43.035583
2013-02-23 16:00:08,677 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 43.193047
2013-02-23 16:00:09,178 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 43.420314
2013-02-23 16:00:09,678 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 43.663815
2013-02-23 16:00:10,179 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 43.908938
2013-02-23 16:00:10,680 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 44.142699
2013-02-23 16:00:11,181 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 44.444640
2013-02-23 16:00:11,682 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 44.712490
2013-02-23 16:00:12,183 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 44.999821
2013-02-23 16:00:12,683 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 45.220594
2013-02-23 16:00:13,184 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 45.452732
2013-02-23 16:00:13,685 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 45.720582
2013-02-23 16:00:14,186 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 45.964083
2013-02-23 16:00:14,687 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 46.249790
2013-02-23 16:00:15,188 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 46.545237
2013-02-23 16:00:15,689 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 46.865034
2013-02-23 16:00:16,190 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 47.225415
2013-02-23 16:00:16,690 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 47.546836
2013-02-23 16:00:17,191 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 47.900723
2013-02-23 16:00:17,692 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 48.196170
2013-02-23 16:00:18,193 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 48.514344
2013-02-23 16:00:18,694 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 48.840635
2013-02-23 16:00:19,195 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 49.176666
2013-02-23 16:00:19,696 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 49.645810
2013-02-23 16:00:20,197 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 50.257808
2013-02-23 16:00:20,697 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 50.897402
2013-02-23 16:00:21,198 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 51.540244
2013-02-23 16:00:21,699 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 52.166852
2013-02-23 16:00:22,200 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 52.728526
2013-02-23 16:00:22,701 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 53.433054
2013-02-23 16:00:23,202 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 54.028819
2013-02-23 16:00:23,703 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 54.600233
2013-02-23 16:00:24,203 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 55.322618
2013-02-23 16:00:24,704 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 56.004419
2013-02-23 16:00:25,205 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 56.942708
2013-02-23 16:00:25,706 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 57.743013
2013-02-23 16:00:26,207 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 58.234884
2013-02-23 16:00:26,708 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 58.945905
2013-02-23 16:00:27,209 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 59.546540
2013-02-23 16:00:27,709 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 60.166654
2013-02-23 16:00:28,210 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 60.799756
2013-02-23 16:00:28,711 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 61.723434
2013-02-23 16:00:29,212 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 62.721786
2013-02-23 16:00:29,713 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 63.346771
2013-02-23 16:00:30,214 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 64.028572
2013-02-23 16:00:30,714 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 64.710373
2013-02-23 16:00:31,215 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 64.997704
2013-02-23 16:00:31,716 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 65.299645
2013-02-23 16:00:32,217 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 65.677882
2013-02-23 16:00:32,718 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 65.963589
2013-02-23 16:00:33,218 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 66.148650
2013-02-23 16:00:33,719 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 66.309360
2013-02-23 16:00:34,220 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 66.522017
2013-02-23 16:00:34,721 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 66.655131
2013-02-23 16:00:35,222 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 66.843438
2013-02-23 16:00:35,723 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 66.981421
2013-02-23 16:00:36,223 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 67.156742
2013-02-23 16:00:36,724 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 67.281739
2013-02-23 16:00:37,225 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 67.432709
2013-02-23 16:00:37,726 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 67.591796
2013-02-23 16:00:38,227 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 67.634003
2013-02-23 16:00:38,728 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 67.700559
2013-02-23 16:00:39,228 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 67.733026
2013-02-23 16:00:39,729 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 67.843413
2013-02-23 16:00:40,230 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 67.955423
2013-02-23 16:00:40,731 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 68.091784
2013-02-23 16:00:41,232 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 68.276844
2013-02-23 16:00:41,733 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 68.486254
2013-02-23 16:00:42,234 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 68.698911
2013-02-23 16:00:42,735 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 68.934295
2013-02-23 16:00:43,236 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 69.185912
2013-02-23 16:00:43,736 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 69.460256
2013-02-23 16:00:44,237 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 69.791417
2013-02-23 16:00:44,738 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 70.166408
2013-02-23 16:00:45,239 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 70.562502
2013-02-23 16:00:45,740 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 70.999179
2013-02-23 16:00:46,241 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 71.476440
2013-02-23 16:00:46,742 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 71.945585
2013-02-23 16:00:47,242 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 72.409859
2013-02-23 16:00:47,743 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 72.874133
2013-02-23 16:00:48,244 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 73.411458
2013-02-23 16:00:48,745 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 73.823785
2013-02-23 16:00:49,246 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 74.317279
2013-02-23 16:00:49,747 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 74.799410
2013-02-23 16:00:50,248 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 75.377318
2013-02-23 16:00:50,749 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 75.820489
2013-02-23 16:00:51,250 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 76.620794
2013-02-23 16:00:51,750 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 77.179222
2013-02-23 16:00:52,251 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 77.802583
2013-02-23 16:00:52,752 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 78.604511
2013-02-23 16:00:53,253 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 79.120732
2013-02-23 16:00:53,754 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 79.615850
2013-02-23 16:00:54,255 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 80.278171
2013-02-23 16:00:54,756 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 80.987569
2013-02-23 16:00:55,256 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 81.695344
2013-02-23 16:00:55,757 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 82.414482
2013-02-23 16:00:56,258 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 83.062194
2013-02-23 16:00:56,759 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 83.695295
2013-02-23 16:00:57,260 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 84.294306
2013-02-23 16:00:57,760 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 84.940394
2013-02-23 16:00:58,261 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 85.497198
2013-02-23 16:00:58,762 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 86.086470
2013-02-23 16:00:59,263 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 86.680611
2013-02-23 16:00:59,764 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 86.982551
2013-02-23 16:01:00,265 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 87.208195
2013-02-23 16:01:00,766 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 87.406242
2013-02-23 16:01:01,267 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 87.614029
2013-02-23 16:01:01,767 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 87.795843
2013-02-23 16:01:02,268 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 87.959800
2013-02-23 16:01:02,769 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 88.125380
2013-02-23 16:01:03,270 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 88.424074
2013-02-23 16:01:03,771 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 88.605888
2013-02-23 16:01:04,272 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 88.763352
2013-02-23 16:01:04,773 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 88.915945
2013-02-23 16:01:05,271 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 89.079286
2013-02-23 16:01:05,272 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 89.079286
2013-02-23 16:01:05,376 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 89.079286
2013-02-23 16:01:05,478 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 89.080560
2013-02-23 16:01:05,979 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 89.212051
2013-02-23 16:01:06,480 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 89.444188
2013-02-23 16:01:06,981 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 89.590288
2013-02-23 16:01:07,482 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 89.754245
2013-02-23 16:01:07,982 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 89.919825
2013-02-23 16:01:08,483 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 90.270466
2013-02-23 16:01:08,984 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 90.629223
2013-02-23 16:01:09,485 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 90.945774
2013-02-23 16:01:09,986 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 91.194145
2013-02-23 16:01:10,487 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 91.463618
2013-02-23 16:01:10,988 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 91.611342
2013-02-23 16:01:11,489 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 91.835363
2013-02-23 16:01:11,990 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 91.994449
2013-02-23 16:01:12,491 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 92.187627
2013-02-23 16:01:12,991 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 92.435997
2013-02-23 16:01:13,507 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 92.645407
2013-02-23 16:01:14,008 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 92.854818
2013-02-23 16:01:14,509 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 93.111305
2013-02-23 16:01:15,010 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 93.354806
2013-02-23 16:01:15,510 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 93.560969
2013-02-23 16:01:16,011 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 93.788236
2013-02-23 16:01:16,512 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 94.013880
2013-02-23 16:01:17,013 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 94.255757
2013-02-23 16:01:17,514 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 94.481401
2013-02-23 16:01:18,015 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 94.744382
2013-02-23 16:01:18,516 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 95.069049
2013-02-23 16:01:19,017 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 95.422936
2013-02-23 16:01:19,195 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 95.523267
2013-02-23 16:01:19,195 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 95.523267
2013-02-23 16:01:19,239 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 95.526166
2013-02-23 16:01:19,740 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 95.756680
2013-02-23 16:01:20,241 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 96.013167
2013-02-23 16:01:20,742 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 96.345951
2013-02-23 16:01:21,243 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 96.660878
2013-02-23 16:01:21,744 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 97.001779
2013-02-23 16:01:22,245 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 97.295603
2013-02-23 16:01:22,745 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 97.636504
2013-02-23 16:01:23,246 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 97.953054
2013-02-23 16:01:23,747 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 98.168958
2013-02-23 16:01:24,248 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 98.345902
2013-02-23 16:01:24,749 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 98.495249
2013-02-23 16:01:25,250 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 98.662452
2013-02-23 16:01:25,751 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 98.808553
2013-02-23 16:01:26,252 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 98.938420
2013-02-23 16:01:26,753 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 99.091013
2013-02-23 16:01:27,254 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 99.261464
2013-02-23 16:01:27,754 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 99.456264
2013-02-23 16:01:28,255 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 99.612104
2013-02-23 16:01:28,756 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 99.769568
2013-02-23 16:01:29,257 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 99.892942
2013-02-23 16:01:29,613 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16906L> 100.000000
2013-02-23 16:01:29,797 DEBUG: install progress dpkg-exec 0.000000
2013-02-23 16:01:30,008 DEBUG: install progress libc6-i386 0.000000
2013-02-23 16:01:30,108 DEBUG: install progress libc6-i386 5.000000
2013-02-23 16:01:30,235 DEBUG: install progress libc6-i386 10.000000
2013-02-23 16:01:30,243 DEBUG: install progress libc6-i386 15.000000
2013-02-23 16:01:30,314 DEBUG: install progress lib32gcc1 15.000000
2013-02-23 16:01:30,357 DEBUG: install progress lib32gcc1 20.000000
2013-02-23 16:01:30,357 DEBUG: install progress lib32gcc1 25.000000
2013-02-23 16:01:30,365 DEBUG: install progress lib32gcc1 30.000000
2013-02-23 16:01:30,447 DEBUG: install progress fglrx-updates 30.000000
2013-02-23 16:01:30,547 DEBUG: install progress fglrx-updates 35.000000
2013-02-23 16:01:32,918 DEBUG: install progress fglrx-updates 40.000000
2013-02-23 16:01:32,935 DEBUG: install progress fglrx-updates 45.000000
2013-02-23 16:01:32,988 DEBUG: install progress fglrx-amdcccle-updates 45.000000
2013-02-23 16:01:33,089 DEBUG: install progress fglrx-amdcccle-updates 50.000000
2013-02-23 16:01:33,138 DEBUG: install progress fglrx-amdcccle-updates 55.000000
2013-02-23 16:01:33,149 DEBUG: install progress fglrx-amdcccle-updates 60.000000
2013-02-23 16:01:33,165 DEBUG: install progress ureadahead 60.000000
2013-02-23 16:01:33,258 DEBUG: install progress dpkg-exec 60.000000
2013-02-23 16:01:33,292 DEBUG: install progress libc6-i386 60.000000
2013-02-23 16:01:33,316 DEBUG: install progress libc6-i386 65.000000
2013-02-23 16:01:33,334 DEBUG: install progress libc6-i386 70.000000
2013-02-23 16:01:33,359 DEBUG: install progress lib32gcc1 70.000000
2013-02-23 16:01:33,366 DEBUG: install progress lib32gcc1 75.000000
2013-02-23 16:01:33,384 DEBUG: install progress lib32gcc1 80.000000
2013-02-23 16:01:33,400 DEBUG: install progress fglrx-updates 80.000000
2013-02-23 16:01:33,443 DEBUG: install progress fglrx-updates 85.000000
2013-02-23 16:01:49,472 DEBUG: install progress fglrx-updates 90.000000
2013-02-23 16:01:49,518 DEBUG: install progress bamfdaemon 90.000000
2013-02-23 16:01:49,554 DEBUG: install progress fglrx-amdcccle-updates 90.000000
2013-02-23 16:01:49,562 DEBUG: install progress fglrx-amdcccle-updates 95.000000
2013-02-23 16:01:49,570 DEBUG: install progress fglrx-amdcccle-updates 100.000000
2013-02-23 16:01:49,581 DEBUG: install progress libc-bin 100.000000
2013-02-23 16:01:49,619 DEBUG: install progress initramfs-tools 100.000000
2013-02-23 16:01:57,636 DEBUG: Selecting previously unselected package libc6-i386.
(Reading database ... 191736 files and directories currently installed.)
Unpacking libc6-i386 (from .../libc6-i386_2.15-0ubuntu10.3_amd64.deb) ...
Selecting previously unselected package lib32gcc1.
Unpacking lib32gcc1 (from .../lib32gcc1_1%3a4.6.3-1ubuntu5_amd64.deb) ...
Selecting previously unselected package fglrx-updates.
Unpacking fglrx-updates (from .../fglrx-updates_2%3a9.000-0ubuntu0.3_amd64.deb) ...
Selecting previously unselected package fglrx-amdcccle-updates.
Unpacking fglrx-amdcccle-updates (from .../fglrx-amdcccle-updates_2%3a9.000-0ubuntu0.3_amd64.deb) ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up libc6-i386 (2.15-0ubuntu10.3) ...
Setting up lib32gcc1 (1:4.6.3-1ubuntu5) ...
Setting up fglrx-updates (2:9.000-0ubuntu0.3) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: using /usr/lib/fglrx/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
Loading new fglrx-updates-9.000 DKMS files...
First Installation: checking all kernels...
Building only for 3.5.0-25-generic
Building for architecture x86_64
Building initial module for 3.5.0-25-generic
Done.

fglrx_updates:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.5.0-25-generic/updates/dkms/

depmod....

DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Setting up fglrx-amdcccle-updates (2:9.000-0ubuntu0.3) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.5.0-25-generic

2013-02-23 16:01:57,785 WARNING: /sys/module/fglrx_updates/drivers does not exist, cannot rebind fglrx_updates driver
2013-02-23 16:02:12,492 DEBUG: fglrx.enabled(fglrx_updates): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2013-02-23 16:02:12,492 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2013-02-23 16:02:12,573 DEBUG: fglrx.enabled(fglrx_updates): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2013-02-23 16:02:12,574 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2013-02-23 16:02:12,722 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-02-23 16:02:12,855 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-02-23 16:02:12,911 DEBUG: fglrx.enabled(fglrx_experimental_9): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2013-02-23 16:02:12,911 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2013-02-23 16:02:12,941 DEBUG: fglrx.enabled(fglrx_updates): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2013-02-23 16:02:12,941 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2013-02-23 16:02:13,024 DEBUG: fglrx.enabled(fglrx_updates): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2013-02-23 16:02:13,025 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2013-02-23 16:02:13,125 DEBUG: fglrx.enabled(fglrx_updates): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2013-02-23 16:02:13,126 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2013-02-23 16:02:13,207 DEBUG: fglrx.enabled(fglrx_updates): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2013-02-23 16:02:13,207 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2013-02-23 16:02:13,354 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-02-23 16:02:13,484 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-02-23 16:03:45,946 DEBUG: Shutting down
2013-02-23 16:05:41,280 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8>
2013-02-23 16:05:43,317 DEBUG: reading modalias file /lib/modules/3.5.0-25-generic/modules.alias
2013-02-23 16:05:43,401 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2013-02-23 16:05:43,402 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2013-02-23 16:05:43,444 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2013-02-23 16:05:43,466 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2013-02-23 16:05:43,467 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2013-02-23 16:05:43,467 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2013-02-23 16:05:43,472 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2013-02-23 16:05:43,477 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2013-02-23 16:05:43,617 DEBUG: XorgDriverHandler(omapdrm_pvr, pvr-omap4, None): Disabling as package is not compatible with Q-LTS X.org
2013-02-23 16:05:43,618 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2013-02-23 16:05:43,618 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2013-02-23 16:05:43,629 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2013-02-23 16:05:43,629 DEBUG: fglrx.available: falling back to default
2013-02-23 16:05:43,775 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2013-02-23 16:05:43,778 WARNING: modinfo for module fglrx_experimental_9 failed: ERROR: modinfo: could not find module fglrx_experimental_9

2013-02-23 16:05:43,797 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverExperimental9 from name FglrxDriverExperimental9
2013-02-23 16:05:43,797 DEBUG: fglrx.available: falling back to default
2013-02-23 16:05:43,928 DEBUG: ATI/AMD proprietary FGLRX graphics driver (**experimental** beta) availability undetermined, adding to pool
2013-02-23 16:05:43,931 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2013-02-23 16:05:43,936 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2013-02-23 16:05:43,936 DEBUG: fglrx.available: falling back to default
2013-02-23 16:05:44,059 DEBUG: XorgDriverHandler(fglrx, fglrx, None): Disabling as package is not compatible with Q-LTS X.org
2013-02-23 16:05:44,059 DEBUG: ATI/AMD proprietary FGLRX graphics driver not available
2013-02-23 16:05:44,059 DEBUG: loading custom handler /usr/share/jockey/handlers/cdv.py
2013-02-23 16:05:44,063 WARNING: modinfo for module cedarview_gfx failed: ERROR: modinfo: could not find module cedarview_gfx

2013-02-23 16:05:44,063 DEBUG: Instantiated Handler subclass __builtin__.CdvDriver from name CdvDriver
2013-02-23 16:05:44,063 DEBUG: cdv.available: falling back to default
2013-02-23 16:05:44,193 DEBUG: XorgDriverHandler(cedarview_gfx, cedarview-graphics-drivers, None): Disabling as package is not compatible with Q-LTS X.org
2013-02-23 16:05:44,194 DEBUG: Intel Cedarview graphics driver not available
2013-02-23 16:05:44,194 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2013-02-23 16:05:44,210 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2013-02-23 16:05:44,219 DEBUG: Software modem not available
2013-02-23 16:05:44,219 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2013-02-23 16:05:44,226 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2013-02-23 16:05:44,231 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2013-02-23 16:05:44,232 DEBUG: nvidia.available: falling back to default
2013-02-23 16:05:44,360 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package is not compatible with Q-LTS X.org
2013-02-23 16:05:44,360 DEBUG: NVIDIA accelerated graphics driver not available
2013-02-23 16:05:44,364 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2013-02-23 16:05:44,368 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2013-02-23 16:05:44,368 DEBUG: nvidia.available: falling back to default
2013-02-23 16:05:44,503 DEBUG: XorgDriverHandler(nvidia_current, nvidia-current, None): Disabling as package is not compatible with Q-LTS X.org
2013-02-23 16:05:44,503 DEBUG: NVIDIA accelerated graphics driver not available
2013-02-23 16:05:44,506 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2013-02-23 16:05:44,511 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2013-02-23 16:05:44,511 DEBUG: nvidia.available: falling back to default
2013-02-23 16:05:44,661 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2013-02-23 16:05:44,664 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2013-02-23 16:05:44,668 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2013-02-23 16:05:44,669 DEBUG: nvidia.available: falling back to default
2013-02-23 16:05:44,802 DEBUG: XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling as package is not compatible with Q-LTS X.org
2013-02-23 16:05:44,802 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2013-02-23 16:05:44,805 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2013-02-23 16:05:44,810 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2013-02-23 16:05:44,810 DEBUG: nvidia.available: falling back to default
2013-02-23 16:05:44,960 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2013-02-23 16:05:44,963 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2013-02-23 16:05:44,967 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2013-02-23 16:05:44,968 DEBUG: nvidia.available: falling back to default
2013-02-23 16:05:45,097 DEBUG: XorgDriverHandler(nvidia_173, nvidia-173, None): Disabling as package is not compatible with Q-LTS X.org
2013-02-23 16:05:45,097 DEBUG: NVIDIA accelerated graphics driver not available
2013-02-23 16:05:45,101 WARNING: modinfo for module nvidia_experimental_310 failed: ERROR: modinfo: could not find module nvidia_experimental_310

2013-02-23 16:05:45,120 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverExperimental310 from name NvidiaDriverExperimental310
2013-02-23 16:05:45,120 DEBUG: nvidia.available: falling back to default
2013-02-23 16:05:45,245 DEBUG: NVIDIA accelerated graphics driver (**experimental** beta) availability undetermined, adding to pool
2013-02-23 16:05:45,248 WARNING: modinfo for module nvidia_experimental_304 failed: ERROR: modinfo: could not find module nvidia_experimental_304

2013-02-23 16:05:45,267 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverExperimental304 from name NvidiaDriverExperimental304
2013-02-23 16:05:45,267 DEBUG: nvidia.available: falling back to default
2013-02-23 16:05:45,392 DEBUG: XorgDriverHandler(nvidia_experimental_304, nvidia-experimental-304, None): Disabling as package is not compatible with Q-LTS X.org
2013-02-23 16:05:45,393 DEBUG: NVIDIA accelerated graphics driver (**experimental** beta) not available
2013-02-23 16:05:45,393 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2013-02-23 16:05:45,397 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2013-02-23 16:05:45,397 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2013-02-23 16:05:45,413 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2013-02-23 16:05:45,413 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2013-02-23 16:05:45,436 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2013-02-23 16:05:45,437 DEBUG: Firmware for DVB cards not available
2013-02-23 16:05:45,437 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2013-02-23 16:05:45,441 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2013-02-23 16:05:45,442 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2013-02-23 16:05:45,442 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2013-02-23 16:05:45,442 DEBUG: all custom handlers loaded
2013-02-23 16:05:45,442 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'acpi:PNP0B00:')
2013-02-23 16:05:45,442 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-02-23 16:05:45,443 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc00ip00')
2013-02-23 16:05:45,479 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-02-23 16:05:45,540 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 16:05:45,540 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'usb:v1D6Bp0001d0305dc09dsc00dp00ic09isc00ip00')
2013-02-23 16:05:45,540 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'pci:v00008086d00002822sv00001458sd0000B000bc01sc04i00')
2013-02-23 16:05:45,779 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'pci:v00008086d00002C2Asv00001458sd00005000bc06sc00i00')
2013-02-23 16:05:45,782 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'acpi:INT0800:')
2013-02-23 16:05:45,782 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'dmi:bvnAwardSoftwareInternational,Inc.:bvrF11:bd03/11/2010:svnGigabyteTechnologyCo.,Ltd.:pnEX58-UD3R:pvr:rvnGigabyteTechnologyCo.,Ltd.:rnEX58-UD3R:rvrx.x:cvnGigabyteTechnologyCo.,Ltd.:ct3:cvr:')
2013-02-23 16:05:45,792 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'usb:v05ACp0220d0069dc00dsc00dp00ic03isc01ip01')
2013-02-23 16:05:45,812 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-02-23 16:05:45,812 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 16:05:45,812 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2013-02-23 16:05:45,812 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 16:05:45,812 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'usb:v05ACp0220d0069dc00dsc00dp00ic03isc00ip00')
2013-02-23 16:05:45,812 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-02-23 16:05:45,813 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 16:05:45,813 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'pci:v00008086d0000342Fsv00000000sd00000000bc08sc00i20')
2013-02-23 16:05:45,815 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'acpi:PNP0103:')
2013-02-23 16:05:45,815 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'platform:regulatory')
2013-02-23 16:05:45,816 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2013-02-23 16:05:45,819 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-23 16:05:45,819 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 16:05:45,819 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'pci:v00008086d00003A37sv00001458sd00005004bc0Csc03i00')
2013-02-23 16:05:45,822 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'x86cpu:vendor:0000:family:0006:model:001A:feature:,0000,0001,0002,0003,0004,0005,0006,0007,0008,0009,000B,000C,000D,000E,000F,0010,0011,0013,0015,0016,0017,0018,0019,001A,001B,001C,001D,001F,002B,0034,003B,003D,0068,006B,006C,006D,006F,0070,0072,0074,0076,0078,007C,0080,0082,0083,0084,0085,0087,0088,0089,008D,008E,008F,0093,0094,0097,00C0,00E7,0100,0101,0102,0103,0104')
2013-02-23 16:05:45,825 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'kvm_intel'}
2013-02-23 16:05:45,825 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'kvm_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 16:05:45,825 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'microcode'}
2013-02-23 16:05:45,826 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'microcode', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 16:05:45,826 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'coretemp'}
2013-02-23 16:05:45,826 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'coretemp', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 16:05:45,826 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2013-02-23 16:05:45,832 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2013-02-23 16:05:45,832 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 16:05:45,832 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'acpi:PNP0100:')
2013-02-23 16:05:45,832 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'pci:v00008086d00002C11sv00001458sd00005000bc06sc00i00')
2013-02-23 16:05:45,835 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'acpi:PNP0501:')
2013-02-23 16:05:45,835 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'pci:v00008086d00003427sv00000000sd00000000bc08sc00i00')
2013-02-23 16:05:45,837 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'pci:v00008086d0000342Dsv00000000sd00000000bc08sc00i20')
2013-02-23 16:05:45,840 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'pci:v00008086d00002C23sv00001458sd00005000bc06sc00i00')
2013-02-23 16:05:45,842 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'platform:pcspkr')
2013-02-23 16:05:45,842 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2013-02-23 16:05:45,843 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 16:05:45,843 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2013-02-23 16:05:45,843 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 16:05:45,843 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'pci:v00008086d0000244Esv00001458sd00005000bc06sc04i01')
2013-02-23 16:05:45,845 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'pci:v00008086d00002C41sv00001458sd00005000bc06sc00i00')
2013-02-23 16:05:45,848 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'acpi:PNP0800:')
2013-02-23 16:05:45,848 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'pci:v00008086d00002C20sv00001458sd00005000bc06sc00i00')
2013-02-23 16:05:45,850 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'pci:v00001002d0000AAB0sv00001787sd0000AAB0bc04sc03i00')
2013-02-23 16:05:46,136 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-02-23 16:05:46,136 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 16:05:46,136 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-02-23 16:05:46,136 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 16:05:46,136 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'pci:v00008086d00003A16sv00001458sd00005001bc06sc01i00')
2013-02-23 16:05:46,139 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'lpc_ich'}
2013-02-23 16:05:46,139 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'lpc_ich', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 16:05:46,139 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'pci:v00001002d00006819sv00001787sd00002320bc03sc00i00')
2013-02-23 16:05:46,142 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2013-02-23 16:05:46,142 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 16:05:46,142 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates'}
2013-02-23 16:05:46,154 DEBUG: fglrx.enabled(fglrx_updates): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2013-02-23 16:05:46,154 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2013-02-23 16:05:46,142 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2013-02-23 16:05:46,220 DEBUG: fglrx.available: falling back to default
2013-02-23 16:05:46,362 DEBUG: fglrx.enabled(fglrx_updates): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2013-02-23 16:05:46,362 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2013-02-23 16:05:46,350 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2013-02-23 16:05:46,426 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_experimental_9', 'package': 'fglrx-experimental-9'}
2013-02-23 16:05:46,438 DEBUG: fglrx.enabled(fglrx_experimental_9): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2013-02-23 16:05:46,438 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2013-02-23 16:05:46,426 DEBUG: found match in handler pool xorg:fglrx_experimental_9([FglrxDriverExperimental9, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (**experimental** beta))
2013-02-23 16:05:46,441 WARNING: modinfo for module fglrx_experimental_9 failed: ERROR: modinfo: could not find module fglrx_experimental_9

2013-02-23 16:05:46,445 DEBUG: fglrx.available: falling back to default
2013-02-23 16:05:46,587 DEBUG: fglrx.enabled(fglrx_experimental_9): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2013-02-23 16:05:46,587 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2013-02-23 16:05:46,575 DEBUG: got handler xorg:fglrx_experimental_9([FglrxDriverExperimental9, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (**experimental** beta))
2013-02-23 16:05:46,588 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2013-02-23 16:05:46,599 DEBUG: fglrx.enabled(fglrx_updates): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2013-02-23 16:05:46,600 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2013-02-23 16:05:46,588 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2013-02-23 16:05:46,668 DEBUG: fglrx.available: falling back to default
2013-02-23 16:05:46,814 DEBUG: fglrx.enabled(fglrx_updates): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2013-02-23 16:05:46,815 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2013-02-23 16:05:46,802 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2013-02-23 16:05:46,879 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2013-02-23 16:05:46,891 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2013-02-23 16:05:46,892 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2013-02-23 16:05:46,879 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2013-02-23 16:05:46,895 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2013-02-23 16:05:46,899 DEBUG: fglrx.available: falling back to default
2013-02-23 16:05:47,026 DEBUG: XorgDriverHandler(fglrx, fglrx, None): Disabling as package is not compatible with Q-LTS X.org
2013-02-23 16:05:47,038 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2013-02-23 16:05:47,038 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2013-02-23 16:05:47,026 DEBUG: ignoring unavailable handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2013-02-23 16:05:47,038 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'pci:v00008086d00003A3Csv00001458sd00005006bc0Csc03i20')
2013-02-23 16:05:47,043 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2013-02-23 16:05:47,043 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2013-02-23 16:05:47,043 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 16:05:47,044 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2013-02-23 16:05:47,044 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 16:05:47,044 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'pci:v00008086d00003A35sv00001458sd00005004bc0Csc03i00')
2013-02-23 16:05:47,048 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'pci:v00008086d00003A3Asv00001458sd00005006bc0Csc03i20')
2013-02-23 16:05:47,051 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'pci:v000014E4d00004329sv00001385sd00007D00bc02sc80i00')
2013-02-23 16:05:47,085 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ssb'}
2013-02-23 16:05:47,085 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ssb', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 16:05:47,085 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'wl', 'package': 'bcmwl-kernel-source'}
2013-02-23 16:05:47,147 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-02-23 16:05:47,085 DEBUG: found match in handler pool kmod:wl([BroadcomWLHandler, nonfree, enabled] Broadcom STA wireless driver)
2013-02-23 16:05:47,210 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-02-23 16:05:47,148 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, enabled] Broadcom STA wireless driver)
2013-02-23 16:05:47,210 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'wl'}
2013-02-23 16:05:47,271 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-02-23 16:05:47,211 DEBUG: found match in handler pool kmod:wl([BroadcomWLHandler, nonfree, enabled] Broadcom STA wireless driver)
2013-02-23 16:05:47,333 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-02-23 16:05:47,272 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, enabled] Broadcom STA wireless driver)
2013-02-23 16:05:47,333 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'usb:v18E3p9101d0000dc00dsc00dp00ic08isc06ip50')
2013-02-23 16:05:47,333 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'acpi:PNP0C01:')
2013-02-23 16:05:47,334 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'pci:v00008086d00002C32sv00001458sd00005000bc06sc00i00')
2013-02-23 16:05:47,338 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'pci:v00008086d00003A36sv00001458sd00005004bc0Csc03i00')
2013-02-23 16:05:47,341 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'usb:v05ACp1006d9615dc09dsc00dp01ic09isc00ip00')
2013-02-23 16:05:47,341 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'pci:v00008086d00002C30sv00001458sd00005000bc06sc00i00')
2013-02-23 16:05:47,344 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'acpi:PNP0700:')
2013-02-23 16:05:47,344 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'pci:v00008086d00002C29sv00001458sd00005000bc06sc00i00')
2013-02-23 16:05:47,346 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'pci:v00008086d00003A39sv00001458sd00005004bc0Csc03i00')
2013-02-23 16:05:47,349 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'pci:v00008086d00002C22sv00001458sd00005000bc06sc00i00')
2013-02-23 16:05:47,351 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'pci:v00008086d00003423sv00000000sd00000000bc08sc00i00')
2013-02-23 16:05:47,353 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'pci:v00008086d0000342Esv00000000sd00000000bc08sc00i00')
2013-02-23 16:05:47,356 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i7core_edac'}
2013-02-23 16:05:47,356 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i7core_edac', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 16:05:47,356 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-02-23 16:05:47,356 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-23 16:05:47,356 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 16:05:47,356 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-02-23 16:05:47,356 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 16:05:47,356 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'pci:v00008086d00003426sv00000000sd00000000bc08sc00i00')
2013-02-23 16:05:47,359 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'pci:v00008086d00002C19sv00001458sd00005000bc06sc00i00')
2013-02-23 16:05:47,361 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'platform:gpio_ich')
2013-02-23 16:05:47,362 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'gpio_ich'}
2013-02-23 16:05:47,362 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'gpio_ich', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 16:05:47,362 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'pci:v00008086d00002C01sv00001458sd00005000bc06sc00i00')
2013-02-23 16:05:47,364 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2013-02-23 16:05:47,364 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-23 16:05:47,364 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 16:05:47,364 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'platform:microcode')
2013-02-23 16:05:47,365 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'wmi:F6CB5C3C-9CAE-4EBD-B577-931EA32A2CC0')
2013-02-23 16:05:47,365 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mxm_wmi'}
2013-02-23 16:05:47,365 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mxm_wmi', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 16:05:47,365 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'pci:v00008086d00003405sv00001458sd00005000bc06sc00i00')
2013-02-23 16:05:47,368 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'pci:v00008086d00002C1Csv00001458sd00005000bc06sc00i00')
2013-02-23 16:05:47,370 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'pci:v00008086d00002C31sv00001458sd00005000bc06sc00i00')
2013-02-23 16:05:47,372 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'acpi:PNP0C02:')
2013-02-23 16:05:47,372 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'pci:v00008086d00002C33sv00001458sd00005000bc06sc00i00')
2013-02-23 16:05:47,375 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip01')
2013-02-23 16:05:47,375 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-02-23 16:05:47,375 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 16:05:47,375 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2013-02-23 16:05:47,375 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 16:05:47,376 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,2,4,k110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,r0,1,6,8,am4,lsfw')
2013-02-23 16:05:47,376 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-23 16:05:47,376 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 16:05:47,376 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-02-23 16:05:47,376 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 16:05:47,376 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'acpi:PNP0200:')
2013-02-23 16:05:47,376 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2013-02-23 16:05:47,376 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-23 16:05:47,376 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 16:05:47,376 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'pci:v00008086d00003A34sv00001458sd00005004bc0Csc03i00')
2013-02-23 16:05:47,379 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001458sd0000E000bc02sc00i00')
2013-02-23 16:05:47,386 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2013-02-23 16:05:47,386 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 16:05:47,386 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2013-02-23 16:05:47,386 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-23 16:05:47,386 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 16:05:47,387 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'pci:v00008086d00003428sv00000000sd00000000bc08sc00i00')
2013-02-23 16:05:47,389 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'pci:v00008086d00002C2Bsv00001458sd00005000bc06sc00i00')
2013-02-23 16:05:47,391 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'platform:coretemp')
2013-02-23 16:05:47,392 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'hid:b0003g0000v0000046Dp0000C52B')
2013-02-23 16:05:47,428 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'hid_logitech_dj'}
2013-02-23 16:05:47,428 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'hid_logitech_dj', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 16:05:47,428 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'hid:b0003g0000v000005ACp00000220')
2013-02-23 16:05:47,429 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'hid_apple'}
2013-02-23 16:05:47,429 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'hid_apple', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 16:05:47,429 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-02-23 16:05:47,429 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'input:b0003v05ACp0220e0111-e0,1,4,k71,72,73,A1,A3,A4,A5,ram4,lsfw')
2013-02-23 16:05:47,429 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-23 16:05:47,429 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 16:05:47,429 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-02-23 16:05:47,429 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 16:05:47,429 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'acpi:PNP0C04:')
2013-02-23 16:05:47,429 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'acpi:PNP0000:')
2013-02-23 16:05:47,429 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'pci:v00008086d00003422sv00000000sd00000000bc08sc00i00')
2013-02-23 16:05:47,432 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mce_xeon75xx'}
2013-02-23 16:05:47,432 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mce_xeon75xx', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 16:05:47,432 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'pci:v00008086d00002C10sv00001458sd00005000bc06sc00i00')
2013-02-23 16:05:47,434 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'input:b0003v05ACp0220e0111-e0,1,4,11,14,k71,72,73,74,75,77,78,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8C,8E,96,98,9E,9F,A1,A3,A4,A5,A6,AD,B0,B1,B2,B3,B4,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,CC,E0,E1,E3,E4,E5,E6,F0,1D0,ram4,l0,1,2,3,4,sfw')
2013-02-23 16:05:47,435 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-23 16:05:47,435 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 16:05:47,435 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-02-23 16:05:47,435 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 16:05:47,435 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'pci:v00008086d00002C28sv00001458sd00005000bc06sc00i00')
2013-02-23 16:05:47,437 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'pci:v00008086d00003A38sv00001458sd00005004bc0Csc03i00')
2013-02-23 16:05:47,440 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'pci:v00008086d00003A3Esv00001458sd0000A002bc04sc03i00')
2013-02-23 16:05:47,442 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-02-23 16:05:47,442 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 16:05:47,442 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-02-23 16:05:47,442 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 16:05:47,442 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2013-02-23 16:05:47,442 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip02')
2013-02-23 16:05:47,443 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-02-23 16:05:47,443 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 16:05:47,443 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2013-02-23 16:05:47,443 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 16:05:47,443 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'pci:v00008086d00002C18sv00001458sd00005000bc06sc00i00')
2013-02-23 16:05:47,446 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'pci:v00008086d00002C21sv00001458sd00005000bc06sc00i00')
2013-02-23 16:05:47,448 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'pci:v00008086d00003A30sv00001458sd00005001bc0Csc05i00')
2013-02-23 16:05:47,450 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801'}
2013-02-23 16:05:47,450 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 16:05:47,450 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'usb:v1D6Bp0002d0305dc09dsc00dp00ic09isc00ip00')
2013-02-23 16:05:47,451 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'pci:v00008086d00003425sv00000000sd00000000bc08sc00i00')
2013-02-23 16:05:47,453 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2013-02-23 16:05:47,453 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-23 16:05:47,453 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 16:05:47,453 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ac5ab8> about HardwareID('modalias', 'pci:v0000104Cd00008024sv00001458sd00001000bc0Csc00i10')
2013-02-23 16:05:47,463 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci'}
2013-02-23 16:05:47,463 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 16:05:47,463 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'acpi:PNP0B00:')
2013-02-23 16:05:47,463 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-02-23 16:05:47,463 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc00ip00')
2013-02-23 16:05:47,463 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'usb:v1D6Bp0001d0305dc09dsc00dp00ic09isc00ip00')
2013-02-23 16:05:47,463 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'pci:v00008086d00002822sv00001458sd0000B000bc01sc04i00')
2013-02-23 16:05:47,463 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'pci:v00008086d00002C2Asv00001458sd00005000bc06sc00i00')
2013-02-23 16:05:47,463 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'acpi:INT0800:')
2013-02-23 16:05:47,463 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'dmi:bvnAwardSoftwareInternational,Inc.:bvrF11:bd03/11/2010:svnGigabyteTechnologyCo.,Ltd.:pnEX58-UD3R:pvr:rvnGigabyteTechnologyCo.,Ltd.:rnEX58-UD3R:rvrx.x:cvnGigabyteTechnologyCo.,Ltd.:ct3:cvr:')
2013-02-23 16:05:47,463 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'usb:v05ACp0220d0069dc00dsc00dp00ic03isc01ip01')
2013-02-23 16:05:47,463 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'usb:v05ACp0220d0069dc00dsc00dp00ic03isc00ip00')
2013-02-23 16:05:47,463 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'pci:v00008086d0000342Fsv00000000sd00000000bc08sc00i20')
2013-02-23 16:05:47,463 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'acpi:PNP0103:')
2013-02-23 16:05:47,464 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'platform:regulatory')
2013-02-23 16:05:47,464 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2013-02-23 16:05:47,464 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'pci:v00008086d00003A37sv00001458sd00005004bc0Csc03i00')
2013-02-23 16:05:47,464 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'x86cpu:vendor:0000:family:0006:model:001A:feature:,0000,0001,0002,0003,0004,0005,0006,0007,0008,0009,000B,000C,000D,000E,000F,0010,0011,0013,0015,0016,0017,0018,0019,001A,001B,001C,001D,001F,002B,0034,003B,003D,0068,006B,006C,006D,006F,0070,0072,0074,0076,0078,007C,0080,0082,0083,0084,0085,0087,0088,0089,008D,008E,008F,0093,0094,0097,00C0,00E7,0100,0101,0102,0103,0104')
2013-02-23 16:05:47,464 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2013-02-23 16:05:47,464 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'acpi:PNP0100:')
2013-02-23 16:05:47,464 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'pci:v00008086d00002C11sv00001458sd00005000bc06sc00i00')
2013-02-23 16:05:47,464 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'acpi:PNP0501:')
2013-02-23 16:05:47,464 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'pci:v00008086d00003427sv00000000sd00000000bc08sc00i00')
2013-02-23 16:05:47,464 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'pci:v00008086d0000342Dsv00000000sd00000000bc08sc00i20')
2013-02-23 16:05:47,464 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'pci:v00008086d00002C23sv00001458sd00005000bc06sc00i00')
2013-02-23 16:05:47,464 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'platform:pcspkr')
2013-02-23 16:05:47,464 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'pci:v00008086d0000244Esv00001458sd00005000bc06sc04i01')
2013-02-23 16:05:47,464 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'pci:v00008086d00002C41sv00001458sd00005000bc06sc00i00')
2013-02-23 16:05:47,464 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'acpi:PNP0800:')
2013-02-23 16:05:47,464 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'pci:v00008086d00002C20sv00001458sd00005000bc06sc00i00')
2013-02-23 16:05:47,464 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'pci:v00001002d0000AAB0sv00001787sd0000AAB0bc04sc03i00')
2013-02-23 16:05:47,465 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'pci:v00008086d00003A16sv00001458sd00005001bc06sc01i00')
2013-02-23 16:05:47,465 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'pci:v00001002d00006819sv00001787sd00002320bc03sc00i00')
2013-02-23 16:05:47,465 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'pci:v00008086d00003A3Csv00001458sd00005006bc0Csc03i20')
2013-02-23 16:05:47,465 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2013-02-23 16:05:47,465 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'pci:v00008086d00003A35sv00001458sd00005004bc0Csc03i00')
2013-02-23 16:05:47,465 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'pci:v00008086d00003A3Asv00001458sd00005006bc0Csc03i20')
2013-02-23 16:05:47,465 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'pci:v000014E4d00004329sv00001385sd00007D00bc02sc80i00')
2013-02-23 16:05:47,465 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'usb:v18E3p9101d0000dc00dsc00dp00ic08isc06ip50')
2013-02-23 16:05:47,465 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'acpi:PNP0C01:')
2013-02-23 16:05:47,465 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'pci:v00008086d00002C32sv00001458sd00005000bc06sc00i00')
2013-02-23 16:05:47,465 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'pci:v00008086d00003A36sv00001458sd00005004bc0Csc03i00')
2013-02-23 16:05:47,465 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'usb:v05ACp1006d9615dc09dsc00dp01ic09isc00ip00')
2013-02-23 16:05:47,465 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'pci:v00008086d00002C30sv00001458sd00005000bc06sc00i00')
2013-02-23 16:05:47,465 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'acpi:PNP0700:')
2013-02-23 16:05:47,465 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'pci:v00008086d00002C29sv00001458sd00005000bc06sc00i00')
2013-02-23 16:05:47,465 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'pci:v00008086d00003A39sv00001458sd00005004bc0Csc03i00')
2013-02-23 16:05:47,466 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'pci:v00008086d00002C22sv00001458sd00005000bc06sc00i00')
2013-02-23 16:05:47,466 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'pci:v00008086d00003423sv00000000sd00000000bc08sc00i00')
2013-02-23 16:05:47,466 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'pci:v00008086d0000342Esv00000000sd00000000bc08sc00i00')
2013-02-23 16:05:47,466 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-02-23 16:05:47,466 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'pci:v00008086d00003426sv00000000sd00000000bc08sc00i00')
2013-02-23 16:05:47,466 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'pci:v00008086d00002C19sv00001458sd00005000bc06sc00i00')
2013-02-23 16:05:47,466 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'platform:gpio_ich')
2013-02-23 16:05:47,466 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'pci:v00008086d00002C01sv00001458sd00005000bc06sc00i00')
2013-02-23 16:05:47,466 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2013-02-23 16:05:47,466 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'platform:microcode')
2013-02-23 16:05:47,466 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'wmi:F6CB5C3C-9CAE-4EBD-B577-931EA32A2CC0')
2013-02-23 16:05:47,466 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'pci:v00008086d00003405sv00001458sd00005000bc06sc00i00')
2013-02-23 16:05:47,466 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'pci:v00008086d00002C1Csv00001458sd00005000bc06sc00i00')
2013-02-23 16:05:47,466 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'pci:v00008086d00002C31sv00001458sd00005000bc06sc00i00')
2013-02-23 16:05:47,466 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'acpi:PNP0C02:')
2013-02-23 16:05:47,466 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'pci:v00008086d00002C33sv00001458sd00005000bc06sc00i00')
2013-02-23 16:05:47,466 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip01')
2013-02-23 16:05:47,467 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,2,4,k110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,r0,1,6,8,am4,lsfw')
2013-02-23 16:05:47,467 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'acpi:PNP0200:')
2013-02-23 16:05:47,467 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2013-02-23 16:05:47,467 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'pci:v00008086d00003A34sv00001458sd00005004bc0Csc03i00')
2013-02-23 16:05:47,467 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001458sd0000E000bc02sc00i00')
2013-02-23 16:05:47,467 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2013-02-23 16:05:47,467 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'pci:v00008086d00003428sv00000000sd00000000bc08sc00i00')
2013-02-23 16:05:47,467 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'pci:v00008086d00002C2Bsv00001458sd00005000bc06sc00i00')
2013-02-23 16:05:47,467 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'platform:coretemp')
2013-02-23 16:05:47,467 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'hid:b0003g0000v0000046Dp0000C52B')
2013-02-23 16:05:47,467 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'hid:b0003g0000v000005ACp00000220')
2013-02-23 16:05:47,467 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-02-23 16:05:47,467 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'input:b0003v05ACp0220e0111-e0,1,4,k71,72,73,A1,A3,A4,A5,ram4,lsfw')
2013-02-23 16:05:47,467 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'acpi:PNP0C04:')
2013-02-23 16:05:47,467 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'acpi:PNP0000:')
2013-02-23 16:05:47,467 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'pci:v00008086d00003422sv00000000sd00000000bc08sc00i00')
2013-02-23 16:05:47,468 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'pci:v00008086d00002C10sv00001458sd00005000bc06sc00i00')
2013-02-23 16:05:47,468 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'input:b0003v05ACp0220e0111-e0,1,4,11,14,k71,72,73,74,75,77,78,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8C,8E,96,98,9E,9F,A1,A3,A4,A5,A6,AD,B0,B1,B2,B3,B4,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,CC,E0,E1,E3,E4,E5,E6,F0,1D0,ram4,l0,1,2,3,4,sfw')
2013-02-23 16:05:47,468 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'pci:v00008086d00002C28sv00001458sd00005000bc06sc00i00')
2013-02-23 16:05:47,468 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'pci:v00008086d00003A38sv00001458sd00005004bc0Csc03i00')
2013-02-23 16:05:47,468 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'pci:v00008086d00003A3Esv00001458sd0000A002bc04sc03i00')
2013-02-23 16:05:47,468 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2013-02-23 16:05:47,468 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip02')
2013-02-23 16:05:47,468 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'pci:v00008086d00002C18sv00001458sd00005000bc06sc00i00')
2013-02-23 16:05:47,468 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'pci:v00008086d00002C21sv00001458sd00005000bc06sc00i00')
2013-02-23 16:05:47,468 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'pci:v00008086d00003A30sv00001458sd00005001bc0Csc05i00')
2013-02-23 16:05:47,468 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'usb:v1D6Bp0002d0305dc09dsc00dp00ic09isc00ip00')
2013-02-23 16:05:47,468 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'pci:v00008086d00003425sv00000000sd00000000bc08sc00i00')
2013-02-23 16:05:47,468 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2013-02-23 16:05:47,468 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2ed59e0> about HardwareID('modalias', 'pci:v0000104Cd00008024sv00001458sd00001000bc0Csc00i10')
2013-02-23 16:05:47,593 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-02-23 16:05:47,710 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-02-23 16:05:47,729 DEBUG: fglrx.enabled(fglrx_experimental_9): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2013-02-23 16:05:47,729 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2013-02-23 16:05:47,747 DEBUG: fglrx.enabled(fglrx_updates): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2013-02-23 16:05:47,747 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2013-02-23 16:05:47,881 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-02-23 16:05:48,003 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-02-23 16:05:48,086 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-02-23 16:05:48,211 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-02-23 16:05:51,375 DEBUG: fglrx.enabled(fglrx_experimental_9): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2013-02-23 16:05:51,375 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2013-02-23 16:05:52,489 DEBUG: fglrx.enabled(fglrx_updates): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2013-02-23 16:05:52,489 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2013-02-23 16:05:56,965 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-02-23 16:05:57,089 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-02-23 16:05:57,302 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-02-23 16:05:57,423 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-02-23 16:06:00,482 DEBUG: Shutting down
2013-02-23 18:27:23,261 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70>
2013-02-23 18:27:25,053 DEBUG: reading modalias file /lib/modules/3.5.0-25-generic/modules.alias
2013-02-23 18:27:25,135 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2013-02-23 18:27:25,135 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2013-02-23 18:27:25,180 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2013-02-23 18:27:25,186 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2013-02-23 18:27:25,203 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2013-02-23 18:27:25,203 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2013-02-23 18:27:25,204 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2013-02-23 18:27:25,209 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2013-02-23 18:27:25,213 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2013-02-23 18:27:25,351 DEBUG: XorgDriverHandler(omapdrm_pvr, pvr-omap4, None): Disabling as package is not compatible with Q-LTS X.org
2013-02-23 18:27:25,352 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2013-02-23 18:27:25,352 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2013-02-23 18:27:25,364 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2013-02-23 18:27:25,364 DEBUG: fglrx.available: falling back to default
2013-02-23 18:27:25,517 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2013-02-23 18:27:25,521 WARNING: modinfo for module fglrx_experimental_9 failed: ERROR: modinfo: could not find module fglrx_experimental_9

2013-02-23 18:27:25,540 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverExperimental9 from name FglrxDriverExperimental9
2013-02-23 18:27:25,540 DEBUG: fglrx.available: falling back to default
2013-02-23 18:27:25,674 DEBUG: ATI/AMD proprietary FGLRX graphics driver (**experimental** beta) availability undetermined, adding to pool
2013-02-23 18:27:25,677 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2013-02-23 18:27:25,681 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2013-02-23 18:27:25,682 DEBUG: fglrx.available: falling back to default
2013-02-23 18:27:25,814 DEBUG: XorgDriverHandler(fglrx, fglrx, None): Disabling as package is not compatible with Q-LTS X.org
2013-02-23 18:27:25,814 DEBUG: ATI/AMD proprietary FGLRX graphics driver not available
2013-02-23 18:27:25,814 DEBUG: loading custom handler /usr/share/jockey/handlers/cdv.py
2013-02-23 18:27:25,819 WARNING: modinfo for module cedarview_gfx failed: ERROR: modinfo: could not find module cedarview_gfx

2013-02-23 18:27:25,820 DEBUG: Instantiated Handler subclass __builtin__.CdvDriver from name CdvDriver
2013-02-23 18:27:25,820 DEBUG: cdv.available: falling back to default
2013-02-23 18:27:25,945 DEBUG: XorgDriverHandler(cedarview_gfx, cedarview-graphics-drivers, None): Disabling as package is not compatible with Q-LTS X.org
2013-02-23 18:27:25,946 DEBUG: Intel Cedarview graphics driver not available
2013-02-23 18:27:25,946 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2013-02-23 18:27:25,962 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2013-02-23 18:27:25,971 DEBUG: Software modem not available
2013-02-23 18:27:25,971 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2013-02-23 18:27:25,978 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2013-02-23 18:27:25,982 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2013-02-23 18:27:25,984 DEBUG: nvidia.available: falling back to default
2013-02-23 18:27:26,116 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package is not compatible with Q-LTS X.org
2013-02-23 18:27:26,116 DEBUG: NVIDIA accelerated graphics driver not available
2013-02-23 18:27:26,119 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2013-02-23 18:27:26,123 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2013-02-23 18:27:26,124 DEBUG: nvidia.available: falling back to default
2013-02-23 18:27:26,251 DEBUG: XorgDriverHandler(nvidia_current, nvidia-current, None): Disabling as package is not compatible with Q-LTS X.org
2013-02-23 18:27:26,251 DEBUG: NVIDIA accelerated graphics driver not available
2013-02-23 18:27:26,254 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2013-02-23 18:27:26,259 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2013-02-23 18:27:26,259 DEBUG: nvidia.available: falling back to default
2013-02-23 18:27:26,419 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2013-02-23 18:27:26,422 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2013-02-23 18:27:26,426 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2013-02-23 18:27:26,427 DEBUG: nvidia.available: falling back to default
2013-02-23 18:27:26,553 DEBUG: XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling as package is not compatible with Q-LTS X.org
2013-02-23 18:27:26,553 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2013-02-23 18:27:26,556 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2013-02-23 18:27:26,560 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2013-02-23 18:27:26,561 DEBUG: nvidia.available: falling back to default
2013-02-23 18:27:26,716 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2013-02-23 18:27:26,719 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2013-02-23 18:27:26,723 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2013-02-23 18:27:26,724 DEBUG: nvidia.available: falling back to default
2013-02-23 18:27:26,854 DEBUG: XorgDriverHandler(nvidia_173, nvidia-173, None): Disabling as package is not compatible with Q-LTS X.org
2013-02-23 18:27:26,854 DEBUG: NVIDIA accelerated graphics driver not available
2013-02-23 18:27:26,857 WARNING: modinfo for module nvidia_experimental_310 failed: ERROR: modinfo: could not find module nvidia_experimental_310

2013-02-23 18:27:26,877 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverExperimental310 from name NvidiaDriverExperimental310
2013-02-23 18:27:26,878 DEBUG: nvidia.available: falling back to default
2013-02-23 18:27:27,002 DEBUG: NVIDIA accelerated graphics driver (**experimental** beta) availability undetermined, adding to pool
2013-02-23 18:27:27,006 WARNING: modinfo for module nvidia_experimental_304 failed: ERROR: modinfo: could not find module nvidia_experimental_304

2013-02-23 18:27:27,025 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverExperimental304 from name NvidiaDriverExperimental304
2013-02-23 18:27:27,025 DEBUG: nvidia.available: falling back to default
2013-02-23 18:27:27,156 DEBUG: XorgDriverHandler(nvidia_experimental_304, nvidia-experimental-304, None): Disabling as package is not compatible with Q-LTS X.org
2013-02-23 18:27:27,156 DEBUG: NVIDIA accelerated graphics driver (**experimental** beta) not available
2013-02-23 18:27:27,156 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2013-02-23 18:27:27,160 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2013-02-23 18:27:27,160 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2013-02-23 18:27:27,176 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2013-02-23 18:27:27,176 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2013-02-23 18:27:27,198 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2013-02-23 18:27:27,198 DEBUG: Firmware for DVB cards not available
2013-02-23 18:27:27,198 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2013-02-23 18:27:27,203 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2013-02-23 18:27:27,203 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2013-02-23 18:27:27,203 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2013-02-23 18:27:27,204 DEBUG: all custom handlers loaded
2013-02-23 18:27:27,204 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'acpi:PNP0B00:')
2013-02-23 18:27:27,204 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc00ip00')
2013-02-23 18:27:27,242 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-02-23 18:27:27,301 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:27:27,301 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'usb:v1D6Bp0001d0305dc09dsc00dp00ic09isc00ip00')
2013-02-23 18:27:27,301 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'pci:v00008086d00002822sv00001458sd0000B000bc01sc04i00')
2013-02-23 18:27:27,540 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'pci:v00008086d00002C2Asv00001458sd00005000bc06sc00i00')
2013-02-23 18:27:27,542 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'acpi:INT0800:')
2013-02-23 18:27:27,542 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'dmi:bvnAwardSoftwareInternational,Inc.:bvrF11:bd03/11/2010:svnGigabyteTechnologyCo.,Ltd.:pnEX58-UD3R:pvr:rvnGigabyteTechnologyCo.,Ltd.:rnEX58-UD3R:rvrx.x:cvnGigabyteTechnologyCo.,Ltd.:ct3:cvr:')
2013-02-23 18:27:27,552 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'usb:v05ACp0220d0069dc00dsc00dp00ic03isc01ip01')
2013-02-23 18:27:27,572 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-02-23 18:27:27,572 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:27:27,572 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2013-02-23 18:27:27,572 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:27:27,572 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'usb:v05ACp0220d0069dc00dsc00dp00ic03isc00ip00')
2013-02-23 18:27:27,573 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-02-23 18:27:27,573 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:27:27,573 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'pci:v00008086d0000342Fsv00000000sd00000000bc08sc00i20')
2013-02-23 18:27:27,575 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'acpi:PNP0103:')
2013-02-23 18:27:27,575 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-02-23 18:27:27,576 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2013-02-23 18:27:27,579 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-23 18:27:27,580 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:27:27,580 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'pci:v00008086d00003A37sv00001458sd00005004bc0Csc03i00')
2013-02-23 18:27:27,582 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'x86cpu:vendor:0000:family:0006:model:001A:feature:,0000,0001,0002,0003,0004,0005,0006,0007,0008,0009,000B,000C,000D,000E,000F,0010,0011,0013,0015,0016,0017,0018,0019,001A,001B,001C,001D,001F,002B,0034,003B,003D,0068,006B,006C,006D,006F,0070,0072,0074,0076,0078,007C,0080,0082,0083,0084,0085,0087,0088,0089,008D,008E,008F,0093,0094,0097,00C0,00E7,0100,0101,0102,0103,0104')
2013-02-23 18:27:27,586 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'kvm_intel'}
2013-02-23 18:27:27,586 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'kvm_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:27:27,586 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'microcode'}
2013-02-23 18:27:27,586 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'microcode', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:27:27,586 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'coretemp'}
2013-02-23 18:27:27,586 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'coretemp', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:27:27,586 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2013-02-23 18:27:27,592 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2013-02-23 18:27:27,593 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:27:27,593 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2013-02-23 18:27:27,593 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'pci:v00008086d00002C11sv00001458sd00005000bc06sc00i00')
2013-02-23 18:27:27,595 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'acpi:PNP0501:')
2013-02-23 18:27:27,595 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'pci:v00008086d00003427sv00000000sd00000000bc08sc00i00')
2013-02-23 18:27:27,598 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'pci:v00008086d0000342Dsv00000000sd00000000bc08sc00i20')
2013-02-23 18:27:27,600 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'pci:v00008086d00002C23sv00001458sd00005000bc06sc00i00')
2013-02-23 18:27:27,603 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'platform:pcspkr')
2013-02-23 18:27:27,603 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2013-02-23 18:27:27,603 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:27:27,603 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2013-02-23 18:27:27,603 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:27:27,603 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'pci:v00008086d0000244Esv00001458sd00005000bc06sc04i01')
2013-02-23 18:27:27,606 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'pci:v00008086d00002C41sv00001458sd00005000bc06sc00i00')
2013-02-23 18:27:27,608 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'acpi:PNP0800:')
2013-02-23 18:27:27,608 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'pci:v00008086d00002C20sv00001458sd00005000bc06sc00i00')
2013-02-23 18:27:27,611 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'pci:v00001002d0000AAB0sv00001787sd0000AAB0bc04sc03i00')
2013-02-23 18:27:27,896 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-02-23 18:27:27,896 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:27:27,897 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-02-23 18:27:27,897 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:27:27,897 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'pci:v00008086d00003A16sv00001458sd00005001bc06sc01i00')
2013-02-23 18:27:27,899 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'lpc_ich'}
2013-02-23 18:27:27,899 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'lpc_ich', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:27:27,899 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'pci:v00001002d00006819sv00001787sd00002320bc03sc00i00')
2013-02-23 18:27:27,902 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2013-02-23 18:27:27,902 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:27:27,903 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates'}
2013-02-23 18:27:27,916 DEBUG: fglrx.enabled(fglrx_updates): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2013-02-23 18:27:27,916 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2013-02-23 18:27:27,903 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2013-02-23 18:27:27,984 DEBUG: fglrx.available: falling back to default
2013-02-23 18:27:28,130 DEBUG: fglrx.enabled(fglrx_updates): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2013-02-23 18:27:28,131 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2013-02-23 18:27:28,118 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2013-02-23 18:27:28,194 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_experimental_9', 'package': 'fglrx-experimental-9'}
2013-02-23 18:27:28,206 DEBUG: fglrx.enabled(fglrx_experimental_9): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2013-02-23 18:27:28,207 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2013-02-23 18:27:28,194 DEBUG: found match in handler pool xorg:fglrx_experimental_9([FglrxDriverExperimental9, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (**experimental** beta))
2013-02-23 18:27:28,210 WARNING: modinfo for module fglrx_experimental_9 failed: ERROR: modinfo: could not find module fglrx_experimental_9

2013-02-23 18:27:28,214 DEBUG: fglrx.available: falling back to default
2013-02-23 18:27:28,357 DEBUG: fglrx.enabled(fglrx_experimental_9): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2013-02-23 18:27:28,357 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2013-02-23 18:27:28,344 DEBUG: got handler xorg:fglrx_experimental_9([FglrxDriverExperimental9, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (**experimental** beta))
2013-02-23 18:27:28,357 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2013-02-23 18:27:28,369 DEBUG: fglrx.enabled(fglrx_updates): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2013-02-23 18:27:28,370 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2013-02-23 18:27:28,357 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2013-02-23 18:27:28,434 DEBUG: fglrx.available: falling back to default
2013-02-23 18:27:28,580 DEBUG: fglrx.enabled(fglrx_updates): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2013-02-23 18:27:28,580 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2013-02-23 18:27:28,569 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2013-02-23 18:27:28,645 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2013-02-23 18:27:28,657 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2013-02-23 18:27:28,657 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2013-02-23 18:27:28,645 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2013-02-23 18:27:28,661 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2013-02-23 18:27:28,665 DEBUG: fglrx.available: falling back to default
2013-02-23 18:27:28,793 DEBUG: XorgDriverHandler(fglrx, fglrx, None): Disabling as package is not compatible with Q-LTS X.org
2013-02-23 18:27:28,805 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2013-02-23 18:27:28,805 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2013-02-23 18:27:28,793 DEBUG: ignoring unavailable handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2013-02-23 18:27:28,806 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'pci:v00008086d00003A3Csv00001458sd00005006bc0Csc03i20')
2013-02-23 18:27:28,810 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2013-02-23 18:27:28,811 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2013-02-23 18:27:28,811 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:27:28,811 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2013-02-23 18:27:28,811 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:27:28,811 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'pci:v00008086d00003A35sv00001458sd00005004bc0Csc03i00')
2013-02-23 18:27:28,815 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'pci:v00008086d00003A3Asv00001458sd00005006bc0Csc03i20')
2013-02-23 18:27:28,819 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'pci:v000014E4d00004329sv00001385sd00007D00bc02sc80i00')
2013-02-23 18:27:28,852 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ssb'}
2013-02-23 18:27:28,853 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ssb', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:27:28,853 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'wl', 'package': 'bcmwl-kernel-source'}
2013-02-23 18:27:28,854 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-02-23 18:27:28,853 DEBUG: found match in handler pool kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2013-02-23 18:27:28,856 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2013-02-23 18:27:28,856 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-02-23 18:27:28,856 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2013-02-23 18:27:28,856 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'usb:v18E3p9101d0000dc00dsc00dp00ic08isc06ip50')
2013-02-23 18:27:28,856 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'acpi:PNP0C01:')
2013-02-23 18:27:28,857 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'pci:v00008086d00002C32sv00001458sd00005000bc06sc00i00')
2013-02-23 18:27:28,861 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'pci:v00008086d00003A36sv00001458sd00005004bc0Csc03i00')
2013-02-23 18:27:28,865 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'usb:v05ACp1006d9615dc09dsc00dp01ic09isc00ip00')
2013-02-23 18:27:28,865 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'pci:v00008086d00002C30sv00001458sd00005000bc06sc00i00')
2013-02-23 18:27:28,868 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'acpi:PNP0700:')
2013-02-23 18:27:28,869 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'pci:v00008086d00002C29sv00001458sd00005000bc06sc00i00')
2013-02-23 18:27:28,871 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'pci:v00008086d00003A39sv00001458sd00005004bc0Csc03i00')
2013-02-23 18:27:28,873 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'pci:v00008086d00002C22sv00001458sd00005000bc06sc00i00')
2013-02-23 18:27:28,876 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'pci:v00008086d00003423sv00000000sd00000000bc08sc00i00')
2013-02-23 18:27:28,878 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'pci:v00008086d0000342Esv00000000sd00000000bc08sc00i00')
2013-02-23 18:27:28,881 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i7core_edac'}
2013-02-23 18:27:28,881 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i7core_edac', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:27:28,881 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-02-23 18:27:28,881 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-23 18:27:28,881 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:27:28,881 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-02-23 18:27:28,881 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:27:28,881 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'pci:v00008086d00003426sv00000000sd00000000bc08sc00i00')
2013-02-23 18:27:28,884 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'pci:v00008086d00002C19sv00001458sd00005000bc06sc00i00')
2013-02-23 18:27:28,886 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'platform:gpio_ich')
2013-02-23 18:27:28,887 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'gpio_ich'}
2013-02-23 18:27:28,887 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'gpio_ich', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:27:28,887 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'pci:v00008086d00002C01sv00001458sd00005000bc06sc00i00')
2013-02-23 18:27:28,889 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2013-02-23 18:27:28,889 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-23 18:27:28,889 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:27:28,890 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'platform:coretemp')
2013-02-23 18:27:28,890 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'wmi:F6CB5C3C-9CAE-4EBD-B577-931EA32A2CC0')
2013-02-23 18:27:28,890 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mxm_wmi'}
2013-02-23 18:27:28,890 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mxm_wmi', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:27:28,890 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'pci:v00008086d00003405sv00001458sd00005000bc06sc00i00')
2013-02-23 18:27:28,893 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'pci:v00008086d00002C1Csv00001458sd00005000bc06sc00i00')
2013-02-23 18:27:28,895 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'pci:v00008086d00002C31sv00001458sd00005000bc06sc00i00')
2013-02-23 18:27:28,897 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'acpi:PNP0C02:')
2013-02-23 18:27:28,898 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'pci:v00008086d00002C33sv00001458sd00005000bc06sc00i00')
2013-02-23 18:27:28,900 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip01')
2013-02-23 18:27:28,900 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-02-23 18:27:28,901 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:27:28,901 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2013-02-23 18:27:28,901 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:27:28,901 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,2,4,k110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,r0,1,6,8,am4,lsfw')
2013-02-23 18:27:28,901 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-23 18:27:28,901 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:27:28,901 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-02-23 18:27:28,901 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:27:28,901 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'acpi:PNP0200:')
2013-02-23 18:27:28,901 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2013-02-23 18:27:28,901 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-23 18:27:28,901 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:27:28,902 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'pci:v00008086d00003A34sv00001458sd00005004bc0Csc03i00')
2013-02-23 18:27:28,904 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001458sd0000E000bc02sc00i00')
2013-02-23 18:27:28,911 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2013-02-23 18:27:28,912 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:27:28,912 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2013-02-23 18:27:28,912 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-23 18:27:28,912 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:27:28,912 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'pci:v00008086d00003428sv00000000sd00000000bc08sc00i00')
2013-02-23 18:27:28,914 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'pci:v00008086d00002C2Bsv00001458sd00005000bc06sc00i00')
2013-02-23 18:27:28,917 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'platform:microcode')
2013-02-23 18:27:28,917 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'hid:b0003g0000v0000046Dp0000C52B')
2013-02-23 18:27:28,953 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'hid_logitech_dj'}
2013-02-23 18:27:28,953 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'hid_logitech_dj', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:27:28,953 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'hid:b0003g0000v000005ACp00000220')
2013-02-23 18:27:28,954 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'hid_apple'}
2013-02-23 18:27:28,954 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'hid_apple', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:27:28,954 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-02-23 18:27:28,954 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'input:b0003v05ACp0220e0111-e0,1,4,k71,72,73,A1,A3,A4,A5,ram4,lsfw')
2013-02-23 18:27:28,954 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-23 18:27:28,955 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:27:28,955 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-02-23 18:27:28,955 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:27:28,955 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'acpi:PNP0C04:')
2013-02-23 18:27:28,955 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'acpi:PNP0000:')
2013-02-23 18:27:28,955 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'pci:v00008086d00003422sv00000000sd00000000bc08sc00i00')
2013-02-23 18:27:28,957 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mce_xeon75xx'}
2013-02-23 18:27:28,957 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mce_xeon75xx', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:27:28,957 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'pci:v00008086d00002C10sv00001458sd00005000bc06sc00i00')
2013-02-23 18:27:28,960 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'input:b0003v05ACp0220e0111-e0,1,4,11,14,k71,72,73,74,75,77,78,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8C,8E,96,98,9E,9F,A1,A3,A4,A5,A6,AD,B0,B1,B2,B3,B4,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,CC,E0,E1,E3,E4,E5,E6,F0,1D0,ram4,l0,1,2,3,4,sfw')
2013-02-23 18:27:28,960 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-23 18:27:28,960 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:27:28,960 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-02-23 18:27:28,960 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:27:28,960 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'pci:v00008086d00002C28sv00001458sd00005000bc06sc00i00')
2013-02-23 18:27:28,963 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'pci:v00008086d00003A38sv00001458sd00005004bc0Csc03i00')
2013-02-23 18:27:28,965 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'pci:v00008086d00003A3Esv00001458sd0000A002bc04sc03i00')
2013-02-23 18:27:28,968 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-02-23 18:27:28,968 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:27:28,968 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-02-23 18:27:28,968 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:27:28,968 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'acpi:PNP0100:')
2013-02-23 18:27:28,968 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip02')
2013-02-23 18:27:28,968 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-02-23 18:27:28,969 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:27:28,969 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2013-02-23 18:27:28,969 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:27:28,969 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'pci:v00008086d00002C18sv00001458sd00005000bc06sc00i00')
2013-02-23 18:27:28,971 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'pci:v00008086d00002C21sv00001458sd00005000bc06sc00i00')
2013-02-23 18:27:28,974 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'pci:v00008086d00003A30sv00001458sd00005001bc0Csc05i00')
2013-02-23 18:27:28,976 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801'}
2013-02-23 18:27:28,976 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:27:28,976 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'usb:v1D6Bp0002d0305dc09dsc00dp00ic09isc00ip00')
2013-02-23 18:27:28,976 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'pci:v00008086d00003425sv00000000sd00000000bc08sc00i00')
2013-02-23 18:27:28,979 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2013-02-23 18:27:28,979 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-23 18:27:28,979 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:27:28,979 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2263a70> about HardwareID('modalias', 'pci:v0000104Cd00008024sv00001458sd00001000bc0Csc00i10')
2013-02-23 18:27:28,988 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci'}
2013-02-23 18:27:28,988 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:27:28,989 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'acpi:PNP0B00:')
2013-02-23 18:27:28,989 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc00ip00')
2013-02-23 18:27:28,989 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'usb:v1D6Bp0001d0305dc09dsc00dp00ic09isc00ip00')
2013-02-23 18:27:28,989 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'pci:v00008086d00002822sv00001458sd0000B000bc01sc04i00')
2013-02-23 18:27:28,989 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'pci:v00008086d00002C2Asv00001458sd00005000bc06sc00i00')
2013-02-23 18:27:28,989 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'acpi:INT0800:')
2013-02-23 18:27:28,989 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'dmi:bvnAwardSoftwareInternational,Inc.:bvrF11:bd03/11/2010:svnGigabyteTechnologyCo.,Ltd.:pnEX58-UD3R:pvr:rvnGigabyteTechnologyCo.,Ltd.:rnEX58-UD3R:rvrx.x:cvnGigabyteTechnologyCo.,Ltd.:ct3:cvr:')
2013-02-23 18:27:28,989 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'usb:v05ACp0220d0069dc00dsc00dp00ic03isc01ip01')
2013-02-23 18:27:28,989 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'usb:v05ACp0220d0069dc00dsc00dp00ic03isc00ip00')
2013-02-23 18:27:28,989 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'pci:v00008086d0000342Fsv00000000sd00000000bc08sc00i20')
2013-02-23 18:27:28,989 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'acpi:PNP0103:')
2013-02-23 18:27:28,989 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-02-23 18:27:28,989 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2013-02-23 18:27:28,989 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'pci:v00008086d00003A37sv00001458sd00005004bc0Csc03i00')
2013-02-23 18:27:28,989 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'x86cpu:vendor:0000:family:0006:model:001A:feature:,0000,0001,0002,0003,0004,0005,0006,0007,0008,0009,000B,000C,000D,000E,000F,0010,0011,0013,0015,0016,0017,0018,0019,001A,001B,001C,001D,001F,002B,0034,003B,003D,0068,006B,006C,006D,006F,0070,0072,0074,0076,0078,007C,0080,0082,0083,0084,0085,0087,0088,0089,008D,008E,008F,0093,0094,0097,00C0,00E7,0100,0101,0102,0103,0104')
2013-02-23 18:27:28,989 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2013-02-23 18:27:28,990 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2013-02-23 18:27:28,990 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'pci:v00008086d00002C11sv00001458sd00005000bc06sc00i00')
2013-02-23 18:27:28,990 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'acpi:PNP0501:')
2013-02-23 18:27:28,990 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'pci:v00008086d00003427sv00000000sd00000000bc08sc00i00')
2013-02-23 18:27:28,990 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'pci:v00008086d0000342Dsv00000000sd00000000bc08sc00i20')
2013-02-23 18:27:28,990 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'pci:v00008086d00002C23sv00001458sd00005000bc06sc00i00')
2013-02-23 18:27:28,990 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'platform:pcspkr')
2013-02-23 18:27:28,990 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'pci:v00008086d0000244Esv00001458sd00005000bc06sc04i01')
2013-02-23 18:27:28,990 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'pci:v00008086d00002C41sv00001458sd00005000bc06sc00i00')
2013-02-23 18:27:28,990 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'acpi:PNP0800:')
2013-02-23 18:27:28,990 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'pci:v00008086d00002C20sv00001458sd00005000bc06sc00i00')
2013-02-23 18:27:28,990 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'pci:v00001002d0000AAB0sv00001787sd0000AAB0bc04sc03i00')
2013-02-23 18:27:28,990 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'pci:v00008086d00003A16sv00001458sd00005001bc06sc01i00')
2013-02-23 18:27:28,990 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'pci:v00001002d00006819sv00001787sd00002320bc03sc00i00')
2013-02-23 18:27:28,990 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'pci:v00008086d00003A3Csv00001458sd00005006bc0Csc03i20')
2013-02-23 18:27:28,990 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2013-02-23 18:27:28,991 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'pci:v00008086d00003A35sv00001458sd00005004bc0Csc03i00')
2013-02-23 18:27:28,991 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'pci:v00008086d00003A3Asv00001458sd00005006bc0Csc03i20')
2013-02-23 18:27:28,991 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'pci:v000014E4d00004329sv00001385sd00007D00bc02sc80i00')
2013-02-23 18:27:28,991 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'usb:v18E3p9101d0000dc00dsc00dp00ic08isc06ip50')
2013-02-23 18:27:28,991 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'acpi:PNP0C01:')
2013-02-23 18:27:28,991 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'pci:v00008086d00002C32sv00001458sd00005000bc06sc00i00')
2013-02-23 18:27:28,991 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'pci:v00008086d00003A36sv00001458sd00005004bc0Csc03i00')
2013-02-23 18:27:28,991 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'usb:v05ACp1006d9615dc09dsc00dp01ic09isc00ip00')
2013-02-23 18:27:28,991 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'pci:v00008086d00002C30sv00001458sd00005000bc06sc00i00')
2013-02-23 18:27:28,991 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'acpi:PNP0700:')
2013-02-23 18:27:28,991 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'pci:v00008086d00002C29sv00001458sd00005000bc06sc00i00')
2013-02-23 18:27:28,991 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'pci:v00008086d00003A39sv00001458sd00005004bc0Csc03i00')
2013-02-23 18:27:28,991 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'pci:v00008086d00002C22sv00001458sd00005000bc06sc00i00')
2013-02-23 18:27:28,991 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'pci:v00008086d00003423sv00000000sd00000000bc08sc00i00')
2013-02-23 18:27:28,991 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'pci:v00008086d0000342Esv00000000sd00000000bc08sc00i00')
2013-02-23 18:27:28,991 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-02-23 18:27:28,992 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'pci:v00008086d00003426sv00000000sd00000000bc08sc00i00')
2013-02-23 18:27:28,992 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'pci:v00008086d00002C19sv00001458sd00005000bc06sc00i00')
2013-02-23 18:27:28,992 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'platform:gpio_ich')
2013-02-23 18:27:28,992 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'pci:v00008086d00002C01sv00001458sd00005000bc06sc00i00')
2013-02-23 18:27:28,992 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2013-02-23 18:27:28,992 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'platform:coretemp')
2013-02-23 18:27:28,992 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'wmi:F6CB5C3C-9CAE-4EBD-B577-931EA32A2CC0')
2013-02-23 18:27:28,992 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'pci:v00008086d00003405sv00001458sd00005000bc06sc00i00')
2013-02-23 18:27:28,992 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'pci:v00008086d00002C1Csv00001458sd00005000bc06sc00i00')
2013-02-23 18:27:28,992 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'pci:v00008086d00002C31sv00001458sd00005000bc06sc00i00')
2013-02-23 18:27:28,992 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'acpi:PNP0C02:')
2013-02-23 18:27:28,992 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'pci:v00008086d00002C33sv00001458sd00005000bc06sc00i00')
2013-02-23 18:27:28,992 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip01')
2013-02-23 18:27:28,992 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,2,4,k110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,r0,1,6,8,am4,lsfw')
2013-02-23 18:27:28,992 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'acpi:PNP0200:')
2013-02-23 18:27:28,992 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2013-02-23 18:27:28,992 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'pci:v00008086d00003A34sv00001458sd00005004bc0Csc03i00')
2013-02-23 18:27:28,993 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001458sd0000E000bc02sc00i00')
2013-02-23 18:27:28,993 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2013-02-23 18:27:28,993 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'pci:v00008086d00003428sv00000000sd00000000bc08sc00i00')
2013-02-23 18:27:28,993 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'pci:v00008086d00002C2Bsv00001458sd00005000bc06sc00i00')
2013-02-23 18:27:28,993 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'platform:microcode')
2013-02-23 18:27:28,993 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'hid:b0003g0000v0000046Dp0000C52B')
2013-02-23 18:27:28,993 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'hid:b0003g0000v000005ACp00000220')
2013-02-23 18:27:28,993 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-02-23 18:27:28,993 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'input:b0003v05ACp0220e0111-e0,1,4,k71,72,73,A1,A3,A4,A5,ram4,lsfw')
2013-02-23 18:27:28,993 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'acpi:PNP0C04:')
2013-02-23 18:27:28,993 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'acpi:PNP0000:')
2013-02-23 18:27:28,993 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'pci:v00008086d00003422sv00000000sd00000000bc08sc00i00')
2013-02-23 18:27:28,993 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'pci:v00008086d00002C10sv00001458sd00005000bc06sc00i00')
2013-02-23 18:27:28,993 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'input:b0003v05ACp0220e0111-e0,1,4,11,14,k71,72,73,74,75,77,78,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8C,8E,96,98,9E,9F,A1,A3,A4,A5,A6,AD,B0,B1,B2,B3,B4,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,CC,E0,E1,E3,E4,E5,E6,F0,1D0,ram4,l0,1,2,3,4,sfw')
2013-02-23 18:27:28,993 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'pci:v00008086d00002C28sv00001458sd00005000bc06sc00i00')
2013-02-23 18:27:28,993 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'pci:v00008086d00003A38sv00001458sd00005004bc0Csc03i00')
2013-02-23 18:27:28,994 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'pci:v00008086d00003A3Esv00001458sd0000A002bc04sc03i00')
2013-02-23 18:27:28,994 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'acpi:PNP0100:')
2013-02-23 18:27:28,994 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip02')
2013-02-23 18:27:28,994 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'pci:v00008086d00002C18sv00001458sd00005000bc06sc00i00')
2013-02-23 18:27:28,994 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'pci:v00008086d00002C21sv00001458sd00005000bc06sc00i00')
2013-02-23 18:27:28,994 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'pci:v00008086d00003A30sv00001458sd00005001bc0Csc05i00')
2013-02-23 18:27:28,994 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'usb:v1D6Bp0002d0305dc09dsc00dp00ic09isc00ip00')
2013-02-23 18:27:28,994 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'pci:v00008086d00003425sv00000000sd00000000bc08sc00i00')
2013-02-23 18:27:28,994 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2013-02-23 18:27:28,994 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2673908> about HardwareID('modalias', 'pci:v0000104Cd00008024sv00001458sd00001000bc0Csc00i10')
2013-02-23 18:27:29,029 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-02-23 18:27:29,057 DEBUG: fglrx.enabled(fglrx_experimental_9): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2013-02-23 18:27:29,057 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2013-02-23 18:27:29,077 DEBUG: fglrx.enabled(fglrx_updates): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2013-02-23 18:27:29,077 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2013-02-23 18:27:29,154 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-02-23 18:27:29,170 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-02-23 18:27:29,185 DEBUG: fglrx.enabled(fglrx_experimental_9): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2013-02-23 18:27:29,185 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2013-02-23 18:27:29,201 DEBUG: fglrx.enabled(fglrx_updates): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2013-02-23 18:27:29,201 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2013-02-23 18:27:32,705 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-02-23 18:27:35,981 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2013-02-23 18:27:35,982 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2013-02-23 18:27:35,999 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-02-23 18:28:24,331 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-02-23 18:28:24,354 DEBUG: fglrx.enabled(fglrx_experimental_9): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2013-02-23 18:28:24,355 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2013-02-23 18:28:24,378 DEBUG: fglrx.enabled(fglrx_updates): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2013-02-23 18:28:24,378 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2013-02-23 18:28:24,462 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-02-23 18:28:24,485 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-02-23 18:28:24,506 DEBUG: fglrx.enabled(fglrx_experimental_9): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2013-02-23 18:28:24,506 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2013-02-23 18:28:24,528 DEBUG: fglrx.enabled(fglrx_updates): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2013-02-23 18:28:24,528 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2013-02-23 18:28:24,682 DEBUG: Shutting down
2013-02-23 18:28:28,829 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70>
2013-02-23 18:28:30,610 DEBUG: reading modalias file /lib/modules/3.5.0-25-generic/modules.alias
2013-02-23 18:28:30,694 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2013-02-23 18:28:30,694 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2013-02-23 18:28:30,737 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2013-02-23 18:28:30,741 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2013-02-23 18:28:30,758 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2013-02-23 18:28:30,759 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2013-02-23 18:28:30,759 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2013-02-23 18:28:30,764 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2013-02-23 18:28:30,769 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2013-02-23 18:28:30,896 DEBUG: XorgDriverHandler(omapdrm_pvr, pvr-omap4, None): Disabling as package is not compatible with Q-LTS X.org
2013-02-23 18:28:30,896 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2013-02-23 18:28:30,896 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2013-02-23 18:28:30,907 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2013-02-23 18:28:30,907 DEBUG: fglrx.available: falling back to default
2013-02-23 18:28:31,052 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2013-02-23 18:28:31,055 WARNING: modinfo for module fglrx_experimental_9 failed: ERROR: modinfo: could not find module fglrx_experimental_9

2013-02-23 18:28:31,074 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverExperimental9 from name FglrxDriverExperimental9
2013-02-23 18:28:31,074 DEBUG: fglrx.available: falling back to default
2013-02-23 18:28:31,205 DEBUG: ATI/AMD proprietary FGLRX graphics driver (**experimental** beta) availability undetermined, adding to pool
2013-02-23 18:28:31,208 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2013-02-23 18:28:31,212 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2013-02-23 18:28:31,212 DEBUG: fglrx.available: falling back to default
2013-02-23 18:28:31,345 DEBUG: XorgDriverHandler(fglrx, fglrx, None): Disabling as package is not compatible with Q-LTS X.org
2013-02-23 18:28:31,345 DEBUG: ATI/AMD proprietary FGLRX graphics driver not available
2013-02-23 18:28:31,345 DEBUG: loading custom handler /usr/share/jockey/handlers/cdv.py
2013-02-23 18:28:31,350 WARNING: modinfo for module cedarview_gfx failed: ERROR: modinfo: could not find module cedarview_gfx

2013-02-23 18:28:31,350 DEBUG: Instantiated Handler subclass __builtin__.CdvDriver from name CdvDriver
2013-02-23 18:28:31,350 DEBUG: cdv.available: falling back to default
2013-02-23 18:28:31,477 DEBUG: XorgDriverHandler(cedarview_gfx, cedarview-graphics-drivers, None): Disabling as package is not compatible with Q-LTS X.org
2013-02-23 18:28:31,477 DEBUG: Intel Cedarview graphics driver not available
2013-02-23 18:28:31,477 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2013-02-23 18:28:31,493 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2013-02-23 18:28:31,500 DEBUG: Software modem not available
2013-02-23 18:28:31,500 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2013-02-23 18:28:31,507 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2013-02-23 18:28:31,511 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2013-02-23 18:28:31,512 DEBUG: nvidia.available: falling back to default
2013-02-23 18:28:31,646 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package is not compatible with Q-LTS X.org
2013-02-23 18:28:31,646 DEBUG: NVIDIA accelerated graphics driver not available
2013-02-23 18:28:31,649 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2013-02-23 18:28:31,653 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2013-02-23 18:28:31,654 DEBUG: nvidia.available: falling back to default
2013-02-23 18:28:31,790 DEBUG: XorgDriverHandler(nvidia_current, nvidia-current, None): Disabling as package is not compatible with Q-LTS X.org
2013-02-23 18:28:31,790 DEBUG: NVIDIA accelerated graphics driver not available
2013-02-23 18:28:31,793 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2013-02-23 18:28:31,797 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2013-02-23 18:28:31,798 DEBUG: nvidia.available: falling back to default
2013-02-23 18:28:31,949 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2013-02-23 18:28:31,953 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2013-02-23 18:28:31,957 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2013-02-23 18:28:31,957 DEBUG: nvidia.available: falling back to default
2013-02-23 18:28:32,087 DEBUG: XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling as package is not compatible with Q-LTS X.org
2013-02-23 18:28:32,087 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2013-02-23 18:28:32,090 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2013-02-23 18:28:32,094 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2013-02-23 18:28:32,095 DEBUG: nvidia.available: falling back to default
2013-02-23 18:28:32,245 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2013-02-23 18:28:32,248 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2013-02-23 18:28:32,252 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2013-02-23 18:28:32,253 DEBUG: nvidia.available: falling back to default
2013-02-23 18:28:32,389 DEBUG: XorgDriverHandler(nvidia_173, nvidia-173, None): Disabling as package is not compatible with Q-LTS X.org
2013-02-23 18:28:32,389 DEBUG: NVIDIA accelerated graphics driver not available
2013-02-23 18:28:32,392 WARNING: modinfo for module nvidia_experimental_310 failed: ERROR: modinfo: could not find module nvidia_experimental_310

2013-02-23 18:28:32,411 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverExperimental310 from name NvidiaDriverExperimental310
2013-02-23 18:28:32,412 DEBUG: nvidia.available: falling back to default
2013-02-23 18:28:32,541 DEBUG: NVIDIA accelerated graphics driver (**experimental** beta) availability undetermined, adding to pool
2013-02-23 18:28:32,544 WARNING: modinfo for module nvidia_experimental_304 failed: ERROR: modinfo: could not find module nvidia_experimental_304

2013-02-23 18:28:32,563 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverExperimental304 from name NvidiaDriverExperimental304
2013-02-23 18:28:32,564 DEBUG: nvidia.available: falling back to default
2013-02-23 18:28:32,690 DEBUG: XorgDriverHandler(nvidia_experimental_304, nvidia-experimental-304, None): Disabling as package is not compatible with Q-LTS X.org
2013-02-23 18:28:32,691 DEBUG: NVIDIA accelerated graphics driver (**experimental** beta) not available
2013-02-23 18:28:32,691 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2013-02-23 18:28:32,694 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2013-02-23 18:28:32,695 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2013-02-23 18:28:32,710 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2013-02-23 18:28:32,710 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2013-02-23 18:28:32,732 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2013-02-23 18:28:32,732 DEBUG: Firmware for DVB cards not available
2013-02-23 18:28:32,733 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2013-02-23 18:28:32,737 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2013-02-23 18:28:32,737 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2013-02-23 18:28:32,737 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2013-02-23 18:28:32,737 DEBUG: all custom handlers loaded
2013-02-23 18:28:32,738 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'acpi:PNP0B00:')
2013-02-23 18:28:32,738 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc00ip00')
2013-02-23 18:28:32,776 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-02-23 18:28:32,832 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:28:32,832 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'usb:v1D6Bp0001d0305dc09dsc00dp00ic09isc00ip00')
2013-02-23 18:28:32,832 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'pci:v00008086d00002822sv00001458sd0000B000bc01sc04i00')
2013-02-23 18:28:33,070 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'pci:v00008086d00002C2Asv00001458sd00005000bc06sc00i00')
2013-02-23 18:28:33,072 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'acpi:INT0800:')
2013-02-23 18:28:33,072 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'dmi:bvnAwardSoftwareInternational,Inc.:bvrF11:bd03/11/2010:svnGigabyteTechnologyCo.,Ltd.:pnEX58-UD3R:pvr:rvnGigabyteTechnologyCo.,Ltd.:rnEX58-UD3R:rvrx.x:cvnGigabyteTechnologyCo.,Ltd.:ct3:cvr:')
2013-02-23 18:28:33,083 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'usb:v05ACp0220d0069dc00dsc00dp00ic03isc01ip01')
2013-02-23 18:28:33,102 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-02-23 18:28:33,102 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:28:33,102 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2013-02-23 18:28:33,102 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:28:33,102 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'usb:v05ACp0220d0069dc00dsc00dp00ic03isc00ip00')
2013-02-23 18:28:33,103 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-02-23 18:28:33,103 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:28:33,103 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'pci:v00008086d0000342Fsv00000000sd00000000bc08sc00i20')
2013-02-23 18:28:33,105 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'acpi:PNP0103:')
2013-02-23 18:28:33,105 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-02-23 18:28:33,106 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2013-02-23 18:28:33,110 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-23 18:28:33,110 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:28:33,110 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'pci:v00008086d00003A37sv00001458sd00005004bc0Csc03i00')
2013-02-23 18:28:33,112 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'x86cpu:vendor:0000:family:0006:model:001A:feature:,0000,0001,0002,0003,0004,0005,0006,0007,0008,0009,000B,000C,000D,000E,000F,0010,0011,0013,0015,0016,0017,0018,0019,001A,001B,001C,001D,001F,002B,0034,003B,003D,0068,006B,006C,006D,006F,0070,0072,0074,0076,0078,007C,0080,0082,0083,0084,0085,0087,0088,0089,008D,008E,008F,0093,0094,0097,00C0,00E7,0100,0101,0102,0103,0104')
2013-02-23 18:28:33,116 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'kvm_intel'}
2013-02-23 18:28:33,116 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'kvm_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:28:33,116 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'microcode'}
2013-02-23 18:28:33,116 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'microcode', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:28:33,116 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'coretemp'}
2013-02-23 18:28:33,116 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'coretemp', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:28:33,116 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2013-02-23 18:28:33,123 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2013-02-23 18:28:33,123 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:28:33,123 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2013-02-23 18:28:33,123 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'pci:v00008086d00002C11sv00001458sd00005000bc06sc00i00')
2013-02-23 18:28:33,125 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'acpi:PNP0501:')
2013-02-23 18:28:33,125 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'pci:v00008086d00003427sv00000000sd00000000bc08sc00i00')
2013-02-23 18:28:33,128 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'pci:v00008086d0000342Dsv00000000sd00000000bc08sc00i20')
2013-02-23 18:28:33,130 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'pci:v00008086d00002C23sv00001458sd00005000bc06sc00i00')
2013-02-23 18:28:33,132 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'platform:pcspkr')
2013-02-23 18:28:33,133 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2013-02-23 18:28:33,133 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:28:33,133 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2013-02-23 18:28:33,133 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:28:33,133 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'pci:v00008086d0000244Esv00001458sd00005000bc06sc04i01')
2013-02-23 18:28:33,136 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'pci:v00008086d00002C41sv00001458sd00005000bc06sc00i00')
2013-02-23 18:28:33,138 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'acpi:PNP0800:')
2013-02-23 18:28:33,138 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'pci:v00008086d00002C20sv00001458sd00005000bc06sc00i00')
2013-02-23 18:28:33,141 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'pci:v00001002d0000AAB0sv00001787sd0000AAB0bc04sc03i00')
2013-02-23 18:28:33,426 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-02-23 18:28:33,427 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:28:33,427 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-02-23 18:28:33,427 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:28:33,427 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'pci:v00008086d00003A16sv00001458sd00005001bc06sc01i00')
2013-02-23 18:28:33,429 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'lpc_ich'}
2013-02-23 18:28:33,430 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'lpc_ich', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:28:33,430 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'pci:v00001002d00006819sv00001787sd00002320bc03sc00i00')
2013-02-23 18:28:33,433 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2013-02-23 18:28:33,433 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:28:33,433 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates'}
2013-02-23 18:28:33,444 DEBUG: fglrx.enabled(fglrx_updates): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2013-02-23 18:28:33,444 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2013-02-23 18:28:33,433 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2013-02-23 18:28:33,513 DEBUG: fglrx.available: falling back to default
2013-02-23 18:28:33,648 DEBUG: fglrx.enabled(fglrx_updates): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2013-02-23 18:28:33,648 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2013-02-23 18:28:33,636 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2013-02-23 18:28:33,724 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_experimental_9', 'package': 'fglrx-experimental-9'}
2013-02-23 18:28:33,735 DEBUG: fglrx.enabled(fglrx_experimental_9): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2013-02-23 18:28:33,736 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2013-02-23 18:28:33,724 DEBUG: found match in handler pool xorg:fglrx_experimental_9([FglrxDriverExperimental9, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (**experimental** beta))
2013-02-23 18:28:33,739 WARNING: modinfo for module fglrx_experimental_9 failed: ERROR: modinfo: could not find module fglrx_experimental_9

2013-02-23 18:28:33,743 DEBUG: fglrx.available: falling back to default
2013-02-23 18:28:33,883 DEBUG: fglrx.enabled(fglrx_experimental_9): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2013-02-23 18:28:33,884 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2013-02-23 18:28:33,871 DEBUG: got handler xorg:fglrx_experimental_9([FglrxDriverExperimental9, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (**experimental** beta))
2013-02-23 18:28:33,884 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2013-02-23 18:28:33,896 DEBUG: fglrx.enabled(fglrx_updates): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2013-02-23 18:28:33,896 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2013-02-23 18:28:33,884 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2013-02-23 18:28:33,977 DEBUG: fglrx.available: falling back to default
2013-02-23 18:28:34,118 DEBUG: fglrx.enabled(fglrx_updates): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2013-02-23 18:28:34,118 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2013-02-23 18:28:34,106 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2013-02-23 18:28:34,186 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2013-02-23 18:28:34,197 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2013-02-23 18:28:34,197 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2013-02-23 18:28:34,186 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2013-02-23 18:28:34,200 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2013-02-23 18:28:34,205 DEBUG: fglrx.available: falling back to default
2013-02-23 18:28:34,333 DEBUG: XorgDriverHandler(fglrx, fglrx, None): Disabling as package is not compatible with Q-LTS X.org
2013-02-23 18:28:34,346 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2013-02-23 18:28:34,346 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2013-02-23 18:28:34,334 DEBUG: ignoring unavailable handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2013-02-23 18:28:34,346 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'pci:v00008086d00003A3Csv00001458sd00005006bc0Csc03i20')
2013-02-23 18:28:34,351 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2013-02-23 18:28:34,351 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2013-02-23 18:28:34,351 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:28:34,351 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2013-02-23 18:28:34,351 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:28:34,352 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'pci:v00008086d00003A35sv00001458sd00005004bc0Csc03i00')
2013-02-23 18:28:34,355 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'pci:v00008086d00003A3Asv00001458sd00005006bc0Csc03i20')
2013-02-23 18:28:34,359 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'pci:v000014E4d00004329sv00001385sd00007D00bc02sc80i00')
2013-02-23 18:28:34,394 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ssb'}
2013-02-23 18:28:34,394 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ssb', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:28:34,394 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'wl', 'package': 'bcmwl-kernel-source'}
2013-02-23 18:28:34,394 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-02-23 18:28:34,394 DEBUG: found match in handler pool kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2013-02-23 18:28:34,397 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2013-02-23 18:28:34,398 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-02-23 18:28:34,398 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2013-02-23 18:28:34,398 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'usb:v18E3p9101d0000dc00dsc00dp00ic08isc06ip50')
2013-02-23 18:28:34,399 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'acpi:PNP0C01:')
2013-02-23 18:28:34,399 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'pci:v00008086d00002C32sv00001458sd00005000bc06sc00i00')
2013-02-23 18:28:34,403 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'pci:v00008086d00003A36sv00001458sd00005004bc0Csc03i00')
2013-02-23 18:28:34,407 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'usb:v05ACp1006d9615dc09dsc00dp01ic09isc00ip00')
2013-02-23 18:28:34,407 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'pci:v00008086d00002C30sv00001458sd00005000bc06sc00i00')
2013-02-23 18:28:34,411 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'acpi:PNP0700:')
2013-02-23 18:28:34,411 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'pci:v00008086d00002C29sv00001458sd00005000bc06sc00i00')
2013-02-23 18:28:34,414 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'pci:v00008086d00003A39sv00001458sd00005004bc0Csc03i00')
2013-02-23 18:28:34,416 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'pci:v00008086d00002C22sv00001458sd00005000bc06sc00i00')
2013-02-23 18:28:34,418 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'pci:v00008086d00003423sv00000000sd00000000bc08sc00i00')
2013-02-23 18:28:34,421 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'pci:v00008086d0000342Esv00000000sd00000000bc08sc00i00')
2013-02-23 18:28:34,423 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i7core_edac'}
2013-02-23 18:28:34,423 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i7core_edac', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:28:34,423 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-02-23 18:28:34,423 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-23 18:28:34,424 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:28:34,424 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-02-23 18:28:34,424 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:28:34,424 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'pci:v00008086d00003426sv00000000sd00000000bc08sc00i00')
2013-02-23 18:28:34,426 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'pci:v00008086d00002C19sv00001458sd00005000bc06sc00i00')
2013-02-23 18:28:34,429 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'platform:gpio_ich')
2013-02-23 18:28:34,429 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'gpio_ich'}
2013-02-23 18:28:34,429 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'gpio_ich', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:28:34,429 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'pci:v00008086d00002C01sv00001458sd00005000bc06sc00i00')
2013-02-23 18:28:34,432 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2013-02-23 18:28:34,432 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-23 18:28:34,432 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:28:34,432 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'platform:coretemp')
2013-02-23 18:28:34,432 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'wmi:F6CB5C3C-9CAE-4EBD-B577-931EA32A2CC0')
2013-02-23 18:28:34,432 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mxm_wmi'}
2013-02-23 18:28:34,432 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mxm_wmi', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:28:34,432 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'pci:v00008086d00003405sv00001458sd00005000bc06sc00i00')
2013-02-23 18:28:34,435 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'pci:v00008086d00002C1Csv00001458sd00005000bc06sc00i00')
2013-02-23 18:28:34,437 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'pci:v00008086d00002C31sv00001458sd00005000bc06sc00i00')
2013-02-23 18:28:34,440 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'acpi:PNP0C02:')
2013-02-23 18:28:34,440 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'pci:v00008086d00002C33sv00001458sd00005000bc06sc00i00')
2013-02-23 18:28:34,442 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip01')
2013-02-23 18:28:34,442 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-02-23 18:28:34,443 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:28:34,443 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2013-02-23 18:28:34,443 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:28:34,443 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,2,4,k110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,r0,1,6,8,am4,lsfw')
2013-02-23 18:28:34,443 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-23 18:28:34,443 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:28:34,443 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-02-23 18:28:34,443 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:28:34,443 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'acpi:PNP0200:')
2013-02-23 18:28:34,443 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2013-02-23 18:28:34,443 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-23 18:28:34,444 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:28:34,444 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'pci:v00008086d00003A34sv00001458sd00005004bc0Csc03i00')
2013-02-23 18:28:34,446 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001458sd0000E000bc02sc00i00')
2013-02-23 18:28:34,453 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2013-02-23 18:28:34,453 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:28:34,453 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2013-02-23 18:28:34,454 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-23 18:28:34,454 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:28:34,454 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'pci:v00008086d00003428sv00000000sd00000000bc08sc00i00')
2013-02-23 18:28:34,456 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'pci:v00008086d00002C2Bsv00001458sd00005000bc06sc00i00')
2013-02-23 18:28:34,459 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'platform:microcode')
2013-02-23 18:28:34,459 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'hid:b0003g0000v0000046Dp0000C52B')
2013-02-23 18:28:34,495 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'hid_logitech_dj'}
2013-02-23 18:28:34,495 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'hid_logitech_dj', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:28:34,495 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'hid:b0003g0000v000005ACp00000220')
2013-02-23 18:28:34,496 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'hid_apple'}
2013-02-23 18:28:34,496 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'hid_apple', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:28:34,496 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-02-23 18:28:34,496 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'input:b0003v05ACp0220e0111-e0,1,4,k71,72,73,A1,A3,A4,A5,ram4,lsfw')
2013-02-23 18:28:34,496 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-23 18:28:34,496 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:28:34,496 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-02-23 18:28:34,496 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:28:34,497 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'acpi:PNP0C04:')
2013-02-23 18:28:34,497 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'acpi:PNP0000:')
2013-02-23 18:28:34,497 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'pci:v00008086d00003422sv00000000sd00000000bc08sc00i00')
2013-02-23 18:28:34,499 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mce_xeon75xx'}
2013-02-23 18:28:34,499 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mce_xeon75xx', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:28:34,499 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'pci:v00008086d00002C10sv00001458sd00005000bc06sc00i00')
2013-02-23 18:28:34,502 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'input:b0003v05ACp0220e0111-e0,1,4,11,14,k71,72,73,74,75,77,78,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8C,8E,96,98,9E,9F,A1,A3,A4,A5,A6,AD,B0,B1,B2,B3,B4,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,CC,E0,E1,E3,E4,E5,E6,F0,1D0,ram4,l0,1,2,3,4,sfw')
2013-02-23 18:28:34,502 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-23 18:28:34,502 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:28:34,502 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-02-23 18:28:34,502 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:28:34,502 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'pci:v00008086d00002C28sv00001458sd00005000bc06sc00i00')
2013-02-23 18:28:34,504 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'pci:v00008086d00003A38sv00001458sd00005004bc0Csc03i00')
2013-02-23 18:28:34,507 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'pci:v00008086d00003A3Esv00001458sd0000A002bc04sc03i00')
2013-02-23 18:28:34,509 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-02-23 18:28:34,509 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:28:34,509 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-02-23 18:28:34,509 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:28:34,510 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'acpi:PNP0100:')
2013-02-23 18:28:34,510 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip02')
2013-02-23 18:28:34,510 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-02-23 18:28:34,510 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:28:34,510 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2013-02-23 18:28:34,510 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:28:34,510 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'pci:v00008086d00002C18sv00001458sd00005000bc06sc00i00')
2013-02-23 18:28:34,513 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'pci:v00008086d00002C21sv00001458sd00005000bc06sc00i00')
2013-02-23 18:28:34,515 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'pci:v00008086d00003A30sv00001458sd00005001bc0Csc05i00')
2013-02-23 18:28:34,517 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801'}
2013-02-23 18:28:34,518 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:28:34,518 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'usb:v1D6Bp0002d0305dc09dsc00dp00ic09isc00ip00')
2013-02-23 18:28:34,518 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'pci:v00008086d00003425sv00000000sd00000000bc08sc00i00')
2013-02-23 18:28:34,520 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2013-02-23 18:28:34,520 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-23 18:28:34,520 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:28:34,521 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ca2a70> about HardwareID('modalias', 'pci:v0000104Cd00008024sv00001458sd00001000bc0Csc00i10')
2013-02-23 18:28:34,530 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci'}
2013-02-23 18:28:34,530 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2013-02-23 18:28:34,530 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'acpi:PNP0B00:')
2013-02-23 18:28:34,530 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc00ip00')
2013-02-23 18:28:34,530 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'usb:v1D6Bp0001d0305dc09dsc00dp00ic09isc00ip00')
2013-02-23 18:28:34,530 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'pci:v00008086d00002822sv00001458sd0000B000bc01sc04i00')
2013-02-23 18:28:34,530 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'pci:v00008086d00002C2Asv00001458sd00005000bc06sc00i00')
2013-02-23 18:28:34,530 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'acpi:INT0800:')
2013-02-23 18:28:34,530 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'dmi:bvnAwardSoftwareInternational,Inc.:bvrF11:bd03/11/2010:svnGigabyteTechnologyCo.,Ltd.:pnEX58-UD3R:pvr:rvnGigabyteTechnologyCo.,Ltd.:rnEX58-UD3R:rvrx.x:cvnGigabyteTechnologyCo.,Ltd.:ct3:cvr:')
2013-02-23 18:28:34,530 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'usb:v05ACp0220d0069dc00dsc00dp00ic03isc01ip01')
2013-02-23 18:28:34,530 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'usb:v05ACp0220d0069dc00dsc00dp00ic03isc00ip00')
2013-02-23 18:28:34,530 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'pci:v00008086d0000342Fsv00000000sd00000000bc08sc00i20')
2013-02-23 18:28:34,530 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'acpi:PNP0103:')
2013-02-23 18:28:34,531 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-02-23 18:28:34,531 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2013-02-23 18:28:34,531 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'pci:v00008086d00003A37sv00001458sd00005004bc0Csc03i00')
2013-02-23 18:28:34,531 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'x86cpu:vendor:0000:family:0006:model:001A:feature:,0000,0001,0002,0003,0004,0005,0006,0007,0008,0009,000B,000C,000D,000E,000F,0010,0011,0013,0015,0016,0017,0018,0019,001A,001B,001C,001D,001F,002B,0034,003B,003D,0068,006B,006C,006D,006F,0070,0072,0074,0076,0078,007C,0080,0082,0083,0084,0085,0087,0088,0089,008D,008E,008F,0093,0094,0097,00C0,00E7,0100,0101,0102,0103,0104')
2013-02-23 18:28:34,531 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2013-02-23 18:28:34,531 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2013-02-23 18:28:34,531 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'pci:v00008086d00002C11sv00001458sd00005000bc06sc00i00')
2013-02-23 18:28:34,531 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'acpi:PNP0501:')
2013-02-23 18:28:34,531 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'pci:v00008086d00003427sv00000000sd00000000bc08sc00i00')
2013-02-23 18:28:34,531 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'pci:v00008086d0000342Dsv00000000sd00000000bc08sc00i20')
2013-02-23 18:28:34,531 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'pci:v00008086d00002C23sv00001458sd00005000bc06sc00i00')
2013-02-23 18:28:34,531 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'platform:pcspkr')
2013-02-23 18:28:34,531 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'pci:v00008086d0000244Esv00001458sd00005000bc06sc04i01')
2013-02-23 18:28:34,531 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'pci:v00008086d00002C41sv00001458sd00005000bc06sc00i00')
2013-02-23 18:28:34,531 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'acpi:PNP0800:')
2013-02-23 18:28:34,531 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'pci:v00008086d00002C20sv00001458sd00005000bc06sc00i00')
2013-02-23 18:28:34,532 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'pci:v00001002d0000AAB0sv00001787sd0000AAB0bc04sc03i00')
2013-02-23 18:28:34,532 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'pci:v00008086d00003A16sv00001458sd00005001bc06sc01i00')
2013-02-23 18:28:34,532 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'pci:v00001002d00006819sv00001787sd00002320bc03sc00i00')
2013-02-23 18:28:34,532 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'pci:v00008086d00003A3Csv00001458sd00005006bc0Csc03i20')
2013-02-23 18:28:34,532 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2013-02-23 18:28:34,532 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'pci:v00008086d00003A35sv00001458sd00005004bc0Csc03i00')
2013-02-23 18:28:34,532 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'pci:v00008086d00003A3Asv00001458sd00005006bc0Csc03i20')
2013-02-23 18:28:34,532 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'pci:v000014E4d00004329sv00001385sd00007D00bc02sc80i00')
2013-02-23 18:28:34,532 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'usb:v18E3p9101d0000dc00dsc00dp00ic08isc06ip50')
2013-02-23 18:28:34,532 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'acpi:PNP0C01:')
2013-02-23 18:28:34,532 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'pci:v00008086d00002C32sv00001458sd00005000bc06sc00i00')
2013-02-23 18:28:34,532 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'pci:v00008086d00003A36sv00001458sd00005004bc0Csc03i00')
2013-02-23 18:28:34,532 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'usb:v05ACp1006d9615dc09dsc00dp01ic09isc00ip00')
2013-02-23 18:28:34,532 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'pci:v00008086d00002C30sv00001458sd00005000bc06sc00i00')
2013-02-23 18:28:34,532 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'acpi:PNP0700:')
2013-02-23 18:28:34,532 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'pci:v00008086d00002C29sv00001458sd00005000bc06sc00i00')
2013-02-23 18:28:34,533 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'pci:v00008086d00003A39sv00001458sd00005004bc0Csc03i00')
2013-02-23 18:28:34,533 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'pci:v00008086d00002C22sv00001458sd00005000bc06sc00i00')
2013-02-23 18:28:34,533 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'pci:v00008086d00003423sv00000000sd00000000bc08sc00i00')
2013-02-23 18:28:34,533 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'pci:v00008086d0000342Esv00000000sd00000000bc08sc00i00')
2013-02-23 18:28:34,533 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-02-23 18:28:34,533 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'pci:v00008086d00003426sv00000000sd00000000bc08sc00i00')
2013-02-23 18:28:34,533 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'pci:v00008086d00002C19sv00001458sd00005000bc06sc00i00')
2013-02-23 18:28:34,533 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'platform:gpio_ich')
2013-02-23 18:28:34,533 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'pci:v00008086d00002C01sv00001458sd00005000bc06sc00i00')
2013-02-23 18:28:34,533 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfwD,')
2013-02-23 18:28:34,533 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'platform:coretemp')
2013-02-23 18:28:34,533 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'wmi:F6CB5C3C-9CAE-4EBD-B577-931EA32A2CC0')
2013-02-23 18:28:34,533 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'pci:v00008086d00003405sv00001458sd00005000bc06sc00i00')
2013-02-23 18:28:34,533 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'pci:v00008086d00002C1Csv00001458sd00005000bc06sc00i00')
2013-02-23 18:28:34,533 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'pci:v00008086d00002C31sv00001458sd00005000bc06sc00i00')
2013-02-23 18:28:34,533 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'acpi:PNP0C02:')
2013-02-23 18:28:34,533 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'pci:v00008086d00002C33sv00001458sd00005000bc06sc00i00')
2013-02-23 18:28:34,534 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip01')
2013-02-23 18:28:34,534 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,2,4,k110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,r0,1,6,8,am4,lsfw')
2013-02-23 18:28:34,534 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'acpi:PNP0200:')
2013-02-23 18:28:34,534 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2013-02-23 18:28:34,534 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'pci:v00008086d00003A34sv00001458sd00005004bc0Csc03i00')
2013-02-23 18:28:34,534 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001458sd0000E000bc02sc00i00')
2013-02-23 18:28:34,534 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2013-02-23 18:28:34,534 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'pci:v00008086d00003428sv00000000sd00000000bc08sc00i00')
2013-02-23 18:28:34,534 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'pci:v00008086d00002C2Bsv00001458sd00005000bc06sc00i00')
2013-02-23 18:28:34,534 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'platform:microcode')
2013-02-23 18:28:34,534 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'hid:b0003g0000v0000046Dp0000C52B')
2013-02-23 18:28:34,534 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'hid:b0003g0000v000005ACp00000220')
2013-02-23 18:28:34,534 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-02-23 18:28:34,534 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'input:b0003v05ACp0220e0111-e0,1,4,k71,72,73,A1,A3,A4,A5,ram4,lsfw')
2013-02-23 18:28:34,534 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'acpi:PNP0C04:')
2013-02-23 18:28:34,534 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'acpi:PNP0000:')
2013-02-23 18:28:34,535 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'pci:v00008086d00003422sv00000000sd00000000bc08sc00i00')
2013-02-23 18:28:34,535 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'pci:v00008086d00002C10sv00001458sd00005000bc06sc00i00')
2013-02-23 18:28:34,535 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'input:b0003v05ACp0220e0111-e0,1,4,11,14,k71,72,73,74,75,77,78,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8C,8E,96,98,9E,9F,A1,A3,A4,A5,A6,AD,B0,B1,B2,B3,B4,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,CC,E0,E1,E3,E4,E5,E6,F0,1D0,ram4,l0,1,2,3,4,sfw')
2013-02-23 18:28:34,535 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'pci:v00008086d00002C28sv00001458sd00005000bc06sc00i00')
2013-02-23 18:28:34,535 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'pci:v00008086d00003A38sv00001458sd00005004bc0Csc03i00')
2013-02-23 18:28:34,535 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'pci:v00008086d00003A3Esv00001458sd0000A002bc04sc03i00')
2013-02-23 18:28:34,535 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'acpi:PNP0100:')
2013-02-23 18:28:34,535 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip02')
2013-02-23 18:28:34,535 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'pci:v00008086d00002C18sv00001458sd00005000bc06sc00i00')
2013-02-23 18:28:34,535 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'pci:v00008086d00002C21sv00001458sd00005000bc06sc00i00')
2013-02-23 18:28:34,535 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'pci:v00008086d00003A30sv00001458sd00005001bc0Csc05i00')
2013-02-23 18:28:34,535 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'usb:v1D6Bp0002d0305dc09dsc00dp00ic09isc00ip00')
2013-02-23 18:28:34,535 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'pci:v00008086d00003425sv00000000sd00000000bc08sc00i00')
2013-02-23 18:28:34,535 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2013-02-23 18:28:34,535 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x30b2908> about HardwareID('modalias', 'pci:v0000104Cd00008024sv00001458sd00001000bc0Csc00i10')
2013-02-23 18:28:34,551 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-02-23 18:28:34,574 DEBUG: fglrx.enabled(fglrx_experimental_9): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2013-02-23 18:28:34,574 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2013-02-23 18:28:34,598 DEBUG: fglrx.enabled(fglrx_updates): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2013-02-23 18:28:34,598 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2013-02-23 18:28:34,673 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-02-23 18:28:34,687 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-02-23 18:28:34,706 DEBUG: fglrx.enabled(fglrx_experimental_9): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2013-02-23 18:28:34,707 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2013-02-23 18:28:34,728 DEBUG: fglrx.enabled(fglrx_updates): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2013-02-23 18:28:34,729 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2013-02-23 18:28:37,150 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-02-23 18:28:40,352 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2013-02-23 18:28:40,353 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2013-02-23 18:28:40,369 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-02-23 18:29:07,703 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-02-23 18:29:07,728 DEBUG: fglrx.enabled(fglrx_experimental_9): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2013-02-23 18:29:07,728 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2013-02-23 18:29:07,752 DEBUG: fglrx.enabled(fglrx_updates): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2013-02-23 18:29:07,752 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2013-02-23 18:29:07,837 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-02-23 18:29:07,862 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-02-23 18:29:07,882 DEBUG: fglrx.enabled(fglrx_experimental_9): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2013-02-23 18:29:07,882 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2013-02-23 18:29:07,904 DEBUG: fglrx.enabled(fglrx_updates): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2013-02-23 18:29:07,904 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2013-02-23 18:29:12,832 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-02-23 18:29:13,044 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2013-02-23 18:29:13,045 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2013-02-23 18:29:13,061 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted

```

---

### Post by westie457 on 2013-02-23
I missed something simple, I think.

Let us try a slightly different approach. in a terminal run ```
sudo apt-get purge bcmwl-kernel source

sudo apt-get clean

sudo apt-get update

sudo apt-get install --reinstall bcmwl-kernel-source
```

This should remove the old driver (the one downloaded by you) 

Then the repositories get realigned

Finally reinstall the newest version.

Now remove the cable and reboot your system.

Has this worked?

Thank you.

---

### Post by tomster2300 on 2013-02-23
> **westie457 said:**
> I missed something simple, I think.

Let us try a slightly different approach. in a terminal run ```
sudo apt-get purge bcmwl-kernel source

sudo apt-get clean

sudo apt-get update

sudo apt-get install --reinstall bcmwl-kernel-source
```

This should remove the old driver (the one downloaded by you) 

Then the repositories get realigned

Finally reinstall the newest version.

Now remove the cable and reboot your system.

Has this worked?

Thank you.

I just tried and that did not work.  I get the Wireless Network -disconnected in my network preferences, but it never shows any wireless networks, even when I try to manually enter them.

I am now getting another system error after trying to use wifi (see attached screenshot).

---

### Post by Hadaka on 2013-02-23
Hi, I noticed the module ssb and wl in your script file, I dont see it in the lsmod
but,it "may" be part of the issue. Here is your lspci report
```
 06:01.0 Network controller [0280]: Broadcom Corporation BCM4321 802.11b/g/n [14e4:4329] (rev 01)
    Subsystem: Netgear WN311B RangeMax Next 270 Mbps Wireless PCI Adapter [1385:7d00]
    Kernel driver in use: wl
    Kernel modules: wl, ssb
```
please post the output of..
```
lspci -nnk | grep -iA3 net 
```
*if...ssb is still there westie can guide you to backlist it.
thanks

---

### Post by tomster2300 on 2013-02-23
> **Hadaka said:**
> Hi, I noticed the module ssb and wl in your script file, I dont see it in the lsmod
but,it "may" be part of the issue. Here is your lspci report
```
 06:01.0 Network controller [0280]: Broadcom Corporation BCM4321 802.11b/g/n [14e4:4329] (rev 01)
    Subsystem: Netgear WN311B RangeMax Next 270 Mbps Wireless PCI Adapter [1385:7d00]
    Kernel driver in use: wl
    Kernel modules: wl, ssb
```
please post the output of..
```
lspci -nnk | grep -iA3 net 
```
*if...ssb is still there westie can guide you to backlist it.
thanks

Sounds good to me.  Here is the output:

```

05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:e000]
	Kernel driver in use: r8169
	Kernel modules: r8169
06:01.0 Network controller [0280]: Broadcom Corporation BCM4321 802.11b/g/n [14e4:4329] (rev 01)
	Subsystem: Netgear WN311B RangeMax Next 270 Mbps Wireless PCI Adapter [1385:7d00]
	Kernel driver in use: wl
	Kernel modules: wl, ssb
06:06.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link) [104c:8024]
tmcgahee@tmcgahee-EX58-UD3R:~$ 


```

Thanks!

---

### Post by westie457 on 2013-02-23
Okay shall we try ```
sudo rmmod wl

sudo rmmod ssb

sudo modprobe wl
```

Don't worry about errors with the first 2 commands.

The last one should return to a blank command prompt.

Unplug the cable and wait a few seconds for the system to notice the driver changes.

Any networks available now?

If yes then ```
echo "blacklist ssb" >> /etc/modprobe.d/blacklist.conf
``` any errors rerun the command with sudo.

@ Hadaka
Thanks for the vote of confidence. Until now I have never had to blacklist anything on this Forum.
Hopefully this is correct.

---

### Post by tomster2300 on 2013-02-23
> **westie457 said:**
> Okay shall we try ```
sudo rmmod wl

sudo rmmod ssb

sudo modprobe wl
```

Don't worry about errors with the first 2 commands.

The last one should return to a blank command prompt.

Unplug the cable and wait a few seconds for the system to notice the driver changes.

Any networks available now?

If yes then ```
echo "blacklist ssb" >> /etc/modprobe.d/blacklist.conf
``` any errors rerun the command with sudo.

@ Hadaka
Thanks for the vote of confidence. Until now I have never had to blacklist anything on this Forum.
Hopefully this is correct.

Unfortunately it did not. Here is is my terminal output:

```

tmcgahee@tmcgahee-EX58-UD3R:~$ sudo rmmod wl
[sudo] password for tmcgahee: 
tmcgahee@tmcgahee-EX58-UD3R:~$ sudo rmmod ssb
ERROR: Module ssb does not exist in /proc/modules
tmcgahee@tmcgahee-EX58-UD3R:~$ sudo modprobe wl
tmcgahee@tmcgahee-EX58-UD3R:~$ 

```

EDIT: Should I reboot and try again, or should the effects have been immediate like you said?

Not sure if it helps or not, but this is my wireless card for reference: [http://www.newegg.com/Product/Product.aspx?Item=N82E16833122163](http://www.newegg.com/Product/Product.aspx?Item=N82E16833122163)

---

### Post by westie457 on 2013-02-23
Try the blacklist command then reboot.

I am going have sleep on this very soon. The extra strong coffee is wearing off.

Will have another look in a while.

Un plug the cable as well.

---

### Post by Hadaka on 2013-02-23
@westie
blacklist command

```
sudo gedit /etc/modprobe.d/blacklist.conf 
```

add ....    blacklist ssb      to the last line in the file
proof read..save..close

---

### Post by tomster2300 on 2013-02-23
> **Hadaka said:**
> @westie
blacklist command

```
sudo gedit /etc/modprobe.d/blacklist.conf 
```

add ....    blacklist ssb      to the last line in the file
proof read..save..close

I added it, rebooted and nothing changed.  

Thanks for all the help guys!

What next?

---

### Post by Hadaka on 2013-02-23
give this a try

```
sudo apt-get install linux-headers-generic
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
 
```

after,without booting,unplug the cable and see if
there are any changes

---

### Post by tomster2300 on 2013-02-23
> **Hadaka said:**
> give this a try

```
sudo apt-get install linux-headers-generic
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
 
```

after,without booting,unplug the cable and see if
there are any changes

Doesn't look like anything changed.  Here is the terminal output:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
tmcgahee@tmcgahee-EX58-UD3R:~$ sudo apt-get install --reinstall bcmwl-kernel-source 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/1,344 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 170081 files and directories currently installed.)
Preparing to replace bcmwl-kernel-source 6.20.155.1+bdcom-0ubuntu0.0.1 (using .../bcmwl-kernel-source_6.20.155.1+bdcom-0ubuntu0.0.1_amd64.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement bcmwl-kernel-source ...
Setting up bcmwl-kernel-source (6.20.155.1+bdcom-0ubuntu0.0.1) ...
Loading new bcmwl-6.20.155.1+bdcom DKMS files...
Building only for 3.5.0-25-generic
Building for architecture x86_64
Building initial module for 3.5.0-25-generic
Done.

wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.5.0-25-generic/updates/dkms/

depmod....

DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.5.0-25-generic
tmcgahee@tmcgahee-EX58-UD3R:~$ sudo modprobe wl
tmcgahee@tmcgahee-EX58-UD3R:~$ 

```

---

### Post by Hadaka on 2013-02-23
Hi, check to see i the Enable Wireless is checked in the drop
down menu from the wireless icon, if yes, boot and see if
there are any changes.

---

### Post by chili555 on 2013-02-23
Just a casual observer here, looking in to see if I can help in any way and hoping not to step on toes. May I see:```
rfkill list all
dmesg | grep wl
lsmod | grep -e brcmsmac -e b43 -e wl
```I think bcmwl-kernel-source is correct for your device. Let's try to see why it isn't taking off like a John Force dragster.

[http://www.allfordmustangs.com/photopost/data/3268/John_Force.jpg](http://www.allfordmustangs.com/photopost/data/3268/John_Force.jpg)

---

### Post by Bucky Ball on 2013-02-23
> **chili555 said:**
> Let's try to see why it isn't taking off like a John Force dragster.

+1. LOL, indeed, and give the output of chilli's suggestions. ;)

---

### Post by tomster2300 on 2013-02-25
> **chili555 said:**
> Just a casual observer here, looking in to see if I can help in any way and hoping not to step on toes. May I see:```
rfkill list all
dmesg | grep wl
lsmod | grep -e brcmsmac -e b43 -e wl
```I think bcmwl-kernel-source is correct for your device. Let's try to see why it isn't taking off like a John Force dragster.

[http://www.allfordmustangs.com/photopost/data/3268/John_Force.jpg](http://www.allfordmustangs.com/photopost/data/3268/John_Force.jpg)

Apologies for the delay, I've been sick the past couple of days.  Here is the output for the above:

```
tmcgahee@tmcgahee-EX58-UD3R:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
tmcgahee@tmcgahee-EX58-UD3R:~$ dmesg | grep wl
[    4.209738] INFO @wl_cfg80211_attach : Registered CFG80211 phy
tmcgahee@tmcgahee-EX58-UD3R:~$ lsmod | grep -e brcmsmac -e b43 -e wl
wl                   3074942  0 
cfg80211              208382  1 wl
lib80211               14382  2 lib80211_crypt_tkip,wl
tmcgahee@tmcgahee-EX58-UD3R:~$ 


```

---

### Post by chili555 on 2013-02-25
Ahhh! My favorite kind of problem. We have gas, air and spark but it just doesn't start. Let's dig deeper. Detach the ethernet and run:```
cat /var/log/syslog | grep -e wl -e eth1 -e etwork | tail -n 20
sudo iwlist eth1 scan
```

---

### Post by tomster2300 on 2013-02-25
> **chili555 said:**
> Ahhh! My favorite kind of problem. We have gas, air and spark but it just doesn't start. Let's dig deeper. Detach the ethernet and run:```
cat /var/log/syslog | grep -e wl -e eth1 -e etwork | tail -n 20
sudo iwlist eth1 scan
```

You know that's going to be MY car one day!  (Hopefully not soon though!)

Output:

```
tmcgahee@tmcgahee-EX58-UD3R:~$ cat /var/log/syslog | grep -e wl -e eth1 -e etwork | tail -n 20
Feb 25 10:59:14 tmcgahee-EX58-UD3R NetworkManager[1342]: <info>   hostname 'tmcgahee-EX58-UD3R'
Feb 25 10:59:14 tmcgahee-EX58-UD3R NetworkManager[1342]: <info>   nameserver '192.168.1.1'
Feb 25 10:59:14 tmcgahee-EX58-UD3R NetworkManager[1342]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Feb 25 10:59:14 tmcgahee-EX58-UD3R NetworkManager[1342]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...
Feb 25 10:59:15 tmcgahee-EX58-UD3R NetworkManager[1342]: <info> DNS: starting dnsmasq...
Feb 25 10:59:15 tmcgahee-EX58-UD3R NetworkManager[1342]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
Feb 25 10:59:15 tmcgahee-EX58-UD3R NetworkManager[1342]: <info> (eth0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Feb 25 10:59:15 tmcgahee-EX58-UD3R NetworkManager[1342]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Feb 25 10:59:15 tmcgahee-EX58-UD3R NetworkManager[1342]: <info> Activation (eth0) successful, device activated.
Feb 25 10:59:15 tmcgahee-EX58-UD3R NetworkManager[1342]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
Feb 25 10:59:31 tmcgahee-EX58-UD3R NetworkManager[1342]: <info> (eth0): IP6 addrconf timed out or failed.
Feb 25 10:59:31 tmcgahee-EX58-UD3R NetworkManager[1342]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Feb 25 10:59:31 tmcgahee-EX58-UD3R NetworkManager[1342]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Feb 25 10:59:31 tmcgahee-EX58-UD3R NetworkManager[1342]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Feb 25 11:47:10 tmcgahee-EX58-UD3R NetworkManager[1342]: <info> (eth0): carrier now OFF (device state 100, deferring action for 4 seconds)
Feb 25 11:47:14 tmcgahee-EX58-UD3R NetworkManager[1342]: <info> (eth0): device state change: activated -> unavailable (reason 'carrier-changed') [100 20 40]
Feb 25 11:47:14 tmcgahee-EX58-UD3R NetworkManager[1342]: <info> (eth0): deactivating device (reason 'carrier-changed') [40]
Feb 25 11:47:15 tmcgahee-EX58-UD3R NetworkManager[1342]: <info> (eth0): canceled DHCP transaction, DHCP client pid 2510
Feb 25 11:47:15 tmcgahee-EX58-UD3R NetworkManager[1342]: <info> DNS: starting dnsmasq...
Feb 25 11:47:15 tmcgahee-EX58-UD3R NetworkManager[1342]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
tmcgahee@tmcgahee-EX58-UD3R:~$ sudo iwlist eth1 scan
eth1      No scan results

tmcgahee@tmcgahee-EX58-UD3R:~$ 

```

---

### Post by chili555 on 2013-02-25
In your syslog, we see perfect connection for eth0, the wired ethernet. Let's narrow the search:```
nm-tool
cat /var/log/syslog | grep -i -e eth1 -e wl | tail -n20
iwconfig
cat /etc/network/interfaces
```

---

### Post by tomster2300 on 2013-02-25
> **chili555 said:**
> In your syslog, we see perfect connection for eth0, the wired ethernet. Let's narrow the search:```
nm-tool
cat /var/log/syslog | grep -i -e eth1 -e wl | tail -n20
iwconfig
cat /etc/network/interfaces
```

Yep, wired internet works perfectly for me.  

Output:

```
tmcgahee@tmcgahee-EX58-UD3R:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             disconnected
  Default:           no
  HW Address:        00:24:B2:B3:D5:2C

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        00:24:1D:1F:5C:10

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         off


tmcgahee@tmcgahee-EX58-UD3R:~$ cat /var/log/syslog | grep -i -e eth1 -e wl | tail -n20
Feb 25 10:56:25 tmcgahee-EX58-UD3R NetworkManager[1342]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:06:01.0/net/eth1, iface: eth1)
Feb 25 10:56:25 tmcgahee-EX58-UD3R NetworkManager[1342]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:06:01.0/net/eth1, iface: eth1): no ifupdown configuration found.
Feb 25 10:56:25 tmcgahee-EX58-UD3R NetworkManager[1342]: <info> found WiFi radio killswitch rfkill1 (at /sys/devices/pci0000:00/0000:00:1e.0/0000:06:01.0/net/eth1/rfkill1) (driver (unknown))
Feb 25 10:56:25 tmcgahee-EX58-UD3R NetworkManager[1342]: <info> (eth1): using nl80211 for WiFi device control
Feb 25 10:56:25 tmcgahee-EX58-UD3R NetworkManager[1342]: <error> [1361807785.990748] [nm-device-wifi.c:2591] real_update_permanent_hw_address(): (eth1): unable to read permanent MAC address (error 0)
Feb 25 10:56:25 tmcgahee-EX58-UD3R NetworkManager[1342]: <info> (eth1): new 802.11 WiFi device (driver: 'wl' ifindex: 3)
Feb 25 10:56:25 tmcgahee-EX58-UD3R NetworkManager[1342]: <info> (eth1): exported as /org/freedesktop/NetworkManager/Devices/1
Feb 25 10:56:25 tmcgahee-EX58-UD3R NetworkManager[1342]: <info> (eth1): now managed
Feb 25 10:56:25 tmcgahee-EX58-UD3R NetworkManager[1342]: <info> (eth1): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Feb 25 10:56:25 tmcgahee-EX58-UD3R NetworkManager[1342]: <info> (eth1): bringing up device.
Feb 25 10:56:25 tmcgahee-EX58-UD3R NetworkManager[1342]: <info> (eth1): preparing device.
Feb 25 10:56:25 tmcgahee-EX58-UD3R NetworkManager[1342]: <info> (eth1): deactivating device (reason 'managed') [2]
Feb 25 10:56:26 tmcgahee-EX58-UD3R NetworkManager[1342]: <info> (eth1): supplicant interface state: starting -> ready
Feb 25 10:56:26 tmcgahee-EX58-UD3R NetworkManager[1342]: <info> (eth1): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Feb 25 10:56:26 tmcgahee-EX58-UD3R NetworkManager[1342]: <info> (eth1): supplicant interface state: ready -> inactive
Feb 25 10:56:27 tmcgahee-EX58-UD3R avahi-daemon[1402]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::224:b2ff:feb3:d52c.
Feb 25 10:56:27 tmcgahee-EX58-UD3R avahi-daemon[1402]: New relevant interface eth1.IPv6 for mDNS.
Feb 25 10:56:27 tmcgahee-EX58-UD3R avahi-daemon[1402]: Registering new address record for fe80::224:b2ff:feb3:d52c on eth1.*.
Feb 25 11:58:08 tmcgahee-EX58-UD3R kernel: [ 3703.097438] ERROR @wl_dev_intvar_get : error (-1)
Feb 25 11:58:08 tmcgahee-EX58-UD3R kernel: [ 3703.097443] ERROR @wl_cfg80211_get_tx_power : error (-1)
tmcgahee@tmcgahee-EX58-UD3R:~$ iwconfig
eth0      no wireless extensions.

eth1      IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.

tmcgahee@tmcgahee-EX58-UD3R:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

tmcgahee@tmcgahee-EX58-UD3R:~$ 

```

---

### Post by tomster2300 on 2013-02-25
I'm unplugging the ethernet cord when doing all of these terminal commands. Is that correct, or should I be keeping it in?

---

### Post by chili555 on 2013-02-25
Hello!>  <error> [1361807785.990748] [nm-device-wifi.c:2591] real_update_permanent_hw_address(): (eth1): unable to read permanent MAC address (error 0)
[ 3703.097438] ERROR @wl_dev_intvar_get : error (-1)
[ 3703.097443] ERROR @wl_cfg80211_get_tx_power : error (-1)Let's try a thing or two. First the easy ones. Please disable IPv6 in Network Manager and the shut down completely and boot up and show us:```
cat /var/log/syslog | grep -i -e eth1 -e wl | tail -n20
```My suggestions get harder from here, so cross your fingers and toes.

---

### Post by chili555 on 2013-02-25
> **tomster2300 said:**
> I'm unplugging the ethernet cord when doing all of these terminal commands. Is that correct, or should I be keeping it in?For these, it may remain plugged in. When we check to see what Network Manage is doing as you try to connect with wireless, we'll want to disconnect the ethernet cable. Until we get the errors out of the way and scan, we're not ready to connect.

---

### Post by tomster2300 on 2013-02-25
> **chili555 said:**
> Hello!Let's try a thing or two. First the easy ones. Please disable IPv6 in Network Manager and the shut down completely and boot up and show us:```
cat /var/log/syslog | grep -i -e eth1 -e wl | tail -n20
```My suggestions get harder from here, so cross your fingers and toes.

Quick question - I do not have a wireless connection listed here in the attached screenshot.  Should I manually add one first?

---

### Post by chili555 on 2013-02-25
> **tomster2300 said:**
> Quick question - I do not have a wireless connection listed here in the attached screenshot.  Should I manually add one first?No. Just select the IPv6 tab and select 'Ignore.' Save and close.

---

### Post by tomster2300 on 2013-02-25
> **chili555 said:**
> No. Just select the IPv6 tab and select 'Ignore.' Save and close.

Problem is I don't believe I can change the IP6 options until I create a wireless entry.

I could be looking at this incorrectly - can you give me steps on how to open the network manager?

---

### Post by tomster2300 on 2013-02-25
So I just tried this and rebooted and it didn't work:  [http://www.noobslab.com/2012/05/disable-ipv6-if-your-internet-is.html](http://www.noobslab.com/2012/05/disable-ipv6-if-your-internet-is.html)

Is that kind of the same thing you were asking me to do?

---

### Post by chili555 on 2013-02-25
> **tomster2300 said:**
> So I just tried this and rebooted and it didn't work:  [http://www.noobslab.com/2012/05/disable-ipv6-if-your-internet-is.html](http://www.noobslab.com/2012/05/disable-ipv6-if-your-internet-is.html)

Is that kind of the same thing you were asking me to do?Yes, exactly. Are there any changes in syslog?```
cat /var/log/syslog | grep -i -e eth1 -e wl | tail -n20
```Thanks.

---

### Post by Hadaka on 2013-02-25
Hi, following along here, please verify your
code to disable ipv6 got written to the file ok.
please do...

```
cat [COLOR=red]/etc/sysctl.conf[/COLOR] 
```

thanks.

---

### Post by tomster2300 on 2013-02-26
Here's to both. Thanks again for all the help thus far!

> **chili555 said:**
> Yes, exactly. Are there any changes in syslog?```
cat /var/log/syslog | grep -i -e eth1 -e wl | tail -n20
```Thanks.

```
tmcgahee@tmcgahee-EX58-UD3R:~$ cat /var/log/syslog | grep -i -e eth1 -e wl | tail -n20
Feb 26 07:54:37 tmcgahee-EX58-UD3R NetworkManager[1246]: <info> (eth1): supplicant interface state: starting -> ready
Feb 26 07:54:37 tmcgahee-EX58-UD3R NetworkManager[1246]: <info> (eth1): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Feb 26 07:54:37 tmcgahee-EX58-UD3R NetworkManager[1246]: <info> (eth1): supplicant interface state: ready -> inactive
Feb 26 07:57:09 tmcgahee-EX58-UD3R kernel: [    3.989814] INFO @wl_cfg80211_attach : Registered CFG80211 phy
Feb 26 07:57:09 tmcgahee-EX58-UD3R kernel: [    4.017869] eth1: Broadcom BCM4329 802.11 Hybrid Wireless Controller 6.20.155.1 (r326264)
Feb 26 07:57:09 tmcgahee-EX58-UD3R NetworkManager[1246]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:06:01.0/net/eth1, iface: eth1)
Feb 26 07:57:09 tmcgahee-EX58-UD3R NetworkManager[1246]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:06:01.0/net/eth1, iface: eth1): no ifupdown configuration found.
Feb 26 07:57:09 tmcgahee-EX58-UD3R NetworkManager[1246]: <info> found WiFi radio killswitch rfkill1 (at /sys/devices/pci0000:00/0000:00:1e.0/0000:06:01.0/net/eth1/rfkill1) (driver (unknown))
Feb 26 07:57:09 tmcgahee-EX58-UD3R NetworkManager[1246]: <info> (eth1): using nl80211 for WiFi device control
Feb 26 07:57:09 tmcgahee-EX58-UD3R NetworkManager[1246]: <error> [1361883429.410183] [nm-device-wifi.c:2591] real_update_permanent_hw_address(): (eth1): unable to read permanent MAC address (error 0)
Feb 26 07:57:09 tmcgahee-EX58-UD3R NetworkManager[1246]: <info> (eth1): new 802.11 WiFi device (driver: 'wl' ifindex: 3)
Feb 26 07:57:09 tmcgahee-EX58-UD3R NetworkManager[1246]: <info> (eth1): exported as /org/freedesktop/NetworkManager/Devices/1
Feb 26 07:57:09 tmcgahee-EX58-UD3R NetworkManager[1246]: <info> (eth1): now managed
Feb 26 07:57:09 tmcgahee-EX58-UD3R NetworkManager[1246]: <info> (eth1): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Feb 26 07:57:09 tmcgahee-EX58-UD3R NetworkManager[1246]: <info> (eth1): bringing up device.
Feb 26 07:57:09 tmcgahee-EX58-UD3R NetworkManager[1246]: <info> (eth1): preparing device.
Feb 26 07:57:09 tmcgahee-EX58-UD3R NetworkManager[1246]: <info> (eth1): deactivating device (reason 'managed') [2]
Feb 26 07:57:09 tmcgahee-EX58-UD3R NetworkManager[1246]: <info> (eth1): supplicant interface state: starting -> ready
Feb 26 07:57:09 tmcgahee-EX58-UD3R NetworkManager[1246]: <info> (eth1): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Feb 26 07:57:09 tmcgahee-EX58-UD3R NetworkManager[1246]: <info> (eth1): supplicant interface state: ready -> inactive
```

> **Hadaka said:**
> Hi, following along here, please verify your
code to disable ipv6 got written to the file ok.
please do...

```
cat [COLOR=red]/etc/sysctl.conf[/COLOR] 
```

thanks.

```
tmcgahee@tmcgahee-EX58-UD3R:~$ cat /etc/sysctl.conf
#
# /etc/sysctl.conf - Configuration file for setting system variables
# See /etc/sysctl.d/ for additional system variables
# See sysctl.conf (5) for information.
#

#kernel.domainname = example.com

# Uncomment the following to stop low-level messages on console
#kernel.printk = 3 4 1 3

##############################################################3
# Functions previously found in netbase
#

# Uncomment the next two lines to enable Spoof protection (reverse-path filter)
# Turn on Source Address Verification in all interfaces to
# prevent some spoofing attacks
#net.ipv4.conf.default.rp_filter=1
#net.ipv4.conf.all.rp_filter=1

# Uncomment the next line to enable TCP/IP SYN cookies
# See http://lwn.net/Articles/277146/
# Note: This may impact IPv6 TCP sessions too
#net.ipv4.tcp_syncookies=1

# Uncomment the next line to enable packet forwarding for IPv4
#net.ipv4.ip_forward=1

# Uncomment the next line to enable packet forwarding for IPv6
#  Enabling this option disables Stateless Address Autoconfiguration
#  based on Router Advertisements for this host
#net.ipv6.conf.all.forwarding=1


###################################################################
# Additional settings - these settings can improve the network
# security of the host and prevent against some network attacks
# including spoofing attacks and man in the middle attacks through
# redirection. Some network environments, however, require that these
# settings are disabled so review and enable them as needed.
#
# Do not accept ICMP redirects (prevent MITM attacks)
#net.ipv4.conf.all.accept_redirects = 0
#net.ipv6.conf.all.accept_redirects = 0
# _or_
# Accept ICMP redirects only for gateways listed in our default
# gateway list (enabled by default)
# net.ipv4.conf.all.secure_redirects = 1
#
# Do not send ICMP redirects (we are not a router)
#net.ipv4.conf.all.send_redirects = 0
#
# Do not accept IP source route packets (we are not a router)
#net.ipv4.conf.all.accept_source_route = 0
#net.ipv6.conf.all.accept_source_route = 0
#
# Log Martian Packets
#net.ipv4.conf.all.log_martians = 1
#

net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1

tmcgahee@tmcgahee-EX58-UD3R:~$ 
```

---

### Post by Hadaka on 2013-02-26
Hi, is your router and modem one unit?
or do you have  cable------modem-------router----- computer?
*IF NOT one unit...
plug directly into to modem, bypassing the router
and see if the wired connection.....connects.

---

### Post by tomster2300 on 2013-02-26
> **Hadaka said:**
> Hi, is your router and modem one unit?
or do you have  cable------modem-------router----- computer?
*IF NOT one unit...
plug directly into to modem, bypassing the router
and see if the wired connection.....connects.

I have a cable modem -> router -> computer setup.

I dualboot Windows 7 on this computer and the wifi adapter works fine with the Windows drivers, so I don't believe it's a router issue.  

The wired connection has worked throughout - do I still need to test it?

---

### Post by Hadaka on 2013-02-26
nm

---

### Post by Hadaka on 2013-02-26
Hi, you are correct no need to direct connect
please try this, 

```
sudo sysctl net.ipv6.conf.default.accept_ra=0
sudo sysctl net.ipv6.conf.all.accept_ra=0
sudo sysctl net.ipv6.conf.eth1.accept_ra=0 
```this turns off ipv6 requets from the router.

thanks.

---

