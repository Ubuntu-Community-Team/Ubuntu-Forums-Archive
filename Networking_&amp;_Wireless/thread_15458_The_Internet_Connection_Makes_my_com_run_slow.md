---
title: "The Internet Connection Makes my com run slow"
date: 2005-02-14
forum: Networking &amp; Wireless
---

### Post by BeSerKa on 2005-02-14
I Installed Ubuntu.
It worked Great.
It worked Wonderful.
I plugged My cable modem into the Already setup Network Card with the correct assigned Ip address, gateway and DNS server Ip's.
The com Slowed down, It slowed down almost to the point of uselessness.
and the Mouse pointer sort of began to flicker, It continues to do this even after I unplug the Network cable again.

Its totally weird does anybody know the where abouts of my problem?

Any help most appreciated.

---

### Post by az on 2005-02-14
do:
sudo top
in a console.

and see what is chewing up your cpu power.

---

### Post by scoon on 2005-02-14
Hey there, 

That is real odd.  I would try something like knoppix to test and see if it happens just w/ ubuntu or with all distros.  Other things to check would be IRQ sharing and maybe running memtest to check for bad ram. 


scoon

---

