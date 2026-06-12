---
title: "reliance zte ac8710 on 9.04"
date: 2010-02-19
forum: Networking &amp; Wireless
---

### Post by sanmat on 2010-02-19
hey .. 
i was using wvdial to connect to the internet on my 9.04 using the reliance netconnect zte ac8710 modem until few days back when i ran the update manager and now it no longer works.. 
get the following error message : 


-->WvDial: Internet Dialer version 1.60
-->Cannot open /dev/ttyUSB0:No such file or directory
-->Cannot open /dev/ttyUSB0:No such file or directory
-->Cannot open /dev/ttyUSB0:No such file or directory

also when i try the pppconfig method for connecting it ,

it gives the following error 

/urs/sbin/pppd: In file /etc/ppp/peers/reliance: unrecognized option '/dev/ttyUSB0'

guess these errors are interrelated... am a noob . :)

somebody please help :)

---

### Post by alexfish on 2010-02-19
hi

not sure of this error

How ever we could try and see which tty ports are been used

from the terminal use this command and post the results

Code:


dmesg | grep -e "modem" -e "tty" 


thanks in advance

alexfish

---

### Post by somushiv on 2010-04-25
Even  My Dell XPS M1230 was showing 

-->WvDial: Internet Dialer version 1.60
-->Cannot open /dev/ttyUSB0:No such file or directory
-->Cannot open /dev/ttyUSB0:No such file or directory
-->Cannot open /dev/ttyUSB0:No such file or directory

I replaced Modem = /dev/ttyUSB0 line with Modem = /dev/tty0 Which I got from dmesg. Its working fine.

Cheers

SomuShiv

---

