---
title: "ALSA plugs issue"
date: 2012-04-21
forum: Multimedia Software
---

### Post by Vevusio on 2012-04-21
problem: i cannot seem to be using the alsa plugs which are listed by aplay

my user is a member of the audio group, the comp is a headless ubuntu intsall, my aplay -l and -L output is

```

vevusio@magician:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: SB [HDA ATI SB], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: SB [HDA ATI SB], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

-----------------------------------------------------

vevusio@magician:~$ aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
hdmi:CARD=Generic
    HD-Audio Generic, ATI HDMI
    HDMI Audio Output
front:CARD=SB,DEV=0
    HDA ATI SB, ALC892 Analog
    Front speakers
surround40:CARD=SB,DEV=0
    HDA ATI SB, ALC892 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=SB,DEV=0
    HDA ATI SB, ALC892 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=SB,DEV=0
    HDA ATI SB, ALC892 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=SB,DEV=0
    HDA ATI SB, ALC892 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=SB,DEV=0
    HDA ATI SB, ALC892 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=SB,DEV=0
    HDA ATI SB, ALC892 Digital
    IEC958 (S/PDIF) Digital Audio Output

```

for all the details, my alsa info is
[http://www.alsa-project.org/db/?f=237bd0ef49a4adb62677bc097723a2f50a35b599](http://www.alsa-project.org/db/?f=237bd0ef49a4adb62677bc097723a2f50a35b599)

--
i can play wav files with the following devices

```

vevusio@magician:~$ aplay -D <device> /mnt/wdcg/duck.wav

--> where <device> can be
hw:1,0
hw:1,1
plughw:1,0
plughw:1,1

```which outputs stereo only (front left and front right)

now, when i try using one of the plugs listed in -L (any one), i get an error, ie.
```

vevusio@magician:~$ aplay -D surround51 /mnt/wdcg/duck.wav
aplay: main:608: audio open error: No such file or directory
OR
vevusio@magician:~$ aplay -D front /mnt/wdcg/duck.wav
aplay: main:608: audio open error: No such file or directory
...

NOTE: explicitly stating plug:surround51 does not work either

```when using speaker-test as in the next code snippet i only hear the output when "0 - Front Left" and "1 - Front Right" is iterated over (while the following do not produce any audio: "4 - Center", "3 - Rear Right",  "2 - Rear Left", "5 - LFE")

```

vevusio@magician:~$ speaker-test -D plughw:1,1 -c 6

```the pc is connected to a sony home theater (decoder? it is split up in a dvd-player unit and a sound-unit which the speakers are plugged in to, i am not sure if the sound-unit can be called a decoder though) using an optical cable (toslink)

however i don't think this really is relevant since the surround51 and all other plugs already fail, so i believe the problem lies with my computer

i have not found anything when googling for stuff like "alsa only hwplug" or "alsa not working plug|plugs" etc. 

any help would be appreciated

---

### Post by BicyclerBoy on 2012-04-21
Are your HDA audio device on a video card or mobo chipset?
Is it a combo CPU/GPU AMD fusion ?
(I'm not familiar with ATI/AMD device labels)

AFAIK If the ATI SB device is a video card then the audio device will not work right without a X server running & AMD proprietary driver Catalyst.

How come your alsa kernel & user libs are so old?
Are you holding back any kernel updates?
My lucid 10.04.3 was alsa 1.0.23/1.0.24...

The Toslink (optical S/PDIF) can only support stereo PCM max 96KHz 24bit & matrix encoded AC3 or DTS digital data stream.
The coaxial S/PDIF max 192KHz/24bit on some pro equip.
S/PDIF can not carry multi-channel PCM..

aplay & speaker-test do not produce matrix encoded test stream only PCM..
aplay requires a 6 ch wav file to test surround51.

The plughw devices automatically re-sample reformat to suit the output device, so aplay -c 6 -r 44100-D plughw:0,0 results in stereo at some default sample rate.

The surround51 device can only output analogue 5.1 or PCM over HDMI unless you link it to an encoder plug (a52 etc)..

To test the multi-channel audio over S/PDIF:
need media player support digital pass-thru'
& media with AC3 or DTS
or media player with AC3 or DTS encoder (VLC, MythTV have AC3 encoder)

Or
 media player that supports multi-ch audio (VLC, mplayer etc)
& media player that can be pointed at a specific audio device (VLC, mplayer)
 alsa plugin a52 encoder
& multi-ch audio media.


The aplay -L devices problem...
You should be able to do this
aplay -c 2 -D surround51 -r 48000 -f S16_LE -V stereo some-stereo-file.wav
aplay -c 6 -D surround51 -r 48000 -f S16_LE -V stereo some-6ch-file.wav
but you only hear stereo unless you have HDMI connection or 6 ch analogue or the alsa a52 encoder plugin..

Note:
Your ~/.asound.rc redefines alsa default to be dmixer linked to hw:1,0 at 44K100Hz stereo

---

