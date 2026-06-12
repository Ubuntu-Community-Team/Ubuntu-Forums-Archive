---
title: "no sound on HDMI, codec: Intel Haswell HDMI"
date: 2013-12-10
forum: Multimedia Software
---

### Post by tho.tran1809 on 2013-12-10
Hi guys,

I tried to connect my Laptop to my TV. The screen is fine, but there's no sound on my TV, just only sound on the laptop.
I've codec Intel Haswell HDMI:
```
cat /proc/asound/card0/codec* | grep Codec
Codec: Intel Haswell HDMI
```

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA Intel HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 0: ALC3226 Analog [ALC3226 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
```


I've Radeon HD 8790M and I installed lastest fglrx from Ubuntu. I also enable radeon sound by adding below in /etc/default/grub:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash radeon.dpm=1 radeon.audio=1"
```


When I connected to TV, I did open pavucontrol and set output to HDMI 5.1 Surround, but still no sound from TV.

Thanks for all your helps!

---

### Post by tho.tran1809 on 2013-12-10
bump bump

some1 help me pls

---

### Post by oldfred on 2013-12-11
There is a comment here that AMD does not enable HDMI audio by default.

[http://www.phoronix.com/scan.php?page=news_item&px=MTUwMTY](http://www.phoronix.com/scan.php?page=news_item&px=MTUwMTY)

So I would research your Radeon settings. I only have nVidia so do not know much else.
Or can you connect HDMI to your motherboard video and use just the Intel video & audio?

Your video & processor are very new, so I do not know if this applies still or not.
[http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-to-work](http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-to-work)

---

### Post by tho.tran1809 on 2013-12-16
bumppppp

is there any1 tried HDMI sound for hybrid system of Intel Haswell and Radeon HD?

---

### Post by kerekfyp on 2013-12-18
Try this:

mplayer -ao alsa:device=hdmi /usr/share/sounds/ubuntu/stereo/system-ready.ogg

---

### Post by tho.tran1809 on 2013-12-20
> **kerekfyp said:**
> Try this:

mplayer -ao alsa:device=hdmi /usr/share/sounds/ubuntu/stereo/system-ready.ogg

below is what i got, NO SOUND:
```

[thaw@thaw-Latitude-E6540 ~]$ mplayer -ao alsa:device=hdmi /usr/share/sounds/ubuntu/stereo/system-ready.ogg
MPlayer2 UNKNOWN (C) 2000-2012 MPlayer Team
mplayer: could not open config files /home/thaw/.lircrc and /etc/lirc/lirc/lircrc
mplayer: No such file or directory
Failed to read LIRC config file ~/.lircrc.

Playing /usr/share/sounds/ubuntu/stereo/system-ready.ogg.
Detected file format: Ogg (libavformat)
[lavf] stream 0: audio (vorbis), -aid 0
Load subtitles in /usr/share/sounds/ubuntu/stereo/
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 1 ch, s16le, 80.0 kbit/11.34% (ratio: 10000->88200)
Selected audio codec: [ffvorbis] afm: ffmpeg (FFmpeg Vorbis)
==========================================================================
AO: [alsa] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:   0.7 (00.7) of 0.8 (00.7)  0.2% 


Exiting... (End of file)

```


By the way, I want to add some more information:
```

[thaw@thaw-Latitude-E6540 ~]$ cat /proc/asound/cards
 0 [HDMI           ]: HDA-Intel - HDA Intel HDMI
                      HDA Intel HDMI at 0xf7d34000 irq 50
 1 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xf7d30000 irq 47

[thaw@thaw-Latitude-E6540 ~]$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA Intel HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 0: ALC3226 Analog [ALC3226 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```


Then I tried: "mplayer -ao alsa:device=hw=1.0 /usr/share/sounds/ubuntu/stereo/system-ready.ogg", it worked, there's sound from laptop's speaker. But if I tried hw=0.3, 0.7 or 0.8, it didn't work.

Thanks for helps!

---

### Post by tho.tran1809 on 2013-12-24
bump bump again :(

---

### Post by andrew.mast.junk on 2014-01-03
I am having same problem but with Nvidia GPU. Laptop is a new Lenovo T440p.

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA Intel HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 0: ALC292 Analog [ALC292 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


HDMI audio refuses to work. I tried using aplay on 0,3 0,7 and 0,8.  And why are there 3 different audio devices?

---

