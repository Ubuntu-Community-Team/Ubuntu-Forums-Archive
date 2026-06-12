---
title: "How-To Flash Audio Problem if sound card not recognized by Pulse Audio"
date: 2009-08-30
forum: Multimedia Software
---

### Post by jfenn2199 on 2009-08-30
How to for Flash Audio Problems in Ubuntu 9.04 (if sound card not recognized by Pulse Audio)

Audio for flash players has been a constant problem with Ubuntu 9.04 one potential way for fixing it is to verify whether or not your card is recognized by Pulse Audio.

First check your Sound Preferences by going to System->Preferences->Sound and under Default Mixer Track select Pulse Audio.  If Pulse Audio is showing Null Output under playback then your card is not recognized by Pulse Audio.  Reselect your <Sound Card> Alsa mixer and from the Terminal use 

```
sudo apt-get install alsamixer

```
(if apt-get is not showing it as available go use aptitude and look under not installed->sound->universe and select by pressing shift+= to create '+' sign)

and

```
sudo apt-get install alsamixergui
```

After installation of both alsamixer and alsamixergui is complete go to Applications->Sound & Video->Alsamixergui

In the top right hand corner it will have Card:<card name>.  If pulseaudio is present instead of your card name then Alsa the alsamixer is pointed to Pulse Audio.  The simplest way to fix this is to remove pulse audio by once again going to the terminal and typing

```
sudo apt-get remove --purge pulseaudio
```

After the removal of pulseaudio is completed close and re-open Alsamixergui.  Now your sound card should be in the upper right hand corner behind card:

Check that PCM is available in your mixer list and that it is unmuted and turned up.  This should fix your Flash Audio problems.


Joseph L. Fennell```

```

---

