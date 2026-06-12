---
title: "Sound works but very quiet"
date: 2007-06-30
forum: Multimedia &amp; Video
---

### Post by MiSS_n00b on 2007-06-30
Hi I have installed Ubuntu feisty on my toshiba a100 pro laptop today, and at first the sound did not work at all.  I followed the instructions on [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) to compile and install the latest alsa driver.  When I type cat /proc/asound/card0/codec\#* it gives me this: 

```

Codec: Realtek ALC861
Address: 0
Vendor Id: 0x10ec0861
Subsystem Id: 0x11791205
Revision Id: 0x100300
Default PCM:
    rates [0x140]: 48000 96000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
Node 0x03 [Audio Output] wcaps 0x405: Stereo Amp-Out
  Amp-Out caps: N/A
  Amp-Out vals:  [0x00 0x00]
  Power: 0x0
Node 0x04 [Audio Output] wcaps 0x405: Stereo Amp-Out
  Amp-Out caps: N/A
  Amp-Out vals:  [0x00 0x00]
  Power: 0x0
Node 0x05 [Audio Output] wcaps 0x405: Stereo Amp-Out
  Amp-Out caps: N/A
  Amp-Out vals:  [0x00 0x00]
  Power: 0x0
Node 0x06 [Audio Output] wcaps 0x405: Stereo Amp-Out
  Amp-Out caps: N/A
  Amp-Out vals:  [0x00 0x00]
  Power: 0x0
Node 0x07 [Audio Output] wcaps 0x605: Stereo Digital Amp-Out
  Amp-Out caps: N/A
  Amp-Out vals:  [0x00 0x00]
  Power: 0x0
Node 0x08 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Amp-In caps: ofs=0x02, nsteps=0x0d, stepsize=0x0b, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00] [0x00 0x00]
  PCM:
    rates [0x140]: 48000 96000
    bits [0x2]: 16
    formats [0x1]: PCM
  Power: 0x0
  Connection: 6
     0x0d 0x0c 0x0f 0x10 0x11 0x15*
Node 0x09 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0a [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0b [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x081f: OUT HP Detect
  Pin Default 0x01014110: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Green
  Pin-ctls: 0x40: OUT
  Power: 0x0
  Connection: 1
     0x16
Node 0x0c [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x0837: IN OUT Detect
  Pin Default 0x9983012e: [Fixed] Line In at Int ATAPI
    Conn = ATAPI, Color = Unknown
  Pin-ctls: 0x20: IN
  Power: 0x0
  Connection: 1
     0x19
Node 0x0d [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x08337: IN OUT Detect
  Pin Default 0x01a19920: [Jack] Mic at Ext Rear
    Conn = 1/8, Color = Pink
  Pin-ctls: 0x24: IN
  Power: 0x0
  Connection: 1
     0x18
Node 0x0e [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x0817: OUT Detect
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
  Pin-ctls: 0x40: OUT
  Power: 0x0
  Connection: 1
     0x19
Node 0x0f [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x0833f: IN OUT HP Detect
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
  Pin-ctls: 0xc0: OUT HP
  Power: 0x0
  Connection: 1
     0x1a
Node 0x10 [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x0833f: IN OUT HP Detect
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
  Pin-ctls: 0x24: IN
  Power: 0x0
  Connection: 1
     0x1b
Node 0x11 [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x0863: IN
  Pin Default 0x99330121: [Fixed] CD at Int ATAPI
    Conn = ATAPI, Color = Unknown
  Pin-ctls: 0x00:
Node 0x12 [Pin Complex] wcaps 0x400301: Stereo Digital
  Pincap 0x0810: OUT
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x07
Node 0x13 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x14 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x0d 0x10
Node 0x15 [Audio Mixer] wcaps 0x20050f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x0c, nsteps=0x17, stepsize=0x0b, mute=1
  Amp-In vals:  [0x00 0x00] [0x97 0x97] [0x00 0x00]
  Amp-Out caps: ofs=0x0c, nsteps=0x0c, stepsize=0x0b, mute=1
  Amp-Out vals:  [0x0c 0x0c]
  Power: 0x0
  Connection: 3
     0x11 0x14 0x1c
Node 0x16 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x00 0x00]
  Connection: 2
     0x03 0x15
Node 0x17 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x04 0x15
Node 0x18 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x05 0x15
Node 0x19 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x06 0x15
Node 0x1a [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x00 0x00] [0x00 0x00]
  Connection: 4
     0x04 0x06 0x15 0x03
Node 0x1b [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 4
     0x04 0x06 0x15 0x03
Node 0x1c [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x0c 0x0f
Node 0x1d [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x1e [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x1f [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x0817: OUT Detect
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
  Pin-ctls: 0x40: OUT
  Power: 0x0
  Connection: 1
     0x18
Node 0x20 [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x0817: OUT Detect
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
  Pin-ctls: 0x40: OUT
  Power: 0x0
  Connection: 1
     0x17
Node 0x21 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x22 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x23 [Beep Generator Widget] wcaps 0x70000c: Mono Amp-Out
  Amp-Out caps: ofs=0x0f, nsteps=0x0f, stepsize=0x0b, mute=1
  Amp-Out vals:  [0x8f]
Codec: Generic 11c1 Si3054
Address: 1
Vendor Id: 0x11c13026
Subsystem Id: 0x11790001
Revision Id: 0x100700

```

So after following the instructions on the webpage I was reading I added the line
```
options snd-hda-intel model=toshiba
``` to the end of my /etc/modprobe.d/alsa-base file.  It now reads:
```

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

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
options snd-hda-intel model=toshiba

```

Now the sound is working, but even with all volume controls at max level I can barely hear it, in any application I tried, xmms, vlc, banshee etc.  SOmebody in the irc room mentioned I should change the external amplifier setting but I can't seem to find that setting. Any help would be much appreciated, I have been trying to fix this for hours and I'm pretty new to linux and I really don't wanna stuff it up.  thank you

---

### Post by RTrev on 2007-06-30
I had very quiet sound also, and found that opening the AlsaMixer Volume Control and moving up the PCM slider was all that was needed.  I put mine almost but not quite all the way up.  HTH.

---

### Post by happyxix on 2007-07-04
Mine was like that when I first installed it. I moved the mixer stuff to the top and its still low. But after shutting down and sleeping.. it magically worked.. so perhaps you should restart it?

---

### Post by Colsta on 2007-10-24
I don't know if you managed to find a solution, but you might like to try what's been discussed in this thread:

[http://ubuntuforums.org/showthread.php?t=373287](http://ubuntuforums.org/showthread.php?t=373287)

---

