---
title: "Ubuntu 8.04 blocking my home network"
date: 2009-01-03
forum: Networking &amp; Wireless
---

### Post by jrogde on 2009-01-03
I am running ubuntu 8.04 and everything is working without problems except for an extremely annoying issue.

All of a sudden I am not able to contact my ubuntu desktop in any way. The screen is either frozen or all black. Neither one of the other computers on my LAN (cabeled or wireless) are able to communicate with the internet. When I look at my router there seems to be continuously traffic from/to my ubuntu desktop(DLink DIR-655 (I have tried using another router too but the same problem occured)) . I am using a cable to this computer, and if I unplug the cable from my router, all of the other devices are able to connect to the internet again. There could be days or just hours between each time the problem occurs. The only way to get the ubuntu desktop to work again is to do a hard restart.

I have looked through the different logs under /var/log without finding anything obvious. Has anyone experience anything similar or have a clue about how to go by to find a solution to this problem?

---

### Post by superprash2003 on 2009-01-03
is ubuntu acting as a gateway or anything of that sort??.. post output of sudo iptables -L from the terminal

---

### Post by jrogde on 2009-01-03
I'm not sure what to make of it, but here is the output:

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

---

### Post by superprash2003 on 2009-01-05
it could have something to do with the dlink wifi card.. what happens when you try via LAN..

---

### Post by jrogde on 2009-01-06
I am connected via LAN. (The DLink device i reffered to was my router)

When it happend last time, i checked the router log there were no traffic registered to any unknown ip addresses. By inspecting the number of packages sent and received, the traffic seemed to be outbound, but the number of packages did not increase dramatically.

I think it might be a hardware problem, and have decieded to buy a new network card and check that possibility. Thank you for your time superprash2003 :P

---

### Post by superprash2003 on 2009-01-06
or you could try resetting your dlink.. or check the web incase that model has that issue and you could get a firmware update if available..

---

### Post by jrogde on 2009-01-11
I have tried resetting my router, I have even replacing it after it got struck by lightning :-) The same issue was there both with the old and the new router.

I have now bought a new lan card. A CNet PCI Gigabit Ethernet Adapter 32-bit PCI, Realtek RTL8169S.

After inserting it and disabling the onboard lan on my ASUS M3N78-VM motherboard, I was hoping for the new LAN card to be autodetected. Of course it wasn't :-(

Any ideas out there?

---

