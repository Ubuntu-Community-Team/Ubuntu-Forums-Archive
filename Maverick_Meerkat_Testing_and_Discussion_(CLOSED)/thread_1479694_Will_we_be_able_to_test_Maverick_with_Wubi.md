---
title: "Will we be able to test Maverick with Wubi"
date: 2010-05-10
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by ToxicBurn on 2010-05-10
just a quick question will we be able to install daily builds of maverick with wubi it will make it easy for me to test this way ?
 
or is it not a good idea to test like that ?
 
 
thanks

---

### Post by philinux on 2010-05-11
> **ToxicBurn said:**
> just a quick question will we be able to install daily builds of maverick with wubi it will make it easy for me to test this way ?
 
or is it not a good idea to test like that ?
 
 
thanks

According to the wubi manual/faq's, if you have wubi.exe and an ubuntu iso file in the same directory it will install it from there.

---

### Post by ToxicBurn on 2010-05-11
> **philinux said:**
> According to the wubi manual/faq's, if you have wubi.exe and an ubuntu iso file in the same directory it will install it from there.
 
 
Thank you very much for your time and help 
 
Im ready to start testing :)

---

### Post by meborc on 2010-05-12
testing with wubi is a good idea - it is easy to install new versions of ubuntu and easy to uninstall without messing with partitions/boot loader

problems could arise when an unstable wubi is used... this could affect your windows install and mess up windows boot loader as wubi edits windows files directly (having a separate partition for ubuntu with ntfs support turned off is more secure way of testing)... just be sure you know how to recover ;)

---

### Post by dino99 on 2010-05-12
dont like Wubi at all, better to use virtualbox

---

### Post by ToxicBurn on 2010-05-12
> **dino99 said:**
> dont like Wubi at all, better to use virtualbox
 
 
what is it about Wubi you do not like ?

---

### Post by meborc on 2010-05-13
> **dino99 said:**
> dont like Wubi at all, better to use virtualbox

testing in virtualbox will not be as good because the hardware is "virtual" :) for example wifi connections etc.

---

### Post by dino99 on 2010-05-13
wubi= linux into a windows file :mad:

do you see where is the bug ? :P

testing with virtualbox is less complicated and more stable. But my testing are all made on a separate partition with real install  :)

---

### Post by meborc on 2010-05-13
> **dino99 said:**
> wubi= linux into a windoz file :mad:

do you see where is the bug ? :P 

testing with virtualbox is less complicated and more stable. But my testing are all made on a separate partition with real install  :)

a year ago i would have agreed with you :) but now... 

wubi is a godsend to all those people stuck with windows machine at work which they are not allowed to partition/format... without wubi, i would be stuck with using windows on my work computer

If you know anything about how wubi works and how ubuntu is initiated from boot, then you know that it is practically the same as install in linux partition file format... the fact that you need windows for wubi is not the "bug"...

testing in virtualbox??? how can you submit bugs? how do you know if the bug is something in the virtualization or the real system?

as you say you test with full partition install, then how can you support virtualbox in this matter? ;)

---

### Post by dino99 on 2010-05-13
i dont like coffee, maybe you like it :confused:

---

### Post by BwackNinja on 2010-05-14
Ubuntu is meant to work in all these scenarios, thus all these scenarios are legitimate for testing. If it doesn't work and its supposed to, its a bug.

---

### Post by garvinrick4 on 2010-05-14
Ubuntu needs Wubi testers a lot of users start Linux by installing Wubi. In testing I would give them the advice to not use Home to save any important files. To uninstall with the uninstall in Wubi folder in C:  and not with Add and Remove programs in Windows so as not
to leave the wubildr in Windows boot manager which Add and Remove will do at times. 
 Have your Windows CD on hand to fix Windows boot if needed, just in case. Learn how to
use your Live CD if problems occur instead of just reinstalling right off the get go.
 To fix a Windows boot is only 2 lines of Code and 1 word lines at that. So do not let that scare anyone off.  Here is a link for that while I am talking about it. When stable it is fine,
I have one machine that I have left with WUBI for 3 years or so just to have a WUBI install to see what is going on and it is the same install. Have fun and enjoy Linux. 

[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708")

---

### Post by VMC on 2010-06-29
> **meborc said:**
> a year ago i would have agreed with you :) but now... 

wubi is a godsend to all those people stuck with windows machine at work which they are not allowed to partition/format... without wubi, i would be stuck with using windows on my work computer

If you know anything about how wubi works and how ubuntu is initiated from boot, then you know that it is practically the same as install in linux partition file format... the fact that you need windows for wubi is not the "bug"...

testing in virtualbox??? how can you submit bugs? how do you know if the bug is something in the virtualization or the real system?

as you say you test with full partition install, then how can you support virtualbox in this matter? ;)
This is an excellent point. People stuck at work and can't re-partition their hard drives for various reasons.

You may have sold me on trying Wubi. I have never tried it, even though I have friends that swear by it. Wubi questions come up all the time and I have no answers. If I installed Wubi then at least I could make some comparisons to the "real" linux installation.

Also, I agree that virtual install does nothing for testing your hardware. Just a look-see at how that distro works.

---

### Post by ranch hand on 2010-06-29
I do not have any MS products so wubi is not needed here.  I think, personally, that it is kind of silly.

That said, Ubuntu supports wubi.  We are testing Ubuntu.  Therefore folks need to test it in a wubi installation.

This has come up, in my knowledge, in the last 2 cycles.  There seems to be a consistent lag between the start of testing and wubi working.

Be patient, I am sure it will be ready to work soon.

---

