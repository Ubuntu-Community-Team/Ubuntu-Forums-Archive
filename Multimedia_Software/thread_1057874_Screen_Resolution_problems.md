---
title: "Screen Resolution problems"
date: 2009-02-02
forum: Multimedia Software
---

### Post by abovenewbi on 2009-02-02
I have Ubuntu 8.4 install on my desktop ( I love it!) 
The resolution is huge! when i go to system -> Preferences -> screen resolution
this is what i get:
1024 x 768
832 x 624
800 x 525
and so on.....
320 x 175

everything on my screen looks huge, I'm using 1024 x 768, if i go lower than this then the bigger it gets

I created another user and was very surprised to see the resolution worked perfectly in that user...
after looking in google, I learn't about the xorg.conf file, i printed this file out in the new user account and on the old user account(resolution not working) and both files were identical


any ideas?

---

### Post by xc3RnbFO8P on 2009-02-02
In Terminal:
> gksu displayconfig-gtk
choose Generic
and resolution that your monitor supports

---

### Post by rogier.de.groot on 2009-02-02
No big surprise, the screen solution tool has sucked for ages. If you've got an nvidia card and are using the nvidia driver (the restricted one) just install nvidia-settings, and use that to configure your resolution. There's probably a similar tool for ati cards (not sure). Otherwise I suggest using an older release (before that damn 'auto-misconfiguring' stuff) and copying it's xorg.conf file.

---

