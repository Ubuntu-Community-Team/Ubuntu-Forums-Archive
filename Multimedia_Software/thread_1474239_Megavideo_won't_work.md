---
title: "Megavideo won't work"
date: 2010-05-05
forum: Multimedia Software
---

### Post by manda417 on 2010-05-05
Hey guys,

Just wondering if anyone else has the same problem--  can't watch videos on Megavideo. Hulu, dailyshow.com, youtube, all other video streams work fine. Flash games work fine too. When i try to click the red play button when megavideo loads, it says it's transferring data but then nothing happens.

Any help someone could give would be great!!

Manda
Ubuntu 10.04

---

### Post by japsai on 2010-05-06
Same here

---

### Post by nemixer on 2010-05-08
same here. 
Lucid 64-bit

---

### Post by jontxudino on 2010-06-02
i dont get the transferring data thing... i just cant click on anything. i click on the red button and i can see it moving but no action.
10.04 64 bit

---

### Post by piotrs on 2010-06-03
The solution of this problem (found somewhere on ubuntuforums):

1. Press ALT+F2 and enter:
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer

2. Add the following line before the last line in the file:
export GDK_NATIVE_WINDOWS=1

3. Save and restart Firefox, or if this doesn't fix it, try restarting Ubuntu.

---

### Post by nos676 on 2010-07-14
it worked perfectly, thanks
i also use x64 lucid lynx

---

