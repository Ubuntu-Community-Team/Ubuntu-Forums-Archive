---
title: "NVidia ION - no digital audio, analogue audio volume low"
date: 2009-08-09
forum: Multimedia Software
---

### Post by 117 on 2009-08-09
Hi, I've just built myself a new machine using a Zotac IONITX-D-E motherboard which uses the NVidia ION chipset.  My problem is that I can't seem to get any sound from the digital audio outputs (co-ax, optical, HDMI), and the volume for the analogue audio seems really low (I have to turn my amp up real high to get a decent sound).

System > Preferences > Sound shows the following:

Autodetect
HDA NVidia NVidia HDMI (ALSA)
HDA NVidia ALC662 Digital (ALSA)
HDA NVidia ALC662 Analog (ALSA)
HDA NVidia ALC662 Analog (OSS)
HDA NVidia ALC662 Analog (OSS)
HDA NVidia ALC662 Analog (OSS)
ALSA
OSS
PulseAudio

If I choose Autodetect or ALSA I get audio through the analogue output (as mentioned, volume is very low), but none of the digital output options seem to work!

---

### Post by SugarLump on 2009-08-09
I have exactly the same problem with Zotac IONITX-A-E. I have tried everything during the weekend, but I still can't get sound out from optical output.

Ubuntu is 9.04 and Nvidia ION driver package is installed. ION drivers fixed screen resolution problems, but sound problem still exists.

---

### Post by l3iggs on 2009-08-09
use the AlsaUpgrade-1.0.x-rev-1.17 script [_here_]("http://ubuntuforums.org/showthread.php?p=6589810#post6589810") to update to the latest stable alsa (v1.0.20 as of this post)
then run
```
gnome-sound-properties
```
and change everything (except capture and mixer device) to 'HDA NVidia ALC662 rev1 Digital (ALSA)' 
then run
```
gnome-volume-control
```
from the dropdown menu at the top select 'HDA NVidia (Alsa mixer)' as your Device.
hit the preferences button at the bottom of the window. tick every box. go to the 'Switches' tab and make sure ALL boxes are checked.

I've got coax, optical and HDMI digital audio output working on my ZOTAC ION board.

---

### Post by 117 on 2009-08-10
that did the trick!  

thanks very much indeed :)

---

### Post by manderson96 on 2009-08-10
I also just built a Zotac ION 330 A, system. Where did you find the Nvidia Drivers that corrected your screen resolution issues. Are they part of the ubuntu build or did you have to reference a 3rd party repo?

---

### Post by 117 on 2009-08-10
> **117 said:**
> that did the trick!  

thanks very much indeed :)

hmmm, a bit strange, although it does indeed work for apps like Rhythmbox, Firefox is outputting the sound through the analogue still, any ideas?


edit: actually, ignore that, a reboot resolved that problem!

---

### Post by 117 on 2009-08-10
> **manderson96 said:**
> I also just built a Zotac ION 330 A, system. Where did you find the Nvidia Drivers that corrected your screen resolution issues. Are they part of the ubuntu build or did you have to reference a 3rd party repo?

I'm pretty sure I used the drivers direct from Nvidia here: [http://www.nvidia.co.uk/object/linux_display_ia32_185.18.31_uk.html](http://www.nvidia.co.uk/object/linux_display_ia32_185.18.31_uk.html)

---

### Post by SugarLump on 2009-08-10
Thanks! Alsa update did the trick, now optical output is working.

Nvidia drivers must be downloaded from Nvidia's website.

---

### Post by trevs.bronco on 2009-08-14
what driver version did you use? I just installed the most recent, 195.18 (i think) and it is very unstable. I only get analog audio when I loose my display, no digital at all. This is with the same motherboard running Mythbuntu 9.04

Trev

---

### Post by matthewbpt on 2009-08-14
> **trevs.bronco said:**
> what driver version did you use? I just installed the most recent, 195.18 (i think) and it is very unstable. I only get analog audio when I loose my display, no digital at all. This is with the same motherboard running Mythbuntu 9.04

Trev

195.18 is the current beta driver, not the stable one, install 185.31 that is the current stable driver

edit: in fact 195 is a leaked beta, 190 is the official beta, and 185 is the stable, you're really bleeding edge =P

---

### Post by trevs.bronco on 2009-08-14
I was wrong it is 185.18.31 i have installed. oh well... no sound for me. I have tried everything I can find to try  and I never get sound unless things go unstable and my screen goes blank. i am very close to giving up completely. no point having a HTPC without sound.

---

### Post by trevs.bronco on 2009-08-16
I finally heard sound for the first time today!

This was accomplished by reinstalling the 185.18.31 Nvidia driver as per [these]("http://ubuntuforums.org/showthread.php?t=1125400&highlight=install+proprietary+drivers") instructions, upgrading ALSA as previously mentioned and following [this]("http://www.mythtv.org/wiki?title=AllensDigitalAudioHowto") how to in the Myth wiki this is my good news.

My bad news is that I still don't have sound from myth and after a few minutes the video becomes unstable and the screen goes blank.

Suggestions anyone?

Trev

---

### Post by 117 on 2009-08-17
> **117 said:**
> hmmm, a bit strange, although it does indeed work for apps like Rhythmbox, Firefox is outputting the sound through the analogue still, any ideas?


edit: actually, ignore that, a reboot resolved that problem!

I'm still having intermittent problems with audio through Flash in Firefox (youtube, for instance), it only seems to work occasionally through the digital out, but always seems to work through analogue

---

### Post by canclan on 2009-11-05
Has this been decidedly resolved?  I am also looking to get a Zotac Ionitx-D-E to run LinuxMCE as a "Media Director" client and a separate "Core" PC.   I just do not want to drop ~$300 for something that will not work.

Also, does anyone know if it can it net boot (I think LinuxMCE supports PXE)?

---

