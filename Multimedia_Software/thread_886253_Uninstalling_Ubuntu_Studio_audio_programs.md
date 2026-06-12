---
title: "Uninstalling Ubuntu Studio audio programs"
date: 2008-08-11
forum: Multimedia Software
---

### Post by clegends on 2008-08-11
Hi Folks, just installed Ubuntu Studio, 8.04, and LOVE it! Needed a desktop system that was stable and once set up would just work... so easy. I'm not new to Linux, but haven't tried Ubuntu before. I decided on Ubuntu Studio, as I wanted a Linux already set up with graphics programs, and video editing capabilities. I also liked that the kernel was specifically compiled for this.

With a bit more research, it seems the kernel is specific for audio editing, something I don't do too much. 

First question, will the customized rt kernel for Ubuntu Studio also help with graphics programs? (i.e., gimp, video editing, etc.)

Second question, is there an easy way to uninstall the audio programs, then add only what I need?

For audio, all I currently need is Audacity, some decent music playing programs, and the plugins to be able to read a wide variety of audio formats when I install other programs... Synaptic package manager wasn't much help with uninstalling them together, so from the terminal I ran: sudo apt-get remove ubuntustudio-audio ubuntustudio-audio-plugins

sudo apt-get autoremove

All this did was remove a few kilobytes of the meta-packages... didn't remove any programs whatsoever... so short of uninstalling all 20 or so of them by hand, can anyone recomend something else for me to try?

I haven't used it widely, but so far Ubuntu is the stablest and most sensible Linux I've used. Cheers.

~Mitchell

---

### Post by logos34 on 2008-08-11
keep the -rt kernel even if you don't do audio editing/need involuntary preemptible kernel...it's fast

> sudo apt-get remove aconnectgui alsa-tools alsa-tools-gui audacious audacious-plugins-extra ardour beast bitscope creox denemo timemachine gtick hydrogen jackbeat jackd jackeq jack-rack jack-tools jamin jdelay lilypond lilypond-data meterbridge muse patchage qamix vkeybd qjackctl puredata rosegarden timidity seq24 shaketracker sooperlooper swami csound tapiir freqtweak mixxx terminatorx zynaddsubfx fluidsynth bristol freebirth qsynth tk707

> sudo apt-get remove aeolus blop caps cmt hexter fil-plugins ladspa-sdk mcp-plugins omins swh-plugins tap-plugins vcf dssi-example-plugins dssi-host-jack fluidsynth-dssi xsynth-dssi dssi-utils

[https://wiki.ubuntu.com/UbuntuStudio/PackageList](https://wiki.ubuntu.com/UbuntuStudio/PackageList)
[https://help.ubuntu.com/community/UbuntuStudio](https://help.ubuntu.com/community/UbuntuStudio)

---

### Post by clegends on 2008-08-11
Wow. That was quick, thanks so much/ Will let you know how I go.
~Mitchell

---

### Post by clegends on 2008-08-11
Ran the commands, and on the links page to the packages list for Ubuntu Studio reinstalled the video packages, as open movie editor had been ununstalled.... all worked beautifully. Thanks again, I've bookmarked those pages so I can find them again easily. Cheers.
~mitchell

---

