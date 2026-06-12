---
title: "SPDIF surround sound HELP!"
date: 2011-08-04
forum: Multimedia Software
---

### Post by TrenTech on 2011-08-04
Ok if I set my hardware profile to digital stereo duplex "iec958" in sound preferences, I can get 2 channel PCM sound throughout the whole system. However if I want to watch a movie in DTS or any other Digital multichannel format, I have to change it to analog stereo duplex. This is a inconvenience having to get up and switch profiles depending on what I'm watching at, as this is a HTPC setup. Is there any way to both digital and analog sound on one profile? I've been scratching my head over this for a while, help would be much appreciated.

---

### Post by BicyclerBoy on 2011-08-05
Because you are using iec958 (S/PDIF) for PCM stereo I assume your AVR can handle AC3 & DTS...

To play AC3 or DTS by decode in your AVR HT amp you need to use S/PDIF digital pass thru'.

Successful digital pass thru' is much more difficult than PCM stereo because the data stream must be exactly right.
Normally this means no audio sharing, no mixer & no volume control.
This can be worked around by using the alsa a52 plugin.

AFAIK pulse audio can not do digital pass thru' yet.

One likely cause of problems is not using the correct clock rate.
Digital pass thru' (matrix encoded 5.1 AC3 or DTS) only works at 48KHz. (AC3 5.1 16bit/48KHz/max 640Kbps)

---

### Post by TrenTech on 2011-08-07
> **BicyclerBoy said:**
> Because you are using iec958 (S/PDIF) for PCM stereo I assume your AVR can handle AC3 & DTS...

To play AC3 or DTS by decode in your AVR HT amp you need to use S/PDIF digital pass thru'.

Successful digital pass thru' is much more difficult than PCM stereo because the data stream must be exactly right.
Normally this means no audio sharing, no mixer & no volume control.
This can be worked around by using the alsa a52 plugin.

AFAIK pulse audio can not do digital pass thru' yet.

One likely cause of problems is not using the correct clock rate.
Digital pass thru' (matrix encoded 5.1 AC3 or DTS) only works at 48KHz. (AC3 5.1 16bit/48KHz/max 640Kbps)

Ok before I start messing around with anything, How do I makes sure I have to correct clock rate set?

---

