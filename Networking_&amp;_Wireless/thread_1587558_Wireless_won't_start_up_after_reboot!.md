---
title: "Wireless won't start up after reboot!"
date: 2010-10-03
forum: Networking &amp; Wireless
---

### Post by earfer on 2010-10-03
Hey everyone, 

So what I'm trying to do is to get my wireless working again after reboot. 
Here is the detail.

I have a laptop that connects to the internet (wireless), but lately I've been using a program call PMS (PS3 Media Server) which help me stream videos to the PS3. **The laptop connects to the PS3 via ethernet cable.**
Whenever I connect to the PS3 via the ethernet cable, the internet will cut off. 

> Laptop Internet --> Connect Ethernet Cable (That is also connected to the PS3) --> Laptop Internet *CUTS OFF*[NOTE]
The PS3's IP Address is 192.168.1.10
The PC's Ethernet IP Address is 192.168.1.9
The PC's Wireless IP Address is 102.168.1.4

Then a friend of mine, gave me this code to copy over to etc/network/interfaces. This allowed the laptop internet to workwhile the PS3's ethernet cable is connected.

```

auto lo eth0
iface lo inet loopback
iface eth0 inet static 
    address 192.168.1.10
    netmask 255.255.255.0

```

But whenever I restart the computer. The wireless will not start up, leaving me with no internet at all.
The only way to get internet again is to reset the code that I typed in back to default and restart.

[NOTE]
My network device is all working, the problem is the mapping of the interface settings???

Thanks in advance~
Mooshi/Earfer~

---

### Post by earfer on 2010-10-04
*Bump*

Can anyone help me with this problem?

---

### Post by xyverz on 2010-10-05
This is shown as solved, but there's no solution here.  I've never been able to get networking going at startup in any of the 10.x releases of ubuntu.  Any suggestions?

---

