---
title: "Dell E1505 post-package-upgrade wireless radio failure"
date: 2011-10-02
forum: Networking &amp; Wireless
---

### Post by ianthealy on 2011-10-02
I have a Dell Inspiron E1705 which has been running Natty for several months without problems. This morning I did a regular package update and since then, I have not been able to get my wireless radio to turn on. This was not a problem prior to the update. I am using a wired connection right now.

I'm relatively new to Ubuntu, so most of what I've learned about it has been due to Google and using the forums here, so bear with me if I'm being boneheaded about something.

Checking the "Additional Drivers" reveals that my Broadcom STA wireless driver is NOT activated. However, when I click "Activate", my Wired connection immediately disconnects and I get an error message:

> Sorry, installation of this driver failed.

Please have a look at the log file for details: /var/log/jockey.logWhen I click on Close, the wired connection immediately re-establishes.

In the Synaptic Package manager, I've tried uninstalling and resintalling "bcmwl-kernel-source", which I've seen was suggested in other forum posts related to this problem, but that has not solved my problem. My wireless radio remains off.

Using "rfkill list all" confirms that my dell-wifi Wireless lan is not Soft blocked or Hard blocked.

I'm looking for suggestions on how to get the radio to turn back on. I'm not sure what information I need to provide to help so let me know what I need to include.

Thanks!

---

### Post by praseodym on 2011-10-02
Hi,

please show the following terminal outputs:

```
uname -a
lspci -nnk | grep -iA2 net
lsmod
iwconfig
cat /var/lib/NetworkManager/NetworkManager.state
```

---

### Post by ianthealy on 2011-10-02
uname-a
```
Linux ubuntu 2.6.35-27-generic #48-Ubuntu SMP Tue Feb 22 20:25:46 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
```lspci -nnk | grep -iA2 net
```
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
    Subsystem: Dell Inspiron 9400 Laptop [1028:01cd]
    Kernel driver in use: b44
--
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4321 802.11a/b/g/n [14e4:4328] (rev 01)
    Subsystem: Dell Wireless 1500 Draft 802.11n WLAN Mini-Card [1028:0009]
    Kernel driver in use: b43-pci-bridge

```lsmod
```
Module                  Size  Used by
b44                    31306  0 
ssb                    46201  1 b44
mii                     5261  1 b44
parport_pc             30086  0 
ppdev                   6804  0 
snd_hda_codec_idt      64699  1 
joydev                 11395  0 
btusb                  12929  0 
usbhid                 42030  0 
hid                    84710  1 usbhid
snd_hda_intel          26147  2 
snd_hda_codec         100951  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               6660  1 snd_hda_codec
snd_pcm                89104  2 snd_hda_intel,snd_hda_codec
bluetooth              59245  1 btusb
i915                  334721  4 
snd_seq_midi            5932  0 
snd_rawmidi            22207  1 snd_seq_midi
snd_seq_midi_event      7291  1 snd_seq_midi
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
snd_timer              23850  2 snd_pcm,snd_seq
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         32836  1 i915
drm                   206198  4 i915,drm_kms_helper
dell_wmi_aio            1682  0 
sparse_keymap           3837  1 dell_wmi_aio
i2c_algo_bit            6208  1 i915
dell_laptop             6722  0 
dell_wmi                3372  0 
r852                   11348  0 
sm_common               4441  1 r852
snd                    64181  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
nand                   38430  2 r852,sm_common
nand_ids                4443  1 nand
nand_ecc                4406  1 nand
coretemp                6442  0 
dcdbas                  6910  1 dell_laptop
mtd                    21479  2 sm_common,nand
psmouse                62080  0 
serio_raw               4910  0 
soundcore               1240  1 snd
video                  22176  1 i915
intel_agp              32334  2 i915
output                  2527  1 video
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
lp                     10201  0 
parport                37032  3 parport_pc,ppdev,lp
sdhci_pci               7765  0 
firewire_ohci          24839  0 
firewire_core          54327  1 firewire_ohci
crc_itu_t               1739  1 firewire_core
sdhci                  18400  1 sdhci_pci
led_class               3393  1 sdhci

```iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

