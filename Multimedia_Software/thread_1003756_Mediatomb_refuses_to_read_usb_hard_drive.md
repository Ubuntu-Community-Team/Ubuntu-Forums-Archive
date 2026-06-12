---
title: "Mediatomb refuses to read usb hard drive"
date: 2008-12-06
forum: Multimedia Software
---

### Post by netron on 2008-12-06
when i am browsing my filesystem via the mediatomb web interface, it refuses
to open up my usb drives in /media , even though i am running mediatomb as myself and i have full rw access to the usb drivs.

any ideas?

---

### Post by netron on 2008-12-06
solved it.  

after apt-get install,  mediatomb launches from /etc/init.d/ and that runs as another user.  shut that instance down , and then launch mediatomb in your own shell account - and voila, you have access to usb drives.

it was a permissions issue.

---

### Post by Aerospaztic on 2010-03-08
I've been trying to figure this out for days!

Thank you, thank you, thank you! :p

---

### Post by mandogon on 2010-11-05
im new to ubuntu and media tomb just wondering how is it that you changed the init.d file what changes were made i been trying to get my usb hard drive to read for days now with no luck and notice your post with no instruction on how to do it but if you could help thanks i have all my media on this drive so your help will be appreciated thanks

---

