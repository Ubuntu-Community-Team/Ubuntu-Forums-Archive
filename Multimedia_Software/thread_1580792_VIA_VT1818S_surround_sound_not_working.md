---
title: "VIA VT1818S surround sound not working"
date: 2010-09-23
forum: Multimedia Software
---

### Post by masher_oz on 2010-09-23
Hi all

I'm having some difficulties getting my sound working. I am running Mythbuntu 10.04.
```
$ uname -a
Linux COMPUTER_NAME 2.6.32-24-generic #43-Ubuntu SMP Thu Sep 16 14:17:33 UTC 2010 i686 GNU/Linux
```

I've got an Asus M4A87TB/USB3 motherboard with a VIA VT1818S 8 channel high definition audio built-in sound card. The rear panel of the MB has three jacks that are tasked to: Line in, Line Out and Mic in. When in 6 channel mode, the same jacks are supposed to be: Rear speaker out, Front speaker out and Center/Subwoofer. The speakers are plugged into the correct jacks. When running mixer, I don't get any options for rear/center/subwoofer speakers, although I do get options for Line In and Mic In, so it looks like it's not properly detecting my speakers, and therefore, not giving me the options for outputting sounds to those jacks.

Does anyone have any ideas as to how to proceed?

I have appended several outputs here to show what my system thinks it has...

