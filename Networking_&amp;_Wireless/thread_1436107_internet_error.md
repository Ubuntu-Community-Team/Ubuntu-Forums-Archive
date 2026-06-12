---
title: "internet error"
date: 2010-03-22
forum: Networking &amp; Wireless
---

### Post by mastikhor_maddy on 2010-03-22
i am not able to access me internet.I am using ubuntu 9.04, i hav a dial up broadband connection.I connect my net by the following commands
sudo pppoeconf


and after sometime i get the following errors :

Mar 22 19:46:14 desktop pppd[2004]: Using interface ppp4
Mar 22 19:46:14 desktop pppd[2004]: Connect: ppp4 <--> eth0
Mar 22 19:46:19 desktop pppd[2004]: CHAP authentication failed: I don't like you.  Go 'way.
Mar 22 19:46:19 desktop pppd[2004]: CHAP authentication failed
Mar 22 19:46:19 desktop pppd[2004]: Connection terminated.



Mar 22 19:44:47 desktop pppd[4726]: No response to 4 echo-requests
Mar 22 19:44:47 desktop pppd[4726]: Serial link appears to be disconnected.
Mar 22 19:44:47 desktop pppd[4726]: Connect time 3.0 minutes.
Mar 22 19:44:47 desktop pppd[4726]: Sent 80446 bytes, received 149869 bytes.
Mar 22 19:44:53 desktop pppd[4726]: Connection terminated.
Mar 22 19:44:53 desktop pppd[4726]: Modem hangup

---

### Post by alexfish on 2010-03-22
hi

What is the make and model number of your modem and how is it connected to the computer

thanks in advance

alexfish

---

### Post by mastikhor_maddy on 2010-03-22
i dont have a modem.i have a broadband connection that requires a username and password

i hav uploaded images of how i connect my internet in windows

---

### Post by mastikhor_maddy on 2010-03-22
guys please help me its urgent

---

### Post by alexfish on 2010-03-22
hi

if you are using LAN connection

can you have a look here

[https://bugs.launchpad.net/ubuntu/+source/pppoeconf/+bug/251241](https://bugs.launchpad.net/ubuntu/+source/pppoeconf/+bug/251241)

link to debian 

[http://packages.debian.org/stable/net/pppoe](http://packages.debian.org/stable/net/pppoe)

it would be possible to save this on hard drive or usb stick/ then install when in Ubuntu
also check the dependencies 

regards

alexfish

---

