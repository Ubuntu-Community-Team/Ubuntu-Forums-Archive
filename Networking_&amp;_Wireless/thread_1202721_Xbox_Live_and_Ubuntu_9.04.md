---
title: "Xbox Live and Ubuntu 9.04"
date: 2009-07-02
forum: Networking &amp; Wireless
---

### Post by LamerBOT on 2009-07-02
Ok, I have: Ubuntu 9.04, Xbox 360, and I want this f**king Xbox Live work perfectly.
I have two Ethernet Cotrollers in my PC. One of them (eth2) provides the internet, the other one (eth0) is connected with my Xbox 360 with a cable. Eth0 Configuration is: IP 192.168.2.1 Mask 255.255.255.0, Xbox Network settings: IP 192.168.2.2 Mask 255.255.255.0, Gate 192.168.2.1, DNS 192.168.2.1. With this settings it all worked perfectly on Windows, but not here... Using Firestarter, I enabled internet connection sharing for eth0, and allowed connections from 192.168.2.2(Xbox). But it still doesn't work! Please, help me. I'm new to Ubunta, and I think, that it's a great operating system, but small issues like this are killing me.:mad:

---

### Post by LamerBOT on 2009-07-02
Bump...Can anyone help me, please.

---

### Post by PieLover on 2009-07-05
bump

---

### Post by Saghaulor on 2009-07-10
Perhaps asking the question more politely would help solicit responses.

If I understand correctly, you're trying to forward the internet connection from your Ubuntu machine to your xbox from one nic forwarded to the other?

Is there any particular reason for doing this? Wouldn't it be easier to use a router?

If you don't have a router, then I understand why your are attempting to do do what it is you're attempting to do.

Does it work if you turn the firewall off entirely? Because if not, then obviously its a routing issue, most likely corrected in iptables.

---

### Post by Grimtagnbag on 2009-07-20
Here i just did this with my xbox 360. i have the internet coming into my computer and running out to my xbox 360. i have 2 network cards so i bridged them to make this work here is the link to what i did.[http://ubuntuforums.org/showthread.php?t=402581](http://ubuntuforums.org/showthread.php?t=402581)

---

