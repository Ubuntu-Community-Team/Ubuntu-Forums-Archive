---
title: "No sound using SB Audigy 2 ZS (SB0350)"
date: 2007-07-14
forum: Multimedia &amp; Video
---

### Post by dlouwers on 2007-07-14
I do not seem to get any sound output using this sound board. I have made sure that it is the only card being used (turned off onboard sound) and messed around with the Audio Analog/Digital Output Jack settings. Nothing helped. Any suggestions or is Audigy 2 support notoriously bad and would you advise removing it and turning on the AC'97 onboard sound?

---

### Post by Subfusc on 2007-07-14
you have to turn all the sound channels on (i know i got the exact same card, and it works smoothly) 
you do this by right clicking your volum control manager on your gnome-toolbar, and open the volum control, then you go to preferences and add all the "tracks to be vissible".
this is how mine look like:
[[IMG]http://img411.imageshack.us/img411/8752/screenshotvolumecontrolco8.png[/IMG]](http://imageshack.us)
Shot at 2007-07-14

i also have analog audio "x" out and the option External Amplefier (allthou i dont think the last is necessary)

---

### Post by kronq on 2008-03-21
cheers! solution worked for me first time :)

---

### Post by fadastic on 2008-03-22
Also, if you have more than one card you may want to edit your /etc/modprobe.d/alsa-base and enter the line "options snd-emu10k1 index=0" so that your Soundblaster loads by default.

---

