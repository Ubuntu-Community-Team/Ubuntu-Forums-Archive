---
title: "Route ssh over wireless connection"
date: 2008-12-09
forum: Networking &amp; Wireless
---

### Post by awreneau on 2008-12-09
I have the following setup:

Laptop
   Wired Connection 11.5.xxx.xxx
   Wireless Connection 192.168.xxx.xxx

I run FF and GAIM proxied thru a SSH connection to my home server so traffic is encrypted.  Yet I have a wired connection that will keep me on the LAN so I can find local devices.  

Is it possible to route SSH traffic to a specific NIC while leaving all other traffic untouched, unless I have it set to run over the SSH connection?  I want to run SSH over the wireless connection.

I've googled this and found hints of how this might be done but nothing concrete, whats more, my searches are broad b/c I'm not sure how to phrase the search.


I connect to my home server w/ the following command.
ssh -p 2222 -D 9999 me@IP-ADDRESS -C

Then I configure GAIM and FF to use a SOCKSHOST V5

Help would me much appreciated.

---

### Post by kevdog on 2008-12-09
Lets just back up a second.  Do you have a ssh server up and running, and if the answer is yes, over what port is it running on?

---

