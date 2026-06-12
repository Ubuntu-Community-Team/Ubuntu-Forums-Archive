---
title: "Wireless suddenly not working/detected???"
date: 2010-03-21
forum: Networking &amp; Wireless
---

### Post by kimw08 on 2010-03-21
Hi everyone

I am running Karmic on a Compaq Presario V3000 and this morning my wireless card is not being detected by Ubuntu's NetworkManager. I have no idea what caused this... literally, it was working when I shutdown my laptop last night. 

When I right-click the NetworkManager icon in the panel it does not show "Enable Wireless" (only "Enable Networking"). When I run ifconfig in terminal it shows my wireless card as being there (UP Broadcast Multicast). One weird thing - on the front of the laptop there is an LED which lights up blue when the card is working (ie normally), but right now it is orange (ie, if you flick the switch on the front of the laptop to toggle the wifi on or off... I have toggled it back and forth but nothing changes!). 

Any help would be much appreciated... thanks!

---

### Post by 666f6f on 2010-03-21
What are the contents of /etc/network/interfaces?

Also, lspci and lsmod output might help.

---

