---
title: "Headphone won't mute speakers"
date: 2011-06-12
forum: Multimedia Software
---

### Post by Lawck on 2011-06-12
When I plug in my headphone on the front panel of the computer case, sound output is muted on both: headphone and speakers.

When I unmute it, it plays on both at the same time.

I can't seem to get it working properly. I've seen people with the same problem but never figured how they got it working and it usually depended on their computer brand. Anyone?


Might be useful:

lsmod
> 
Module                  Size  Used by
binfmt_misc            17565  1 
vesafb                 13761  1 
snd_hda_codec_hdmi     28103  4 
snd_hda_codec_via      62470  1 
snd_hda_intel          33211  3 
snd_usb_audio         112426  2 
snd_usbmidi_lib        25139  1 snd_usb_audio
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel
nvidia              10709116  48 
snd_hwdep              13604  2 snd_usb_audio,snd_hda_codec
snd_seq_midi           13324  0 
snd_pcm                96625  6 snd_hda_codec_hdmi,snd_hda_intel,snd_usb_audio,snd_hda_codec
snd_rawmidi            30486  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    67382  20 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel,snd_usb_audio,snd_usbmidi_lib,snd_hda_codec,snd_hwdep,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
gspca_zc3xx            52441  0 
gspca_main             36853  1 gspca_zc3xx
videodev               82052  1 gspca_main
v4l2_compat_ioctl32    17078  1 videodev
lp                     17825  0 
ppdev                  17113  0 
psmouse                73535  0 
parport_pc             36959  1 
serio_raw              13166  0 
parport                46458  3 lp,ppdev,parport_pc
asus_atk0110           17976  0 
usbhid                 46956  0 
hid                    91020  1 usbhid
r8169                  48022  0 
pata_jmicron           12747  1 


lspci

> 
00:00.0 Host bridge: Intel Corporation Core Processor DMI (rev 11)
00:03.0 PCI bridge: Intel Corporation Core Processor PCI Express Root Port 1 (rev 11)
00:08.0 System peripheral: Intel Corporation Core Processor System Management Registers (rev 11)
00:08.1 System peripheral: Intel Corporation Core Processor Semaphore and Scratchpad Registers (rev 11)
00:08.2 System peripheral: Intel Corporation Core Processor System Control and Status Registers (rev 11)
00:08.3 System peripheral: Intel Corporation Core Processor Miscellaneous Registers (rev 11)
00:10.0 System peripheral: Intel Corporation Core Processor QPI Link (rev 11)
00:10.1 System peripheral: Intel Corporation Core Processor QPI Routing and Protocol Registers (rev 11)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA IDE Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.5 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 2 port SATA IDE Controller (rev 06)
01:00.0 VGA compatible controller: nVidia Corporation GF104 [GeForce GTX 460] (rev a1)
01:00.1 Audio device: nVidia Corporation GF104 High Definition Audio Controller (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
03:00.0 IDE interface: JMicron Technology Corp. JMB368 IDE controller



aplay -l
> 
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 1/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: Intel [HDA Intel], device 1: VT1708S Digital [VT1708S Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


alsa-base.conf
> 
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


Thanks in advance.

---

### Post by Lawck on 2011-06-13
Anyone?

On alsamixer I've realized that turning "Independent HP" on mutes my headphone. Is there anyway I can change it to mute my speakers instead?

---

### Post by lidex on 2011-06-18
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by Lawck on 2011-06-18
Thank you for your response. Here's the file you requested:

[http://www.alsa-project.org/db/?f=3b638dcf996a951a480da2b8a0cbc6f131d51221](http://www.alsa-project.org/db/?f=3b638dcf996a951a480da2b8a0cbc6f131d51221)

---

### Post by lidex on 2011-06-18
See the last post here:
[http://ubuntuforums.org/showthread.php?t=1615907](http://ubuntuforums.org/showthread.php?t=1615907)

---

### Post by Lawck on 2011-06-18
I changed it to AC97 but it made no difference. The problem persists. =/

---

### Post by alienjon on 2012-05-11
Was this problem ever resolved?  I seem to have the same problem myself.  I can't set the audio device in the BIOS on my laptop (I don't even have an audio option there).  Here's the also info:

[http://www.alsa-project.org/db/?f=d806ac9609237736177d932f80f014d091167663]("http://www.alsa-project.org/db/?f=d806ac9609237736177d932f80f014d091167663")

---

### Post by Lawck on 2012-05-11
Unfortunately not. I've given up long ago. :(

---

### Post by alienjon on 2012-05-11
Hmm... It seems that if I change the snd-hda-intel model option to anything but 3stack-6ch-dig I only get sound out of my subwoofer, but I also can mute the speakers with the headset plugged in (the option appears in alsamixer as well).  When I have 3stack-6ch-dig set, however, sound comes out of the speakers as they should, but I don't even have the option come up in alsamixer.  Unfortunately my laptop's model is ALC1200 which isn't mentioned in the list, so I don't have much direction other than randomly trying and rebooting...

---

