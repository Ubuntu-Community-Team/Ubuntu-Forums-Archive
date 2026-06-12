---
title: "ossxmix won't save certain mute settings (savemixer)"
date: 2008-10-18
forum: Multimedia Software
---

### Post by theirishfozz on 2008-10-18
Hi everyone. Im using ossmix to control volume settings and in order for the mic to work I have to mute a number of record mixer channels but savemixer wont save these specific settings. It saves main settings like the main mutingof different channels, channel type settings and all volumes so in general it seems ok.

Im using (according to ossxmix) a High definition Audio ALC883, according to lspci Intel 82801H (ICH8 famil) hd audio controller. 

In codec1/record there are two mix sections. Each mix section contains one volume slider and a mute section. Each mute section contains a list of channels: mix, int-mic, blue, int-speaker, headphone, int-speaker, input-mix. savemixer saves changes I make to mic, int-mic and blue, but not to the rest, so every time I restart I have to go in and mute those channels for the mic to work. 

If anyone knows a fix (either a script to manually mute these channels on startup, or some fix to save those settings when savemixer is run) then I would be very grateful!

thanks

Fozz

---

