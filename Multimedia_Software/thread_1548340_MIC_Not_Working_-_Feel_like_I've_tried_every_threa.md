---
title: "MIC Not Working - Feel like I've tried every thread here"
date: 2010-08-08
forum: Multimedia Software
---

### Post by chris_safrica on 2010-08-08
Hi, 

I've had a major problem getting my mic to work with pulseaudio. After looking around for a while I see that I'm certainly not the only one.

I have run a whole lot of suggested commands - copied all sorts of lines into /etc/modprobe.d/alsa-base.conf - upped all sorts of volume controls with alsamixer or pulseaudio - uninstalled and reinstalled - upgraded and..

NOTHING WORKS

I actually messed around with it so much that I had to reinstall Ubuntu again (10.04)

I have been using linux on-and-off for a while but have never been the kind of person to remember all these long commands...so please consider me to be Newbie (as I feel like one at the moment)

I'm sure if there's anyone out there able to help they'll need a bit of info about the machine. 

This is after a fresh install - so please feel free to take anything step-by-step upgrades...commands...the lot

Lets start with:

Packard Bell EasyNote V5 series (V5910)

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)

The sudo gedit /etc/modprobe.d/alsa-base.config - brings up 

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

Somewhere along the line I have run commands to get all sorts of info. So please feel free to send more if need be.

There are all sorts of threads relating to specific machines - specific audio cards - etc....I probably have read them....but post anyway. 

All I want is my MIC To work. My Sound Works fine. 

Thanks in advance.

---

### Post by utilitytrack on 2010-08-08
Hello. Give on forum more diagnostic info:

```
$ uname -r
$ dpkg -l alsa-*
$ lspci -nn | grep Audio
$ cat /proc/asound/card0/codec#0 | grep Codec
$ cat /proc/asound/devices
$ cat /etc/modprobe.d/alsa-base.conf
$ grep -e audio /etc/group
# hwinfo --sound

```
and your PC/laptop model

---

### Post by chris_safrica on 2010-08-08
Hi Thanks for Quick Response, It's really appreciated!!!

Just a note, this is a fresh install of Ubuntu so no upgrades or anything like that have been installed.

Here's all that info:

$uname -r
2.6.32-21-generic

$dpkg -l alsa-*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  alsa-base      1.0.22.1+dfsg- ALSA driver configuration files
un  alsa-oss       <none>         (no description available)
ii  alsa-utils     1.0.22-0ubuntu ALSA utilities

$lspci -nn | grep Audio
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)

$ cat /proc/asound/card0/codec#0 | grep Codec
Codec: Realtek ALC260

$ cat /proc/asound/devices
  2:        : timer
  3:        : sequencer
  4: [ 0- 1]: digital audio playback
  5: [ 0- 0]: digital audio playback
  6: [ 0- 0]: digital audio capture
  7: [ 0- 1]: hardware dependent
  8: [ 0- 0]: hardware dependent
  9: [ 0]   : control

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

$ grep -e audio /etc/group
audio:x:29:pulse

$ hwinfo --sound
10: PCI 1b.0: 0403 Audio device                                 
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_8086_27d8
  Unique ID: u1Nb.ul4ocaS8Tf0
  SysFS ID: /devices/pci0000:00/0000:00:1b.0
  SysFS BusID: 0000:00:1b.0
  Hardware Class: sound
  Model: "Intel 82801G (ICH7 Family) High Definition Audio Controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x27d8 "82801G (ICH7 Family) High Definition Audio Controller"
  SubVendor: pci 0x1631 "Packard Bell B.V."
  SubDevice: pci 0xc017 
  Revision: 0x02
  Driver: "HDA Intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0xac340000-0xac343fff (rw,non-prefetchable)
  IRQ: 23 (967 events)
  Module Alias: "pci:v00008086d000027D8sv00001631sd0000C017bc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

---

### Post by chris_safrica on 2010-08-08
OH Yes Sorry:

My Laptop is a:

Packard Bell
P/N : PB53D0026
EasyNote v5910

And I also see:

MS Model:SAG00IN002F - If that means anything in particular

---

### Post by utilitytrack on 2010-08-08
I can't find this "EasyNote v5910" laptop on Packard Bell site. Also Google don't know anything. It is some old and rare laptop? Did you don't mistaken in model number? May be it's EasyNote V5/MV45 series?

---

### Post by chris_safrica on 2010-08-08
All I can See on the Bottom Sticker is the following:

Packard Bell
Model MIT-SABLE-G

S/N:
S/N: 691301060239
MS Model:SAG00IN002F

REF:
P/N : PB53D0026
EASYNOTE v5910

I also tried to look for it on the Google and think it falls into the following catgory: 
[http://www.yadigi.com/bater%C3%83%C2%ADa-packard-bell-easynote-v5-v5908-v5910-mv45-serie-bp8050s-p-7183.html](http://www.yadigi.com/bater%C3%83%C2%ADa-packard-bell-easynote-v5-v5908-v5910-mv45-serie-bp8050s-p-7183.html)

You can see the v5910 there. Thats What is says on the bottom of mine. 

Is this what you were looking for?

---

### Post by chris_safrica on 2010-08-08
Hi Sorry...Just saw your last post. 

Yes I think it is the EasyNote V5/MV45.

In fact quite sure.

---

### Post by chris_safrica on 2010-08-08
By The way - You're right about it being fairly old and arcane.

I often think it was a model not fit for the western world so it just got dumped here in Africa...lol

I've never really been able to find real support for it. Even with its original XP.

---

### Post by utilitytrack on 2010-08-08
Ok. I think that you need properly configured audio codec. First, upgrade your ALSA because ([http://www.alsa-project.org/main/index.php/Changes_v1.0.22_v1.0.23#HDA_Codec_driver]("http://www.alsa-project.org/main/index.php/Changes_v1.0.22_v1.0.23#HDA_Codec_driver")): 
> ALSA: hda - Fix secondary ADC of ALC260 basic model

Follow these instructions for that: [http://ubuntuforums.org/showthread.php?p=6589810#post6589810]("http://ubuntuforums.org/showthread.php?p=6589810#post6589810")

Second, probable you will need change args that pass to [FONT="Courier New"]snd-hda-intel[/FONT] module. But it on the future. Upgrade ALSA first, next run [FONT="Courier New"]alsamixer[/FONT], type F4 and make the levels up ("Capture", "Mic Boost", "Internal Mic Boost" and may be some other). If these controls are present then run test record
```
$ arecord -vv -f cd -t wav sample.wav
```
and give here your impressions.

---

### Post by lidex on 2010-08-08
What do you get for these commands:
```
dmesg | grep -C1 -E 'ALSA|HDA|HDMI|sound|hda.codec|hda.intel'
```
```
sudo dmidecode -t bios
sudo dmidecode -t baseboard

```

---

### Post by chris_safrica on 2010-08-10
utilitytrack,

It Worked!

Thank you so much...Really I can't thank you enough. 
Its guys like you and Lidex that really make the difference with Linux and specifically Ubuntu.

Also that guy who wrote the script....what a lot of work.

If you ever come to SA let me know, I own an accommodation establishment and the hours you saved me certainly worth a couple free nights.

Best and Thanks again, 

Chris

---

### Post by chris_safrica on 2010-08-10
.

---

### Post by utilitytrack on 2010-08-10
**chris_safrica,** I am very happy for you! Thank you!

---

