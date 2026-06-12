---
title: "No sound in lucid"
date: 2010-07-26
forum: Multimedia Software
---

### Post by BlackMaxPhoto on 2010-07-26
Need help!
:(

---

### Post by BlackMaxPhoto on 2010-07-26
11063148	Yes	VIA Technologies, Inc.	P4M266 Host Bridge	via-agp	
1106b091		VIA Technologies, Inc.	VT8633 [Apollo Pro266 AGP]		
11063038	Yes	VIA Technologies, Inc.	VT82xxxxx UHCI USB 1.1 Controller	usb-uhci,uhci-hcd	
11063038	Yes	VIA Technologies, Inc.	VT82xxxxx UHCI USB 1.1 Controller	usb-uhci,uhci-hcd	
11063038	Yes	VIA Technologies, Inc.	VT82xxxxx UHCI USB 1.1 Controller	usb-uhci,uhci-hcd	
11063104	Yes	VIA Technologies, Inc.	USB 2.0	ehci-hcd	
11063177	Yes	VIA Technologies, Inc.	VT8235 ISA Bridge	i2c-viapro,via-ircc	v2.6.25-
11060571	Yes	VIA Technologies, Inc.	VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE	pata_via,via82cxxx	v2.6.25-
11063059	Yes	VIA Technologies, Inc.	VT8233/A/8235/8237 AC97 Audio Controller	snd-via82xx,via82cxxx_audio	v2.6.25-
11063065	Yes	VIA Technologies, Inc.	VT6102 [Rhine-II]	via-rhine	v2.6.25-
53338d04	Yes	S3 Inc.	VT8375 [ProSavage8 KM266/KL266]	savagefb	v2.6.25-

---

### Post by lidex on 2010-07-26
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -1 /proc/asound/card0/codec97#0/ac97#0-0 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)
```
sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
```
```
dmesg | grep -C1 -E 'ALSA|HDA|HDMI|sound|hda.codec|hda.intel'
```

---

### Post by BlackMaxPhoto on 2010-07-26
```
 uname -a
Linux  2.6.32-24-generic #38-Ubuntu SMP Mon Jul 5 09:22:14 UTC 2010 i686 GNU/Linux
-desktop:~$ aplay -l
aplay: device_list:223: no soundcards found...
-desktop:~$ dpkg -l | grep "alsa"
ii  alsa-base                             1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-oss                              1.0.17-3                                        ALSA wrapper for OSS applications
ii  alsa-utils                            1.0.22-0ubuntu5                                 ALSA utilities
ii  alsaplayer-common                     0.99.80-5                                       PCM player designed for ALSA (common files)
ii  alsaplayer-gtk                        0.99.80-5                                       PCM player designed for ALSA (GTK+ version)
ii  alsaplayer-oss                        0.99.80-5                                       PCM player designed for ALSA (OSS output module)
ii  bluez-alsa                            4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                    0.10.28-1                                       GStreamer plugin for ALSA
rc  libesd-alsa0                          0.2.41-5                                        Enlightened Sound Daemon (ALSA) - Shared libraries
rc  libsdl1.2debian-alsa                  1.2.13-4ubuntu4                                 Simple DirectMedia Layer (with X11 and ALSA options)
ii  libsox-fmt-alsa                       14.3.0-1.1build1                                SoX alsa format I/O library
desktop:~$ head -1 /proc/asound/card0/codec97#0/ac97#0-0
head: cannot open `/proc/asound/card0/codec97#0/ac97#0-0' for reading: No such file or directory
desktop:~$ 


```


VIA Technologies, Inc.	VT8233/A/8235/8237 AC97 Audio Controller	snd-via82xx,via82cxxx_audio	v2.6.25-

---

### Post by lidex on 2010-07-26
Try re-installing alsa. Using a Terminal="Applications->Accessories->Terminal"
```
sudo apt-get update
sudo apt-get upgrade
```
```
sudo apt-get purge linux-sound-base alsa-base alsa-utils

```
```
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop

```
**gdm and ubuntu-desktop usually get taken out in the process, so we add them back**
**Reboot.**

---

### Post by BlackMaxPhoto on 2010-07-26
Reboot and still no sound
:popcorn:

---

### Post by lidex on 2010-07-26
How about aplay -l now?

Better still. Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Provide a link for the output or post it here using code tags.

---

### Post by BlackMaxPhoto on 2010-07-26
```
aplay: device_list:223: no soundcards found...
```



:popcorn:

---

### Post by BlackMaxPhoto on 2010-07-26
```
upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.59
!!################################

!!Script ran on: Tue Jul 27 01:31:21 UTC 2010


!!Linux Distribution
!!------------------

Ubuntu 10.04.1 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"


!!DMI Information
!!---------------

Manufacturer:      VIA Technologies, Inc.
Product Name:      P4M266-8235


!!Kernel Information
!!------------------

Kernel release:    2.6.32-24-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     
Library version:    1.0.22
Utilities version:  1.0.22


!!Loaded ALSA modules
!!-------------------



!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------



!!PCI Soundcards installed in the system
!!--------------------------------------

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:11.5 0401: 1106:3059 (rev 50)
	Subsystem: 16f3:4765


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-usb-caiaq: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2


!!Loaded sound module options
!!--------------------------


!!ALSA Device nodes
!!-----------------



!!Aplay/Arecord output
!!------------

APLAY

aplay: device_list:223: no soundcards found...

ARECORD

arecord: device_list:223: no soundcards found...

!!Amixer output
!!-------------


!!Alsactl output
!!-------------

--startcollapse--
--endcollapse--


!!All Loaded Modules
!!------------------

Module
savage
drm
binfmt_misc
oss_usb
oss_via823x
osscore
fbcon
tileblit
font
bitblit
softcursor
i2c_viapro
vga16fb
vgastate
via_ircc
ppdev
ns558
via_agp
lp
joydev
psmouse
serio_raw
irda
crc_ccitt
gameport
parport_pc
shpchp
agpgart
parport
usbhid
hid
via_rhine
mii
pata_via
floppy


!!ALSA/HDA dmesg
!!------------------



```

---

### Post by lidex on 2010-07-26
Your alsa install is borked, as I suspected. Try re-installing again, with this slight variation.
First
```
sudo apt-get purge linux-sound-base alsa-base alsa-utils alsa-oss alsaplayer-oss libesd-alsa0 libsdl1.2debian-alsa   
```
Next
```
sudo apt-get install linux-sound-base alsa-base alsa-utils alsa-oss gdm ubuntu-desktop
```
**Reboot**

---

### Post by BlackMaxPhoto on 2010-07-26
... no sound

```
upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.59
!!################################

!!Script ran on: Tue Jul 27 01:57:46 UTC 2010


!!Linux Distribution
!!------------------

Ubuntu 10.04.1 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"


!!DMI Information
!!---------------

Manufacturer:      VIA Technologies, Inc.
Product Name:      P4M266-8235


!!Kernel Information
!!------------------

Kernel release:    2.6.32-24-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     
Library version:    1.0.22
Utilities version:  1.0.22


!!Loaded ALSA modules
!!-------------------



!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------



!!PCI Soundcards installed in the system
!!--------------------------------------

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:11.5 0401: 1106:3059 (rev 50)
	Subsystem: 16f3:4765


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-usb-caiaq: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2


!!Loaded sound module options
!!--------------------------


!!ALSA Device nodes
!!-----------------



!!Aplay/Arecord output
!!------------

APLAY

aplay: device_list:223: no soundcards found...

ARECORD

arecord: device_list:223: no soundcards found...

!!Amixer output
!!-------------


!!Alsactl output
!!-------------

--startcollapse--
--endcollapse--


!!All Loaded Modules
!!------------------

Module
binfmt_misc
savage
drm
oss_usb
oss_via823x
osscore
fbcon
tileblit
i2c_viapro
font
bitblit
softcursor
ns558
vga16fb
vgastate
via_ircc
psmouse
ppdev
via_agp
lp
gameport
parport_pc
shpchp
irda
serio_raw
agpgart
joydev
parport
crc_ccitt
usbhid
hid
via_rhine
mii
pata_via
floppy


!!ALSA/HDA dmesg
!!------------------



```

---

### Post by lidex on 2010-07-26
Wow. How old is this board? A little more info please:
```
sudo lshw -C multimedia
sudo dmidecode -t bios
sudo dmidecode -t baseboard
```

---

### Post by BlackMaxPhoto on 2010-07-26
11063148	Yes	VIA Technologies, Inc.	P4M266 Host Bridge	via-agp	
1106b091	 VIA Technologies, Inc.	VT8633 [Apollo Pro266 AGP]	
11063038	Yes	VIA Technologies, Inc.	VT82xxxxx UHCI USB 1.1 Controller	usb-uhci,uhci-hcd	
11063038	Yes	VIA Technologies, Inc.	VT82xxxxx UHCI USB 1.1 Controller	usb-uhci,uhci-hcd	
11063038	Yes	VIA Technologies, Inc.	VT82xxxxx UHCI USB 1.1 Controller	usb-uhci,uhci-hcd	
11063104	Yes	VIA Technologies, Inc.	USB 2.0	ehci-hcd	
11063177	Yes	VIA Technologies, Inc.	VT8235 ISA Bridge	i2c-viapro,via-ircc	v2.6.25-
11060571	Yes	VIA Technologies, Inc.	VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE	pata_via,via82cxxx	v2.6.25-
11063059	Yes	VIA Technologies, Inc.	VT8233/A/8235/8237 AC97 Audio Controller	snd-via82xx,via82cxxx_audio	v2.6.25-
11063065	Yes	VIA Technologies, Inc.	VT6102 [Rhine-II]	via-rhine	v2.6.25-
53338d04	Yes	S3 Inc.	VT8375 [ProSavage8 KM266/KL266]	savagefb	v2.6.25-

The BIOS date is 2003
... old 266mhz buss board

---

### Post by BlackMaxPhoto on 2010-07-26
```
 *-multimedia            
       description: Multimedia audio controller
       product: VT8233/A/8235/8237 AC97 Audio Controller
       vendor: VIA Technologies, Inc.
       physical id: 11.5
       bus info: pci@0000:00:11.5
       version: 50
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: driver=oss_via823x latency=0
       resources: irq:5 ioport:e000(size=256)

```

```
# dmidecode 2.9
SMBIOS 2.3 present.

Handle 0x0000, DMI type 0, 20 bytes
BIOS Information
	Vendor: Phoenix Technologies, LTD
	Version: 6.00 PG
	Release Date: 11/20/2003
	Address: 0xE0000
	Runtime Size: 128 kB
	ROM Size: 256 kB
	Characteristics:
		ISA is supported
		PCI is supported
		PNP is supported
		APM is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		Boot from CD is supported
		Selectable boot is supported
		BIOS ROM is socketed
		EDD is supported
		5.25"/360 KB floppy services are supported (int 13h)
		5.25"/1.2 MB floppy services are supported (int 13h)
		3.5"/720 KB floppy services are supported (int 13h)
		3.5"/2.88 MB floppy services are supported (int 13h)
		Print screen service is supported (int 5h)
		8042 keyboard services are supported (int 9h)
		Serial services are supported (int 14h)
		Printer services are supported (int 17h)
		CGA/mono video services are supported (int 10h)
		ACPI is supported
		USB legacy is supported
		AGP is supported
		LS-120 boot is supported
		ATAPI Zip drive boot is supported

Handle 0x001E, DMI type 13, 22 bytes
BIOS Language Information
	Installable Languages: 3
		n|US|iso8859-1
		n|US|iso8859-1
		r|CA|iso8859-1
	Currently Installed Language: n|US|iso8859-1

```

```
# dmidecode 2.9
SMBIOS 2.3 present.

Handle 0x0003, DMI type 2, 8 bytes
Base Board Information
	Manufacturer:  
	Product Name: P4M266-8235
	Version:  
	Serial Number: 
```

---

### Post by lidex on 2010-07-26
You may want to stick with an older release or try a bios update and we can try to get it working with lucid.

---

### Post by Yellow Pasque on 2010-07-27
> configuration: driver=oss_via823x latency=0
It looks like you tried to install OSS4 and didn't properly uninstall it.

---

### Post by lidex on 2010-07-27
> **Temüjin said:**
> It looks like you tried to install OSS4 and didn't properly uninstall it.

Totally missed that - good eye *Temüjin*.
I'm getting a little weary of dealing with the casualties of these posters pushing OSS as a fix for everything.

---

### Post by BlackMaxPhoto on 2010-07-27
> **Temüjin said:**
> It looks like you tried to install OSS4 and didn't properly uninstall it.

... exactly, OSS worked in Karmic, Karmic was updated to Lucid and then no sound again.

---

### Post by Yellow Pasque on 2010-07-27
Well, if OSS4 works for you, then you should probably update it and/or redo the steps in the OpenSound guide, because upgrading to a new Ubuntu generally installs the ubuntu-desktop meta-package and thus, ALSA/pulse stuff.

> I'm getting a little weary of dealing with the casualties of these posters pushing OSS as a fix for everything.
I once actively suggested OSS4 as a fix for many and wrote a guide on how to install it, but quickly figured out that OSS4 is best left for Ubuntu'ers to discover and play with on their own.

---

### Post by lidex on 2010-07-27
> **Temüjin said:**
> 
I once actively suggested OSS4 as a fix for many and wrote a guide on how to install it, but quickly figured out that OSS4 is best left for Ubuntu'ers to discover and play with on their own.
As you well know, there is a place for it, although certainly not for everyone. I do appreciate your approach.

---

