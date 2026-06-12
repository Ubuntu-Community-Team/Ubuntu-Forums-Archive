---
title: "Toshiba Tecra A8 Laptop, Realtek ALC262"
date: 2010-09-18
forum: Multimedia Software
---

### Post by bad.skipper on 2010-09-18
Hi,

I have installed ubuntu 32 bit using live CD. During installation sound was working. 

After running updates and installing some software sound was lost.

I have tried many different fixes, included downloading and compiling alsa driver. Below is my alsa-base.conf and alsa info: 

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
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
alias snd-card-0 snd-hda-intel
options snd-hda-intel enable=1 index=0 model=toshiba-s06

```

alsainfo:

```

!!################################
!!ALSA Information Script v 0.4.59
!!################################

!!Script ran on: Sun May 30 07:39:52 UTC 2010


!!Linux Distribution
!!------------------

Ubuntu 10.04 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.04 LTS"


!!DMI Information
!!---------------

Manufacturer:      TOSHIBA
Product Name:      TECRA A8


!!Kernel Information
!!------------------

Kernel release:    2.6.32-22-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     
Library version:    1.0.16
Utilities version:  


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



!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:27d8 (rev 02)
    Subsystem: 1179:0001


!!Modprobe options (Sound related)
!!--------------------------------

snd-hda-intel: model=3stack
snd-hda-intel: enable=1 index=0 model=basic
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



!!Aplay/Arecord output
!!------------

APLAY

./alsa-info.sh: line 118: aplay: command not found

ARECORD

./alsa-info.sh: line 122: arecord: command not found

!!Amixer output
!!-------------


!!Alsactl output
!!-------------

--startcollapse--
--endcollapse--


!!All Loaded Modules
!!------------------

Module
ppp_deflate
zlib_deflate
bsd_comp
ppp_async
crc_ccitt
option
usbserial
nls_utf8
isofs
binfmt_misc
vboxnetadp
vboxnetflt
vboxdrv
joydev
fbcon
tileblit
font
bitblit
softcursor
vga16fb
vgastate
pcmcia
arc4
i915
drm_kms_helper
iwl3945
iwlcore
ppdev
drm
sdhci_pci
mac80211
parport_pc
yenta_socket
rsrc_nonstatic
pcmcia_core
sdhci
led_class
usb_storage
psmouse
toshiba_acpi
serio_raw
cfg80211
soundcore
intel_agp
agpgart
i2c_algo_bit
video
lp
output
parport
hid_a4tech
usbhid
hid
ohci1394
ieee1394
e1000e


!!ALSA/HDA dmesg
!!------------------




```

---

### Post by Kixtosh on 2010-09-20
I'm not an expert user, by any means, but I know how tricky using the Terminal can seem sometimes as a new user of Ubuntu! After doing some searching, I don't think ALSA is properly installed on your Tecra. Check the output from this poster with the same Realtek ALC262 on a Sony laptop, and compare it to the result you posted above:

[http://ubuntuforums.org/showthread.php?p=8562889&highlight=Realtek+ALC262#post8562889](http://ubuntuforums.org/showthread.php?p=8562889&highlight=Realtek+ALC262#post8562889)

Especially, this part:

```
!!ALSA Version
!!------------

Driver version:     1.0.20
Library version:    1.0.20
Utilities version:  1.0.20


!!Loaded ALSA modules
!!-------------------

snd_hda_intel
```And this part:```
!!Soundcards recognised by ALSA
!!-----------------------------

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xd5600000 irq 22
```

There's also this thread which suggested a solution to a problem with the same card on another Sony.

**[http://ubuntuforums.org/showthread.php?t=1577845](http://ubuntuforums.org/showthread.php?t=1577845)**

You don't need to use the Alt+F2 method suggested to run a Terminal command if you are already familiar with opening up the Terminal (which you seem to be). Using Alt+F2 can sometimes seem confusing to a new user (at least I think so). Also, be careful to check that nothing is muted in the settings by checking the System - Preferences - Sound (from the top panel "System" drop down menu).

I'm sorry you had to lose six hours over this already. Sometimes you just get lucky and no tweaking is necessary to get basic stuff working with a new installation (like my recent installation on a Toshiba Portégé R205), but with Ubuntu, I think almost everyone actually *wants* to tweak eventually, so maybe you're just getting an early lesson!

---

### Post by bad.skipper on 2010-09-20
Hi Kixtosh,

Many thanks for looking at my problem. I am not an sound expert as well. 

I have seen this what you are pointing to. I am not sure if this is not a result of running ALSA upgrade script:

[http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)

"The script is not in line with Debian/Ubuntu rules for package handling. It just overwrites existing files.  You won't see any changes on the ALSA package-ids within Synaptic!"

So I am not sure if alsa-info.sh is showing correct data. 

thanks

Bad Skipper.

---

### Post by Kixtosh on 2010-09-20
bad.skipper, have you tried this procedure yet, to update your ALSA drivers (which seem to be missing)?

[http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)

Start with the output of the Terminal command: ```
cat /proc/asound/version
```This should give you a result something like this:```
myname@myubuntu:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.

```
So, you see, my drivers are not even up to date it seems (the latest version is 1.0.23 at the time of writing)!

I had to do this procedure when troubleshooting sound problems on an old Dell (about ten years old), and I eventually got it working (after some other tweaks). The downloads can take a while, depending on your internet connection speed.

---

### Post by bad.skipper on 2010-09-20
I have recived following result:

```

username@adam-laptop:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on Jul  6 2010 for kernel 2.6.32-24-generic (SMP).
username@adam-laptop:~$ 

```

---

### Post by Kixtosh on 2010-09-20
> **bad.skipper said:**
> I have recived following result: ...That looks better than mine, so, did you try the final step suggested?```
sudo alsaconf
```You'll be asked for your login password, and then reboot ...

---

### Post by bad.skipper on 2010-09-23
Hi,

Yes, I did. I compiled alsa-drivers 1.0.23, installed, still no sound.
I have started Ubuntu 10.04 from Live CD - still no sound!. I am very surprised, because last time when I have been installing Ubuntu from the same CD sound was WORKING!!!
It may be kind of hardware problem. There are also oped bugs related to the support for Realtek 262 in alsa code.

regards,
Adam

---

### Post by lkjoel on 2010-09-24
Try Fix your sound! in my signature.
Then use Post-Fix your sound! in my signature.

---

### Post by lidex on 2010-09-25
> **bad.skipper said:**
> Hi,

I have installed ubuntu 32 bit using live CD. During installation sound was working. 

After running updates and installing some software sound was lost.

I have tried many different fixes, included downloading and compiling alsa driver. Below is my alsa-base.conf and alsa info: 

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
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
alias snd-card-0 snd-hda-intel
options snd-hda-intel enable=1 index=0 model=toshiba-s06

```

alsainfo:

```

!!################################
!!ALSA Information Script v 0.4.59
!!################################

!!Script ran on: Sun May 30 07:39:52 UTC 2010


!!Linux Distribution
!!------------------

Ubuntu 10.04 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.04 LTS"


!!DMI Information
!!---------------

Manufacturer:      TOSHIBA
Product Name:      TECRA A8


!!Kernel Information
!!------------------

Kernel release:    2.6.32-22-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     
Library version:    1.0.16
Utilities version:  


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



!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:27d8 (rev 02)
    Subsystem: 1179:0001


!!Modprobe options (Sound related)
!!--------------------------------

snd-hda-intel: model=3stack
snd-hda-intel: enable=1 index=0 model=basic
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



!!Aplay/Arecord output
!!------------

APLAY

./alsa-info.sh: line 118: aplay: command not found

ARECORD

./alsa-info.sh: line 122: arecord: command not found

!!Amixer output
!!-------------


!!Alsactl output
!!-------------

--startcollapse--
--endcollapse--


!!All Loaded Modules
!!------------------

Module
ppp_deflate
zlib_deflate
bsd_comp
ppp_async
crc_ccitt
option
usbserial
nls_utf8
isofs
binfmt_misc
vboxnetadp
vboxnetflt
vboxdrv
joydev
fbcon
tileblit
font
bitblit
softcursor
vga16fb
vgastate
pcmcia
arc4
i915
drm_kms_helper
iwl3945
iwlcore
ppdev
drm
sdhci_pci
mac80211
parport_pc
yenta_socket
rsrc_nonstatic
pcmcia_core
sdhci
led_class
usb_storage
psmouse
toshiba_acpi
serio_raw
cfg80211
soundcore
intel_agp
agpgart
i2c_algo_bit
video
lp
output
parport
hid_a4tech
usbhid
hid
ohci1394
ieee1394
e1000e


!!ALSA/HDA dmesg
!!------------------




```

This alsa-info is ancient:
> !!Script ran on: Sun May 30 07:39:52 UTC 2010
Rerun the script and post a link so we can see your current state. Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by Kixtosh on 2010-09-25
> **lidex said:**
> This alsa-info is ancient:

