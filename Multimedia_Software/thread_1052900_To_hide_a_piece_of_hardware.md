---
title: "To hide a piece of hardware"
date: 2009-01-28
forum: Multimedia Software
---

### Post by GepettoBR on 2009-01-28
Short version: I want to trick Ubuntu into not knowing I have an external soundcard so it's forced to use my onboard sound.

Long Version: I have onboard Intel HDA sound and a cheap SoundBlaster card I got because my capture quality with the onboard was very low. As it turns out, it was simply because the ALSA driver for my on-board was flaky (I had to compile from source for it to even be recognized) and the latest version fixed this problem, rendering my cheap SoundBlaster useless. However, PulseAudio suddenly (after I ran Update Manager three days ago, and IIRC nothing directly related to PA was even updated) decided to ALWAYS default to the cheap card, not save my preferences when I change the default and generally be a total douchebag. I can work around this by changing each individual application's stream on padevchooser's Volume Control, but some applications (most annoyingly Firefox and Audacity) don't even appear on the list, so they have gone mute.

I could just remove the soundcard, but disabling a piece of hardware is so ridiculously simple in Windows that I refuse to not know how to do it in Linux. I have a vague idea that it has something to do with finding and blacklisting a kernel module or two, but I don't know how I'd go about doing that (or, more specifically, undoing it if I happen to blacklist the wrong module). Simply hiding the soundcard from ALSA and Pulse will also do.

Thanks in advance for all responses,
Paulo.

---

### Post by GepettoBR on 2009-01-29
One day, one BUMP

---

### Post by ibutho on 2009-01-29
One option is to take a look at the modules that are loaded for the soundblaster card (using lsmod) and then blacklist them in /etc/modprobe.d/blacklist.

---

### Post by Neural oD on 2009-01-29
agreed - have a look at this: [http://thoughtsbyclayg.blogspot.com/2008/01/ubuntu-disable-hardware.html](http://thoughtsbyclayg.blogspot.com/2008/01/ubuntu-disable-hardware.html)

---

### Post by GepettoBR on 2009-01-29
> **ibutho said:**
> One option is to take a look at the modules that are loaded for the soundblaster card (using lsmod) and then blacklist them in /etc/modprobe.d/blacklist.

> **Neural oD said:**
> agreed - have a look at this: [http://thoughtsbyclayg.blogspot.com/2008/01/ubuntu-disable-hardware.html](http://thoughtsbyclayg.blogspot.com/2008/01/ubuntu-disable-hardware.html)

Yes! This is what I thought I should have done! Thank you both very much. My only question is how do I identify which module is my soundcard's? There's lots of snd_xxx, most of them are apparently codec-related. I'm sure of which is the onboard soundcard (the one I want to keep): snd_hda_intel.


Can anyone post the relevant portions of their lsmod so I can see which modules aren't hardware-specific and find mine by elimination?

Thanks in advance,

Paulo.

---

### Post by ibutho on 2009-01-29
What is the output when you run
```
sudo lsmod | grep -i snd
```
Post that and I am sure we can identify which modules are associated with the soundblaster.

---

### Post by cariboo on 2009-01-29
Depending on how old your Soundblaster card is, it could use either the sb module or in the case of the Soundblaster card I've got is uses the snd_ens1371 module.

Jim

---

### Post by GepettoBR on 2009-01-29
Hello, and thank you!

I've found the culprit! I had forgotten that I had another computer I could cross-check with. The module for my card was "snd_cs46xx". It is now blacklisted and out of my way.

Even before I found it, though, there was an update to PulseAudio that fixed the regression keeping it from respecting my selections. Still, it's great to know that I'll be safe from similar problems in the future now that I have acquired this new skill.

Thank you all for your time and help.
Paulo.

EDIT: Why can't I mark the thread SOLVED? Shouldn't the button be in the Thread Tools menu?

---

