---
title: "No sound via HDMI outside of mythtv"
date: 2013-02-02
forum: Mythbuntu
---

### Post by AppleTech on 2013-02-02
Hi,

Just downloaded and installed the latest version of mythbuntu a few days ago and have it up and running on my new hardware (2.13GHz Atom with integrated Nvidia GT520 w/ HDMI).  I've got mythtv up and running with my capture card, so far so good.

mythtv audio out is set up thusly (and working):


```
ALSA:hdmi:CARD=NVidia,DEV=1
```

Now, I'd like to be able to open up YouTube or Hulu in Chromium, but I'm getting no audio.  I've tried the following:

1. Installed alsamixergui and made sure all channels are unmuted and full volume (strangely, I don't see any entries for HDMI).  No change after force reload of alsa or reboot.

2. I've entered the following into /etc/asound.conf (after verifying /proc/asound/card1/id = NVidia)

```
pcm.!default {
        type hw
        card 1
}
```

3. I've installed pulseaudio and pavucontrol and no luck there either.

4. Verified I'm using the "recommended" NVidia drivers.

To aid in troubleshooting:
```
root@mythtv:~# aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    PulseAudio Sound Server
sysdefault:CARD=Intel
    HDA Intel, ALC892 Analog
    Default Audio Device
front:CARD=Intel,DEV=0
    HDA Intel, ALC892 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC892 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC892 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC892 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC892 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC892 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, ALC892 Digital
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=Intel,DEV=0
    HDA Intel, ALC892 Analog
    Direct sample mixing device
dmix:CARD=Intel,DEV=1
    HDA Intel, ALC892 Digital
    Direct sample mixing device
dsnoop:CARD=Intel,DEV=0
    HDA Intel, ALC892 Analog
    Direct sample snooping device
dsnoop:CARD=Intel,DEV=1
    HDA Intel, ALC892 Digital
    Direct sample snooping device
hw:CARD=Intel,DEV=0
    HDA Intel, ALC892 Analog
    Direct hardware device without any conversions
hw:CARD=Intel,DEV=1
    HDA Intel, ALC892 Digital
    Direct hardware device without any conversions
plughw:CARD=Intel,DEV=0
    HDA Intel, ALC892 Analog
    Hardware device with all software conversions
plughw:CARD=Intel,DEV=1
    HDA Intel, ALC892 Digital
    Hardware device with all software conversions
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, HDMI 0
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=1
    HDA NVidia, HDMI 1
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=2
    HDA NVidia, HDMI 2
    HDMI Audio Output
dmix:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct sample mixing device
dmix:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 1
    Direct sample mixing device
dmix:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 2
    Direct sample mixing device
dsnoop:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 1
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 2
    Direct sample snooping device
hw:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 1
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 2
    Direct hardware device without any conversions
plughw:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 1
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 2
    Hardware device with all software conversions
```

Help me please... pulling my hair out!

---

### Post by dlwhite67 on 2013-02-02
I had the same scenario. Ubuntu uses the default sound hardware, rather than the HDMI link. There is no tool (that I could find) to modify this behavior. The solution can be found in this post:
[http://ubuntuforums.org/showthread.php?t=2107038&highlight=hdmi](http://ubuntuforums.org/showthread.php?t=2107038&highlight=hdmi)

Per the Asoundrc wiki I was able to find my card number by going to /proc/asound/cards

I was able to determine my device number by looking at the sound config in Mythbuntu.

So, my config is:
pcm.!default {
	type hw
	card 1
        device 9
}

ctl.!default {
	type hw           
	card 1
        device 9
}

I hope this saves you some head scratching!

Don't forget to restart the service, or log out and then back into your session for the change to take effect.

---

### Post by AppleTech on 2013-02-03
Thank you for the feedback... I ended up bulldozing and doing a fresh 12.04 LTS install and confirming audio output via pavucontrol, then loading mythtv on top.  Lots more small settings to tweak, so I wish I could have stayed with mythbuntu.

I'm curious though if the panel I found where I controlled the output hardware selection from was not visible in mythbuntu pavucontrol or if I just missed it.  May give it another go from a USB install when I have time - if possible, that would be a simple GUI way to set it up for newbs like me!

---

