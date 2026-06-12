---
title: "Remove the options when connecting to a samba share"
date: 2009-06-29
forum: Networking &amp; Wireless
---

### Post by dermawan123 on 2009-06-29
I'm running Ubuntu 9.04. Whenever I want to connect to a samba share on other computer, there will be a dialog box to enter:

* username
* domain
* password

and the radiobuttons:

* forget password immediately
* remember password until you logout
* remember forever

Is it possible to force the user to only select "forget password immediately"? Or even better, to not show the radiobuttons at all...

Any help will be appreciated... :)

---

### Post by petermck on 2009-08-01
Hi,
I want to do the same thing. Did you get an answer on how to do it?

---

### Post by dermawan123 on 2009-08-03
So far, I haven't found any solution yet, unfortunately...

---

### Post by petermck on 2009-08-06
Did you try anything with PolicyKit? I'm about to, but I won't waste my time if someone else has already been down that road.

---

### Post by petermck on 2009-08-22
If you're still interested in doing this I managed to stop the password saving options by changing the execute permissions on /usr/bin/gnome-keyring-daemon. Unfortunately this effectively means no keyring and this will no doubt be a pain when it comes to other applications like wireless network management, but that is not a problem in my application.
The password is still stored in memory until you either log off or unmount the share or kill the relevant gvfs-smbd process. I'm trying to think of a way around this as I would like the share to be unmounted when the user closes the nautilus window or ideally navigates away from the share.

---

### Post by Kurgan_it on 2010-05-18
I need the same thing, too. Some ideas?

---

