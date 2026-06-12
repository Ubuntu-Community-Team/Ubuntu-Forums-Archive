---
title: "Sounds 'pop' when they are played."
date: 2010-07-12
forum: Multimedia Software
---

### Post by theyain on 2010-07-12
When ever I play any sound, It 'pops' at the beginning.  These pops could be split seconds of no sound, actual popping sounds, or clicking.  I'm thinking its Pulse Audio. Is there anything I can do so that more experienced people can help diagnose this problem of mine?

---

### Post by theyain on 2010-07-13
Bump? 

This is an extremely annoying problem.

---

### Post by scottuss on 2010-07-13
Sorry that I'm not offering a solution, but please remember to leave your posts at least 24 hours before bumping.

There are many walkthroughs on the Internet on how to remove Pulse, you could give that a go.

---

### Post by theyain on 2010-07-13
I know this, as I had to do it on 9.10.  However many applications in the repos are stripped of ALSA, OSS, or any other sound server support.  I do not have the time or patience to recompile every one of those programs.  Nor do I have the time to remove Pulse, install ALSA, then pray to God that I get it working.

---

### Post by lidex on 2010-07-14
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#*
cat /etc/modprobe.d/alsa-base.conf 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by theyain on 2010-07-14
What, pastebin isn't good enough for you?

Personally I prefer pastebin as so I don't crowd the page, but if you insist..


```

theyain@theyain-laptop:~$ uname -a
Linux theyain-laptop 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 07:54:58 UTC 2010 i686 GNU/Linux
theyain@theyain-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
theyain@theyain-laptop:~$ dpkg -l | grep "alsa"
ii  alsa-base                                      1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                                     1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                                     4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                             0.10.28-1                                       GStreamer plugin for ALSA
pc  linux-backports-modules-alsa-2.6.32-21-generic 2.6.32-21.11                                    Ubuntu supplied Linux modules for version 2.
theyain@theyain-laptop:~$ head -n 1 /proc/asound/card*/codec#*
Codec: IDT 92HD81B1X5
theyain@theyain-laptop:~$ cat /etc/modprobe.d/alsa-base.conf
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
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
theyain@theyain-laptop:~$ 

```

Lets see...  I have a Compaq Mini 110c-1105DX.  Running 10.04.

---

### Post by lidex on 2010-07-14
Firstly I would suggest removing that alsa-backports package. Next reboot and follow the alsa-upgrade link in my sig to get v. 1.0.23

---

### Post by Linuxforall on 2010-07-14
I had the same issue, luckily this is Linux and Ubuntu has excellent Kubuntu minus pulse, it solved it for me, don't bother tearing your hair, just install Kubuntu and add kubuntu ppa for latest KDE, you are all set, no popping, cracking, pure sound as its intended to be from my awesome Yamaha sound card. You are still with Ubuntu, except its KDE variant. No harm there.

---

### Post by theyain on 2010-07-15
> **lidex said:**
> Firstly I would suggest removing that alsa-backports package. Next reboot and follow the alsa-upgrade link in my sig to get v. 1.0.23


Won't that remove pulse?

---

### Post by lidex on 2010-07-17
> **theyain said:**
> Won't that remove pulse?

No. Pulse and alsa work together.

---

