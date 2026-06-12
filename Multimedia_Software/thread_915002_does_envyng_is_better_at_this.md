---
title: "does envyng is better at this?"
date: 2008-09-09
forum: Multimedia Software
---

### Post by syms on 2008-09-09
hi
i heard talks that if i install my ati proprietary driver through envy they will work faster than through restricted driver manager, is this true?

---

### Post by tuxxy on 2008-09-09
envy should select the correct one for you, im not so sure it will fix all errors you experince with your ATI cards as it never did this for me on mine.

---

### Post by syms on 2008-09-09
thanks, i dont have serious problems, but maximise wobble effect lags, i didnt noticed that with open source drivers. so i guess ill try install drivers from envyng tommorow

---

### Post by syms on 2008-09-13
well ive tried it, and i can say that envy didnt work well for me. first of all i get white screen after login, then i pressed alt+f2 and typed metacity --replace, then desktop was fine, but when i ran glxgears i got very low framerate, and fglrxinfo showed me mesa driver. i didnt noticed all of these problems when ive installed driver through restricted manager.

---

### Post by saravanan.2407 on 2008-09-13
I have Nvidia 9600 GT card. On installing Ubuntu it doesnt ask to install Restricted Drivers. I have widescreen lcd monitor and Ubuntu finds the correct resolution and everything looks good except Desktop effects which cant be enabled.
I tried envyng .
I tried Automatic Detection of Hardware option for Nvidia card and it said that the hardware is unknown. (Strange)
But when i tried the manual installation, all went fine and after rebooting i had nvidia driver working.

---

### Post by markbuntu on 2008-09-13
> **syms said:**
> well ive tried it, and i can say that envy didnt work well for me. first of all i get white screen after login, then i pressed alt+f2 and typed metacity --replace, then desktop was fine, but when i ran glxgears i got very low framerate, and fglrxinfo showed me mesa driver. i didnt noticed all of these problems when ive installed driver through restricted manager.

Envy is not the best thing for getting ati drivers. It does not have the latest version and often the driver gets misinstalled, like what happened to you. The best way to get the latest ati driver is here, follow Method 2:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

This is especially important if you are using amd64 Hardy.

---

### Post by syms on 2008-09-13
thank you for answers :)

---

