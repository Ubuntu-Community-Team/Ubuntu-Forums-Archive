---
title: "Firefox crashes when Flash is involved"
date: 2010-01-26
forum: Multimedia Software
---

### Post by Rhemat on 2010-01-26
I don't know what happened, but this happened in openSuSE 11.2 as well.  Now when I try to view any media that involves the flash plugin, FireFox crashes.  I've reinstalled the flash-plugin multiple times.  I've tried downgrading to FireFox 3, but 3.5 always remains.  I installed some software last night, but it didn't conflict with anything on my system.  Is there some form of bug with the new flash?  Is there a functionality time-bomb, that kills itself after a while?  I saw that someone else was having issues with flash freezing FireFox.
Here is some system info:
CPU - AMD Athlon 64 3200+ 2GHz
Video - ATi 2400HD chipset (MSI RX2400Pro)
Audio - Ensoniq PCI card
RAM - 2GB DDR1

Thanks in advance.

---

### Post by Rhemat on 2010-01-26
Okay, I ran firefox in terminal, and I grabbed the output.  Here is what it gave me.

(firefox:5075): GLib-WARNING **: g_set_prgname() called multiple times
LoadPlugin: failed to initialize shared library /home/haunter/.mozilla/firefox/x68kvmbb.default/extensions/quakeliveplugin@idsoftware.com/plugins/npquakelive.x64.so [/home/haunter/.mozilla/firefox/x68kvmbb.default/extensions/quakeliveplugin@idsoftware.com/plugins/npquakelive.x64.so: wrong ELF class: ELFCLASS64]
ALSA lib pulse.c:229:(pulse_connect) PulseAudio: Unable to connect: Timeout

ALSA lib pulse.c:229:(pulse_connect) PulseAudio: Unable to connect: Timeout

ALSA lib pulse.c:229:(pulse_connect) PulseAudio: Unable to connect: Timeout

ALSA lib pulse.c:229:(pulse_connect) PulseAudio: Unable to connect: Timeout

ALSA lib pulse.c:229:(pulse_connect) PulseAudio: Unable to connect: Timeout

Killed

I have to note, that I did not visit QuakeLive, but instead visited icanhascheezburger.com.  I tried playing one of their Viddler videos, and Firefox would recover for a moment, then freeze again.  I'm going to see if reinstalling PulseAudio will fix this, but why would PulseAudio have anything to do with this?
Thanks in advance.

---

### Post by Rhemat on 2010-01-26
Nope, upgrading PulseAudio did not fix the problem.

---

### Post by Rhemat on 2010-01-26
Well, as it turns out, PulseAudio is the culprit, and is killing other things as well.  I tried to play Doom II with PRBoom, and I saw this:

I_InitSound: ALSA lib pulse.c:229:(pulse_connect) PulseAudio: Unable to connect: Timeout

It hung at I_InitSound: for a while, then finally, spat out the whole string there.  Rhythmbox hangs when I try to play music.  Pretty much anything that involves sound, PulseAudio crashes.  Is there a reason PulseAudio was implemented into Ubuntu?
I'm going to uninstall PulseAudio, setup what Ubuntu used before, and hopefully, this will work.

---

### Post by jakslev on 2010-03-31
Hi Rhemat - did you get any further with this issue? I think it might be the same as my issue here: [http://ubuntuforums.org/showthread.php?t=1429511&highlight=firefox+hangs](http://ubuntuforums.org/showthread.php?t=1429511&highlight=firefox+hangs). 

Firefox greys out when I try and click on (what I believe) is javascripted pop-ups. One easy example is trying to click on a picture here: [http://www.beretta.com/Long-guns/Field-guns/Semi-automatic/AL-391-Light-White/index.aspx?m=82&f=2&id=1024](http://www.beretta.com/Long-guns/Field-guns/Semi-automatic/AL-391-Light-White/index.aspx?m=82&f=2&id=1024). 

However I am also having audio problems in SecondLife and that I have heard should be related to Alsa. 

I have reinstalled the computer from scratch and updated all + gotten the "play proprietary files" plugin. It is Ubuntu 9.10 64-bit, ATI Mobility 4650, SSD harddisk with 2.8 Ghz processors. 

Cheers, 

jakslev

---

### Post by Rhemat on 2010-04-20
No, I didn't really.  PulseAudio has been playing nice as of late, but I haven't fixed it.

I wish I could change the title of this subject, because PulseAudio has been the culprit all along, not Flash or FireFox.

---

