---
title: "Hosed MiniDLNA - how to do clean reinstall?"
date: 2012-01-02
forum: Multimedia Software
---

### Post by drl2 on 2012-01-02
Have been playing with MiniDLNA on 11.10 and had it partially working, but database updates were failing, and I made the problem worse by playing with permissions.  I decided to re-install, so I sudo apt-get removed it, then tried to install again - it failed, unable to write /etc/minidlna.conf (which wasn't there because I'd renamed my existing one).  So in my naivete I decided to manually remove all the related files, including init.d/minidlna and /etc/default/minidlna, assuming they'd be created on install ... which, it turns out, they're not.

Is there any relatively painless (read: not wiping and re-installing the OS) way to get my system into a state where I can do a clean, working minidlna install at this point?

---

