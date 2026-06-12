---
title: "problem with arptables"
date: 2011-09-12
forum: Networking &amp; Wireless
---

### Post by Verifone on 2011-09-12
Hi,

I am trying to install arptables on a SheevaPlug (A plug computer) with Jaunty (9.04) on it. I installed the package successfully, but when I run it I get:

arptables v0.0.3.3: can't initialize arptables table `filter': arptables who? (do you need to insmod?)
Perhaps arptables or your kernel needs to be upgraded.

Then I tried to add arptables to the kernel, but I couldn't find such module anywhere. The kernel is 2.6.22.18.

Before advising me to upgrade to Natty, I can't. SheevaPlug is not compatible with anything higher than 9.04.

Thanks in advance,

---

### Post by Dangertux on 2011-09-12
Verify that you are running the command as root

```

sudo arptables -A ...

```If that does not work you can try building the package from source sometimes arptables-filter.ko gets left out when installing from the repos.

Use the packages from hardy to build from source (Lucid will likely fail without a kernel update)

[http://packages.ubuntu.com/source/hardy/arptables](http://packages.ubuntu.com/source/hardy/arptables)

EDIT : Now that I see you are using the same version that ships in Lucid repos, you may consider building from source on version 0.3.0 if running the command as root fails.

---

