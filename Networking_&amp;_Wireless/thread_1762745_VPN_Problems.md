---
title: "VPN Problems"
date: 2011-05-19
forum: Networking &amp; Wireless
---

### Post by Atticus92 on 2011-05-19
Alright, So I have Ubuntu Server 10.04 running as a samba server and a VPN server using PPTPD. I am trying to connect two users to the VPN, which I am running Windows Ultimate on one, and Windows Home Premium.

Connecting to the VPN server from any location, I get an error 619 on the windows machines, and I have googled for what feels like days about the error and can't find a working solution.

I look in the /var/log/messages file and see:

***
Plugin /usr/lib/pptpd/pptpd-logwtmp.so loaded.
pppd 2.4.5 started by root, uid 0
Using interface ppp0
Connect: ppp0 <--> /dev/pts/1
Modem hang up
Connection terminated
Exit.
***

Does anyone have any ideas what could be wrong?

---

### Post by UNOE on 2011-05-20
> **Atticus92 said:**
> Alright, So I have Ubuntu Server 10.04 running as a samba server and a VPN server using PPTPD. I am trying to connect two users to the VPN, which I am running Windows Ultimate on one, and Windows Home Premium.
 
Connecting to the VPN server from any location, I get an error 619 on the windows machines, and I have googled for what feels like days about the error and can't find a working solution.
 
I look in the /var/log/messages file and see:
 
***
Plugin /usr/lib/pptpd/pptpd-logwtmp.so loaded.
pppd 2.4.5 started by root, uid 0
Using interface ppp0
Connect: ppp0 <--> /dev/pts/1
Modem hang up
Connection terminated
Exit.
***
 
Does anyone have any ideas what could be wrong?
 
I'm trying to just get a VPN server up.
[http://ubuntuforums.org/showthread.php?p=10842141](http://ubuntuforums.org/showthread.php?p=10842141)
I'm sure you already tried this but your ports are forwarded right ?

---

### Post by Atticus92 on 2011-05-21
> **UNOE said:**
> I'm trying to just get a VPN server up.
[http://ubuntuforums.org/showthread.php?p=10842141](http://ubuntuforums.org/showthread.php?p=10842141)
I'm sure you already tried this but your ports are forwarded right ?

As far as I know. I forwarded both 1723 and 500 to the server.

---

