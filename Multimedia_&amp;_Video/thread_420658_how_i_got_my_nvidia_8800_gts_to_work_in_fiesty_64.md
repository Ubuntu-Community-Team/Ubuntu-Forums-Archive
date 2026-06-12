---
title: "how i got my nvidia 8800 gts to work in fiesty 64"
date: 2007-04-23
forum: Multimedia &amp; Video
---

### Post by eponymous on 2007-04-23
ok so i've tried just about every different method under the sun to get my nvidia 8800 gts to work.
nothing worked as advertised, and that's probably because i'm a linux noob but whatever.

the thing that finally worked the way i had it in feisty beta (did a clean install for release) was pretty ghetto fabulous.

i can't boot into the X server if my bios has the pci-e slot enabled, so i have to boot into recovery mode, run the nvidia driver from the terminal (just download the driver from nvidia.com), then start the gnome desktop.

this, for some reason, gave me no nvidia settings app (it was there but there were no settings available, only the config screen for the settings app itself, strange) so i ran automatix2's nvidia drivers installation and poof! there was my config app the way i remember it. setting up dual display with 2 x servers was point and click from there.

i also tried nvidia-glx-new, automatic through the restricted drivers manager, and envy. and actually i'm pretty sure without each of these components i wouldn't have been able to get to my desktop at one of several crucial points and it wouldn't have worked out in the end.

the lesson is don't give up, it's not always simple and you may not understand it but it'll work eventually!

---

