---
title: "What is lo ?"
date: 2006-07-11
forum: Networking &amp; Wireless
---

### Post by zugu on 2006-07-11
Everyime I enter the ifconfig command with no arguments, I get a status report about a device (I think) called 'lo'. In order to get info about my only ethernet card I ned to run 'ifconfig eth0'.

What is 'lo' and why is it more important than 'eth0'(i.e. is the default output on running ifconfig without arguments)?

Cheers.

---

### Post by mogelhead on 2006-07-11
When I execute the ifconfig command, both the eth0 and lo interfaces are listed. 

I assume you are doing this from a terminal window in the GNOME desktop environment. Maybe you can just scroll up in the terminal window and the text is there?

lo (short for loopback) is a dummy network interface that goes directly back to the computer. See [this]("http://en.wikipedia.org/wiki/Loopback") Wikipedia article.

---

### Post by zugu on 2006-07-11
Thank you for the information.

---

### Post by harisund on 2006-07-11
If your eth0 is activated, then by default ifconfig will reveal both lo and eth0 and all other activated cards actually. 

lo is what determines whether the TCP/IP stack on your computer is working properly or not. Without that, something is wrong with TCP.

---

