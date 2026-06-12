---
title: "PPPOECONF modconf problems + DLINK DE220 Driver"
date: 2005-12-27
forum: Networking &amp; Wireless
---

### Post by Jeff12088 on 2005-12-27
Hello,

I've just got Ubuntu displaying and mouse working, now I'm trying to get it connected to Internet.

The ethernet card I am using it DLINK DE220. It is a very old chipset and DLINK no longers supports it and I too have no drivers. Any help finding the driver?

---

### Post by Jeff12088 on 2005-12-27
Bumpy bump

---

### Post by Jeff12088 on 2005-12-28
No help anyone? :(

---

### Post by mips on 2005-12-28
[http://www.petersblog.org/tags/2?from=50](http://www.petersblog.org/tags/2?from=50)  See "**Hello from Ubuntu**"

also found this

[http://www.uwsg.iu.edu/hypermail/linux/net/9909.2/0051.html](http://www.uwsg.iu.edu/hypermail/linux/net/9909.2/0051.html)

You might also have to play around with the ACPI & APIC setting in the GRUB loader as I'm asuming it is a old pre-pnp ISA card but try the above first.

---

### Post by Jeff12088 on 2005-12-28
I tried the method in Peter's Blog but doesn't work:
"FATAL: Error inserting ne (/lib/modules/2.6.12-9-386/kernel/drivers/net/ne.ko): No such device or address"
I tried looking and the ne.ko does exist under the same exact address, so don't know what's the problem.

The same problem occurs when I try the second link ;) 
The second link tells me to get a file called ne.c but the link is broken :???:

---

### Post by Jeff12088 on 2005-12-29
I recieved more information that D-Link DE220 is a ISA network card.
and I also read that I need to do some activating or configuring in my BIOS to enable the plug in and play setting.
How would that work?

P.S.  I have an Award BIOS

---

### Post by yyagol on 2005-12-30
My advice :  buy a new card it is not expensive (10$)

---

### Post by Jeff12088 on 2005-12-30
Yup, still looking for suggestions, [http://ubuntuforums.org/showthread.php?t=109183](http://ubuntuforums.org/showthread.php?t=109183)

---

