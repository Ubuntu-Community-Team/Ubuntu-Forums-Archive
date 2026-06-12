---
title: "issues with dhcp and  ethernet cards"
date: 2009-02-17
forum: Networking &amp; Wireless
---

### Post by schnem on 2009-02-17
My router had a hardware fault
and while I was trying to diagnose the fault 
my Ubuntu 8.04 box stopped its IP connectivity
I was in and out of the network configuration gui and  editing the interface file.
 when I did the ifconfig command it said my box had  an ip address of 169.254.6.115 which I think indicates that there is no DHCP server.
I tried setting up a static ip address any but i could not ping a thing

In the end after  looking at a post in this  forum
I unplugged the ethernet cable 
downed the box and pulled out the power plug from the power supply on the PC .

Bingo it worked !!!! I had ip connectivity 
I have posted this so someone else  will save about 10 hours of mucking about

- Marty Moose

---

