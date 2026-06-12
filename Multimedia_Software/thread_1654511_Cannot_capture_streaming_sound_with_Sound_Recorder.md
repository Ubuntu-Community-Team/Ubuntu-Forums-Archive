---
title: "Cannot capture streaming sound with Sound Recorder or Audacity"
date: 2010-12-28
forum: Multimedia Software
---

### Post by VanillaMozilla on 2010-12-28
I'm trying to record sound from here:  [http://kdhx.fm/archives/archive_gen.php?show=musicfromthehills](http://kdhx.fm/archives/archive_gen.php?show=musicfromthehills) .  I've played with both Sound Preferences and AlsaMixer, with no luck.  Nothing is muted.  I can hear the sound all right, and I can record from a microphone, but I can't record from the Internet.  I've tried recording with Audacity and with Sound Recorder.  No luck.

Audacity has no input selector.  According to this:  [http://audacity.sourceforge.net/manual-1.2/tutorial_basics_4.html](http://audacity.sourceforge.net/manual-1.2/tutorial_basics_4.html) (step 2, sentence 1), it's supposed to have one on the mixer toolbar.

According to the Alsa Mixer I have an HDA-Intel card with an ALC888 chip.  There is no other sound card.  I'm using Lucid with more-or-less default sound devices, I think.  I've made a reasonable effort, but so far I'm stymied.

If it's a matter of preferences and controls, maybe someone can play with it and discover which sliders on which device control the volume, and maybe summarize what controls what, if you get that far.  Or maybe you can point me in the right direction (even though your results may vary, I know).  As a carrot, you may like the link I posted.  Dec. 26 is especially nice.  ;)  Thanks very much.

---

### Post by mocha on 2010-12-28
When you start recording you go into the Pulseaudio volume control panel and the recording tab.  Then right click on the application that is recording and choose "monitor of ...".  You should see the volume level meter moving then.  You'll see what I mean.

---

### Post by VanillaMozilla on 2010-12-28
How do I get to that?  There are so many sound devices.  Pulse Audio is installed, but so far I can't figure out how to get to its control panel.

---

### Post by lidex on 2010-12-29
The filename is pavucontrol. To install use a terminal:
```
sudo apt-get install pavucontrol
```
To run use the Alt+F2 launcher and type in:
```
pavucontrol
```

---

### Post by VanillaMozilla on 2010-12-29
Thanks very much for your help.  I'm making a bit of progress.  For the moment it appears to be solved, but something is still very flaky.  I'm not sure if the problem is software, hardware, or both.

The Sound Preferences dialog shows this version of Audacity as using the ALSA plug-in, so it does not apparently use Pulse Audio.  I installed pavucontrol, and it appears to do exactly the same as Sound Preferences.

**I switched hardware from Analog Stereo Duplex to Analog Stereo Output** and it works (but I lose microphone input -- this is not a problem).  At the moment everything is perfect.  Yesterday, however, there were several problems:
(1) It still worked if I switched back to duplex.  Thereafter, microphone input and stream capture were quite unpredictable.  (It behaved as if the switch were defective, but this is a digital control!)
(2) Gain was wildly unpredictable, and sound was scratchy when the gain changed; it sounded like a bad electrical contact somewhere.
(3) There were very odd echo pulses that were added to the recording about every 6 seconds under some conditions.  This appears to be a software problem because it's hard to imagine how a hardware problem could add an echo, but I can't duplicate it.


Sound is an incredible mess.  The following references may be helpful:

[Audacity Linux issues]("http://wiki.audacityteam.org/index.php?title=Linux_Issues")
[Audacity recent packages]("http://audacity.sourceforge.net/download/linux")
[Ubuntu sound--how it works]("http://ubuntuforums.org/showthread.php?p=5931543")
[[SOLVED] Multiple Sound Solution (ALSA w Pulseaudio)]("http://ubuntuforums.org/showthread.php?t=843012")
[Pulse Audio--the Perfect Setup]("http://pulseaudio.org/wiki/PerfectSetup")
[ALSA instead of Pulseaudio for Ubuntu 8.10 Intrepid – a Non-Destructive way]("http://idyllictux.wordpress.com/2008/10/29/alsa-instead-of-pulseaudio-for-ubuntu-810-intrepid-a-non-destructive-way/")
[lucid pulseaudio and alsa problems]("http://ubuntuforums.org/showthread.php?p=9944385")
[Lucid PPA]("https://launchpad.net/~diwic/+archive/ppa")
[HOWTO: PulseAudio Fixes & System-Wide Equalizer Support]("http://ubuntuforums.org/showthread.php?t=789578")
[Ubuntu Wiki -- Debugging Sound Problems]("https://wiki.ubuntu.com/DebuggingSoundProblems")

There is at least one other, fairly minor software problem:  the system lacks a separate record volume control.

---

### Post by lidex on 2010-12-29
> **VanillaMozilla said:**
> 
There is at least one other, fairly minor software problem:  the system lacks a separate record volume control.

That should be 'Capture' in your mixer.

---

### Post by VanillaMozilla on 2010-12-30
It should be, but it isn't, at least in the Alsa Mixer.  If you find it, let me know.

One of those references mentions how everything is often mislabeled and thoroughly a mess.  It also mentions that your results may vary, alas.  If there is a separate control, I haven't been able to find it.  Probably not a software error so much as a generalized industry screw-up.

---

### Post by VanillaMozilla on 2011-01-02
Update:  I updated to Maverick.  So far it works perfectly, and I can also use Analog Stereo Duplex.  I haven't tried to see if I have a separate record volume control.

Moral:  upgrade to current version.

---

