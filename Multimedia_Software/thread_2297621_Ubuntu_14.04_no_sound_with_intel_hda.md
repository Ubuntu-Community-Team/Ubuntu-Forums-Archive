---
title: "Ubuntu 14.04 no sound with intel hda"
date: 2015-10-05
forum: Multimedia Software
---

### Post by arysar on 2015-10-05
I made some steps in the sound troubleshoting procedure but I am not sure how to continue so I excuted the alsa-info.sh and I hope I can get some help here, thanks!

> 
upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.64
!!################################

!!Script ran on: Mon Oct  5 14:10:51 UTC 2015


!!Linux Distribution
!!------------------

Ubuntu 14.04.3 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 14.04.3 LTS" NAME="Ubuntu" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu 14.04.3 LTS" HOME_URL="http://www.ubuntu.com/" SUPPORT_URL="http://help.ubuntu.com/" BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"


!!DMI Information
!!---------------

Manufacturer:      To Be Filled By O.E.M.
Product Name:      To Be Filled By O.E.M.
Product Version:   To Be Filled By O.E.M.
Firmware Version:  P1.30


!!Kernel Information
!!------------------

Kernel release:    3.13.0-65-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         i686
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     k3.13.0-65-generic
Library version:    1.0.27.2
Utilities version:  1.0.27.2


!!Loaded ALSA modules
!!-------------------



!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes


!!Soundcards recognised by ALSA
!!-----------------------------

--- no soundcards ---


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 01)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!-------------------------------------------------------

00:1b.0 0403: 8086:27d8 (rev 01)
	Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-


!!Modprobe options (Sound related)
!!--------------------------------

snd_atiixp_modem: index=-2
snd_intel8x0m: index=-2
snd_via82xx_modem: index=-2
snd_usb_audio: index=-2
snd_usb_caiaq: index=-2
snd_usb_ua101: index=-2
snd_usb_us122l: index=-2
snd_usb_usx2y: index=-2
snd_cmipci: mpu_port=0x330 fm_port=0x388
snd_pcsp: index=-2
snd_usb_audio: index=-2
snd_hda_intel: model=auto


!!Loaded sound module options
!!---------------------------


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116,  1 Oct  5 09:22 /dev/snd/seq
crw-rw----+ 1 root audio 116, 33 Oct  5 09:22 /dev/snd/timer


!!Aplay/Arecord output
!!--------------------

APLAY

aplay: device_list:268: no soundcards found...

ARECORD

arecord: device_list:268: no soundcards found...

!!Amixer output
!!-------------


!!Alsactl output
!!--------------

--startcollapse--
--endcollapse--


!!All Loaded Modules
!!------------------

Module
dm_crypt
rfcomm
bnep
bluetooth
binfmt_misc
nls_utf8
gpio_ich
coretemp
snd_hda_intel
snd_hda_codec
snd_hwdep
snd_pcm
snd_page_alloc
snd_seq_midi
snd_seq_midi_event
snd_rawmidi
uvcvideo
serio_raw
videobuf2_vmalloc
videobuf2_memops
videobuf2_core
videodev
lpc_ich
snd_seq
snd_seq_device
snd_timer
parport_pc
shpchp
ppdev
mac_hid
snd
lp
soundcore
parport
i915
video
i2c_algo_bit
psmouse
drm_kms_helper
r8169
mii
pata_acpi
drm
floppy


!!ALSA/HDA dmesg
!!--------------

[   15.260683] coretemp coretemp.0: Using relative temperature scale!
[   15.276404] snd_hda_intel 0000:00:1b.0: irq 41 for MSI/MSI-X
[   15.310046] type=1400 audit(1444047721.919:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=380 comm="apparmor_parser"
--
[   15.315162] type=1400 audit(1444047721.923:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/ntpd" pid=400 comm="apparmor_parser"
[   16.296014] hda-intel 0000:00:1b.0: Codec #0 probe error; disabling it...
[   16.702056] EXT4-fs (sdc1): re-mounted. Opts: errors=remount-ro
--
[   21.262013] IPv6: ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   21.344205] hda-intel 0000:00:1b.0: no codecs initialized
[   23.430791] init: plymouth-upstart-bridge main process ended, respawning




---

### Post by dino99 on 2015-10-05
pulseaudio is now very sensitive about hardware settings: 'hda' need to be selected into the bios (not 'ac97'), and jacks have to be stricly plugged by color
to fine tune you can also use 'paref' & 'pavucontrol'

---

### Post by arysar on 2015-10-05
I have checked the hardware settings and didn't find any configurations only that I can enable or disable mother's soundcard. Pavucontrol shows that the sound is not muted and no  sound card to configure but as I saw alsa doesnt recognize any sound card, how can I make alsa to recognize the sound card??

---

