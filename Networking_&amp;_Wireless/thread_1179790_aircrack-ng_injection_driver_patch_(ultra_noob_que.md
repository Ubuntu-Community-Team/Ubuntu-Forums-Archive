---
title: "aircrack-ng injection driver patch (ultra noob question)"
date: 2009-06-06
forum: Networking &amp; Wireless
---

### Post by unmole on 2009-06-06
i have a broadcom card with b43 driver installed on jaunty. I tried to inject packets and failed..........Do I have to patch the driver or the kernal in order to be able to do this ?

---

### Post by redspider on 2009-07-04
driver.
"iwconfig"  in a terminal 
so you know which one to get.




iwconfig - checks a bunch of wireless settings. best friend when figuring out wireless problems.

---

### Post by Crafty Kisses on 2009-07-04
Depending on what kernel you have you may not even need the Injection driver patch. If you're using kernels 2.6.24 or 2.6.25 then you need the patch. If you have a kernel later than the mentioned, you don't need to have the injection patch. If you're not sure what kernel you have, go into the Terminal and type:
```
uname -r
```
Now if you're wondering on how to apply the patch once you have downloaded the injection patch, you can just simply run:
```
patch -p1 -i b43-injection-<2.6.24>.patch
```
I'm just guessing you're using the "2.6.24" kernel. Then that should apply the patch and you should be ready to go. Once you applied the patch you should probably see if you're running the new patched module, so you can run in a Terminal:
```
modinfo b43
```
That will tell you some details about the new module and what not. In all honesty though, I don't even think this patch applies to you, because you probably have a newer kernel.

---

