---
title: "ALSA Surround Sound - ATI IXP AC97"
date: 2010-06-11
forum: Multimedia Software
---

### Post by esoikie on 2010-06-11
Having some problems with my surround sound.  Ultimately, I'd like to listen to MP3's in Amarok using the 4 speakers and subwoofer.

some sound system information:

aplay -l output
```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: IXP [ATI IXP], device 1: ATI IXP IEC958 [ATI IXP IEC958 (AC97)]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

aplay -L output
```

aplay -L
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=IXP,DEV=0
    ATI IXP, ATI IXP AC97
    Front speakers
surround40:CARD=IXP,DEV=0
    ATI IXP, ATI IXP AC97
    4.0 Surround output to Front and Rear speakers
surround41:CARD=IXP,DEV=0
    ATI IXP, ATI IXP AC97
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=IXP,DEV=0
    ATI IXP, ATI IXP AC97
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=IXP,DEV=0
    ATI IXP, ATI IXP AC97
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
iec958:CARD=IXP,DEV=0
    ATI IXP, ATI IXP IEC958 (AC97)
    IEC958 (S/PDIF) Digital Audio Output
```

Also, here is my current .asoundrc
```
pcm.atiixp {
          type hw
          card 0
       }
       
ctl.atiixp {
          type hw
          card 0

```

Now... I have a 6 channel wav file.  When I type 'aplay 6channel.wav':
It says "Front Left" played through the front left speaker
It says "Front Right" played through the front right speaker
It says "Center" which isn't heard.  (So far so good)
It says "Rear Left" played through the front left and right speakers.
It says "Rear Right" played through the rear right speaker.

Also when I type 'speaker-test' I get no sound through the rear left speaker under the current configuration.  At some point yesterday (I have no idea how) I did temporarily have sound in the rear left speaker, so I know it works.  However when I rebooted, I lost it.

---

