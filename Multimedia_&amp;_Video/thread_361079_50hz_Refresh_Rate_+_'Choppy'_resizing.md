---
title: "50hz Refresh Rate + 'Choppy' resizing"
date: 2007-02-13
forum: Multimedia &amp; Video
---

### Post by Gruelius on 2007-02-13
Hey everyone,
After installing the latest aiglx or whatever they are called nvidia drivers with Beryl my hertz has gone down to 50hz and i cant increase it. I am using two LCD's for which refresh rate should be irrelivant, however i would like to set them to 75 so i can have a faster frame rate without tearing.

My other thing is with Resizing and scrolling it gets a bit choppy, not system speed but the frame looks terrible. Is there a way to force it to update the window faster or something? ill fraps it if i have to however i dont really wanna bother installing fraps.

Ive allways noticed the choppyness on all computers ive put ubuntu on so hopefully i can change it !

Oh yeah im using gnome.

Thanks
Julius

---

### Post by mr.v. on 2007-02-14
have you run ```
nvidia-settings
``` in a terminal to see if the nvidia driver can detect both monitors correctly and is getting their make/model info?

---

### Post by Gruelius on 2007-02-15
Hey,
It gets my model numbers and everything however it says they are CRT's

I set the max refresh rate in the nvidia-settings thing with sudo on however i still get the problem!

Ive also noticed that my cpu usage jumps to 100% when i start resizing windows..

Im going to give XFCE a run.

Also i think im using the GLX drivers no the AIGLX drivers somebody reccomended. Can i be pointed in the right direction?
Thanks

*edit*

XFCE doesnt fix the problem, i might install gentoo to see if i have the problem in that, heh will be fun -.-

---

### Post by mr.v. on 2007-02-15
What version of the nvidia drivers are you using? Where did you get it from? And How did you install them?

Also, can you post your /etc/X11/xorg.conf file in between code /code tags or attach it as a file? Maybe there's something wrong in it and we can look over it to help you fix it.

---

