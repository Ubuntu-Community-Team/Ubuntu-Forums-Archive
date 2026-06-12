---
title: "Can't recognize sound card/hardware anymore"
date: 2012-02-10
forum: Multimedia Software
---

### Post by HUN73R on 2012-02-10
Hello,

I just plugged my new 5.1 sound (Samsung ht-d350k) to my notebook (Sony Vaio VPCF115FM) optical out port.

Things were going well, except for the fact it was playing like a 2.1 sound system. Unsuccessfully trying to make it work correctly, I downloaded and installed a new Realtek driver, which after installed, simply made my sound card disappear from the system.

Now I can't get any sound reproduced, nor the sound card is displayed under the "Hardware" tab (System => Preferences => Sound) anymore.

Therefore, any tip is appreciated!! I tried reinstalling alsa and taking some other steps I found on the web, however nothing worked. Also, the sound icon is no longer visible on the system tray.

Ubuntu 11.04 Natty 64 bits
uname -a: Linux mauro 2.6.38-13-generic #55-Ubuntu SMP Tue Jan 24 15:34:24 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux


What should I do next?
Thanks in advance!

---

### Post by HUN73R on 2012-02-11
Ok, booting with an older kernel version (2.6.38-12-generic) the sound is back, however, still 2.1 channels and without the sound icon on the tray.

Should I remove the newest kernel version (2.6.38-13-generic)? If so, how to do that?

And how to have a 5.1 system playing?


Thanks!

---

### Post by BicyclerBoy on 2012-02-11
5.1 output over iec958 is not just streamed audio, it is a digital data stream.

The 5.1 output (AC3/DTS) is matrix encoded data & must be output as such from the **player** application.

You can not use the internal mixer/volume control (no sharing & set volume to unmute/max)

It is possible to get pulse/alsa to encode all audio to AC3-5.1 but this is not easy or recommended.

Start mplayer or VLC with iec958 output
vlc -aout alsa -alsa-device iec958

then play a real AC3 soundtrack from BD or DVD.
VLC can encode multi-channel AAC etc into AC3 5.1 for digital pass-thru.
Remember the application player has to setup pulse (recent) or alsa to allow digital pass-thru'.

---

### Post by HUN73R on 2012-02-12
Hi, thanks for you reply, however it did not work. Vlc also plays 2.1.

Is there a way to make rhythmbox output 5.1?

---

### Post by BicyclerBoy on 2012-02-12
I'm not sure about rhythmbox..I doubt it is capable of AC3/DTS/HDA or even multi-channel audio.
I use Clementine because it can be configured to use a specific audio plug & plays 192KHz/24bit.
The very latest pulse audio is capable of AC3/DTS pass-through finally..

Are you sure you picked the 5.1 audio sound track ?
VLC seems to pick the wrong audio track & 2 ch audio device..

There are AC3 5.1 audio test-tracks free on the web..

---

### Post by HUN73R on 2012-02-13
Hey,
I'll give Clementine a try. Just installed it. Now, how to update pulseaudio?? It doesn't appear to be update on update manager.

---

### Post by BicyclerBoy on 2012-02-13
You would have to build pulse-audio from source or find a ppa with recent builds for your *buntu version.
I can't suggest any without research..
But pulse audio is not stopping S/PDIF AC3/DTS 5.1 from working..& it never did.

I would get Clementine from one of the devs ppa (davidsansome).

You should not get 2.1 sound from your HT amp with 2 ch audio unless it is mixing.

Post your:
aplay -l
aplay -L

There is a free AC3 test track on [www.lynnemusic](www.lynnemusic), clementine will not play it.
MythTV & vlc play it okay.

---

### Post by HUN73R on 2012-02-16
Hi,
I couldn´t try your suggestions yet.
As soon as I reach my computer I´ll let you know the output of those commands.

Anyway, when I play any song on Windows, all speakers output something and I think that´s what you mean by "mixing", right?

That would be good if I could have that behavior on Linux also. Besides having it outputting true 5.1, I want it to propagate any sound to all speakers.


