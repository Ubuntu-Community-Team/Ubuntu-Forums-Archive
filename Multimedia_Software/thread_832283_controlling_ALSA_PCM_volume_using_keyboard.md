---
title: "controlling ALSA PCM volume using keyboard"
date: 2008-06-17
forum: Multimedia Software
---

### Post by mrmustardman on 2008-06-17
My speakers' volume is controlled by the PCM level in alsamixer. When I twist the volume knob on my keyboard, it changes the Master level. Is there any way I can make my keyboard control the PCM level, or somehow swap Master for PCM or make PCM the master volume? Right now, when I change the master volume, my speaker's volume wont change.

edit: since my speakers are plugged into my headphone jack, being able to control the Headphone level would be just as effective.

thanks

---

### Post by markbuntu on 2008-06-17
Just right click on the volume control and go to preferences and choose pcm.

---

### Post by mrmustardman on 2008-06-19
nope, still wont work. It effectivly changed the panel item settings, so if I control the volume with the panel item, it works, but changing it on my keyboard still changes the master. A step forward though. thanks for the reply.

---

### Post by markbuntu on 2008-06-19
Did you try rebooting? A lot of the keyboard defaults are set at boot. 

You can also get keytouch and keytouch editor and use those to make a custom keyboard layout. That may work. There are also a few threads around here about changing the volume and other controls. I had no need for them so I didn't pay much attention...

Try a search..

---

### Post by mrmustardman on 2008-06-20
thanks! I was able to find the keytouch program on synaptic, and I installed it, changed the Amixer volume control to change the PCM instead of the Master, and It works great. Only drawback is that when I change the volume, I dont get the fancy schmancy speaker logo, just a small default-looking meter. Thanks though, this did the trick.

---

