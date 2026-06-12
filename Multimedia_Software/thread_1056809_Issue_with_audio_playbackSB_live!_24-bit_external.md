---
title: "Issue with audio playback/SB live! 24-bit external"
date: 2009-02-01
forum: Multimedia Software
---

### Post by ELWisty on 2009-02-01
Hi,

Anyone could give some clues as to the correct settings etc. on this one?

**I have:**

Acer Aspire 5040 laptop
Creative Sound Blaster Live! 24-bit external
Ubuntu Intrepid (8.10)
Firefox (3.0.5)

The audio settings are as follows:

System > Preferences > Sound: all set as "Creative Technology SB Live! 24-bit External USB Audio (OSS)

Volume control preferences (device and track to control): SB Live! 24-bit External (alsa mixer)

Volume control (device): same as above.
[B]
With these settings, sound DOES come through the external soundcard with:[/B]

-Totem movie player, all video playback
-Rhythmbox music player, mp3 and flac playback

**I can get laptop speaker blayback (and headphones plugged to the laptop) ONLY with the following:**

-Youtube
-VLC, all video playback

In the case of Youtube, is some additional plugin required for the browser to get the sound through the external soundcard?

In the case of VLC, changing the sound preferences does not seem to have an effect.

I have tried fiddling with the settings in Sound etc. (for instance changing to "Creative Technology SB Live! 24-bit External USB Audio (ALSA)") but the only result is that also Totem and mp3 playback no longer come through the external sound card.

It's possible that I simply have not managed to choose the correct combination of audio settings yet. Not a huge issue but it would be good to get all the audio working through SB.

---

### Post by erikthedrink on 2009-09-08
I've got logitech usb speakers:lolflag:.  In Xubuntu, go to Applications, then Accessories, then Terminal.  In Terminal, type

[FONT=Georgia][SIZE=4]asoundconf set-default-card 1[/SIZE][/FONT]

Then close and re-open your browser (Mozilla Firefox) or restart your system.
:P
Note, if you unplug your usb speakers, your laptop speakers will take over.  In order to re-establish contact with the usb speakers, you will need to (plug them back in) restart the system.

---

