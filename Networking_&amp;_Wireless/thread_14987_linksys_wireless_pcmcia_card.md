---
title: "linksys wireless pcmcia card"
date: 2005-02-11
forum: Networking &amp; Wireless
---

### Post by eendz0r on 2005-02-11
i installed ubuntu for 4 days now, during the install the wireless pcmcia card was inserted but i just thinks he doesnt recognice this one, on the linksys site you dont see any linux driver tho.

Its a Linksys wireless-G notebook adaptor WPC54G ver. 1.2 and made by cisco

i tried everything but is doesnt work, ubuntu shows only my eth0 and can not find my wireless pcmcia card. so if you guys could help me ? :p

thanks alot

---

### Post by mendicant on 2005-02-11
Are you hearing any beeps?  You should hear two high beeps if the card is recognized.

---

### Post by poofyhairguy on 2005-04-11
[QUOTE=eendz0r]i installed ubuntu for 4 days now, during the install the wireless pcmcia card was inserted but i just thinks he doesnt recognice this one, on the linksys site you dont see any linux driver tho.

Its a Linksys wireless-G notebook adaptor WPC54G ver. 1.2 and made by cisco

i tried everything but is doesnt work, ubuntu shows only my eth0 and can not find my wireless pcmcia card. so if you guys could help me ? :p

thanks alot[/QUOTE]

You need ndiswrapper

---

### Post by joplass on 2005-04-12
Search the forum for related thread.  I am working on the same problem right now but some people on the forum have been successful making WPC54G work with Hoary thru ndiswrapper mentioned above by poofyhairguy.  Also check on Wiki from the main page of the forum.

---

### Post by rmeekers on 2005-04-14
This is the driver you need for ndiswrapper:

[ftp://ftp.linksys.com/pub/network/WPC54Gv4_driver_rev_1.22.1.2004.zip](ftp://ftp.linksys.com/pub/network/WPC54Gv4_driver_rev_1.22.1.2004.zip)

It works perfect with WPC54G v1.2

Kind Regards

Ronnie

---

### Post by az on 2005-04-14
unzip the above file from a teminal

unzip WPC*
cd into the directory that it creates (if it creates one)
look fot the .inf file
ls *.inf
sudo ndiswrapper -i <file.inf>
sudo modprobe ndiswrapper

confugre your card in the network tool...

---

