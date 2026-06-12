---
title: "Ati x1250 and fglrx"
date: 2008-04-28
forum: Multimedia Software
---

### Post by murlosad on 2008-04-28
So, I've read posts here and on phoronix and a couple other sites saying that people have gotten this card to work with the fglrx drivers. I, unfortunately have had no such luck. I've tried manually installing the drivers, using envy and restricted drivers, and following [this]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide") guide on both 64bit and x86 versions of Hardy.

Ati says that card is supported, but all I get when I install the drivers is my monitor going to sleep. Does anyone here have any advice or has anyone here been able to get this card to work with Hardy? 

I've read every thread I can find regarding this card here for the past month or so to avail.

Thanks guys, any help is appreciated

---

### Post by Solrac924 on 2008-05-01
sorry guy. i'm using an onboard ATI Radeon x1250 also. i'm looking for answers as well. 

upon installation, i had a great resolution. 1280x1024 i think. now, the best i can get is 800x600. :confused:

i dunno WTH went wrong. now, i can't change my monitor nor graphics card. it keeps defaulting to "low graphics". this is getting aggravating!! :mad:

---

### Post by murlosad on 2008-05-01
> **Solrac924 said:**
> upon installation, i had a great resolution. 1280x1024 i think. now, the best i can get is 800x600. :confused:

Mine did that at one point too, it was after I had tried installing the drivers with envy and then uninstalling them. that was when I decided to try using hardy 32bit, so of course my resolution was fine after the install.

have you tried reconfiguring X? dpkg-reconfigure -phigh xorg-xserver.

This is getting frustrating, I just want some desktop effects... :(

---

### Post by Solrac924 on 2008-05-01
Funny, i did the same thing & now everything's good. :)

Sunday is when i did a fresh install of Gutsy. after getting corrupt graphics, i did some updates to the drivers & that's when the resolution "zoomed in". i could not recover my original settings for the life of me.

late last night i updated to Hardy & the screen resolution is perfectly fixed. :guitar:

---

### Post by murlosad on 2008-05-02
> **Solrac924 said:**
> Funny, i did the same thing & now everything's good. :)

Sunday is when i did a fresh install of Gutsy. after getting corrupt graphics, i did some updates to the drivers & that's when the resolution "zoomed in". i could not recover my original settings for the life of me.

late last night i updated to Hardy & the screen resolution is perfectly fixed. :guitar:

Wait, so you have working 3d with this card and Hardy? Are you using the newest ATI driver, and where did you get it from (envy, restricted drivers, etc...) Or are you just saying that you got your resolution back to 1280x1024?

I've been thinking that it could just be a problem with the mobo I have, maybe something to do with the way it assigns memory to the video card, but idk. I'm going to try manually allotting memory and see if it makes a difference. I'm running out of ideas though.

---

