---
title: "&quot;Digital Stereo (IEC958) Output + Analog Stereo Input&quot;"
date: 2009-11-07
forum: Multimedia Software
---

### Post by skin1990 on 2009-11-07
Hi!

I'm trying to use my notebook to record my calls made with Ekiga (using a Voip user). I need to record what I hear by the headphones and what I tell by the microphone.

Ubuntu 9.10 allow me to select (in "audio preferences" -> "hardware") between:

-Spento (switched off)
-Analog Stereo Input
-Digital Stereo Duplex (IEC958 )
-Digital Stereo (IEC958 ) Output + Analog Stereo Input
-Analog Stereo Output
-Analog Stereo Duplex

If I choose "Analog Stereo Output" or "Analog Stereo Duplex" (the lasts), I'm able to hear the output audio by the headphones. But if I choose the others, the computer doesn't allow me to hear anything.
I thought that the solution was to select "-Digital Stereo (IEC958 ) Output + Analog Stereo Input" but I don't hear anything!

Is there somebody who can help me?

---

### Post by ajgreeny on 2009-11-07
You are not alone in this sound problem.  It took a while for me to be able to hear anything that was input through my microphone, though I could still record with audacity or sound recorder, and skype picked up the input as well.

Although your situation is a bit different, I suggest you use the terminal utility alsamixer.  This will open in a terminal and you can move from slider to slider and raise or lower the sliders with the cursor keys, and mute/unmute items with the "M" key.  Tab will move you through output/recording/all groups of sliders.

This, I think is one of the difficulties of pulseaudio.  There appears to be no way to change levels of input or output of anything until you have the applications open that are using the sound server.

---

### Post by presario_ubun2 on 2009-11-11
Hello, I'm just trying to get Digital Stereo Output (IEC958) + Analog Stereo Input to work...i can only get analog stereo...

Is there a difference anyway?

---

### Post by drexell0680 on 2009-12-08
I'm having issues with this as well.  In fact, my only option for my USB external sound (Turtle Beach Audio Advantage Micro) is Analog Stereo Output.  Is there a different hardware profile I need?

---

### Post by bxcrx on 2009-12-27
If you use the bootable CD does Sound Recorder pick up your voice from the Live9.10 CD?

If it does you may suffer from this problem

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/460351](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/460351)

FYI my analog mic worked just fine in 9.04

---

