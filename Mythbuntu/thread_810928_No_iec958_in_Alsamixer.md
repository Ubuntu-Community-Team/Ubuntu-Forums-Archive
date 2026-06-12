---
title: "No iec958 in Alsamixer?"
date: 2008-05-28
forum: Mythbuntu
---

### Post by dsbw on 2008-05-28
OK, I just upgraded my ALSA drivers which was necessary because the default ALSA drivers with Hardy don't recognize HDMI-Audio on this motherboard (K9NGM3) until version 1.14.

Found a great script to do it:

[http://www.stchman.com/alsa_update.html](http://www.stchman.com/alsa_update.html)

And now, when I do aplay -L, I get (for the first time), iec958 showing up:

iec958: CARD=NVidia,DEV=0
    HDA NVidia
    iec958 (S/PDIF) DIgital Audio Output

Yay! But I don't see anything on alsamixer. I was expecting something I could un-mute.

I've changed the sound-device from "default" to "0 Nvidia".

What else do I need to do?:guitar:

---

### Post by pssturges on 2008-05-28
Have you tried going to preferences and checking iec958?

Phil

---

### Post by dsbw on 2008-05-28
> **pssturges said:**
> Have you tried going to preferences and checking iec958?Phil

Preferences? Vas ist das?

Right now I'm outside of Myth and just trying to get some output through the speakers. If I use xfce4-mixer, I can choose default or the 0 Nvidia HDA.

But it is a myth install, so I don't think I *have* an Ubuntu  preferences dialog anywhere. Not in settings. Not anywhere in MythTV that I know of.

:confused:

---

### Post by pssturges on 2008-05-28
In xfce4-mixer, goto file->options. This should give a list of available mixer sliders. Make sure all the iec958 related ones are selected + External Amplifier. Also, at the bottom of the the mixer window, expand the show switches dialogue & check the settings there.

Hope that helps
Phil

---

### Post by dsbw on 2008-05-29
Thanks, Phil. I'm actually doing this on two machines at once, which is informative. One is the NVidia based K9NGM3 and the other is the ATI based GA-MA69GM-S2H.

> **pssturges said:**
> In xfce4-mixer, goto file->options. This should give a list of available mixer sliders.

On the ATI machine I have three options for Devices: 

#0: HDA ATI SB
#1: SAA1734
#2: HDA ATI HDMI

#0 offers a broad assortment of switches: Master, Headphone, PCM, Front, Front Mic, Front Mic Boost, Surround, Center, LFE, Side, Line, Mic, Mic Boost, IEC958, Capture.0, Capture.1, Capture.2, Input Source.0, Input Source.1, Input Source.2.

These are all followed by .0, except for the Capture and Input Sources that are followed by .0, .1 and .2 as shown.

#1 offers just Line.1, Line.2 and Video.0

#2 offers just IEC958.0

> **pssturges said:**
> Make sure all the iec958 related ones are selected + External Amplifier. Also, at the bottom of the the mixer window, expand the show switches dialogue & check the settings there.

The iec958 option(s) are checked. I have no external amplifier option. The unhidden switches are checked--actually I should try the headphones and see if that does anything.

I notice that xfce4-mixer is somewhat recalcitrant as far as actually taking options that I select. I did manage, at one point, to have #2 be the default, and only the IEC958 option appeared in the whole panel. That didn't seem right somehow but maybe I should try it again?

Meanwhile, on the NVidia based machine, the iec958 shows up in an "aplay -L" but nowhere else! Not in xfce4-mixer or alsamixer...Nothin'. 

Frustrating to be stumped on these two boxes in the same place....

---

