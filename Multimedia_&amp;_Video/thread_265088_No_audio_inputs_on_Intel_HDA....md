---
title: "No audio inputs on Intel HDA..."
date: 2006-09-25
forum: Multimedia &amp; Video
---

### Post by Donshyoku on 2006-09-25
For some reason, I am not recieving any input for audio.  My microphone or line in is not inputting the audio I am routing to it via my TV tuner.  It is not interal routing either, as there is a physical cord running from the back of my card into the rear mic or rear line input.  

ALSA shows that these devices are on, set to capture, and not muted, but I get no audio in TV Time.   I noticed that the Gnome Volume Control lists my TV tuner as an audio source.  However, when I turn the line up and unmute the line support for the card, I still get no sound.  Navigating away from the tuner sound settings, it resets it to mute.

I have yet to try OSS, but I figured I would drop this in for some hints while I mess with it.  If that doesn't work, I may install the new ALSA drivers (1.0.12) and see how that goes.

Please help!

---

### Post by Donshyoku on 2006-09-25
OSS does not support anything but audio output on my card.

And ALSA wants to me recompile my kernel in order to update the driver, I'm not about to do that.  I've never done it before and don't trust myself to do it now! ;)

---

