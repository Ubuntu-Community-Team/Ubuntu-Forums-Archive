---
title: "How to Lan two ubuntu computers"
date: 2009-07-26
forum: Networking &amp; Wireless
---

### Post by mono_indeed on 2009-07-26
Hi guys, for a school ICT project we are trying to lan two ubuntu 7.1 computers, we have tried looking up instruction on how to do this on the internet but we have not found any instructions. 
 
Thanks in advance
 
Mono

---

### Post by dmizer on 2009-07-26
What do you mean by "trying to LAN"?

LAN = Local Area Network. So, if you plug both computers into a router, then you have a LAN.

---

### Post by mono_indeed on 2009-07-26
We realise that and have done that but they still dont see each other and cant share files :confused:

---

### Post by jm2 on 2009-07-26
Do you have the /etc/hosts file set with unique static IP Address?
And the eth0 card in /etc/network/interfaces with a static address?
You need static IP address so it doesn't change each time you re-boot. Since you want to be able to talk together.

If the above is set, you should be able to ping each other.
If so, then you can use telnet or ftp to transfer files.

---

### Post by synapsys on 2009-07-26
[http://thanhsiang.org/faqing/node/114](http://thanhsiang.org/faqing/node/114)

7.10 is outdated and un-supported. You won't be able to download and install programs.
Might I suggest using something newer?

---

### Post by lisati on 2009-07-26
> **mono_indeed said:**
> Hi guys, for a school ICT project we are trying to lan two ubuntu 7.1 computers, we have tried looking up instruction on how to do this on the internet but we have not found any instructions. 
 
Thanks in advance
 
Mono

Suggestion: look for instructions on "[samba]("http://ubuntuforums.org/showthread.php?t=202605")". It's not the only way of doing things, but it has an advantage over some other methods in that if you need to figure a machine running Windows into the picture, it will cope.

---

