---
title: "PulseAudio PCM channel broken"
date: 2012-12-15
forum: Multimedia Software
---

### Post by Carl Foxmarten on 2012-12-15
I'm using XUbuntu Quantal, and have been fairly happy with it, until a couple of days ago.

I was recording something off my USB tape deck (a Grace Digital Audio device, I'll figure out the numbers and such later), and had to force Audacity to get around something that prevented it from using the built-in USB sound card in the player.
(I had to use the Line-In port on the motherboard)

Unfortunately, somehow when I muted the Master volume control during recording, something "broke" somewhere in the PCM mixer.

Right now, through the speakers, I can hear anything that comes in the microphone and line-in inputs, but nothing I've tried so far has been able to make noise from the software itself.
So, no playing music, no games make sound, etc, etc, etc.

There's a headphone port on the front of the PC, as well as a microphone port, but when I plug anything in there, the Master volume level gets muted, and sometimes even has the Master volume set to 0% as well.
It also mutes the Surround, Center and LFE volume controls.

When it's unplugged, the Master volume control is again muted, but the Surround, Center and LFE volume controls are unmuted.

I tried to find the configuration files for PulseAudio, and found the files in /etc/pulse/, but I don't understand any of them.

Does anybody have any suggestions?

---

### Post by Carl Foxmarten on 2012-12-16
If I use the xfce4-mixer tool and play around with the mute buttons for the various channels, as well as the "Headphones" switch, *sometimes* I can get sound working again, but it doesn't seem to be reliable, nor consistent.

---

