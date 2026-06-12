---
title: "No sound with integrated Intel 82801G sound card"
date: 2009-01-07
forum: Multimedia Software
---

### Post by skueppers on 2009-01-07
I'm a new Ubuntu user, so please bear with me.

I am unable to get sound working on my Ubuntu 8.10 installation on a Dell XPS 400 PC.  It has an Intel 82801G integrated sound card, using the SigmaTel STAC9221 codec. 

The internal speaker works, in that I get keyboard beeps and the like if I have the "PCM" volume slider turned on in Volume Control.

My sound card is recognized by lspci and aplay, and ALSA has loaded the correct module.  I have verified that all of the sliders in Volume Control are turned up.  I ran the alsamixer application from the command line, but only got one slider -- the Card and Chip are both labelled as "PulseAudio" and the slider is labelled "Master".  I have tried tinkering with different "model=" options for the snd-hda-intel module in the /etc/modprobe/alsa-base file.  I have verified that I have permission to use Audio devices. 

I ran the ALSA information script, the output of which is located at:

[http://www.alsa-project.org/db/?f=e368b49caabdd67df0ebd7f5836ceb6b9379e2aa](http://www.alsa-project.org/db/?f=e368b49caabdd67df0ebd7f5836ceb6b9379e2aa)

I am wondering whether it is significant that the PulseAudio sound server is listed as not running in the output from this script, but I have no idea what to do about it if it is a problem. 

Any thoughts on how I should proceed from here would be most welcome!

Oh, I should also note that audio doesn't work from the Live CD for 8.10 or 8.04 for me either.  Those are the only versions of Ubuntu I have used.

---

### Post by skern03 on 2009-01-07
At the top of the forum in which you posted this is a sticky post, Comprehensive Sound Problem Solutions Guide:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

Try the solutions there. It installs PulseAudio, which fixed similar sound issues with my system. It also has trouble-shooting tips.

---

### Post by skueppers on 2009-01-07
Is there a specific item in that sticky that you think would be particularly relevant?

I have read the sticky many times, and tried many of its suggestions.  I have not tried removing the packages and reinstalling them, as that did not seem relevant to my situation (sound has never worked, does not work with LiveCD).  I also have not tried compiling newer versions of the ALSA drivers myself, as that also didn't seem relevant.

---

### Post by skern03 on 2009-01-07
> **skueppers said:**
> Is there a specific item in that sticky that you think would be particularly relevant?

I have read the sticky many times, and tried many of its suggestions.  I have not tried removing the packages and reinstalling them, as that did not seem relevant to my situation (sound has never worked, does not work with LiveCD).  I also have not tried compiling newer versions of the ALSA drivers myself, as that also didn't seem relevant.

Someone else posted issues with recent HDA cards (also an Intel, I forget the card number). The Alsa Driver site hasn't caught up, from what I saw.

When you launch the PulseAudio Device Chooser (Applications, Sound & video, PulseAudio Device Chooser), you should get an icon in the top menu bar. When you click it, and choose Volume Control, you should get a multi-tabbed window. The Playback tab is empty unless a source is playing, which threw me for a loop. I played an MP3 through Amarok, then opened Volume Control. The slider was set to 0 for playback. Once I cranked it up, it worked for other sources, including SMPlayer. See attached image.

If this doesn't help, then try searching the forum or even the web itself on Intel HDA. You can also search Launchpad to see if it's a bug.
[https://launchpad.net/](https://launchpad.net/)

---

### Post by skueppers on 2009-01-07
Thanks for trying to help me out!

I installed the PulseAudio device chooser and modified the settings as you suggested, but it did not improve my situation.  

I have already tried searching the web, I will try looking in Launchpad to see if there are any relevant bugs.

---

### Post by hugoheden on 2009-02-01
Take a look at [http://ubuntuforums.org/showthread.php?t=1043568&](http://ubuntuforums.org/showthread.php?t=1043568&)

I have a similar setup I think, and finally managed to get sound out of my speakers, see comment #2.

---

