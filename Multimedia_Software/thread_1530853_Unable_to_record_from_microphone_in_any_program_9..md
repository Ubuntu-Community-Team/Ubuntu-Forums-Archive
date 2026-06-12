---
title: "Unable to record from microphone in any program 9.10"
date: 2010-07-14
forum: Multimedia Software
---

### Post by triften on 2010-07-14
I was running 9.04 and could, through some magical sequence of toggling options that I was unable to figure out, occasionally get recording from the mic to work in audacity. Ardour worked more reliably, but is kind of over-featured. Audacity is simpler and I know how to get things done. For a while, I was doing basic recording in Ardour, saving it to wav then editing in audacity.

Well, I noticed a howto on getting audacity working in 9.10... so I upgraded ("what could possibly go wrong?"). I still can't record audio in audacity and ardour is now ALSO unable to record audio. They start recording samples but nothing comes in but silence.

I've got audacity set to ALSA/default/default and when I click monitor, the stream appears in the pavucontrol app. I've moved it to the input device and that doesn't seem to affect the results at all. Everything looks like it should be working fine except there's some invisible mute button, or something. Under alsamixer's Capture section, Mic has a red "CAPTUR" with no bar to adjust.

---

### Post by triften on 2010-07-14
I've since tried upgrading to 10.04 and that didn't help either. I guess it's some issue with the emu10k1 module or something, because I've enabled the on-board sound and can record audio from the mic input there. The onboard sound is an Intel HDA (which I had disabled previously while trying to get duplex to work.)

---

### Post by lidex on 2010-07-17
The <M> key mutes/unmutes elements in alsamixer. 
So your problem boils down to a capture problem with your soundcard, correct?
With onboard disabled -> Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by triften on 2010-07-20
PC is a custom-built Intel box. (I've become a lazy geek and couldn't tell you the exact setup off the top of my head.) Intel branded MB (DG31PR), GeForce 8400, SB Live.

```
uname -a
Linux abaddon 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 07:54:58 UTC 2010 i686 GNU/Linux

```

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Live [SB Live! Platinum [CT4760P]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
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
card 0: Live [SB Live! Platinum [CT4760P]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Live [SB Live! Platinum [CT4760P]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```
dpkg -l | grep "alsa"
ii  alsa-base                                  1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-oss                                   1.0.17-3                                        ALSA wrapper for OSS applications
ii  alsa-source                                1.0.22.1+dfsg-0ubuntu3                          ALSA driver sources
ii  alsa-tools                                 1.0.22-0ubuntu1                                 Console based ALSA utilities for specific ha
ii  alsa-tools-gui                             1.0.22-0ubuntu1                                 GUI based ALSA utilities for specific hardwa
ii  alsa-utils                                 1.0.22-0ubuntu5                                 ALSA utilities
ii  alsaplayer-alsa                            0.99.80-5                                       PCM player designed for ALSA (ALSA output mo
ii  alsaplayer-common                          0.99.80-5                                       PCM player designed for ALSA (common files)
ii  alsaplayer-gtk                             0.99.80-5                                       PCM player designed for ALSA (GTK+ version)
ii  bluez-alsa                                 4.60-0ubuntu8                                   Bluetooth audio support
ii  gnome-alsamixer                            0.9.7~cvs.20060916.ds.1-2                       ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                         0.10.28-1                                       GStreamer plugin for ALSA
ii  libesd-alsa0                               0.2.41-6ubuntu1                                 Enlightened Sound Daemon (ALSA) - transition
ii  libpt-1.10.10-plugins-alsa                 1.10.10-3ubuntu1                                Portable Windows Library Audio Plugin for th
rc  libsdl1.2debian-alsa                       1.2.13-4ubuntu4                                 Simple DirectMedia Layer (with X11 and ALSA 
ii  libsox-fmt-alsa                            14.3.0-1.1build1                                SoX alsa format I/O library

```

(I was getting errors, so I tweaked the head command line a little.)
```
head -n 1 /proc/asound/card*/codec*/*
==> /proc/asound/card0/codec97#0/ac97#0-0 <==
0-0/0: SigmaTel STAC9721,23

==> /proc/asound/card0/codec97#0/ac97#0-0+regs <==
0:00 = 6940

```

Hmmm... That's weird. I may not know what I'm talking about, but shouldn't that be "emu10k1" or something?

Thanks,
Triften

---

### Post by lidex on 2010-07-21
How about this:
```
arecord -l
```

And you did this:
[http://forum.audacityteam.org/viewtopic.php?p=75044#p75044](http://forum.audacityteam.org/viewtopic.php?p=75044#p75044)

---

### Post by triften on 2010-07-22
BTW, thank you for providing your attention to this issue.

```
arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: Live [SB Live! Platinum [CT4760P]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Live [SB Live! Platinum [CT4760P]], device 1: emu10k1 mic [Mic Capture]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Live [SB Live! Platinum [CT4760P]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Yeah, I tried that (the audacity forum "fix") and there's no "the sound card device that you are using" option, so I tried both options ("SB LIVE! Emu10k1..." and "Monitor of..."). Neither worked.

-Triften

---

### Post by triften on 2010-07-22
Also, if I run audacity from the command line, I see
```
Expression 'stream->capture.pcm' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 3653

```
when it starts up.

Seems related, but I'm not sure hot to wisely follow up on it. (Google gives a few hits searching on that sentence but none of them seem too helpful.)

-Triften

---

### Post by lidex on 2010-07-22
For that I think your best source is the audacity forum. Seems to be a lot going on there.

---

### Post by triften on 2010-07-22
Agreed, but any help on the sound input in general? The regular sound recorder doesn't work either.

Thanks,
Triften

---

### Post by lidex on 2010-07-22
> **triften said:**
> Agreed, but any help on the sound input in general? The regular sound recorder doesn't work either.

Thanks,
Triften

Have a look here;
[http://ubuntuforums.org/showpost.php?p=3544343&postcount=5](http://ubuntuforums.org/showpost.php?p=3544343&postcount=5)

More here:
[http://www.google.com/search?q=SB+Live+mixer&sitesearch=ubuntuforums.org](http://www.google.com/search?q=SB+Live+mixer&sitesearch=ubuntuforums.org)

You may also want to set your defaults to alsa. From an Alt+F2 run dialog:
```
gstreamer-properties
```
Reference:
[http://ubuntuforums.org/showpost.php?p=4894533&postcount=2](http://ubuntuforums.org/showpost.php?p=4894533&postcount=2)

---

