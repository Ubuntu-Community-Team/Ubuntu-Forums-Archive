---
title: "Wifi is not working in ubuntu 12.04.2"
date: 2013-05-25
forum: Networking &amp; Wireless
---

### Post by prantik on 2013-05-25
Hi,

I am using Toshiba satellite C640 (core i5 2nd gen intel, 4 gb ram, 500 gb hdd) and I am quite new to Linux. I have been using ubuntu 12.04 for quite some time. At first I worked in 12.04 and then I switched to 12.04.2 64 bit. 

In 12.04.2, the wifi is not working. In the network applet, it alway shows "Wireless is disabled by hardware switch" and is always darkened. When I press the wireless function key (Fn+F8), it does nothing. But all the other keys like function keys for sound, graphics, logoff etc works perfectly. 

I have also tried- sudo rfkill unblock. But nothing happened. 


Computer
********


Summary
-------

-Computer-
Processor        : 4x Intel(R) Core(TM) i5-2430M CPU @ 2.40GHz
Memory        : 3995MB (701MB used)
Operating System        : Ubuntu 12.04.2 LTS
User Name        : anindya (anindya)
Date/Time        : Sat 25 May 2013 12:39:17 PM IST
-Display-
Resolution        : 1366x768 pixels
OpenGL Renderer        : Unknown
X11 Vendor        : The X.Org Foundation
-Multimedia-
Audio Adapter        : HDA-Intel - HDA Intel PCH

Operating System
----------------

-Version-
Kernel        : Linux 3.5.0-30-generic (x86_64)
Compiled        : #51~precise1-Ubuntu SMP Wed May 15 08:48:19 UTC 2013
C Library        : Unknown
Default C Compiler        : GNU C Compiler version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) 
Distribution        : Ubuntu 12.04.2 LTS
-Current Session-
Computer Name        : anindya-Satellite-C640
User Name        : anindya (anindya)
Home Directory        : /home/anindya
Desktop Environment        : GNOME (gnome-classic)
-Misc-
Uptime        : 40 minutes
Load Average        : 0.18, 0.13, 0.15

Kernel Modules
--------------

-Loaded Modules-
ppp_deflate
zlib_deflate
bsd_comp
ppp_async
crc_ccitt        : CRC-CCITT calculations
option        : USB Driver for GSM modems
usb_wwan        : USB Driver for GSM modems
usbserial        : USB Serial Driver core
cdc_ether        : USB CDC Ethernet devices
usbnet        : USB network driver framework
pci_stub
vboxpci        : Oracle VM VirtualBox PCI access Driver
vboxnetadp        : Oracle VM VirtualBox Network Adapter Driver
vboxnetflt        : Oracle VM VirtualBox Network Filter Driver
vboxdrv        : Oracle VM VirtualBox Support Driver
rfcomm        : Bluetooth RFCOMM ver 1.11
bnep        : Bluetooth BNEP ver 1.3
parport_pc        : PC-style parallel port driver
ppdev
joydev        : Joystick device interfaces
snd_hda_codec_conexant        : Conexant HD-audio codec
coretemp        : Intel Core temperature monitor
kvm_intel
kvm
ghash_clmulni_intel        : GHASH Message Digest Algorithm, acclerated by PCLMULQDQ-NI
aesni_intel        : Rijndael (AES) Cipher Algorithm, Intel AES-NI instructions optimized
cryptd        : Software async crypto daemon
aes_x86_64        : Rijndael (AES) Cipher Algorithm, asm optimized
ath3k        : Atheros AR30xx firmware driver
btusb        : Generic Bluetooth USB driver ver 0.6
bluetooth        : Bluetooth Core ver 2.16
uvcvideo        : USB Video Class driver
videobuf2_core        : Driver helper framework for Video for Linux 2
videodev        : Device registrar for Video4Linux drivers v2
videobuf2_vmalloc        : vmalloc memory handling routines for videobuf2
videobuf2_memops        : common memory handling routines for videobuf2
ext2        : Second Extended Filesystem
snd_hda_intel        : Intel HDA driver
snd_hda_codec        : HDA codec core
snd_hwdep        : Hardware dependent layer
snd_pcm        : Midlevel PCM code for ALSA.
microcode        : Microcode Update Driver
snd_seq_midi        : Advanced Linux Sound Architecture sequencer MIDI synth.
snd_rawmidi        : Midlevel RawMidi code for ALSA.
snd_seq_midi_event        : MIDI byte &lt;-&gt; sequencer event coder
arc4        : ARC4 Cipher Algorithm
psmouse        : PS/2 mouse driver
serio_raw        : Raw serio driver
snd_seq        : Advanced Linux Sound Architecture sequencer.
toshiba_bluetooth        : Toshiba Laptop ACPI Bluetooth Enable Driver
ath9k        : Support for Atheros 802.11n wireless LAN cards.
mac80211        : IEEE 802.11 subsystem
snd_timer        : ALSA timer interface
ath9k_common        : Shared library for Atheros wireless 802.11n LAN cards.
snd_seq_device        : ALSA sequencer device management
ath9k_hw        : Support for Atheros 802.11n wireless LAN cards.
ath        : Shared library for Atheros wireless LAN cards.
cfg80211        : wireless configuration support
toshiba_acpi        : Toshiba Laptop ACPI Extras Driver
sparse_keymap        : Generic support for sparse keymaps
snd        : Advanced Linux Sound Architecture driver for soundcards.
wmi        : ACPI-WMI Mapping Driver
i915        : Intel Graphics
soundcore        : Core sound module
snd_page_alloc        : Memory allocator for ALSA system.
drm_kms_helper        : DRM KMS helper
lpc_ich        : LPC interface for Intel ICH
drm        : DRM shared core routines
i2c_algo_bit        : I2C-Bus bit-banging algorithm
video        : ACPI Video Driver
mac_hid
mei        : Intel(R) Management Engine Interface
lp
parport
ums_realtek        : Driver for Realtek USB Card Reader
usb_storage        : USB Mass Storage driver for Linux
atl1c        : Qualcom Atheros 100/1000M Ethernet Network Driver
ahci        : AHCI SATA low-level driver
libahci        : Common AHCI SATA low-level routines

