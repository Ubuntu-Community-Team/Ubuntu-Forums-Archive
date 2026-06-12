---
title: "I do not understand this Alsa/Pulseaudio Sound System"
date: 2010-09-06
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Yumi on 2010-09-06
I read numerous threads about my sound problems since before Lucid. Since the last update it did not work again, and I found a new solution which works, I am listing to online radio at the moment. But I do not know why and do not find a permanent solution.

My orginial problem was/is that Pulsaudio shows the level of sound, but says "Dummy Output". Soundcard is recognised and the signal gets through - no sound at the speakers.

Situation now:
After starting up and login there will be no sound. In a terminal I have to do "~$ pactl load-module module-detect". This command will mute and reset the volume slider on some channels in gnome-Alsa-Mixer and Alsamixergui.

I then have to open Gnome-Alsa-mixer and unmute/reset Volume levels. Still no sound.

Next opening alsamixergui and unmuting/resetting the output channel - instand high quality sound.

Questions:

Gnome-Alsa-mixer without Alsamixergui does not work. Can I uninstall it?

How can I make sure that module-detect is loaded automatically? I tried to edit /etc/pulse/default.pa but to no avail.

How can I permanently unmute and set output levels in alsamixergui?

Thanks, Michael

---

### Post by kyleabaker on 2010-09-06
> **Yumi said:**
> I read numerous threads about my sound problems since before Lucid. Since the last update it did not work again, and I found a new solution which works, but I do not know why and do not find a permanent solution.

Situation:
After starting up and login there will be no sound. In a terminal I have to do "~$ pactl load-module module-detect". This command will mute and reset the volume slider on some channels in gnome-Alsa-Mixer and Alsamixergui.

I then have to open Gnome-Alsa-mixer and unmute/reset Volume levels. Still no sound.

Next opening alsamixergui and unmuting/resetting the output channel - instand high quality sound.

Questions:

Gnome-Alsa-mixer without Alsamixergui does not work. Can I uninstall it?

How can I make sure that module-detect is loaded automatically? I tried to edit /etc/pulse/default.pa but to no avail.

How can I permanently unmute and set output levels in alsamixergui?

Thanks, Michael

My audio devices weren't detected for some reason on a fresh Beta install, while they worked fine earlier from a fresh Aplha 2 install.

Here is what I followed to get them working again..
[http://ubuntuforums.org/showthread.php?t=1515200&p=9494585](http://ubuntuforums.org/showthread.php?t=1515200&p=9494585)

---

