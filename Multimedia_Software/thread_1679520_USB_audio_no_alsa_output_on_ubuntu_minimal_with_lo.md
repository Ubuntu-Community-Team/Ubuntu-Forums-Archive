---
title: "USB audio no alsa output on ubuntu minimal with loaded with xbmc-live"
date: 2011-02-01
forum: Multimedia Software
---

### Post by dEv_ on 2011-02-01
hi all 

i'm kinda new to this ubuntu cli thing. hope the pros here can help me on the following matter. 

the sound system doesnt seem to be working with after i reboot the system. so i decide to upgrade my alsa driver. however, the sound system doesnt seem to be working. 

attached is the code from the alsa-info script

```
upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Tue Feb  1 09:50:28 UTC 2011


!!Linux Distribution
!!------------------

Ubuntu 10.04.1 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"


!!DMI Information
!!---------------

Manufacturer:              
Product Name:              
Product Version:           


!!Kernel Information
!!------------------

Kernel release:    2.6.32-28-generic-pae
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.23
Library version:    1.0.23
Utilities version:  1.0.23


!!Loaded ALSA modules
!!-------------------

snd_usb_audio


!!Sound Servers on this system
!!----------------------------

No sound servers found.


!!Soundcards recognised by ALSA
!!-----------------------------

 1 [HUDmx1         ]: USB-Audio - Audinst HUD-mx1
                      Audinst, Inc. Audinst HUD-mx1 at usb-0000:00:1a.0-2, full speed


!!PCI Soundcards installed in the system
!!--------------------------------------



!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------



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

!!Module: snd_usb_audio
	async_unlink : Y
	device_setup : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
	ignore_ctl_error : N
	index : -2,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	nrpacks : 8
	pid : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	vid : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1


!!USB Mixer information
!!---------------------------
--startcollapse--

USB Mixer: usb_id=0x18527925, ctrlif=1, ctlerr=0
Card: Audinst, Inc. Audinst HUD-mx1 at usb-0000:00:1a.0-2, full speed
  Unit: 11
    Control: name="PCM Capture Source", index=0
    Info: id=11, control=0, cmask=0x0, channels=1, type="U8"
    Volume: min=1, max=2, dBmin=0, dBmax=0
  Unit: 14
    Control: name="Line Capture Volume", index=0
    Info: id=14, control=2, cmask=0x3, channels=2, type="S16"
    Volume: min=-10240, max=3072, dBmin=-4000, dBmax=1200
  Unit: 14
    Control: name="Line Capture Switch", index=0
    Info: id=14, control=1, cmask=0x0, channels=1, type="INV_BOOLEAN"
    Volume: min=0, max=1, dBmin=0, dBmax=0
  Unit: 16
    Control: name="PCM Playback Volume", index=0
    Info: id=16, control=2, cmask=0x3, channels=2, type="S16"
    Volume: min=-14080, max=0, dBmin=-5500, dBmax=0
  Unit: 16
    Control: name="PCM Playback Switch", index=0
    Info: id=16, control=1, cmask=0x0, channels=1, type="INV_BOOLEAN"
    Volume: min=0, max=1, dBmin=0, dBmax=0
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116,  5 Feb  1 17:49 /dev/snd/controlC1
crw-rw----+ 1 root audio 116,  4 Feb  1 17:49 /dev/snd/pcmC1D0c
crw-rw----+ 1 root audio 116,  3 Feb  1 17:49 /dev/snd/pcmC1D0p
crw-rw----+ 1 root audio 116,  2 Feb  1 17:49 /dev/snd/pcmC1D1p
crw-rw----+ 1 root audio 116,  1 Feb  1 17:49 /dev/snd/seq
crw-rw----+ 1 root audio 116, 33 Feb  1 17:49 /dev/snd/timer

/dev/snd/by-id:
total 0
drwxr-xr-x 2 root root  60 Feb  1 17:49 .
drwxr-xr-x 4 root root 200 Feb  1 17:49 ..
lrwxrwxrwx 1 root root  12 Feb  1 17:49 usb-Audinst__Inc._Audinst_HUD-mx1-01 -> ../controlC1

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Feb  1 17:49 .
drwxr-xr-x 4 root root 200 Feb  1 17:49 ..
lrwxrwxrwx 1 root root  12 Feb  1 17:49 pci-0000:00:1a.0-usb-0:2:1.1 -> ../controlC1


!!Aplay/Arecord output
!!------------

APLAY

aplay: device_list:235: no soundcards found...

ARECORD

arecord: device_list:235: no soundcards found...

!!Amixer output
!!-------------

!!-------Mixer controls for card 1 [HUDmx1]

Invalid card number.
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
Invalid card number.
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


!!Alsactl output
!!-------------

--startcollapse--
--endcollapse--


!!All Loaded Modules
!!------------------

Module
nls_iso8859_1
nls_cp437
vfat
fat
snd_usb_audio
snd_pcm_oss
snd_mixer_oss
snd_pcm
snd_page_alloc
snd_hwdep
snd_usbmidi_lib
snd_seq_dummy
snd_seq_oss
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
snd_seq
snd_timer
snd_seq_device
snd
fbcon
tileblit
font
bitblit
softcursor
vga16fb
vgastate
i915
joydev
drm_kms_helper
psmouse
lp
serio_raw
usbhid
soundcore
hid
parport
drm
i2c_algo_bit
video
output
intel_agp
agpgart
raid10
raid456
async_raid6_recov
async_pq
usb_storage
raid6_pq
async_xor
xor
async_memcpy
async_tx
raid1
raid0
multipath
e1000e
linear
ahci


!!ALSA/HDA dmesg
!!------------------

[   14.343019] Console: switching to colour frame buffer device 160x48
[   16.348224] ALSA endpoint.c:448: 2:2:1: add audio endpoint 0x82
[   16.351223] ALSA endpoint.c:448: 2:2:2: add audio endpoint 0x82
[   16.355229] ALSA endpoint.c:448: 2:3:1: add audio endpoint 0x3
[   16.358221] ALSA endpoint.c:448: 2:3:2: add audio endpoint 0x3
[   16.358700] kjournald starting.  Commit interval 5 seconds
[   16.361229] ALSA endpoint.c:448: 2:3:3: add audio endpoint 0x3
[   16.364238] EXT3 FS on dm-1, internal journal
[   16.364242] EXT3-fs: mounted filesystem with ordered data mode.
[   16.365225] ALSA mixer.c:1150: [16] FU [PCM Playback Switch] ch = 1, val = 0/1/1
[   16.378222] ALSA mixer.c:454: cannot set ctl value: req = 0x4, wValue = 0x201, wIndex = 0x1001, type = 4, data = 0x40/0x0
[   16.383223] ALSA mixer.c:1150: [16] FU [PCM Playback Volume] ch = 2, val = -14080/0/128
[   16.383229] ALSA mixer.c:1150: [14] FU [Line Capture Switch] ch = 1, val = 0/1/1
[   16.396222] ALSA mixer.c:454: cannot set ctl value: req = 0x4, wValue = 0x201, wIndex = 0xe01, type = 4, data = 0x40/0x0
[   16.401228] ALSA mixer.c:1150: [14] FU [Line Capture Volume] ch = 2, val = -10240/3072/128
[   16.401233] ALSA mixer.c:1832: [11] SU [PCM Capture Source] items = 2
[   16.401523] usbcore: registered new interface driver snd-usb-audio


```

hope you guys can shed some light on the above matter. thanks.

---

