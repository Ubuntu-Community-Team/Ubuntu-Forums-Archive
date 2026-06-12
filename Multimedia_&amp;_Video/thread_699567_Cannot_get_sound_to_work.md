---
title: "Cannot get sound to work"
date: 2008-02-17
forum: Multimedia &amp; Video
---

### Post by ptoye on 2008-02-17
I'm sure that this question has been answered here many times, but searching doesn't seem to find the solution.

I'm a newbie to Linux (though not to Unix) and am trying to get a fairly old box to work.The sound hardware's a SB Live! card dating from about 2001.

Installed Gutsy Gibbon Ubuntu with no problems, I switched the sound preferences to ALSA (I assume this is correct - the help file is out of date and is not much help). When I try the test buttons I get "audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing."http://ubuntuforums.org/showthread.php?t=205449

Opening a terminal window and trying alsamixer I get "alsamixer: function snd_ctl_open failed for default: No such device"

I've read [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) and I think everything's set up OK. alsaplay -l shows the card with driver emu10k1. lspci -v shows the device as being there. 

I've edited /etc/modprobe.d/alsa-base to include the driver with option=0 (and rebooted after)

I've even removed and reinstalled the sound modules in case plugging in a USB sound card screwed things up.

And still the same happens.

Can someone pleeease help me to get it to work? This was meant to be a spare-time activity :-(>

---

### Post by ptoye on 2008-02-22
What, no-one willing to help?

---

### Post by lifewithryan on 2008-02-22
for the thread that you said you followed...could we get what your output was?  Sound is always tough for me to troubleshoot, bit I haven't had trouble with getting it to work in years....its normally just fine out of the box.

So if you can get us more information...(be very verbose) I'm sure someone can help out.

My first question...does any of this work as "root" (or with sudo I suppose)?

---

### Post by ptoye on 2008-02-24
Thanks for the encouragement. I hope this isn't too verbose.

Contents of various /proc/asounds files:

/proc/asound$ cat cards
 0 [Live           ]: EMU10K1 - SBLive! Value [CT4830]
                      SBLive! Value [CT4830] (rev.7, serial:0x80261102) at 0xd400, irq 11

/proc/asound$ cat devices
  2:        : timer
  3:        : sequencer
  4: [ 0- 0]: hardware dependent
  5: [ 0- 0]: raw midi
  6: [ 0- 3]: digital audio playback
  7: [ 0- 2]: digital audio playback
  8: [ 0- 2]: digital audio capture
  9: [ 0- 1]: digital audio capture
 10: [ 0- 0]: digital audio playback
 11: [ 0- 0]: digital audio capture
 12: [ 0]   : control
 13: [ 0- 2]: hardware dependent
 14: [ 0- 1]: raw midi
 15: [ 0- 2]: raw midi

/proc/asound$ cat hwdep
00-00: EMU10K1 (FX8010)
00-02: Emux WaveTable

/proc/asound$ cat version
Advanced Linux Sound Architecture Driver Version 1.0.14 (Thu May 31 09:03:25 2007 UTC).

/proc/asound$ cat modules
 0 snd_emu10k1

/proc/asound$ cat pcm
00-03: emu10k1 : Multichannel Playback : playback 1
00-02: emu10k1 efx : Multichannel Capture/PT Playback : playback 8 : capture 1
00-01: emu10k1 mic : Mic Capture : capture 1
00-00: emu10k1 : ADC Capture/Standard PCM Playback : playback 32 : capture 1

/proc/asound$ cat timers
G0: system timer : 4000.000us (10000000 ticks)
C0-0: EMU10K1 timer : 20.833us (1024 ticks)
P0-0-0: PCM playback 0-0-0 : SLAVE
P0-0-1: PCM capture 0-0-1 : SLAVE
P0-0-2: PCM playback 0-0-2 : SLAVE
P0-0-4: PCM playback 0-0-4 : SLAVE
P0-0-6: PCM playback 0-0-6 : SLAVE
P0-0-8: PCM playback 0-0-8 : SLAVE
P0-0-10: PCM playback 0-0-10 : SLAVE
P0-0-12: PCM playback 0-0-12 : SLAVE
P0-0-14: PCM playback 0-0-14 : SLAVE
P0-0-16: PCM playback 0-0-16 : SLAVE
P0-0-18: PCM playback 0-0-18 : SLAVE
P0-0-20: PCM playback 0-0-20 : SLAVE
P0-0-22: PCM playback 0-0-22 : SLAVE
P0-0-24: PCM playback 0-0-24 : SLAVE
P0-0-26: PCM playback 0-0-26 : SLAVE
P0-0-28: PCM playback 0-0-28 : SLAVE
P0-0-30: PCM playback 0-0-30 : SLAVE
P0-0-32: PCM playback 0-0-32 : SLAVE
P0-0-34: PCM playback 0-0-34 : SLAVE
P0-0-36: PCM playback 0-0-36 : SLAVE
P0-0-38: PCM playback 0-0-38 : SLAVE
P0-0-40: PCM playback 0-0-40 : SLAVE
P0-0-42: PCM playback 0-0-42 : SLAVE
P0-0-44: PCM playback 0-0-44 : SLAVE
P0-0-46: PCM playback 0-0-46 : SLAVE
P0-0-48: PCM playback 0-0-48 : SLAVE
P0-0-50: PCM playback 0-0-50 : SLAVE
P0-0-52: PCM playback 0-0-52 : SLAVE
P0-0-54: PCM playback 0-0-54 : SLAVE
P0-0-56: PCM playback 0-0-56 : SLAVE
P0-0-58: PCM playback 0-0-58 : SLAVE
P0-0-60: PCM playback 0-0-60 : SLAVE
P0-0-62: PCM playback 0-0-62 : SLAVE
P0-1-1: PCM capture 0-1-1 : SLAVE
P0-2-0: PCM playback 0-2-0 : SLAVE
P0-2-1: PCM capture 0-2-1 : SLAVE
P0-2-2: PCM playback 0-2-2 : SLAVE
P0-2-4: PCM playback 0-2-4 : SLAVE
P0-2-6: PCM playback 0-2-6 : SLAVE
P0-2-8: PCM playback 0-2-8 : SLAVE
P0-2-10: PCM playback 0-2-10 : SLAVE
P0-2-12: PCM playback 0-2-12 : SLAVE
P0-2-14: PCM playback 0-2-14 : SLAVE
P0-3-0: PCM playback 0-3-0 : SLAVE

/proc/asound$ cat /etc/modprobe.d/alsa-base
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
options snd-emu10k1 index=0

And after all that, here are the results of trying to do something:

/proc/asound$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device

/proc/asound$ sudo alsamixer
[sudo] password for ptoye:

alsamixer: function snd_ctl_open failed for default: No such device

/proc/asound$ aplay
ALSA lib confmisc.c:769:(parse_card) cannot find card '&#65533;g_driver'
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3982:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM default
aplay: main:545: audio open error: No such device

/proc/asound$ arecord
ALSA lib confmisc.c:769:(parse_card) cannot find card '&#65533;g_driver'
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3982:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM default
arecord: main:545: audio open error: No such device


And in GNOME System|preferences|Sound, trying to test a playback I get a window saying:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing.

When testing  recording I get a similar message:
gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not open resource for writing.

When trying to use Sound Recorder I get a window saying:
Your audio capture settings are invalid. Please correct them in the Multimedia settings.

I hope that's enough for someone to be looking at.

I don't remember the long set of error messages on aplay and arecord before. Ths only change I made was to add snd-emu10k1 to /etc/modules as recommended by LordRaiden.

---

### Post by ptoye on 2008-03-01
Well, that didn't work, did it. I think I'm back to WIndows. So much for the "community".

---

