---
title: "One of the latest updates crashed my ubuntu"
date: 2010-08-06
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-08-06
i just downloaded updates after five hours of not updating and then something failed in the install and then everything stopped responding not the browser not apport not 
even when i pressed the restart option so i was forced to hard boot the computer and now when i try to start ubuntu i reach the command line windows meaning i need to 
enter user name and password and then i get command line only.
 
What can i do about it?

---

### Post by dino99 on 2010-08-06
ive got an buffer overflow while updating libglib2.0-0 and now about 20 packages are broken, cant find a workaround, so im waiting for new updates, will see on next monday now

---

### Post by aninaiian on 2010-08-06
In case you didn't know you can try downgrading libglib ala something like this:

```
dpkg -i /var/cache/apt/archives/libglib2.0-0_2.25.11-3ubuntu1_amd64.deb /var/cache/apt/archives/libglib2.0-data_2.25.11-3ubuntu1_all.deb
```

or if on 32 bit

```
dpkg -i /var/cache/apt/archives/libglib2.0-0_2.25.11-3ubuntu1_i386.deb /var/cache/apt/archives/libglib2.0-data_2.25.11-3ubuntu1_all.deb
```

I also had this problem but caught it early and am now sticking with the previous version.

I just realized more packages just came in it seems you'll also have to downgrade at least gconf-defaults-service, gconf2, libdconf0, libgconf2-4, libglib2.0-bin

Apparently, the first command is not needed as 64 bit is not affected

---

### Post by SevenMachines on 2010-08-06
Yes, the new glib will crash, as a result gdm and X will crash so you'll be staring at a command line. stick with or downgrade
[http://archive.ubuntu.com/ubuntu/pool/main/g/glib2.0/libglib2.0-0_2.25.11-3ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/glib2.0/libglib2.0-0_2.25.11-3ubuntu1_i386.deb)

[EDIT] You might also want to downgrade -bin -data ( and -dev if you need to) from the same place using the 19th July versions 2.25.11-3ubuntu1
[http://archive.ubuntu.com/ubuntu/pool/main/g/glib2.0/](http://archive.ubuntu.com/ubuntu/pool/main/g/glib2.0/)

---

### Post by rjkothari on 2010-08-06
I tried your suggestion for 32 bit, but got following error

dpkg: error processing /var/cache/apt/archives/libglib2.0-0_2.25.11-3ubuntu1_i386.deb (--install):
 cannot access archive: No such file or directory
dpkg: error processing /var/cache/apt/archives/libglib2.0-data_2.25.11-3ubuntu1_all.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /var/cache/apt/archives/libglib2.0-0_2.25.11-3ubuntu1_i386.deb
 /var/cache/apt/archives/libglib2.0-data_2.25.11-3ubuntu1_all.deb

---

### Post by aninaiian on 2010-08-06
Can you post the output of this

```
ls -l /var/cache/apt/archives/ | grep libglib
```

I might have missed some updates or you did and as a result we weren't using the same version.

---

### Post by Framli on 2010-08-06
[Critical bug #614240]("https://bugs.launchpad.net/ubuntu/+source/glib2.0/+bug/614240")

---

### Post by joey-elijah on 2010-08-06
> **aninaiian said:**
> In case you didn't know you can try downgrading libglib ala something like this:

```
dpkg -i /var/cache/apt/archives/libglib2.0-0_2.25.11-3ubuntu1_amd64.deb /var/cache/apt/archives/libglib2.0-data_2.25.11-3ubuntu1_all.deb
```

or if on 32 bit

```
dpkg -i /var/cache/apt/archives/libglib2.0-0_2.25.11-3ubuntu1_i386.deb /var/cache/apt/archives/libglib2.0-data_2.25.11-3ubuntu1_all.deb
```

I also had this problem but caught it early and am now sticking with the previous version.

I just realized more packages just came in it seems you'll also have to downgrade at least gconf-defaults-service, gconf2, libdconf0, libgconf2-4, libglib2.0-bin

I've re-installed the packages you list... here goes rebooting...

---

### Post by aninaiian on 2010-08-06
> **joey-elijah said:**
> I've re-installed the packages you list... here goes rebooting...

My list may be a bit too long as I got that listing from my 64 bit system which doesn't seem affected.  My 32 bit system only needs the libglib2.0-0, libglib2.0-bin, and libglib2.0-data packages downgraded as no other packages on my end require libglib.  Also, if libglib2.0-0-dbg or libglib2.0-dev is installed they need to be downgraded too...

---

### Post by lsrg on 2010-08-06
It worked for me!!! thanks


> **SevenMachines said:**
> Yes, the new glib will crash, as a result gdm and X will crash so you'll be staring at a command line. stick with or downgrade
[http://archive.ubuntu.com/ubuntu/pool/main/g/glib2.0/libglib2.0-0_2.25.11-3ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/glib2.0/libglib2.0-0_2.25.11-3ubuntu1_i386.deb)

[EDIT] You might also want to downgrade -bin -data ( and -dev if you need to) from the same place using the 19th July versions 2.25.11-3ubuntu1
[http://archive.ubuntu.com/ubuntu/pool/main/g/glib2.0/](http://archive.ubuntu.com/ubuntu/pool/main/g/glib2.0/)

---

### Post by aviramof on 2010-08-06
Is there any simple solution to this problem like running update from recovery mode that would download and fix the problem?

---

### Post by mkis62 on 2010-08-06
The last update fixed the problem

libglib2.0-0 v.2.25.12.is.2.25.11-0ubuntu1

---

### Post by psyke83 on 2010-08-06
> **rjkothari said:**
> I tried your suggestion for 32 bit, but got following error

dpkg: error processing /var/cache/apt/archives/libglib2.0-0_2.25.11-3ubuntu1_i386.deb (--install):
 cannot access archive: No such file or directory
dpkg: error processing /var/cache/apt/archives/libglib2.0-data_2.25.11-3ubuntu1_all.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /var/cache/apt/archives/libglib2.0-0_2.25.11-3ubuntu1_i386.deb
 /var/cache/apt/archives/libglib2.0-data_2.25.11-3ubuntu1_all.deb

The suggestion was for aviramof (the thread creator). This thread is within the Maverick Meerkat (10.10) forum, and your issue appears to be completely unrelated.

You're using an older release version (Karmic), so you're looking for advice in the in the wrong place. You should create a new thread in the proper forum (i.e., not in the development testing forum), or search for the bug on Launchpad.

---

### Post by cariboo on 2010-08-06
> **psyke83 said:**
> The suggestion was for aviramof (the thread creator). This thread is within the Maverick Meerkat (10.10) forum, and your issue appears to be completely unrelated.

You're using an older release version (Karmic), so you're looking for advice in the in the wrong place. You should create a new thread in the proper forum (i.e., not in the development testing forum), or search for the bug on Launchpad.

I moved the post to it's own thread in Networking & Wireless.

---

### Post by aviramof on 2010-08-06
> **mkis62 said:**
> The last update fixed the problem

libglib2.0-0 v.2.25.12.is.2.25.11-0ubuntu1

Thanks for the information problem is solved.

---

