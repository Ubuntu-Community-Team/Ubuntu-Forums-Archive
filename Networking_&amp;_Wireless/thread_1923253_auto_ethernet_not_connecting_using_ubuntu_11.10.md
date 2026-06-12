---
title: "auto ethernet not connecting using ubuntu 11.10"
date: 2012-02-10
forum: Networking &amp; Wireless
---

### Post by andyboy on 2012-02-10
I have a dual boot machine and the ethernet connection has just stopped connecting whilst running Ubuntu  .Any help to solve this problem would be appreciated .

---

### Post by guyrichie@hotmail.com on 2012-02-10
Hello,

Do you mean the connection has failed all together... or... the connection does not connect automatically at boot?

If the latter click on the netwrok manager notification at the top left and select edit connections.  In this pop-up window there is a check box for automatic connection.  If the former, check dmesg for any issues with the hardware's driver - (do this by opening a terminal and tying dmesg and hitting enter).  Have a read through the output and determine if their is a problem with eth0.

Trust this get you going in the right direction.
Guy.

---

### Post by andyboy on 2012-02-10
guy ,

thanks for prompt reply , it doesn't connect at all and the automatic connection is ticked . 
in the terminal the it states that eth0 : no IPv6 routers present
any idea what else i can do ?

---

### Post by guyrichie@hotmail.com on 2012-02-10
Thats strange. It sounds as though the network card is recognized but just not fully working! Have you run the update manager recently? Perhaps a kernel update has caused this sudden failure?

---

### Post by andyboy on 2012-02-10
guy ,

i updated the windows installation this morning and ubuntu stopped connecting when i booted back into it , i really don't know what else to do ..... any ideas ?

---

### Post by guyrichie@hotmail.com on 2012-02-10
When you reboot do you have other linux kernel versions available i.e. 3.0.0-12. If so try booting into that to see if that restores your connection. 

Upgarding windows should have no effect on ubuntu.

Just out of interest try booting from the ubuntu live / install CD to double check that no extrenal mattets are causing this.  Try rebooting your router too, just to dbl chk.

---

### Post by andyboy on 2012-02-10
guy ,

i tried booting into older versions of ubuntu without success 
i restarted the router , then i tried a live cd of 10.10 
and nothing has helped but thanks for all you help 
andy

---

