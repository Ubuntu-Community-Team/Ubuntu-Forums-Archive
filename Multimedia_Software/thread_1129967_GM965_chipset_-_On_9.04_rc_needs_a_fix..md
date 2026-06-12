---
title: "GM965 chipset - On 9.04 rc needs a fix."
date: 2009-04-19
forum: Multimedia Software
---

### Post by hackercoolio on 2009-04-19
i recently downloaded 9.04rc cuz i saw there was an update on xerver and xorg drivers anyways.. installed it and updated all the packages!

Nothing works now = Ubuntu crashes more often.. Compiz Dosen't work. just the the basic desktop effects.. 

when you try to go for advance effects.. ( looking for drivers then an error pops up saying desktop effects are not supported.)

Specs : Dell 1525 Inspiron - Gm965 Chipset - Integrated graphics x3100 - 


Quintuple booting :D

Under Grub: (GfxGrub :D)
              
* Vista Loader :
*---------Ms Windows xp pro sp3.
*---------Ms Windows 7(7000)(Cracked)

* Ubuntu 9.04 - Jaunty

* Mac OS X 10.5.6

* Open Solaris

---

### Post by rhewt on 2009-04-19
Yeah, I have this problem too. I did a fresh install of 9.04 on my inspiron 1420n laptop that also has an intel GM965 x3100 and I can't get desktop effects working. I'm researching if there is a current work-around, I'm sure there will be a permanent fix soon as this is a popular integrated vid card.

---

### Post by _gpf_ on 2009-04-19
I have been using Jaunty since Alpha5, and I, too, have a Dell with X3100 graphics.  The desktop effects were working up until the most recent update to the RC packages.  

I had read that there were some issues with random freezes/lockups with the xorg intel driver...  has it been axed for now in RC?

---

### Post by cariboo on 2009-04-20
Have a look [here]("http://www.ubuntu.com/getubuntu/releasenotes/904"), under Other Known Issues.

Jim

---

### Post by _gpf_ on 2009-04-20
Thanks for your quick reply, cariboo907.  Unfortunately, none of these worked for me.  After attempting all the workarounds listed on that page, I still get the same result as the original poster.  When I attempt to enable advanced effects via System -> Preferences -> Appearance, it "Searches for Drivers" and then says the effects cannot be enabled.

This is truly strange since it worked just fine up until about Saturday morning when I did and apt upgrade after the RC was released.

---

### Post by _gpf_ on 2009-04-20
I was able to get this working by adding

```
SKIP_CHECKS=yes
```

to 

```
~/.config/compiz/compiz-manager
```

per the Compiz Wiki.  Hope that helps!

---

### Post by Guranic on 2009-04-21
Worked. Thanks. (I had to create the file compiz-manager.)

---