Rerun the script and post a link so we can see your current state. Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.Hmmm, just for comparison, and reference purposes, I ran this myself on my _working_ system, and there are quite a few differences with your non-working system - this is also a Toshiba, remember, but not a Tecra A8:```

!!################################
!!ALSA Information Script v 0.4.59
!!################################

!!Script ran on: Sat Sep 25 04:26:52 UTC 2010


!!Linux Distribution
!!------------------

Ubuntu 10.04.1 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"


!!DMI Information
!!---------------

Manufacturer:      TOSHIBA
Product Name:      PORTEGE R205


!!Kernel Information
!!------------------

Kernel release:    2.6.32-24-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.21
Library version:    1.0.22
Utilities version:  1.0.22


!!Loaded ALSA modules
!!-------------------

snd_intel8x0


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

 0 [ICH6           ]: ICH4 - Intel ICH6
                      Intel ICH6 with AD1981B at irq 17


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:1e.2 0401: 8086:266e (rev 03)
	Subsystem: 1179:0248


!!Modprobe options (Sound related)
!!--------------------------------

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

!!Module: snd_intel8x0
	ac97_clock : 0
	ac97_quirk : <NULL>
	buggy_irq : N
	buggy_semaphore : N
	enable : N
	id : <NULL>
	index : -1
	joystick : 0
	spdif_aclink : 0
	xbox : N


!!AC97 Codec information
!!---------------------------
--startcollapse--

0-0/0: Analog Devices AD1981B

PCI Subsys Vendor: 0x1179
PCI Subsys Device: 0x0248

Flags: 10
Capabilities     : -headphone out-
DAC resolution   : 20-bit
ADC resolution   : 16-bit
3D enhancement   : No 3D Stereo Enhancement

Current setup
Mic gain         :  0dB [ 0dB]
POP path         : pre 3D
Sim. stereo      : off
3D enhancement   : off
Loudness         : off
Mono output      : MIX
Mic select       : Mic1
ADC/DAC loopback : off
Extended ID      : codec=0 rev=1 AMAP DSA=0 VRA
Extended status  : VRA
PCM front DAC    : 44100Hz
PCM ADC          : 44100Hz



AD18XX configuration
Unchained        : 0x1000,0x0000,0x0000
Chained          : 0x0000,0x0000,0x0000

0:00 = 0090
0:02 = 0000
0:04 = 0000
0:06 = 801f
0:08 = 0000
0:0a = 0000
0:0c = 801f
0:0e = 801f
0:10 = 9f9f
0:12 = 0606
0:14 = 0000
0:16 = 9f9f
0:18 = 0000
0:1a = 0000
0:1c = 0000
0:1e = 0000
0:20 = 0000
0:22 = 0000
0:24 = 0000
0:26 = 000f
0:28 = 0601
0:2a = 0031
0:2c = ac44
0:2e = 0000
0:30 = 0000
0:32 = ac44
0:34 = 0000
0:36 = 0000
0:38 = 0000
0:3a = 2000
0:3c = 0000
0:3e = 0000
0:40 = 0000
0:42 = 0000
0:44 = 0000
0:46 = 0000
0:48 = 0000
0:4a = 0000
0:4c = 0000
0:4e = 0000
0:50 = 0000
0:52 = 0000
0:54 = 0000
0:56 = 0000
0:58 = 0000
0:5a = 0000
0:5c = 4000
0:5e = 0000
0:60 = 8080
0:62 = 0000
0:64 = 8000
0:66 = 0000
0:68 = 0000
0:6a = 0000
0:6c = 0000
0:6e = 0000
0:70 = 0000
0:72 = 000c
0:74 = 1001
0:76 = 2010
0:78 = 0000
0:7a = 0000
0:7c = 4144
0:7e = 5374
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----  1 root audio 116, 10 Sep 24 18:15 /dev/snd/controlC0
crw-rw----  1 root audio 116,  9 Sep 24 18:15 /dev/snd/pcmC0D0c
crw-rw----  1 root audio 116,  8 Sep 24 21:24 /dev/snd/pcmC0D0p
crw-rw----  1 root audio 116,  7 Sep 24 18:15 /dev/snd/pcmC0D1c
crw-rw----  1 root audio 116,  6 Sep 24 18:15 /dev/snd/pcmC0D2c
crw-rw----  1 root audio 116,  5 Sep 24 18:15 /dev/snd/pcmC0D3c
crw-rw----  1 root audio 116,  4 Sep 24 18:15 /dev/snd/pcmC0D4p
crw-rw----  1 root audio 116,  3 Sep 24 18:15 /dev/snd/seq
crw-rw----  1 root audio 116,  2 Sep 24 18:15 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Sep 24 18:15 .
drwxr-xr-x 3 root root 240 Sep 24 18:15 ..
lrwxrwxrwx 1 root root  12 Sep 24 18:15 pci-0000:00:1e.2 -> ../controlC0


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 1: Intel ICH - MIC ADC [Intel ICH6 - MIC ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 2: Intel ICH - MIC2 ADC [Intel ICH6 - MIC2 ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 3: Intel ICH - ADC2 [Intel ICH6 - ADC2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [ICH6]

Card hw:0 'ICH6'/'Intel ICH6 with AD1981B at irq 17'
  Mixer name	: 'Analog Devices AD1981B'
  Components	: 'AC97a:41445374'
  Controls      : 28
  Simple ctrls  : 20
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Master Mono',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-46.50dB] [off]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Headphone Jack Sense',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [12.00dB] [on]
  Front Right: Playback 31 [100%] [12.00dB] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [-34.50dB] [off] Capture [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off] Capture [off]
Simple mixer control 'Line Jack Sense',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 25 [81%] [3.00dB] [on] Capture [off]
  Front Right: Playback 25 [81%] [3.00dB] [on] Capture [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-34.50dB] [off]
  Front Left: Capture [on]
  Front Right: Capture [on]
Simple mixer control 'Mic Boost ( 20dB)',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Mic Select',0
  Capabilities: enum
  Items: 'Mic1' 'Mic2'
  Item0: 'Mic1'
Simple mixer control 'Video',0
  Capabilities: cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Phone',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-34.50dB] [off]
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Aux',0
  Capabilities: pvolume pswitch cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [-34.50dB] [off] Capture [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off] Capture [off]
Simple mixer control 'Mono Output Select',0
  Capabilities: enum
  Items: 'Mix' 'Mic'
  Item0: 'Mix'
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 0 [0%] [0.00dB] [on]
  Front Right: Capture 0 [0%] [0.00dB] [on]
Simple mixer control 'Mix',0
  Capabilities: cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Mix Mono',0
  Capabilities: cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'External Amplifier',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Stereo Mic',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]


!!Alsactl output
!!-------------

--startcollapse--
state.ICH6 {
	control.1 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Master Playback Switch'
		value.0 true
		value.1 true
	}
	control.2 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -4650
		comment.dbmax 0
		iface MIXER
		name 'Master Playback Volume'
		value.0 31
		value.1 31
	}
	control.3 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Headphone Playback Switch'
		value.0 true
		value.1 true
	}
	control.4 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -4650
		comment.dbmax 0
		iface MIXER
		name 'Headphone Playback Volume'
		value.0 31
		value.1 31
	}
	control.5 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Master Mono Playback Switch'
		value false
	}
	control.6 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 31'
		comment.dbmin -4650
		comment.dbmax 0
		iface MIXER
		name 'Master Mono Playback Volume'
		value 0
	}
	control.7 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Phone Playback Switch'
		value false
	}
	control.8 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Phone Playback Volume'
		value 0
	}
	control.9 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Mic Playback Switch'
		value false
	}
	control.10 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Mic Playback Volume'
		value 0
	}
	control.11 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Mic Boost ( 20dB)'
		value false
	}
	control.12 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Line Playback Switch'
		value.0 false
		value.1 false
	}
	control.13 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Line Playback Volume'
		value.0 0
		value.1 0
	}
	control.14 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'CD Playback Switch'
		value.0 true
		value.1 true
	}
	control.15 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'CD Playback Volume'
		value.0 25
		value.1 25
	}
	control.16 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Aux Playback Switch'
		value.0 false
		value.1 false
	}
	control.17 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Aux Playback Volume'
		value.0 0
		value.1 0
	}
	control.18 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'PCM Playback Switch'
		value.0 true
		value.1 true
	}
	control.19 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'PCM Playback Volume'
		value.0 31
		value.1 31
	}
	control.20 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 2
		comment.item.0 Mic
		comment.item.1 CD
		comment.item.2 Video
		comment.item.3 Aux
		comment.item.4 Line
		comment.item.5 Mix
		comment.item.6 'Mix Mono'
		comment.item.7 Phone
		iface MIXER
		name 'Capture Source'
		value.0 Mic
		value.1 Mic
	}
	control.21 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Capture Switch'
		value.0 true
		value.1 true
	}
	control.22 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 15'
		comment.dbmin 0
		comment.dbmax 2250
		iface MIXER
		name 'Capture Volume'
		value.0 0
		value.1 0
	}
	control.23 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Mix
		comment.item.1 Mic
		iface MIXER
		name 'Mono Output Select'
		value Mix
	}
	control.24 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Mic1
		comment.item.1 Mic2
		iface MIXER
		name 'Mic Select'
		value Mic1
	}
	control.25 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Stereo Mic'
		value false
	}
	control.26 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Headphone Jack Sense'
		value false
	}
	control.27 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Line Jack Sense'
		value false
	}
	control.28 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'External Amplifier'
		value true
	}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
hidp
binfmt_misc
rfcomm
ppdev
sco
bridge
stp
bnep
l2cap
input_polldev
fbcon
tileblit
font
bitblit
softcursor
vga16fb
vgastate
arc4
snd_intel8x0
snd_ac97_codec
ac97_bus
joydev
snd_pcm_oss
snd_mixer_oss
snd_pcm
snd_seq_dummy
snd_seq_oss
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
btusb
bluetooth
snd_seq
snd_timer
snd_seq_device
pcmcia
snd
ath5k
i915
tpm_infineon
mac80211
drm_kms_helper
yenta_socket
sdhci_pci
ath
soundcore
tpm
psmouse
drm
rsrc_nonstatic
sdhci
intel_agp
i2c_algo_bit
serio_raw
tpm_bios
snd_page_alloc
cfg80211
pcmcia_core
led_class
video
toshiba_acpi
output
agpgart
lp
parport
usbhid
hid
sky2


!!ALSA/HDA dmesg
!!------------------
```So, follow the suggestion given by lidex and post your results.

---

### Post by bad.skipper on 2010-09-30
Hi,

