---
title: "Recent Updates broke my sound - ION HDMI - Karmic and 10.10"
date: 2010-10-24
forum: Multimedia Software
---

### Post by xbmcoholic on 2010-10-24
Since the latest update for **Karmic**, sound has been broken on my Aspire Revo R6310.  It took a lot of effort and troubleshooting to get it working in the first place so I ran back to my bookmarked forum threads and ran through verification on alsa-mixer and the sound preferences along with many others to find no solution.  After hours I finally broke down and performed a clean install of the latest **10.10** release, hoping it would fix my problems... No luck.

I've hit just about every guide out there for ubuntu+ion based systems but still can't solve this.  

Here are some outputs that may be useful.  If any guru's out there may be able to help, I'd really appreciated it.

-My Sound Prefs->Hardware is set to
Internal Audio
1 Output / 1 Input
Digital Stereo (HDMI) Output + Analog Stereo Input


> 
aplay -l
card 0: NVidia [HDA NVidia], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

aplay -L
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Digital
    IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output


---

### Post by xbmcoholic on 2010-10-25
I'm not sure if this is a change in the 1.0.23 version of ALSA, but I have no /etc/asound.conf file.  Seems odd as Pulse seems to detect all the sound output options yet I get no sound.

---

### Post by xbmcoholic on 2010-10-25
Update: Just tested the headphone jack and audio seems to work when pulse is set to "Analog Stereo Output" but is broken for "Digital Stereo (HDMI) Output"

Note:  HDMI audio works fine when booted to Win7 x64 Home

---

### Post by lidex on 2010-10-25
> **xbmcoholic said:**
> I'm not sure if this is a change in the 1.0.23 version of ALSA, but I have no /etc/asound.conf file.  Seems odd as Pulse seems to detect all the sound output options yet I get no sound.
Most systems do not need it - its a file for custom configuration.
Have you seen these threads:
[http://ubuntuforums.org/showthread.php?t=1552250](http://ubuntuforums.org/showthread.php?t=1552250)
[http://ubuntuforums.org/showthread.php?t=1542401](http://ubuntuforums.org/showthread.php?t=1542401)

---

### Post by axept on 2010-10-26
> **xbmcoholic said:**
> Update: Just tested the headphone jack and audio seems to work when pulse is set to "Analog Stereo Output" but is broken for "Digital Stereo (HDMI) Output"

Note:  HDMI audio works fine when booted to Win7 x64 Home

Hey,

Have you tested this:

- Set the output to "Digital Stereo (HDMI) Output"
- In terminal, run "alsamixer"
- Go to the right to you find the "S/PDIF", hit "M" to mute it. If you have more then one of the S/PDIF's, mute them all.
- Hit "Esc" to exit, when back in terminal -> sudo alsactl store

This helped me for some reason :popcorn:

BTW, this was on a ASRock 330HT-BD ION, but anyway, worth a try..

---

### Post by xbmcoholic on 2010-10-26
> **axept said:**
> Hey,

Have you tested this:

- Set the output to "Digital Stereo (HDMI) Output"
- In terminal, run "alsamixer"
- Go to the right to you find the "S/PDIF", hit "M" to mute it. If you have more then one of the S/PDIF's, mute them all.
- Hit "Esc" to exit, when back in terminal -> sudo alsactl store

This helped me for some reason :popcorn:

BTW, this was on a ASRock 330HT-BD ION, but anyway, worth a try..

Very interesting axept, I couldn't get it to work but I noticed if I left alsamixer running, when i tried the sound tests in pulse's "Sound Preferences" as soon as I clicked the "Test" button for left or right, S/PDIF unmuted itself in alsamixer.  There's also an "S/PDIF D" next to the SPDIF in alsamixer and when I have it selected, the top shows Item: S/PDIF Default PCM [Off]

---

### Post by xbmcoholic on 2010-10-26
> **lidex said:**
> Most systems do not need it - its a file for custom configuration.
Have you seen these threads:
[http://ubuntuforums.org/showthread.php?t=1552250](http://ubuntuforums.org/showthread.php?t=1552250)
[http://ubuntuforums.org/showthread.php?t=1542401](http://ubuntuforums.org/showthread.php?t=1542401)

Thanks for the suggestion lidex but I'm already running the 2.6.35-22-generic kernel.

On a side note though, I think somewhere in Alsa's config it may have SPDIF configured as the default PCM device, but I cant seem to find where to change it...  The hardware device for my HDMI that always worked in the past was hw:0,3 but I just can't seem to get it to work now, even with aplay.

---

### Post by xbmcoholic on 2010-10-26
> **xbmcoholic said:**
> Very interesting axept, I couldn't get it to work but I noticed if I left alsamixer running, when i tried the sound tests in pulse's "Sound Preferences" as soon as I clicked the "Test" button for left or right, S/PDIF unmuted itself in alsamixer.  There's also an "S/PDIF D" next to the SPDIF in alsamixer and when I have it selected, the top shows Item: S/PDIF Default PCM [Off]

Mwahahahah!!!  Got it working!!!

So simple!

alsamixer -> S/PDIF 1 <- un-mute by hitting m

What a horrible description in alsamixer!!!

So for my alsamixer screen
Master=100
PCM=100<>100
Front=100<>100
Mic=MM 0<>0
Mic Boos=0<>0
S/PDIF=00
S/PDIF D=MM
S/PDIF 1=00

On my Acer Aspire Revo R3610 (330 ION)
:popcorn:

Now I just need to wait for them to release a maverick PPA for XBMC :)

---

### Post by lidex on 2010-10-26
> **xbmcoholic said:**
> Mwahahahah!!!  Got it working!!!

So simple!

alsamixer -> S/PDIF 1 <- un-mute by hitting m

What a horrible description in alsamixer!!!

So for my alsamixer screen
Master=100
PCM=100<>100
Front=100<>100
Mic=MM 0<>0
Mic Boos=0<>0
S/PDIF=00
S/PDIF D=MM
S/PDIF 1=00

On my Acer Aspire Revo R3610 (330 ION)
:popcorn:

Now I just need to wait for them to release a maverick PPA for XBMC :)

Whaaaaat? :(
All's well that ends well

---

