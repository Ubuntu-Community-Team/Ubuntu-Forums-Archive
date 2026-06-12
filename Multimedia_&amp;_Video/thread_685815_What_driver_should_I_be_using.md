---
title: "What driver should I be using?"
date: 2008-02-02
forum: Multimedia &amp; Video
---

### Post by xtxzt on 2008-02-02
I have an HP dx6650us laptop with a GMA x3100 Integrated graphics card. Whenever I go in to any basic 3d game it lags a ton, even with Compiz off. What graphics card driver should I select in the screen and graphics dialog? I am really new to Ubuntu so forgive me if this is a stupid question.

---

### Post by jan quark on 2008-02-03
first check if there are inactive drivers in the restricted drivers manager
system > administration > restricted drivers manager

---

### Post by xtxzt on 2008-02-09
> **jan quark said:**
> first check if there are inactive drivers in the restricted drivers manager
system > administration > restricted drivers manager

It says that my hardware does not need any restricted drivers.

---

### Post by xtxzt on 2008-02-13
Can someone help please? :(

---

### Post by theacoustician on 2008-02-13
> **xtxzt said:**
> Can someone help please? :(

There are no restricted drivers for Intel.  That's an ATi/nVidia thing only.

Intel chips and Compiz don't play nice together.  You can unblacklist your chip by following this procedure ([http://ubuntuforums.org/showthread.php?t=674123&highlight=x3100](http://ubuntuforums.org/showthread.php?t=674123&highlight=x3100)) but it breaks video playback.  The simple answer is if you need 3D now, you need to go nVidia or ATi.  Sorry, but if you can wait, Intel is supposed to be working on this.

---

### Post by xtxzt on 2008-02-13
> **theacoustician said:**
> There are no restricted drivers for Intel.  That's an ATi/nVidia thing only.

Intel chips and Compiz don't play nice together.  You can unblacklist your chip by following this procedure ([http://ubuntuforums.org/showthread.php?t=674123&highlight=x3100](http://ubuntuforums.org/showthread.php?t=674123&highlight=x3100)) but it breaks video playback.  The simple answer is if you need 3D now, you need to go nVidia or ATi.  Sorry, but if you can wait, Intel is supposed to be working on this.

So un-blacklisting it will make Compiz function correctly, but it will break video playaback? Also will un-blacklistng it make most of my other 3d games run well?

Sorry, I'm sort of new at this. :/

---

### Post by theacoustician on 2008-02-13
> **xtxzt said:**
> So un-blacklisting it will make Compiz function correctly, but it will break video playaback? Also will un-blacklistng it make most of my other 3d games run well?

Sorry, I'm sort of new at this. :/Yes and probably, yes.

---

### Post by xtxzt on 2008-02-13
> **theacoustician said:**
> Yes and probably, yes.

Does video playback completely break, or just skip a lot?

EDIT: I tried that un-blacklisting thing and I got up to the third step- The only problem is that I don't have the first file, and there is no skip_check in the other one.

---

