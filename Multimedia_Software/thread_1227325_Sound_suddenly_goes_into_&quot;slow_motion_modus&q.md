---
title: "Sound suddenly goes into &quot;slow motion modus&quot;"
date: 2009-07-30
forum: Multimedia Software
---

### Post by Milkman Mr. Miller on 2009-07-30
Hi everyone,

I've been looking for answers a few days now, unable to find the solution the problem I'm dealing with. I'm using Ubuntu Studio 8.04 (which is a great distribution of Ubuntu, I've been using it with no problems at all, for months).

**Problem**
My sound is not working as it should. Everything works fine after start up. But - depending on the amount of processes using my sound cards I'm running - suddenly some sort of congestion starts acting up. I've got a feeling that says its some buffer overflow. 
To describe it: it's like playing a video tape and slowing it down. The sound goes all clutchy and bad. Playing one second of music takes about 5 seconds. It occurs when streaming internet radio, playing Alien Arena, playing tunes on the fine Rhythmbox (or Amarok, or Audacious).  When skipping a bit in the song, the song skips as it should, but the playing continues slomo as described above. 
As far as now, it's only fixed by rebooting. It occurs on both ALSA and Pulseaudio.

**What have I tried?**
[LIST=1]
[*]Re-installing Ubuntu Studio 8.04
[*]Removing, reïnstalling, installing whatever codecs there were available both ALSA and Pulseaudio
[*]Re-installing Ubuntu Studio 8.04 again to fix what I'd done ;)
[*]Plugging out my new Sweex digital 7.1 sound card again and leaving the on-board VIA sound card alone
[*]Switching apparatus on Sound Preferences from OSS to ALSA to Pulse to Autodetect etc. etc.
[*]Re-install the ubuntu-studio-desktop package again using synaptic
[*]Plugging my Sweex sound card (C-Media) back in
[*]Ran through the [walkthrough somewhere else on Ubuntuforums.org]("http://ubuntuforums.org/showthread.php?t=789578") which fixed other sound errors (connected to PulseAudio, it's a must-see) and got Ubuntu to recognise my Sweex sound card (or at least I discovered that it did)
[/LIST]

**Current setup**
I'm using my Sweex annex C-Media as my standard device. Which I selected using the Pulse Audio device chooser. Though the problem already occured to my computer when I only used my VIA onboard card.

At the moment Rhythmbox is working properly. Result of *[COLOR="Red"]aplay -l[/COLOR]* is looking just great! Here it is:
> **** List of PLAYBACK devices ****
kaart 0: VT82xx [HDA VIA VT82xx], apparaat 0: ALC861 Analog [ALC861 Analog]
  Sub-devices: 1/1
  Sub-device #0: subdevice #0
kaart 0: VT82xx [HDA VIA VT82xx], apparaat 1: ALC861 Digital [ALC861 Digital]
  Sub-devices: 1/1
  Sub-device #0: subdevice #0
kaart 2: CMI8768 [C-Media CMI8768], apparaat 0: CMI8738-MC8 [C-Media PCI DAC/ADC]
  Sub-devices: 0/1
  Sub-device #0: subdevice #0
kaart 2: CMI8768 [C-Media CMI8768], apparaat 1: CMI8738-MC8 [C-Media PCI 2nd DAC]
  Sub-devices: 1/1
  Sub-device #0: subdevice #0
kaart 2: CMI8768 [C-Media CMI8768], apparaat 2: CMI8738-MC8 [C-Media PCI IEC958]
  Sub-device: 1/1
  Sub-device #0: subdevice #0


**And the problem occurs,,, sort of**
My sound just hangs on Rhythmbox playing the same split second of music over and over. This time, no slow motion.
Audacious can still play tracks. Though it goes into slow motion mode when skipping tracks. It sounds like it has a problem when fading in and/or out
Nothing changed in aplay -l. 

A few examples on behaviour:
1. When using Autodetection in Audio preferences: the slowmo occurs instantly at Rhythmbox, and when skipping on Audacious
2. When using my C-media. Audio preferences hangs on testing. In many ways sound playback does not occur.
3. When selecting ALSA it seems that it uses my VIA onboard but sounds seems to function properly, I can hear Nick Drake so clear playing on Rhythmbox, but Alien Arena gives no sound at all.

**My conclusion**:
I'm confused...
What do I do?

---

### Post by tiggsy on 2010-04-07
I'm running Karmic, after a system rebuild. My sound is in slomo, It's very funny, as it sounds like a demon has taken over, but not useful, and I would like to play both my music, and videos, so on.

My standard practice when I do an upgrade is to run the HOWTO: PulseAudio Fixes & System-Wide Equalizer stuff, and i have done so, but this time it's not fixing the problem.

---

### Post by tiggsy on 2010-04-12
OK I suddenly remembered a sound troubleshooter on here, and found it. It fixed my problem, so quick. 

[Comprehensive Sound Problem Solutions Guide v0.5e]("http://ubuntuforums.org/showthread.php?t=205449")

I just followed the instructions under the heading "Getting the ALSA drivers from a *fresh* kernel", rebooted, and I now have sound again.

---

