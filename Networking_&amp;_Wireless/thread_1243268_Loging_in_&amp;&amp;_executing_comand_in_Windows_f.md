---
title: "Loging in &amp;&amp; executing comand in Windows from Linux"
date: 2009-08-18
forum: Networking &amp; Wireless
---

### Post by kcode on 2009-08-18
Hi,
This is what I want to do:
After loging in from linux machine to windows, execute shutdown -s. 

I am able to login to windows machine using rdesktop in GUI mode and the operations as if I working on a native windows machine, but I want all in text mode.
Actually there would be a shell script which would kill all computers in a lab when run from the main machine.

Thanks

---

### Post by superprash2003 on 2009-08-18
you could do this via SSH

---

### Post by SlugSlug on 2009-08-18
yes there is a winssh
[http://winsshd.bitvise-limited.qarchive.org/](http://winsshd.bitvise-limited.qarchive.org/)

---

### Post by kcode on 2009-08-19
> **SlugSlug said:**
> yes there is a winssh
[http://winsshd.bitvise-limited.qarchive.org/](http://winsshd.bitvise-limited.qarchive.org/)

Thanks, it was helpful. :-)

---

### Post by kevdog on 2009-08-19
Or you could install cygwin if you are familar with linux since this basically masks a red-hat linux environment on a windows machine

---

