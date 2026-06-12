---
title: "default audio device"
date: 2007-06-06
forum: Multimedia &amp; Video
---

### Post by nightwulf on 2007-06-06
i have two audio devices nvidia onboard card and cmedia 
i am using cmedia and i manage to configure xmms to use it but i can't configure mplayer and flash palyer plugin for firefox (those 2 are outputing using nvidia card wich is system default)

can anyone help me ?

the system that i am using is kubuntu 7.04

---

### Post by steeleyuk on 2007-06-06
If you are not using the nVidia card at all then you should be able to disable it in the BIOS.

---

### Post by pbw on 2007-06-06
If you don't want to use onboard sound, why not just disable it in bios?

Otherwise you can set default soundcard with alsaconf.

sudo asoundconf list
(it'll list the two names)

sudo asoundconf set-default-card cmedia (or whatever the card is called)

---

