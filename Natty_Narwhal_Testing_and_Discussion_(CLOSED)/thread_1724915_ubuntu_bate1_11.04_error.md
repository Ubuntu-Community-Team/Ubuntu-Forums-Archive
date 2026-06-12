---
title: "ubuntu bate1 11.04 error"
date: 2011-04-08
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by oklokl on 2011-04-08
[IMG]http://2.bp.blogspot.com/-aB_iMimvtZc/TZ_Rpk_-KjI/AAAAAAAAAE8/huGEYWMGsT0/s320/Screenshot.png[/IMG]

Only one installation
ubuntu bate1 11.04 en

GPG
Update
 Certificates
 Right click
 Ctrl + V
 Does not work ..

NVIDIA GeForce 9800GT 512m 
ubuntu Logo break down
Drive Not Supported

---

### Post by Hedgehog1 on 2011-04-09
After the first install of the beta 1 of natty, if you have an Nvidia card (and you do!) you need to:

* Select the 'classic' desktop, no effects, login.
* Load the resticted driver for your nvidia card
* Then reboot
* Select the 'classic' desktop again, login.
* Use update manager to run all the updates.
* Then reboot

Now you can login and use Unity.


***The Hedge***

:KS

---

### Post by Sef on 2011-04-09
Moved to Natty T&D.

---

### Post by beew on 2011-04-09
Well why did you upgrade? 11.04 is a beta.

---

### Post by oklokl on 2011-04-09
no upgrade
Only install

After the first install of the beta 1 of natty, if you have an Nvidia card (and you do!) you need to:

* Select the 'classic' desktop, no effects, login.
yes error..Occurs

* Load the resticted driver for your nvidia card
yes error..Occurs
No cognize.. bug
Do not support

* Then reboot
* Select the 'classic' desktop again, login.
yes error..Occurs Logo.. 
* Use update manager to run all the updates.
Multiple attempts
 Failure
* Then reboot

Now you can login and use Unity.

---

### Post by beew on 2011-04-09
> **oklokl said:**
> no upgrade
Only install

Sorry, my bad.

---

### Post by Hedgehog1 on 2011-04-09
> **oklokl said:**
> no upgrade
Only install

After the first install of the beta 1 of natty, if you have an Nvidia card (and you do!) you need to:

* Select the 'classic' desktop, no effects, login.
yes error..Occurs

* Load the resticted driver for your nvidia card
yes error..Occurs
No cognize.. bug
Do not support

* Then reboot
* Select the 'classic' desktop again, login.
yes error..Occurs Logo.. 
* Use update manager to run all the updates.
Multiple attempts
 Failure
* Then reboot

Now you can login and use Unity.

oklokl,

These are the steps that worked for me (I am posting from Natty with an Nvidia GPU).  The only other thing you can try is this:

Reinstall Natty, and DO NOT download updates during install.  **Don't allow any updates** until you have rebooted as part of the install **and loaded the restricted driver**.  Once the restricted driver is loaded and you reboot (again), then allow updates.

You are using a beta with BIG changes from the previous release, so this is really still for experienced Ubuntu users (particularly if you use nvidia GPU at the 'driver' is ALSO a beta).

If you are still getting errors, and cannot resolve them on your own, you might want to wait for beta 2.

***The Hedge***

:KS

---

