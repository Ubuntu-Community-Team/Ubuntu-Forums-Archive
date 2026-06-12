---
title: "HDA ATI HDMI Loud Background, Tiny Voice"
date: 2008-10-07
forum: Multimedia Software
---

### Post by boralyl on 2008-10-07
I had spent many hours getting sound to work through HDMI for mythbuntu 8..04.  It finally worked with VLC and xine, which was good enough for me.  However today, after changing no settings, I went to paly a video with VLC and noticed an odd problem.  It was a sketch comedy, and the audience laughter was very loud, but I would have to crank up the volume to hear anything the characters had to say.  I confirmed this with several other video files.  Any idea as to what happened?

Some information:

```

$cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC885

```

```

$lshw
      *-multimedia
             description: Audio device
             product: SBx00 Azalia
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=32 module=snd_hda_intel

```

```

$aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC882 Analog [ALC882 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC882 Digital [ALC882 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```

$ cat /proc/asound/cards
0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfe024000 irq 16
1 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xfdffc000 irq 19

```

The relevant config in ~/.vlc/vlcrc
```

# ALSA Device Name (string)
alsadev=plughw:1,3

```

I am confused because I didn't change any settings, or update any packages.  The only package I had installed since it stopped working was php5-cli, which has nothing to do with sound.

---

### Post by markbuntu on 2008-10-08
Your channels are all mixed up. Front and center are usually the ones with the dialog and rear and side for background sounds, like the audience. How that happened, I don't know. 

You can make a default channel map that may help but I don't know much about how that will effect the HDMI. Here are all the links I have collected about digital output and surround sound. No doubt you have been to may of them already but there is always a chance...


[http://www.automaticable.com/2008-05-28/how-to-enable-surround-sound-on-ubuntu-hardy/](http://www.automaticable.com/2008-05-28/how-to-enable-surround-sound-on-ubuntu-hardy/)


[http://ubuntuforums.org/showthread.php?t=795525](http://ubuntuforums.org/showthread.php?t=795525)


[http://alsa.opensrc.org/index.php/DigitalOut](http://alsa.opensrc.org/index.php/DigitalOut)

[http://ubuntuforums.org/showthread.php?t=899139](http://ubuntuforums.org/showthread.php?t=899139)

[http://ubuntuforums.org/showthread.php?t=776958](http://ubuntuforums.org/showthread.php?t=776958)

[http://ubuntuforums.org/showthread.php?t=714712](http://ubuntuforums.org/showthread.php?t=714712)

---

