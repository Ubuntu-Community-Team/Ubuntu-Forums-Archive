---
title: "setting default system audio device (and Boxee)"
date: 2011-04-23
forum: Mythbuntu
---

### Post by davidstoll on 2011-04-23
I'm running Mythbuntu 10.10 32bit and using HDMI to connect to my TV.  I can get audio working in MythTV and XBMC, but not fully in Boxee or the Mythbuntu system itself.

Can someone assist me in getting audio working in the OS itself?

In Boxee, the startup sound plays about 90% and then cuts out, and I can't get audio in any video or even navigation sounds.  So, I'm thinking if I had the default device setup in the system, I could just use "default" in Boxee...but if someone has any ideas for Boxee too, that would be great.

Thank you for any help you can provide.

---

### Post by nickrout on 2011-04-24
> **davidstoll said:**
> I'm running Mythbuntu 10.10 32bit and using HDMI to connect to my TV.  I can get audio working in MythTV and XBMC, but not fully in Boxee or the Mythbuntu system itself.

Can someone assist me in getting audio working in the OS itself?

In Boxee, the startup sound plays about 90% and then cuts out, and I can't get audio in any video or even navigation sounds.  So, I'm thinking if I had the default device setup in the system, I could just use "default" in Boxee...but if someone has any ideas for Boxee too, that would be great.

Thank you for any help you can provide.

Hi David,

please post the audio device myth is using (setup|general, about page 3) and the output of aplay -L and aplay -l

---

### Post by davidstoll on 2011-04-24
audio device in myth setup shows:
ALSA:hw:CARD=NVidia,DEV=3

[code]$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0[code]

[code]$ aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=NVidia
    HDA NVidia, ALC662 rev1 Analog
    Default Audio Device
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
dmix:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    Direct sample mixing device
dmix:CARD=NVidia,DEV=1
    HDA NVidia, ALC662 rev1 Digital
    Direct sample mixing device
dmix:CARD=NVidia,DEV=3
    HDA NVidia, NVIDIA HDMI
    Direct sample mixing device
dsnoop:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=1
    HDA NVidia, ALC662 rev1 Digital
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=3
    HDA NVidia, NVIDIA HDMI
    Direct sample snooping device
hw:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=1
    HDA NVidia, ALC662 rev1 Digital
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=3
    HDA NVidia, NVIDIA HDMI
    Direct hardware device without any conversions
plughw:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=1
    HDA NVidia, ALC662 rev1 Digital
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=3
    HDA NVidia, NVIDIA HDMI
    Hardware device with all software conversions[code]

> **nickrout said:**
> Hi David,

please post the audio device myth is using (setup|general, about page 3) and the output of aplay -L and aplay -l

---

### Post by azmyth on 2011-04-24
I'm using myth and boxee under 10.04 64 bit. I'm running pulseaudio (pa) for myth but pa doesn't work for boxee so I have a script that kills pa and uses alsa. Don't know if this is your situation.

---

### Post by nickrout on 2011-04-25
I think you need to set your default alsa device to be the hdmi connection.

/etc/asound.conf will need to look like this:

```
pcm.!default {
type plug
slave.pcm {
type hw
card 0
device 3
}
} 
```

---

### Post by davidstoll on 2011-04-27
Sorry I didn't respond sooner, but I didn't get a notification of the last post...once in a while that happens for some strange reason....

Anyway, that seems to have fixed it.  Now all my misc programs, web browsers and xbmc (with defaults) works perfectly.

Thank you very much.  I really appreciate that.
I should be able to replicate this for other machines with different configurations now.  Awesome!

Two quick questions.

1) Isn't there a place in the home dir where I can put this instead?  ~/.asound.conf or something like that?

2) Any ideas why Boxee still has issues...probably more of a boxee specific question, but it's worth a try I guess.. :)



> **nickrout said:**
> I think you need to set your default alsa device to be the hdmi connection.

/etc/asound.conf will need to look like this:

```
pcm.!default {
type plug
slave.pcm {
type hw
card 0
device 3
}
} 
```

---

### Post by nickrout on 2011-04-27
I think the per user file is ~/.asoundrc

But unless you want users having different sound setups, this will need to be replicated for each user, easier to make it system wide.

As far as boxee is concerned, try disabling pulse, per the other post above?

---

### Post by davidstoll on 2011-04-28
That's good advice.  This is a Mythbuntu machine, so it doesn't really have multiple users, it's only for TV.  My thought was that it's just easier to backup the home dir rather than trying to remember all the little files littered through out the system...that way I don't have to make changes to my backup script.

Thanks for the reminder though.  It's easy to forget that kind of stuff.


> **nickrout said:**
> I think the per user file is ~/.asoundrc

But unless you want users having different sound setups, this will need to be replicated for each user, easier to make it system wide.

As far as boxee is concerned, try disabling pulse, per the other post above?

---

### Post by davidstoll on 2011-04-28
One other interesting tidbit...

I do have a ~/.asoundrc

```
~$ cat .asoundrc
defaults.ctl.card 4
defaults.pcm.card 4
defaults.timer.card 4
```

Just an FYI.  I am going to try simply deleting it (and the /etc/asound.conf) and see what happens.  Then put the correct config in ~/.asoundrc

I thought that in general the file in ~/ takes precedence over the one in /etc ?  But maybe because there isn't useful info in the ~ location, it makes a last ditch effort to find something in /etc/ ?

This conflicting info might be what is causing problems with Boxee.  Although, Boxee has it's on asound.conf, although it is quite complicated and much more lengthy (/opt/boxee/system/asound.conf) on some systems.

David

---

### Post by mmaki on 2011-06-30
Thank you! Creating this file (/etc/asound.conf) gave me sound in xfce after I exited MythTV.

pcm.!default {
type plug
slave.pcm {
type hw
card 0
device 3
}
}

---

