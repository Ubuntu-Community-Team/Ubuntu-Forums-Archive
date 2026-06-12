---
title: "New kernel  not used by system"
date: 2011-01-29
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Quackers on 2011-01-29
In my main Natty install I updated to the new kernel this afternoon. All was well after rebooting and the new kernel is now being used by the system.
In my other Natty install, I've just updated to the new kernel, and although synaptic reports all aspects of the kernel are installed, the system won't use it! It's still showing 2.6.37-12 as being used. This happened once before with this particular installation but just for a couple of days. Then, for some reason, it started using the newer kernel.
Any ideas why that might happen?
Thanks.

---

### Post by arpanaut on 2011-01-29
If you have multiple installs of linux on the same computer boot into the install that controls grub and update grub.
Obvious, yes,  but sometimes on multi-boot systems we forget which grub.cfg we are using.

Shot in the dark, but hey, it's late...

---

### Post by nm_geo on 2011-01-29
> **arpanaut said:**
> If you have multiple installs of linux on the same computer boot into the install that controls grub and update grub.
Obvious, yes,  but sometimes on multi-boot systems we forget which grub.cfg we are using.

Shot in the dark, but hey, it's late...

+1 I was just about to type that but Quackers you know that LOL

---

### Post by Quackers on 2011-01-29
Thanks people :-)
I actually thought I had done that, but with 4 different grubs I must have updated the wrong one! N0ob!
All fixed now :-)

---

### Post by nm_geo on 2011-01-29
> **Quackers said:**
> Thanks people :-)
I actually thought I had done that, but with 4 different grubs I must have updated the wrong one! N0ob!
All fixed now :-)

I totally understand Quackers.  I sometimes forget how many installs i have on this one poor old computer and which is my primary boot.

---

### Post by Quackers on 2011-01-29
Lol, it's an occupational habit :-)

---

### Post by arpanaut on 2011-01-29
LOL, Yousewelcome!
I figured it was a brainfart... 

At present I have 5'buntus, and a Win installed on a mixture of 2 pata and 2 sata drives and never know in which order the system is going to mount the drives so I am extra observant of which grub is in charge and which drive to install grub to. ( Thank goodness for UUID"s)

Keeps me on my toes, never a dull moment, especially in testing.

---

### Post by Quackers on 2011-01-29
Lol, I've got a foolproof method! Honest! Well nearly foolproof :-)
I have 4 Ubuntus and each grub is set up differently.
My Lucid is absolutely standard (no splash screen, standard text size)
My Maverick is standard, except for smaller text on the grub screen
My 2 Nattys have different splash images and smaller text.
So, as you can see, foolproof! 
Until the fool using it forgets which is which :wink:

---

### Post by arpanaut on 2011-01-29
> so, as you can see, foolproof! 
Until the fool using it forgets which is which :wink:+1 too true!

---

