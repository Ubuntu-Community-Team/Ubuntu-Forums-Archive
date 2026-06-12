---
title: "Unable to get sound working + other weird issue. Ubuntu 19.04"
date: 2019-05-12
forum: Multimedia Software
---

### Post by alankong on 2019-05-12
I encountered an issue where all my sound is not working although it seems the hardware is detected.
There is no sound and in the sound setting, I could not select my correct sound card, just blank.

This happened after I left my computer in sleep mode for too long till the battery was finished and when I restore power to it and reboot, the sound doesnt work. It was working prefect before this incident. I could detect most of the stuff. I had also change abit of grub setting prior to this and am not sure if this is an issue. I also was trying out some video recording app like Kazam and EasyScreenCast. I left the app on before my computer goes into sleep mode (no recording).

My guess might be a software driver issue which I didnt have much luck finding information online.
Here is the few specs for reference.

uname -l
```
Linux alankong-APEX-17 5.0.0-13-generic #14-Ubuntu SMP Mon Apr 15 14:59:14 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux
```

aplay -l
```
**** List of PLAYBACK Hardware Devices ****card 0: PCH [HDA Intel PCH], device 0: Generic Analog [Generic Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: Generic Digital [Generic Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Audio [Sennheiser Main Audio], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Audio [Sennheiser Main Audio], device 1: USB Audio [USB Audio #1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

cat /proc/asound/version
```
Advanced Linux Sound Architecture Driver Version k5.0.0-13-generic.
```

head -n 1 /proc/asound/card*/codec#*
```
==> /proc/asound/card0/codec#0 <==Codec: Realtek Generic


==> /proc/asound/card0/codec#2 <==
Codec: Intel Generic


==> /proc/asound/card2/codec#0 <==
Codec: Nvidia GPU 93 HDMI/DP
```


cat /etc/modprobe.d/alsa-base.conf

```
# autoloader aliasesinstall sound-slot-0 /sbin/modprobe snd-card-0
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
options snd-hda-intel model=generic
```

I added the line below after much searching on google but this did not solve my sound issue.
```
options snd-hda-intel model=generic
``` to ```
etc/modprobe.d/alsa-base.conf
```\

The list of other weird issue that came of the sound not working:
[LIST]
[*]Some of my app such as Terminal, Files and Screenshot was not able to start. I had to change the Region & Language to make it run, each time I use it.
[*]Video on Youtube could not be played. Kept in the Loading stage
[*]No Sound in any of my application including using Video conference app, Spotify etc. Video Conference App cannot detect my speaker as well as my headphone and mic via usb.
[/LIST]

---

### Post by TheFu on 2019-05-13
There is a sound-troubleshooting guide [https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)  

Ubuntu switched to using Pulse Audio a few years ago. Use **pavucontrol** to configure it.  This has been working for me the last 5+ yrs. The only thing I've done on 16.04 is to disable using shm in the pulse client.conf file. It helped with crashes as different applications wanted to produce sound output. I didn't need to do anything else except setup pulse, via that program, to have the correct input and output devices.

Probably best to put the configurations back to the original.

---

### Post by alankong on 2019-05-15
[ATTACH=CONFIG]283269[/ATTACH]

Hi @TheFu.

Thanks for the reply. I actually tried the information on [https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)
I installed Pulse Audio and pavucontrol but In pavucontrol, I cannot even see my audio device as shown on the pic above.

[COLOR=#000000]I will try looking into pulse client.conf file
[/COLOR]

---

### Post by alankong on 2019-05-27
Hi all, I found out the issue is chrome remote desktop. When I installed it, it screw up all my audio setting. I uninstalled it and sound was back up again.

---

### Post by TheFu on 2019-05-28
Thanks for posting the cause of the issue.
Would be really helpful if you clicked "thread tools" at the top and marked this thread SOLVED for others to find.

---

