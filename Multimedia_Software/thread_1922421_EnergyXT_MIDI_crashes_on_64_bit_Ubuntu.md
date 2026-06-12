---
title: "EnergyXT MIDI crashes on 64 bit Ubuntu"
date: 2012-02-08
forum: Multimedia Software
---

### Post by jemb on 2012-02-08
So I'm having a problem with EnergyXT and MIDI, it works perfectly on 32bit Ubuntu, but 64bit Ubuntu is a different story. I am using Ubuntu 11.10 64bit.

When I select  a MIDI input, such as my MIDI interface box which has a keyboard connected to it. As soon as I click the check box next to the MIDI interface the program window vanishes. When I run EnergyXT from terminal it produces this message:

 ALSA lib rawmidi_hw.c:100: (snd_rawmidi_hw_params) SNDRV_RAWMIDI_IOCTL_PARAMS failed: Invalid argument
energyXT: rawmidi.c:264: snd_rawmidi_open_conf: Assertion `err >= 0' failed.
Aborted

MIDI seems work fine with other programs. This just seems to be with EnergyXT on 64bit Ubuntu.

Any thoughts or solutions?

---

### Post by jinnan_tonnix on 2012-02-27
Same problem with me.

The problem is with the libaam.so file, which needs to be compiled for 64 bit. I followed a few guides on how to compile the 32 bit driver on a 64 bit system, but didn't have any success.

I found that the KXStudio group have created a new libaam.so with Jack support. The libaam.so handles sound I/O and MIDI traffic.

My plan was to use Jack to route the MIDI to EnergyXT.

I added their PPA and searched for 'energyxt'; their libaam.so file can be installed then copied to my EnergyXT install.

EnergyXT doesn't crash anymore, and sees the MIDI input through the Jack system, but I have had no luck at all getting any MIDI messages through Jack to EnergyXT.


Oh well.

EnergyXT is a great program, but have you tried the latest LMMS?
[http://lmms.sourceforge.net/home.php](http://lmms.sourceforge.net/home.php)

I found that the KXStudio group have done a splendid job packaging LMMS. The LMMS in Ubuntu's repository is completely smashed, with unresolved dependencies. Adding KXStudio's PPA gives you the latest version of LMMS, which works well. Moreover, KXStudio's version has Jack support for LMMS (out only), so this means you can sync different Jack-aware apps (e.g. LMMS for bass and rhythm, Ardour for live sounds like guitar and vox.) Just a thought....


LMMS comes with the fantastic ZynAddSubFX synth, one of the best synths available. It also comes with a built-in SoundFont player and sample player, so that pretty much covers every sort of instrument you can imagine.

---

