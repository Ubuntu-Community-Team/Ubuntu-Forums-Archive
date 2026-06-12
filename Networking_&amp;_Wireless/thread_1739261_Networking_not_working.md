---
title: "Networking not working"
date: 2011-04-25
forum: Networking &amp; Wireless
---

### Post by Veresh on 2011-04-25
Friends,

I was using ubuntu happily for 6 - 8 months but yesterday I updated to 10.10 from 10.4 and now i cant get networking working, I search on the forums but no help.
Please let me know what did i do wrong I am completely helpless.
Machine is 64bit HP HDX 16.

Regards
Veresh

---

### Post by spike_seti on 2011-04-25
what you may have to is reboot ubuntu 10.10, but you may not have to do that if you see all the computers on your network in the network file in ubuntu, if you do just install samba 4 in the terminal
 
sudo apt-get install samba4 
 
and you will be networking in notime and you may not have to change anything in the config file. but if you reboot ubuntu to start the network connect to the internet when you do the install and then still install samba4

---

### Post by Iowan on 2011-04-25
Does **ifconfig -a ** (from a terminal) show the interface with an IP address?

---

