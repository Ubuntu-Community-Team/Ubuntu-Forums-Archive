---
title: "Anyone else try 2.6.37-2 yet?"
date: 2010-11-04
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by autocrosser on 2010-11-04
Just got 2.6.37-2 x86-64 & as far as I can get in either normal or recovery mode is GDM--system locks up hard right about the time I try to select the session user...Anyone else seeing this?

---

### Post by dino99 on 2010-11-04
installed on my end:
- i386
- nvidia (x-swat)

no issue and my fans are noiseless :)
but still acpi conflict, hest table not found (like the previous kernels)

---

### Post by kerry_s on 2010-11-04
i show it as new in repository, which usually means it's not ready, something missing.

---

### Post by dino99 on 2010-11-04
> **kerry_s said:**
> i show it as new in repository, which usually means it's not ready, something missing.

its the meta-package, so nothing important.

---

### Post by kerry_s on 2010-11-04
> **dino99 said:**
> its the meta-package, so nothing important.

so you guys are just jumping ahead of the updates. :)

---

### Post by meborc on 2010-11-04
> **kerry_s said:**
> so you guys are just jumping ahead of the updates. :)

Even pre-alpha ubuntu is not bleeding edge enough for some people :P

---

### Post by ronacc on 2010-11-04
2.6.37-2 64bit boots ok on my AMD64/Nvidia box , I'm set for auto-login with a 10 sec delay and just let it auto-login I didn't try selecting a new session , it did seem to pause for a sec or 2 about 3/4 of the way through the timer on the login screen .

---

### Post by Killigrew on 2010-11-04
2.6.37-2 from xorg-edgers with Radeon R500 no problems so far :)

---

### Post by cecilpierce on 2010-11-04
works fine but the boot time went way up, about 30 secs.

---

### Post by autocrosser on 2010-11-04
> **ronacc said:**
> 2.6.37-2 64bit boots ok on my AMD64/Nvidia box , I'm set for auto-login with a 10 sec delay and just let it auto-login I didn't try selecting a new session , it did seem to pause for a sec or 2 about 3/4 of the way through the timer on the login screen .

Hmmmm--I used my old install--guess that I need to boot my new install & check--

Meborc---it showed as ready to install in Synaptic for me. so I pulled it in...........not using xorg-edgers PPA---am using the main repo.

---

### Post by sgage on 2010-11-04
Seems to be working fine for me, though I also notice an increase in boot time.

- i386
- NVIDIA proprietary drivers (260.19.06)

---

### Post by plun on 2010-11-04
No problems at all as I can see.... was already running RC1 from Ubuntu Mainline.

Xorg-edgers and X-swat enabled.

nVidia driver 260.19.12 running with excellent performance.

---

### Post by autocrosser on 2010-11-04
Hmmm--OK, I'll run it on my new install & see if  its my hardware or just cruft in my old install causing the problem.......

---

### Post by gnomeuser on 2010-11-04
with the Lucid configuration I had working USB connected DVD drive, in Maverick it was detected by the kernel but not made available correctly to user space.. with .37 we are now down to not even registering when I plug it in.

*sigh*

I believe this is what would normally be called.. wrong.

---

### Post by plun on 2010-11-04
> **autocrosser said:**
> Hmmm--OK, I'll run it on my new install & see if  its my hardware or just cruft in my old install causing the problem.......

Well.... long time ago since I reinstalled....;)

I bought myself a SSD disk in June and since then it has been rock solid during Maverick and now Nattys development.

Noticed that suspend is broken with the 2.6.37 kernel with my laptop....(wait and see)

---

### Post by scradock on 2010-11-05
> **plun said:**
> Well.... long time ago since I reinstalled....;)

I bought myself a SSD disk in June and since then it has been rock solid during Maverick and now Nattys development.

Noticed that suspend is broken with the 2.6.37 kernel with my laptop....(wait and see)
2.6.37-2-generic kenel is working for me, AMD64.

I've been having suspend problems with 2.6.36-1, but I only checked using the lid switch. Screen blanks, but fans never stop, and no resume.

With 2.6.37-2 suspend works from the menu, including resume........

I'll send this before checking the lid switch.....

Checked - suspends and resumes fine using the lid switch with 2.6.37-2-generic!

---

### Post by autocrosser on 2010-11-05
Well--I updated again this morning & Lo---my old install boots from the new kernel...Like the old man that it is (Lucid testing updated thru Maverick & now Natty), must have been cranky about new toys :P:P

My new install (Unity desktop testing) booted it without a problem one...

---

### Post by cipherboy_loc on 2010-11-05
I am using 2.6.37-2 through the launchpad repositories, along with x-swat on my Maverick install. I have to say it actually boots faster than my other linux image (2.6.35-22-ck-generic). Running on an old Dell laptop (i686). ATI Radeon graphics.


Cipherboy

---

### Post by dino99 on 2010-11-05
for the first time, i get swap disk not mounted/ready when the system load plymouth: might be a race somewhere or my hdd too slow now (seagate 7200-7)

---

### Post by gnomeuser on 2010-11-05
There is a fairly easy to trigger crash in this one with my USB Ralink Technology, Corp. RT2501/RT2573 Wireless Adapter (rt73/rt2x00lib). I am trying to get a proper snapshot of the trace for a report but at least people might want to be a bit careful.

---

