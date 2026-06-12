---
title: "Lucid &amp; fglrx issues"
date: 2010-06-18
forum: Multimedia Software
---

### Post by SmokingMan on 2010-06-18
Hey all!

I've got a problem that has me at a loss, so I need some new suggestions. I'm still pretty green to Linux, so that is an additional hurdle. ;)

I am running Ubuntu Studio 10.04 Lucid Lynx and have an ATI HD2400 Pro AGP card that are having issues with each other. I previously ran this same hardware setup in Karmic with the ATI (fglrx) Catalyst 10.1 drivers with no major issues. After upgrading to Lucid, the fglrx stopped working. After trying other versions of the ATI drivers (10.4, 10.5 & 10.6) and also trying the Lucid native ati/radeon drivers, I still only get partial functionality. Automatic install of the ATI packages and manual builds produced the same results. I also tried the Proprietary Hardware Drivers installer from Ubuntu and it failed to install as well.

I have removed/purged all of the above drivers along with xorg-server and reinstalled in various combinations with no real success. I currently have installed the 10.6 drivers that I built packages for Lucid but still have issues with fglrx. 

lsmod does not show fglrx loaded.

```
Module                  Size  Used by
binfmt_misc             8444  1 
snd_hda_codec_atihdmi     3412  1 
snd_hda_intel          26824  0 
snd_cmipci             32992  4 
snd_hda_codec          76052  2 snd_hda_codec_atihdmi,snd_hda_intel
gameport               11996  1 snd_cmipci
snd_opl3_lib           10612  1 snd_cmipci
snd_hwdep               7416  2 snd_hda_codec,snd_opl3_lib
snd_pcm_oss            38112  0 
snd_mpu401_uart         7092  1 snd_cmipci
snd_mixer_oss          16564  1 snd_pcm_oss
snd_pcm                75096  5 snd_hda_intel,snd_cmipci,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2680  0 
snd_seq_oss            28736  0 
snd_seq_midi            6560  0 
it87                   19428  0 
hwmon_vid               2932  1 it87
snd_rawmidi            22240  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      7092  2 snd_seq_oss,snd_seq_midi
lp                      9604  0 
snd_seq                50896  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
sis_agp                 6996  1 
i2c_sis96x              3992  0 
ppdev                   6712  0 
agpgart                35440  1 sis_agp
parport_pc             31812  1 
snd_timer              22040  3 snd_opl3_lib,snd_pcm,snd_seq
snd_seq_device          6944  6 snd_opl3_lib,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    60740  22 snd_hda_intel,snd_cmipci,snd_hda_codec,snd_opl3_lib,snd_hwdep,snd_pcm_oss,snd_mpu401_uart,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport                35976  3 lp,ppdev,parport_pc
soundcore               7968  1 snd
snd_page_alloc          9244  2 snd_hda_intel,snd_pcm
shpchp                 32712  0 
serio_raw               5432  0 
usbhid                 38144  0 
sis900                 20148  0 
mii                     5204  1 sis900
floppy                 55300  0 
dm_raid45              84892  0 
xor                     7420  1 dm_raid45
```

fglrxinfo gives this:
```
~$ fglrxinfo
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  15
  Current serial number in output stream:  15
```

xorg.conf does show fglrx as the driver:
```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection
```

The ATI CCC runs and shows that it is using 10.5 drivers though they were removed previously. However it doesn't show a version of OpenGL that is being used.

Any ideas on how I can resolve this?
Thanks in advance. :)

---

### Post by latebeat on 2010-07-04
any updates on the issue? I have exactly the same problem and I was wondering...

---

