---
title: "Need guidance on hooking up my guitar"
date: 2007-10-22
forum: Multimedia Production
---

### Post by kircher1 on 2007-10-22
I have a mac and garageband, and it is possibly the simplest way for me to hook up my guitar and jam. I just downloaded ubuntu studio and I would really like to try it out. However, im completely lost as to how I should hook up my guitar. 

I have ubuntu 7.10
Integrated sound - no soundcard
and I use the 1/4" to 1/8" cable that plugs into the mic jack in the back of the computer

I've messed around with a few of the applications to no avail. I just want someone to point me in the right direction so I can start playing my guitar on my PC. Please help.

---

### Post by Microsoft_Sam on 2007-10-23
Go to Applications>Sound & Video>Audio Production>JACK Control. Click the "Start" button. This starts the JACK Server. Then you click the "Connect" button and in the left column, there should be alsa_pcm, Click its little arrow, then click capture_1 and then click the "Connect" button. You should then be able to hear your guitar.

Then you can open creox to add effects to your guitar, but I recommend using actuall pedals for this, it's a quality thing...

Then you can open Audacity, and hit Ctrl+P. Under Recording in the top right, there is the device, change that to Jack Audio Connection Kit: creox.

Hit "OK" then the record button and you should be recording your guitar using the creox effects.

If you're like me and hate the creox effects, change the recording device to JACK Audio Connection Kit: alsa_pcm and you'll be recording straight from your mic jack. And just close creox (or never open it). Hope this helps!

---

### Post by kircher1 on 2007-10-23
Thanks for the advice, it was very helpful. I've got playback now.

Its really quiet, though. My speakers and volume settings cranked and its at a normal volume. I assume that means i should run my guitar through my amp, unless theres another way to increase the volume. 

I usually run my guitar straight into my mac when using Garageband and don't bother with my amp, and it projects at a good volume. 

Any suggestions on how to increase my playback volume levels?!

---

### Post by nalmeth on 2007-10-23
Check the preferences in the volume mixer, make sure all the controls are being displayed. Turn up anything that wasn't already. 

If you're just plugging your guitar in clean, it needs some amplification to go louder.

I can't remember if Audacity supports live plugins, but you will need to install some LADSPA plugins. 

I can't remember which set of plugins has the amplifier I use, I usually just have all of them installed:
blop caps cmt fil-plugins ladspa-sdk mcp-plugins omins swh-plugins tap-plugins vcf-plugins dssi-example-plugins dssi-host-jack dssi-plugin-fluidsynth dssi-plugin-hexter dssi-plugin-hexter dssi-plugin-xsynth dssi-utils

It might be either caps, tap-plugins, or swh that you need to get the amplifier. Just install/uninstall as you see fit

Easiest way to install multiple things at the same time is with the terminal (Applications -> Accessories -> Terminal):
```
sudo apt-get install caps tap-plugins swh
```

Restart audacity and those plugins should be available. There are other more advanced apps than audacity, but I would start there until you need more.

---

### Post by Endolith on 2007-12-05
Jokosher is supposed to be similar to Garageband.

---

