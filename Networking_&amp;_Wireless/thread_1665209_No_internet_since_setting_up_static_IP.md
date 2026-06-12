---
title: "No internet since setting up static IP"
date: 2011-01-12
forum: Networking &amp; Wireless
---

### Post by JustGus on 2011-01-12
I set up a static IP address yesterday, following the instructions at the top of [this page]("http://www.liberiangeek.net/2010/06/how-to-configure-static-ip-addresses-in-ubuntu-10-04-lucid-lynx/") and since my machine no longer connects to the internet (although all other machines are connecting fine, so I know it's a result of this change).  Can anyone offer a suggestion as to why this has happened, and, more importantly, what can be done to correct the problem. 

Thanks in advance for any help!

Gus

---

### Post by PatchesTheCaveman on 2011-01-12
Which method did you use?

Provide a screenshot of the settings you changed if you used the first method, or provide a copy of the files you changed if you used the second method.

---

### Post by dineshs on 2011-01-12
Does ```
route -n
``` show gateway ?
Note:While setting up static IP via network manager you may press enter key after typing the gateway address.

---

### Post by sj1410 on 2011-01-12
whats the output of

ifconfig
route -n

cat /etc/resolv.conf

---

### Post by JustGus on 2011-01-12
Thanks to all of you.  I hit Tab (rather than Enter, as Dinesh advised) when I followed the original instructions, so when I opened up the settings I found that "0.0.0.0" had been stored for the gateway.  I've put in the appropriate address and have the internet back.  A rookie move on my part!  I appreciate the advice!

---

### Post by sj1410 on 2011-01-12
> **JustGus said:**
> Thanks to all of you.  I hit Tab (rather than Enter, as Dinesh advised) when I followed the original instructions, so when I opened up the settings I found that "0.0.0.0" had been stored for the gateway.  I've put in the appropriate address and have the internet back.  A rookie move on my part!  I appreciate the advice!

Good Luck!!!!!!!

---

### Post by dineshs on 2011-01-13
Kindly mark the thread as solved via thread tools

---

