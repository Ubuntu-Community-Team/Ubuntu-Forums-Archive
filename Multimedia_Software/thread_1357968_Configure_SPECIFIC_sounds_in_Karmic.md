---
title: "Configure SPECIFIC sounds in Karmic?"
date: 2009-12-17
forum: Multimedia Software
---

### Post by r_avital on 2009-12-17
Hello,

I have two questions:

1. I am trying to figure out if there is a way to configure **specific **sounds for events like login/system ready, logout, etc., in Karmic.

uname -a returns:
**[FONT=Courier New]Linux [machine-name] 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009 i686 GNU/Linux[/FONT]**

aplay -l returns:
[B][FONT=Courier New]**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1                                                   
  Subdevice #0: subdevice #0                                        
card 0: NVidia [HDA NVidia], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1                                                     
  Subdevice #0: subdevice #0      [/FONT][/B]

I'm getting sounds ok.  My question is - in Jaunty, I am able to run System -> Preferences -> Sound, and in the "Sounds" tab, I get to either accept a default sound file or select a sound file (usually .ogg) for specific desktop events.

This is all gone in Karmic.   There is no "Sounds" tab.

Does anyone know - Is this yet one more oversight in the development of Karmic, or what we used to call a "Feature of Windows" - intentionally removing a capability for some reason?  (If the latter, then it will be one more disappointment for me in Karmic, and one more reason to stick with Jaunty till Lucid is released).

I believe I've seen this referred to as a bug by the developers, but I thought the good people on this forum might have better info, or a workaround - I'll be happy to backup/edit config files if anyone can point me in the right direction.

2. In Jaunty, even though I am able to configure specific .ogg files for the events shown under the "Sounds" tab (System -> Preferences -> Sound), the only time I actually get the sound is when I log in (I believe this is referred to by the developers as the System-Ready sound).  I get the short drumroll when GDM starts, and when Gnome starts after I log in successfully, I get the (default) System-Ready sound.  Any reason why I would not be getting any other sounds, like logout, empty-trash and so on?  Has anyone else experienced this?

Many thanks in advance.

---

### Post by r_avital on 2009-12-28
Bump.

If this is not the correct forum for this question, please direct me to the correct one.

Thanks, and Happy New Year :)

---

