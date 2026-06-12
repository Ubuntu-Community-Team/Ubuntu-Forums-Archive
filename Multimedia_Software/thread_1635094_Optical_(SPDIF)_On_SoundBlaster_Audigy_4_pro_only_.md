---
title: "Optical (S/PDIF) On SoundBlaster Audigy 4 pro only in stereo"
date: 2010-12-01
forum: Multimedia Software
---

### Post by JDFire on 2010-12-01
Hello All,

I have an issue that I can't seem to resolve. I have an optical cable going from my SoundBlaster Audigy 4 Pro to my AV receiver. On my AV receiver it is only showing Stereo. I have tried to enable "S/PDIF Optical Raw" but when I do no sound is heard. Now I know that this optical connection can produce 5.1 surround sound as I was able to get sound when I install LinuxMCE which was able to get it to work but I was unable to determine the configuration in order to copy it to my Ubuntu 10.10 install. Below you will find the output for aplay -l and aplay -L

aplay -l
```
 **** List of PLAYBACK Hardware Devices ****
card 0: Audigy2 [SB Audigy 4 PRO [SB0380]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 0: Audigy2 [SB Audigy 4 PRO [SB0380]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Audigy2 [SB Audigy 4 PRO [SB0380]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Audigy2 [SB Audigy 4 PRO [SB0380]], device 4: p16v [p16v]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
 
```aplay -L

```
 default
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=Audigy2,DEV=0
    SB Audigy 4 PRO [SB0380], ADC Capture/Standard PCM Playback
    Front speakers
rear:CARD=Audigy2,DEV=0
    SB Audigy 4 PRO [SB0380], ADC Capture/Standard PCM Playback
    Rear speakers
center_lfe:CARD=Audigy2,DEV=0
    SB Audigy 4 PRO [SB0380], ADC Capture/Standard PCM Playback
    Center and Subwoofer speakers
side:CARD=Audigy2,DEV=0
    SB Audigy 4 PRO [SB0380], ADC Capture/Standard PCM Playback
    Side speakers
surround40:CARD=Audigy2,DEV=0
    SB Audigy 4 PRO [SB0380], ADC Capture/Standard PCM Playback
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Audigy2,DEV=0
    SB Audigy 4 PRO [SB0380], ADC Capture/Standard PCM Playback
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Audigy2,DEV=0
    SB Audigy 4 PRO [SB0380], ADC Capture/Standard PCM Playback
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Audigy2,DEV=0
    SB Audigy 4 PRO [SB0380], ADC Capture/Standard PCM Playback
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Audigy2,DEV=0
    SB Audigy 4 PRO [SB0380], ADC Capture/Standard PCM Playback
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Audigy2,DEV=0
    SB Audigy 4 PRO [SB0380], ADC Capture/Standard PCM Playback
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=Audigy2,DEV=0
    SB Audigy 4 PRO [SB0380], ADC Capture/Standard PCM Playback
    Direct sample mixing device
dmix:CARD=Audigy2,DEV=2
    SB Audigy 4 PRO [SB0380], Multichannel Capture/PT Playback
    Direct sample mixing device
dmix:CARD=Audigy2,DEV=3
    SB Audigy 4 PRO [SB0380], Multichannel Playback
    Direct sample mixing device
dmix:CARD=Audigy2,DEV=4
    SB Audigy 4 PRO [SB0380], p16v
    Direct sample mixing device
dsnoop:CARD=Audigy2,DEV=0
    SB Audigy 4 PRO [SB0380], ADC Capture/Standard PCM Playback
    Direct sample snooping device
dsnoop:CARD=Audigy2,DEV=2
    SB Audigy 4 PRO [SB0380], Multichannel Capture/PT Playback
    Direct sample snooping device
dsnoop:CARD=Audigy2,DEV=3
    SB Audigy 4 PRO [SB0380], Multichannel Playback
    Direct sample snooping device
dsnoop:CARD=Audigy2,DEV=4
    SB Audigy 4 PRO [SB0380], p16v
    Direct sample snooping device
hw:CARD=Audigy2,DEV=0
    SB Audigy 4 PRO [SB0380], ADC Capture/Standard PCM Playback
    Direct hardware device without any conversions
hw:CARD=Audigy2,DEV=2
    SB Audigy 4 PRO [SB0380], Multichannel Capture/PT Playback
    Direct hardware device without any conversions
hw:CARD=Audigy2,DEV=3
    SB Audigy 4 PRO [SB0380], Multichannel Playback
    Direct hardware device without any conversions
hw:CARD=Audigy2,DEV=4
    SB Audigy 4 PRO [SB0380], p16v
    Direct hardware device without any conversions
plughw:CARD=Audigy2,DEV=0
    SB Audigy 4 PRO [SB0380], ADC Capture/Standard PCM Playback
    Hardware device with all software conversions
plughw:CARD=Audigy2,DEV=2
    SB Audigy 4 PRO [SB0380], Multichannel Capture/PT Playback
    Hardware device with all software conversions
plughw:CARD=Audigy2,DEV=3
    SB Audigy 4 PRO [SB0380], Multichannel Playback
    Hardware device with all software conversions
plughw:CARD=Audigy2,DEV=4
    SB Audigy 4 PRO [SB0380], p16v
    Hardware device with all software conversions
 
```If anyone could assist me with this I would be most grateful. Thank you for your time and have a great day!

Kind regards,
JDFire

---

### Post by JDFire on 2010-12-01
dump ( Any ideas? )

---

### Post by mc4man on 2010-12-01
Probably the most direct way would be to enable digital 5.1 output in pulse. Then you'll get 5.1 pass thru for ac3 and dts. The only downside will be, (if it is to you), that stereo tracks will also show up as digital and be output in 6 channel. (screen

Another option would be to leave pulse at digital stereo (duplex) and use a player that can bypass pulse for s/pdif pass thru. Mplayer is an example there, can be set to try pass thru first automatically in it's config w/ something like this

> # Write your default config options here!
ao=alsa:device=spdif
afm=hwac3


I've 2 installs here (maverick, natty), one set up w/ the former. one the latter.
At this point I think I may go with the former and use either mplayer or audacious for stereo playback (2 speaker + sub), I can always process externally for stereo x2 or surround if desired. ( or use pulse
( audacious can use as in screen 2

There was a launchpad bug about pulse and d. 5.1 where how to enable was worked out, also have seen a thread here recently that shows how to also, - I'll find and edit in link.

edit: here's the link, seems pretty well laid out though I'd do something first.
If you look closely the command set you'll run it will get the libasound2-plugins source, build and cp some files. If you don't have the build-deps it will try to install and most likely fail there. So first go - 
```
sudo apt-get build-dep libasound2-plugins
```
Then copy and run the whole command set at once.

When done do a restart - do check /etc/asound.conf  and make sure it _looks like what's posted,_ particularly this area (blue), 
     ```
 channels 6
      card [COLOR="Blue"]$CARD[/COLOR]
    }
```
You should then find digital 5.1 available in Sound Preferences -> Hardware - profile dropdown

[http://ubuntuforums.org/showthread.php?t=1608804](http://ubuntuforums.org/showthread.php?t=1608804)

---

### Post by JDFire on 2010-12-01
mc4man, 

Thank you SO MUCH!!! This worked. Have a great day!

---

