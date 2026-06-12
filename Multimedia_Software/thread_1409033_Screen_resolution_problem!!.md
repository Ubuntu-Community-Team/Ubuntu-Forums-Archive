---
title: "Screen resolution problem!!"
date: 2010-02-17
forum: Multimedia Software
---

### Post by slappadudle on 2010-02-17
Hi there. New to Linux but loving it so far!!

Ubuntu identified my Dell Studio 17 laptop specs right out the box but today I plugged my TV into my HDMI port so I could watch a movie from my computer (it prompted me to change the resolution but of course I assumed I would be able change it back!). Since then it's been stuck on 1280x720 which seems to be the highest resolution available in Display Preferences now!!

I found some answers which involve adding code to /etc/X11/xorg.conf but I don't know what code to add AND my file is read-only. I *think* my screen is 1440 x 900 but I'm not certain..

What should I do?

---

### Post by chewearn on 2010-02-17
Could you please post output from:
```
lshw -c display
```

and
```
lspci -nn | grep VGA
```

This will tell us the which graphics processor you have.

---

### Post by slappadudle on 2010-02-18
Hi chewearn, thanks for your response. Here's the output:


**$ lshw -c display**
WARNING: you should run this program as super-user.
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: Mobility Radeon HD 3650
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:e0000000-efffffff(prefetchable) ioport:ee00(size=256) memory:f6df0000-f6dfffff memory:f6d00000-f6d1ffff(prefetchable)

**$ lspci -nn | grep VGA**
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Mobility Radeon HD 3650 [1002:9591]

---

### Post by slappadudle on 2010-02-18
umm so what do i do next?

---

### Post by chewearn on 2010-02-18
I'm sorry, I don't know about fixing ATI graphics problem.  I would have to defer to someone else with knowledge of ATI.

---

### Post by slappadudle on 2010-02-24
Anyone? My screen still looks terrible!!!

---

### Post by Little Ghost on 2010-02-24
UP! Also with an ATI graphic card (ATI hd 5470)

---

### Post by FeTTo on 2010-02-24
i had this problem with the new 9.10 too. my resolution gets all funky after plugging it into my DLP. are you using the function + Display key? on my dell its Func + F8. if id unhook it while in that mode my laptop would still be in the resolution for the external display and look terrible. Id have to plug it back into the tv and cycle through the crt, crt + laptop, laptop settings on the actual laptop to get it back to the right settings. i hope this makes sense to you hah. works for me.

---

### Post by slappadudle on 2010-02-24
Thanks for your input FeTTo.

That does make sense and i am trying it but still no luck, the resolution I want is not available in the list even after cycling through the modes with Fn & F8.

What do I doooooooo???? I need more pixels than this :(

---

### Post by slappadudle on 2010-02-24
FIXED.

I got the right driver from AMD's website and install it. Done.

All this hassle simply because I plugged my TV in to my laptop!?!?!?!?

---

