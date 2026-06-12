---
title: "Tired of re-installing restricted nvidia drivers after each kernel update :("
date: 2008-11-28
forum: Multimedia Software
---

### Post by crazyfuturamanoob on 2008-11-28
I don't want to every time reinstall & reconfigure my restricted nvidia drivers I got a kernel update.

This is very annoying. Any solution?


And also, some time ago when I tried to fix pulseaudio, I had to install linux-rt kernel image. 

But it isn't needed anymore, so I want to get rid of it, because the update manager keeps downloading large linux-rt kernel updates.

However, when I try to uninstall every rt-thing with synaptic, it refuses. Why?!!?!? I want to uninstall rt kernel.


Thanks.

---

### Post by momo971 on 2008-11-28
> **crazyfuturamanoob said:**
> I don't want to every time reinstall & reconfigure my restricted nvidia drivers I got a kernel update.

This is very annoying. Any solution?


And also, some time ago when I tried to fix pulseaudio, I had to install linux-rt kernel image. 

But it isn't needed anymore, so I want to get rid of it, because the update manager keeps downloading large linux-rt kernel updates.

However, when I try to uninstall every rt-thing with synaptic, it refuses. Why?!!?!? I want to uninstall rt kernel.


Thanks.


Hello.
If you're talking about manually installed NVIDIA-Linux-x86-XXX.XX.XX-pkg1.run drivers you should try this guide :

[http://ubuntuforums.org/showthread.php?t=835573](http://ubuntuforums.org/showthread.php?t=835573)

I've been using it for months and it worked great.


For your kernel issue you should try to install linux-generic.
I hope this help.

---

### Post by crazyfuturamanoob on 2008-11-28
Sorry double posted this topic due to laag at ubuntuforums.
It said "service temporary unavailable blablabla" and I posted this twice, 'cause I thought previous post didn't work.

---

### Post by crazyfuturamanoob on 2008-11-28
> **momo971 said:**
> 
For your kernel issue you should try to install linux-generic.
I hope this help.

I already have it. When I try to uninstall rt kernel, it forces me to install newer version of rt kernel.

---

