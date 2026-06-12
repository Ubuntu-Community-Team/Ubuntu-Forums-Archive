---
title: "Pulseaudio screwed my sound, how do I change default soundcard?"
date: 2009-10-21
forum: Multimedia Software
---

### Post by chris_andrew on 2009-10-21
Hi, all.

Got a beautiful installation of Koala running and stupidly decided to install Rhythmbox.  This is stupid because it drags in Pulseaudio as a dependency, which in the past has screwed my sound set-up.

Rhythmbox and Pulseaudio are now removed, but my sound is still trying to come out of the wrong sound card.

The one I want to use is alsa number 2.  I have tried xfce mixer and checked alsa to see whether my sound is turned-up on the appropriate sound card; all to no avail.  Can anyone remind me how to tell alsa which soundcard I want as default?  Bloody Pulseaudio.....

Cheers,

Chris.

---

### Post by kostkon on 2009-10-21
```
asoundconf list
```
to list the available devices and then
```
asoundconf set-default-card CARD_NAME
```
whereas *CARD_NAME* is the name of the audio device you want, as listed in the previous command.

---

### Post by chris_andrew on 2009-10-22
> **kostkon said:**
> ```
asoundconf list
```
to list the available devices and then
```
asoundconf set-default-card CARD_NAME
```
whereas *CARD_NAME* is the name of the audio device you want, as listed in the previous command.

This looks like the stuff I remember.  Unfortunately, asound isn't availible as an option either as a user or root.  I can install asoundconf-gtk, but I'd rather not as it seems unnecessary and only pulls in a couple of libs, not CLI asound.  Maybe the command has changed.

Any further clues anyone?  I'll Google around.

Chris.

---

### Post by chris_andrew on 2009-10-22
This solves my problem, but isn't an elegant solution.

Having removed PulseAudio, I rebooted (yikes!).  My sound is now working, again.

Chris.

---

