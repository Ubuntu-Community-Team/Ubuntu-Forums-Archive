---
title: "Conexant on, ALC883 OFF"
date: 2007-05-29
forum: Multimedia &amp; Video
---

### Post by Otpadnik on 2007-05-29
Hi!

I've finally managed to install my conexant modem and just when I was totally happy I've realised that my sound cad stopped working.

It worked just fine until now (after installing feisty it worked by default).

So, it must be that somehow I've managed to do something bad to it, but I dont know what or wen or...

Can someone please help me?

Sound card is Realtek ALC883.

Thanks!

---

### Post by Otpadnik on 2007-05-30
Someone? Anyone?

Ok, let's try to be more specific.
Cause my sound card was detected by default I would like to force feisty to "rescan" for my sound card as when my system was initialed.

Btw, I've noticed that when i type sudo gedit ANYTHING there is bunsh of something in therminal.... Errors and stuff...

Help?
Please?

---

### Post by Otpadnik on 2007-05-30
No one?

Ok, for now I've managed to get this out of my computer:

1. When I use gedit I get this output(and gedit works just fine):

[HTML]user@Computer:~$ gedit
ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3968:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3968:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default[/HTML]

2. ALSA information script gives me:

[HTML]###############################
ALSA Information Script v 0.4.24
################################


Linux Distribution
------------------

Ubuntu 7.04 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 7.04"


Kernel Information
------------------

Kernel release:    2.6.20-15-386
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       No


ALSA Version
------------

Driver version:     1.0.14rc1
Library version:    1.0.13
Utilities version:  1.0.13


Loaded ALSA modules
-------------------

saa7134_alsa


Soundcards recognised by ALSA
-----------------------------

 1 [SAA7134        ]: SAA7134 - SAA7134
                      saa7130[0] at 0xfbfffc00 irq 20


PCI Soundcards installed in the system
--------------------------------------

00:06.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
01:00.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)


Advanced information - PCI Vendor/Device/Susbsystem ID's
--------------------------------------------------------

00:06.1 0403: 10de:0371 (rev a2)
	Subsystem: 1462:7250


HDA-Intel Codec information
---------------------------



ALSA Device nodes
-----------------

crw-rw---- 1 root audio 116, 5 2007-05-30 14:42 /dev/snd/controlC1
crw-rw---- 1 root audio 116, 4 2007-05-30 14:42 /dev/snd/pcmC1D0c
crw-rw---- 1 root audio 116, 3 2007-05-30 14:42 /dev/snd/seq
crw-rw---- 1 root audio 116, 2 2007-05-30 14:42 /dev/snd/timer


Aplay output
------------

**** List of PLAYBACK Hardware Devices ****


Amixer output
-------------

-------Mixer controls for card 0 ]

Usage: amixer <options> [command]

Available options:
  -h,--help       this help
  -c,--card N     select the card
  -D,--device N   select the device, default 'default'
  -d,--debug      debug mode
  -n,--nocheck    do not perform range checking
  -v,--version    print version of this program
  -q,--quiet      be quiet
  -i,--inactive   show also inactive controls
  -a,--abstract L select abstraction level (none or basic)
  -s,--stdin      Read and execute commands from stdin sequentially

Available commands:
  scontrols       show all mixer simple controls
  scontents	  show contents of all mixer simple controls (default command)
  sset sID P      set contents for one mixer simple control
  sget sID        get contents for one mixer simple control
  controls        show all controls for given card
  contents        show contents of all controls for given card
  cset cID P      set control contents for one control
  cget cID        get control contents for one control


All Loaded Modules
------------------

Module
ppp_deflate
zlib_deflate
bsd_comp
ppp_async
crc_ccitt
nls_iso8859_1
nls_cp437
vfat
fat
usb_storage
libusual
binfmt_misc
rfcomm
l2cap
ppdev
powernow_k8
cpufreq_ondemand
cpufreq_powersave
cpufreq_stats
cpufreq_conservative
freq_table
cpufreq_userspace
tc1100_wmi
sony_acpi
dev_acpi
pcc_acpi
asus_acpi
container
battery
ac
backlight
video
dock
button
sbs
i2c_ec
ipv6
ppp_generic
slhc
nls_utf8
ntfs
parport_pc
lp
parport
fuse
saa7134_alsa
snd_pcm_oss
snd_mixer_oss
snd_pcm
snd_seq_dummy
snd_seq_oss
nvidia
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
snd_seq
snd_timer
snd_seq_device
hci_usb
snd
ide_cd
bluetooth
agpgart
rtc
hcfpcihw
hcfpciserial
hcfpciengine
soundcore
cdrom
k8temp
pcspkr
snd_page_alloc
serio_raw
psmouse
saa7134
video_buf
compat_ioctl32
ir_kbd_i2c
ir_common
videodev
v4l2_common
v4l1_compat
shpchp
pci_hotplug
hcfpciosspec
i2c_nforce2
af_packet
i2c_core
evdev
tsdev
ext3
jbd
mbcache
sg
sd_mod
amd74xx
generic
ata_generic
ohci_hcd
forcedeth
sata_nv
libata
scsi_mod
ehci_hcd
usbcore
thermal
processor
fan
fbcon
tileblit
font
bitblit
softcursor
vesafb
capability
commoncap[/HTML]


And SAA7134 is my TV card chip?!
And I cannot do rmmod sa7134_alsa?!!

And I use onboard sound card (motherboard MSI K9N Ultra) and.... HELP!!! PLEASE?

---

### Post by Otpadnik on 2007-05-31
Ok, I've realised that my sound card works perfectly under ubuntu 2.6.20.15-generic, and doesn't work under 2.6.20.15-386...

Why?
I don't know....

Thanks..... for nothing.... i feel really bad, cause noone even wrote "I don't know"

Bye!

---