I have updated the Alsa drivers, as shown [here](http://ubuntuforums.org/showthread.php?t=1046137).
```
$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on Sep 23 2010 for kernel 2.6.32-24-generic (SMP).
```

If I run speaker-test, I can get some odd results:
```
$ speaker-test -twav -l1 -Dplug:surround51 -c6

speaker-test 1.0.23

Playback device is plug:surround51
Stream parameters are 48000Hz, S16_LE, 6 channels
WAV file(s)
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 64 to 16384
Period size range from 32 to 8192
Using max buffer size 16384
Periods = 4
was set period_size = 4096
was set buffer_size = 16384
 0 - Front Left
 4 - Center
 1 - Front Right
 3 - Rear Right
 2 - Rear Left
 5 - LFE
Time per period = 8.367061
```
I only hear the soothing voice on the front left and right. It does seem to think that it has 6 channels to output to.

If I try
```
$ speaker-test -twav -l1 -Dsurround51 -c6

speaker-test 1.0.23

Playback device is surround51
Stream parameters are 48000Hz, S16_LE, 6 channels
WAV file(s)
Channels count (6) not available for playbacks: Invalid argument
Setting of hwparams failed: Invalid argument
```
then it errors out due to not enough channels, however, if I try
```
$ speaker-test -twav -l1 -Dsurround51 -c2

speaker-test 1.0.23

Playback device is surround51
Stream parameters are 48000Hz, S16_LE, 2 channels
WAV file(s)
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 64 to 16384
Period size range from 32 to 8192
Using max buffer size 16384
Periods = 4
was set period_size = 4096
was set buffer_size = 16384
 0 - Front Left
 1 - Front Right
Time per period = 2.733282
```
Then I do get sounds in my front speakers.

My alsa-base.conf file is:
```
$ cat /etc/modprobe.d/alsa-base.conf
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


#test edit
options snd-hda-intel model=3stack-6ch-dig index=0
```
I have tried several models for that last line, both with and without the index=0, and it doesn't seem to help, although I am willing to try again... sudo alsa force-reload


My card is recognised by the OS:
```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: VT1818S Analog [VT1818S Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: SB [HDA ATI SB], device 1: VT1818S Digital [VT1818S Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


$ aplay -L
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: VT1818S Analog [VT1818S Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: SB [HDA ATI SB], device 1: VT1818S Digital [VT1818S Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
matthew@matthew-desktop:~/Documents/sound$ cat aplay-L
null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=SB
    HDA ATI SB, VT1818S Analog
    Default Audio Device
front:CARD=SB,DEV=0
    HDA ATI SB, VT1818S Analog
    Front speakers
surround40:CARD=SB,DEV=0
    HDA ATI SB, VT1818S Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=SB,DEV=0
    HDA ATI SB, VT1818S Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=SB,DEV=0
    HDA ATI SB, VT1818S Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=SB,DEV=0
    HDA ATI SB, VT1818S Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=SB,DEV=0
    HDA ATI SB, VT1818S Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=SB,DEV=0
    HDA ATI SB, VT1818S Digital
    IEC958 (S/PDIF) Digital Audio Output
```

lspci tells me that it is also recognised:
```
$ lspci | grep "Audio"
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)

$ lspci -v
**SNIP**
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
	Subsystem: ATI Technologies Inc SBx00 Azalia (Intel HDA)
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at f9cf8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
**SNIP**
```

---

### Post by lkjoel on 2010-09-23
> **masher_oz said:**
> Hi all

I'm having some difficulties getting my sound working. I am running Mythbuntu 10.04.
```
$ uname -a
Linux COMPUTER_NAME 2.6.32-24-generic #43-Ubuntu SMP Thu Sep 16 14:17:33 UTC 2010 i686 GNU/Linux
```

I've got an Asus M4A87TB/USB3 motherboard with a VIA VT1818S 8 channel high definition audio built-in sound card. The rear panel of the MB has three jacks that are tasked to: Line in, Line Out and Mic in. When in 6 channel mode, the same jacks are supposed to be: Rear speaker out, Front speaker out and Center/Subwoofer. The speakers are plugged into the correct jacks. When running mixer, I don't get any options for rear/center/subwoofer speakers, although I do get options for Line In and Mic In, so it looks like it's not properly detecting my speakers, and therefore, not giving me the options for outputting sounds to those jacks.

Does anyone have any ideas as to how to proceed?

I have appended several outputs here to show what my system thinks it has...

I have updated the Alsa drivers, as shown [here](http://ubuntuforums.org/showthread.php?t=1046137).
```
$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on Sep 23 2010 for kernel 2.6.32-24-generic (SMP).
```

If I run speaker-test, I can get some odd results:
```
$ speaker-test -twav -l1 -Dplug:surround51 -c6

speaker-test 1.0.23

Playback device is plug:surround51
Stream parameters are 48000Hz, S16_LE, 6 channels
WAV file(s)
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 64 to 16384
Period size range from 32 to 8192
Using max buffer size 16384
Periods = 4
was set period_size = 4096
was set buffer_size = 16384
 0 - Front Left
 4 - Center
 1 - Front Right
 3 - Rear Right
 2 - Rear Left
 5 - LFE
Time per period = 8.367061
```
I only hear the soothing voice on the front left and right. It does seem to think that it has 6 channels to output to.

If I try
```
$ speaker-test -twav -l1 -Dsurround51 -c6

speaker-test 1.0.23

Playback device is surround51
Stream parameters are 48000Hz, S16_LE, 6 channels
WAV file(s)
Channels count (6) not available for playbacks: Invalid argument
Setting of hwparams failed: Invalid argument
```
then it errors out due to not enough channels, however, if I try
```
$ speaker-test -twav -l1 -Dsurround51 -c2

speaker-test 1.0.23

Playback device is surround51
Stream parameters are 48000Hz, S16_LE, 2 channels
WAV file(s)
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 64 to 16384
Period size range from 32 to 8192
Using max buffer size 16384
Periods = 4
was set period_size = 4096
was set buffer_size = 16384
 0 - Front Left
 1 - Front Right
Time per period = 2.733282
```
Then I do get sounds in my front speakers.

My alsa-base.conf file is:
```
$ cat /etc/modprobe.d/alsa-base.conf
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


#test edit
options snd-hda-intel model=3stack-6ch-dig index=0
```
I have tried several models for that last line, both with and without the index=0, and it doesn't seem to help, although I am willing to try again... sudo alsa force-reload


My card is recognised by the OS:
```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: VT1818S Analog [VT1818S Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: SB [HDA ATI SB], device 1: VT1818S Digital [VT1818S Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


$ aplay -L
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: VT1818S Analog [VT1818S Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: SB [HDA ATI SB], device 1: VT1818S Digital [VT1818S Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
matthew@matthew-desktop:~/Documents/sound$ cat aplay-L
null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=SB
    HDA ATI SB, VT1818S Analog
    Default Audio Device
front:CARD=SB,DEV=0
    HDA ATI SB, VT1818S Analog
    Front speakers
surround40:CARD=SB,DEV=0
    HDA ATI SB, VT1818S Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=SB,DEV=0
    HDA ATI SB, VT1818S Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=SB,DEV=0
    HDA ATI SB, VT1818S Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=SB,DEV=0
    HDA ATI SB, VT1818S Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=SB,DEV=0
    HDA ATI SB, VT1818S Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=SB,DEV=0
    HDA ATI SB, VT1818S Digital
    IEC958 (S/PDIF) Digital Audio Output
```

lspci tells me that it is also recognised:
```
$ lspci | grep "Audio"
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)

$ lspci -v
**SNIP**
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
	Subsystem: ATI Technologies Inc SBx00 Azalia (Intel HDA)
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at f9cf8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
**SNIP**
```
Try Fix your sound! in my signature.
Then use Post-Fix your sound! in my signature.

---

### Post by masher_oz on 2010-09-24
Fixed by [installing the Alsa snapshot drivers](http://ubuntuforums.org/showthread.php?t=1046137).

---

