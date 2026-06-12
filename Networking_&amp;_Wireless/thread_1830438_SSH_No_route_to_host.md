---
title: "SSH No route to host"
date: 2011-08-21
forum: Networking &amp; Wireless
---

### Post by davethewave83 on 2011-08-21
When I try to SSH From Linux to Linux I get SSH error No Route To Host. 

When I try to SSH From Windows using PuTTY to Linux it connects fine. 

the error must then be on the client side of the linux software. Any ideas on a fix? Thanks! 

I download puTTY for Linux also, and tried that (Linux/Putty to Linux) it gave me the no route to host error.

---

### Post by bholzer on 2011-08-21
I had the same issue, but only when to computer I was trying to connect to was hibernating or asleep.

All I had to do was move the mouse on the computer I was connecting to.

This was linux to mac and linux to linux.

---

### Post by papibe on 2011-08-22
One of the reasons that that is happening is when the name of the machine isn't being recognized by your DNS.

Could you post the result of these commands?
```
$ ping destination

$ nslookup destination

$ ping destination.local
```
Replace 'destination' with the name of the machine you're trying to connect.

Regards.

---

### Post by lisati on 2011-08-22
Yup, been there!

I've had "No route to host" in two main types of situation, both of which have been touched on in previous responses. Typically I've either made a typo in the details I've put in, e.g. wrong IP address or host name, or the machine I'm connecting to isn't available, e.g. hibernating, rebooting or some such problem.

---

### Post by bholzer on 2011-08-22
Also forgot to say that sometimes the ip of the host will change. Happened to me recently causing quite a bit of confusion!

---

### Post by meesha on 2013-03-24
For anyone who's not so fluent in Ubuntu/SSH: 
This may be because there is already a "fingerprint" assigned the requested ip. Which means another connection used this ip. SSH stores the fingerprint (certificate) of the connected host for every ip-adress in the file /home/yourusername/.ssh/known_hosts. If already an entry with another fingerprint for the requested ip exists in the file, SSH refuses to connect, because it compares the ip's - not matching - fingerprint. You may resolve that by deleting the accordingly entry from the file, or - not recommended for productive enviroments - delete the whole file.

---

### Post by travalon on 2013-03-24
so, following meesha's statement, static ip addresses should fix that problem.

---

