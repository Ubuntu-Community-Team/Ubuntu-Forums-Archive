---
title: "SPDIF choppy at higher datarates"
date: 2016-08-28
forum: Mythbuntu
---

### Post by craiggraham on 2016-08-28
I've a frontend system with a C-Media USB audio dongle driving an amp via SPDIF. Previously, on an ancient install of Linux and Myth, direct digital passthrough worked fine. Now, after installing a recent Mythbuntu, some files that used to play OK have frequent gaps in the audio making them unwatchable. The amp shows it's continually locking and unlocking to the streaming data. The sound, when playing, is correct- data's being lost, not delayed. No hardware was changed during the upgrade. I don't know specifically *what* the audio dongle is, it just identifies in lsusb as a "C-Media Electronics Inc Audio Adapter" and the dongle itself is covered in glue- past history :)

Looking at the files, the ones that don't play correctly are encoded AC3, 48kHz, 640Kb/s and the files that do play are the same aside from having a 384Kb/s datarate. 

I've installed SMPlayer and reproduced the problem in there, showing it's a system software issue, not a specific Myth issue. Changing audio settings inside Myth (including ticking the HBR Passthrough Support tickbox) doesn't help- the best I can do is to drop it to software decoded stereo, which isn't what I want on a 5.1 system.

On the offchance, I set the CPU governer to "performance" though since there's no issue with playback of the video I didn't expect it to make any difference. It didn't.

The system's 4.4.0-34 generic #53 Ubuntu SMP. Anyone know where I can go from here?

---

### Post by uteck on 2016-09-04
I found a page about setting the .asoundrc file, might be a place to look;
[https://wiki.gentoo.org/wiki/ALSA#S.2FPDIF_or_HDMI_.asoundrc](https://wiki.gentoo.org/wiki/ALSA#S.2FPDIF_or_HDMI_.asoundrc)

---

