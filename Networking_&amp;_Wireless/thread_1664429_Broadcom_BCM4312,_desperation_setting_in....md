---
title: "Broadcom BCM4312, desperation setting in..."
date: 2011-01-10
forum: Networking &amp; Wireless
---

### Post by Kernelingus on 2011-01-10
I'm flummoxed, guilt-stricken and near my wit's end.  

The Ubuntu-preloaded Inspiron 1545 I persuaded my girfriend to buy contains the dreaded BCM4312, and nothing I can think of seems to be helping.

I've tried various approaches with the STA and B43 drivers.  Gad, I feel like I've tried ***EVERYTHING***.  

Here's where her poor machine's at right now:

```

**uname -r**

2.6.35-24-generic


**lspci -v** *-- omitting output from all the unrelated devices*

0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
	Subsystem: Dell Wireless 1397 WLAN Mini-Card
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at f69fc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: wl
	Kernel modules: wl, ssb


**lshw -C network**

*-network DISABLED      
       description: Wireless interface
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 70:1a:04:16:2a:72
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:f69fc000-f69fffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: 00:25:64:62:f5:7b
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 duplex=full firmware=N/A ip=192.168.0.101 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:44 memory:f68fc000-f68fffff ioport:de00(size=256)


**lsmod**

Module                  Size  Used by
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
dm_crypt               11385  0 
joydev                  8767  0 
snd_hda_codec_idt      54887  1 
snd_hda_intel          22107  2 
snd_hda_codec          87552  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
lib80211_crypt_tkip     7736  0 
dell_wmi_aio            1733  0 
dell_wmi                2852  0 
uvcvideo               55847  0 
dell_laptop             5730  0 
dcdbas                  5402  1 dell_laptop
cdc_acm                15203  0 
wl                   1959533  0 
videodev               43098  1 uvcvideo
v4l1_compat            13359  2 uvcvideo,videodev
snd                    49038  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                59033  0 
serio_raw               4022  0 
soundcore                880  1 snd
lib80211                5058  2 lib80211_crypt_tkip,wl
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
dm_raid45              81721  0 
xor                    15136  1 dm_raid45
i915                  294989  4 
drm_kms_helper         30200  1 i915
drm                   168092  4 i915,drm_kms_helper
usb_storage            40172  0 
intel_agp              26694  2 i915
ahci                   19198  2 
sky2                   45127  0 
agpgart                32011  2 drm,intel_agp
i2c_algo_bit            5168  1 i915
libahci                21664  1 ahci
video                  18712  1 i915
output                  1883  1 video


**iwconfig**

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:24 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=5/5  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


**ifconfig**

eth0      Link encap:Ethernet  HWaddr 00:25:64:62:f5:7b  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::225:64ff:fe62:f57b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1467 errors:0 dropped:0 overruns:0 frame:0
          TX packets:803 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:926538 (926.5 KB)  TX bytes:119108 (119.1 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1440 (1.4 KB)  TX bytes:1440 (1.4 KB)


```

Help badly needed, please!

---

### Post by Bucky Ball on 2011-01-10
Broadcom is not dreaded at all nowadays. Installs easily, especially that card. 

I'll take one guess; it has 10.10 on it?

Anyhow, plug in an ethernet cable, do an update via System >Administration >Update Manager, then go to System >Administration >Additional Drivers.

You may get offered the drivers for your card before you get this far!

That card really shouldn't be an issue, but if you try this and still no go, and you are using 10.10, please open a terminal (Applications >Accessories >Terminal) and copy and paste this in:

```
uname -r
```If that says:

