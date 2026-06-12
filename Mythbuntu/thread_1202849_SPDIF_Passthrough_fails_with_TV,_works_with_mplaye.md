---
title: "SPDIF Passthrough fails with TV, works with mplayer"
date: 2009-07-02
forum: Mythbuntu
---

### Post by gungfujoe on 2009-07-02
I've got a number of mkv format video files on my HTPC that have AC3 audio, and I've got mplayer set up to pass the AC3 audio via S/PDIF to my receiver.  As it does with any other audio source, the receiver decodes it and sends it off to my speakers.

MythTV can't seem to manage this feat for live (or recorded) TV, though.  If I enable AC3 and DTS passthrough, live TV plays with kind of a "machine gun static" audio, which seems to be the sound of encoded audio being played as stereo PCM (which is indeed what the receiver says it's getting over the S/PDIF line).  I can only get audio with TV if I disable the passthrough, and let MythTV convert the audio to stereo before sending it over the cable, which is problematic on a number of fronts (aside from the fact that I want surround sound, the AC3 decoder produces really inconsistent volume.  Quiet on one channel, not so quiet on the next, all of them much quieter than native PCM stereo or native AC3 surround passed through to the receiver).

What is MythTV doing?  It seems to be somehow fooling my receiver into thinking that it's sending stereo PCM while sending unencoded AC3.  How do I get MythTV to **properly** send a raw AC3 track over S/PDIF?

---

### Post by epi 1:10,000 on 2009-07-02
you may have to play with your Audio Output Device and Passthrough Output Device settings in the frontend settings. 

It should have options like........  ALSA:*device* (where *device* is a valid ALSA device such as spdif; iec958; default; hw::0,0; plughw:0,0; etc)

[http://www.mythtv.org/wiki/User_Manual:Index](http://www.mythtv.org/wiki/User_Manual:Index) and then click on [Frontend Configuration]("http://www.mythtv.org/wiki/User_Manual:Detailed_configuration_Frontend") 


I can remember my settings but it may be differ from one audio chipset to another.

---

### Post by gungfujoe on 2009-07-02
> **epi 1:10,000 said:**
> you may have to play with your Audio Output Device and Passthrough Output Device settings in the frontend settings. I've done that.  Only two of the options work, ALSA:default, and one other, I forget which (ALSA:surround, or something like that).  Both behave in exactly the same manner - output normal stereo or mis-identify AC3 as stereo to the receiver.  The other options output nothing.

The page you linked to (the link is broken, but the way, it stuck a :grin in it) does suggest disabling internal volume control when using AC3 output, though it doesn't say anything about it causing problems.  I'll have to try that tomorrow.

---

### Post by epi 1:10,000 on 2009-07-02
with Realtek ACL888 audio hardware w/ iec958 turned on in alsamixer

I have mine set to 

Audio Output Device                   ALSA:spdif

Passthrough Output Device         ALSA:iec958: { AESO 0x02 }

Max Audio Channels                   Stereo

---

### Post by Das Hammer on 2009-07-02
I always got the machine gun static too until:

[LIST]
[*]I used Alsa:SPDIF
[*]Checked AC3/DTS passthrough
[*]Unchecked use internal mixer
[*]Went into alsaconf and upped the volume levels for Master, PCM, and IEC958. On some cards/chipsets some of the important volume controls are muted by default.[/LIST]

After that, the passthrough worked great. I chose the alsa:spdif because then the audio from the PVR-250 capture worked, but even since I've switched to a DVB card from the PVR card, the same setup still works.

Hopefully something here helps you.

---

### Post by gungfujoe on 2009-07-03
I ended out solving this problem by turning off the internal volume control.  The MythTV wiki says "You may also want to disable this if you are using AC3 output as volume control will be done by your surround amplifier or receiver."  It doesn't say anything about the internal volume control totally screwing AC3 passthrough up, but apparently it does, at least on my system.  It's periodically dropping out with errors when I change channels, but at least I've got both video and sound with TV now.  I'm getting closer to getting this thing to actually work. :)

---

