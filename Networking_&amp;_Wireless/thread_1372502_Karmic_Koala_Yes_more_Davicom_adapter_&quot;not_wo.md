---
title: "Karmic Koala Yes more Davicom adapter &quot;not working&quot; issues."
date: 2010-01-04
forum: Networking &amp; Wireless
---

### Post by VMPhil on 2010-01-04
Hello all, Im a long time lurker, first time poster.

So i installed Karmic Koala on my HP mini and obviously the wireless driver does not work from the get go. so instead i decided to try to connect my Davicom (9601 chip) USB to ethernet adapter and then get all the appropriate stuff (NDISwrapper/broadcom driver etc.) through a hardline. yet that is proving difficult as well. 

kernel is 2.6.31-14 The system sees the adapter. i have the driver for it but it will not compile. i keep getting errors on compile. probably as the driver is a touch old. I did a search and read through all of the old threads concerning the davicom adapter. i tried to blacklist the tulip driver that didnt work. I read through the thread that talks about modifying the config.h to modify configfs.h but that only concerns releases prior to mine.

i grabbed this driver [http://ubuntuforums.org/showthread.php?t=869618&highlight=davicom](http://ubuntuforums.org/showthread.php?t=869618&highlight=davicom)

but it completely fails to compile

any suggestions?

---

### Post by VMPhil on 2010-01-05
no one?

---

### Post by changingstate on 2010-01-05
I've done some checking and the davicom module you've linked to won't build and .31 or later due to the kernel devs dropping legacy support for older networking modules ( hence the compilation errors ).

The davicom module WILL build under jaunty's 2.6.28-16 kernel, so there's one possible solution..

I've also gone a bit mad and tried rewriting the module to work with the new kernel. My rewritten version builds and insmods fine on my karmic machine, but I've no hardware to test it against. If you feel brave and fancy trying it, my code is attached. I'll be astounded if it works, but you never know. :)

---

### Post by VMPhil on 2010-01-05
Thanks ill give it a shot. No harm in trying it, worse case scenario is reinstall and this is a fairly fresh build.

---

### Post by VMPhil on 2010-01-06
When i installed the driver, it came up on the networking interface and connected it. now i get internet. not sure what you did to the driver but it worked. Thanks! :KS

---

### Post by changingstate on 2010-01-06
Thanks for the feedback, VMPhil! It's good to know my rusty C coding skills came in handy :)

---