Thanks!

---

### Post by HUN73R on 2012-07-15
Hey, it's been so long, but hopefully you can still help me with this question, which is not solved yet =\

Following the output of aplay -l and aplay -L:

```
mauro@mauro:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC275 Analog [ALC275 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC275 Digital [ALC275 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
mauro@mauro:~$ aplay -L
default
    Playback/recording through the PulseAudio sound server
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=Intel,DEV=0
    HDA Intel, ALC275 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC275 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC275 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC275 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC275 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC275 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, ALC275 Digital
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=Intel,DEV=0
    HDA Intel, ALC275 Analog
    Direct sample mixing device
dmix:CARD=Intel,DEV=1
    HDA Intel, ALC275 Digital
    Direct sample mixing device
dsnoop:CARD=Intel,DEV=0
    HDA Intel, ALC275 Analog
    Direct sample snooping device
dsnoop:CARD=Intel,DEV=1
    HDA Intel, ALC275 Digital
    Direct sample snooping device
hw:CARD=Intel,DEV=0
    HDA Intel, ALC275 Analog
    Direct hardware device without any conversions
hw:CARD=Intel,DEV=1
    HDA Intel, ALC275 Digital
    Direct hardware device without any conversions
plughw:CARD=Intel,DEV=0
    HDA Intel, ALC275 Analog
    Hardware device with all software conversions
plughw:CARD=Intel,DEV=1
    HDA Intel, ALC275 Digital
    Hardware device with all software conversions
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, HDMI 0
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=1
    HDA NVidia, HDMI 0
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=2
    HDA NVidia, HDMI 0
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    HDMI Audio Output
dmix:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct sample mixing device
dmix:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 0
    Direct sample mixing device
dmix:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 0
    Direct sample mixing device
dmix:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 0
    Direct sample mixing device
dsnoop:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 0
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 0
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 0
    Direct sample snooping device
hw:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
plughw:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 0
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 0
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 0
    Hardware device with all software conversions
```

---

### Post by HUN73R on 2012-07-15
Ok, don't know how, vlc now plays 5.1 with a true 5.1 DVD inserted, however, I'd like to have such behavior for songs that are not 5.1 (most of my mp3 files).
Also I noticed that if I use vlc to play a 2 ch file, when I switch back to a 5.1, it doesn't play as such, and then I have to open the sound preferences, choose an invalid option, save, open it again, select my output device and then it'll be able to play 5.1 back again.

---

### Post by HUN73R on 2013-01-14
Hey,

7 months later, I'm back together with that problem, which persists.

Just updated to Ubuntu 12.10 x86_64.

That would be great if anyone could say something.. any input is welcome.

In addition, this is what I get from lspci -v | grep Audio:

```
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
01:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)

```

Also, I set on /etc/pulse/daemon.conf:
```
enable-lfe-remixing = yes
``` 
and
```
default-sample-channels = 6
```

Anyone?
Thanks!!

---

### Post by BicyclerBoy on 2013-01-14
iec958 (S/PDIF) can only output stereo PCM or encoded (AC3/DTS) bitstream.
Would be better off with HDMI HT amp.

iec958 output:
If you want to change volume on AC3/DTS  &/or upmix 2.0 to 5.1 then this dmix output must be encoded into AC3.
This a52 encoder is not foss or licence free.

VLC can do this internally.
MythTV can do this internally.
The normal method of AC3/DTS playback is pass-thru over iec958. (Both above apps do this as well)

There is an alsa plugin (might be a pulseaudio plugin) that encodes 5.1 PCM to AC3 bitstream  out over iec958.

This arrangement could mean you decode AC3:2.0 or 5.1 (play) & then send to alsa a52 plug & it encodes to AC3:5.1 to output..
I think MythTV is smart enough not to do this as along as software volume control is turned off.

The /etc/pulse/daemon.conf options you have only effect discrete PCM audio. These can be output as analogue 5.1 or HDMI PCM 5.1 or iec958 AC3.

---

