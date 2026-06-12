---
title: "ATI s-video IN"
date: 2006-10-10
forum: Multimedia &amp; Video
---

### Post by themitchy on 2006-10-10
MY GOAL: playback video coming in on my ATI AIW Radeon 9600's S-Video IN.

ASSUMPTIONS: gatos project drivers KM and AvView are the way to go

RUMORS: I don't need any gatos drivers if I'm using Dapper(confirmations?)

SO FAR:

trying to install km results in the error

make -C /lib/modules/2.6.15-27-686/build M=/home/mitchy/km modules
make: *** /lib/modules/2.6.15-27-686/build: No such file or directory.  Stop.
make: *** [all] Error 2

MY QUESTION: what do I need to install to get what I need under /lib/modules/2.6.15-27-686/ ?


Any other suggestions/experiences to get S-Video IN working on Dapper would be very welcome :D

---

### Post by themitchy on 2006-10-10
Well I've ansewered my question but I'm still having no success.
I needed the package linux-headers-2.6.15-27-686

Now I get the message:

/home/mitchy/km/km.c:1026: error: âPCI_DEVICE_ID_ATI_RADEON_LEâ undeclared here (not in a function)
/home/mitchy/km/km.c:1028: error: âPCI_DEVICE_ID_ATI_RADEON_LFâ undeclared here (not in a function)

---

### Post by themitchy on 2006-10-11
so I've managed to get the gatos km modules and avviewer compiled and running.  Km had to be patched as per [https://www.rocklinux.net/submaster/data/2006/03/2913345407392.patch](https://www.rocklinux.net/submaster/data/2006/03/2913345407392.patch)

When I switch avviewer to s-video input I still just get blackness.

Hours of getting this stuff to compile and run and then nothing.  Has ANYONE actually got s-video input to work on Dapper with ATI?

---

### Post by crokett on 2006-10-11
> **themitchy said:**
>  Has ANYONE actually got s-video input to work on Dapper with ATI?

Yes. I have an ATI All in Wonder Radeon. Mine was new in 2000.  It does not have separate s-video. It has a port that takes a cable that has composite video and svideo on it. I started to do what you did.  Then I decided to assume no problems, downloaded XawTV and was watching video from my camcorder via what XawTV thinks is the s-video connection in just a few minutes.

---

### Post by themitchy on 2006-10-12
Lucky you! :)  Can you tell me which driver you're using?  Do you have a /dev/video0 device?  TVtime complained about no /dev/video0.   I'll try xawtv when I get home.

While we're at it could you post your xorg.conf and the modules you have loaded?

This lack of svideo is a thorn in my side! ](*,)

---

### Post by crokett on 2006-10-14
I do not have a /dev/video0 device.  That is my problem - I need it to capture video.  I don't care so much about watching video as I do about capturing for editing.  

xawtv  can use /dev/video0 for watching but it requires it for capture.  My research says I need to install a module called 'km' - available at the gatos project - to get /dev/video0 for an ATI card.  I am having problems with the compile right now - maybe we can work together on it.

I will post modules and my xorg.conf later but I didn't do anything special to be able to watch video.

---

### Post by crokett on 2006-10-14
okey dokey
<edit>

Forgot to mention that xawtv works for me since it can use video 4 linux and /dev/video but doesn;t have to for watching TV/video/etc.  However it is required for video capture and that is why I want it to work.

Quick question, that patch you linked to in an earlier post, what exactly do I do with it?  I am trying to compile km and have the same exact problem you do.

Loaded modules: - videodev is loaded but I loaded it manually via modprobe.  How do I get it loaded automatically short of recompiling the kernel?
    
