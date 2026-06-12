---
title: "print server setup"
date: 2010-08-14
forum: Networking &amp; Wireless
---

### Post by fubar65 on 2010-08-14
Hi, I have started playing with xubuntu as I find Windows boring now..

A while back I bought a print server, an Edimax ps-3205U, it has served me well in Windows and I have it sort of working in xubuntu..

I have an HP LaserJet 4L hooked up to lpt1, which is a paralel port on the server, it also has 2 USB ports, I have an HP DeskJet 1220c hooked up to one of the USB ports, it is labeled as lpt2.

I have the laserjet printing fine but every time I try to print to the deskjet it prints garbage out of the laserjet..

I am using ipp to connect to the printers, for the laserjet the address is;
socket://192.168.2.199/lpt1
for the deskjet the address is;
socket://192.168.2.199/lpt2

I am not sure if this is even correct for the laserjet but it works so I figured I would run with it..

there is a linux source code available to be downloaded, which I have but I have no clue what to do with it or if it will even help me..

so, am I close or totally wrong on the address / setup, I am not sure if I need to include the port number in it or not, I have tried with and without and didn't notice any difference.

Thanks.

---

### Post by drdos2006 on 2010-08-14
This might help.

[http://ubuntuforums.org/showthread.php?p=9714107#post9714107](http://ubuntuforums.org/showthread.php?p=9714107#post9714107)

regards

---

### Post by fubar65 on 2010-08-15
I have tried this, every time I go to make a change it asks for a user name and password for CUPS.
I have no idea what it is.. not my login apparently.

I am not sure if this is relevant as the server is working, my linux pc just prints everything to the laserjet..

I can connect to the print server via it's IP and it is configured correctly..

I will keep playing, if there's any other info I should give, please let me know.

Thanks again.

---

### Post by fubar65 on 2010-08-21
I am getting frustrated with this now..

anyone have any suggestions or advice for me to try?

thanks.


solved with this:
[http://ubuntuforums.org/showpost.php?p=8333760&postcount=2](http://ubuntuforums.org/showpost.php?p=8333760&postcount=2)

---

