---
title: "Unable to get sound through Nvidia ION with HDMI Ubuntu 10.10"
date: 2011-01-09
forum: Multimedia Software
---

### Post by hybrid180 on 2011-01-09
Hi, 

I am a total noob to Ubuntu, and linux in general. I have an hold PC laying around that I want to use as an htpc. I added a ZOTAC ION-GPU-A-E ION graphics card to the pc and installed Ubuntu 10.10. Video works fine except there is no sound coming out of the HDMI. I have unmuted all spdif outputs in alsamixer, and I see it listed when I type aplay -l

Here is the output from aplay -l:
```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

output from aplay -L

```

default
pulse
    Playback/recording through the PulseAudio sound server
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=1
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=2
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=3
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
dmix:CARD=NVidia,DEV=3
    HDA NVidia, NVIDIA HDMI
    Direct sample mixing device
dmix:CARD=NVidia,DEV=7
    HDA NVidia, NVIDIA HDMI
    Direct sample mixing device
dmix:CARD=NVidia,DEV=8
    HDA NVidia, NVIDIA HDMI
    Direct sample mixing device
dmix:CARD=NVidia,DEV=9
    HDA NVidia, NVIDIA HDMI
    Direct sample mixing device
dsnoop:CARD=NVidia,DEV=3
    HDA NVidia, NVIDIA HDMI
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=7
    HDA NVidia, NVIDIA HDMI
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=8
    HDA NVidia, NVIDIA HDMI
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=9
    HDA NVidia, NVIDIA HDMI
    Direct sample snooping device
hw:CARD=NVidia,DEV=3
    HDA NVidia, NVIDIA HDMI
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=7
    HDA NVidia, NVIDIA HDMI
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=8
    HDA NVidia, NVIDIA HDMI
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=9
    HDA NVidia, NVIDIA HDMI
    Direct hardware device without any conversions
plughw:CARD=NVidia,DEV=3
    HDA NVidia, NVIDIA HDMI
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=7
    HDA NVidia, NVIDIA HDMI
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=8
    HDA NVidia, NVIDIA HDMI
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=9
    HDA NVidia, NVIDIA HDMI
    Hardware device with all software conversions
front:CARD=CK804,DEV=0
    NVidia CK804, NVidia CK804
    Front speakers
surround40:CARD=CK804,DEV=0
    NVidia CK804, NVidia CK804
    4.0 Surround output to Front and Rear speakers
surround41:CARD=CK804,DEV=0
    NVidia CK804, NVidia CK804
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=CK804,DEV=0
    NVidia CK804, NVidia CK804
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=CK804,DEV=0
    NVidia CK804, NVidia CK804
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=CK804,DEV=0
    NVidia CK804, NVidia CK804
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=CK804,DEV=0
    NVidia CK804, NVidia CK804 - IEC958
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=CK804,DEV=0
    NVidia CK804, NVidia CK804
    Direct sample mixing device
dmix:CARD=CK804,DEV=2
    NVidia CK804, NVidia CK804 - IEC958
    Direct sample mixing device
dsnoop:CARD=CK804,DEV=0
    NVidia CK804, NVidia CK804
    Direct sample snooping device
dsnoop:CARD=CK804,DEV=2
    NVidia CK804, NVidia CK804 - IEC958
    Direct sample snooping device
hw:CARD=CK804,DEV=0
    NVidia CK804, NVidia CK804
    Direct hardware device without any conversions
hw:CARD=CK804,DEV=2
    NVidia CK804, NVidia CK804 - IEC958
    Direct hardware device without any conversions
plughw:CARD=CK804,DEV=0
    NVidia CK804, NVidia CK804
    Hardware device with all software conversions
plughw:CARD=CK804,DEV=2
    NVidia CK804, NVidia CK804 - IEC958
    Hardware device with all software conversions

```

Is there something I am doing wrong here? Or something I should look at? I would appreciate any help as the movies look great but just isn't the same without sound :)

Thanks

---

### Post by alcantir on 2011-01-22
Just wanted to add in that I have the same issue as far as I can see. I'm using the Asus AT5IonT-I MB. It is a fresh install Ubuntu 10.10. I've tried selecting HDMI for default output with no success. S/PDIF and analog works fine.

Any help is deeply appreciated.

aplay -l:
```
**** Lista över PLAYBACK hårdvaruenheter ****
kort 0: Intel [HDA Intel], enhet 0: ALC887 Analog [ALC887 Analog]
  Underordnade enheter: 1/1
  Underordnad enhet nr. 0: subdevice #0
kort 0: Intel [HDA Intel], enhet 1: ALC887 Digital [ALC887 Digital]
  Underordnade enheter: 1/1
  Underordnad enhet nr. 0: subdevice #0
kort 1: NVidia [HDA NVidia], enhet 3: NVIDIA HDMI [NVIDIA HDMI]
  Underordnade enheter: 1/1
  Underordnad enhet nr. 0: subdevice #0
kort 1: NVidia [HDA NVidia], enhet 7: NVIDIA HDMI [NVIDIA HDMI]
  Underordnade enheter: 1/1
  Underordnad enhet nr. 0: subdevice #0
kort 1: NVidia [HDA NVidia], enhet 8: NVIDIA HDMI [NVIDIA HDMI]
  Underordnade enheter: 1/1
  Underordnad enhet nr. 0: subdevice #0
