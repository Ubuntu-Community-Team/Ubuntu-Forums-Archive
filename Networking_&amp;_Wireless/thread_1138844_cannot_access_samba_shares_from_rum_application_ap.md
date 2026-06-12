---
title: "cannot access samba shares from rum application applet"
date: 2009-04-26
forum: Networking &amp; Wireless
---

### Post by khizar on 2009-04-26
i just did a clean jaunty install n set up samba.everything is working fine i.e i can share my folders n access others through terminal as well as just giving the adress in the address bar of nautilus like smb://192.168.*.*. the only problem is tht i cannot do the same from the run application applet. it gives an error saying
> Could not open location 'smb://192.168.34.12/'
No application is registered as handling this file

dun know wat this means so any help will be greatly appreciated.
cheers
khizar

---

### Post by khizar on 2009-04-30
plzz guys a little help hre. i think the problem hre is tht my samba is working fine as i can share things and access shares but when i try to access from 'connect to server' or Alt+F2 , i get this error . so i think they dont know tht the application to open the shares in is nautilus , can sum1 tell me the way to tell this to thm??

thanking in anticipation.....

---

### Post by frekja on 2009-05-03
I'm pretty sure this relates to a couple of known bugs - see the links below for more details:

[http://bugzilla.gnome.org/show_bug.cgi?id=573994](http://bugzilla.gnome.org/show_bug.cgi?id=573994)
[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/291259](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/291259)
[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/252245](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/252245)

Unfortunately, these bugs have been around for a while.

---

### Post by khizar on 2009-05-04
> **frekja said:**
> I'm pretty sure this relates to a couple of known bugs - see the links below for more details:

[http://bugzilla.gnome.org/show_bug.cgi?id=573994](http://bugzilla.gnome.org/show_bug.cgi?id=573994)
[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/291259](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/291259)
[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/252245](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/252245)

Unfortunately, these bugs have been around for a while.

thanx a lot mate. solved my problem.

cheers

---

