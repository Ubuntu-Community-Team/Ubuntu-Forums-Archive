---
title: "UFW weirdness"
date: 2009-10-25
forum: Networking &amp; Wireless
---

### Post by mike30188 on 2009-10-25
Hey guys. I'm not sure if UFW is functioning properly. 

I have the following rules set:

Status: active

To                         Action  From
--                         ------  ----
80/tcp                     ALLOW   Anywhere
53/udp                     ALLOW   Anywhere
38501/tcp                  ALLOW   Anywhere
38502/tcp                  ALLOW   Anywhere

---------------------------------------------------------

But notice what happens when I run an Nmap scan on the first 1024 ports:

Not shown: 997 filtered ports
PORT    STATE SERVICE
25/tcp  open  smtp
80/tcp  open  http
110/tcp open  pop3

----------------------------------------------------------

Should ports 25 and 110 be open if IPTables is setup properly?

---