```cat /var/lib/NetworkManager/NetworkManager.state
```
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

```

---

### Post by praseodym on 2011-10-02
Install the packages **dkms**, **patch**, **fakeroot**, and **bcmwl-kernel-source** by adding the installation medium to your software sources. After that:

```
sudo depmod -a
```
Now you should be able to activate the driver.

---

### Post by ianthealy on 2011-10-02
I did this:
```
$ sudo apt-get install dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
dkms is already the newest version.
dkms set to manually installed.
The following packages were automatically installed and are no longer required:
  nspluginwrapper liboverlay-scrollbar-0.1-0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
$ sudo apt-get install patch
Reading package lists... Done
Building dependency tree       
Reading state information... Done
patch is already the newest version.
patch set to manually installed.
The following packages were automatically installed and are no longer required:
  nspluginwrapper liboverlay-scrollbar-0.1-0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
$ sudo apt-get install fakeroot
Reading package lists... Done
Building dependency tree       
Reading state information... Done
fakeroot is already the newest version.
fakeroot set to manually installed.
The following packages were automatically installed and are no longer required:
  nspluginwrapper liboverlay-scrollbar-0.1-0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
$ sudo apt-get install bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
bcmwl-kernel-source is already the newest version.
The following packages were automatically installed and are no longer required:
  nspluginwrapper liboverlay-scrollbar-0.1-0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
$ sudo depmod -a
$ 

```Then I opened Additional Drivers from the System menu. The Broadcom STA wireless driver was still not activated. When I clicked Activate, my Wired connection immediately disconnected and the driver installation failed.

Is there a way to completely uninstall the driver at a fundamental level and then do a fresh install, maybe?

---

### Post by praseodym on 2011-10-02
Try

```
sudo apt-get install --reinstall dkms patch fakeroot bcmwl-kernel-source
sudo depmod -a
```

---

### Post by ianthealy on 2011-10-02
I tried this:
```
$ sudo apt-get install --reinstall dkms patch fakeroot bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  nspluginwrapper liboverlay-scrollbar-0.1-0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 4 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/1,448 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 234416 files and directories currently installed.)
Preparing to replace bcmwl-kernel-source 5.100.82.38+bdcom-0ubuntu3.2 (using .../bcmwl-kernel-source_5.100.82.38+bdcom-0ubuntu3.2_amd64.deb) ...
Removing all DKMS Modules (1)
Done.
Unpacking replacement bcmwl-kernel-source ...
Preparing to replace dkms 2.1.1.2-5ubuntu1 (using .../dkms_2.1.1.2-5ubuntu1_all.deb) ...
Unpacking replacement dkms ...
Preparing to replace fakeroot 1.14.4-1ubuntu1 (using .../fakeroot_1.14.4-1ubuntu1_amd64.deb) ...
Unpacking replacement fakeroot ...
Preparing to replace patch 2.6-3 (using .../archives/patch_2.6-3_amd64.deb) ...
Unpacking replacement patch ...
Processing triggers for man-db ...
Setting up fakeroot (1.14.4-1ubuntu1) ...
Setting up patch (2.6-3) ...
Setting up dkms (2.1.1.2-5ubuntu1) ...
Setting up bcmwl-kernel-source (5.100.82.38+bdcom-0ubuntu3.2) ...
Loading new bcmwl-5.100.82.38+bdcom DKMS files...
Building for 2.6.35-27-generic and 2.6.38-11-generic
Building for architecture x86_64
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
Building initial module for 2.6.38-11-generic
Done.

wl.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.38-11-generic/updates/dkms/

depmod....

DKMS: install Completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.38-11-generic
$ sudo depmod -a

