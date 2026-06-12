---
title: "conflct between upstart and  sysvinit"
date: 2010-08-11
forum: Networking &amp; Wireless
---

### Post by javadit on 2010-08-11
Hi 
I want to install a file server on ubuntu 10
I downloaded **nfs-kernel-server **and faced this error :
Error: Dependency is not satisfiable: sysvinit (>= 2.80-1)

Then I downloaded and run sysvinit 
this time error was : error: breaks existing package 'upstart' conflict: sysvinit () 

How can I solve this conflict ?

---

### Post by javadit on 2010-08-14
No one can help me?

---

### Post by chienpo on 2010-08-24
Did you ever get this figured out on your machine?

Do you have a version of sysvinit installed and if so, what version? (dpkg -l | grep sysvinit)

From a quick check on packages.ubuntu.com I see that ultimately nfs-kernel-server depends on (indirectly) initscripts which depends on sysvinit-utils, but I don't even see a package named sysvinit for Lucid.

Also, is you system up to date (sudo apt-get update && sudo apt-get upgrade) ?

---

### Post by capscrew on 2010-08-24
> **chienpo said:**
> Did you ever get this figured out on your machine?

Do you have a version of sysvinit installed and if so, what version? (dpkg -l | grep sysvinit)

From a quick check on packages.ubuntu.com I see that ultimately nfs-kernel-server depends on (indirectly) initscripts which depends on sysvinit-utils, but I don't even see a package named sysvinit for Lucid.

Also, is you system up to date (sudo apt-get update && sudo apt-get upgrade) ?

See [here]("http://packages.ubuntu.com/lucid/sysvinit-utils").

---

