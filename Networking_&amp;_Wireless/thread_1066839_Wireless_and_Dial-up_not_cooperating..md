---
title: "Wireless and Dial-up not cooperating."
date: 2009-02-11
forum: Networking &amp; Wireless
---

### Post by lowtolerance on 2009-02-11
I'm having an issue with my wireless home network setup. When my wireless card connects, it causes the internet coming from my dial-up connection to not function. Can anyone point me in the right direction of where to look to fix this? I would like to be able to share this connection over the network, and I know it's possible, but this conflict is frustrating. Any help would be appreciated.

---

### Post by superprash2003 on 2009-02-11
this should help.. just ensure that you put in the right interfaces at the right places.. [http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)

---

### Post by lowtolerance on 2009-02-12
I was able to follow all of the steps, but I still have the same problem. The moment my wireless card connects, I'm unable to access the internet. Even though I used the command "ifconfig wlan0 192.168.0.1", which I presume sets a static IP for that interface, the router still assigns it a different IP via DHCP. Is that a router issue or does the interface have to request an IP for it to assigned? Am I making any sense? :P

---

### Post by lowtolerance on 2009-02-12
Nevermind about the IP issue, I figured that one out I think. Still didn't fix the problem, though.

---

### Post by superprash2003 on 2009-02-12
in that case you would need to DISABLE DHCP in your router and run a dhcp server in ubuntu

---

