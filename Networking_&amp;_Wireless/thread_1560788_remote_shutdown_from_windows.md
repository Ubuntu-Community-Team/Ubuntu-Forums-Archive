---
title: "remote shutdown from windows"
date: 2010-08-25
forum: Networking &amp; Wireless
---

### Post by palves on 2010-08-25
Hi,

I am using ubuntu for the last couple of months and I am very pleased with it. 

This said, I still have one issue to sort out. I also use the ubuntu machine as a fileserver and I can wake it up using wol, but I am struggling to remotly shut it down.

I am trying to use the putty command line application plink and I just cannot get it to work. 
I have tried:
1) plink user@xxxx -pw mypass /sbin/shutdown -h now
shutdown: need to be root

2)plink user@xxxx -pw mypass sudo /sbin/shutdown now
sudo: no tty present and no askpass program specified

the idea is to get a batch file that can be clickable. Any help?

Thanks in advance.
PA

---

