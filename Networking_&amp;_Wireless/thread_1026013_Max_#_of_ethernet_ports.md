---
title: "Max # of ethernet ports??"
date: 2008-12-30
forum: Networking &amp; Wireless
---

### Post by amoeba13 on 2008-12-30
Is there a limit on the number of ethernet ports Linux will allow? I am trying to build a DMZ server with 6 ethernet ports(2 onboard and 4 on addon card). I have tried the following boards: DLink 4-port NIC card, Soekris 4-port NIC, and a RouterBOARD 4-port. I have also tried using two Intel dual-port Server NICs as well. What is happening is all show that they are linked, but I cannot ping from one of the six ports (usually the second one down from the top of the card), the other 5 work. I am using Ubuntu Server 8.10. Any help would be appreciated.

Thanks in advance,
Ray

---

### Post by mpokrywka on 2008-12-31
I have succesfully used linux box with 10 ethernet ports (1 built-in e100, 1 realtek 8139too and two 4 port sunhme).
Maybe your routing is wrong? Run your diagnostic ping, and on another console check on which interface packets leave/return (i.e. **tcpdump -ni eth0**).
Maybe you have some problem with interrupt lines?
Check how interrupts are assigned after all interfaces are up (**cat /proc/interrupts**).
You can also check for tx/rx errors by running **ifconfig**

---

### Post by amoeba13 on 2009-01-02
Found the problem was the pci-x port next to the pciexpress port. For some reason, with a card in that slot I would loose one of the ports on the 4-port NIC or would have 5k-10k ms ping times. Moving the card would eliminate the problem. Thanks for the help.

---

