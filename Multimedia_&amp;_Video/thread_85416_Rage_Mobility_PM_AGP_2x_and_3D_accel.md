---
title: "Rage Mobility P/M AGP 2x and 3D accel??"
date: 2005-11-02
forum: Multimedia &amp; Video
---

### Post by herot on 2005-11-02
i have this card: 
Rage Mobility P/M AGP 2x (rev 64)
(mach64???)

anywayz i want to know how to get 3D acceleration to work with it...
im using the "ati" driver in my xorg.conf and getting like 118 fps with glxgears...
all the gl screensavers run horribly and i want to be able to use gl with mame and some other programs...

i found some threads discussing this in the warty releases but i dont know if they are still valid for breezy...
my card is said to support 3D here:  [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards)

any help would be appreciated...

---

### Post by TopPretender on 2005-11-07
can someone help solving this problem please? i have the same issue! thanks

---

### Post by ranf on 2005-11-07
[QUOTE=herot]i have this card: 
Rage Mobility P/M AGP 2x (rev 64)
(mach64???)

anywayz i want to know how to get 3D acceleration to work with it...
[/QUOTE]
I'm not sure if compiling DRI kernel modules is still needed. 
Give it a try:
[http://ubuntuforums.org/showthread.php?t=7200&highlight=mach64](http://ubuntuforums.org/showthread.php?t=7200&highlight=mach64)

---

### Post by herot on 2005-12-02
glxinfo | grep "direct"


it says "direct rendering: no",

even after following the howto instructions perfectly...

---

### Post by ranf on 2005-12-02
[QUOTE=herot]glxinfo | grep "direct"

it says "direct rendering: no",

even after following the howto instructions perfectly...[/QUOTE]
Which files exactly did you download?

edit:
I recompiled my DRI drivers last week. I followed this HowTo (it is more up to date):
[http://ubuntuforums.org/showthread.php?t=75393](http://ubuntuforums.org/showthread.php?t=75393)

(just replace savage with mach64)

---