Filesystems
-----------

-Mounted File Systems-
/dev/sda6    /    17.92 % (30.1 GiB of 36.7 GiB)    
udev    /dev    0.00 % (1.9 GiB of 1.9 GiB)    
tmpfs    /run    0.11 % (779.5 MiB of 780.3 MiB)    
none    /run/lock    0.08 % (5.0 MiB of 5.0 MiB)    
none    /run/shm    0.01 % (1.9 GiB of 1.9 GiB)    
/dev/sda1    /boot    16.40 % (372.9 MiB of 446.1 MiB)    
/dev/sda7    /home    44.19 % (233.1 GiB of 417.6 GiB)    

Display
-------

-Display-
Resolution        : 1366x768 pixels
Vendor        : The X.Org Foundation
Version        : 1.13.0
-Monitors-
Monitor 0        : 1366x768 pixels
-Extensions-

Devices
*******

Processor
---------

-Processors-
Intel(R) Core(TM) i5-2430M CPU @ 2.40GHz        : 800.00MHz
Intel(R) Core(TM) i5-2430M CPU @ 2.40GHz        : 800.00MHz
Intel(R) Core(TM) i5-2430M CPU @ 2.40GHz        : 800.00MHz
Intel(R) Core(TM) i5-2430M CPU @ 2.40GHz        : 800.00MHz

Memory
------

-Memory-
Total Memory        : 3995304 kB
Free Memory        : 2757264 kB
Buffers        : 73192 kB
Cached        : 538292 kB
Cached Swap        : 0 kB
Active        : 592648 kB
Inactive        : 502204 kB
Active(anon)        : 484624 kB
Inactive(anon)        : 95732 kB
Active(file)        : 108024 kB
Inactive(file)        : 406472 kB
Unevictable        : 0 kB
Mlocked        : 0 kB
Virtual Memory        : 3998716 kB
Free Virtual Memory        : 3998716 kB
Dirty        : 48 kB
Writeback        : 0 kB
AnonPages        : 483392 kB
Mapped        : 101944 kB
Shmem        : 96996 kB
Slab        : 57400 kB
SReclaimable        : 31928 kB
SUnreclaim        : 25472 kB
KernelStack        : 2936 kB
PageTables        : 22672 kB
NFS_Unstable        : 0 kB
Bounce        : 0 kB
WritebackTmp        : 0 kB
CommitLimit        : 5996368 kB
Committed_AS        : 2216680 kB
VmallocTotal        : 34359738367 kB
VmallocUsed        : 556664 kB
VmallocChunk        : 34359176192 kB
HardwareCorrupted        : 0 kB
AnonHugePages        : 0 kB
HugePages_Total        : 0
HugePages_Free        : 0
HugePages_Rsvd        : 0
HugePages_Surp        : 0
Hugepagesize        : 2048 kB
DirectMap4k        : 77824 kB
DirectMap2M        : 4065280 kB

