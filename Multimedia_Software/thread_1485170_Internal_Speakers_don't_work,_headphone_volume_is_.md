---
title: "Internal Speakers don't work, headphone volume is very low"
date: 2010-05-16
forum: Multimedia Software
---

### Post by fysicsandpholds on 2010-05-16
I have an imac and i recently decided to dual boot Ubuntu as well.
The sound is fine on the mac partition but the internal speakers dont work on the Ubuntu side.
headphones do work but the volume is oddly low
Nothing is muted on alsamixer, and I think i have the right driver for my sound card.
Any help would be greatly appreciated, I have resorted to plugging my computer into my mono guitar amp which wastes enormous amounts of power and I lose half the sound.
my card is the HDA Intel
my chip is the Realtek ALC887A

---

### Post by fysicsandpholds on 2010-05-16
I have already searched through many threads and guides so this is my last resort

---

### Post by fysicsandpholds on 2010-05-16
SOLVED
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by KevG on 2010-05-16
I don't have a mac, but I do have hda-intel sound that wasn't working on fresh install of 10.04

My system details are:

SONY VPCEB1M0E

$ aplay -l 
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC269
Codec: Intel G45 DEVIBX

$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)

This fixed sound for me:

Download hda-verb from [ftp://ftp.suse.com/pub/people/tiwai/...erb-0.3.tar.gz]("ftp://ftp.suse.com/pub/people/tiwai/misc/hda-verb-0.3.tar.gz").

decompress with:
gunzip hda-verb-0.3.tar.gz
untar with:
tar -xf hda-verb-0.3.tar
make and install with:
cd hda-verb-0.3 ; sudo make ; sudo cp hda-verb /usr/bin/

just before exit(0) in /etc/rc.local add the following line to enable audio amp at reboot

hda-verb /dev/snd/hwC0D0 0x19 SET_PIN_WIDGET_CONTROL 0x22

Got any more info on your system?

Also this thread might be useful:
[http://ubuntuforums.org/showthread.php?t=1043568&highlight=hda-verb](http://ubuntuforums.org/showthread.php?t=1043568&highlight=hda-verb)

---

### Post by lidex on 2010-05-16
*edit:sorry...wrong thread*

---

