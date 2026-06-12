---
title: "No audio coming out of my hdmi port"
date: 2013-06-07
forum: Multimedia Software
---

### Post by fillmore73 on 2013-06-07
I just installed lubuntu and trying to setup a HTPC running XBMC

However not able to get any audio out from the HDMI port. Tried the following

This is my version
cat /proc/version
Linux version 3.8.0-23-generic (buildd@aatxe) (gcc version 4.7.3 (Ubuntu/Linaro 4.7.3-1ubuntu1) ) #34-Ubuntu SMP Wed May 29 20:24:54 UTC 2013




These are the sound drivers/cards available in my system


xbmc@xbmc-GA-E350N:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: SB [HDA ATI SB], device 0: ALC887-VD Analog [ALC887-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: SB [HDA ATI SB], device 1: ALC887-VD Digital [ALC887-VD Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
xbmc@xbmc-GA-E350N:~$ 


------------------
fix1
--------
Tried setting the sound device to card 0 in alsamixer
Still no output


fix2
------
Installed pulseaudio 


ran pavucontrol
set the port to HDMI / DisplayPort


Still no output


fix3
------
got the name of the device via
less /proc/asound/modules 


 0 snd_hda_intel
 1 snd_hda_intel


created the following file
/etc/modprobe.d/sound


Added the following entry in it 
options snd_hda_intel index=1 


and rebooted.
No sound
--------------------
fix 4
--------
This is the content of the following file 


/etc/modprobe.d/alsa-base.conf
do I need to change anything here ?
====================
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
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }


# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2
options snd-hda-intel model=auto


================================
In the above file I tried setting the index values to 
index=0 
index=1 


after each setting did a 


sudo depmod -a
  sudo alsa force-reload


Still no audio.


Appreciate any help in solving my problem

---

### Post by fillmore73 on 2013-06-09
for now I have uninstalled pulseaudio. still same issue.

---

### Post by Yellow Pasque on 2013-06-09
I see you have AMD graphics. Are you running the proprietary fglrx/Catalyst driver or the default open-source driver? If the latter, see id "workaround 1" helps: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/864735](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/864735)

---

### Post by fillmore73 on 2013-06-10
> **Temüjin said:**
> I see you have AMD graphics. Are you running the proprietary fglrx/Catalyst driver or the default open-source driver? If the latter, see id "workaround 1" helps: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/864735](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/864735)

I didn't install any proprietary catalyst drivers yet. So I assume I am running proprietary fglrx.
Will give it a shot today once I get back home. Am at work at the moment.

---

### Post by Yellow Pasque on 2013-06-10
> **fillmore73 said:**
> I didn't install any proprietary catalyst drivers yet. So I assume I am running proprietary fglrx.

fglrx and Catalyst are the same thing. If you didn't install any drivers, then you are using the default open-source radeon driver.

---

### Post by fillmore73 on 2013-06-10
> **Temüjin said:**
> fglrx and Catalyst are the same thing. If you didn't install any drivers, then you are using the default open-source radeon driver.

Did some more googling, Partial success
Audio music files now play just fine.

Video files have a jagged audio feed like start/stop full of breaks :-( Need to fix this now.

Consolidated additional stuff that I did 

[COLOR=#000000][FONT=Arial]file : /etc/modprobe.d/alsa-base.conf
no change , all changes reverted back. it is same as the original updated above.

listing of sound cards
```
cat /proc/asound/cards
 0 [Generic        ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xfe020000 irq 41
 1 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfe024000 irq 16





```

Model of sound card 

```
cat /proc/asound/card0/codec* | grep Codec
Codec: ATI R6xx HDMI


```

Grub change
```
opened /etc/default/grub 
changed 
old line
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

new line
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash radeon.audio=1"

[FONT=Verdana]sudo update-grub[/FONT]
```

rebooted.
[/FONT][/COLOR]
So now audio files work fine, however the audio on video files is not working properly.
Not sure if its something to do with the h/w or anything that I can do to fix it.

Appreciate your help so far.

Additional notes
used alsamixer 
ensured nothing is muted for the HDMI 0 card (as in my case)

The following shows that 
 HDMI is card 0, device 3. OS recognizes it

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: SB [HDA ATI SB], device 0: ALC887-VD Analog [ALC887-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: SB [HDA ATI SB], device 1: ALC887-VD Digital [ALC887-VD Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Listing with capital "L" this time. 
This lists the modes for all cards. 
```

aplay -L 
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    PulseAudio Sound Server
hdmi:CARD=Generic,DEV=0
    HD-Audio Generic, HDMI 0
    HDMI Audio Output
dmix:CARD=Generic,DEV=3
    HD-Audio Generic, HDMI 0
    Direct sample mixing device
dsnoop:CARD=Generic,DEV=3
    HD-Audio Generic, HDMI 0
    Direct sample snooping device
hw:CARD=Generic,DEV=3
    HD-Audio Generic, HDMI 0
    Direct hardware device without any conversions
plughw:CARD=Generic,DEV=3
    HD-Audio Generic, HDMI 0
    Hardware device with all software conversions
default:CARD=SB
    HDA ATI SB, ALC887-VD Analog
    Default Audio Device
sysdefault:CARD=SB
    HDA ATI SB, ALC887-VD Analog
    Default Audio Device
front:CARD=SB,DEV=0
    HDA ATI SB, ALC887-VD Analog
    Front speakers
surround40:CARD=SB,DEV=0
    HDA ATI SB, ALC887-VD Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=SB,DEV=0
    HDA ATI SB, ALC887-VD Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=SB,DEV=0
    HDA ATI SB, ALC887-VD Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=SB,DEV=0
    HDA ATI SB, ALC887-VD Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=SB,DEV=0
    HDA ATI SB, ALC887-VD Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=SB,DEV=0
    HDA ATI SB, ALC887-VD Digital
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=SB,DEV=0
    HDA ATI SB, ALC887-VD Analog
    Direct sample mixing device
dmix:CARD=SB,DEV=1
    HDA ATI SB, ALC887-VD Digital
    Direct sample mixing device
dsnoop:CARD=SB,DEV=0
    HDA ATI SB, ALC887-VD Analog
    Direct sample snooping device
dsnoop:CARD=SB,DEV=1
    HDA ATI SB, ALC887-VD Digital
    Direct sample snooping device
hw:CARD=SB,DEV=0
    HDA ATI SB, ALC887-VD Analog
    Direct hardware device without any conversions
hw:CARD=SB,DEV=1
    HDA ATI SB, ALC887-VD Digital
    Direct hardware device without any conversions
plughw:CARD=SB,DEV=0
    HDA ATI SB, ALC887-VD Analog
    Hardware device with all software conversions
plughw:CARD=SB,DEV=1
    HDA ATI SB, ALC887-VD Digital
    Hardware device with all software conversions 

```

---

### Post by Yellow Pasque on 2013-06-10
The only thing I can suggest for skipping sound is: [https://wiki.ubuntu.com/Audio/PositionReporting](https://wiki.ubuntu.com/Audio/PositionReporting)

---

### Post by FuzzyFeat on 2013-08-15
Grub change
```
opened /etc/default/grub 
changed 
old line
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

new line
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash radeon.audio=1"

[FONT=Verdana]sudo update-grub[/FONT]
```

rebooted.
*********************


You be the MAN!! Worked like a charm for me on 12.04  Thanks for sharing. This thread should be marked [SOLVED] so others may find it.

---

