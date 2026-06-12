---
title: "How to connect to computers directly using cross cable.?"
date: 2009-11-06
forum: Networking &amp; Wireless
---

### Post by Harshana on 2009-11-06
Hello everybody.........

I tried to connect my HP mini directly to another ubuntu running computer through Ethernet cross cable by setting IPs and Subnetmasks in
 **Preference => network connections => wired => Add** in both computers (As it is the way using in windows).
But it didn't work.
How should i do this ?
I couldn't tell that i use UNR & other one use Ububtu 8.04.
Thanx

---

### Post by Iowan on 2009-11-06
It should work... use **ifconfig -a** to verify that the addresses are in the same subnet. Try **pinging** the other machine (by address). You *might* need to set the gateway address as being the other machine (not so sure about that one...)

---

### Post by Harshana on 2009-11-10
> **Iowan said:**
> It should work... use **ifconfig -a** to verify that the addresses are in the same subnet. Try **pinging** the other machine (by address). You *might* need to set the gateway address as being the other machine (not so sure about that one...)

I did them all.Pinging was also not worked.Cable is also ok as it worked with windows.I dont understand y.

---

### Post by Devi1903 on 2009-11-10
Can you post the read out from "ifconfig -a" here.

---

### Post by fargle on 2009-11-10
I've found that, unless you're doing it an awful lot, it's easiest to just let Network Manager fail getting an IP address, then manually set one from a command prompt with " sudo ifconfig eth0 192.168.26.1 netmask 255.255.255.0" and the same on the other machine except use 192.168.26.2.

---

