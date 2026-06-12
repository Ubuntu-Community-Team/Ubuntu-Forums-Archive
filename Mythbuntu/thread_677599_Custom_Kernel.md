---
title: "Custom Kernel?"
date: 2008-01-25
forum: Mythbuntu
---

### Post by jablack on 2008-01-25
I've been thinking about running a custom (Ubuntu) kernel for my Mythbuntu box. I've searched everywhere in dselect (I came from using Debian, so that is naturally easier for me), and can't find the kernel-source for Ubuntu. Where can I find this at? Will I have to recompile LIRC to get it to work with the new kernel? What do you think about running a custom vs. stock kernel?

Thanks.

Jonathan

---

### Post by superm1 on 2008-01-25
In Ubuntu, (especially on a mythbuntu box), if you are going to be using your own kernel, you best have a good reason.

I say this because you will lose all the nice restricted-modules, as well as everything sitting in linux-ubuntu-modules.  This means that you will have to compile lirc, wireless drivers, video drivers, some webcame drivers, and the list goes on depending on what hardware you have.

If you have a working box, as tempting as it is to mess with the innards, you ever heard the expression 'if it ain't broke don't fix it' ? ;)

---

### Post by superm1 on 2008-01-25
To answer your original question however, there are several ways to compile the kernel depending on what you are looking to achieve.

Here's some wikimentation for you to read:

[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

Good luck!

---

### Post by jablack on 2008-01-26
My reasoning for it was speed. I'm running this on an old Pentium III 800 MHZ with 512 MB of RAM, so I need all I can get. Would I get much from compiling the kernel? -- At this point it isn't sounding so enticing, so I might just stick with the stock kernel.

---

### Post by superm1 on 2008-01-26
Honestly, I don't forsee a very large improvement in custom compiling your kernel to your CPU, especially for this amount of effort.

You may however get better performance with some of the other options of kernels shipped with Ubuntu.  Try the -i386 variants rather than -generic.

---

### Post by wizard10000 on 2008-01-26
> **jablack said:**
> My reasoning for it was speed. I'm running this on an old Pentium III 800 MHZ with 512 MB of RAM, so I need all I can get. Would I get much from compiling the kernel? -- At this point it isn't sounding so enticing, so I might just stick with the stock kernel.

You'll get a bigger performance boost by changing the window manager.  Run myth under e16 or e17, xfce or blackbox.

---

### Post by superm1 on 2008-01-26
> **wizard10000 said:**
> You'll get a bigger performance boost by changing the window manager.  Run myth under e16 or e17, xfce or blackbox.
Mythbuntu already runs under xfce :)

---

### Post by wizard10000 on 2008-01-26
> **superm1 said:**
> Mythbuntu already runs under xfce :)

It does?  I didn't know that.

Please carry on.

:)

---