I have reinstalled pluseaudio and alsa drivers. Still no sound :-(

```

!!################################
!!ALSA Information Script v 0.4.59
!!################################

!!Script ran on: Thu Sep 30 20:12:45 UTC 2010


!!Linux Distribution
!!------------------

Ubuntu 10.04.1 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"


!!DMI Information
!!---------------

Manufacturer:      TOSHIBA
Product Name:      TECRA A8


!!Kernel Information
!!------------------

Kernel release:    2.6.32-25-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.23
Library version:    1.0.23
Utilities version:  1.0.22


!!Loaded ALSA modules
!!-------------------

snd_hda_intel


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

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0x6a080000 irq 28


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:27d8 (rev 02)
    Subsystem: 1179:0001


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-usb-caiaq: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-1
snd-hda-intel: model=sony-assamd


!!Loaded sound module options
!!--------------------------

!!Module: snd_hda_intel
    bdl_pos_adj : 1,-1,-1,-1,-1,-1,-1,-1
    beep_mode : 1,1,1,1,1,1,1,1
    enable : Y,Y,Y,Y,Y,Y,Y,Y
    enable_msi : -1
    id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
    index : -1,-1,-1,-1,-1,-1,-1,-1
    model : sony-assamd,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
    patch : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
    position_fix : 0,0,0,0,0,0,0,0
    power_save : 0
    power_save_controller : Y
    probe_mask : -1,-1,-1,-1,-1,-1,-1,-1
    probe_only : 0,0,0,0,0,0,0,0
    single_cmd : N


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: Realtek ALC262
Address: 0
Function Id: 0x1
Vendor Id: 0x10ec0262
Subsystem Id: 0x11790580
Revision Id: 0x100100
No Modem Function Group found
Default PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=4, o=0, i=0, unsolicited=1, wake=0
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[2]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[3]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Node 0x02 [Audio Output] wcaps 0x11: Stereo
  Device: name="ALC262 Analog", type="Audio", device=0
  Converter: stream=5, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x03 [Audio Output] wcaps 0x11: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x04 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x05 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x06 [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0x1e]: 16 20 24 32
    formats [0x1]: PCM
Node 0x07 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Control: name="Capture Switch", index=0, device=0
  Control: name="Capture Volume", index=0, device=0
  Device: name="ALC262 Analog", type="Audio", device=0
  Amp-In caps: ofs=0x08, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x91 0x91]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0x6]: 16 20
    formats [0x1]: PCM
  Connection: 1
     0x24
Node 0x08 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Control: name="Capture Switch", index=1, device=0
  Control: name="Capture Volume", index=1, device=0
  Amp-In caps: ofs=0x08, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x94 0x94]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0x6]: 16 20
    formats [0x1]: PCM
  Connection: 1
     0x23
Node 0x09 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Control: name="Capture Switch", index=2, device=0
  Control: name="Capture Volume", index=2, device=0
  Amp-In caps: ofs=0x08, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x94 0x94]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0x6]: 16 20
    formats [0x1]: PCM
  Connection: 1
     0x22
Node 0x0a [Audio Input] wcaps 0x100391: Stereo Digital
  Converter: stream=0, channel=0
  SDI-Select: 0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0x1e]: 16 20 24 32
    formats [0x1]: PCM
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x1f
Node 0x0b [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Mic Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Mic Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="ATAPI Mic Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=1, ofs=0
  Control: name="ATAPI Mic Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=1, ofs=0
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x11 0x11] [0x12 0x12] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x97 0x97] [0x97 0x97]
  Connection: 8
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15
Node 0x0c [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Control: name="Master Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x17 0x17]
  Connection: 2
     0x02 0x0b
Node 0x0d [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 2
     0x03 0x0b
Node 0x0e [Audio Mixer] wcaps 0x20010e: Mono Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00] [0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x00]
  Connection: 2
     0x02 0x0b
Node 0x0f [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x10 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x11 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x12 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x13 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x14 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000003e: IN OUT HP Detect Trigger
  Pin Default 0x90170110: [Fixed] Speaker at Int N/A
    Conn = Analog, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0xc0: OUT HP
  Unsolicited: tag=00, enabled=0
  Connection: 2
     0x0c* 0x0d
Node 0x15 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000003e: IN OUT HP Detect Trigger
  Pin Default 0x0221101f: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Black
    DefAssociation = 0x1, Sequence = 0xf
  Pin-ctls: 0xc0: OUT HP
  Unsolicited: tag=04, enabled=1
  Connection: 2
     0x0c* 0x0d
Node 0x16 [Pin Complex] wcaps 0x40010c: Mono Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80]
  Pincap 0x00000010: OUT
  Pin Default 0x40f000f6: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x6
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x0e
Node 0x17 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x18 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000173e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x02a110f0: [Jack] Mic at Ext Front
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Connection: 2
     0x0c* 0x0d
Node 0x19 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000173e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x40f000f8: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x8
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Connection: 2
     0x0c* 0x0d
Node 0x1a [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000173e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x218411f0: [Jack] Line In at Sep Rear
    Conn = RCA, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 2
     0x0c* 0x0d
Node 0x1b [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000173e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x210411f0: [Jack] Line Out at Sep Rear
    Conn = RCA, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 2
     0x0c* 0x0d
Node 0x1c [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x40f000fb: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0xb
  Pin-ctls: 0x00:
Node 0x1d [Pin Complex] wcaps 0x400000: Mono
  Pincap 0x00000020: IN
  Pin Default 0x598301f0: [N/A] Line In at Int ATAPI
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
Node 0x1e [Pin Complex] wcaps 0x400380: Mono Digital
  Pincap 0x00000010: OUT
  Pin Default 0x40f000fd: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0xd
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x06
Node 0x1f [Pin Complex] wcaps 0x400280: Mono Digital
  Pincap 0x00000020: IN
  Pin Default 0x40f000fe: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0xe
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
Node 0x20 [Vendor Defined Widget] wcaps 0xf00040: Mono
  Processing caps: benign=0, ncoeff=17
Node 0x21 [Volume Knob Widget] wcaps 0x600080: Mono
  Volume-Knob: delta=0, steps=32, direct=0, val=64
  Unsolicited: tag=00, enabled=0
  Connection: 0
Node 0x22 [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Control: name="Input Source", index=2, device=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Amp-Out caps: N/A
  Amp-Out vals:  [0x00 0x00]
  Connection: 9
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x0b
Node 0x23 [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Control: name="Input Source", index=1, device=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Amp-Out caps: N/A
  Amp-Out vals:  [0x00 0x00]
  Connection: 9
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x0b
Node 0x24 [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Control: name="Input Source", index=0, device=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Amp-Out caps: N/A
  Amp-Out vals:  [0x00 0x00]
  Connection: 9
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x0b
Codec: LSI Si3054
Address: 1
Function Id: 0x2
Vendor Id: 0x11c13026
Subsystem Id: 0x11790001
Revision Id: 0x100700
Modem Function Group: 0x1
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----  1 root audio 116,  0 Sep 30 22:08 /dev/snd/controlC0
crw-rw----  1 root audio 116,  4 Sep 30 22:08 /dev/snd/hwC0D0
crw-rw----  1 root audio 116,  5 Sep 30 22:08 /dev/snd/hwC0D1
crw-rw----  1 root audio 116, 24 Sep 30 22:09 /dev/snd/pcmC0D0c
crw-rw----  1 root audio 116, 16 Sep 30 22:11 /dev/snd/pcmC0D0p
crw-rw----  1 root audio 116, 30 Sep 30 22:08 /dev/snd/pcmC0D6c
crw-rw----  1 root audio 116, 22 Sep 30 22:08 /dev/snd/pcmC0D6p
crw-rw----  1 root audio 116,  1 Sep 30 22:08 /dev/snd/seq
crw-rw----  1 root audio 116, 33 Sep 30 22:08 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Sep 30 22:08 .
drwxr-xr-x 3 root root 240 Sep 30 22:08 ..
lrwxrwxrwx 1 root root  12 Sep 30 22:08 pci-0000:00:1b.0 -> ../controlC0


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC262 Analog [ALC262 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC262 Analog [ALC262 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [Intel]

Card hw:0 'Intel'/'HDA Intel at 0x6a080000 irq 28'
  Mixer name    : 'Realtek ALC262'
  Components    : 'HDA:10ec0262,11790580,00100100 HDA:11c13026,11790001,00100700'
  Controls      : 18
  Simple ctrls  : 12
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 23 [74%] [-12.00dB] [on]
  Front Right: Playback 23 [74%] [-12.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 250 [98%] [-1.00dB]
  Front Right: Playback 250 [98%] [-1.00dB]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 17 [55%] [-9.00dB] [on]
  Front Right: Playback 17 [55%] [-9.00dB] [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 17 [55%] [13.50dB] [off]
  Front Right: Capture 17 [55%] [13.50dB] [off]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 20 [65%] [18.00dB] [off]
  Front Right: Capture 20 [65%] [18.00dB] [off]
Simple mixer control 'Capture',2
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 20 [65%] [18.00dB] [off]
  Front Right: Capture 20 [65%] [18.00dB] [off]
Simple mixer control 'ATAPI Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 18 [58%] [-7.50dB] [on]
  Front Right: Playback 18 [58%] [-7.50dB] [on]
Simple mixer control 'Caller ID',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Mic' 'Front Mic' 'Line' 'CD'
  Item0: 'Mic'
Simple mixer control 'Input Source',1
  Capabilities: cenum
  Items: 'Mic' 'Front Mic' 'Line' 'CD'
  Item0: 'Mic'
Simple mixer control 'Input Source',2
  Capabilities: cenum
  Items: 'Mic' 'Front Mic' 'Line' 'CD'
  Item0: 'Mic'
Simple mixer control 'Off-hook',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]


!!Alsactl output
!!-------------

--startcollapse--
state.Intel {
    control.1 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -4650
        comment.dbmax 0
        iface MIXER
        name 'Master Playback Volume'
        value.0 23
        value.1 23
    }
    control.2 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Master Playback Switch'
        value true
    }
    control.3 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'Mic Playback Volume'
        value.0 17
        value.1 17
    }
    control.4 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Mic Playback Switch'
        value.0 true
        value.1 true
    }
    control.5 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'ATAPI Mic Playback Volume'
        value.0 18
        value.1 18
    }
    control.6 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'ATAPI Mic Playback Switch'
        value.0 true
        value.1 true
    }
    control.7 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Capture Switch'
        value.0 false
        value.1 false
    }
    control.8 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Capture Switch'
        index 1
        value.0 false
        value.1 false
    }
    control.9 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Capture Switch'
        index 2
        value.0 false
        value.1 false
    }
    control.10 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -1200
        comment.dbmax 3450
        iface MIXER
        name 'Capture Volume'
        value.0 17
        value.1 17
    }
    control.11 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -1200
        comment.dbmax 3450
        iface MIXER
        name 'Capture Volume'
        index 1
        value.0 20
        value.1 20
    }
    control.12 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -1200
        comment.dbmax 3450
        iface MIXER
        name 'Capture Volume'
        index 2
        value.0 20
        value.1 20
    }
    control.13 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 1
        comment.item.0 Mic
        comment.item.1 'Front Mic'
        comment.item.2 Line
        comment.item.3 CD
        iface MIXER
        name 'Input Source'
        value Mic
    }
    control.14 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 1
        comment.item.0 Mic
        comment.item.1 'Front Mic'
        comment.item.2 Line
        comment.item.3 CD
        iface MIXER
        name 'Input Source'
        index 1
        value Mic
    }
    control.15 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 1
        comment.item.0 Mic
        comment.item.1 'Front Mic'
        comment.item.2 Line
        comment.item.3 CD
        iface MIXER
        name 'Input Source'
        index 2
        value Mic
    }
    control.16 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Off-hook Switch'
        value false
    }
    control.17 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Caller ID Switch'
        value false
    }
    control.18 {
        comment.access 'read write user'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 255'
        comment.tlv '0000000100000008ffffec1400000014'
        comment.dbmin -5100
        comment.dbmax 0
        iface MIXER
        name 'PCM Playback Volume'
        value.0 250
        value.1 250
    }
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
xt_limit
xt_tcpudp
ipt_LOG
ipt_MASQUERADE
xt_DSCP
ipt_REJECT
nf_conntrack_irc
nf_conntrack_ftp
xt_state
aes_i586
aes_generic
rfcomm
binfmt_misc
lp
sco
bridge
stp
bnep
l2cap
vboxnetadp
vboxnetflt
vboxdrv
btusb
bluetooth
joydev
snd_hda_codec_si3054
snd_hda_codec_realtek
fbcon
tileblit
font
bitblit
softcursor
vga16fb
vgastate
iptable_nat
nf_nat
nf_conntrack_ipv4
nf_conntrack
nf_defrag_ipv4
iptable_mangle
iptable_filter
ip_tables
x_tables
pcmcia
arc4
snd_hda_intel
snd_hda_codec
snd_hwdep
snd_pcm_oss
snd_mixer_oss
snd_pcm
snd_seq_dummy
snd_seq_oss
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
iwl3945
snd_seq
iwlcore
ppdev
i915
drm_kms_helper
snd_timer
snd_seq_device
mac80211
parport_pc
sdhci_pci
yenta_socket
rsrc_nonstatic
intel_agp
drm
i2c_algo_bit
parport
psmouse
serio_raw
toshiba_acpi
sdhci
led_class
cfg80211
pcmcia_core
agpgart
video
output
snd
soundcore
snd_page_alloc
ohci1394
ieee1394
e1000e


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x14 0x90170110
0x15 0x0221101f
0x16 0x40f000f6
0x18 0x02a110f0
0x19 0x40f000f8
0x1a 0x218411f0
0x1b 0x210411f0
0x1c 0x40f000fb
0x1d 0x598301f0
0x1e 0x40f000fd
0x1f 0x40f000fe

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:

/sys/class/sound/hwC0D1/init_pin_configs:

/sys/class/sound/hwC0D1/driver_pin_configs:

/sys/class/sound/hwC0D1/user_pin_configs:

/sys/class/sound/hwC0D1/init_verbs:


!!ALSA/HDA dmesg
!!------------------

[   15.135548] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   15.135653] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
[   15.135690] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
[   15.135696] HDA Intel 0000:00:1b.0: enabling device (0000 -> 0002)
[   15.135704]   alloc irq_desc for 22 on node -1
[   15.135706]   alloc kstat_irqs on node -1
[   15.135714] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   15.135753]   alloc irq_desc for 28 on node -1
[   15.135755]   alloc kstat_irqs on node -1
[   15.135765] HDA Intel 0000:00:1b.0: irq 28 for MSI/MSI-X
[   15.135797] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   15.141972] vga16fb: initializing
--
[   15.141982] vga16fb: not registering due to another framebuffer present
[   15.180836] hda_codec: ALC262: SKU not ready 0x598301f0
[   15.180979] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input6
[   15.269180] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input7

```

---

### Post by lidex on 2010-09-30
> **bad.skipper said:**
> Hi,

I have reinstalled pluseaudio and alsa drivers. Still no sound :-(

```

!!################################
!!ALSA Information Script v 0.4.59
!!################################

!!Script ran on: Thu Sep 30 20:12:45 UTC 2010


!!Linux Distribution
!!------------------

Ubuntu 10.04.1 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"


!!DMI Information
!!---------------

Manufacturer:      TOSHIBA
Product Name:      TECRA A8


!!Kernel Information
!!------------------

Kernel release:    2.6.32-25-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.23
Library version:    1.0.23
Utilities version:  1.0.22


!!Loaded ALSA modules
!!-------------------

snd_hda_intel


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

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0x6a080000 irq 28


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:27d8 (rev 02)
    Subsystem: 1179:0001


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-usb-caiaq: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-1
snd-hda-intel: model=sony-assamd


!!Loaded sound module options
!!--------------------------

!!Module: snd_hda_intel
    bdl_pos_adj : 1,-1,-1,-1,-1,-1,-1,-1
    beep_mode : 1,1,1,1,1,1,1,1
    enable : Y,Y,Y,Y,Y,Y,Y,Y
    enable_msi : -1
    id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
    index : -1,-1,-1,-1,-1,-1,-1,-1
    model : sony-assamd,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
    patch : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
    position_fix : 0,0,0,0,0,0,0,0
    power_save : 0
    power_save_controller : Y
    probe_mask : -1,-1,-1,-1,-1,-1,-1,-1
    probe_only : 0,0,0,0,0,0,0,0
    single_cmd : N


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: Realtek ALC262
Address: 0
Function Id: 0x1
Vendor Id: 0x10ec0262
Subsystem Id: 0x11790580
Revision Id: 0x100100
No Modem Function Group found
Default PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=4, o=0, i=0, unsolicited=1, wake=0
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[2]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[3]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Node 0x02 [Audio Output] wcaps 0x11: Stereo
  Device: name="ALC262 Analog", type="Audio", device=0
  Converter: stream=5, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x03 [Audio Output] wcaps 0x11: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x04 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x05 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x06 [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0x1e]: 16 20 24 32
    formats [0x1]: PCM
Node 0x07 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Control: name="Capture Switch", index=0, device=0
  Control: name="Capture Volume", index=0, device=0
  Device: name="ALC262 Analog", type="Audio", device=0
  Amp-In caps: ofs=0x08, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x91 0x91]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0x6]: 16 20
    formats [0x1]: PCM
  Connection: 1
     0x24
Node 0x08 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Control: name="Capture Switch", index=1, device=0
  Control: name="Capture Volume", index=1, device=0
  Amp-In caps: ofs=0x08, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x94 0x94]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0x6]: 16 20
    formats [0x1]: PCM
  Connection: 1
     0x23
Node 0x09 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Control: name="Capture Switch", index=2, device=0
  Control: name="Capture Volume", index=2, device=0
  Amp-In caps: ofs=0x08, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x94 0x94]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0x6]: 16 20
    formats [0x1]: PCM
  Connection: 1
     0x22
Node 0x0a [Audio Input] wcaps 0x100391: Stereo Digital
  Converter: stream=0, channel=0
  SDI-Select: 0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0x1e]: 16 20 24 32
    formats [0x1]: PCM
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x1f
Node 0x0b [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Mic Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Mic Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="ATAPI Mic Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=1, ofs=0
  Control: name="ATAPI Mic Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=1, ofs=0
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x11 0x11] [0x12 0x12] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x97 0x97] [0x97 0x97]
  Connection: 8
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15
Node 0x0c [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Control: name="Master Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x17 0x17]
  Connection: 2
     0x02 0x0b
Node 0x0d [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 2
     0x03 0x0b
Node 0x0e [Audio Mixer] wcaps 0x20010e: Mono Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00] [0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x00]
  Connection: 2
     0x02 0x0b
Node 0x0f [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x10 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x11 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x12 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x13 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x14 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000003e: IN OUT HP Detect Trigger
  Pin Default 0x90170110: [Fixed] Speaker at Int N/A
    Conn = Analog, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0xc0: OUT HP
  Unsolicited: tag=00, enabled=0
  Connection: 2
     0x0c* 0x0d
Node 0x15 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000003e: IN OUT HP Detect Trigger
  Pin Default 0x0221101f: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Black
    DefAssociation = 0x1, Sequence = 0xf
  Pin-ctls: 0xc0: OUT HP
  Unsolicited: tag=04, enabled=1
  Connection: 2
     0x0c* 0x0d
Node 0x16 [Pin Complex] wcaps 0x40010c: Mono Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80]
  Pincap 0x00000010: OUT
  Pin Default 0x40f000f6: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x6
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x0e
Node 0x17 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x18 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000173e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x02a110f0: [Jack] Mic at Ext Front
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Connection: 2
     0x0c* 0x0d
Node 0x19 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000173e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x40f000f8: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x8
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Connection: 2
     0x0c* 0x0d
Node 0x1a [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000173e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x218411f0: [Jack] Line In at Sep Rear
    Conn = RCA, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 2
     0x0c* 0x0d
Node 0x1b [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000173e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x210411f0: [Jack] Line Out at Sep Rear
    Conn = RCA, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 2
     0x0c* 0x0d
Node 0x1c [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x40f000fb: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0xb
  Pin-ctls: 0x00:
Node 0x1d [Pin Complex] wcaps 0x400000: Mono
  Pincap 0x00000020: IN
  Pin Default 0x598301f0: [N/A] Line In at Int ATAPI
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
Node 0x1e [Pin Complex] wcaps 0x400380: Mono Digital
  Pincap 0x00000010: OUT
  Pin Default 0x40f000fd: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0xd
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x06
Node 0x1f [Pin Complex] wcaps 0x400280: Mono Digital
  Pincap 0x00000020: IN
  Pin Default 0x40f000fe: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0xe
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
Node 0x20 [Vendor Defined Widget] wcaps 0xf00040: Mono
  Processing caps: benign=0, ncoeff=17
Node 0x21 [Volume Knob Widget] wcaps 0x600080: Mono
  Volume-Knob: delta=0, steps=32, direct=0, val=64
  Unsolicited: tag=00, enabled=0
  Connection: 0
Node 0x22 [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Control: name="Input Source", index=2, device=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Amp-Out caps: N/A
  Amp-Out vals:  [0x00 0x00]
  Connection: 9
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x0b
Node 0x23 [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Control: name="Input Source", index=1, device=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Amp-Out caps: N/A
  Amp-Out vals:  [0x00 0x00]
  Connection: 9
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x0b
Node 0x24 [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Control: name="Input Source", index=0, device=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Amp-Out caps: N/A
  Amp-Out vals:  [0x00 0x00]
  Connection: 9
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x0b
Codec: LSI Si3054
Address: 1
Function Id: 0x2
Vendor Id: 0x11c13026
Subsystem Id: 0x11790001
Revision Id: 0x100700
Modem Function Group: 0x1
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----  1 root audio 116,  0 Sep 30 22:08 /dev/snd/controlC0
crw-rw----  1 root audio 116,  4 Sep 30 22:08 /dev/snd/hwC0D0
crw-rw----  1 root audio 116,  5 Sep 30 22:08 /dev/snd/hwC0D1
crw-rw----  1 root audio 116, 24 Sep 30 22:09 /dev/snd/pcmC0D0c
crw-rw----  1 root audio 116, 16 Sep 30 22:11 /dev/snd/pcmC0D0p
crw-rw----  1 root audio 116, 30 Sep 30 22:08 /dev/snd/pcmC0D6c
crw-rw----  1 root audio 116, 22 Sep 30 22:08 /dev/snd/pcmC0D6p
crw-rw----  1 root audio 116,  1 Sep 30 22:08 /dev/snd/seq
crw-rw----  1 root audio 116, 33 Sep 30 22:08 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Sep 30 22:08 .
drwxr-xr-x 3 root root 240 Sep 30 22:08 ..
lrwxrwxrwx 1 root root  12 Sep 30 22:08 pci-0000:00:1b.0 -> ../controlC0


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC262 Analog [ALC262 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC262 Analog [ALC262 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [Intel]

Card hw:0 'Intel'/'HDA Intel at 0x6a080000 irq 28'
  Mixer name    : 'Realtek ALC262'
  Components    : 'HDA:10ec0262,11790580,00100100 HDA:11c13026,11790001,00100700'
  Controls      : 18
  Simple ctrls  : 12
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 23 [74%] [-12.00dB] [on]
  Front Right: Playback 23 [74%] [-12.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 250 [98%] [-1.00dB]
  Front Right: Playback 250 [98%] [-1.00dB]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 17 [55%] [-9.00dB] [on]
  Front Right: Playback 17 [55%] [-9.00dB] [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 17 [55%] [13.50dB] [off]
  Front Right: Capture 17 [55%] [13.50dB] [off]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 20 [65%] [18.00dB] [off]
  Front Right: Capture 20 [65%] [18.00dB] [off]
Simple mixer control 'Capture',2
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 20 [65%] [18.00dB] [off]
  Front Right: Capture 20 [65%] [18.00dB] [off]
Simple mixer control 'ATAPI Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 18 [58%] [-7.50dB] [on]
  Front Right: Playback 18 [58%] [-7.50dB] [on]
Simple mixer control 'Caller ID',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Mic' 'Front Mic' 'Line' 'CD'
  Item0: 'Mic'
Simple mixer control 'Input Source',1
  Capabilities: cenum
  Items: 'Mic' 'Front Mic' 'Line' 'CD'
  Item0: 'Mic'
Simple mixer control 'Input Source',2
  Capabilities: cenum
  Items: 'Mic' 'Front Mic' 'Line' 'CD'
  Item0: 'Mic'
Simple mixer control 'Off-hook',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]


!!Alsactl output
!!-------------

--startcollapse--
state.Intel {
    control.1 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -4650
        comment.dbmax 0
        iface MIXER
        name 'Master Playback Volume'
        value.0 23
        value.1 23
    }
    control.2 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Master Playback Switch'
        value true
    }
    control.3 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'Mic Playback Volume'
        value.0 17
        value.1 17
    }
    control.4 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Mic Playback Switch'
        value.0 true
        value.1 true
    }
    control.5 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'ATAPI Mic Playback Volume'
        value.0 18
        value.1 18
    }
    control.6 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'ATAPI Mic Playback Switch'
        value.0 true
        value.1 true
    }
    control.7 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Capture Switch'
        value.0 false
        value.1 false
    }
    control.8 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Capture Switch'
        index 1
        value.0 false
        value.1 false
    }
    control.9 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Capture Switch'
        index 2
        value.0 false
        value.1 false
    }
    control.10 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -1200
        comment.dbmax 3450
        iface MIXER
        name 'Capture Volume'
        value.0 17
        value.1 17
    }
    control.11 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -1200
        comment.dbmax 3450
        iface MIXER
        name 'Capture Volume'
        index 1
        value.0 20
        value.1 20
    }
    control.12 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -1200
        comment.dbmax 3450
        iface MIXER
        name 'Capture Volume'
        index 2
        value.0 20
        value.1 20
    }
    control.13 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 1
        comment.item.0 Mic
        comment.item.1 'Front Mic'
        comment.item.2 Line
        comment.item.3 CD
        iface MIXER
        name 'Input Source'
        value Mic
    }
    control.14 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 1
        comment.item.0 Mic
        comment.item.1 'Front Mic'
        comment.item.2 Line
        comment.item.3 CD
        iface MIXER
        name 'Input Source'
        index 1
        value Mic
    }
    control.15 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 1
        comment.item.0 Mic
        comment.item.1 'Front Mic'
        comment.item.2 Line
        comment.item.3 CD
        iface MIXER
        name 'Input Source'
        index 2
        value Mic
    }
    control.16 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Off-hook Switch'
        value false
    }
    control.17 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Caller ID Switch'
        value false
    }
    control.18 {
        comment.access 'read write user'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 255'
        comment.tlv '0000000100000008ffffec1400000014'
        comment.dbmin -5100
        comment.dbmax 0
        iface MIXER
        name 'PCM Playback Volume'
        value.0 250
        value.1 250
    }
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
xt_limit
xt_tcpudp
ipt_LOG
ipt_MASQUERADE
xt_DSCP
ipt_REJECT
nf_conntrack_irc
nf_conntrack_ftp
xt_state
aes_i586
aes_generic
rfcomm
binfmt_misc
lp
sco
bridge
stp
bnep
l2cap
vboxnetadp
vboxnetflt
vboxdrv
btusb
bluetooth
joydev
snd_hda_codec_si3054
snd_hda_codec_realtek
fbcon
tileblit
font
bitblit
softcursor
vga16fb
vgastate
iptable_nat
nf_nat
nf_conntrack_ipv4
nf_conntrack
nf_defrag_ipv4
iptable_mangle
iptable_filter
ip_tables
x_tables
pcmcia
arc4
snd_hda_intel
snd_hda_codec
snd_hwdep
snd_pcm_oss
snd_mixer_oss
snd_pcm
snd_seq_dummy
snd_seq_oss
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
iwl3945
snd_seq
iwlcore
ppdev
i915
drm_kms_helper
snd_timer
snd_seq_device
mac80211
parport_pc
sdhci_pci
yenta_socket
rsrc_nonstatic
intel_agp
drm
i2c_algo_bit
parport
psmouse
serio_raw
toshiba_acpi
sdhci
led_class
cfg80211
pcmcia_core
agpgart
video
output
snd
soundcore
snd_page_alloc
ohci1394
ieee1394
e1000e


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x14 0x90170110
0x15 0x0221101f
0x16 0x40f000f6
0x18 0x02a110f0
0x19 0x40f000f8
0x1a 0x218411f0
0x1b 0x210411f0
0x1c 0x40f000fb
0x1d 0x598301f0
0x1e 0x40f000fd
0x1f 0x40f000fe

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:

/sys/class/sound/hwC0D1/init_pin_configs:

/sys/class/sound/hwC0D1/driver_pin_configs:

/sys/class/sound/hwC0D1/user_pin_configs:

/sys/class/sound/hwC0D1/init_verbs:


!!ALSA/HDA dmesg
!!------------------

[   15.135548] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   15.135653] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
[   15.135690] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
[   15.135696] HDA Intel 0000:00:1b.0: enabling device (0000 -> 0002)
[   15.135704]   alloc irq_desc for 22 on node -1
[   15.135706]   alloc kstat_irqs on node -1
[   15.135714] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   15.135753]   alloc irq_desc for 28 on node -1
[   15.135755]   alloc kstat_irqs on node -1
[   15.135765] HDA Intel 0000:00:1b.0: irq 28 for MSI/MSI-X
[   15.135797] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   15.141972] vga16fb: initializing
--
[   15.141982] vga16fb: not registering due to another framebuffer present
[   15.180836] hda_codec: ALC262: SKU not ready 0x598301f0
[   15.180979] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input6
[   15.269180] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input7

```

Much better, with a quirk or two. How did you get upgraded alsa? What is the output of this command:
```
cat /etc/modprobe.d/alsa-base.conf
```
and this:
```
sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
```

---

### Post by bad.skipper on 2010-09-30
> **lidex said:**
> Much better, with a quirk or two. How did you get upgraded alsa? What is the output of this command:
```
cat /etc/modprobe.d/alsa-base.conf
```

Lidex, 

I have upgraded alsa few times, first I used upgrade script, second I compiled from source.

This is a content of the alsa-base file:
```

~$ cat /etc/modprobe.d/alsa-base.conf
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
options snd-pcsp index=-1
# options snd-hda-intel model=hippo_1
# options snd-hda-intel model=hippo_1 
options snd-hda-intel model=sony-assamd

```additionally I have added symbolic link:

sudo ln -s /etc/modprobe.d/sound /etc/modprobe.d/sound.conf

```

sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*

                     USER        PID ACCESS COMMAND
/dev/snd/controlC0:  username   1737 F.... pulseaudio
/dev/snd/pcmC0D0p:   username   1737 F...m pulseaudio

```Accordint to some Linux Laptop group sound on Toshiba Tecra A8 works fine:
[http://www.linlap.com/wiki/toshiba+tecra+a8](http://www.linlap.com/wiki/toshiba+tecra+a8)

thanks,

Bad.

---

### Post by lidex on 2010-09-30
> **bad.skipper said:**
> Lidex, 

I have upgraded alsa few times, first I used upgrade script, second I compiled from source.

This is a content of the alsa-base file:
```

~$ cat /etc/modprobe.d/alsa-base.conf
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
options snd-pcsp index=-1
# options snd-hda-intel model=hippo_1
# options snd-hda-intel model=hippo_1 
options snd-hda-intel model=sony-assamd

```additionally I have added symbolic link:

sudo ln -s /etc/modprobe.d/sound /etc/modprobe.d/sound.conf

```

sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*

                     USER        PID ACCESS COMMAND
/dev/snd/controlC0:  username   1737 F.... pulseaudio
/dev/snd/pcmC0D0p:   username   1737 F...m pulseaudio

```Accordint to some Linux Laptop group sound on Toshiba Tecra A8 works fine:
[http://www.linlap.com/wiki/toshiba+tecra+a8](http://www.linlap.com/wiki/toshiba+tecra+a8)

thanks,

Bad.

I'm afraid that combining approaches is causing your issues.
I want you to remove these lines from alsa-base.conf:
```
# options snd-hda-intel model=hippo_1
# options snd-hda-intel model=hippo_1 
options snd-hda-intel model=sony-assamd
```
add this line:
```
options snd-hda-intel enable=1 index=0 model=basic
```
remove these also:
```
/etc/modprobe.d/sound
/etc/modprobe.d/sound.conf
```
Now reboot.

---

### Post by bad.skipper on 2010-10-01
> **lidex said:**
> I'm afraid that combining approaches is causing your issues.
I want you to remove these lines from alsa-base.conf:
```
# options snd-hda-intel model=hippo_1
# options snd-hda-intel model=hippo_1 
options snd-hda-intel model=sony-assamd
```add this line:
```
options snd-hda-intel enable=1 index=0 model=basic
```remove these also:
```
/etc/modprobe.d/sound
/etc/modprobe.d/sound.conf
```Now reboot.

Lidex,

Many thanks for support. I have edited many times mentioned files (alsa-base.conf) and sound.conf (it is a symbolic like to /modprobe.d/sound file). I have tried many options of the snd-hda-intel model=XXX (using realtek ALC262), without success.

Today I tried going back to basic settings, as you suggested, sadly nothing have changed.

As far as I remember I have downloaded REALTEK driver, and I have tried to compile it. Compilation failed, later I have found that this package was NOT expected to be compiled for Ubuntu.

Anyway I am very surprised. I have booted from Ubuntu live CB 10.04 - and there is no SOUND too!!! When I have installing this system from the same CD sound was on.

I cannot go back to windows (just cant!) but I need a sound for my work (skype). I have found this post:
[https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/115966](https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/115966)
That confused me a lot. I am not quite sure if I can make bootable windows disk with all required drivers (I have created bootable win disk using BartPE, and tried to enable sound but it didnt helped)

Thanks and regards,

Bad.

---

### Post by lidex on 2010-10-01
Have you checked your bios settings?
Post these outputs please:
```
sudo dmidecode -t bios
sudo dmidecode -t baseboard

```

---

### Post by bad.skipper on 2010-10-03
> **lidex said:**
> Have you checked your bios settings?
Post these outputs please:
```
sudo dmidecode -t bios
sudo dmidecode -t baseboard

```

Lidex,

Thanks for update. 

```

username@toshiba-laptop:~$ sudo dmidecode -t bios
# dmidecode 2.9
SMBIOS 2.4 present.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
    Vendor: TOSHIBA
    Version: Version 3.40
    Release Date: 03/12/2007
    Address: 0xE0000
    Runtime Size: 128 kB
    ROM Size: 1024 kB
    Characteristics:
        ISA is supported
        PCI is supported
        PC Card (PCMCIA) is supported
        PNP is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        VLB is supported
        Boot from CD is supported
        Selectable boot is supported
        EDD is supported
        Japanese floppy for Toshiba 1.2 MB is supported (int 13h)
        3.5"/720 KB floppy services are supported (int 13h)
        Print screen service is supported (int 5h)
        8042 keyboard services are supported (int 9h)
        Serial services are supported (int 14h)
        Printer services are supported (int 17h)
        ACPI is supported
        USB legacy is supported
        BIOS boot specification is supported
        Function key-initiated network boot is supported
        Targeted content distribution is supported
    BIOS Revision: 3.40
    Firmware Revision: 5.20
[B]
Invalid entry length (0). DMI table is broken! Stop.[/B]


```

and second command:

```

username@toshiba-laptop:~$ sudo dmidecode -t baseboard
# dmidecode 2.9
SMBIOS 2.4 present.

Handle 0x0002, DMI type 2, 8 bytes
Base Board Information
    Manufacturer: TOSHIBA
    Product Name: Portable PC
    Version: Version A0
    Serial Number: $$C0748E4M

Handle 0x0058, DMI type 10, 18 bytes
On Board Device 1 Information
    Type: Other
    Status: Enabled
    Description: MODEM
On Board Device 2 Information
    Type: Other
    Status: Enabled
    Description: USB
On Board Device 3 Information
    Type: Video
    Status: Enabled
    Description: VIDEO
On Board Device 4 Information
    Type: Ethernet
    Status: Enabled
    Description: ETHERNET
On Board Device 5 Information
    Type: Sound
    Status: Enabled
    Description: SOUND
On Board Device 6 Information
    Type: Other
    Status: Enabled
    Description: WIRELESS LAN
On Board Device 7 Information
    Type: Other
    Status: Enabled
    Description: BLUETOOTH

Invalid entry length (0). DMI table is broken! Stop.

```

---

### Post by lidex on 2010-10-03
A bios update may help you.

---

### Post by Kixtosh on 2010-10-03
> **lidex said:**
> A bios update may help you.I'm curious: are you suggesting this because of the error message?```
Invalid entry length (0). DMI table is broken! Stop.
```
Here are my results for comparison (another Toshiba, but not a Tecra model). There is no newer BIOS available in my case:```
~$ **sudo dmidecode -t bios**
# dmidecode 2.9
SMBIOS 2.3 present.

Handle 0x0000, DMI type 0, 20 bytes
BIOS Information
	Vendor: TOSHIBA
	Version: Version 1.70
	Release Date: 02/14/2008
	Address: 0xE0000
	Runtime Size: 128 kB
	ROM Size: 1024 kB
	Characteristics:
		ISA is supported
		PCI is supported
		PC Card (PCMCIA) is supported
		PNP is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		VLB is supported
		Boot from CD is supported
		Selectable boot is supported
		EDD is supported
		Japanese floppy for Toshiba 1.2 MB is supported (int 13h)
		3.5"/720 KB floppy services are supported (int 13h)
		Print screen service is supported (int 5h)
		8042 keyboard services are supported (int 9h)
		Serial services are supported (int 14h)
		Printer services are supported (int 17h)
		ACPI is supported
		USB legacy is supported
		BIOS boot specification is supported
		Function key-initiated network boot is supported
``````
~$ **sudo dmidecode -t baseboard**
# dmidecode 2.9
SMBIOS 2.3 present.

Handle 0x0002, DMI type 2, 8 bytes
Base Board Information
	Manufacturer: TOSHIBA
	Product Name: Portable PC
	Version: Version A0
	Serial Number: $$0000017p

Handle 0x0058, DMI type 10, 18 bytes
On Board Device 1 Information
	Type: Other
	Status: Enabled
	Description: MODEM
On Board Device 2 Information
	Type: Other
	Status: Enabled
	Description: USB
On Board Device 3 Information
	Type: Video
	Status: Enabled
	Description: VIDEO
On Board Device 4 Information
	Type: Ethernet
	Status: Enabled
	Description: ETHERNET
On Board Device 5 Information
	Type: Sound
	Status: Enabled
	Description: SOUND
On Board Device 6 Information
	Type: Other
	Status: Enabled
	Description: WIRELESS LAN
On Board Device 7 Information
	Type: Other
	Status: Enabled
	Description: BLUETOOTH
```

---

### Post by bad.skipper on 2010-10-04
Hi!

I have checked toshiba support, it looks that BIOS v3.40 it is most up-do-date version.
Anyway Toshiba Tecra A8 BIOS install is windows based archive to be installed on windows. I will try to find a way how to re-install it on Ubuntu.

---

### Post by bad.skipper on 2010-10-05
Hi All,

During system boot I have seen following warnings related to ALSA. I am not quite sure if this is because I have been compiling few times ALSA drivers or because once I have tried to compile Relatek ALC262 driver for linux that failed (it was not a driver for debian/ubuntu):

```

username@toshiba-laptop:/var/log$ cat boot.log 

udevd[378]: BUS= will be removed in a future udev version, please use SUBSYSTEM= to match the event device, or SUBSYSTEMS= to match a parent device, in /lib/udev/rules.d/40-alsa-firmware-loaders.rules:9

udevd[378]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /lib/udev/rules.d/40-alsa-firmware-loaders.rules:9

udevd[378]: BUS= will be removed in a future udev version, please use SUBSYSTEM= to match the event device, or SUBSYSTEMS= to match a parent device, in /lib/udev/rules.d/40-alsa-firmware-loaders.rules:10

udevd[378]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /lib/udev/rules.d/40-alsa-firmware-loaders.rules:10

udevd[378]: BUS= will be removed in a future udev version, please use SUBSYSTEM= to match the event device, or SUBSYSTEMS= to match a parent device, in /lib/udev/rules.d/40-alsa-firmware-loaders.rules:12

udevd[378]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /lib/udev/rules.d/40-alsa-firmware-loaders.rules:12

udevd[378]: BUS= will be removed in a future udev version, please use SUBSYSTEM= to match the event device, or SUBSYSTEMS= to match a parent device, in /lib/udev/rules.d/40-alsa-firmware-loaders.rules:13

udevd[378]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /lib/udev/rules.d/40-alsa-firmware-loaders.rules:13

udevd[378]: BUS= will be removed in a future udev version, please use SUBSYSTEM= to match the event device, or SUBSYSTEMS= to match a parent device, in /lib/udev/rules.d/40-alsa-firmware-loaders.rules:15

udevd[378]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /lib/udev/rules.d/40-alsa-firmware-loaders.rules:15

udevd[378]: BUS= will be removed in a future udev version, please use SUBSYSTEM= to match the event device, or SUBSYSTEMS= to match a parent device, in /lib/udev/rules.d/40-alsa-firmware-loaders.rules:16

udevd[378]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /lib/udev/rules.d/40-alsa-firmware-loaders.rules:16

fsck from util-linux-ng 2.17.2
/dev/sda1: clean, 271111/7058880 files, 11731355/28180480 blocks
 * Starting AppArmor profiles                                                   Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
                                                                         [ OK ]
 * Setting sensors limits                                                                                                                             [ OK ]
 * Starting the Firestarter firewall...                                                                                                               [fail]
Starting VMware services:
   VMware USB Arbitrator                                               done
   Virtual machine monitor                                            failed
   Virtual machine communication interface                            failed
   VM communication interface socket family                           failed
   Blocking file system                                               failed
   Virtual ethernet                                                   failed
 * Not starting jetty - edit /etc/default/jetty and change NO_START to be 0 (or comment it out).
 * Starting Postfix Mail Transport Agent postfix 

```

thanks a lot for help better that in many commercial products,

regards,

Bad Skipper.

---

### Post by lidex on 2010-10-05
> **bad.skipper said:**
> Hi All,

During system boot I have seen following warnings related to ALSA. I am not quite sure if this is because I have been compiling few times ALSA drivers or because once I have tried to compile Relatek ALC262 driver for linux that failed (it was not a driver for debian/ubuntu):

```

username@toshiba-laptop:/var/log$ cat boot.log 

udevd[378]: BUS= will be removed in a future udev version, please use SUBSYSTEM= to match the event device, or SUBSYSTEMS= to match a parent device, in /lib/udev/rules.d/40-alsa-firmware-loaders.rules:9

udevd[378]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /lib/udev/rules.d/40-alsa-firmware-loaders.rules:9

udevd[378]: BUS= will be removed in a future udev version, please use SUBSYSTEM= to match the event device, or SUBSYSTEMS= to match a parent device, in /lib/udev/rules.d/40-alsa-firmware-loaders.rules:10

udevd[378]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /lib/udev/rules.d/40-alsa-firmware-loaders.rules:10

udevd[378]: BUS= will be removed in a future udev version, please use SUBSYSTEM= to match the event device, or SUBSYSTEMS= to match a parent device, in /lib/udev/rules.d/40-alsa-firmware-loaders.rules:12

udevd[378]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /lib/udev/rules.d/40-alsa-firmware-loaders.rules:12

udevd[378]: BUS= will be removed in a future udev version, please use SUBSYSTEM= to match the event device, or SUBSYSTEMS= to match a parent device, in /lib/udev/rules.d/40-alsa-firmware-loaders.rules:13

udevd[378]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /lib/udev/rules.d/40-alsa-firmware-loaders.rules:13

udevd[378]: BUS= will be removed in a future udev version, please use SUBSYSTEM= to match the event device, or SUBSYSTEMS= to match a parent device, in /lib/udev/rules.d/40-alsa-firmware-loaders.rules:15

udevd[378]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /lib/udev/rules.d/40-alsa-firmware-loaders.rules:15

udevd[378]: BUS= will be removed in a future udev version, please use SUBSYSTEM= to match the event device, or SUBSYSTEMS= to match a parent device, in /lib/udev/rules.d/40-alsa-firmware-loaders.rules:16

udevd[378]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /lib/udev/rules.d/40-alsa-firmware-loaders.rules:16

fsck from util-linux-ng 2.17.2
/dev/sda1: clean, 271111/7058880 files, 11731355/28180480 blocks
 * Starting AppArmor profiles                                                   Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
                                                                         [ OK ]
 * Setting sensors limits                                                                                                                             [ OK ]
 * Starting the Firestarter firewall...                                                                                                               [fail]
Starting VMware services:
   VMware USB Arbitrator                                               done
   Virtual machine monitor                                            failed
   Virtual machine communication interface                            failed
   VM communication interface socket family                           failed
   Blocking file system                                               failed
   Virtual ethernet                                                   failed
 * Not starting jetty - edit /etc/default/jetty and change NO_START to be 0 (or comment it out).
 * Starting Postfix Mail Transport Agent postfix 

```

thanks a lot for help better that in many commercial products,

regards,

Bad Skipper.
Looks like that refers to alsa-firmware-loaders which you do not require for ALC262. You could safely remove that package. 

As for the bios, I was looking mainly at the date, although the error message is not good either. It took a few bios updates on my main PC to get full compatibility with linux. Alsa looks to the bios for hardware info, then loads appropriate modules based on that.

---

### Post by bad.skipper on 2010-10-06
Hi Lidex,

I have removed alsa-firmware package giving this warning.

I have booted laptop form Live Windoows XP CD, and installed un-mute tool from toshiba.

Sadly this patch requires reboot of Windows XP, so using Live CD it didnt work.

I need to resize my ext4 partition and install win XP there :-) I guess. It looks like a lot of fun. I will update this thread ASAP I will know if this was a problem.

regards,

Adam

---

### Post by Kixtosh on 2010-10-06
So, if you open a terminal and enter:```
alsamixer
``` What happens? It should open a window as shown in the attached screenshot.

---

### Post by bad.skipper on 2010-10-06
Kixtosh

Alsamixer screenshot attached.

regards,

Bad.

---

### Post by lidex on 2010-10-07
> **bad.skipper said:**
> Kixtosh

Alsamixer screenshot attached.

regards,

Bad.

Please do not run alsamixer with sudo, it can screw up your permissions.

---

### Post by Kixtosh on 2010-10-07
Have you tried the troubleshooting procedure in this thread yet?

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by bad.skipper on 2010-10-07
PROBLEM SOLVED!!!

This was really nasty hardware bug in Toshiba Tecra A8. It is described in this bug report:

[https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/115966](https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/115966)

My FIX:

1.Using Ubuntu 10.10 RC live CD resize existing partition and create 25 GB unpartitioned disk space.

2. Install Microsoft Windows XP Home to just created 25 GB partition, NTFS file system.

3. Using live CD (see point 1) fix boot loader (grub2) to display all systems on startup

4. Download and install drivers for Toshiba Tecra A8 from Toshiba support:
[http://eu.computers.toshiba-europe.com/innovation/generic/SUPPORT_PORTAL/](http://eu.computers.toshiba-europe.com/innovation/generic/SUPPORT_PORTAL/)

5. Download and run Toshiba unmute utility (I don't know if it was necessary)

6. Shut down (not reboot) computer few times

7. Started Windows, using keys enabled sound - ALLELUIA!!!! Sound works.

8. Reboot into Ubuntu 10.04, sound WORKS FINE just from start!

PROBLEM SOLVED. 

:) Many Thanks to Lidex and Kixtosh for very professional support. Good work guys. :)

---

### Post by lidex on 2010-10-07
> **bad.skipper said:**
> Kixtosh

Alsamixer screenshot attached.

regards,

Bad.

More info would be helpful. 
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by bad.skipper on 2010-10-08
Hi all,

This fix was done totaly outside Ubuntu, after installing Windows I have installed sound drivers and enabled sound. Then after rebook into Linux sound was working. 

It is well-known problem with Toshiba Tecra Laptops that in some very special conditions (during installation of the system for example) using functional buttons to switch-off sound does it permanently.


```

upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.59
!!################################

!!Script ran on: Fri Oct  8 07:39:40 UTC 2010


!!Linux Distribution
!!------------------

Ubuntu 10.04.1 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"


!!DMI Information
!!---------------

Manufacturer:      TOSHIBA
Product Name:      TECRA A8


!!Kernel Information
!!------------------

Kernel release:    2.6.32-25-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.23
Library version:    1.0.23
Utilities version:  1.0.23


!!Loaded ALSA modules
!!-------------------

snd_hda_intel


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

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0x6a080000 irq 28


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:27d8 (rev 02)
    Subsystem: 1179:0001


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-usb-caiaq: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-1
snd-hda-intel: enable=1 index=0 model=basic


!!Loaded sound module options
!!--------------------------

!!Module: snd_hda_intel
    bdl_pos_adj : 1,-1,-1,-1,-1,-1,-1,-1
    beep_mode : 1,1,1,1,1,1,1,1
    enable : Y,Y,Y,Y,Y,Y,Y,Y
    enable_msi : -1
    id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
    index : 0,-1,-1,-1,-1,-1,-1,-1
    model : basic,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
    patch : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
    position_fix : 0,0,0,0,0,0,0,0
    power_save : 0
    power_save_controller : Y
    probe_mask : -1,-1,-1,-1,-1,-1,-1,-1
    probe_only : 0,0,0,0,0,0,0,0
    single_cmd : N


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: Realtek ALC262
Address: 0
Function Id: 0x1
Vendor Id: 0x10ec0262
Subsystem Id: 0x11790580
Revision Id: 0x100100
No Modem Function Group found
Default PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=4, o=0, i=0, unsolicited=1, wake=0
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[2]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[3]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Node 0x02 [Audio Output] wcaps 0x11: Stereo
  Device: name="ALC262 Analog", type="Audio", device=0
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x03 [Audio Output] wcaps 0x11: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x04 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x05 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x06 [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0x1e]: 16 20 24 32
    formats [0x1]: PCM
Node 0x07 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Control: name="Capture Switch", index=0, device=0
  Control: name="Capture Volume", index=0, device=0
  Device: name="ALC262 Analog", type="Audio", device=0
  Amp-In caps: ofs=0x08, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x9f 0x9f]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0x6]: 16 20
    formats [0x1]: PCM
  Connection: 1
     0x24
Node 0x08 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Control: name="Capture Switch", index=1, device=0
  Control: name="Capture Volume", index=1, device=0
  Amp-In caps: ofs=0x08, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x00 0x00]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0x6]: 16 20
    formats [0x1]: PCM
  Connection: 1
     0x23
