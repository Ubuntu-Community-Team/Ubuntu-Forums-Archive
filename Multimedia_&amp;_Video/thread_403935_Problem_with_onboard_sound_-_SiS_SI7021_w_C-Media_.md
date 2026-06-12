---
title: "Problem with onboard sound - SiS SI7021 w/ C-Media CMI9761 chip"
date: 2007-04-07
forum: Multimedia &amp; Video
---

### Post by mudfanatic on 2007-04-07
I'm having problems with the onboard sound on my computer. The built-in audio device is an SiS SI7012 sound controller with a C-Media CMI9761 chip. The sound device is listed in **lspci** but will not function. Period. I have been through the comprehensive sound guide posted on the forums and everything went well, but after reinstalling and reconfiguring alsa with the correct drivers (as per the alsa website) I still have no sound whatsoever. The volume-control applet on the gnome taskbar gives me this error message when I try to open it:

**No volume control GStreamer plugins and/or devices found.**

Even though the sound device is listed in **lspci** the **System->Preferences->Sound** "Default Sound Card" drop-down menu shows no sound cards attached to the system. **However**, the **System->Administration->Device Manager** dialog shows the sound card and all it's sub-components, such as the ALSA PCM Playback Device etc. etc. Why do some system dialogs contradict others? I'm running a fresh install of Ubuntu 6.06 LTS although I had the same problem with Breezy and with Edgy. Any help would be much appreciated!

---

### Post by Shinoda on 2007-04-14
Can you post the output for the following commands?```
lspci | grep -i media
lsmod | grep -i snd
cat /proc/asound/cards
cat /proc/asound/modules
asoundconf list
aplay -l
cat ~/.asoundrc
cat ~/.asoundrc.asoundconf
cat /etc/asound.conf
cat /etc/modprobe.d/alsa-base
```

---

### Post by brigit on 2007-04-14
I feel cheeky but I'm having very similar problems and have tryed everything I've found sugested and if anything its just got worse, here are the out puts to the comarnds you gave, if you can suggest anything, i would be so greatful, 

lspci | grep -i media
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)

lsmod | grep -i snd
snd_intel8x0           34844  1
snd_ac97_codec         97696  1 snd_intel8x0
snd_ac97_bus            3456  1 snd_ac97_codec
snd_pcm_oss            47360  0
snd_mixer_oss          19584  1 snd_pcm_oss
snd_pcm                84612  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25348  1 snd_pcm
snd                    58372  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm

cat /proc/asound/cards
 0 [SI7012         ]: ICH - SiS SI7012
                      SiS SI7012 with CMI9739 at 0xdc00, irq 201

cat /proc/asound/modules
 0 snd_intel8x0

asoundconf list
SI7012

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SI7012 [SiS SI7012], device 0: Intel ICH [SiS SI7012]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

cat ~/.asoundrc
# ALSA library configuration file

# Include settings that are under the control of asoundconf(1).
# (To disable these settings, comment out this line.)
</home/trunk/.asoundrc.asoundconf>

cat ~/.asoundrc.asoundconf
 ALSA library configuration file managed by asoundconf(1).
#
# MANUAL CHANGES TO THIS FILE WILL BE OVERWRITTEN!
#
# Manual changes to the ALSA library configuration should be implemented
# by editing the ~/.asoundrc file, not by editing this file.
!defaults.pcm.card UART
defaults.ctl.card UART
defaults.pcm.device 0
defaults.pcm.subdevice -1
defaults.pcm.nonblock 1
defaults.pcm.ipc_key 5678293
defaults.pcm.ipc_gid audio
defaults.pcm.ipc_perm 0660
defaults.pcm.dmix_max_periods 0
defaults.rawmidi.card 0
defaults.rawmidi.device 0
defaults.rawmidi.subdevice -1
defaults.hwdep.card 0
defaults.hwdep.device 0
defaults.timer.class 2
defaults.timer.sclass 0
defaults.timer.card 0
defaults.timer.device 0
defaults.timer.subdevice 0

cat /etc/asound.conf
cat: /etc/asound.conf: No such file or directory

cat /etc/modprobe.d/alsa-base
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
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --Qb snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }

# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2

---

### Post by jcraveiro on 2007-04-14
[http://ubuntuforums.org/showthread.php?t=409116](http://ubuntuforums.org/showthread.php?t=409116)

---

### Post by brigit on 2007-04-15
thanks alot,I now have soundback,although still having problems with the mic.

---

### Post by tmasboa on 2007-04-19
> **brigit said:**
> thanks alot,I now have soundback,although still having problems with the mic.

I have the same card, and is shows in lcpci and everything and the volume "works" but there is absolutely no sound?

---

### Post by Shinoda on 2007-04-19
Is ALSA chosen for the first 4 options in System > Preferences > Sound > Devices (also use the Test button next to them while you're at it), and the correct card selected both at the bottom of either that or the Sounds tab and in Volume Control's File menu > Change Device?

---

