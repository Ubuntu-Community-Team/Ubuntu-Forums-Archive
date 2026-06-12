---
title: "connect ubuntu 8.04 to internet using BSNL dataone connection"
date: 2008-12-28
forum: Networking &amp; Wireless
---

### Post by nithuldershs on 2008-12-28
I,m a bsnl dataone broadband user.
 cn connect to internet from windows,but I was unable to connect from ubuntu
:confused:

I used network manager to set hosts static IP
as 192.168.1.2
subnet mask 255.255.0.0
Gateway address as 192.168.1.1

I configured my connection using command
"sudo pppoeconf" 
And when I gave command plog in terminal,
I got the folowing response

```
nit@nithul-desktop:~$ sudo pppoeconf

[sudo] password for nit: 

Plugin rp-pppoe.so loaded.

nit@nithul-desktop:~$ plog

Dec 28 10:34:34 nithul-desktop pppd[7364]: Plugin rp-pppoe.so loaded.

Dec 28 10:34:34 nithul-desktop pppd[7366]: pppd 2.4.4 started by root, uid 0

Dec 28 10:34:34 nithul-desktop pppd[7366]: PPP session is 9160

Dec 28 10:34:34 nithul-desktop pppd[7366]: Using interface ppp0

Dec 28 10:34:34 nithul-desktop pppd[7366]: Connect: ppp0 <--> eth0

Dec 28 10:34:34 nithul-desktop pppd[7366]: CHAP authentication failed: Invalid CHAP-Password

Dec 28 10:34:34 nithul-desktop pppd[7366]: CHAP authentication failed

Dec 28 10:34:34 nithul-desktop pppd[7366]: Connection terminated.


```

It says that CHAP authentication failed.
Why is it so?
I gave the same username and password for logging
into internet from windows,while I configured pppoeconf.

---

