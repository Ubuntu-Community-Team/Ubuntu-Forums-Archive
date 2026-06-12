---
title: "Compiz clipping in asymmetric dual-head with fglrx"
date: 2009-04-18
forum: Multimedia Software
---

### Post by bernerbits on 2009-04-18
Hi...

I'm having trouble getting compiz configured on a new 9.04 xubuntu install. I have a Radeon Mobility HD 3450 card with VGA/HDMI/DVI output. I have a 24" monitor with max 1920x1080 resolution on the DVI and a 19" with max 1440x900 on the VGA.

I installed compiz and emerald from the repositories, and when I tried to run it, it correctly replaced the decorators and rendered the windows, but the larger display is clipped to the size of the smaller display, with strange artifacts in the remaining area: [IMG]http://ubuntuforums.org/attachment.php?attachmentid=110261&stc=1&d=1240106277[/IMG]

If I set the resolution on the larger monitor down to 1440x900 it goes away, and if I configure ATI to ignore the smaller monitor, it works fine at full resolution.

Has anyone else experienced this issue? Is there any way to get around it?[ATTACH]110260[/ATTACH]

---

### Post by markbuntu on 2009-04-19
aticonfig --help is your new best friend.

---

### Post by bernerbits on 2009-04-20
I'm confused. I already did aticonfig for a dual-head setting and it autoconfigured my xorg.conf, and the resolutions are correct and display fine as long as I'm not trying to run compiz.

Or are you suggesting to just try different stuff that comes up in the help dump? Because I'm not exactly seeing a silver bullet.

---

### Post by markbuntu on 2009-04-20
The virtual screen size compiz is using is probably 2880x900 which is your smaller screen x 2 instead of 3840x1080 which is you big monitor x2. There are ways to add a new pairmode and a new virtual screen size but you need to look in the aticonfig --help for examples of that.

---

### Post by bernerbits on 2009-04-25
When I try to do anything with pair mode in aticonfig, I get the following error:

```
berner@berner-desktop:~$ aticonfig --list-pairmode
Error: pair mode is not supported when RandR 1.2 is enabled!
```

---