```
Module                  Size  Used by
videodev                9856  0 
rfcomm                 40216  0 
l2cap                  26244  5 rfcomm
bluetooth              50020  4 rfcomm,l2cap
ppdev                   9220  0 
radeon                116000  1 
drm                    73236  2 radeon
video                  16260  0 
tc1100_wmi              6916  0 
sony_acpi               5644  0 
pcc_acpi               12416  0 
hotkey                 11556  0 
dev_acpi               11140  0 
container               4608  0 
button                  6672  0 
acpi_sbs               19980  0 
battery                 9988  1 acpi_sbs
ac                      5252  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
ipv6                  265728  10 
nls_utf8                2176  3 
ntfs                  103536  3 
dm_mod                 58936  1 
md_mod                 72532  0 
lp                     11844  0 
af_packet              22920  2 
tsdev                   8000  0 
usblp                  13056  0 
floppy                 62148  0 
pcspkr                  2180  0 
psmouse                36100  0 
serio_raw               7300  0 
rtc                    13492  0 
shpchp                 45632  0 
pci_hotplug            29236  1 shpchp
via686a                17672  0 
snd_ca0106             34212  1 
snd_rawmidi            25504  1 snd_ca0106
snd_seq_device          8716  1 snd_rawmidi
snd_ac97_codec         93216  1 snd_ca0106
snd_pcm_oss            53664  0 
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_ca0106,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
snd                    55268  10 snd_ca0106,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_ac97_bus            2304  1 snd_ac97_codec
e100                   40580  0 
mii                     5888  1 e100
snd_page_alloc         10632  2 snd_ca0106,snd_pcm
i2c_isa                 4992  1 via686a
i2c_viapro              8980  0 
i2c_core               21904  4 i2c_acpi_ec,via686a,i2c_isa,i2c_viapro
parport_pc             35780  1 
parport                36296  3 ppdev,lp,parport_pc
via_agp                 9856  1 
agpgart                34888  2 drm,via_agp
sg                     37920  0 
sr_mod                 16932  0 
evdev                   9856  1 
ext3                  135816  3 
jbd                    58772  1 ext3
usb_storage            74304  0 
ide_generic             1536  0 
ehci_hcd               34184  0 
uhci_hcd               33808  0 
usbcore               130820  5 usblp,usb_storage,ehci_hcd,uhci_hcd
sd_mod                 19984  11 
aic7xxx               183124  16 
scsi_transport_spi2    24960  1 aic7xxx
scsi_mod              139496  6 sg,sr_mod,usb_storage,sd_mod,aic7xxx,scsi_transport_spi2
ide_cd                 33028  0 
cdrom                  38560  2 sr_mod,ide_cd
via82cxxx               9988  0 [permanent]
generic                 5124  0 
thermal                13576  0 
processor              23360  1 thermal
fan                     4868  0 
capability              5000  0 
commoncap               7296  1 capability
vga16fb                13704  1 
vgastate               10368  1 vga16fb
fbcon                  42784  72 
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit

```

And xorg.conf - this is vanilla except the line I added under Modules for v4l - video 4 Linux.  Not that it helped me any...

```

# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"v4l"
        Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon R100 QD [Radeon 7200]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon R100 QD [Radeon 7200]"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by themitchy on 2006-10-15
You can add modules for auto loading to /etc/modules

The patch I posted is just a diff of km.c.  I just applied it manually before running make.  Look for the following line(should be line 871 with km-0.6.1)

```

#define PCI_DEVICE_ID_ATI_RADEON_RD    0x5147
#endif

```

and add the following

```


#ifndef PCI_DEVICE_ID_ATI_RADEON_LE
#define PCI_DEVICE_ID_ATI_RADEON_LE 0x4d45
#endif

#ifndef PCI_DEVICE_ID_ATI_RADEON_LF
#define PCI_DEVICE_ID_ATI_RADEON_LF 0x4d46
#endif

```

If I understand correctly it's because the kernel headers for 2.6.12 and beyond left this out.  

Thanks for posting your configs.  At first glance it seems like xawtv should work for me since I have v4l loaded but I'll dig a little deeper.

---

### Post by crokett on 2006-10-15
xawtv should work for you - it prefers v4l to work but is not required, at least for watching TV.  It is required for capture.

After fighting this for 2 weeks, I decided to repair my XP install and do my video capture there.  I will keep Linux around but I think XP will become my primary OS again. Tried linux a couple times in the last few years and there is always something I need that I can't get working. For a while I thought Ubuntu was it.  there are a lot of good things about Linux but I've always had issues of one sort or another. I dunno, maybe I never have the right HW.

---

### Post by CarpKing on 2006-10-15
Maybe look into [http://www.ubuntuforums.org/showthread.php?t=273291](http://www.ubuntuforums.org/showthread.php?t=273291)

I haven't gotten up the courage to try it yet (especially since I had to install fglrx before I could see anything after installing Dapper), but there seems to be quite a bit of information there.

---

### Post by crokett on 2006-10-16
Thx. I've bookmarked the thread and will try it as I have time.  For now, I got XP installed and was capturing video again in about an hr.  Of course I also discvoered that my USB ports appear to be failing.  :neutral:

---

