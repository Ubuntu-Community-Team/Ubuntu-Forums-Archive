---
title: "Can't see the name of my machine"
date: 2009-03-03
forum: Networking &amp; Wireless
---

### Post by borobudur on 2009-03-03
Hi, I should mount a network directory in my company. 

The administrator tells me he can't give me the permission on my machine to mount because he doesn't see the name of my machine. Instead he sees my IP. He says that with other linux systems from other people he doesn't have this problem. 

Do you know where to fix that?

---

### Post by gvr2600 on 2009-03-03
hostname - show or set the system's host name 

hostname [-v] [-F filename] [--file filename] [hostname]

---

### Post by borobudur on 2009-03-03
Unfortunately this didn't solve the problem. 

I see the correct name of my machine with *hostname* but still the admin says that he sees just the ip

---

### Post by terazen on 2009-03-03
It sounds like your machine is supposed to register itself to dns.  If your IT guy says that's what is supposed to be happening then you could try the dhclient setting from this url with your hostname.
[http://ubuntuforums.org/showthread.php?t=122002&page=2](http://ubuntuforums.org/showthread.php?t=122002&page=2)

/etc/dhcp3/dhclient.conf:
```
send fqdn.server-update on;
```

---

### Post by borobudur on 2009-03-06
Our super hero, the admin, found the solution, with the additional stuff in the -o flag it works:
```
-o 'username=me,domain=domain.tld,port=999,netbiosname=mymaschine'
```But thanks anyway for your help!

---

