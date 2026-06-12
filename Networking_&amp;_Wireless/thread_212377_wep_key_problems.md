---
title: "wep key problems"
date: 2006-07-09
forum: Networking &amp; Wireless
---

### Post by ronoc on 2006-07-09
Hi folks,
My wireless works fine once the network is wide open. 
I have attempted to set a wep key but the laptop (sat pro A100) then fails to pick up the connection. I am running dapper 6.06. Anyone have any suggestions as to what to do. Linux newbie here...

---

### Post by harishg on 2006-07-09
Two possible things:
1. There are two ways of entering the code ascii or hexadecimal.Make sure you make the right choice.

2.In case you have the firewall (firestarter) installed check if it is not blocking the ports.Do you have openssl installed.If not get it from apt repositories using synaptic.

---

### Post by ronoc on 2006-07-10
I have OpenSSL installed and no firestarter.
The config management tool for the netgear router gives me 4 options which it randomly generates from a key (in text which I input) I choose one of these options. The keys look to be  hex e.g  aabb33ccddff kind of thing. On the wireless config I am certain to enter the hex key as hex...
Anything I can try to narrow it down. 
What is the equivalent of getting what ip the router has assigned to me in ubuntu
Win32 - ipconfig
Ubuntu ?
i have used ifldown and iflup to try an reinitialize it but alas to no avail.

---

### Post by kwalters on 2007-07-10
I am having a similar problem with my Belkin router/modem and a Belkin USB wireless dongle on this Ubuntu Feisty machine.  Everything works fine as long as I have no encryption,  Every differnt effort to use WEP has gone wrong and gives me no network available, a very slow machine and a  red cross at the bottom of the network icon at top of screen.

My router offers encryption on or off and 2 different flavours of WEP:  64 bit or 128 bit.  In Windows I always used 128 bit with an ascii passphrase 7 digits long.  I can also select the key for the wep (I  use key 1, the default for my router)  There is also a channel control and I leave it where the machine puts it at Channel 11.

What confuses me is that I can see no way of selecting whether I am looking for 64 bit or 128 bit WEP in Ubuntu  (I use the graphical interface, despite the dire warnings on  this forum)   In other configuration programs there is a choice of open key, shared key etc.  I use open key in Windows and in the router control.

Can anyone take us a bit further on this. I have heard that lots of people have problems with WPA, so I am ignoring it.  Others claim that Ubuntu can only cope with 64 bit WEP.  I have read about (and tried) various suggestions of entering in ascii rather than hex (and vice versa.  Some people claim that pass phrases must be EXACTLY 5 or 13 letters long.  I do feel nervous running an open system; from here I could, if I wished, use at least 3 neighbours' open system

KW

---

