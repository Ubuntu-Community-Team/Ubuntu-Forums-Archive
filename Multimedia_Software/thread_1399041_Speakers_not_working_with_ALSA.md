---
title: "Speakers not working with ALSA??"
date: 2010-02-05
forum: Multimedia Software
---

### Post by muffinboy on 2010-02-05
I have an HP-dc5800 computer, and my internal speaker was not working, no matter what i did. However, i could get sound with headphones. 

Here is what i did to fix it. It may work for you.


*sudo gedit /etc/modprobe.d/alsa-base.conf*


Add 
options snd-hda-intel model=hp-m4 enable_msi=1

to the end of the file. I changed model=hp-m4 to model=hp-dc5800. So,
changing the model to the model of your computer may work.

Underneath that, i put in;

options snd-hda-intel enable=1 enable_msi=1 single_cmd=1 power_save_controller=1


reboot, and sound worked fine.


Hopefully this will help someone.


<3

here is a list of some of the models.
[http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt](http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt)

---

### Post by morgue on 2010-04-12
The headphones jack works for me, but have you gotten the speaker to work?

---

### Post by Ollytheninja on 2010-07-11
Try system -> preferences  -> sound  -> Output tab
and try different options from the connectors dropdown menu

---