Node 0x09 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Control: name="Capture Switch", index=2, device=0
  Control: name="Capture Volume", index=2, device=0
  Amp-In caps: ofs=0x08, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x00 0x00]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0x6]: 16 20
    formats [0x1]: PCM
  Connection: 1
     0x22
Node 0x0a [Audio Input] wcaps 0x100391: Stereo Digital
  Converter: stream=0, channel=0
  SDI-Select: 0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0x1e]: 16 20 24 32
    formats [0x1]: PCM
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x1f
Node 0x0b [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="CD Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=4, ofs=0
  Control: name="CD Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=4, ofs=0
  Control: name="Line Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Control: name="Line Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Control: name="Mic Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Mic Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Front Mic Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=1, ofs=0
  Control: name="Front Mic Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=1, ofs=0
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x19 0x19] [0x80 0x80] [0x97 0x97] [0x97 0x97]
  Connection: 8
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15
Node 0x0c [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Control: name="Front Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x09 0x09]
  Connection: 2
     0x02 0x0b
Node 0x0d [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Control: name="Headphone Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x09 0x09]
  Connection: 2
     0x03 0x0b
Node 0x0e [Audio Mixer] wcaps 0x20010e: Mono Amp-In Amp-Out
  Control: name="Mono Playback Volume", index=0, device=0
    ControlAmp: chs=2, dir=Out, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00] [0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x00]
  Connection: 2
     0x02 0x0b
Node 0x0f [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x10 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x11 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x12 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x13 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x14 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Control: name="Front Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000003e: IN OUT HP Detect Trigger
  Pin Default 0x90170110: [Fixed] Speaker at Int N/A
    Conn = Analog, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 2
     0x0c* 0x0d
Node 0x15 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Control: name="Headphone Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000003e: IN OUT HP Detect Trigger
  Pin Default 0x0221101f: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Black
    DefAssociation = 0x1, Sequence = 0xf
  Pin-ctls: 0xc0: OUT HP
  Unsolicited: tag=00, enabled=0
  Connection: 2
     0x0c 0x0d*
Node 0x16 [Pin Complex] wcaps 0x40010c: Mono Amp-Out
  Control: name="Mono Playback Switch", index=0, device=0
    ControlAmp: chs=2, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80]
  Pincap 0x00000010: OUT
  Pin Default 0x40f000f6: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x6
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x0e
Node 0x17 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x18 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Control: name="Mic Boost", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000173e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x02a110f0: [Jack] Mic at Ext Front
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Connection: 2
     0x0c* 0x0d
Node 0x19 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Control: name="Front Mic Boost", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000173e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x40f000f8: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x8
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 2
     0x0c* 0x0d
Node 0x1a [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000173e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x218411f0: [Jack] Line In at Sep Rear
    Conn = RCA, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 2
     0x0c* 0x0d
Node 0x1b [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000173e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x210411f0: [Jack] Line Out at Sep Rear
    Conn = RCA, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 2
     0x0c* 0x0d
Node 0x1c [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x40f000fb: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0xb
  Pin-ctls: 0x00:
Node 0x1d [Pin Complex] wcaps 0x400000: Mono
  Pincap 0x00000020: IN
  Pin Default 0x598301f0: [N/A] Line In at Int ATAPI
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
Node 0x1e [Pin Complex] wcaps 0x400380: Mono Digital
  Pincap 0x00000010: OUT
  Pin Default 0x40f000fd: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0xd
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x06
Node 0x1f [Pin Complex] wcaps 0x400280: Mono Digital
  Pincap 0x00000020: IN
  Pin Default 0x40f000fe: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0xe
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
Node 0x20 [Vendor Defined Widget] wcaps 0xf00040: Mono
  Processing caps: benign=0, ncoeff=17
Node 0x21 [Volume Knob Widget] wcaps 0x600080: Mono
  Volume-Knob: delta=0, steps=32, direct=0, val=64
  Unsolicited: tag=00, enabled=0
  Connection: 0
Node 0x22 [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Control: name="Input Source", index=2, device=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Amp-Out caps: N/A
  Amp-Out vals:  [0x00 0x00]
  Connection: 9
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x0b
Node 0x23 [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Control: name="Input Source", index=1, device=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Amp-Out caps: N/A
  Amp-Out vals:  [0x00 0x00]
  Connection: 9
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x0b
Node 0x24 [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Control: name="Input Source", index=0, device=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Amp-Out caps: N/A
  Amp-Out vals:  [0x00 0x00]
  Connection: 9
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x0b
Codec: LSI Si3054
Address: 1
Function Id: 0x2
Vendor Id: 0x11c13026
Subsystem Id: 0x11790001
Revision Id: 0x100700
Modem Function Group: 0x1
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116,  0 Oct  8 08:34 /dev/snd/controlC0
crw-rw----+ 1 root audio 116,  4 Oct  8 08:34 /dev/snd/hwC0D0
crw-rw----+ 1 root audio 116,  5 Oct  8 08:34 /dev/snd/hwC0D1
crw-rw----+ 1 root audio 116, 24 Oct  8 09:37 /dev/snd/pcmC0D0c
crw-rw----+ 1 root audio 116, 16 Oct  8 09:37 /dev/snd/pcmC0D0p
crw-rw----+ 1 root audio 116, 30 Oct  8 08:34 /dev/snd/pcmC0D6c
crw-rw----+ 1 root audio 116, 22 Oct  8 08:34 /dev/snd/pcmC0D6p
crw-rw----+ 1 root audio 116,  1 Oct  8 08:34 /dev/snd/seq
crw-rw----+ 1 root audio 116, 33 Oct  8 08:34 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Oct  8 08:34 .
drwxr-xr-x 3 root root 240 Oct  8 08:34 ..
lrwxrwxrwx 1 root root  12 Oct  8 08:34 pci-0000:00:1b.0 -> ../controlC0


!!ALSA configuration files
!!------------------------

!!System wide config file (/etc/asound.conf)

pcm.pulse {
type pulse
}
ctl.pulse {
type pulse
}
pcm.!default {
type pulse
}
ctl.!default {
type pulse
}


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC262 Analog [ALC262 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC262 Analog [ALC262 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [Intel]

Card hw:0 'Intel'/'HDA Intel at 0x6a080000 irq 28'
  Mixer name    : 'Realtek ALC262'
  Components    : 'HDA:10ec0262,11790580,00100100 HDA:11c13026,11790001,00100700'
  Controls      : 30
  Simple ctrls  : 19
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 9 [29%] [-33.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Front Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Front Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%]
  Front Right: 0 [0%]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 25 [81%] [3.00dB] [on]
  Front Right: Playback 25 [81%] [3.00dB] [on]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%]
  Front Right: 0 [0%]
Simple mixer control 'Mono',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-46.50dB] [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 31 [100%] [34.50dB] [off]
  Front Right: Capture 31 [100%] [34.50dB] [off]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 0 [0%] [-12.00dB] [on]
  Front Right: Capture 0 [0%] [-12.00dB] [on]
Simple mixer control 'Capture',2
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 0 [0%] [-12.00dB] [on]
  Front Right: Capture 0 [0%] [-12.00dB] [on]
Simple mixer control 'Caller ID',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Mic' 'Front Mic' 'Line' 'CD'
  Item0: 'Mic'
Simple mixer control 'Input Source',1
  Capabilities: cenum
  Items: 'Mic' 'Front Mic' 'Line' 'CD'
  Item0: 'Mic'
Simple mixer control 'Input Source',2
  Capabilities: cenum
  Items: 'Mic' 'Front Mic' 'Line' 'CD'
  Item0: 'Mic'
Simple mixer control 'Off-hook',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]


!!Alsactl output
!!-------------

--startcollapse--
state.Intel {
    control.1 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -4650
        comment.dbmax 0
        iface MIXER
        name 'Front Playback Volume'
        value.0 31
        value.1 31
    }
    control.2 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Front Playback Switch'
        value.0 true
        value.1 true
    }
    control.3 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'CD Playback Volume'
        value.0 25
        value.1 25
    }
    control.4 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'CD Playback Switch'
        value.0 true
        value.1 true
    }
    control.5 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'Line Playback Volume'
        value.0 0
        value.1 0
    }
    control.6 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Line Playback Switch'
        value.0 false
        value.1 false
    }
    control.7 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'Mic Playback Volume'
        value.0 0
        value.1 0
    }
    control.8 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Mic Playback Switch'
        value.0 false
        value.1 false
    }
    control.9 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 3'
        comment.dbmin 0
        comment.dbmax 3000
        iface MIXER
        name 'Mic Boost'
        value.0 0
        value.1 0
    }
    control.10 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'Front Mic Playback Volume'
        value.0 0
        value.1 0
    }
    control.11 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Front Mic Playback Switch'
        value.0 false
        value.1 false
    }
    control.12 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 3'
        comment.dbmin 0
        comment.dbmax 3000
        iface MIXER
        name 'Front Mic Boost'
        value.0 0
        value.1 0
    }
    control.13 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -4650
        comment.dbmax 0
        iface MIXER
        name 'Headphone Playback Volume'
        value.0 31
        value.1 31
    }
    control.14 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Headphone Playback Switch'
        value.0 true
        value.1 true
    }
    control.15 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 1
        comment.range '0 - 31'
        comment.dbmin -4650
        comment.dbmax 0
        iface MIXER
        name 'Mono Playback Volume'
        value 0
    }
    control.16 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Mono Playback Switch'
        value false
    }
    control.17 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Capture Switch'
        value.0 false
        value.1 false
    }
    control.18 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Capture Switch'
        index 1
        value.0 true
        value.1 true
    }
    control.19 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Capture Switch'
        index 2
        value.0 true
        value.1 true
    }
    control.20 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -1200
        comment.dbmax 3450
        iface MIXER
        name 'Capture Volume'
        value.0 31
        value.1 31
    }
    control.21 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -1200
        comment.dbmax 3450
        iface MIXER
        name 'Capture Volume'
        index 1
        value.0 0
        value.1 0
    }
    control.22 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -1200
        comment.dbmax 3450
        iface MIXER
        name 'Capture Volume'
        index 2
        value.0 0
        value.1 0
    }
    control.23 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 1
        comment.item.0 Mic
        comment.item.1 'Front Mic'
        comment.item.2 Line
        comment.item.3 CD
        iface MIXER
        name 'Input Source'
        value Mic
    }
    control.24 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 1
        comment.item.0 Mic
        comment.item.1 'Front Mic'
        comment.item.2 Line
        comment.item.3 CD
        iface MIXER
        name 'Input Source'
        index 1
        value Mic
    }
    control.25 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 1
        comment.item.0 Mic
        comment.item.1 'Front Mic'
        comment.item.2 Line
        comment.item.3 CD
        iface MIXER
        name 'Input Source'
        index 2
        value Mic
    }
    control.26 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 1
        comment.range '0 - 31'
        comment.dbmin -4650
        comment.dbmax 0
        iface MIXER
        name 'Master Playback Volume'
        value 9
    }
    control.27 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Master Playback Switch'
        value true
    }
    control.28 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Off-hook Switch'
        value false
    }
    control.29 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Caller ID Switch'
        value false
    }
    control.30 {
        comment.access 'read write user'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 255'
        comment.tlv '0000000100000008ffffec1400000014'
        comment.dbmin -5100
        comment.dbmax 0
        iface MIXER
        name 'PCM Playback Volume'
        value.0 255
        value.1 255
    }
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
hid_a4tech
usbhid
hid
mmc_block
xt_limit
xt_tcpudp
ipt_LOG
ipt_MASQUERADE
xt_DSCP
ipt_REJECT
nf_conntrack_irc
nf_conntrack_ftp
xt_state
nls_utf8
isofs
nls_iso8859_1
nls_cp437
vfat
fat
aes_i586
aes_generic
xts
gf128mul
dm_crypt
binfmt_misc
lp
vboxnetadp
vboxnetflt
vboxdrv
rfcomm
sco
bridge
stp
bnep
l2cap
btusb
bluetooth
joydev
snd_hda_codec_si3054
snd_hda_codec_realtek
fbcon
tileblit
font
bitblit
softcursor
vga16fb
vgastate
snd_hda_intel
snd_hda_codec
snd_hwdep
snd_pcm_oss
snd_mixer_oss
snd_pcm
pcmcia
arc4
snd_seq_dummy
iptable_nat
nf_nat
nf_conntrack_ipv4
snd_seq_oss
nf_conntrack
nf_defrag_ipv4
iptable_mangle
iptable_filter
ip_tables
x_tables
snd_seq_midi
snd_rawmidi
iwl3945
snd_seq_midi_event
snd_seq
ppdev
iwlcore
i915
drm_kms_helper
parport_pc
snd_timer
usblp
snd_seq_device
mac80211
sdhci_pci
yenta_socket
rsrc_nonstatic
parport
drm
toshiba_acpi
intel_agp
snd
sdhci
led_class
psmouse
serio_raw
pcmcia_core
cfg80211
i2c_algo_bit
video
output
agpgart
soundcore
snd_page_alloc
ohci1394
e1000e
ieee1394


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x14 0x90170110
0x15 0x0221101f
0x16 0x40f000f6
0x18 0x02a110f0
0x19 0x40f000f8
0x1a 0x218411f0
0x1b 0x210411f0
0x1c 0x40f000fb
0x1d 0x598301f0
0x1e 0x40f000fd
0x1f 0x40f000fe

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:

