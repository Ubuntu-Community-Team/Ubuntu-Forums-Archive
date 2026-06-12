---
title: "Audio problems with Gutsy"
date: 2007-11-05
forum: Multimedia &amp; Video
---

### Post by V!NCENT on 2007-11-05
Hello all,

My SB Live! card was dead and my onboard audio sound didn't work so I plugged in my old C-media 4.1 PCI soundcard. I booted my pc and it worked! I was _so_ happy because I didn't had sound for a very long time.

So far so good. But when I booted my pc the next morning the sound didn't work and all applications geared towards playing audio/video plain froze and crashed. I rebooted my pc and got into the BIOS setup to check if the BIOS still remembered the changes I made (disable onboard audio) and it did. So I booted into Ubuntu again but still no sound. I ran Doom3 to see if that might give me sound but no. I changed my audio device to OSS and back to ALSA but both gave me nothing but silence.

This is wierd. Everything is unmuted. I tried all the physical audio ports on the back of my pc but with no succes.

All help will be greatly appreciated!

---

### Post by jefe on 2007-11-05
Did you check /etc/modprobbe.d/alsa /etc/modules /etc. if there's everything as it should be? Maybe something's missing or some extra values were added by *buntu.

---

### Post by V!NCENT on 2007-11-05
> **jefe said:**
> Did you check /etc/modprobbe.d/alsa /etc/modules /etc. if there's everything as it should be? Maybe something's missing or some extra values were added by *buntu.
1) There is no alsa file in /etc/modprobe.d/
2) /etc/modules doesn't exist
3) There's no such thing as a alsa file in /etc
4) I know nothing about anything related to audio in Linux except that there is ALSA and OSS :(

---

### Post by V!NCENT on 2007-11-06
Would it work if I re-installed Ubuntu? Maybe it is configured for my onboard soundcard or something?

---

### Post by rmtatum on 2007-11-06
Post the results of ```
asoundconf list
```

---

### Post by V!NCENT on 2007-11-06
```
$ asoundconf list
Names of available sound cards:
CMI8738
U0x46d0x8da
```

Note that Volume Control Preferences gives me the following available devices to choose from (which are more than two devices):

1) C-Media PCI CMI8738 (Alsa mixer)
2) USB Device 0x46d:0x8da (Alsa mixer) *Strangely I don't have a USB soundcard or headset and I have never connected one in my entire life. I do have front USB and audio though.*
3) CMedia PCI (OSS Mixer) *Could that be the onboard soundcard? I have a motherboard with 'nForce2 audio'.*

---

### Post by V!NCENT on 2007-11-07
*Bump for going down to page 6*

---

