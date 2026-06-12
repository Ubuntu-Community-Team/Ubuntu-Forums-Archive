---
title: "/dev/mixer or /dev/dsp - signal from PulseAudio mixer"
date: 2013-09-26
forum: Multimedia Software
---

### Post by aso824 on 2013-09-26
Hi,
I want use "gpsk31" - specialised software for amateur radio. In a nutshell, I want audio signal from default PulseAudio mixer in this program.
Unfortunately, it's written to use OSS (default device is */dev/dsp*). Of course, Ubuntu has default pulse, so /dev/dsp doesn't exist.
I know about padsp, but it didn't work. When I'm run:
```
padsp gpsk31
```
Audio signal is empty (in gpsk31 settings I have /dev/dsp). The sound I'm looking for is from Google Chrome, but in future - it's from line-in / microphone.

My hardware configuration is integral sound card - I'm not using it - and Audigy 2 ZS (without any problems in system, works from install). Any solutions?
Ubuntu version: 13.04

Thanks!

---

### Post by kostkon on 2013-09-26
You could try the following:
first of all, install the PulseAudio Volume Control utility (package name is pavucontrol);

then start recording in gpsk31 and open the pavucontrol and see if gpsk31 is listed in the Recording tab (that means gpsk31 works with padsp, because some OSS apps don't). If it does, then set the recording source for gpsk31 to the Monitor of your sound card and it will start recording every sound being played on your desktop, including Chrome. If you want to record from the input of your card, set the source accordingly. 

And actually Ubuntu, like any other modern Linux OS uses ALSA and PulseAudio instead of OSS.

If you realise that you can't make gpsk31 work with padsp, then I don't know what else to recommend, maybe run Ubuntu, or even better Ubuntu Studio, in a VM and install OSS to it (you don't want to mess your main installation), or any other distro that comes with OSS by default, if you can find one.

Hope that helps.

---