```
2.6.35-24
```... you have a problem and would be much better off with 10.04 LTS (I don't for the life of me know why any company would sell pre-installed Ubuntu comp with anything but the latest production release on it, though). That kernel has bugs at the moment and one of them is a distinct dislike for Broadcom. If it is that kernel, unless you want to be tweaking that thing for the next few days, I would advise the switch.

PS: If my first tip doesn't work, is there an earlier kernel on the kernel list when you boot up? 2.6.35-23??? If so, boot into that and try the same steps again.

Deep breath, don't panic. New machine with no valuable data on it as yet and only Ubuntu installed (and running)? Bah, we'll sort this out in no time. There's absolutely nothing wrong except the missing firmware and driver for the wireless card by the looks. ;)

---

### Post by Kernelingus on 2011-01-11
Good guess, I'm running 10.10.  And, notwithstanding your generous help, still at a loss.

I tried rolling kernel back to 2.6.31-22, but when I tried using "Additional Drivers" utility to load STA (proprietary) driver, got error saying:

```
Sorry, installation of this driver failed.

Please have a look at the log file for details: /var/log/jockey.log
```

Very well, then. 

Here's all of what ../jockey.log had to say:

```
2011-01-10 21:56:34,406 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x87594ac>
2011-01-10 21:56:34,430 DEBUG: reading modalias file /lib/modules/2.6.31-22-generic/modules.alias
2011-01-10 21:56:34,600 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2011-01-10 21:56:34,616 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2011-01-10 21:56:34,630 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-01-10 21:56:34,669 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2011-01-10 21:56:34,689 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2011-01-10 21:56:34,709 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2011-01-10 21:56:34,712 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2011-01-10 21:56:34,730 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2011-01-10 21:56:35,067 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2011-01-10 21:56:35,139 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
  File "/usr/share/jockey/handlers/nvidia.py", line 184, in __init__
    raise SystemError, 'does not currently work with xserver 1.9'
SystemError: does not currently work with xserver 1.9
2011-01-10 21:56:35,201 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-01-10 21:56:35,203 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2011-01-10 21:56:35,238 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-01-10 21:56:35,238 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2011-01-10 21:56:35,243 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-01-10 21:56:35,245 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2011-01-10 21:56:35,258 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-01-10 21:56:35,258 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2011-01-10 21:56:35,279 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-01-10 21:56:35,281 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2011-01-10 21:56:35,293 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2011-01-10 21:56:35,294 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-01-10 21:56:35,300 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-01-10 21:56:35,313 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2011-01-10 21:56:35,314 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2011-01-10 21:56:35,314 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2011-01-10 21:56:35,417 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2011-01-10 21:56:35,418 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2011-01-10 21:56:35,454 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2011-01-10 21:56:35,455 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2011-01-10 21:56:35,455 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2011-01-10 21:56:35,487 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2011-01-10 21:56:35,538 DEBUG: Software modem not available
2011-01-10 21:56:35,538 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2011-01-10 21:56:35,544 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2011-01-10 21:56:35,545 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2011-01-10 21:56:35,546 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2011-01-10 21:56:35,546 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2011-01-10 21:56:35,664 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2011-01-10 21:56:35,664 DEBUG: Firmware for DVB cards not available
2011-01-10 21:56:35,665 DEBUG: all custom handlers loaded
2011-01-10 21:56:35,665 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87594ac> about HardwareID('modalias', 'pci:v00008086d00002A43sv00001028sd000002AAbc03sc80i00')
2011-01-10 21:56:35,900 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87594ac> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-01-10 21:56:36,267 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-01-10 21:56:36,268 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87594ac> about HardwareID('modalias', 'pci:v00008086d00002929sv00001028sd000002AAbc01sc06i01')
2011-01-10 21:56:36,271 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87594ac> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2011-01-10 21:56:36,273 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87594ac> about HardwareID('modalias', 'acpi:PNP0800:')
2011-01-10 21:56:36,273 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87594ac> about HardwareID('modalias', 'acpi:PNP0303:')
2011-01-10 21:56:36,274 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87594ac> about HardwareID('modalias', 'pci:v00008086d00002937sv00001028sd000002AAbc0Csc03i00')
2011-01-10 21:56:36,277 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87594ac> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-01-10 21:56:36,278 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-01-10 21:56:36,278 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87594ac> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-01-10 21:56:36,278 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87594ac> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2011-01-10 21:56:36,304 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87594ac> about HardwareID('modalias', 'pci:v00008086d00002930sv00001028sd000002AAbc0Csc05i00')
2011-01-10 21:56:36,307 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2011-01-10 21:56:36,307 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87594ac> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2011-01-10 21:56:36,307 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-01-10 21:56:36,307 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87594ac> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-01-10 21:56:36,308 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87594ac> about HardwareID('modalias', 'platform:dcdbas')
2011-01-10 21:56:36,308 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87594ac> about HardwareID('modalias', 'pci:v000011ABd00004354sv00001028sd000002AAbc02sc00i00')
2011-01-10 21:56:36,335 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sky2', 'jockey_handler': 'KernelModuleHandler'}
2011-01-10 21:56:36,335 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87594ac> about HardwareID('modalias', 'platform:eisa')
2011-01-10 21:56:36,335 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87594ac> about HardwareID('modalias', 'pci:v00008086d00002919sv00001028sd000002AAbc06sc01i00')
2011-01-10 21:56:36,338 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2011-01-10 21:56:36,338 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87594ac> about HardwareID('modalias', 'pci:v00008086d00002A40sv00001028sd000002AAbc06sc00i00')
2011-01-10 21:56:36,341 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_agp', 'jockey_handler': 'KernelModuleHandler'}
2011-01-10 21:56:36,341 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87594ac> about HardwareID('modalias', 'usb:v1004p618Ed0100dc02dsc02dp00icFFiscFFipFF')
2011-01-10 21:56:36,342 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87594ac> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2011-01-10 21:56:36,342 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87594ac> about HardwareID('modalias', 'acpi:PNP0000:')
2011-01-10 21:56:36,342 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87594ac> about HardwareID('modalias', 'pci:v00008086d00002A42sv00001028sd000002AAbc03sc00i00')
2011-01-10 21:56:36,345 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2011-01-10 21:56:36,345 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87594ac> about HardwareID('modalias', 'acpi:PNP0F13:')
2011-01-10 21:56:36,345 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87594ac> about HardwareID('modalias', 'acpi:LNXTHERM:')
2011-01-10 21:56:36,345 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87594ac> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-01-10 21:56:36,346 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87594ac> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-01-10 21:56:36,346 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87594ac> about HardwareID('modalias', 'usb:v0BDAp0158d5888dc00dsc00dp00ic08isc06ip50')
2011-01-10 21:56:36,351 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2011-01-10 21:56:36,351 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87594ac> about HardwareID('modalias', 'pci:v00008086d0000293Csv00001028sd000002AAbc0Csc03i20')
2011-01-10 21:56:36,354 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87594ac> about HardwareID('modalias', 'pci:v00008086d0000293Asv00001028sd000002AAbc0Csc03i20')
2011-01-10 21:56:36,357 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87594ac> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C0,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,EE,ram4,l0,1,2,sfw')
2011-01-10 21:56:36,357 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-01-10 21:56:36,357 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87594ac> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2011-01-10 21:56:36,357 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-01-10 21:56:36,358 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87594ac> about HardwareID('modalias', 'usb:v1004p618Ed0100dc02dsc02dp00ic0Aisc00ip00')
2011-01-10 21:56:36,358 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87594ac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-01-10 21:56:36,358 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-01-10 21:56:36,358 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87594ac> about HardwareID('modalias', 'input:b0011v0002p0008e7321-e0,1,2,3,k110,111,112,145,14A,r0,1,a0,1,18,mlsfw')
2011-01-10 21:56:36,359 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-01-10 21:56:36,359 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-01-10 21:56:36,359 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-01-10 21:56:36,359 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87594ac> about HardwareID('modalias', 'pci:v00008086d00002939sv00001028sd000002AAbc0Csc03i00')
2011-01-10 21:56:36,362 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87594ac> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA10:bd07/17/2009:svnDellInc.:pnInspiron1545:pvr:rvnDellInc.:rn0G848F:rvr:cvnDellInc.:ct8:cvr:')
2011-01-10 21:56:36,378 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_wmi', 'jockey_handler': 'KernelModuleHandler'}
2011-01-10 21:56:36,378 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_laptop', 'jockey_handler': 'KernelModuleHandler'}
2011-01-10 21:56:36,378 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87594ac> about HardwareID('modalias', 'acpi:PNP0200:')
2011-01-10 21:56:36,378 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87594ac> about HardwareID('modalias', 'usb:v1004p618Ed0100dc02dsc02dp00icFFisc42ip01')
2011-01-10 21:56:36,379 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87594ac> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2011-01-10 21:56:36,379 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-01-10 21:56:36,379 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87594ac> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2011-01-10 21:56:36,380 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87594ac> about HardwareID('modalias', 'usb:v0C45p63EEd9429dcEFdsc02dp01ic0Eisc01ip00')
2011-01-10 21:56:36,431 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2011-01-10 21:56:36,432 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87594ac> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2011-01-10 21:56:36,432 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87594ac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2011-01-10 21:56:36,432 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-01-10 21:56:36,432 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87594ac> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-01-10 21:56:36,432 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87594ac> about HardwareID('modalias', 'pci:v00008086d00002936sv00001028sd000002AAbc0Csc03i00')
2011-01-10 21:56:36,435 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87594ac> about HardwareID('modalias', 'usb:v1004p618Ed0100dc02dsc02dp00ic02isc02ip01')
2011-01-10 21:56:36,436 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'cdc_acm', 'jockey_handler': 'KernelModuleHandler'}
2011-01-10 21:56:36,436 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87594ac> about HardwareID('modalias', 'pci:v00008086d00002938sv00001028sd000002AAbc0Csc03i00')
2011-01-10 21:56:36,439 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87594ac> about HardwareID('modalias', 'pci:v00008086d00002935sv00001028sd000002AAbc0Csc03i00')
2011-01-10 21:56:36,441 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87594ac> about HardwareID('modalias', 'pci:v00008086d0000293Esv00001028sd000002AAbc04sc03i00')
2011-01-10 21:56:36,444 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-01-10 21:56:36,444 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87594ac> about HardwareID('modalias', 'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2011-01-10 21:56:36,445 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-01-10 21:56:36,445 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87594ac> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-01-10 21:56:36,445 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87594ac> about HardwareID('modalias', 'usb:v0C45p63EEd9429dcEFdsc02dp01ic0Eisc02ip00')
2011-01-10 21:56:36,446 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87594ac> about HardwareID('modalias', 'pci:v000014E4d00004315sv00001028sd0000000Cbc02sc80i00')
2011-01-10 21:56:36,495 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ssb', 'jockey_handler': 'KernelModuleHandler'}
2011-01-10 21:56:36,504 DEBUG: got handler firmware:b43([B43Handler, free, disabled] Broadcom B43 wireless driver)
2011-01-10 21:56:36,509 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-01-10 21:56:36,510 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-01-10 21:56:36,510 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2011-01-10 21:56:36,511 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87594ac> about HardwareID('modalias', 'platform:pcspkr')
2011-01-10 21:56:36,512 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2011-01-10 21:56:36,512 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2011-01-10 21:56:36,512 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87594ac> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-01-10 21:56:36,530 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2011-01-10 21:56:36,530 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-01-10 21:56:36,530 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87594ac> about HardwareID('modalias', 'usb:v1004p618Ed0100dc02dsc02dp00ic08isc06ip50')
2011-01-10 21:56:36,531 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2011-01-10 21:56:36,531 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87594ac> about HardwareID('modalias', 'input:b0001v111Dp76B2e0001-e0,12,kramls1,2,fw')
2011-01-10 21:56:36,531 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-01-10 21:56:36,531 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87594ac> about HardwareID('modalias', 'pci:v00008086d00002934sv00001028sd000002AAbc0Csc03i00')
2011-01-10 21:56:36,534 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87594ac> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,k94,95,A1,E0,E1,EC,EE,1AF,ramlsfw')
2011-01-10 21:56:36,535 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-01-10 21:56:36,535 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87594ac> about HardwareID('modalias', 'input:b0003v0C45p63EEe9429-e0,1,kD4,ramlsfw')
2011-01-10 21:56:36,535 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-01-10 21:56:36,535 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87594ac> about HardwareID('modalias', 'acpi:PNP0100:')
2011-01-10 21:56:36,535 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89cb58c> about HardwareID('modalias', 'pci:v00008086d00002A43sv00001028sd000002AAbc03sc80i00')
2011-01-10 21:56:36,535 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89cb58c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-01-10 21:56:36,536 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89cb58c> about HardwareID('modalias', 'pci:v00008086d00002929sv00001028sd000002AAbc01sc06i01')
2011-01-10 21:56:36,536 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89cb58c> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2011-01-10 21:56:36,536 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89cb58c> about HardwareID('modalias', 'acpi:PNP0800:')
2011-01-10 21:56:36,536 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89cb58c> about HardwareID('modalias', 'acpi:PNP0303:')
2011-01-10 21:56:36,536 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89cb58c> about HardwareID('modalias', 'pci:v00008086d00002937sv00001028sd000002AAbc0Csc03i00')
2011-01-10 21:56:36,536 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89cb58c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-01-10 21:56:36,536 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89cb58c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-01-10 21:56:36,537 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89cb58c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2011-01-10 21:56:36,537 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89cb58c> about HardwareID('modalias', 'pci:v00008086d00002930sv00001028sd000002AAbc0Csc05i00')
2011-01-10 21:56:36,537 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89cb58c> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2011-01-10 21:56:36,537 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89cb58c> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-01-10 21:56:36,537 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89cb58c> about HardwareID('modalias', 'platform:dcdbas')
2011-01-10 21:56:36,537 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89cb58c> about HardwareID('modalias', 'pci:v000011ABd00004354sv00001028sd000002AAbc02sc00i00')
2011-01-10 21:56:36,537 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89cb58c> about HardwareID('modalias', 'platform:eisa')
2011-01-10 21:56:36,537 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89cb58c> about HardwareID('modalias', 'pci:v00008086d00002919sv00001028sd000002AAbc06sc01i00')
2011-01-10 21:56:36,538 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89cb58c> about HardwareID('modalias', 'pci:v00008086d00002A40sv00001028sd000002AAbc06sc00i00')
2011-01-10 21:56:36,538 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89cb58c> about HardwareID('modalias', 'usb:v1004p618Ed0100dc02dsc02dp00icFFiscFFipFF')
2011-01-10 21:56:36,538 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89cb58c> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2011-01-10 21:56:36,538 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89cb58c> about HardwareID('modalias', 'acpi:PNP0000:')
2011-01-10 21:56:36,538 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89cb58c> about HardwareID('modalias', 'pci:v00008086d00002A42sv00001028sd000002AAbc03sc00i00')
2011-01-10 21:56:36,538 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89cb58c> about HardwareID('modalias', 'acpi:PNP0F13:')
2011-01-10 21:56:36,538 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89cb58c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2011-01-10 21:56:36,538 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89cb58c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-01-10 21:56:36,539 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89cb58c> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-01-10 21:56:36,539 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89cb58c> about HardwareID('modalias', 'usb:v0BDAp0158d5888dc00dsc00dp00ic08isc06ip50')
2011-01-10 21:56:36,539 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89cb58c> about HardwareID('modalias', 'pci:v00008086d0000293Csv00001028sd000002AAbc0Csc03i20')
2011-01-10 21:56:36,539 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89cb58c> about HardwareID('modalias', 'pci:v00008086d0000293Asv00001028sd000002AAbc0Csc03i20')
2011-01-10 21:56:36,539 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89cb58c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C0,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,EE,ram4,l0,1,2,sfw')
2011-01-10 21:56:36,539 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89cb58c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2011-01-10 21:56:36,539 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89cb58c> about HardwareID('modalias', 'usb:v1004p618Ed0100dc02dsc02dp00ic0Aisc00ip00')
2011-01-10 21:56:36,540 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89cb58c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-01-10 21:56:36,540 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89cb58c> about HardwareID('modalias', 'input:b0011v0002p0008e7321-e0,1,2,3,k110,111,112,145,14A,r0,1,a0,1,18,mlsfw')
2011-01-10 21:56:36,540 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89cb58c> about HardwareID('modalias', 'pci:v00008086d00002939sv00001028sd000002AAbc0Csc03i00')
2011-01-10 21:56:36,540 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89cb58c> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA10:bd07/17/2009:svnDellInc.:pnInspiron1545:pvr:rvnDellInc.:rn0G848F:rvr:cvnDellInc.:ct8:cvr:')
2011-01-10 21:56:36,540 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89cb58c> about HardwareID('modalias', 'acpi:PNP0200:')
2011-01-10 21:56:36,540 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89cb58c> about HardwareID('modalias', 'usb:v1004p618Ed0100dc02dsc02dp00icFFisc42ip01')
2011-01-10 21:56:36,540 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89cb58c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2011-01-10 21:56:36,540 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89cb58c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2011-01-10 21:56:36,541 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89cb58c> about HardwareID('modalias', 'usb:v0C45p63EEd9429dcEFdsc02dp01ic0Eisc01ip00')
2011-01-10 21:56:36,541 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89cb58c> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2011-01-10 21:56:36,541 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89cb58c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2011-01-10 21:56:36,541 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89cb58c> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-01-10 21:56:36,541 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89cb58c> about HardwareID('modalias', 'pci:v00008086d00002936sv00001028sd000002AAbc0Csc03i00')
2011-01-10 21:56:36,541 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89cb58c> about HardwareID('modalias', 'usb:v1004p618Ed0100dc02dsc02dp00ic02isc02ip01')
2011-01-10 21:56:36,541 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89cb58c> about HardwareID('modalias', 'pci:v00008086d00002938sv00001028sd000002AAbc0Csc03i00')
2011-01-10 21:56:36,541 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89cb58c> about HardwareID('modalias', 'pci:v00008086d00002935sv00001028sd000002AAbc0Csc03i00')
2011-01-10 21:56:36,542 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89cb58c> about HardwareID('modalias', 'pci:v00008086d0000293Esv00001028sd000002AAbc04sc03i00')
2011-01-10 21:56:36,542 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89cb58c> about HardwareID('modalias', 'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2011-01-10 21:56:36,542 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89cb58c> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-01-10 21:56:36,542 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89cb58c> about HardwareID('modalias', 'usb:v0C45p63EEd9429dcEFdsc02dp01ic0Eisc02ip00')
2011-01-10 21:56:36,542 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89cb58c> about HardwareID('modalias', 'pci:v000014E4d00004315sv00001028sd0000000Cbc02sc80i00')
2011-01-10 21:56:36,542 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89cb58c> about HardwareID('modalias', 'platform:pcspkr')
2011-01-10 21:56:36,542 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89cb58c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-01-10 21:56:36,542 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89cb58c> about HardwareID('modalias', 'usb:v1004p618Ed0100dc02dsc02dp00ic08isc06ip50')
2011-01-10 21:56:36,543 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89cb58c> about HardwareID('modalias', 'input:b0001v111Dp76B2e0001-e0,12,kramls1,2,fw')
2011-01-10 21:56:36,543 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89cb58c> about HardwareID('modalias', 'pci:v00008086d00002934sv00001028sd000002AAbc0Csc03i00')
2011-01-10 21:56:36,543 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89cb58c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,k94,95,A1,E0,E1,EC,EE,1AF,ramlsfw')
2011-01-10 21:56:36,543 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89cb58c> about HardwareID('modalias', 'input:b0003v0C45p63EEe9429-e0,1,kD4,ramlsfw')
2011-01-10 21:56:36,543 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89cb58c> about HardwareID('modalias', 'acpi:PNP0100:')
2011-01-10 21:56:36,775 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-01-10 21:56:36,921 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-01-10 21:56:40,799 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-01-10 21:56:45,454 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-01-10 21:56:50,527 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-01-10 21:56:50,528 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2011-01-10 21:56:50,636 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-01-10 21:57:11,847 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-01-10 21:57:11,902 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-01-10 21:57:12,015 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-01-10 21:57:13,319 DEBUG: Shutting down
```

Good times, eh?

Maybe the answer lies in ../blacklist.conf?  

Can't hurt to look...

```
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
blacklist bcm43xx

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
blacklist amd76x_edac
```

jockey.log seems to suggest that something is blacklisted that shouldn't be.  But unless I'm missing something, I just see a legacy driver and some stuff for unrelated hardware.

Maybe the B43 driver is what I should be messing with after all, instead of this STA thing?  I don't know...

I'm so confused.

Somebody help me, please.:confused:

---

### Post by Bucky Ball on 2011-01-11
System >Admin >Synaptic Package Manager. Look for and install:

firmware-b43-installer
b43-fwcutter

In that order.

---

### Post by fil_lif on 2011-01-11
been using 10.04 lucid for about 9 months with BCM4312 and bcmwl-kernel-source worked out of the box, needed to activate the driver in menu>system>admin>hardware drivers first.

Looking at your ifconfig output, could it just be "ifconfig eth1 up"?

otherwise try bucky's idea, b43-fwcutter worked for me in a backtrack live cd, and also likes monitor mode :)

---

### Post by Kernelingus on 2011-01-11
Both **firmware-b43-installer** and **b43-fwcutter** are installed, but when I use the "Additional Drivers" utility to install the B43 driver I get this:

```
SystemError: installArchives() failed
```

Any other ideas?!  

(Thanks so much for helping me!)

---

### Post by Bucky Ball on 2011-01-11
You have done updates? Silly question perhaps but just checking ...

Maybe try these two commands one at a time in a terminal while online with cable:

```
sudo apt-get update
sudo apt-get upgrade
```The last will NOT upgrade the OS, just all packages.

The last will NOT upgrade OS, just all packages.

---

