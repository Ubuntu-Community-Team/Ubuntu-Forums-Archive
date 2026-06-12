---
title: "SSH Key Not Unlocked on Login"
date: 2010-09-05
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Joeb454 on 2010-09-05
I think this issue is to do with gnome-keyring, however, I cannot figure out how to fix it, so if anybody knows, your help would be much appreciated :)

The issue I have is that whenever I log in, I'm then required to enter the passphrase for my ssh key. This gets remarkably tedious, and essentially negates the use of having key authentication :p

I've tried checking /etc/pam.d/gdm and /etc/pam.d/gdm-autologin and they look correct, however, the issue still persists. Previously the key was unlocked upon login.

Also - If this is a known bug, I apologise now :)

---

### Post by ranch hand on 2010-09-05
If you are using auto login you have not given a password for the system to use to unlock anything.

---

### Post by cariboo on 2010-09-05
Joeb, this may be more in bodhi.zazens sphere of expertise, him being the expert on all things security related.

---

### Post by ktp on 2010-09-05
> **Joeb454 said:**
> I think this issue is to do with gnome-keyring, however, I cannot figure out how to fix it, so if anybody knows, your help would be much appreciated :)

The issue I have is that whenever I log in, I'm then required to enter the passphrase for my ssh key. This gets remarkably tedious, and essentially negates the use of having key authentication :p

I've tried checking /etc/pam.d/gdm and /etc/pam.d/gdm-autologin and they look correct, however, the issue still persists. Previously the key was unlocked upon login.

Also - If this is a known bug, I apologise now :)

I am assuming you have installed libpam-keyring, the keyring and login password match, and have following in  /etc/pam.d/gdm

> @include common-pamkeyring

If so then it might a bug.

---

### Post by Joeb454 on 2010-09-06
> **ranch hand said:**
> If you are using auto login you have not given a password for the system to use to unlock anything.

I'm not using auto-login :)

> **cariboo907 said:**
> Joeb, this may be more in bodhi.zazens sphere of expertise, him being the expert on all things security related.

Could be, I'll ask him :)

> **ktp said:**
> I am assuming you have installed libpam-keyring, the keyring and login password match, and have following in  /etc/pam.d/gdm


Trying to install libpam-keyring installs libpam-gnome-keyring instead, which is already installed. Adding the line to /etc/pam.d/gdm prevents me from logging in via the GUI, and the passwords do match :)

---

### Post by hugmenot on 2010-09-11
Seems to be a bug: [https://bugzilla.gnome.org/show_bug.cgi?id=627815](https://bugzilla.gnome.org/show_bug.cgi?id=627815)

---

