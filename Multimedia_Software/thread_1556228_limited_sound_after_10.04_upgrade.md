---
title: "limited sound after 10.04 upgrade"
date: 2010-08-19
forum: Multimedia Software
---

### Post by astriemer on 2010-08-19
I also have had some sound problems since upgrading to 10.04 this weekend, 
sound was working fine in 9.10, and if anyone can shed some light on  what is going on I'd appreciate it. I'm fairly computer literate, but am  new to linux.

After the upgrade I initially had no sound and so using some of the  troubleshooting guides I was able to determine that I had some muted  channels and after unmuting everything I now have some sound. However,  I'm not sure that really was the best solution as the channel that seems  to have sound on it appears to be my microphone channel. Furthermore the sound  actually sounds a bit like it is coming from a microphone (it is coming  through the speakers) as it is tinny and a little staticy.

What is really strange however is that other than the startup sound I  don't have any sound unless I have the Sound Preferences dialog box  open. Sound seems to work for any of the programs that I've tried as  long as the Sound Preferences is open or minimized, but otherwise no  sound. As soon as I close the Sound Preferences window the sound stops (though it starts back up again if I open the window back up again).

Here is some other information that may be helpful.

aplay:

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI_1 [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

lspci:

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
    Subsystem: ASUSTeK Computer Inc. Device 8288
    Flags: bus master, slow devsel, latency 64, IRQ 16
    Memory at fe4f4000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

01:00.1 Audio device: ATI Technologies Inc RV630/M76 audio device [Radeon HD 2600 Series]
    Subsystem: VISIONTEK Device aa08
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at fe5ec000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

02:00.1 Audio device: ATI Technologies Inc RV630/M76 audio device [Radeon HD 2600 Series]
    Subsystem: VISIONTEK Device aa08
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at fe6ec000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel


cat /etc/modprobe.d/alsa-base.conf
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
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS &&  { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe  --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS  && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer  $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist  snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS  && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ;  /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi  $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist  snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1  $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist  snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx  $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist  snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS  && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2


Thanks in advance for any help!

Woo Hoo! I figured it out.

Turns out that I had the wrong playback source for my S/PDIF selected. When I changed that to PCM in the alsamixer everything started working correctly.

---

