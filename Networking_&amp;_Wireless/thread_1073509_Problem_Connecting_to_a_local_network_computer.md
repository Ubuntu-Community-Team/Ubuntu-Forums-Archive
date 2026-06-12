---
title: "Problem Connecting to a local network computer"
date: 2009-02-18
forum: Networking &amp; Wireless
---

### Post by BlackDrake on 2009-02-18
I just installed Ubuntu 8.10
And when I try to access my local server or an other computer I get these errors.

Yday I got the 2nd one.. today I only get error msg1

No program is registered to handle this file.

Anyone have an Idea?

What did I forget to do?:p

In advance Thanx

---

### Post by superprash2003 on 2009-02-18
are you trying to access this via nautilus?? i guess it is a nautilus bug.. you should try refreshing.. or attempting 2 or 3 times

---

### Post by BlackDrake on 2009-02-18
I Just do as I normaly do.
Alt +F2 (Run)
and smb://192.168....

and I got when I tried to use with nautilus.
Nautilus cannot handle smb locations

---

### Post by BlackDrake on 2009-02-18
found one "solution"

I was able to recreate this bug in 8.10.  I can verify that the problem
does not exist in 8.04.1.  In 8.04.1, running smb:// brought up the
nautilus network browser.  The workaround is very simple.  You should be
able to navigate your samba network through the nautilus File Browser or
through the Places -> Network menu.  Your printer should be listed
there.

this works

---

