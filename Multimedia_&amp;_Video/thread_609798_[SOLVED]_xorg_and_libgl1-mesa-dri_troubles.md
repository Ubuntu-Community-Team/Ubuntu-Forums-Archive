---
title: "[SOLVED] xorg and libgl1-mesa-dri troubles"
date: 2007-11-11
forum: Multimedia &amp; Video
---

### Post by karvec on 2007-11-11
Looking at what I've searched for, there doesn't seem to be alot of support with XOrg and OpenGL drivers...  So, here's the story...

When I first installed, I ran tremulous just fine.  No problems whatsoever...  Then for a programming assignment in C, I had to compile an opengl program.  So I went ahead and downloaded libgl1-mesa-dev and lah dee dah installed fine.  No problems.  *BUT*!!!!  Tremulous didn't work anymore, and for some odd reason "dri" is not being used anymore...  (The direct rendering interface or whatever the technical term is...)  I've googled this countless times, but I've had no luck in turning *ANYTHING* up...  I've tried uninstalling libgl1-mesa-dev, and anything else I could find related that wouldn't remove xorg...  No luck.  I even used an earlier xorg.conf that I had-- no luck...  (Learning the console a bit better, though, that darned GUI didn't start a couple times.  ;))

So, anyways, I've also removed tremulous, rm -rf .tremulous in the home directory, cleaned it out from synaptic, and still no luck.  I don't know what to do anymore, I've tried adding:

Load "dri"

in xorg.conf and no luck either....

What can I do?  I have a feeling that it'll eventually end up as a reinstall, but just thought I'd ask before I lose all my custom configurations.  I'm really used to reinstalling windows to the default system, because windows just managed to kill itself over time anyways.  The windows default system isn't bad, and the Ubuntu base install is definitely not bad!!  But having compiled several programs from source and customizing the voltages using Linux-PHC and just the tiny little tweaks that make you feel good and that sense of accomplishment--  I don't want to lose all that.  :P  Please let me know if anyone has had the same problem...


Thanks so much for being a great community, Ubuntu...  This OS is definitely a piece of work and I appreciate all the time that everyone has donated to make it what it is.  Humanity to others, for sure.


~~Karvec

---

### Post by karvec on 2007-11-11
Forgot to add that my graphics card is integrated intel, what I could find on it:



Graphics Processor / Vendor
    Intel GMA 950
Video Memory
    Dynamic Video Memory Technology 3.0 


and

Processor

Processor
    Intel Core 2 Duo T5500 / 1.66 GHz
Multi-Core processor technology
    Dual-Core
64-bit processor
    Yes
Data bus speed
    667 MHz
Chipset type
    Mobile Intel 945PM Express



If you want more info, it's an Acer Aspire 5630-6288...

---

### Post by karvec on 2007-11-12
Well, sorted it out a little tiny bit by using part of my other configuration from another xorg.conf file...  I believe it was a backup.  So semi-fixed.  Now, the fonts are completely skewed and tremulous looks really funny...

---

### Post by karvec on 2007-11-12
*bump*

Does anyone know how to fix the fonts, or should I run the liveCD and try to use the xorg.conf generated from that?

---

### Post by karvec on 2007-11-13
*bump* again...  Anyone have the problem of skewed graphics in fullscreen OpenGL applications?  And how to fix them?

---

