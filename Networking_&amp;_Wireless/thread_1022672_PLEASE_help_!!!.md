---
title: "PLEASE help !!!"
date: 2008-12-27
forum: Networking &amp; Wireless
---

### Post by mrsozzy on 2008-12-27
:confused:I have not a clue as to how to connect to to the internet. I have a pc and just got a dell mini 9 and have a router but it's not working. any suggestions?? what do you use? THANKS!!!

---

### Post by namdung on 2008-12-27
> **mrsozzy said:**
> :confused:I have not a clue as to how to connect to to the internet. I have a pc and just got a dell mini 9 and have a router but it's not working. any suggestions?? what do you use? THANKS!!!

Firstly, Pls avoid cross posting.
The other post : [http://ubuntuforums.org/showthread.php?t=1022637](http://ubuntuforums.org/showthread.php?t=1022637)

Can u pls give more details? Is it a Wireless Router? Model no? Do u know the IPs for the gateway IP, ur PC's and the DNS? Is ur PC able to connect to the Internet?

---

### Post by mrsozzy on 2008-12-27
> **namdung said:**
> Firstly, Pls avoid cross posting.
The other post : [http://ubuntuforums.org/showthread.php?t=1022637](http://ubuntuforums.org/showthread.php?t=1022637)

Can u pls give more details? Is it a Wireless Router? Model no? Do u know the IPs for the gateway IP, ur PC's and the DNS? Is ur PC able to connect to the Internet?


yes, it is a wireless router. Linksys model no. wrt54g v5. My desktop pc doesn't run on this router, it is cable modem, and it works perfectly. The other things you were wanting to know, the IP and DNS..I have no idea what those are. :confused:
This is frustrating....almost enough to send it back to Dell and lose  15% to stocking!!

---

### Post by Iowan on 2008-12-27
Having two threads DOES make it difficult to see what's been suggested...
IP address can be discovered by running "\**ifconfig -a" in a terminal**.

---

### Post by namdung on 2008-12-28
IP, DNS, Gateway IPs are provided by ur ISP. Pls get in touch with them.
Post the output of the following commands in the terminal
```

gedit /etc/network/interfaces

gedit /etc/resolv.conf
```

I reckon ur machine has a wireless card. When u right click on the Network icon, is the *Enable Wireless* checked?

---

