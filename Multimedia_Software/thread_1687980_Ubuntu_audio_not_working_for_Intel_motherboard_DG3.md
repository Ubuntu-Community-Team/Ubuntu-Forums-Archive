---
title: "Ubuntu audio not working for Intel motherboard DG33BU"
date: 2011-02-14
forum: Multimedia Software
---

### Post by calif99x on 2011-02-14
Hi:

This is a problem that I have had since Ubuntu 8.04 when the sound on my system stopped working.  I have an Intel DG33BU motherboard with audio onboard.

I originally had 7.04 installed on the system (sound worked fine) and did an upgrade to 8.04 for a couple of reasons and found the sound no longer worked.

I have since upgraded to 10.10 and despite trolling various audio threads have yet to get the sound working again.  I have noted that when the system boots up there is a quick message (approximately from memory) 9.32.0061: audio codec not found for hda-intel.

Is there a troubleshooting guide or information someone can point me toward as I would like to solve this problem?

I have been trying to use the information at [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure) to work through the problem.

Output:

WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf.083110, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf-bak, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf.083110, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf-bak, it will be ignored in a future release.
/usr/sbin/alsactl: save_state:1504: No soundcards found...
cat: /tmp/alsa-info.5d6DcEo41d/alsactl.tmp: No such file or directory
upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Tue Feb 15 17:01:44 UTC 2011


!!Linux Distribution
!!------------------

Ubuntu 10.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.10"


!!DMI Information
!!---------------

Manufacturer:              
Product Name:              
Product Version:           


!!Kernel Information
!!------------------

Kernel release:    2.6.35-25-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.23
Library version:    1.0.23
Utilities version:  1.0.23


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

--- no soundcards ---


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:293e (rev 02)
	Subsystem: 8086:0001


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-caiaq: index=-2
snd-usb-ua101: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-usb-audio: index=-2
snd-intel8x0: ac97_quirk=1 buggy_irq=1 enable=1 index=0
snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-caiaq: index=-2
snd-usb-ua101: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-usb-audio: index=-2
snd-hda-intel: model=6stack-dig
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

crw-rw----+ 1 root audio 116, 3 Feb 15 09:00 /dev/snd/seq
crw-rw----+ 1 root audio 116, 2 Feb 15 09:00 /dev/snd/timer


!!Aplay/Arecord output
!!------------

APLAY

aplay: device_list:235: no soundcards found...

ARECORD

arecord: device_list:235: no soundcards found...

!!Amixer output
!!-------------


!!Alsactl output
!!-------------

--startcollapse--
--endcollapse--


!!All Loaded Modules
!!------------------

Module
autofs4
binfmt_misc
vmnet
vmblock
vsock
vmci
vmmon
parport_pc
ppdev
snd_hda_intel
snd_hda_codec
snd_hwdep
snd_pcm
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
snd_seq
i915
snd_timer
snd_seq_device
drm_kms_helper
snd
drm
soundcore
i2c_algo_bit
video
snd_page_alloc
intel_agp
output
lp
parport
usbhid
hid
firewire_ohci
ahci
firewire_core
crc_itu_t
pata_marvell
sata_sil
e1000e
libahci


!!ALSA/HDA dmesg
!!------------------

[   15.432403]   alloc kstat_irqs on node -1
[   15.432410] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   15.432448]   alloc irq_desc for 48 on node -1
[   15.432450]   alloc kstat_irqs on node -1
[   15.432458] HDA Intel 0000:00:1b.0: irq 48 for MSI/MSI-X
[   15.432480] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   15.520026] hda-intel: no codecs found!
[   15.520100] HDA Intel 0000:00:1b.0: PCI INT A disabled
[   15.721330] ppdev: user-space parallel port driver




Thanks
Sandeep

---

### Post by jerrrys on 2011-02-16
audio codec not found ?

you have restricted extras installed ?

---

