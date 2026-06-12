---
title: "Mic not recording"
date: 2006-08-04
forum: Multimedia &amp; Video
---

### Post by BobSongs on 2006-08-04
I started going through the procedure of removing drivers and re-installing them. But before I go and do something I consider radical (like recompiling my kernel *shudder*), I thought I'd put the problem to the forum and see if this is just a "meh, reinstall Ubuntu" thing.

Here goes.

**Specs**
Celeron generic box
SoundBlaster Live! 5.1
512 Mb RAM
Ubuntu 6.06
Microphone
Altec Lansing speakers.

**Problem**
I cannot record from the Microphone. Perhaps it's a Volume Control setting that's off. I can list them.

I hear sound from the mic through the speakers. That's not the issue. The PC is receiving the feed. I get a howling feedback if I raise the speaker volume too high.

But "Sound Recorder" or "Audacity" do not detect any sound when I select Microphone and hit Record. I slide the volume control in Audacity and I can hear the sound the mic is receiving increase.

Other than the PC's inability to capture sound everything else works fine.

Note: I put a DVD into the DVD drive and captured what was coming out of the speakers in Sound Recorder. So capturing works. Just ... not from the Microphone. Should I re-install?

**Sound Control Settings**
Capture Tab: "Capture" and "Microphone" are both set to 100%; both lower icons are enabled. Everything else is muted. I've done every assortment of enabling and disabling those icons. Still Audacity flatlines when recording. All the while sound comes through the speakers.

P.S.: This is not the first time I've installed Dapper. The microphone has worked before. This install something went wrong.

P.P.S.: I just flipped over to XP and easily recorded microphone sounds in Sound Recorder. Just to make matters more difficult.

---

### Post by cantormath on 2006-08-04
> **BobSongs said:**
> I started going through the procedure of removing drivers and re-installing them. But before I go and do something I consider radical (like recompiling my kernel *shudder*), I thought I'd put the problem to the forum and see if this is just a "meh, reinstall Ubuntu" thing.

Here goes.

**Specs**
Celeron generic box
SoundBlaster Live! 5.1
512 Mb RAM
Ubuntu 6.06
Microphone
Altec Lansing speakers.

**Problem**
I cannot record from the Microphone. Perhaps it's a Volume Control setting that's off. I can list them.

I hear sound from the mic through the speakers. That's not the issue. The PC is receiving the feed. I get a howling feedback if I raise the speaker volume too high.

But "Sound Recorder" or "Audacity" do not detect any sound when I select Microphone and hit Record. I slide the volume control in Audacity and I can hear the sound the mic is receiving increase.

Other than the PC's inability to capture sound everything else works fine.

Note: I put a DVD into the DVD drive and captured what was coming out of the speakers in Sound Recorder. So capturing works. Just ... not from the Microphone. Should I re-install?

**Sound Control Settings**
Capture Tab: "Capture" and "Microphone" are both set to 100%; both lower icons are enabled. Everything else is muted. I've done every assortment of enabling and disabling those icons. Still Audacity flatlines when recording. All the while sound comes through the speakers.

P.S.: This is not the first time I've installed Dapper. The microphone has worked before. This install something went wrong.

P.P.S.: I just flipped over to XP and easily recorded microphone sounds in Sound Recorder. Just to make matters more difficult.

Im not sure if you did this.......but

double click on the little speaker near the clock.
Click on Capture tab.
enable line in, microphone and/or capture, depending on what you want to do.

let me know if that works.

---

### Post by BobSongs on 2006-08-04
> **cantormath said:**
> I'm not sure if you did this.......but

double click on the little speaker near the clock.
Click on Capture tab.
enable line in, microphone and/or capture, depending on what you want to do.

let me know if that works.
Good one. Already tried it. No go. I opened up everything: Synth, Wave, Line in, CD... nothing works. I thought Capture might get in the way. But, alas, it's not the problem.

Sorry to put forth such a poser. I can open a terminal and throw any number of commands at it. So far everything I've tried shows a fully functional sound card.

---

### Post by PatrickMay16 on 2006-11-05
I have the same problem. I cannot record from Microphone or Line-in.

My sound card is a Sound Blaster Live. No matter what I do, I can hear my voice from the microphone playing in the speakers, or the music playing into the line in, but no recording application picks it up at all.
It worked fine on releases prior to Dapper.

I also have this same problem with my Laptop, which has a "crystal soundfusion" if I remember correctly. It is an IBM Thinkpad T22.
However, recording does indeed work with microphone and line-in on my spare test computer, which has an ALS4000.

Perhaps it is worth mentioning that on both the machines which I have this problem with, they both have soundcards with hardware sound mixing? That is, the ability to play several different streams of audio at once, mixed in hardware.

---

### Post by PatrickMay16 on 2006-11-06
Heh heh heh. We are all LINUX USERS here at Ubuntuforums.
I have FIXED the problem. I went into the alsamixer and turned "AC97" all the way down to zero... now mysteriously I can record from my microphone.

---

### Post by Steve H on 2007-04-16
I´m having the same problem, but turning down AC97 doesn´t help (partly because it was already turned down and muted).

Did anyone manage to get this working? I´ve tried all the inputs as the mic. I can hear the mic from my headphones but neither TeamSpeak nor Sound Recorder actually pick up the sound.

---

