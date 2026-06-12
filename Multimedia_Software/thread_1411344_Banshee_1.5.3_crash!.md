---
title: "Banshee 1.5.3 crash!"
date: 2010-02-19
forum: Multimedia Software
---

### Post by insanekat on 2010-02-19
Hello,
I am running Ubuntu 9.10

I am using Banshee 1.5.3 and haven't had a problem up until today. Whenever I edit a track and click save, it crashes. Or whenever I delete a track from my library it crashes.

I tried reinstalling and I tried completely removing then reinstalling, both with no results.

If you need any more information let me know. Thanks.

---

### Post by tgalati4 on 2010-02-19
In a terminal:

banshee --debug

---

### Post by insanekat on 2010-02-19
kat@kat-laptop:~$ banshee --debug
** Running Mono with --debug   **
[Debug 23:57:13.087] Bus.Session.RequestName ('org.bansheeproject.Banshee') replied with InQueue

---

### Post by tgalati4 on 2010-02-22
Well that was uber-helpful.  Try rolling back to an earlier version.  Don't forget to purge any old configuration files:

sudo apt-get purge banshee

Also, check for disk read errors:

dmesg | tail -100

A failing disk can cause strange symptoms that appear to be software problems.

---

### Post by insanekat on 2010-02-22
Sorry I don't exactly know what I'm doing! But it was a problem with the banshee.db, I deleted it and re-imported my library so it's fixed now. Thank you for your time!

---

