---
title: "Wireless Keeps not refreshing / freezing"
date: 2009-04-13
forum: Networking &amp; Wireless
---

### Post by kehon on 2009-04-13
i goto college and so when i move around in the building (also happens at home for different routers) i get disconnected(normal) then when i try to reconnect the network adapter seems like it hasnt refreshed all it shows is the old network so i disable then reenable and that doesnt work either because then no acces points show up how do i refresh the adapter from commandline and is there a fix for this

---

### Post by mr dodo on 2009-04-13
Actually i habe the same problem 
please if anyone know the fix for this issue 

a lot of thanks

---

### Post by mr dodo on 2009-04-13
this is some useful commands for the networking 

Network
ifconfig - show network information
iwconfig - show wireless information
**sudo iwlist scan - scan for wireless networks**
sudo /etc/init.d/networking restart - reset network
(file) /etc/network/interfaces - manual configuration
ifup interface - bring interface online
ifdown interface - disable interface

---

### Post by kehon on 2009-04-23
could i get some more post on this and thanks for the reply above i will try but this is a really annoying problem and i hope to fix it but need some help

edit: i tried those commands when i had the problem and it didnt do anything all it said was that there were no wireless networks when i know its here(can see on psp)

---