```Nothing has changed. The Wired connection still immediately disconnects when I attempt to activate the driver (and get the error message to check /var/log/jockey.log).

I opened /var/log/jockey.log and this is what it reports (warning: long, and I don't know what specifically pertains to the problem I'm having):
```
2011-10-02 17:29:28,843 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x18887a0>
2011-10-02 17:29:30,549 DEBUG: reading modalias file /lib/modules/2.6.35-27-generic/modules.alias
2011-10-02 17:29:30,657 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2011-10-02 17:29:30,657 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-10-02 17:29:30,691 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2011-10-02 17:29:30,708 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2011-10-02 17:29:30,712 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2011-10-02 17:29:30,712 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2011-10-02 17:29:30,732 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2011-10-02 17:29:30,732 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2011-10-02 17:29:30,739 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2011-10-02 17:29:30,739 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2011-10-02 17:29:30,739 DEBUG: nvidia.available: falling back to default
2011-10-02 17:29:30,815 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI xorg-video-abi-8 does not match X.org video ABI xorg-video-abi-10
2011-10-02 17:29:30,816 DEBUG: NVIDIA accelerated graphics driver not available
2011-10-02 17:29:30,819 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-10-02 17:29:30,820 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2011-10-02 17:29:30,820 DEBUG: nvidia.available: falling back to default
2011-10-02 17:29:30,858 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-10-02 17:29:30,858 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 947, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2011-10-02 17:29:30,863 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-10-02 17:29:30,863 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2011-10-02 17:29:30,863 DEBUG: nvidia.available: falling back to default
2011-10-02 17:29:30,900 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-10-02 17:29:30,901 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-10-02 17:29:30,906 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-10-02 17:29:30,926 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2011-10-02 17:29:30,927 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2011-10-02 17:29:30,927 DEBUG: loading custom handler /usr/share/jockey/handlers/nouveau3d.py
2011-10-02 17:29:30,952 DEBUG: Instantiated Handler subclass __builtin__.Nouveau3DHandler from name Nouveau3DHandler
2011-10-02 17:29:30,952 DEBUG: Experimental 3D support for NVIDIA cards not available
2011-10-02 17:29:30,953 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2011-10-02 17:29:30,973 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2011-10-02 17:29:30,987 DEBUG: Software modem not available
2011-10-02 17:29:30,987 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2011-10-02 17:29:30,992 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2011-10-02 17:29:30,993 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2011-10-02 17:29:30,993 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2011-10-02 17:29:30,993 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2011-10-02 17:29:31,017 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2011-10-02 17:29:31,017 DEBUG: Firmware for DVB cards not available
2011-10-02 17:29:31,017 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2011-10-02 17:29:31,022 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-10-02 17:29:31,023 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2011-10-02 17:29:31,023 DEBUG: fglrx.available: falling back to default
2011-10-02 17:29:31,061 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2011-10-02 17:29:31,061 DEBUG: all custom handlers loaded
2011-10-02 17:29:31,061 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x18887a0> about HardwareID('modalias', 'acpi:PNP0100:')
2011-10-02 17:29:31,062 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x18887a0> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2011-10-02 17:29:31,144 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-02 17:29:31,144 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x18887a0> about HardwareID('modalias', 'ssb:v4243id0807rev03')
2011-10-02 17:29:31,147 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x18887a0> about HardwareID('modalias', 'acpi:PNP0F13:')
2011-10-02 17:29:31,147 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x18887a0> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-10-02 17:29:31,147 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x18887a0> about HardwareID('modalias', 'pci:v00008086d000027A6sv00001028sd000001CDbc03sc80i00')
2011-10-02 17:29:31,409 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x18887a0> about HardwareID('modalias', 'platform:coretemp')
2011-10-02 17:29:31,410 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x18887a0> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2011-10-02 17:29:31,431 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x18887a0> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-10-02 17:29:31,431 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-02 17:29:31,431 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x18887a0> about HardwareID('modalias', 'usb:v0A5Cp4503d0100dc00dsc00dp00ic03isc01ip02')
2011-10-02 17:29:31,433 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-10-02 17:29:31,433 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x18887a0> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2011-10-02 17:29:31,433 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x18887a0> about HardwareID('modalias', 'acpi:PNP0C32:')
2011-10-02 17:29:31,433 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x18887a0> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-10-02 17:29:31,433 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x18887a0> about HardwareID('modalias', 'input:b0003v0A5Cp4503e0111-e0,1,2,4,k110,111,112,r0,1,am4,lsfw')
2011-10-02 17:29:31,433 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-02 17:29:31,434 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x18887a0> about HardwareID('modalias', 'platform:dell-laptop')
2011-10-02 17:29:31,434 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x18887a0> about HardwareID('modalias', 'wmi:9DBB5994-A997-11DA-B012-B622A1EF5492')
2011-10-02 17:29:31,434 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_wmi', 'jockey_handler': 'KernelModuleHandler'}
2011-10-02 17:29:31,434 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x18887a0> about HardwareID('modalias', 'pci:v00008086d000027A0sv00001028sd000001CDbc06sc00i00')
2011-10-02 17:29:31,437 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_agp', 'jockey_handler': 'KernelModuleHandler'}
2011-10-02 17:29:31,437 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x18887a0> about HardwareID('modalias', 'pci:v00008086d000027C9sv00001028sd000001CDbc0Csc03i00')
2011-10-02 17:29:31,440 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x18887a0> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2011-10-02 17:29:31,440 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x18887a0> about HardwareID('modalias', 'acpi:PNP0303:')
2011-10-02 17:29:31,440 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x18887a0> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-10-02 17:29:31,440 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x18887a0> about HardwareID('modalias', 'pci:v00008086d000027A2sv00001028sd000001CDbc03sc00i00')
2011-10-02 17:29:31,443 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2011-10-02 17:29:31,443 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x18887a0> about HardwareID('modalias', 'pci:v00008086d000027C8sv00001028sd000001CDbc0Csc03i00')
2011-10-02 17:29:31,446 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x18887a0> about HardwareID('modalias', 'acpi:device:')
2011-10-02 17:29:31,446 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x18887a0> about HardwareID('modalias', 'pci:v00001180d00000822sv00001028sd000001CDbc08sc05i01')
2011-10-02 17:29:31,448 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2011-10-02 17:29:31,449 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2011-10-02 17:29:31,449 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x18887a0> about HardwareID('modalias', 'pci:v00008086d00002448sv00001028sd000001CDbc06sc04i01')
2011-10-02 17:29:31,451 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x18887a0> about HardwareID('modalias', 'pci:v00008086d000027B9sv00001028sd000001CDbc06sc01i00')
2011-10-02 17:29:31,454 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_rng', 'jockey_handler': 'KernelModuleHandler'}
2011-10-02 17:29:31,454 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2011-10-02 17:29:31,454 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'leds_ss4200', 'jockey_handler': 'KernelModuleHandler'}
2011-10-02 17:29:31,454 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x18887a0> about HardwareID('modalias', 'usb:v413Cp8126d0100dcE0dsc01dp01icE0isc01ip01')
2011-10-02 17:29:31,469 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2011-10-02 17:29:31,469 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x18887a0> about HardwareID('modalias', 'usb:v0A5Cp4502d0100dc00dsc00dp00ic03isc01ip01')
2011-10-02 17:29:31,470 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-10-02 17:29:31,470 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x18887a0> about HardwareID('modalias', 'input:b0003v0A5Cp4502e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2011-10-02 17:29:31,470 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-02 17:29:31,470 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x18887a0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-10-02 17:29:31,471 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-02 17:29:31,471 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x18887a0> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-10-02 17:29:31,471 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-02 17:29:31,471 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x18887a0> about HardwareID('modalias', 'ssb:v4243id0806rev07')
2011-10-02 17:29:31,471 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'b44', 'jockey_handler': 'KernelModuleHandler'}
2011-10-02 17:29:31,471 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x18887a0> about HardwareID('modalias', 'acpi:PNP0000:')
2011-10-02 17:29:31,471 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x18887a0> about HardwareID('modalias', 'pci:v00008086d000027CCsv00001028sd000001CDbc0Csc03i20')
2011-10-02 17:29:31,474 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x18887a0> about HardwareID('modalias', 'input:b0011v0002p0007e0FB1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,mlsfw')
2011-10-02 17:29:31,474 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-02 17:29:31,474 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-10-02 17:29:31,474 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-10-02 17:29:31,474 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x18887a0> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-10-02 17:29:31,475 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x18887a0> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA08:bd04/02/2007:svnDellInc.:pnMP061:pvr:rvnDellInc.:rn0FF049:rvr:cvnDellInc.:ct8:cvr:')
2011-10-02 17:29:31,489 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_wmi_aio', 'jockey_handler': 'KernelModuleHandler'}
2011-10-02 17:29:31,489 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_laptop', 'jockey_handler': 'KernelModuleHandler'}
2011-10-02 17:29:31,489 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x18887a0> about HardwareID('modalias', 'pci:v00001180d00000592sv00001028sd000001CDbc08sc80i00')
2011-10-02 17:29:31,489 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x18887a0> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-10-02 17:29:31,489 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x18887a0> about HardwareID('modalias', 'pci:v000014E4d0000170Csv00001028sd000001CDbc02sc00i00')
2011-10-02 17:29:31,535 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'b44', 'jockey_handler': 'KernelModuleHandler'}
2011-10-02 17:29:31,536 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x18887a0> about HardwareID('modalias', 'ssb:v4243id0817rev04')
2011-10-02 17:29:31,536 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x18887a0> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,k94,95,A1,E0,E1,E3,EC,EE,ramlsfw')
2011-10-02 17:29:31,536 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-02 17:29:31,536 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x18887a0> about HardwareID('modalias', 'usb:v413Cp8126d0100dcE0dsc01dp01icFEisc01ip00')
2011-10-02 17:29:31,537 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2011-10-02 17:29:31,537 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x18887a0> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2011-10-02 17:29:31,537 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'option', 'jockey_handler': 'KernelModuleHandler'}
2011-10-02 17:29:31,537 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x18887a0> about HardwareID('modalias', 'usb:v413CpA005d5018dc09dsc00dp02ic09isc00ip02')
2011-10-02 17:29:31,538 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x18887a0> about HardwareID('modalias', 'pci:v00008086d000027DAsv00001028sd000001CDbc0Csc05i00')
2011-10-02 17:29:31,541 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2011-10-02 17:29:31,541 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x18887a0> about HardwareID('modalias', 'pci:v00008086d000027D8sv00001028sd000001CDbc04sc03i00')
2011-10-02 17:29:31,544 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-10-02 17:29:31,544 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x18887a0> about HardwareID('modalias', 'pci:v00001180d00000852sv00001028sd000001CDbc08sc80i00')
2011-10-02 17:29:31,544 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r852', 'jockey_handler': 'KernelModuleHandler'}
2011-10-02 17:29:31,544 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x18887a0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2011-10-02 17:29:31,545 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-02 17:29:31,545 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x18887a0> about HardwareID('modalias', 'acpi:PNP0200:')
2011-10-02 17:29:31,545 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x18887a0> about HardwareID('modalias', 'wmi:8D9DDCBC-A997-11DA-B012-B622A1EF5492')
2011-10-02 17:29:31,545 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x18887a0> about HardwareID('modalias', 'acpi:PNP0800:')
2011-10-02 17:29:31,545 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x18887a0> about HardwareID('modalias', 'platform:pcspkr')
2011-10-02 17:29:31,545 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2011-10-02 17:29:31,546 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2011-10-02 17:29:31,546 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x18887a0> about HardwareID('modalias', 'usb:v413Cp8126d0100dcE0dsc01dp01icFFiscFFipFF')
2011-10-02 17:29:31,546 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2011-10-02 17:29:31,546 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x18887a0> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2011-10-02 17:29:31,546 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x18887a0> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,F0,ram4,l0,1,2,sfw')
2011-10-02 17:29:31,547 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-02 17:29:31,547 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x18887a0> about HardwareID('modalias', 'wmi:A80593CE-A997-11DA-B012-B622A1EF5492')
2011-10-02 17:29:31,547 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x18887a0> about HardwareID('modalias', 'usb:v0A5Cp4500d0100dc09dsc00dp00ic09isc00ip00')
2011-10-02 17:29:31,547 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x18887a0> about HardwareID('modalias', 'wmi:A3776CE0-1E88-11DB-A98B-0800200C9A66')
2011-10-02 17:29:31,547 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x18887a0> about HardwareID('modalias', 'platform:dcdbas')
2011-10-02 17:29:31,548 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x18887a0> about HardwareID('modalias', 'pci:v00001180d00000832sv00001028sd000001CDbc0Csc00i10')
2011-10-02 17:29:31,548 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ohci1394', 'jockey_handler': 'KernelModuleHandler'}
2011-10-02 17:29:31,548 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2011-10-02 17:29:31,548 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x18887a0> about HardwareID('modalias', 'pci:v000014E4d00004328sv00001028sd00000009bc02sc80i00')
2011-10-02 17:29:31,554 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-10-02 17:29:31,555 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-10-02 17:29:31,554 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2011-10-02 17:29:31,555 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ssb', 'jockey_handler': 'KernelModuleHandler'}
2011-10-02 17:29:31,555 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x18887a0> about HardwareID('modalias', 'pci:v00008086d000027CBsv00001028sd000001CDbc0Csc03i00')
2011-10-02 17:29:31,559 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x18887a0> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-10-02 17:29:31,568 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2011-10-02 17:29:31,569 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-10-02 17:29:31,569 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x18887a0> about HardwareID('modalias', 'ssb:v4243id0812rev0B')
2011-10-02 17:29:31,569 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'b43', 'jockey_handler': 'KernelModuleHandler'}
2011-10-02 17:29:31,569 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x18887a0> about HardwareID('modalias', 'acpi:LNXTHERM:')
2011-10-02 17:29:31,569 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x18887a0> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2011-10-02 17:29:31,569 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-02 17:29:31,569 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x18887a0> about HardwareID('modalias', 'pci:v00008086d000027CAsv00001028sd000001CDbc0Csc03i00')
2011-10-02 17:29:31,572 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x18887a0> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2011-10-02 17:29:31,572 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e058c0> about HardwareID('modalias', 'acpi:PNP0100:')
2011-10-02 17:29:31,572 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e058c0> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2011-10-02 17:29:31,572 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e058c0> about HardwareID('modalias', 'ssb:v4243id0807rev03')
2011-10-02 17:29:31,572 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e058c0> about HardwareID('modalias', 'acpi:PNP0F13:')
2011-10-02 17:29:31,573 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e058c0> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-10-02 17:29:31,573 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e058c0> about HardwareID('modalias', 'pci:v00008086d000027A6sv00001028sd000001CDbc03sc80i00')
2011-10-02 17:29:31,573 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e058c0> about HardwareID('modalias', 'platform:coretemp')
2011-10-02 17:29:31,573 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e058c0> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2011-10-02 17:29:31,573 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e058c0> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-10-02 17:29:31,573 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e058c0> about HardwareID('modalias', 'usb:v0A5Cp4503d0100dc00dsc00dp00ic03isc01ip02')
2011-10-02 17:29:31,573 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e058c0> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2011-10-02 17:29:31,573 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e058c0> about HardwareID('modalias', 'acpi:PNP0C32:')
2011-10-02 17:29:31,573 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e058c0> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-10-02 17:29:31,573 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e058c0> about HardwareID('modalias', 'input:b0003v0A5Cp4503e0111-e0,1,2,4,k110,111,112,r0,1,am4,lsfw')
2011-10-02 17:29:31,573 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e058c0> about HardwareID('modalias', 'platform:dell-laptop')
2011-10-02 17:29:31,574 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e058c0> about HardwareID('modalias', 'wmi:9DBB5994-A997-11DA-B012-B622A1EF5492')
2011-10-02 17:29:31,574 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e058c0> about HardwareID('modalias', 'pci:v00008086d000027A0sv00001028sd000001CDbc06sc00i00')
2011-10-02 17:29:31,574 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e058c0> about HardwareID('modalias', 'pci:v00008086d000027C9sv00001028sd000001CDbc0Csc03i00')
2011-10-02 17:29:31,574 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e058c0> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2011-10-02 17:29:31,574 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e058c0> about HardwareID('modalias', 'acpi:PNP0303:')
2011-10-02 17:29:31,574 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e058c0> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-10-02 17:29:31,574 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e058c0> about HardwareID('modalias', 'pci:v00008086d000027A2sv00001028sd000001CDbc03sc00i00')
2011-10-02 17:29:31,574 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e058c0> about HardwareID('modalias', 'pci:v00008086d000027C8sv00001028sd000001CDbc0Csc03i00')
2011-10-02 17:29:31,574 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e058c0> about HardwareID('modalias', 'acpi:device:')
2011-10-02 17:29:31,574 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e058c0> about HardwareID('modalias', 'pci:v00001180d00000822sv00001028sd000001CDbc08sc05i01')
2011-10-02 17:29:31,574 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e058c0> about HardwareID('modalias', 'pci:v00008086d00002448sv00001028sd000001CDbc06sc04i01')
2011-10-02 17:29:31,575 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e058c0> about HardwareID('modalias', 'pci:v00008086d000027B9sv00001028sd000001CDbc06sc01i00')
2011-10-02 17:29:31,575 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e058c0> about HardwareID('modalias', 'usb:v413Cp8126d0100dcE0dsc01dp01icE0isc01ip01')
2011-10-02 17:29:31,575 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e058c0> about HardwareID('modalias', 'usb:v0A5Cp4502d0100dc00dsc00dp00ic03isc01ip01')
2011-10-02 17:29:31,575 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e058c0> about HardwareID('modalias', 'input:b0003v0A5Cp4502e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2011-10-02 17:29:31,575 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e058c0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-10-02 17:29:31,575 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e058c0> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-10-02 17:29:31,575 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e058c0> about HardwareID('modalias', 'ssb:v4243id0806rev07')
2011-10-02 17:29:31,575 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e058c0> about HardwareID('modalias', 'acpi:PNP0000:')
2011-10-02 17:29:31,575 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e058c0> about HardwareID('modalias', 'pci:v00008086d000027CCsv00001028sd000001CDbc0Csc03i20')
2011-10-02 17:29:31,575 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e058c0> about HardwareID('modalias', 'input:b0011v0002p0007e0FB1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,mlsfw')
2011-10-02 17:29:31,575 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e058c0> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-10-02 17:29:31,575 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e058c0> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA08:bd04/02/2007:svnDellInc.:pnMP061:pvr:rvnDellInc.:rn0FF049:rvr:cvnDellInc.:ct8:cvr:')
2011-10-02 17:29:31,576 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e058c0> about HardwareID('modalias', 'pci:v00001180d00000592sv00001028sd000001CDbc08sc80i00')
2011-10-02 17:29:31,576 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e058c0> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-10-02 17:29:31,576 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e058c0> about HardwareID('modalias', 'pci:v000014E4d0000170Csv00001028sd000001CDbc02sc00i00')
2011-10-02 17:29:31,576 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e058c0> about HardwareID('modalias', 'ssb:v4243id0817rev04')
2011-10-02 17:29:31,576 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e058c0> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,k94,95,A1,E0,E1,E3,EC,EE,ramlsfw')
2011-10-02 17:29:31,576 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e058c0> about HardwareID('modalias', 'usb:v413Cp8126d0100dcE0dsc01dp01icFEisc01ip00')
2011-10-02 17:29:31,576 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e058c0> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2011-10-02 17:29:31,576 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e058c0> about HardwareID('modalias', 'usb:v413CpA005d5018dc09dsc00dp02ic09isc00ip02')
2011-10-02 17:29:31,576 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e058c0> about HardwareID('modalias', 'pci:v00008086d000027DAsv00001028sd000001CDbc0Csc05i00')
2011-10-02 17:29:31,576 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e058c0> about HardwareID('modalias', 'pci:v00008086d000027D8sv00001028sd000001CDbc04sc03i00')
2011-10-02 17:29:31,576 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e058c0> about HardwareID('modalias', 'pci:v00001180d00000852sv00001028sd000001CDbc08sc80i00')
2011-10-02 17:29:31,577 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e058c0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2011-10-02 17:29:31,577 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e058c0> about HardwareID('modalias', 'acpi:PNP0200:')
2011-10-02 17:29:31,577 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e058c0> about HardwareID('modalias', 'wmi:8D9DDCBC-A997-11DA-B012-B622A1EF5492')
2011-10-02 17:29:31,577 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e058c0> about HardwareID('modalias', 'acpi:PNP0800:')
2011-10-02 17:29:31,577 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e058c0> about HardwareID('modalias', 'platform:pcspkr')
2011-10-02 17:29:31,577 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e058c0> about HardwareID('modalias', 'usb:v413Cp8126d0100dcE0dsc01dp01icFFiscFFipFF')
2011-10-02 17:29:31,577 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e058c0> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2011-10-02 17:29:31,577 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e058c0> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,F0,ram4,l0,1,2,sfw')
2011-10-02 17:29:31,577 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e058c0> about HardwareID('modalias', 'wmi:A80593CE-A997-11DA-B012-B622A1EF5492')
2011-10-02 17:29:31,577 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e058c0> about HardwareID('modalias', 'usb:v0A5Cp4500d0100dc09dsc00dp00ic09isc00ip00')
2011-10-02 17:29:31,577 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e058c0> about HardwareID('modalias', 'wmi:A3776CE0-1E88-11DB-A98B-0800200C9A66')
2011-10-02 17:29:31,578 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e058c0> about HardwareID('modalias', 'platform:dcdbas')
2011-10-02 17:29:31,578 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e058c0> about HardwareID('modalias', 'pci:v00001180d00000832sv00001028sd000001CDbc0Csc00i10')
2011-10-02 17:29:31,578 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e058c0> about HardwareID('modalias', 'pci:v000014E4d00004328sv00001028sd00000009bc02sc80i00')
2011-10-02 17:29:31,578 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e058c0> about HardwareID('modalias', 'pci:v00008086d000027CBsv00001028sd000001CDbc0Csc03i00')
2011-10-02 17:29:31,578 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e058c0> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-10-02 17:29:31,578 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e058c0> about HardwareID('modalias', 'ssb:v4243id0812rev0B')
2011-10-02 17:29:31,578 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e058c0> about HardwareID('modalias', 'acpi:LNXTHERM:')
2011-10-02 17:29:31,578 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e058c0> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2011-10-02 17:29:31,578 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e058c0> about HardwareID('modalias', 'pci:v00008086d000027CAsv00001028sd000001CDbc0Csc03i00')
2011-10-02 17:29:31,578 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1e058c0> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2011-10-02 17:29:31,604 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-10-02 17:29:31,638 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-10-02 17:29:31,659 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-10-02 17:29:33,326 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-10-02 17:29:38,688 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-10-02 17:29:38,689 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2011-10-02 17:29:38,719 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-10-02 17:29:41,149 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-10-02 17:29:41,161 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-10-02 17:29:41,181 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-10-02 17:29:42,951 DEBUG: Shutting down
```

---

### Post by praseodym on 2011-10-03
```
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
```

You need these files, too:

[http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.35-27-generic_2.6.35-27.48_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.35-27-generic_2.6.35-27.48_amd64.deb)

[http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.35-27_2.6.35-27.48_all.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.35-27_2.6.35-27.48_all.deb)

Then try the driver installation again. After that update your system:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get install linux-headers-generic
```

BTW: This is a Maverick-Kernel, the module for the Natty-Kernel was built:

```
Building initial module for 2.6.38-11-generic
Done.
```
This was an upgrade vom Maverick to Natty? Check the following:

Reboot and hold the SHIFT-button pressed. Choose in Grub the Kernel 2.6.38-11-generic, wireless should work there now.

---

### Post by ianthealy on 2011-10-03
THANK YOU SO MUCH!

This fixed the problem. Upon installing those two files in your last comment, when I opened the Additional Drivers, my Broadcom driver was activated but not in use, so I did not have to activate it.

I performed the other steps you outlined.

Yes, this was an upgrade from Maverick to Natty. Upon reboot, my wireless radio activated and I am now using my wireless connection again.

You were extremely helpful. Thank you again!):P

---

