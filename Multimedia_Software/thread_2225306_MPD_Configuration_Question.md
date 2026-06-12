---
title: "MPD Configuration Question"
date: 2014-05-20
forum: Multimedia Software
---

### Post by trijutro on 2014-05-20
Hello,

I'm trying to setup MPD server for playing music remotely controled by my phone. 
The sound should be played on HDMI out. But when I press play nothing happens. 
Obviously something is wrong configured. I hope the following information helps solving my problem. 

mpd.conf 
```

...
audio_output {
    type        "alsa"
    name        "HOMEBOX"
    device          "hw:1,0" # optional
#    format          "44100:16:2" #optional
    mixer_type      "software"      # optional
#    mixer_device    "default"    # optional
#    mixer_control    "PCM"        # optional
#    mixer_index    "0"        # optional
}
...

```

aplay -l
```

Karte 0: HDMI [HDA Intel HDMI], Gerät 3: HDMI 0 [HDMI 0]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
Karte 1: PCH [HDA Intel PCH], Gerät 0: ALC887-VD Analog [ALC887-VD Analog]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
Karte 1: PCH [HDA Intel PCH], Gerät 1: ALC887-VD Digital [ALC887-VD Digital]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0



```

aplay -L
```

null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    PulseAudio Sound Server
hdmi:CARD=HDMI,DEV=0
    HDA Intel HDMI, HDMI 0
    HDMI Audio Output
dmix:CARD=HDMI,DEV=3
    HDA Intel HDMI, HDMI 0
    Direct sample mixing device
dsnoop:CARD=HDMI,DEV=3
    HDA Intel HDMI, HDMI 0
    Direct sample snooping device
hw:CARD=HDMI,DEV=3
    HDA Intel HDMI, HDMI 0
    Direct hardware device without any conversions
plughw:CARD=HDMI,DEV=3
    HDA Intel HDMI, HDMI 0
    Hardware device with all software conversions
default:CARD=PCH
    HDA Intel PCH, ALC887-VD Analog
    Default Audio Device
sysdefault:CARD=PCH
    HDA Intel PCH, ALC887-VD Analog
    Default Audio Device
front:CARD=PCH,DEV=0
    HDA Intel PCH, ALC887-VD Analog
    Front speakers
surround40:CARD=PCH,DEV=0
    HDA Intel PCH, ALC887-VD Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=PCH,DEV=0
    HDA Intel PCH, ALC887-VD Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=PCH,DEV=0
    HDA Intel PCH, ALC887-VD Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=PCH,DEV=0
    HDA Intel PCH, ALC887-VD Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=PCH,DEV=0
    HDA Intel PCH, ALC887-VD Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=PCH,DEV=0
    HDA Intel PCH, ALC887-VD Digital
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=PCH,DEV=0
    HDA Intel PCH, ALC887-VD Analog
    Direct sample mixing device
dmix:CARD=PCH,DEV=1
    HDA Intel PCH, ALC887-VD Digital
    Direct sample mixing device
dsnoop:CARD=PCH,DEV=0
    HDA Intel PCH, ALC887-VD Analog
    Direct sample snooping device
dsnoop:CARD=PCH,DEV=1
    HDA Intel PCH, ALC887-VD Digital
    Direct sample snooping device
hw:CARD=PCH,DEV=0
    HDA Intel PCH, ALC887-VD Analog
    Direct hardware device without any conversions
hw:CARD=PCH,DEV=1
    HDA Intel PCH, ALC887-VD Digital
    Direct hardware device without any conversions
plughw:CARD=PCH,DEV=0
    HDA Intel PCH, ALC887-VD Analog
    Hardware device with all software conversions
plughw:CARD=PCH,DEV=1
    HDA Intel PCH, ALC887-VD Digital
    Hardware device with all software conversions

```

tail -f /var/log/mpd/mpd.log
```

...
May 21 02:13 : avahi: Service 'HOMEBOX' successfully established.
May 21 02:13 : alsa_mixer: Failed to read mixer for 'HOMEBOX': no such mixer control: PCM
May 21 02:13 : player: played "..."
ALSA lib pcm_hw.c:1667:(_snd_pcm_hw_open) Invalid value for card
May 21 02:13 : alsa_output: Failed to open "HOMEBOX" [alsa]: Failed to open ALSA device "hw:1,0": No such file or directory
May 21 02:13 : output: Failed to open audio output
May 21 02:13 : player: problems opening audio device while playing "..."
...

```

I also run the ALSA Information Script. The result is on [Pastebin]("http://pastebin.com/1x4n99yk").

I guess its the wrong device in mpd.conf. How can I figure out which is the right one? And which mixer control?

---

### Post by ssam on 2014-05-21
should it be
```
device          "hw:1,1"
```
does it help to comment out the mixer_type line?

---

