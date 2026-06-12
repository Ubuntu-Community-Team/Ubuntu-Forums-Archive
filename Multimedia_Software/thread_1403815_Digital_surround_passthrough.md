---
title: "Digital surround passthrough"
date: 2010-02-10
forum: Multimedia Software
---

### Post by golovan on 2010-02-10
I can't seem to get my Karmic box to speak digital with my surround receiver. Sound Preferences doesn't give me a digital surround option. Been searching these forums +Google, and found that I can use Analog Stereo Duplex, but no luck. I have managed to get a digital PCM 96khz signal to my receiver, but it only outputs in stereo.

Is it impossible to have Dolby Digital passthrough to my receiver with Karmic? XBMC without surround is kind of a drag.

I'm using an optical cable, and my soundcard is Creative SB XFi PCI.

---

### Post by golovan on 2010-02-12
Is there really no one that has got optical surround to work?
Can it be done?

aplay -l gives: 
```
**** List of PLAYBACK Hardware Devices ****
card 0: XFi [Creative X-Fi], device 0: ctxfi [Front/WaveIn]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: XFi [Creative X-Fi], device 1: ctxfi [Surround]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: XFi [Creative X-Fi], device 2: ctxfi [Center/LFE]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: XFi [Creative X-Fi], device 3: ctxfi [Side]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: XFi [Creative X-Fi], device 4: ctxfi [IEC958 Non-audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by golovan on 2010-02-12
*nothing to see here* sorry

---

### Post by makaveli789 on 2010-02-12
> **golovan said:**
> Is there really no one that has got optical surround to work?
Can it be done?
I had a thread on here not too long ago. Here is the result of my efforts in searching around for a solution. I have not had time to actually try it myself so can't confirm, but the OP I got the info from seems to think it works. So give it a try if you have time and post back your results here.
[COLOR=Blue][B]
[http://ubuntuforums.org/showthread.php?t=1334258](http://ubuntuforums.org/showthread.php?t=1334258)[/B][/COLOR] 
[quote]
[Just found this post on another forum by ]("http://www.silicondust.com/forum/viewtopic.php?t=7876&sid=093a13bb3ad8260a49d82aa19f5fc401")**[WattoDaToydarian]("http://www.silicondust.com/forum/viewtopic.php?t=7876&sid=093a13bb3ad8260a49d82aa19f5fc401")**. I will try this whenI get a bit of time to play around with Ubuntu at home.

> **WattoDaToydarian]
I recently installed Ubuntu 9.10 on my PC and found that the included PulseAudio version blocks SPDIF passthrough for media players including VLC. 
However it includes a program called pasuspender which you can use to run media players to bypass PulseAudio for direct access to the SPDIF port. 
 
I had some time today and decided to see if I could hack the source to the hdhomerun gui to include pasuspender when launching VLC. An hour or so later I finally got it to work so I decided to share it with everyone. 
 
First you need to download and extract both source code tarballs from [here]("http://www.silicondust.com/downloads/linux") (do "tar xzf *" in the download location.) Next open "hdhomerun_config_gui/src/Viewer.cpp" in a text editor. Then scroll to line #161 and replace it with this: 
```
execlp("/usr/bin/pasuspender", ExeName.c_str(), ExeName.c_str(), "udp://@127.0.0.1:5000", (char *) NULL) said:**
> 


---

### Post by golovan on 2010-02-13
Tnx for the reply! I looked into it, but isn't this for  something called HDHomerun? 

I need spdif to work for xbmc/vlc and this fix doesn't help unfortunately:( It looks like it only throws in pasuspender. But tnx anyway:) 

Anyone else that have 2cents/a solution for me? I really would like this to work.

---

### Post by makaveli789 on 2010-02-13
Apologies. I didn't read the entire post. Hope you find a solution.

---

### Post by chronos00 on 2011-04-29
I have the same problem!
Did you manage to get it working?

I found [this bug report]("https://bugs.launchpad.net/ubuntu/+source/pavucontrol/+bug/519374?comments=all"), explaining this issue. We should all click in "this bug also affects me"!

Any insight on a work-around is greatly appreciated!

---

### Post by mc4man on 2011-04-29
Well I use 5.1 digital output pulseaudio here (see screen), though not 100% sure I get what happens to stereo tracks when using players w/ pulse
(So I usually play 'normal' stuff thru audacious or mplayer which can bypass pulseaudio

Not sure if this works with all cards (audigy 2 ZS here) or how easy to 'undo'
(have only done on maverick and natty, not lucid (never used lucid much

Method is shown here but if inclined read my comments in post 18 first.
[http://ubuntuforums.org/showthread.php?t=1608804](http://ubuntuforums.org/showthread.php?t=1608804)

---

### Post by golovan on 2011-05-04
> **chronos00 said:**
> I have the same problem!
Did you manage to get it working?

I found [this bug report]("https://bugs.launchpad.net/ubuntu/+source/pavucontrol/+bug/519374?comments=all"), explaining this issue. We should all click in "this bug also affects me"!

Any insight on a work-around is greatly appreciated!

Nope doesn't work yet. Clicked on "also affects me"

---

### Post by BicyclerBoy on 2011-05-04
AFAIK
Digital pass thru (AC3, DTS) is/was not possible with pulse device but it has been stated it will some day..
(does not work with 10.04)

vlc --aout alsa --alsa-audio-device iec958

You can configure vlc to do by default as well..

It is possible to use alsa to encode to AC3 5.1 but it is a bit unreliable/flaky

XBMC must have an audio configuration that overrides the desktop settings (MythTV does this.)

---

