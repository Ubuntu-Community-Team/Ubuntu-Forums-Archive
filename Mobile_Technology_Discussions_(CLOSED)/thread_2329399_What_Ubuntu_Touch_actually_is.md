---
title: "What Ubuntu Touch actually is?"
date: 2016-07-01
forum: Mobile Technology Discussions (CLOSED)
---

### Post by xflopin on 2016-07-01
So, I just bought Aquaris M10. I watched development of Ubuntu Touch and I was so excited to hear that tablet with Ubuntu is out. I read some reviews a was pretty excited. Looked great, the "Convergence" feature - AWESOME concept! Idea of Ubuntu providing a decent touch experience while still be able to easily switch to full desktop was just hard to resit. I am with desktop Ubuntu since version 6, it always stood out of line. Easy and comfortable to use while still providing full linux experience. With inexhaustible repository of software, my computer was always one command away from becoming webserver, database or whatever I wanted it to be. Even gaming, with more and more premium games available is becoming great experience.
 
I did not expect Ubuntu Touch to be perfect and bugless, I know it is sill in early development, but, apparently, developers decided to create whole new concept of packaging and application environment, repository instantly becoming barren wasteland. You are not even able to use apt-get anymore, the root filesystem is read-only. Why? They say for security reasons. Does that imply that classic Ubuntu is not secure or what? Yes, you can remount the filesystem to be writeable, but be aware, that can break the system, the say! What? Break? What is happening here? I cannot use any (literally, any!) of the software I use on desktop! What is the point of convergence then? Will there ever be a chance to use this reasonably? Or does it mean that we have to wait for each piece of software to be recoded, or at least repackaged? I can't imagine how long would that take.


Ubuntu Touch is obviously trying to mimic concepts of systems like Android and iOS, except it is 10 years behind now. But why? Why would anybody wanted to do that, when you could create a great thing now! Or am I missing something here?


I am really sad, disappointed and angry. Not because I just spent 230 euro for useless thing, but because big chance of creating something unique a wonderful had been thrown away.

---

### Post by angel-granados-j on 2016-07-04
Hi,

The problem is that the x11 are not available for a tactile environment. This has led to them having to develop new graphics servers as Mir (Ubuntu) or Wayland.

This means that programs with graphical environment x11 must be reprogrammed in new environments Wayland and Mir.

To reconcile with x11, both Mir and Wayland supports x11 support. This is the principle of convergence, but is currently still very  green because you have to recompile the packages and the OS itself needs  support.

So on the tablet you have only a few PC applications, which are further modified to run properly on the x11 adapter. All x11 graphics applications that need not be installed in Unity 8 must come precompiled.

I think the arrival of the snappy packages can improve this situation.

You  can make an apt, and all commands that you know, it is the same ubuntu  15.10 that you have on a PC (but with MIR and Unity 8 instead of x11 and  Unity 7), but involves excessive risk so it is only advisable if you are a programmer. This reason is why there filesystem read-only. If you throw commands to trace the rewritable drive you can make.

The problem of a mobile / tablet if there is an error in the system boot is that it can become unusable. A pc can always boot with boot disks, but the mobile / tablet have more danger.

This will succeed with the support of everyone, but it is a time to be what you expected (which I hope will be)

---

