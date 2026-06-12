---
title: "Ndiswrapper"
date: 2006-07-13
forum: Networking &amp; Wireless
---

### Post by SupremeSpike on 2006-07-13
whenever I start up ubuntu I have to reenable the wireless card by issuing the sudo modprobe ndiswrapper command.  How might I allow my laptop to have the card auto enabled?  Thanks for any help you could offer.

---

### Post by Dr. Nick on 2006-07-13
add "ndiswrapper" to the top line of /etc/modules, save it and it should load on startup

sudo gedit /etc/modules

---

### Post by GTvulse on 2006-07-13
The Way To Do It (tm) is to create a file called ```
/etc/modprobe.d/ndsiwrapper
``` and add to it the magic line: ```
alias wlan0 ndiswrapper
```, in fact, if you just type ```
sudo ndiswrapper -m
``` in a terminal window, that file will be created automatically by the ndsiwrapper admin utility. One has to wonder if you read the docs... ;-)

---

