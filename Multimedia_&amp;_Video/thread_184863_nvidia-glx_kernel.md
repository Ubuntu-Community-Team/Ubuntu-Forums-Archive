---
title: "nvidia-glx kernel"
date: 2006-05-30
forum: Multimedia &amp; Video
---

### Post by denisesballs on 2006-05-30
Why does upgrading nvidia-glx want to install a different kernel? I'm currently running 2.6.15-23-k7 and it wants to install linux-image-2.6.15-23-386 just to upgrade nvidia-glx. Isn't there one for the k7 kernel?

---

### Post by fragos on 2006-06-01
K7 is tailored for your 32 bit AMD but the i386 works for all 32 bit chips.  I'd doubt you'd notice any difference in performance.

---

### Post by glennric on 2006-06-01
I had this trouble too.  The problem is that nvidia-glx depends on the linux-restricted-modules.  By default it is trying to install the linux-restricted-modules for the 386 architecture.  The linux-restricted-modules-386 package then depends on the linux-image for the 386 architecture and so it tries to install them.  What you need to do is first select the linux-restricted-modules for the K7 architecture, and then select the nvidia-glx package in synaptic.  Then it won't try to install the 386 kernel.

By the way, I have heard many people say that they don't notice much of a difference between the 387 and K7 kernels, but I have noticed a rather significant improvement in speed amond other things after changing to the K7 kernel.  My processor is an AMD Athlon XP+ 2700

---

