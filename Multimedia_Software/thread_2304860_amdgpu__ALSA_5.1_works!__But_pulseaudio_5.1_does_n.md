---
title: "amdgpu:  ALSA 5.1 works!  But pulseaudio 5.1 does not"
date: 2015-11-30
forum: Multimedia Software
---

### Post by bmlong137 on 2015-11-30
I recently upgraded from Ubuntu 15.04 to 15.10, which meant trying out Linux 4.2.x and the amdgpu module.  I found the following results:

_Linux 3.x w/ radeon & fglrx_
HDMI 2.0 - ALSA & pulseaudio work
Optical 2.0 - ALSA & pulseaudio work
HDMI 5.1 - None

_Linux 4.x w/ fglrx_
HDMI 2.0 - ALSA & pulseaudio work
Optical 2.0 - ALSA & pulseaudio work
HDMI 5.1 - None

_Linux 4.x w/ amdgpu_
HDMI 2.0 - ALSA & pulseaudio work
Optical 2.0 - ALSA & pulseaudio work
HDMI 5.1 - ALSA works

This is promising.  I got 5.1 working for the 1st time with an AMD chip.  However, pulseaudio refuses to work with it.  The drop down has 5.1 as an option, but only the front left/right speakers work when performing the "test" through the UI.  When piping 5.1 to pulseaudio configured for 5.1, I get no sound.  I would like to funnel mythfrontend through pulseaudio, but right now it is using ALSA directly for 5.1.

Thanks,
Brian

---

### Post by blm-ubunet on 2015-12-03
When you say "5.1" do you want 6 discrete channels of digital output ? or do you mean AC3-5.1 &/or DTS?

Depending on what is connected to the end of the hdmi cable, matrix encoded AC3/DTS/DTS-MA etc or discrete 8 ch audio is possible.

Pulse audio pass-thru AC3/DTS:
Install/run pavucontrol
- Configuration tab: set as digital stereo (not surround 5.1)
- Output tab: click advanced & then tick AC3 DTS etc.

---

### Post by bmlong137 on 2015-12-20
I already have it configured that way, which works for basic sound.  However, when using MythTV, I have to go direct to Alsa/HDMI to get 6 channels.  If I configure it for pulseaudio, it is not possible to get the 6 channels.  pavucontrol shows 5.1, but it simply doesn't work.  Not sure why, because it certainly works with alsa.

---

### Post by bmlong137 on 2015-12-20
Basically, pulseaudio only shows "hw:CARD=HDMI,DEV=3".  I want it to see "hdmi:CARD=HDMI,DEV=0".  The latter is the one that works with surround.

---

### Post by blm-ubunet on 2015-12-23
Like I said in post 2? Don't pick 5.1..
Selecting the 5.1 device in pulseaudio selects/output over discrete 6 channels which can be analogue (3 stereo jacks) or over HDMI.
Your HDMI attached device may not work with discrete multichannel only stereo mode bitstream pass thru AC3/DTS.

Pulse audio:
Has worked with AC3 pass thru bitstreaming for couple of years..
If you want to output AC3 5.1 or DTS 5.1 then select digital **stereo** as output configuration.
Then find the advanced hidden button/widget & tick the boxes for AC3 &DTS pass thru'..
MythTV:
Scan pick the pulseaudio digital stereo device & then tick the boxes to pass thru AC3/DTS etc.

---

