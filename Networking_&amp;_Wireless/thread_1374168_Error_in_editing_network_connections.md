---
title: "Error in editing network connections"
date: 2010-01-06
forum: Networking &amp; Wireless
---

### Post by obscurant1st on 2010-01-06
Hi,
I am using Karmic n loving it.
now i was trying to use opendns for my mobile internet connection.
So i got an article which says how to set the dns nameservers.
I right clicked and seleced edit connections from the network icon which shows up on the right side of the taksbar.(near the time and date).
and then i selected mobile broadband and thn clicked on edit, now at first i was able to edit the nameserver which was under ipv4.
But now after a reboot when i tried to go there by doing the same steps, whihc click on edit in the mobile broadband tab, i am asked for the password. I have the administrator password, so i tried it here.But no luck, it says error initializing editor and insufficient privileges.

---

### Post by Iowan on 2010-01-06
Is the administrator password different from yours?  (Did you try yours?)

---

### Post by obscurant1st on 2010-01-06
actually for all the other things i'm using a password.
and here also i tried with that password.
for example i use this password for connecting to wireless networks, mounting windows partitions etc etc.
but still the same thing happens.. :(

---

### Post by Iowan on 2010-01-07
Which article? Did it use **root** or **sudo**?  Can you use **sudo** at all? From a terminal does **sudo ls** work?

---

### Post by obscurant1st on 2010-01-07
yeah, sudo is just working fine.
as i said everything else is just working fine, i donno why this happens.
For all the other network adapters its working as exxpected. But for this mobile broadband thing, it says insufficient privileges.

Screen shots.
1. this happens when i try editing normal network connections/adapters.( it is working quite normal)

[[IMG]http://img340.imageshack.us/img340/5088/screenshotbf.th.png[/IMG]](http://img340.imageshack.us/i/screenshotbf.png/)


2. This is the problem I am facing. This happnes only with The specified connection. Mobile Broadband. But believe me, it was working 2 days back.
[[IMG]http://img138.imageshack.us/img138/4340/screenshot1t.th.png[/IMG]](http://img138.imageshack.us/i/screenshot1t.png/)

And one thing i see is, the error comes even before typing the password, which i didnt knw at first.

---

### Post by zweiundzwei on 2010-03-10
I have the same problem, did you solve it?

---

### Post by obscurant1st on 2010-03-10
no man, i just uninstalled that application, and installed wicd, its far more better.. :D

---

### Post by redman5087 on 2010-03-14
same problem

---

### Post by groovur on 2010-03-16
Delete the connection which you can no longer edit.

Recreate it but this time...

Try leaving the checkbox "Available to all users" unchecked. Worked for me under Mobile Broadband. ;)

---