PCI Devices
-----------

-PCI Devices-
Host bridge        : Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
VGA compatible controller        : Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
Communication controller        : Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
USB controller        : Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04) (prog-if 20 [EHCI])
Audio device        : Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
PCI bridge        : Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4) (prog-if 00 [Normal decode])
PCI bridge        : Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b4) (prog-if 00 [Normal decode])
USB controller        : Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04) (prog-if 20 [EHCI])
ISA bridge        : Intel Corporation HM65 Express Chipset Family LPC Controller (rev 04)
SATA controller        : Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 04) (prog-if 01 [AHCI 1.0])
SMBus        : Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 04)
Ethernet controller        : Atheros Communications Inc. AR8152 v2.0 Fast Ethernet (rev c1)
Network controller        : Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

USB Devices
-----------


Printers
--------

-Printers-
No printers found

Battery
-------

-No batteries-
No batteries found on this system

Sensors
-------


Input Devices
-------------

-Input Devices-
 Power Button
 Lid Switch
 Power Button
 AT Translated Set 2 keyboard
 Toshiba input device
 TOSHIBA Web Camera - MP
 Video Bus
 SynPS/2 Synaptics TouchPad

Storage
-------

-SCSI Disks-
ATA TOSHIBA MK5076GS
TSSTcorp CDDVDW TS-L633F
HUAWEI Mass Storage
HUAWEI SD Storage

DMI
---

-BIOS-
Date        : 04/01/2011
Vendor        : INSYDE
Version        : 1.00
-Board-
Name        : Portable PC
Vendor        : TOSHIBA ([www.toshiba.com](www.toshiba.com))


Benchmarks
**********


CPU Blowfish
------------

-CPU Blowfish-
<big><b>This Machine</b></big>    800 MHz    14.598    
Intel(R) Celeron(R) M processor         1.50GHz    (null)    26.1876862    
PowerPC 740/750 (280.00MHz)    (null)    172.816713    

CPU CryptoHash
--------------

-CPU CryptoHash-
<big><b>This Machine</b></big>    800 MHz    96.000    

CPU Fibonacci
-------------

-CPU Fibonacci-
<big><b>This Machine</b></big>    800 MHz    6.754    
Intel(R) Celeron(R) M processor         1.50GHz    (null)    8.1375674    
PowerPC 740/750 (280.00MHz)    (null)    58.07682    

CPU N-Queens
------------

-CPU N-Queens-
<big><b>This Machine</b></big>    800 MHz    18.142    

FPU FFT
-------

-FPU FFT-
<big><b>This Machine</b></big>    800 MHz    3.864    

FPU Raytracing
--------------

-FPU Raytracing-
<big><b>This Machine</b></big>    800 MHz    13.277    
Intel(R) Celeron(R) M processor         1.50GHz    (null)    40.8816714    
PowerPC 740/750 (280.00MHz)    (null)    161.312647

---

### Post by claracc on 2013-05-25
I think this link: [http://askubuntu.com/questions/139036/how-do-i-fix-a-wireless-is-disabled-by-hardware-switch-error](http://askubuntu.com/questions/139036/how-do-i-fix-a-wireless-is-disabled-by-hardware-switch-error) can help you to fix the problem.

There are different approaches, read the link and try them.

---

### Post by lethall1 on 2013-05-25
[http://askubuntu.com/questions/205704/cannot-get-atheros-ar9285-to-work-on-12-10](http://askubuntu.com/questions/205704/cannot-get-atheros-ar9285-to-work-on-12-10)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/732038](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/732038)
```
[COLOR=#333333][FONT=Ubuntu Mono]sudo apt-get install firmware-[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Mono]b43-installer[/FONT][/COLOR]
```

---

### Post by prantik on 2013-05-29
Hi claracc,

Thanks for your reply.

I have already tried this post. When I list the rfkill, it shows:

```

anindya@anindya-Satellite-C640:~$ sudo rfkill list all
0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
anindya@anindya-Satellite-C640:~$ 
```

As the wifi is not soft blocked, rfkill unblock command doesn't heal anything. 

I have repeatedly pressed the wifi key (Fn+F8) but all in vain.

---

