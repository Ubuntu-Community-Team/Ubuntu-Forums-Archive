---
title: "Yet another audacity thread. &quot;error while opening device&quot;"
date: 2007-09-01
forum: Multimedia Production
---

### Post by NoSmokingBandit on 2007-09-01
I just got my sound card to work (sound blaster live platinum) and set off to record but audacity doesnt let me. When i hit the rec button i get the "error while opening device" error. It plays back sound just fine if i import a file. The sample rate is 44100, so i know thats not the problem. My prefs window looks like this:

```

Playback Device:
SB Live! Platinum [ct4760p]: ADC Capture/Standard PCM  playback hw: (0,0)

Recording:
SB Live! Platinum [ct4760p]: Multi-channel Capture/PT playback hw: (0,2)
Channels:
1 (mono)

```
Neither of the boxes are checked.
I've installed the asla-oss and have tried running "aoss audacity" but nothing has worked. Both my line-in and mic are unmuted. Any ideas?

---

### Post by urangela on 2007-09-12
I get the same error, I am running ubuntu studio on an acer aspire 5570z; I think it is a problem with the configuration, but I am not sure. I am really new at this.

---

### Post by dabl on 2007-09-12
Audacity is real particular about having exclusive access to the sound device, for playback especially.  Close your browser and anything else that has a remote chance of making a sound, then restart Audacity.

I assume you're using ALSA as the sound system, and have the alsa-base, alsa-oss, and alsamixergui packages installed.  :)

---

### Post by NoSmokingBandit on 2007-09-12
i actually gave up on running linux on my recording box. I installed XP Performance edition and everything works fine on that. I tried your remedies and several others, none worked. God, i want to use linux, but linux doesnt want me to use it. Anywho, thanks for the help regardless :)

---

### Post by dabl on 2007-09-13
Some of the newer Creative Labs cards are pretty tough, apparently. You will probably see Linux support develop for them in the not-too-distant future. :)

---

### Post by NoSmokingBandit on 2007-09-13
its a few years old, just like the rest of my computer, yet certain things dont work. When linux gets support for my hardware i'll be back.

---

### Post by eye208 on 2007-09-14
Audacity's playback feature doesn't work here either. Cannot select any output device in the preferences window. Everything else works fine though, so I guess it's a bug in Audacity.

---

### Post by Stochastic on 2007-09-17
Playback is working fine for me in Audacity, running through Jack.

---

### Post by OutsideEdge on 2007-09-21
Had the same issue.

Tried reinstall and manual edit of .audacity file without success.

Audacity worked fine after changing sound preferences in System->Preferences->Sound Devices tab to all ALSA devices.

---

### Post by dabl on 2007-09-21
Install the alsa-oss package.

Set your Audacity output device as the OSS device.  Worked for me, on Gutsy 64-bit.  :)

---

### Post by stmiller on 2007-09-23
Ubuntu Feisty has the OLD version of Audacity which is oss-only. Try the newer version of Audacity which works with ALSA and Jack, and has tons of improvements. 
You can even just download the Gutsy Audacity deb and extract the audacity executable from that package, for an easy way to get the new version.

---

### Post by NJC on 2007-09-25
I've had the Audacity "can't open I/O device.." A LOT. Check out the Troubleshooting - Linux at bottom of [this page.]("http://flossmanuals.net/Audacity/RecordingASound") After unselecting ESD (System > Prefs > Sound, and uncheck "Enable software sound mixing (ESD)"), I still needed to do the following:```
sudo killall esd
```Normally just closing the other conflicting sound device works - if not, I have to kill ESD.

---

