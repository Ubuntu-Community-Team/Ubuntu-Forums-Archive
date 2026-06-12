---
title: "Some sound over HDMI"
date: 2009-08-25
forum: Multimedia Software
---

### Post by juicedM3 on 2009-08-25
I recently purchased an ASUS EN9500GT video card to add to my Mythbuntu system.  I cannot get multi-channel sound over HDMI.  I can run the following command and hear 2-channel stereo sound:

```

$ speaker-test -Dplughw:0,0 -c2

```

But if I change that to 6 channel or anything else, I get nothing.  Using the mobo (ASUS M3N78 PRO) onboard HDMI out previously, I was able to get 6-channel, DTS or DD.

alsamixer is not muted.

Output from aplay -l:

```

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Output from aplay -L

```

default:CARD=NVidia
    HDA NVidia, ALC1200 Analog
    Default Audio Device
front:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Digital
    IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)

```

Running mplayer on the command line, everything looks good.  No errors, finds the correct codecs, etc.

I was just able to run a DD test through the iec958 & surround51 device (from aplay -L).  Running the DTS test through the same devices produces static.  Using the HDMI device produces silence.

asound.conf just has the following line:

```

defaults.pcm.device 3

```

I'm running out of ideas but I'll continue to search.  Any help would be appreciated.

System:

ASUS M3N78 PRO mobo
ASUS EN9500GT video card
Mythbuntu 9.04 64-bit
nVidia 180.44
Alsa 1.0.20
Kernel 2.6.28-15

---

### Post by juicedM3 on 2009-08-26
Ok.  Some persistence has paid off.

I first upgraded to NVIDIA's 185.18.36 drivers.  I had to uninstalled Mythbuntu's 180.44 kernel modules to make that work.  I tested it with my onboard video card and it worked.

Still no sound w/ the 9500GT.

I then began to follow this thread:

[http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384)

Installing one of those packages changed something because I was able to run DD & DTS test successfully over iec958.

Next, I took a stab at my asound.conf file.  I searched for "asound.conf" and "iec958".  The first result yielded this page [http://www.mythtv.org/wiki/Intel_HD_Audio_-_Realtek_ALC88x](http://www.mythtv.org/wiki/Intel_HD_Audio_-_Realtek_ALC88x).  So I tried their asound.conf setting at the bottom of the page and now I can play MP3 files via mplayer!

My asound.conf file now looks like:

```

pcm.!default {
        type plug
        slave {
                rate 48000
                pcm "spdif"
                }
}
```

Now I just need to figure out my MythTV settings and I'll be happy.

w00t!  Just figured them out!  And now I have DD w/ OTA HDTV!  And reasonable sound levels!  My sound use to be incredible low and I'd have to crank up the volume on my receiver.

My settings:

```

Audio output device: /dev/adsp (I tried almost all of them!)
Passthrough output device: ALSA:iec958:{ AES0 0x02 } (not sure if it's necessary)
Enable AC3 to SPDIF passthrough (YES!)
Enable DTS to SPDIF passthroug (YES!)
```

I'd rather run the current NVIDIA driver's available w/ 9.04, but oh well.  Maybe I'll try backing them out.  I'd hate to undo something that works.

Ok.  Time for bed.

---