/sys/class/sound/hwC0D1/init_pin_configs:

/sys/class/sound/hwC0D1/driver_pin_configs:

/sys/class/sound/hwC0D1/user_pin_configs:

/sys/class/sound/hwC0D1/init_verbs:


!!ALSA/HDA dmesg
!!------------------

[   19.134384] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   19.135807] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
[   19.135846] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
[   19.135852] HDA Intel 0000:00:1b.0: enabling device (0000 -> 0002)
[   19.135861]   alloc irq_desc for 22 on node -1
[   19.135863]   alloc kstat_irqs on node -1
[   19.135879] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   19.136177]   alloc irq_desc for 28 on node -1
[   19.136179]   alloc kstat_irqs on node -1
[   19.136190] HDA Intel 0000:00:1b.0: irq 28 for MSI/MSI-X
[   19.136222] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   19.136488] vga16fb: initializing
--
[   19.145805] Console: switching to colour frame buffer device 160x50
[   19.185216] hda_codec: ALC262: SKU not ready 0x598301f0
[   19.185368] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input6
[   19.209746] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input7

```

---

### Post by Kixtosh on 2010-10-08
From the launchpad bug report:> After a frustrating week of trying all the various suggested solutions it was a matter of reloading Windows, _manually toggling the sound function button to "on" (hold Fn and click Esc button_), reload Ubuntu and I have sound. I didn't even have to change the alsa-base.conf file.
My Portégé has this same hotkey layout, with Fn+ESC to mute/unmute in Windows. Several Fn hotkey functions do not seem to work with many Toshiba laptops when using Ubuntu (or any other Linux O.S. I may have tried), including (in my case):

- Fn+ESC: mute/unmute
- Fn+F3: standby
- Fn+F4: hibernate
- Fn+F6 & Fn+F7: adjust brightness (down or up)
- Fn+F8: turn wireless and/or bluetooth on/off (only bluetooth works)
- Fn+F9: touchpad on/off.

Several of the other Fn hotkey functions do work, such as the numeric pad (Fn+F11) or external vs. internal monitor selection (Fn+F5).

When I try to adjust the keyboard shortcuts using the System --> Preferences menu, curiously, the Fn key is never recognized when depressed to create new shortcuts. I got around this by assigning ALT+ESC to the mute/unmute function on my Portégé.

**What I'm wondering is:** would modifying that shortcut have been enough to enable you to use the same key sequence to turn sound back on. Perhaps you could try it with a Live CD of 10.04 Lucid Lynx, if you ever get the chance, since that would be a much easier solution, and it might be worth making it known to others in that case.

---

