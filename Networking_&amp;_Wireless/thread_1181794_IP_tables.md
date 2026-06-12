---
title: "IP tables"
date: 2009-06-08
forum: Networking &amp; Wireless
---

### Post by grimm08 on 2009-06-08
I am trying to write some rules for IPtables and I am writing the rule to allow only Established traffic in, but I get BAD State error.  I typed in the command just like the documentation says from [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)  I get this error no matter if I type in a port number or a protocol.  This is not a major concern since my box is a test machine right now and I am behind a Cisco firewall but it would be nice to figure out IPtables, thanks for anyone that responds. This is IPtables version 1.40.

---

### Post by superprash2003 on 2009-06-08
try installing gufw easy way to handle

---

### Post by brabo on 2009-06-08
Hi there,

i have had some trouble with iptables too in the past, but i get it now.
please post the exact command you gave, and i'll try to correct it.

grtz,
brabo.

---

### Post by grimm08 on 2009-06-24
I was able to figure it out.  It helps if you don't put spaces in after your commas.

---

