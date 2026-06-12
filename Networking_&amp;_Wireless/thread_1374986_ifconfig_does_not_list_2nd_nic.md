---
title: "ifconfig does not list 2nd nic"
date: 2010-01-07
forum: Networking &amp; Wireless
---

### Post by GPToyz on 2010-01-07
hello

new member here

i am using ubuntu server and when i run ifconfig i do not see my second nic

i'm running a supermicro 5015 dual core atom 330 server

ubuntu server 9.1

---

### Post by elliotbeken on 2010-01-07
hi there are u using the device ? is it active or does it need drivers ?

---

### Post by GPToyz on 2010-01-07
well that's what i can't tell...

when i originally deployed ubuntu the server was able to network off the bat

but i can't tell if the other nic is on or even present

i went as far as to get xwindows running, but i still don't see the hardware

---

### Post by Iowan on 2010-01-07
Check **lshw -C network** for some information about your interfaces.

---

