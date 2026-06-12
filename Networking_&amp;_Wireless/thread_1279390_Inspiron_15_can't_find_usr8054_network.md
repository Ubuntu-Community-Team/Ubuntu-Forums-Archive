---
title: "Inspiron 15 can't find usr8054 network"
date: 2009-09-30
forum: Networking &amp; Wireless
---

### Post by lzboy4jake on 2009-09-30
I am running ubuntu jaunty 64 bit on my dell inspiron 15 and have been trying to connect to my wireless home cable network.  When I open up the networks drop-down menu my computer won't even detect the wireless network.  I cannot figure out what the problem is.  I am not to savvy with networking yet so "idiot's guide" advice would be appreciated.

---

### Post by kreggz on 2009-10-03
try this:

[http://linux.dell.com/wiki/index.php/Products/Client](http://linux.dell.com/wiki/index.php/Products/Client)

---

### Post by dukehunter1 on 2009-10-03
Well I got the computer to find the network but when I click it to connect it brings up the WEP authentication screen, I type in the key, it acts like it's finishing up the connection but then it just opens up the authentication screen again and it just goes around in circles.

---

### Post by kreggz on 2009-10-03
if you are familiar with the terminal type this in after you tried to authenticate:

dmesg

and

cat /var/log/wpa_supplicant.log


there might be a clue in those logs

Also, that page I linked has a modified version of Ubuntu for Dell machines.

---