### Post by TrenTech on 2011-08-07
OK I got bored so I went ahead and tried the a52 plug-in using these instructions:[https://help.ubuntu.com/community/DigitalAC-3Pulseaudio]("https://help.ubuntu.com/community/DigitalAC-3Pulseaudio")

Now PCM stereo gets decoded to Digital surround sound on the fly which is kind of nice, but not what I was going for. My receiver can do that. However the problem now is I can't get AC3 sounds to play at all. none of my true digital tracks work anymore, no matter what profile I have it set to. I assume I got ahead of myself here, Appears I need something for AC3 passthru that I'm not seeing. Not very good with this audio crap.

---

### Post by BicyclerBoy on 2011-08-07
On the contrary, you have done well, nothing broken...

The a52 alsa plugin is not a good solution for AC3 playback.
It should work if you point the player at surround5.1.
Or set your alsa default as surround5.1.
None of these are good solutions..

The other fly-in-the-ointment is that the channel order is wrong (10.04).
AC3 == SMPTE /= alsa /= ffmpeg-a52.

The a52 plugin is the only way to share the digital pass-thru' i.e. system sounds & apps.

What are you using to play AC3 ?

Digital pass-thru' does not share; MythTV, XBMC etc can be directly configured to do digital pass thru'. There is no system wide setting as such.
VLC has pass-thru' setting buried deep or cmd-line options.
mplayer needs cmd-line options.

You need to config the player to do pass-thru'

The "rate 48000" line was necessary with 8.04 or 9.10 ...but I do not use it with 10.04 (will check later).
Forcing the 48000 rate for everything causes a re-sampling of CD 44.1KHz.

So to clarify..
I have a52 & swap51 alsa plug device (just to expt)
My swap51 is a reordering alsa plug that uses a52.
I do not point pulseaudio at a52 or swap51 because it crashes (10.04)
I use MythTV with audio setup for digital pass-thru'.
Stereo 2 ch PCM stays 2 ch & AC3/DTS are passed-thru'

---

### Post by TrenTech on 2011-08-07
> **BicyclerBoy said:**
> On the contrary, you have done well, nothing broken...

The a52 alsa plugin is not a good solution for AC3 playback.
It should work if you point the player at surround5.1.
Or set your alsa default as surround5.1.
None of these are good solutions..

The other fly-in-the-ointment is that the channel order is wrong (10.04).
AC3 == SMPTE /= alsa /= ffmpeg-a52.

The a52 plugin is the only way to share the digital pass-thru' i.e. system sounds & apps.

What are you using to play AC3 ?

Digital pass-thru' does not share; MythTV, XBMC etc can be directly configured to do digital pass thru'. There is no system wide setting as such.
VLC has pass-thru' setting buried deep or cmd-line options.
mplayer needs cmd-line options.

You need to config the player to do pass-thru'

The "rate 48000" line was necessary with 8.04 or 9.10 ...but I do not use it with 10.04 (will check later).
Forcing the 48000 rate for everything causes a re-sampling of CD 44.1KHz.

So to clarify..
I have a52 & swap51 alsa plug device (just to expt)
My swap51 is a reordering alsa plug that uses a52.
I do not point pulseaudio at a52 or swap51 because it crashes (10.04)
I use MythTV with audio setup for digital pass-thru'.
Stereo 2 ch PCM stays 2 ch & AC3/DTS are passed-thru'


Im using XBMC on 10.10. Passthrough output device is set to iec958, the other choices are irrelevant ie: HDMI, etc. There is an option for custom passthrough device but I have no idea what I would put there. Further digging, if I set the audio output to analog I can get sound from all formats but this means, AC3 is being mixed down so I'm loosing the digital quality. Until I figure out what I'm missing I'm leaving it at that. What is the swap51 plugin for? Also you say that your stereo 2 ch PCM stays 2 ch. I have 6 ch system wide with PCM. Don't know, figured it might be a clue is to what I got going on here. Thanks for the help so far. Getting closer to what I'm looking for.

---

### Post by TrenTech on 2011-08-07
After reading This:[http://colin.guthr.ie/2010/12/bobby-digital-in-5-1-surround/]("http://colin.guthr.ie/2010/12/bobby-digital-in-5-1-surround/")

It states that some application such as XBMC consider a52 as analog. Does this mean that even though I have it set to analog I'm not degrading my sound?

---

### Post by BicyclerBoy on 2011-08-08
Decoding to 5.1 PCM and then re-encoding via a52 plugin is not a good idea.
I don't think the a52 plug-in works right anyway & it crashes/stutters after about 1 hr..the audio quality is questionable.

The a52 plugin is an internal virtual analogue input plug device that encodes & outputs AC3 5.1. I believe that normally you would modify the default surround5.1 to use a52 plugin.
 
You don't need a52 or my swap51 plugs..

I don't use XBMC but MythTV stops the pulseaudio server & it drives the h/w correctly.

The internet searches seem to blame pulse-audio for XBMC pass-thru' problems.

Can you try this in XBMC custom pass-thru' ?
HDA Nvidia hdmi
iec958:CARD=Nvidia,DEV=3         or similar

Try running XBMC from the command line so we see the error messages..

Can you post your 
aplay -L
output ?

---

### Post by TrenTech on 2011-08-08
> **BicyclerBoy said:**
> Decoding to 5.1 PCM and then re-encoding via a52 plugin is not a good idea.
I don't think the a52 plug-in works right anyway & it crashes/stutters after about 1 hr..the audio quality is questionable.

The a52 plugin is an internal virtual analogue input plug device that encodes & outputs AC3 5.1. I believe that normally you would modify the default surround5.1 to use a52 plugin.
 
You don't need a52 or my swap51 plugs..

I don't use XBMC but MythTV stops the pulseaudio server & it drives the h/w correctly.

The internet searches seem to blame pulse-audio for XBMC pass-thru' problems.

Can you try this in XBMC custom pass-thru' ?
HDA Nvidia hdmi
iec958:CARD=Nvidia,DEV=3         or similar

Try running XBMC from the command line so we see the error messages..

Can you post your 
aplay -L
output ?

aplay -L outputs: ```
terrence@Terrence-PC:~$ aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    Playback/recording through the PulseAudio sound server
default
front:CARD=SB,DEV=0
    HDA ATI SB, VT1708S Analog
    Front speakers
surround40:CARD=SB,DEV=0
    HDA ATI SB, VT1708S Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=SB,DEV=0
    HDA ATI SB, VT1708S Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=SB,DEV=0
    HDA ATI SB, VT1708S Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=SB,DEV=0
    HDA ATI SB, VT1708S Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=SB,DEV=0
    HDA ATI SB, VT1708S Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=SB,DEV=0
    HDA ATI SB, VT1708S Digital
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=SB,DEV=0
    HDA ATI SB, VT1708S Analog
    Direct sample mixing device
dmix:CARD=SB,DEV=1
    HDA ATI SB, VT1708S Digital
    Direct sample mixing device
dsnoop:CARD=SB,DEV=0
    HDA ATI SB, VT1708S Analog
    Direct sample snooping device
dsnoop:CARD=SB,DEV=1
    HDA ATI SB, VT1708S Digital
    Direct sample snooping device
hw:CARD=SB,DEV=0
    HDA ATI SB, VT1708S Analog
    Direct hardware device without any conversions
hw:CARD=SB,DEV=1
    HDA ATI SB, VT1708S Digital
    Direct hardware device without any conversions
plughw:CARD=SB,DEV=0
    HDA ATI SB, VT1708S Analog
    Hardware device with all software conversions
plughw:CARD=SB,DEV=1
    HDA ATI SB, VT1708S Digital
    Hardware device with all software conversions
a52:CARD=SB
    HDA ATI SB
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=1
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=2
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=3
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
dmix:CARD=NVidia,DEV=3
    HDA NVidia, NVIDIA HDMI
    Direct sample mixing device
dmix:CARD=NVidia,DEV=7
    HDA NVidia, NVIDIA HDMI
    Direct sample mixing device
dmix:CARD=NVidia,DEV=8
    HDA NVidia, NVIDIA HDMI
    Direct sample mixing device
dmix:CARD=NVidia,DEV=9
    HDA NVidia, NVIDIA HDMI
    Direct sample mixing device
dsnoop:CARD=NVidia,DEV=3
    HDA NVidia, NVIDIA HDMI
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=7
    HDA NVidia, NVIDIA HDMI
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=8
    HDA NVidia, NVIDIA HDMI
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=9
    HDA NVidia, NVIDIA HDMI
    Direct sample snooping device
hw:CARD=NVidia,DEV=3
    HDA NVidia, NVIDIA HDMI
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=7
    HDA NVidia, NVIDIA HDMI
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=8
    HDA NVidia, NVIDIA HDMI
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=9
    HDA NVidia, NVIDIA HDMI
    Direct hardware device without any conversions
plughw:CARD=NVidia,DEV=3
    HDA NVidia, NVIDIA HDMI
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=7
    HDA NVidia, NVIDIA HDMI
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=8
    HDA NVidia, NVIDIA HDMI
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=9
    HDA NVidia, NVIDIA HDMI
    Hardware device with all software conversions
a52:CARD=NVidia
    HDA NVidia

```

running XBMC from terminal outputs nothing expect a problem with SMB but thats unrelated and not setup at the moment

---

### Post by BicyclerBoy on 2011-08-08
Maybe I have your requirement all wrong...
Do you want digital pass-thru' over HDMI or over your onboard mobo soundcard via S/PDIF coaxial or toslink cable ?
speaker-test -c 2 -r 48000 -D iec958:CARD=SB,DEV=0
(output over mobo soundcard)

Should find the real output device that is connected to your HDMI device..
This name is the direct output alsa name alias

speaker-test -c 2 -r 48000 -D hw:CARD=NVidia,DEV=3
speaker-test -c 2 -r 48000 -D hw:CARD=NVidia,DEV=7
speaker-test -c 2 -r 48000 -D hw:CARD=NVidia,DEV=8
speaker-test -c 2 -r 48000 -D hw:CARD=NVidia,DEV=9

One of these should make pink noise on the HDMI receiver..

Because you have HDMI output partially working I guess your device-subdevice will be one of the first (2) listed.

---

### Post by TrenTech on 2011-08-09
I'm sorry I should have clarified this from the start. I'm using digital thru the onboard SPDIF over toslink. The HDMI I have turned off in the sound preferences. Actaully this brings up an earlier point. Before I made the recent changes, if I set HDMI as my default device, then set SPDIF in XBMC as my default device, I could get passthru to work just fine and have analog stereo working without switching profiles, but if I wanted to listen to music on a music player, system sounds etc, I had to switch the default back to SPDIF in system preferences. This was wierd. You are right about a52, Sometimes the sound quality can get pretty aweful. maybe if I backtrack, remove a52 and set everything back to what I originally had it you could help me with that?

---

### Post by kaefert66014235 on 2012-01-04
where you successful with your attempts of digital pass-thru of surround sound streams via your S/PDIF cable? I am searching for the same thing for my HTPC since I switched from an analog sound system to one with a big digital receiver in its center, and at the moment I can only output stereo sound with my ubuntu machine to that receiver. not really satisfying..

---

### Post by BicyclerBoy on 2012-01-04
kaefert
Understand that S/PDIF can only support stereo audio stream up to 96KHz (192K for some) & matrix encoded multi-channel (AC3/DTS) data stream at 48KHz. (640Kbitsps/1M5bitsps)

The multi-channel audio is a data stream, you can not (easily) mix/share (no volume controls).
The multi-channel stream must be initiated/supported from the player software.
The very latest Pulse audio may support...

HDMI audio connect is far superior if your AVR supports it..

---

