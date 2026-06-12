---
title: "network connection problems"
date: 2009-06-09
forum: Networking &amp; Wireless
---

### Post by mistic8817 on 2009-06-09
Hello, 

I am quite new to ubuntu and linux in general.

Right now I am having a problem with network connections in ubuntu, I am not able to surf the internet nor does there seem to be any type of active connection as the network icon in the top right has a red x and oddly enough I cannot select a wired connection through it. I have gone into the network connections and set the connection to a static address (dhcp does not work if I were to set it to that). I verified that it was correct by typing "ifconfig" in terminal and it came back with eth0 having the correct ip address, netmask, etc. 

The odd thing is that being that the GUI is telling me there is no active network connection and the machine not able to browse the internet it is able to ping other computers within the network including the default gateway. I have also tried putting in a default route to get out of the network and still no dice. 

I am getting frustrated as the network in ubuntu has only worked less then 1/4 of the time that I have had ubuntu installed and seems to have a mind of its own dropping the internet connection out of the blue (when it is able to browse the net) with me not able to fix it and get it back online.

---

### Post by superprash2003 on 2009-06-09
have you tried to right click on that icon and clicking on "enable networking" ?

---

### Post by Iowan on 2009-06-09
Does **route -n** show the proper gateway?

---

