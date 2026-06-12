---
title: "debian sid connects to network but i have no internet!"
date: 2009-09-19
forum: Networking &amp; Wireless
---

### Post by jackgu1988 on 2009-09-19
hi! i am running debian sid on an hp hdx 16 (64 bit) with kde 4.3. i always install new updates and my last update was 2 days ago! now when i booted i could connect to the internet but when i try to visit a web address or even run apt-get update, i get nothing! i tried both wicd and kdenetworkmanager but they don't work! i also tried wifi and ethernet and still nothing! also it can not be the network because i can connect using an acer aspire one with debian sid and gnome. i can also ssh to the hp through my acer but still apt-get update does not load! before the shuting down my hp the last time i had internet working i modified /etc/hosts. could this be the problem?

my /etc/hosts looks like:

```
jack@debian:~$ cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 debian.local debian

# The following lines are desirable for IPv6 capable hosts
::1 localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```

while before changing it looked like:

```
jack@debian:~$ cat /etc/hosts~
127.0.0.1	localhost.localdomain localhost
127.0.1.1	debian

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

it is the same both on my hp and my acer but the acer has connection!

thank you,
jack

---

### Post by jackgu1988 on 2009-09-19
ps: i also can not ping any website.

---

### Post by utnubuuser on 2009-09-19
did you make a backup of your hosts file before changing it?

---

### Post by jackgu1988 on 2009-09-19
yeah but if i restore it then the sendmail application will have a problem. i will check if the internet works when i restore it and if yes i will check for a solution for sendmail. i ll inform you when i do so!

---

### Post by jackgu1988 on 2009-09-19
nothing changed even now that i reset my /etc/hosts :(

---

### Post by Sef on 2009-09-20
moved.

---

### Post by jackgu1988 on 2009-09-20
problem solved here: [http://forums.debian.net/viewtopic.php?f=5&t=45312](http://forums.debian.net/viewtopic.php?f=5&t=45312)

---

### Post by tryinghard on 2010-01-08
I'm just wondering what is the name of ubuntu 9.10?
Thanks
tryinghard

---

