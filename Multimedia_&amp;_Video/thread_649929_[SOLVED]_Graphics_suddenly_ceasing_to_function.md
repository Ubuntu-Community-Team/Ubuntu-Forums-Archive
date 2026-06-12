---
title: "[SOLVED] Graphics suddenly ceasing to function"
date: 2007-12-25
forum: Multimedia &amp; Video
---

### Post by SamsLembas on 2007-12-25
First of all, here is my grapihcs setup:
Card: GeForce 8600
Monitor: HP w2207


When I installed Ubuntu Gusty, everything worked perfectly. It asked me if I wanted to use the proprietary nVidia drivers, I said yes, and it was flawless, including for playing games. Since then, I have had no problems and never so much as touched my xorg.config.

Today, I plugged in my new Logitech G9 mouse. It was not recognized by Ubuntu, which was rather weired, but I just thought whatever and rebooted to Vista to get the special features customized before worrying about that. When in Vista, the only software update I gave it permission to do was a Java one that should have no effect on this. But you know Vista, anything could have happened. I do not boot into it much, so if there was any graphics updates, they probably installed.

When I booted back to Ubuntu, X failed to start. I got the GUI error message, but the GUI was off the side of the screen and pretty much unusable (so much for fail proof). My initial reaction was "Wow, didn't know a mouse could do this." I unplugged my mouse and rebooted, and the error stayed. Booting from the LiveCD yielded the same result.

Needless to say, I am very confused as to what happened here. Did that mouse somehow cause all of this? Did Vista install a graphics update that did something? (I tried searching the forums under the assumption that it would be all over if this was the case, but no such luck)



Thanks in advanced, and merry Christmas.

---

### Post by SamsLembas on 2007-12-25
bump

---

### Post by SamsLembas on 2007-12-25
I tried booting from my LiveCD again and found that it does work. Don't know what was going on last time.

I think that the problem is with the nVidia drivers. When booting up, the nVidia splash appears several times before bringing me to the error message. Is there any way I can reset the nVidia drivers to the default setting or something?

---

### Post by SamsLembas on 2007-12-25
SOLVED (Yaaa!)

For anyone with the same problem:
The trick was to run dkpg-reconfigure xserver-xorg and pick the free drives (nv). Once the system is up again, you can use restricted drivers manager to switch back the the non-free ones. I don't know why this work, but I am just happy that it does ;)

---

