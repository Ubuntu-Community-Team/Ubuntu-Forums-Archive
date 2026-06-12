---
title: "Error After Installing Xampp .Error :Xampp Could Not Start MySql."
date: 2013-06-10
forum: Myanmar Team
---

### Post by Htut Myat on 2013-06-10
Error -Warning: World-writable config file '/opt/lampp/etc/my.cnf' is ignoredXAMPP: Couldn't start MySQL!

---

### Post by Htut Myat on 2013-06-10
sudo chmod 755 /opt/lampp/etc/my.cnf

---

### Post by Lars Noodén on 2013-06-10
Welcome.  Actually XAMPP is not needed on Ubuntu, you can get all those same packages through the repository instead by adding a single package:

```

sudo apt-get update
sudo apt-get install lamp-server^

```

(Note the caret ^ )
Or you can use Synaptic instead of apt-get.  

That will install everything **in the right places** except for Perl which is already there because it is built into Ubuntu.  After that, you can safely delete what you put under /opt.  Using the package manager has several advantages.  One is that security and performance updates can be managed automatically, as will the related notifications.  Another is that everything will be in the right place (as opposed to the wrong places for XAMPP) which will make it easier to troubleshoot or have other people help you.  XAMPP is a fine crutch for people still on Windows, but it is the next hardest way to do things in the Linux world.  In the Linux world we rather let as much as possible be taken care of automatically.

---

