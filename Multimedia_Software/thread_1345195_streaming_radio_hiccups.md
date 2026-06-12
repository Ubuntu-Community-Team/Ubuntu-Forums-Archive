---
title: "streaming radio hiccups"
date: 2009-12-03
forum: Multimedia Software
---

### Post by glandeur on 2009-12-03
I'm stumped by streaming radio hiccups in both rhythmbox and totem.  Overall my sound seems fine, but when I stream radio after about 5-8 minutes in either player I get buffering hiccups every 45 seconds or so.  It sounds great those first 8 minutes.

The computer is old (dell pIII 1g, 384mb, on board sound) but surely powerful enough to stream audio.

I'm running karmic with xfce from a minimal install, not the full xubuntu desktop package.  I've used synaptic to add rb and totem and they seem to work for everything but radio.  I'm not sure what package gave me pulseaudio but I got rid of that (now it seems it wasn't the problem) and went to just alsa.

The last thing I had on this computer was xubuntu hardy (up to last week) and I could stream radio fine with totem and listen.  I did a clean install not an upgrade.

I have broadband and all the other devices in my house have no issues with the same stations I've been trying.

One clue I can offer is that as opposed to spiking my cpu bottoms out in the panel graph when the hiccups occur, but maybe the applet is just experiencing the same hiccup.

Many thanks for any suggestions.

---

### Post by glandeur on 2009-12-09
While I didn't figure out exactly what was going on, this is no longer an issue for me.  I found an old sound blaster card laying around and switching to that from the on-board audio has solved the problem.

I'm guess my on-board audio must not have liked something about 9.10 compared to 8.04.

---

