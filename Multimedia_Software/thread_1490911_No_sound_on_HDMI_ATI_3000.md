---
title: "No sound on HDMI ATI 3000"
date: 2010-05-22
forum: Multimedia Software
---

### Post by EthanMN on 2010-05-22
Video is ok, but never any sound.
I went through and made sure the HDMI is selected as the audio device and I upgraded to the latest driver binary. 

HDMI sound works *without* the ATI proprietary driver installed, but the needed resolution is not available and the picture overlaps the edges on my 32" LCD.  At least I know it is not a hardware issue.

ALSA is loaded and selected as the sound manager, but the volume controls don't appear in the ALSA slider console.

I tested the cable and display on another computer. 

I am using a new Gigabyte GA-MA78LM-SH2, it is the integrated video.

Any suggestions?

---

### Post by EthanMN on 2010-05-23
After many hours of research and attempted fixes I'm getting the idea that the AMD 7xx chipsets and/or ATI 3xxx video cards are not fully supported. Since I can't return a pile of used hardware, this appears to leave only one choice... fork over for W7. It's to bad.

Everything else works beautifully, I just can't get by without HDMI sound in this case.

So I'm hoping beyond hope that someone knows of a reliable fix?

---

### Post by dino99 on 2010-05-23
first question: how is sound detected ? (system pref sound)

second: have you paprefs and gnome-alsamixer installed ?
third: how are gnome-alsamixer settings ?

fourth: what about errors into logs and xsession-errors ?

[http://ubuntuforums.org/showthread.php?t=1466111](http://ubuntuforums.org/showthread.php?t=1466111)

---

### Post by EthanMN on 2010-05-23
> **dino99 said:**
> first question: how is sound detected ? (system pref sound)

second: have you paprefs and gnome-alsamixer installed ?
third: how are gnome-alsamixer settings ?

fourth: what about errors into logs and xsession-errors ?

[http://ubuntuforums.org/showthread.php?t=1466111](http://ubuntuforums.org/showthread.php?t=1466111)


Sound Preferences list the Realtek HDMI as output, and Realtek analog chipset as input. This appears to be correctly seen and configured.

*I just loaded paprefs*.

Gnome alsamixer is installed and has 2 tabs, one is the Realtek analog sound and has sliders for all features. 

The second alsamixer tab is the HDMI, it is blank except for the IEC958 check box, which is checked.

I'm working on getting the logs..

Thing is the HDMI video and sound works *without* the ATI drivers installed. The only limitation for me are the video options. Also, my LCD TV is being seen as a projector in the Catalyst control panel, but my max resolution is available when the ATI driver is installed.

If there is a way to install the ATI video drivers (to get correct resolution) and keep Ubuntu dev ported HDMI sound drivers that would be dandy.

---

