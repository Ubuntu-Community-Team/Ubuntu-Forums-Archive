---
title: "Mythbuntu 12 and HDMI audio"
date: 2015-01-01
forum: Mythbuntu
---

### Post by Larry_K on 2015-01-01
Hello,

I apologize in advance if I an not following the forum protocol. I have searched far and wide for a solution to my problem, but none has been found. 

I am a long-time mythtv user and I recently picked up one of the ECS Liva devices as a lightweight frontend. It looked like mythbuntu would be a great choice to load onto this device. Because my existing backend and 3 other frontends are all running myth 0.26.1, I had to go with mythbuntu 12 and roll forward to 0.26. Upgrading to 0.27 or higher is further complicated by the fact these existing systems are running on EL6 and there are upgrade issues related to EL7. 

Anyway, mythbuntu 12 is running on the Liva and I can connect to the backend and play my recorded programs. The problem is, I cannot get the audio to work over my HDMI connection. I was hoping someone in this forum can help me out. 

One of the complicating factors is that I am not running the nvidia driver, and that is where this Liva device differs from all my existing frontends, and most of the stuff I have found online centers around nvidia when it comes to HDMI audio. The Liva does not work with nvidia from what I have learned. 

Do I need to remove pulseaudio? This seems to be a common theme in the myth community. 

I have no asound file installed. Not sure if I need one. 

I have opened alsamixer and confirmed that nothing is muted. 

speaker-test has been unsuccessful so far. Not sure I have the right parameters though.

I have gone into mythfrontend audio setup and toggled through all the choices and tested each one with a recorded program. Nothing has worked.

In the Liva BIOS, there are choices to disable the onboard audio, but since I have no other card (as I do with my other systems that have GeForce cards installed), I have left this enabled.

Listed below are some things that might be relevant to this issue

Thanks,
Larry

```
uname -a
Linux myhost 3.11.0-26-generic #45~precise1-Ubuntu SMP Tue Jul 15 04:02:35 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

```

```

cat /proc/asound/modules 
 0 snd_hda_intel

```

aplay -l shows this: 
```
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC282 Analog [ALC282 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: ID 2882 Digital [ID 2882 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
aplay -L shows this 


```

null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    PulseAudio Sound Server
default:CARD=PCH
    HDA Intel PCH, ALC282 Analog
    Default Audio Device
sysdefault:CARD=PCH
    HDA Intel PCH, ALC282 Analog
    Default Audio Device
front:CARD=PCH,DEV=0
    HDA Intel PCH, ALC282 Analog
    Front speakers
surround40:CARD=PCH,DEV=0
    HDA Intel PCH, ALC282 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=PCH,DEV=0
    HDA Intel PCH, ALC282 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=PCH,DEV=0
    HDA Intel PCH, ALC282 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=PCH,DEV=0
    HDA Intel PCH, ALC282 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=PCH,DEV=0
    HDA Intel PCH, ALC282 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
hdmi:CARD=PCH,DEV=0
    HDA Intel PCH, ID 2882 Digital
    HDMI Audio Output
dmix:CARD=PCH,DEV=0
    HDA Intel PCH, ALC282 Analog
    Direct sample mixing device
dmix:CARD=PCH,DEV=3
    HDA Intel PCH, ID 2882 Digital
    Direct sample mixing device
dsnoop:CARD=PCH,DEV=0
    HDA Intel PCH, ALC282 Analog
    Direct sample snooping device
dsnoop:CARD=PCH,DEV=3
    HDA Intel PCH, ID 2882 Digital
    Direct sample snooping device
hw:CARD=PCH,DEV=0
    HDA Intel PCH, ALC282 Analog
    Direct hardware device without any conversions
hw:CARD=PCH,DEV=3
    HDA Intel PCH, ID 2882 Digital
    Direct hardware device without any conversions
plughw:CARD=PCH,DEV=0
    HDA Intel PCH, ALC282 Analog
    Hardware device with all software conversions
plughw:CARD=PCH,DEV=3
    HDA Intel PCH, ID 2882 Digital
    Hardware device with all software conversions


```

Here is the lengthy alsa modprobe that was installed by default:

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

```

---

### Post by gordintoronto on 2015-01-02
I suggest you browse through the reviews on Newegg, several have suggestions. Number one on the list is to use the latest kernel. There are numerous tutorials on kernel upgrades, such as [http://ubuntuhandbook.org/index.php/2014/08/install-upgrade-linux-kernel-3-16/](http://ubuntuhandbook.org/index.php/2014/08/install-upgrade-linux-kernel-3-16/)

---

### Post by Larry_K on 2015-01-02
> **gordintoronto said:**
> I suggest you browse through the reviews on Newegg, several have suggestions. Number one on the list is to use the latest kernel. There are numerous tutorials on kernel upgrades, such as [http://ubuntuhandbook.org/index.php/2014/08/install-upgrade-linux-kernel-3-16/](http://ubuntuhandbook.org/index.php/2014/08/install-upgrade-linux-kernel-3-16/)

Thank you so much for that tip.  I followed your link and installed the 3.16 kernel.  Now, audio works!  You are a genius! ):P

Larry

---

### Post by gordintoronto on 2015-01-03
Good to hear! Please mark this thread as "solved."

---

