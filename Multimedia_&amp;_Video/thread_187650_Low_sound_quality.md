---
title: "Low sound quality"
date: 2006-06-03
forum: Multimedia &amp; Video
---

### Post by Bd4e on 2006-06-03
Hello !

I have just installed Ubuntu 6.06. everything went smooth, but when listening to music i can hear some rustling, (some background noise), which is very annoying.
How can i get rid of that.
I am using Nfroce2 chipset soundcard. SOund quality in Win XP is normal.

---

### Post by ibrastix on 2006-07-05
i had the same problem and the problem turned out to be because of the volume in the media player was set to max.
for example, when i was using XMMS, if the volume is 100%, i hear distortion, but, when i decrease it to 70% for example the distortion disappears.
wierd but that worked for me.
hope i helped.

---

### Post by pertti on 2006-07-06
That's true, but on windows my volume is quite higher and without the hiss.

By the way, a week ago or so my volume decreased without any apparent reason. I couldn't hear properly some of my videos because of that. Then I opened xmms (which I don't use) and noticed that its volume bar controlled some "hidden" volume setting. Once I raised it to 100% everything went back to it's nice pre-hiss state :). Weird.

---

### Post by daou on 2006-07-07
I had the same problem about a week ago. The problem turned out to be the PCM volume control.

Like **ibrastix** noted, it sounds fine when it's set to 70% and begins distorting above that.

You need to go to your XMMS preferences->Audio I/O plugins. Set the output plugin to ALSA if it isn't already. Then click the configure button in the Output Plugin section to "configure" the ALSA preferences.

A new window opens up. In the Device Settings tab, Mixer section, set the Mixer device to Master. It is currently probably set to PCM.

Now when you adjust the volume in XMMS, it changes the master volume (sound level of the OS) and not PCM. If this is not what you want, you can click the "Use software volume control" in the Mixer device section. Then the XMMS volume control controls only the XMMS volume (but then you can't set the sound level with ie. your keyboard volume controls and the sound level will be "normal" at 100%, meaning you can only turn the volume lower in respect to the volume level of other apps).

Now use Synaptic to install alsa-mixer (either alsamixergui or gnome-alsamixer). Use that to set the PCM volume to a level (probably near 70%) where it doesn't distort the sound.

---

