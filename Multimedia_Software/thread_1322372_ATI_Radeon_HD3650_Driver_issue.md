---
title: "ATI Radeon HD3650 Driver issue"
date: 2009-11-10
forum: Multimedia Software
---

### Post by Crash~Override on 2009-11-10
Hey guys, I seem to be having some issues with my graphics driver on ubuntu.

I have a radeon hd 3650 512mb ddr2 graphics card. It works great on windows 7. But on ubuntu partition i get a lot of lag when i play videos. And overall performance is just not smooth enough. 

Has anyone else had this problem and/or have a fix for this?

---

### Post by alphacrucis2 on 2009-11-10
> **Crash~Override said:**
> Hey guys, I seem to be having some issues with my graphics driver on ubuntu.

I have a radeon hd 3650 512mb ddr2 graphics card. It works great on windows 7. But on ubuntu partition i get a lot of lag when i play videos. And overall performance is just not smooth enough. 

Has anyone else had this problem and/or have a fix for this?


Did you try installing the proprietary ATI Catalyst -fglrx driver?

From the Menu --- System ---- Administration --- Hardware Drivers

Once it installs the fglrx driver don't reboot right away, even though it tells you to. Do the following command from the terminal first:

```
aticonfig --initial
```

Then reboot.

---

### Post by Crash~Override on 2009-11-11
> **alphacrucis2 said:**
> Did you try installing the proprietary ATI Catalyst -fglrx driver?

From the Menu --- System ---- Administration --- Hardware Drivers

Once it installs the fglrx driver don't reboot right away, even though it tells you to. Do the following command from the terminal first:

```
aticonfig --initial
```Then reboot.

okay i will try that and report back

---

### Post by PD_Steve on 2010-12-28
> **Crash~Override said:**
> okay i will try that and report back

So did I and although I got the darn proprietary drivers to work, they would freeze the computer....aka no mouse no keyboard. The only way to get back to the standard drivers was to go into terminal and back the darn things out.

I actually did the installer with the 10-12 version which was delivered on 13 December.....ARRRRRG 

The video on my Boxee does play but the frame rate is rather jerky. Sound is fine.


The video is a HD 3650, the cpu is a AMD 3200 on some old e machines old box with 1 Gg of PC2700 memory. 

Is there a way to tweak the standard driver for better frame rate while AMD video sorts out?

---

