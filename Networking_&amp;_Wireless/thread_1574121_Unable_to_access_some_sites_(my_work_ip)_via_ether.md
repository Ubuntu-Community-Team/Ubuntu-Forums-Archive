---
title: "Unable to access some sites (my work ip) via ethernet connection"
date: 2010-09-13
forum: Networking &amp; Wireless
---

### Post by C-free on 2010-09-13
Greetings,

Unable to access our site via eth0. Can access the same site, via same ISP on wireless laptop, or via eth0, but using ip annonymizer service. 

Have a feel that it could be something obvious, but after digging through Modems firmware I am running out of ideas. Please help.

Thank you.

---

### Post by gordintoronto on 2010-09-13
Any time I have had this type of problem, it turned out to be the DNS servers. To see what your DNS servers are, open Accessories, Terminal, and Paste this command in:
cat /etc/resolv.conf

You may notice that it changes between your wireless and wired connections.

---

### Post by C-free on 2010-09-13
Thanks for advice. Fixed it a minute ago by using proxy server as suggested by my provider to work around this problem.

---

### Post by C-free on 2010-09-13
Cant access some things by proxy(eg server/mail),and the issue seems to be from inability to access certain port that the hoster uses. 

How should the right port be enabled?

---

