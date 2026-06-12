---
title: "ATI Rage128- cannot get dualhead"
date: 2006-07-24
forum: Multimedia &amp; Video
---

### Post by info2 on 2006-07-24
Hello.

i have an older Laptop (PIII-600) with a graphiccard detected as :

0000:01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage LT Pro AGP-133 (rev dc)


The Laptop have an external VGA-Connector where i connected a TFT-Display.

Now i want to use DualHead - Display, but i cannot make it working. Whatever i do (trying many howto's), i always get the similar content on booth screens (cloned).

So i wonder if the current "ati" / "r128" - driver isn't able to use dualhead or if my card doesn't support it.

Somebody know something more about that? Is there a way to find out if the graphiccard support dualhead?

What's that "mergedFB"-thing i read about somewhere?

Thank you for every answear :)

-tf-

---

### Post by FlyingCheese on 2006-07-24
I don't know if this helps at all but my desktop version of Rage128 Pro doesn't support dual-head (only 1 VGA Port), so I would assume it is the same for the mobile one.

---

### Post by patrick295767 on 2006-07-24
> **info2 said:**
> Hello.

i have an older Laptop (PIII-600) with a graphiccard detected as :

0000:01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage LT Pro AGP-133 (rev dc)


The Laptop have an external VGA-Connector where i connected a TFT-Display.

Now i want to use DualHead - Display, but i cannot make it working. Whatever i do (trying many howto's), i always get the similar content on booth screens (cloned).

So i wonder if the current "ati" / "r128" - driver isn't able to use dualhead or if my card doesn't support it.

Somebody know something more about that? Is there a way to find out if the graphiccard support dualhead?

What's that "mergedFB"-thing i read about somewhere?

Thank you for every answear :)

-tf-
  
Hi, 

Do you have glx acceletino with you card ?
If yes, sounds good.
  
In case, you cannot make it with Xorg, I use now XFree86 with Ati rage, and that gives better results than xorg. 
  
Look the warty distro wiht xfree86, they certainly could make it the acceleration and I am rather sure too with dualhead. I will try that one day ... but still dont know when I'll have time. 

Cheers

---

