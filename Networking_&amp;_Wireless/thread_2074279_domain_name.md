---
title: "domain name"
date: 2012-10-21
forum: Networking &amp; Wireless
---

### Post by ellankavi on 2012-10-21
Hello people,

I use ubuntu at home and recently installed Debian for my office server. In ubuntu, I had no problems remotely connecting as [email]user@hostname.domain[/email]name

But in debian (latest, v6), I am not able to connect in such a fashion. When I try : ssh [email]user@hostname.domain[/email]name, it says no such domain name exists. 

I tried to search online but i am not able to find any posts that are helpful. Could you people help me??

Thanks

---

### Post by cipherboy_loc on 2012-10-21
Are you trying to connect to a local server by hostname or a remote server?

Thanks,
Cipherboy

---

### Post by ellankavi on 2012-10-22
I'm trying to connect to a local server by hostname

---

### Post by cipherboy_loc on 2012-10-22
Ah, that explains it. Can you ping the computer by hostname? If not, post the contents /etc/hosts file?

---

### Post by ellankavi on 2012-10-23
Actually, scheduling an 'nsupdate' to crontab solved the problem. Don't know how ubuntu does it automatically and not debian because I could not find an nsupdate script in ubuntu's cron list!

Thanks for your update guys.

---

