---
title: "Firestarter blocks 192.168.1.1 and 100??"
date: 2010-07-23
forum: Networking &amp; Wireless
---

### Post by deskman on 2010-07-23
Hello everybody! I have wireless connection between my router and PC. It is the only computer connected. Sometimes Firestarter blocks ports 1900 and 6771 from 192.168.1.100 IP address and sometimes port 68 from 192.168.1.1 IP. I'm a bit confused because 192.168.1.100 is the IP addres i use to open ports in router and 192.168.1.1 is used to access the router settings.. Please, help me to understand what are these and what shell i do? Allow? Deny?

---

### Post by n.hinton on 2010-07-23
You could try: Firestarter -> Edit -> Preferences -> Advanced Options

And uncheck any checked checkboxes and logout and in or restart.

---

### Post by dca on 2010-07-23
Some wireless routers do not allow wireless connections for configurations from anywhere.  You have to CAT5 cable direct into router and disable that security function.  Should be the same as the setting for allowing two or more devices on your network to connect to each other...
 
...if the issue not w/ router, than yeah, maybe Firestarter is culprit.

---

### Post by deskman on 2010-07-23
yes firestarter is the problem but i generally mean r these connections safe?

---

### Post by n.hinton on 2010-07-23
It was the only way I could make my Ubuntu 'windows network' visible, and I've had no problems.

---

### Post by dca on 2010-07-23
I'm drawing a picture in my head what you're telling me, if it's within your wall (router/network) then I guess it's fine.
 
Long story, short:  IPtables (Linux kernel based firewall) is a pain to configure, so Firestarter is a front-end GUI program to that.  Recently Ubuntu added UFW which is a CLI-based front-end to IPtables to make firewalls easier to configure using *sudo ufw service allow* instead of the long drawn out commands...
 
On all my Ubuntu machines headless, PC, desktop, etc running Server vers or Desktop first thing I do on server is issue *sudo ufw enable* to let Ubuntu Server know I'm using that as my firewall handler and to activate.  On desktop/laptop, I install GUFW which is the GUI graphic front-end to UFW.  For me being lazy and still not knowing all their is to know w/ IPtables AFTER 10+ G** D*** years, this has been a life-saver.
 
You can try removing Firestarter, installing GUFW and after install, see what that references as the open/closed ports based on what IPtables is indicating...

---

### Post by deskman on 2010-07-25
4 me, firestarter is simpler... but maybe it's more security question i mean it doesn't matter what kind of GUI i have.. fire starter or guwf, i just don't know what to do, allow 192.168.1.1 and 100 or not?

---

### Post by n.hinton on 2010-07-25
The IP address 192.168.1.0 represents the 192.168.1.x range of addresses where x is between 1 and 255. 192.168.1.0 is your private IP network.

Providing your router is using say WPA & WPA2 security you shouldn't have any problems.

---

