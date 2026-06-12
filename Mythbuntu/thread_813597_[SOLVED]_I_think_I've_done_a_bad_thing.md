---
title: "[SOLVED] I think I've done a bad thing"
date: 2008-05-31
forum: Mythbuntu
---

### Post by Meph1st0 on 2008-05-31
I just got home from a 4 month business trip and wanted to install any updates on my myth box that I'd missed.  But some of the updates wouldn't install (kept getting 404 url not found errors) and so I opened a terminal window and typed sudo apt-get update and sudo apt-get upgrade.  

I think I read somewhere in these forums that I shouldn't ever do an apt-get upgrade.

Have I done a bad thing?  It's not finished upgrading yet.  Are there any huge problems that I should expect?  Should I backup all my movies and music before I reboot?

I"m still running gutsy.  I didn't just upgrade to hardy did I?

---

### Post by tamoneya on 2008-05-31
that shouldnt upgrade you to hardy but you can check with ```
lsb_release -a
```as for fixing the 404 errors you should try to switch the mirror you are using.  In synaptic select settings -> repositories.  Then use the drop down mirror to select a different mirror.

---

### Post by Meph1st0 on 2008-05-31
Alright, well, after rebooting everything seems fine.  I guess I just panicked.  I thought I'd read somewhere that I shouldn't do an apt-get upgrade.  Maybe it was something else.  Thanks anyway.

---

### Post by inportb on 2008-05-31
To the contrary... you *should* apt-get update and apt-get upgrade once in a while to keep your system up-to-date =D

I tend to upgrade whenever my notification applet indicates that upgrades are available.

---

### Post by atomicfire on 2008-05-31
sudo apt-get dist-upgrade is the one you don't want to run.

Good luck!

---

### Post by Nikas on 2008-05-31
> **atomicfire said:**
> sudo apt-get dist-upgrade is the one you don't want to run.

Good luck!

Why not? I do it all the time. The last time i got the kernel update for hardy. ;)

dist-upgrade will NOT upgrade from gutsy to hardy.

---

