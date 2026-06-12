---
title: "Sound -- about to switch back to windows"
date: 2008-07-24
forum: Multimedia Software
---

### Post by mvchuck137 on 2008-07-24
I recently installed **Ubuntu 8.04 64-bit** and am a absolute novice on how this OS works. I consider myself good with computers and even programmed here and there, but I am having huge troubles with my sound card.

I have a **Turtle Beach Riviera** sound card and, yes, I have looked and looked all over google and this forums for help before posting. Linux reads my sound card as **CMI8738** and I did find one website with the driver, but the driver/package is really outdated (asks for me to install files into folders that do not exist) and the README that came with it is confusing as hell for me. I am also not using the digial output but the 5.1 jacks into the sound card.

I get absolute NO sound going through my headphones, so I decided to go to System>Admin>HardwareTesting. The very first test was a sound test and I was ready to press [No, I do not hear a sound] but I did hear a sound! The sound test detected the sound card CMI8738 and was able to play the little drum pattern.

I then turned on the Volume Meter and replayed the test. The volume meter did not read the sound that I was hearing.

I have also **unmuted everything** under the volume control plus messed around with the switches. Odd thing is, under the Volume Control I go to File>ChangeDevice and there is a list of 9 devices.

PLEASE help me (keep the directions easy), and thank you so much.

---

### Post by funkydan2 on 2008-07-26
So is the problem that you can hear sounds out of your speakers but not your headphones?

The issue might be to do with the 5.1 output you're trying to use.  A quick search for CMI8738 on the forums came up with [this]("http://ubuntuforums.org/showthread.php?t=251380") which may help.

It's not weird to have 9 devices in the volume control.  For my laptop (which has one phyiscal soundcard) I have 5 entries (which isn't all that user friendly).  It looks like they refer to either the input or output parts of the card, and also to different 'drivers' that the card is able to use (ALSA, OSS, Pulseaudio...)

---

### Post by funkydan2 on 2008-07-26
--Double Post--

---

### Post by funkydan2 on 2008-07-27
You should have a chat with [this guy]("http://ubuntuforums.org/showthread.php?t=870019") who is raving about how good this sound card is under Linux.

---

