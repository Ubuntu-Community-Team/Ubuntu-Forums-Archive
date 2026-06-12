---
title: "pulseaudio iec958 headaches"
date: 2009-06-08
forum: Multimedia Software
---

### Post by shamgar03 on 2009-06-08
So I know that spdif/digital out works because the following commands put sounds out:

mplayer -ao alsa:device=iec958 test.mp3
aplay -D iec958:CARD=ICE1724,DEV=0 ~/Desktop/Prelude.wav 

However, I cannot figure out how to set that as the default output. I changed all the settings in system->preferences->sound to 
ICE1724 IEC1724 IEC958 (ALSA) and the test sound works, but for some reason none of the applications (nor the operating system) output to the speakers. Anyone know whats going on?

This is a fresh install of Jaunty.

---

### Post by shamgar03 on 2009-06-08
Is there anyone on here who has gotten optical/digital/iec958 out working?

---

### Post by shamgar03 on 2009-06-09
Alright so I finally figured it out. Basically pulseaudio wasn't automatically loading the module for hw:0,1, so I had to do the following and then reboot: (its maybe possible you could just unload and reload some module, but rebooting is easier)

add to /etc/pulse/default.pa:
load-module module-alsa-sink device=hw:0,1

It should be noted that this does not preclude the loading of hw:0,0. After that, when I would run paman under devices alsa_output.hw_0_1 showed up. Then to get sound out to it, I used padevchooser. Through some bug in padevchooser doesn't show any sinks, so I had to type in

alsa_output.hw_0_1

in the sink->other box

We'll see if everything sticks after I reboot...

---

### Post by shamgar03 on 2009-06-10
Still can't get 5.1 output working. Does anyone know of a guide for that?

---

