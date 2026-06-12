---
title: "Pulseaudio &amp; Wine, imperfect together"
date: 2009-04-18
forum: Multimedia Software
---

### Post by davidgurvich on 2009-04-18
There seems to be a problem with some programs run under wine when pulseaudio is installed.  The windows program crashes at semi-random intervals.  

There is no problem if sound is disabled in the windows program.  Everything runs smoothly.  There would be more of an issue if the program would not start at all, giving no chance of disabling sound.  I've run the same program on other systems without pulseaudio and there is no problem there with sound under wine.

The following options have failed: aoss, padsp, pasuspender.  The first is the alsa-oss wrapper, which failed as I cannot seem to halt pulseaudio properly.  The second, padsp, is a pulseaudio oss wrapper.  Looks like either wine's or pulseaudio's oss support is lacking.  The third, pasuspender, should stop pulseaudio but doesn't.

---

### Post by markbuntu on 2009-04-19
WHich ubuntu are you using?

---

### Post by davidgurvich on 2009-04-19
Jaunty with pulseaudio 0.9.15, though there is no difference between from 0.9.14 in terms of crashing.  I simply thought there may have been some change for the better.  For now, I believe any change needs to be done in wine.

---

### Post by markbuntu on 2009-04-20
Well yes, the wine devs are still plugging along. Hopefully they will have a working pulse plugin soon.

---

### Post by davidgurvich on 2009-04-21
For now I've removed pulseaudio + alsa and installed oss4 from 4front.  I'll post back if there is any change for the better.  Right now the sound is working with some differences.

---

### Post by davidgurvich on 2009-04-22
There is a problem with oss4 kernel 2.6.28 and the ubuntu startup scripts.  They cause the kernel to crash with oss4 failing to start.  In addition, there is a crackling noise which I don't know enough about ossmix to fix.  The kernel does not crash if oss4 is turned on after boot.

For now, I've remove oss4 and changed to just using alsa.  That should work with wine as alsa allows low level access to the hardware.

---

### Post by markbuntu on 2009-04-22
Are you launching the program with padsp or wine?

---

### Post by davidgurvich on 2009-04-23
The problem is identical with alsa alone, pulseaudio removed.

---

### Post by psyke83 on 2009-04-24
> **davidgurvich said:**
> The problem is identical with alsa alone, pulseaudio removed.

First you install OSSv4, then you remove PulseAudio? Ouch ;). I hope your system is in a consistent state after all those changes.

WINE's ALSA output plugin still doesn't co-operate very well with PulseAudio, unfortunately. The good news, however, is that the OSS output plugin works perfectly. See Appendix C of [this guide]("http://ubuntuforums.org/showthread.php?t=789578").

Although you say that you've tried OSS output with the padsp wrapper and suffered instability, it's possible that either a) your PulseAudio configuration has a problem, or b) your issue is not related to PulseAudio or audio at all.

Did you consider upgrading WINE to the latest upstream release?

---

### Post by Neva on 2011-01-18
I found a pulseaudio-capable wine here:

[http://www.webupd8.org/2010/05/install-wine-with-built-in-pulseaudio.html](http://www.webupd8.org/2010/05/install-wine-with-built-in-pulseaudio.html)

Since I'm using Ubuntu Lucid 10.04, I used the latter repository
sudo add-apt-repository ppa:c-korn/ppa

After that, went to Synaptic package manager and chose to install Wine  1.3 as opposed to Wine 1.2 that's offered from the Ubuntu repositories.  Ran winecfg and chose pulseaudio there.

---

