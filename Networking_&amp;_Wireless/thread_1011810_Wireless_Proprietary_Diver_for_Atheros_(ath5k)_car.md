---
title: "Wireless Proprietary Diver for Atheros (ath5k) card missing"
date: 2008-12-15
forum: Networking &amp; Wireless
---

### Post by The Judderman on 2008-12-15
Dear All,

I had my wireless working perfectly having followed this [thread]("http://ubuntuforums.org/showthread.php?t=967855") when I upgraded to Intrepid.

However after a recent "security" update (I didn't register completely what it was), I've lost the ath5k driver in the hardware driver manager, so can't connect to wireless via that driver. I've got it working with madwifi, but with not with WPA (so using WEP at the mo).

Any ideas? Anybody had the same problem?

Thanks

---

### Post by mdhunn on 2008-12-16
Try adding ath5k to the /ect/modules file.  I had to do somthing simular with my laptop using ath9k.

---

### Post by mdhunn on 2008-12-16
Another thing to consider is that kernal modules must be compiled for the specific version that you are using, if the magic number embedded in the module doesn't agree with the kernal the module will not run.  In grub try loading the *pre* update kernal; if your wireless works that's your problem.

Fortunately compiling a new module for your kernal is easy;)

Just point your browser to [http://wireless.kernel.org/](http://wireless.kernel.org/) and look in the users section.

---

### Post by The Judderman on 2008-12-16
> **mdhunn said:**
> Try adding ath5k to the /ect/modules file.  I had to do somthing simular with my laptop using ath9k.

DId that but it didn't make any difference. How do I recompile the module for the kernel, and how do I know which one for which kernel?

I've been on Ubuntu a little while, but still need a lot of guidance!

Thanks for your time!

---

### Post by The Judderman on 2008-12-16
> **mdhunn said:**
> Another thing to consider is that kernal modules must be compiled for the specific version that you are using, if the magic number embedded in the module doesn't agree with the kernal the module will not run.  In grub try loading the *pre* update kernal; if your wireless works that's your problem.

Fortunately compiling a new module for your kernal is easy;)

Just point your browser to [http://wireless.kernel.org/](http://wireless.kernel.org/) and look in the users section.

The kernel I've got is 2.6.27-7-generic. I don't have an option on my grub menu to pre load. The only options I have are 2.6.27-generic and recovery

Any further thoughts?

---

### Post by mdhunn on 2008-12-16
Make sure that you have build-essential and the kernal headers.  When you compile, the compiler uses the headers as a reference when building for your kernel.  So if your build system is ok it will compile the modules specifially for your kernal.  But be prepaired to recompile the next time you have a kernal update.  
When that happens go back to the folder where you put the modules sourse and run "make distclean" then comple normally.  

Also I'm pretty religous about applying security updates and my kernal is 2.6.27-9.  Check to make sure your security updates applied fully.  You might also want to install the start up manager, it will give you the option of keeping previous kernals in grub.

---

### Post by The Judderman on 2009-01-01
Thanks for your help..

In the end I've gone for a drastic solution. I've reinstalled intrepid, did all the updates with a wired connection, and only then installed linux-backports-modules-intrepid. Interestingly, it also installed linux-backports-modules-linux-2.6.27-9, which is my current kernel!

And it all works beautifully... Not sure if I'll be able to resolve the problem if it arises ok, but for now, i'm surfing WiFi!

Thanks MdHunn for your time!

The Judderman

---

