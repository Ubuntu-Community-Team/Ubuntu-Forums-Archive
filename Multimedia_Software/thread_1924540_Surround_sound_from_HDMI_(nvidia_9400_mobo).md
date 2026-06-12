---
title: "Surround sound from HDMI (nvidia 9400 mobo)"
date: 2012-02-12
forum: Multimedia Software
---

### Post by lindsayward on 2012-02-12
Hi, and thanks for watching :)
I have a ubuntu 11.10 (just upgraded from 10.10) system on a HTPC with a Lanparty JR GF9400-T2RS motherboard that (apparently) supports 5.1 over HDMI, and I'd like get/confirm surround working.
I have the HDMI hooked up to an LG LCD TV, then run optical out from the TV to an LG 5.1 home theatre. 
I'm actually not entirely sure how to test it to see if 5.1 is working. Perhaps someone could start by helping me with that. (Is there a multi-channel test audio file I could play?)
Most (all?) of the TV I record says "Digital Stereo" on the icons I see when I press Info twice in MythTV. I have one recording that says AC3 instead of MP2, but it's still stereo...

In the Sound preferences in ubuntu, I can set my card and choose Speaker Test - no matter what I select, I can only ever hear something in Front L/R - nothing comes out when I click on the other speakers (same for the command line version with speaker-test...).
Should I be able to hear something through the other speakers at this stage? 
I figure if I can't hear anything with the speaker tests, there's no point looking into MythTV options or something else, but I could be wrong.

I'm also not sure if my home theatre needs to be set to something specific. I can get sound out of the other speakers if I set it to some of the other VSM modes (e.g. Pro Logic II ones or Virtual), but these are not what I want AFAIK. I have it set on "Bypass" - is that right?

It's been a while since I set it up with PulseAudio, which I think was because I set VLC's output to play sound out of the analogue connection to a different set of speakers (music in the house).

