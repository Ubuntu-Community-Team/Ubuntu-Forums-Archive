---
title: "drivers for Pritel 621B HSDPA  modem"
date: 2009-11-10
forum: Networking &amp; Wireless
---

### Post by janadaman on 2009-11-10
hi all..

I'm using Pritel 621B HSDPA modem and is not working with ubuntu 9.04. seems like problem with with the drivers. any one have the drivers for the modem pls tel me how to configure and add the drivers.
and make the modem working..

thanx...........

---

### Post by janadaman on 2009-11-11
hi all.... 
pls some one help to me fro find the driver for the HSDPA modem. its really really urgent
thanx all..............

---

### Post by pdc on 2009-11-12
I have done a google search on 

> ubuntu Pritel 621B HSDPA 

and you are about the only person in the world who google has heard of on this topic;

so you're pretty special! 

so you had better tell us about yourself: what country; what network;

plug your modem in and in a terminal type

> lsusb

and then 

> sudo tail -f /var/log/messages

and copy and paste the results back here

---

### Post by janadaman on 2009-12-02
> **pdc said:**
> I have done a google search on 

 

and you are about the only person in the world who google has heard of on this topic;

so you're pretty special! 

so you had better tell us about yourself: what country; what network;

plug your modem in and in a terminal type



and then 



and copy and paste the results back here
hi all..
thanx for replying..

I'm From Sri Lanka...
n I'm univercity student who is willing to learn and experiment about the ubuntu and who is doing degree specialized in computer systems networking.
Specially i need the moden to run the updates and install servers like Apache,DNS DHCP like wise..  but the problem is, since my modem cant recognize by the OS I'm stuck with those works.. 
i had run the 
> lsusb  
and no usb device were list down in the out put..
but once i plug huwavi modem and run the 
> lsusb
i had shown the details of that modem. 
since my modem is not recognized by the OS i was unable to do any kind of work with i preferred.

Finally i contact the vendors and they told me that the modem is not supporting to linux OSs. Modem only support to the Windows and MAC OSs only.

---

### Post by teward on 2009-12-02
which means that Linux and your modem won't work together.  simple as that.

---

### Post by pdc on 2009-12-02
I did tell you to give us this

> sudo tail -f /var/log/messages 

run this command

plug modem in

copy and paste sequence back here

---

