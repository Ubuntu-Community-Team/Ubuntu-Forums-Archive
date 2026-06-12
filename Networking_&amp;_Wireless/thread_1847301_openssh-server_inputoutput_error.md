---
title: "openssh-server input/output error"
date: 2011-09-20
forum: Networking &amp; Wireless
---

### Post by litspliff on 2011-09-20
when i login to my xubuntu 11.04 ssh box the shell session returns "input/output error" and drops the session. however, the tunneling functionality still works.

something similar happened under xubuntu 10.04, but the seesion didn't drop. almost every command would return "input/output" error. so i wiped the HD, re-installed 11.04 with openssh-server and ddclient, then moved ssh to a 5 digit port. two days later the shell sessions were dropping immediately.

i am somewhat concerned due to the fact that it has a public domain pointed at it all the time. 
maybe i am getting hit by an exploit?

how do i go about diagnosing the problem?
i have taken the box offline for now.

---

### Post by Dangertux on 2011-09-20
That issue actually has to do with stdio not the ssh service itself. You may have a failing hard disk. 

You might want to check

/var/log/syslog

---

### Post by litspliff on 2011-09-21
> **Dangertux said:**
>  You may have a failing hard disk. 

good thing i have about 30 10GB HDD's laying around!


HDD replaced. 
OS re-installed.

all good so far.

i'll report back after a few days of service.

many thanks, friend.


one bummer was that setting up the networking during the install created a situation where it disabled network manager on the connection and automatically assigned an IPV6 address (which i'd like to remove). i don't like any IPV6 traffic on my networks.

---

