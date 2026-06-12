---
title: "Sound problem on Acer Aspire 8920"
date: 2009-10-11
forum: Multimedia Software
---

### Post by devix91 on 2009-10-11
I have seen several threads with similar problem to what i am having but i have yet to find a solution to my problem.

   After doing a clean install of ubuntu 9.04, everything worked great, except for the sound. I did some research and ended up removing ALSA and updating my OSS through a .deb package. Didnt help.
   On top of it all when i now go to system -> preferences -> sound. It doesnt load, it shows 'loading sound' at the bottom shelf, and then it disappears. So that is pretty much my situation.
   If it helps any i am posting the output i got from ossmix and ossinfo -v3

OSSMIX
```
Selected mixer 0/High Definition Audio 0x10ec0889
Known controls are:
mode <mix|mix|mix|mix|mix|input> (currently input)
mute ON|OFF (currently OFF)
mode <mix|mix|mix|mix|mix|input> (currently mix)
mute ON|OFF (currently OFF)
mode <mix|mix|mix|mix|mix|input> (currently mix)
- [<leftvol>:<rightvol>] (currently 29.9:29.9 dB)
mute ON|OFF (currently OFF)
mode <mix|mix|mix|mix|mix|input> (currently input)
- [<leftvol>:<rightvol>] (currently 29.9:29.9 dB)
mute ON|OFF (currently OFF)
select <fp-mic|fp-linein|mix|int-mic> (currently fp-mic)
- [<leftvol>:<rightvol>] (currently 37.9:37.9 dB)
fp-mic ON|OFF (currently OFF)
fp-linein ON|OFF (currently OFF)
int-speaker ON|OFF (currently OFF)
fp-headphone ON|OFF (currently OFF)
mix ON|OFF (currently ON)
- [<leftvol>:<rightvol>] (currently 37.9:37.9 dB)
fp-mic ON|OFF (currently OFF)
fp-linein ON|OFF (currently OFF)
int-speaker ON|OFF (currently OFF)
fp-headphone ON|OFF (currently OFF)
mix ON|OFF (currently OFF)
- [<leftvol>:<rightvol>] (currently 37.9:37.9 dB)
fp-mic [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)
fp-linein [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)
int-speaker [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)
fp-headphone [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)
mix <fp-mic|fp-linein> (currently fp-mic)
pcm-mute ON|OFF (currently OFF)
mix-mute ON|OFF (currently OFF)
mix [<leftvol>:<rightvol>] (currently 51.9:51.9 dB)
mix <pcm|mix> (currently pcm)
pcm-mute ON|OFF (currently OFF)
mix-mute ON|OFF (currently OFF)
mix [<leftvol>:<rightvol>] (currently 51.9:51.9 dB)
mix <pcm|mix> (currently pcm)
pcm-mute ON|OFF (currently OFF)
mix-mute ON|OFF (currently OFF)
mix [<leftvol>:<rightvol>] (currently 51.9:51.9 dB)
mix <pcm|mix> (currently pcm)
pcm-mute ON|OFF (currently OFF)
mix-mute ON|OFF (currently OFF)
mix [<leftvol>:<rightvol>] (currently 51.9:51.9 dB)
mix <pcm|mix> (currently pcm)
pcm-mute ON|OFF (currently OFF)
mix-mute ON|OFF (currently OFF)
mix [<leftvol>:<rightvol>] (currently 51.9:51.9 dB)
mix <pcm|mix> (currently pcm)

```

ossinfo -v3

```
Version info: OSS 4.2 (b 2000/200909092208) (0x00040100) TRIAL
Platform: Linux/i686 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:49:34 UTC 2009 (krystof-laptop)

Number of audio devices:	0
Number of audio engines:	0
Number of MIDI devices:		0
Number of mixer devices:	1


Device objects
 0: osscore0 OSS core services
 1: oss_hdaudio0 Intel HD Audio interrupts=2083 (2083)
    HD Audio controller Intel HD Audio
    Vendor ID    0x8086284b
    Subvendor ID 0x10250145
     Codec  0: Unknown (0x10ec0889/0x10250145)
     Codec  1: Unknown (0x11c11040)
 2: oss_usb0 USB audio core services

MIDI devices (/dev/midi*)

Mixer devices
 0: High Definition Audio 0x10ec088 (Mixer 0 of device object 1)
    Device file /dev/oss/oss_hdaudio0/mix0, Legacy device /dev/mixer0
    Priority: 10
    Caps: 
    Device handle: PCI01451025-0000:00:1b.0-mx01
    Device priority: 10


Audio devices

Nodes

```

I am always available on skype,msn or yahoo. Thanks for any help in advance ^___^
Krystof.

---

### Post by devix91 on 2009-10-13
bump?

---