I have edited the pulsaudio daemon.conf file to set the channels to 6, as it says at: [https://help.ubuntu.com/community/SurroundSound](https://help.ubuntu.com/community/SurroundSound)
With pavumeter running, when I run:
**speaker-test -Dplug:surround51 -c6 -l1 -twav**
I get nothing. When I run:
**speaker-test -c6 -l1 -twav**
I get sound from front L/R and I see the meter move for the others, but I can't hear anything.
I have checked alsamixer and nothing is muted that shouldn't be. I even disabled auto-mute mode, whatever that is.

Thanks in advance!

Below is the output from **aplay -L**
(Are there any other settings that would be useful to share?)
```
default
    Playback/recording through the PulseAudio sound server
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=NVidia,DEV=0
    HDA NVidia, ALC889A Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, ALC889A Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, ALC889A Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, ALC889A Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, ALC889A Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, ALC889A Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=NVidia,DEV=0
    HDA NVidia, ALC889A Digital
    IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, HDMI 0
    HDMI Audio Output
dmix:CARD=NVidia,DEV=0
    HDA NVidia, ALC889A Analog
    Direct sample mixing device
dmix:CARD=NVidia,DEV=1
    HDA NVidia, ALC889A Digital
    Direct sample mixing device
dmix:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct sample mixing device
dsnoop:CARD=NVidia,DEV=0
    HDA NVidia, ALC889A Analog
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=1
    HDA NVidia, ALC889A Digital
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct sample snooping device
hw:CARD=NVidia,DEV=0
    HDA NVidia, ALC889A Analog
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=1
    HDA NVidia, ALC889A Digital
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
plughw:CARD=NVidia,DEV=0
    HDA NVidia, ALC889A Analog
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=1
    HDA NVidia, ALC889A Digital
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Hardware device with all software conversions

```

---

### Post by BicyclerBoy on 2012-02-13
Your TV will not encode LPCM into AC3 5.1.
AFAIK Most TVs will not output AC3 pass-thru from their S/PDIF outputs when playing from HDMI input..

The only way you are likely to get AC3 5.1 from the TV is to send AC3 5.1 from the PC over HDMI/IEC958 or internal DVB tuner if TV channel has AC3 audio track (mandatory in US ATSC?).

You can not use aplay or speaker-test to directly test AC3/DTS playback.
The player app must configure the digital pass-thru'.

You can start VLC with
vlc -aout alsa -alsa-device iec958
& then play a DVD with AC3 5.1 (remember to pick the AC3/DTS audio track)
There are free AC3 test tracks on the web.

You could consider HDMI connection from HTPC to HT amp then TV.
Put the TV audio output on another amp input (for some other purpose).
Your DVI/HDMI output supports HDA audio formats (8 ch LPCM etc ) that can not be sent over S/PDIF.

---

### Post by lindsayward on 2012-02-14
Thanks heaps for your reply.
You said:
> The only way you are likely to get AC3 5.1 from the TV is to send AC3 5.1 from the PC over HDMI/IEC958 or internal DVB tuner if TV channel has AC3 audio track (mandatory in US ATSC?).
I'm not sure how I do this and test it. If the TV channel does have an AC3 audio track, is there anything else I need to do to set it up?
My amp is a lifestyle system sort of thing, so it doesn't have another HDMI input. 
Possibly I could send my S/PDIF (optical) from the HTPC to the amp instead of sending audio to the TV (or get a new, more flexible, amp).

I don't use VLC to that amp/speakers, but I'll give what you suggest a try to test it.

---

### Post by lindsayward on 2012-02-14
OK, so I swapped my optical cable to go to the amp directly from the HTPC, and set mythtv and then vlc to output to iec958 instead. Works! I can get test AC3 files to sound correctly through each of the 5 speakers. 

Is there any reason why in ubuntu's sound preference the only option for iec958 is stereo instead of surround?

I am trying to set vlc back to what it was on analogue output (different speakers) but it still outputs through the amp/digital as well... :(

Edit: I found a mute option for the simultaneous output through digital (didn't matter when I was using hdmi). This didn't work in the ubuntu main sound prefs but did work in the pulseaudio panel :)

---

### Post by lindsayward on 2012-02-14
Alright, so that worked for a while, then all of a sudden I got sound coming out of the digital S/PDIF as well (which I don't want). If I open the pulseaudio volume control (without needing to touch anything in there), it stops and we're back to 'normal'. 
This lasts for a while - in fact until the next song exactly, and then comes back. I could mute both outputs in the pulseaudio control, but then can't hear other things on the desktop, like youtube.

Hmm... tried the mute buttons again (back to as they were) and it's working even when I change songs. It's so hard to figure this out - it's not consistent.

No... that didn't work for long. If I close the youtube clip, the next song will come back into the digital speakers. If I load youtube again, it stops and I'm back to OK, but only for a while.

So, if it wasn't clear, what I want is:
ALL sound gets sent through the digital optical IEC958 output (to the amp in my lounge room) and
ONLY VLC output goes to the analog output.
ALWAYS :)

Any help would be super, thanks!

---

### Post by BicyclerBoy on 2012-02-15
Just to clarify..
AC3/DTS are matrix encoded multi-channel formats. These sent over S/PDIF is a digital data stream (pass-thru') is **not** raw audio data.
Stereo (2ch) over S/PDIF is a raw digital audio stream.

The OS sound driver can not interfere with pass-thru'; no volume control or mixing, only mute.
The sound driver is only directly involved with AC3/DTS if you install an alsa/pulse plugin real-time encoder.

Programs that output digital pass-thru' S/PDIF (HDMI or toslink/coaxial) can be pointed directly at the alsa device.
MythTV stops the pulse audio server if it is using an alsa device.

By default vlc uses the default gnome audio device..
The best pulse config/control is 'pavucontrol'; it can config/save audio for running applications.

So you should be able to (pavucontrol):
 turn off simultaneous output
- set desktop default to analogue stereo output (mobo analogue out)
- config MythTV to use iec958

If you only want vlc to use analogue stereo (mobo):
- set default to hdmi (pavucontrol)
- turn off simultaneous output (pavucontrol)
- invoke vlc -aout alsa -alsa-device hw:0,0
 or figure out the notation for device dmix:CARD=NVidia,DEV=0.

Your chipset audio config is a little different to 'normal' because your on-board audio codec is also the hdmi audio codec..
With a PCIe hdmi video card you get (2) 'soundcards' & (2) S/pDIF output options.
I'm not sure if you have (2) completely separate S/PDIF outputs (HDMI & optical/coax).

---

### Post by lindsayward on 2012-02-27
I thought I'd come back and update: I got a nice Yamaha RX-V671 amp, so I'm now connected via HDMI again, which is nice and easy.
Now I just wish they would broadcast movies on TV in surround sound...

---

