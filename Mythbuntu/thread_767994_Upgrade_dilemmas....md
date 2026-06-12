---
title: "Upgrade dilemmas..."
date: 2008-04-26
forum: Mythbuntu
---

### Post by pommattski on 2008-04-26
Hi all. 

I have an always-on P4 3GHz machine with 2 tuner cards running Feisty (32bit) with MythTV master backend-master and frontend - version 0.20.  It runs funtionally and solidly and I am quite reluctant to upgrade it until absolutely necessary.  
Neither option (Feisty->Gutsy->Hardy upgrade with associated MythTV issues OR a fresh install and configure) excites me!

A PC (core2) in another room  which I use for work and play is currently runnings Feisty (32bit) with a mythtv frontend (0.20). 
For a number of reasons I'm planning to do a fresh install of Hardy 64-bit on this machine. 

Am I going to have problems running a v0.21 frontend connecting to a 0.20 backend?... and even more importantly, could it corrupt the database?

Thanks for your thoughts.
Matt.

---

### Post by laga on 2008-04-26
> **pommattski said:**
> 
Am I going to have problems running a v0.21 frontend connecting to a 0.20 
backend?


Yes. It simply won't work.

> 
... and even more importantly, could it corrupt the database?

Thanks for your thoughts.
Matt.

Depends on your definition of "corruption" :) The database will be upgraded to a new schema version. After that it probably/most likely won't work with 0.20 anymore. However, a database backup is created when upgrading to 0.21.

Keep in mind that feisty will see its End Of Life in 6 months, which means no more security updates. I still have to upgrade my backend :/


Here's what you can do:
a) upgrade your backend to Hardy which comes with 0.21 (and is based on an LTS release!)
b) upgrade your MythTV install on your feisty backend to 0.21
c) Build MythTV 0.20 from source on your new frontend. (Or rebuild the source packages from feisty)

As for b), I might try to provide a build for 0.21 on the weekly builds PPA if you like. Of course, that still means you have to upgrade MythTV.

---

### Post by pommattski on 2008-04-26
Thanks laga,
> **laga said:**
> ...upgrade your backend to Hardy which comes with 0.21 (and is based on an LTS release!)Yep. I think this is really the right way forward, (even though, as I think you agree, the prospect of having to reconfigure everything again is not a nice one).
I'll try upgrading to Gutsy, then Hardy. [-o< If that fails at either stage I'll have to try a fresh install of Hardy. 
Wish me luck!

As far as the other front-end machine goes, I'm multi-booting that for now (XP, Feisty32 and Hardy64) so that I can test 64bit Hardy first.  All's well with this one so far.

Cheers,
Matt.

---

### Post by pommattski on 2008-04-27
Maybe I should have had a little more faith... I'm having a hard time believing it now!... 

Today I upgraded my Ubuntu Desktop with MythTV backend-master and frontend from Feisty to Gutsy and from Gutsy to Hardy - and it all still works!! \\:D/

Feisty to Gutsy was completely flawless.
Gutsy to Hardy upgrade had me worried at the end when upgrade-manager reported that it had to close and that my system may be inoperable!... but I rebooted and everything (that I've tried so-far)'just-works'!

---