kort 1: NVidia [HDA NVidia], enhet 9: NVIDIA HDMI [NVIDIA HDMI]
  Underordnade enheter: 1/1
  Underordnad enhet nr. 0: subdevice #0

```aplay -L:
```
default
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=Intel,DEV=0
    HDA Intel, ALC887 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC887 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC887 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC887 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC887 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC887 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, ALC887 Digital
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=Intel,DEV=0
    HDA Intel, ALC887 Analog
    Direct sample mixing device
dmix:CARD=Intel,DEV=1
    HDA Intel, ALC887 Digital
    Direct sample mixing device
dsnoop:CARD=Intel,DEV=0
    HDA Intel, ALC887 Analog
    Direct sample snooping device
dsnoop:CARD=Intel,DEV=1
    HDA Intel, ALC887 Digital
    Direct sample snooping device
hw:CARD=Intel,DEV=0
    HDA Intel, ALC887 Analog
    Direct hardware device without any conversions
hw:CARD=Intel,DEV=1
    HDA Intel, ALC887 Digital
    Direct hardware device without any conversions
plughw:CARD=Intel,DEV=0
    HDA Intel, ALC887 Analog
    Hardware device with all software conversions
plughw:CARD=Intel,DEV=1
    HDA Intel, ALC887 Digital
    Hardware device with all software conversions
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=1
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=2
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=3
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
dmix:CARD=NVidia,DEV=3
    HDA NVidia, NVIDIA HDMI
    Direct sample mixing device
dmix:CARD=NVidia,DEV=7
    HDA NVidia, NVIDIA HDMI
    Direct sample mixing device
dmix:CARD=NVidia,DEV=8
    HDA NVidia, NVIDIA HDMI
    Direct sample mixing device
dmix:CARD=NVidia,DEV=9
    HDA NVidia, NVIDIA HDMI
    Direct sample mixing device
dsnoop:CARD=NVidia,DEV=3
    HDA NVidia, NVIDIA HDMI
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=7
    HDA NVidia, NVIDIA HDMI
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=8
    HDA NVidia, NVIDIA HDMI
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=9
    HDA NVidia, NVIDIA HDMI
    Direct sample snooping device
hw:CARD=NVidia,DEV=3
    HDA NVidia, NVIDIA HDMI
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=7
    HDA NVidia, NVIDIA HDMI
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=8
    HDA NVidia, NVIDIA HDMI
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=9
    HDA NVidia, NVIDIA HDMI
    Direct hardware device without any conversions
plughw:CARD=NVidia,DEV=3
    HDA NVidia, NVIDIA HDMI
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=7
    HDA NVidia, NVIDIA HDMI
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=8
    HDA NVidia, NVIDIA HDMI
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=9
    HDA NVidia, NVIDIA HDMI
    Hardware device with all software conversions
```

---

### Post by Nitrok on 2011-01-22
Hi,
had same problem and these settings worked: [http://ubuntuforums.org/showthread.php?t=1607475](http://ubuntuforums.org/showthread.php?t=1607475)

---

### Post by michcook on 2011-01-23
> **Nitrok said:**
> Hi,
had same problem and these settings worked: [http://ubuntuforums.org/showthread.php?t=1607475](http://ubuntuforums.org/showthread.php?t=1607475)

This too worked for me.  I tried updating pulseaudio etc as per older forum threads.  That made things worse.  In the end, unmuting "S/PDIF 1 <- un-mute by hitting m" did the trick... completely unobvious.

Now I'm left with partial delay/drift < 0.02secs between audio & video and if I turn off my HDMI receiver and/or suspend my Zotac I get audio drops every 15secs for about 0.5 secs until I reboot the Zotac box.

As an aside: Anyone know how to adjust the audio-sync delay in XBMC by keyboard instead of mouse. ;o)

---

### Post by alcantir on 2011-01-31
Thnx for your help, really appreciated. Unfortunately it still does not work. I've been muting and unmuting forever it seems with no success.

Any tips much appreciated!

---

### Post by michcook on 2011-01-31
> **alcantir said:**
> Thnx for your help, really appreciated. Unfortunately it still does not work. I've been muting and unmuting forever it seems with no success.

Any tips much appreciated!

I'm sorry, I dont have much to offer.  I dont know how sound in general, let alone HDMI be so complicated in Linux.  Dont get me started on screen resolutions and xorg.conf!

I did attempt to follow some older posts about recompiling PulseAudio or switch to ALSA... I tried down that path, the compliation/repositories failed and I gave up and looked for the above unmute-solution.

I feel your pain.

---

### Post by alcantir on 2011-03-12
My problem is solved.:D

Found the following page which helped me out.
[http://ubuntuforums.org/showthread.php?t=1668737&highlight=hdmi+sound](http://ubuntuforums.org/showthread.php?t=1668737&highlight=hdmi+sound)

The tricky thing is finding what probe_mask worx for your card. For the Asus AT5IonT-I I used

```
options snd-hda-intel probe_mask=-1,0x2
```Consider the following link for help on finding your probe_mask
[http://ubuntuforums.org/showpost.php?p=10465858&postcount=21](http://ubuntuforums.org/showpost.php?p=10465858&postcount=21)

---

### Post by croxas on 2011-03-26
Thanks, after all the "google-ing" this fixes the HDMI sound output on my HTPC build (ASUS AT51ONT-I).

---

