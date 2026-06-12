---
title: "Default sound device"
date: 2009-08-25
forum: Multimedia Software
---

### Post by ghostofmybrain on 2009-08-25
I'm having trouble figuring out how to set my default sound device.  It seems like about half my sounds come through my speakers and the other half through my USB headset.  For example, Rythmbox and system sounds come through the speakers, but Amarok and firefox come through the headset.  I went to System/Preferences/Sound and changed all the output to the HDA Intel ALC1200 Analog (OSS), which when I push the "test" button gives me sound through the speakers.  But still, about half the programs will make sound through the headset, which I don't want.

Um... I'm using Jaunty... I'm also very very new to linux, so I don't know what other information you need to help me out. :P

---

### Post by lian1238 on 2009-08-25
Do you have the option "ALSA - Advanced Linux Sound Architecture"? Try that.

---

### Post by ghostofmybrain on 2009-08-25
> **lian1238 said:**
> Do you have the option "ALSA - Advanced Linux Sound Architecture"? Try that.
Yes, I do.  I tried that first, but when I click "test" I get no sound whatsoever.

---

### Post by krul on 2009-08-26
install padevchooser...this is a system tray application where you can specify for each program/source on which sound card it should play...works like a charm

---

### Post by ghostofmybrain on 2009-08-26
> **krul said:**
> install padevchooser...this is a system tray application where you can specify for each program/source on which sound card it should play...works like a charm
I can't figure out where in that program I can specify for each program which sound card it should play on.

Also, is there anything specific my settings need to be in "sound" for this to work?

---

### Post by ghostofmybrain on 2009-08-26
> **ghostofmybrain said:**
> I can't figure out where in that program I can specify for each program which sound card it should play on.

Also, is there anything specific my settings need to be in "sound" for this to work?
Aha!  I figured it out reading the [Jaunty 9.04 Sound Solutions thread](http://ubuntuforums.org/showthread.php?t=1130384).  Yay. I will celebrate with my favourite food. :popcorn:

---

