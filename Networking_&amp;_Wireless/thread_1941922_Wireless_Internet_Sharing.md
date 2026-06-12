---
title: "Wireless Internet Sharing"
date: 2012-03-16
forum: Networking &amp; Wireless
---

### Post by BcRich on 2012-03-16
Hi
I have two computers running Ubuntu 10.10 and 10.04. The 10.10 machine has a working wireless connection that I use to access the internet and a network card eth0. I have the 10.04 machine connected to the 10.10 computer via a crossover cable and I'd like to share the 10.10's internet connection with the other computer which also has a network card eth0 (which the other end of the crossover cable is plugged into). 
This wiki [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing) has been helpful to a point but I still can't access the internet through the 10.04 machine.
Basically what I've done is on the server machine 10.10 under Network Connections > IPv4 Settings I've chosen "Shared to other computers" as the Method. Then on the Client machine 10.04 in the same location I've chosen "Manual" as Method and set an IP address and netmask 192.168.0.10 and 255.255.255.0. Network manager recognizes the connection and says that I am connected to "Auto eth0" which is the name of the wired connection on both computers. So what am I doing wrong? Would really appreciate some help, please...

---

### Post by praseodym on 2012-03-16
Hi, try this:

Host: LAN: shared...
      WLAN: automatic DHCP

Client: LAN: automatic DHCP

---

### Post by BcRich on 2012-03-16
> **praseodym said:**
> Hi, try this:

Host: LAN: shared...
      WLAN: automatic DHCP

Client: LAN: automatic DHCP
Hi praseodym
Thanks for the suggestion :) I already tried that. for some reason when I don't use a static IP for the client it can't connect to "auto eth0" (wired connection), any other ideas?

---

### Post by wannabe user on 2012-03-16
It should work with DHCP, however usually it won't use 192.168.x.x, what I mean is if your 10.10 system is using 192.168.0.x then you won't use that subnet for the share, it's technically a different network. Normally any machine connected via ICS gets 10.x.x.x to prevent it from conflicting with your other addresses.

But if it hasn't worked with DHCP which it should, you could try this:

[http://ubuntuforums.org/showpost.php?p=6408893&postcount=2](http://ubuntuforums.org/showpost.php?p=6408893&postcount=2)

---

