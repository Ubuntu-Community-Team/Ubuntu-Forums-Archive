---
title: "Forward ports on one IP to ports on another IP"
date: 2011-08-10
forum: Networking &amp; Wireless
---

### Post by tjetson on 2011-08-10
I am relatively new to Linux, and even newer to networking with Linux, and require some assistance. I have a Virtual Private Server running Ubuntu 11.04 64 bits. The VPS has two IP addresses. What I need to do is forward port 20 on the second IP to port 22 on the first IP; and also forward port 21 on the second IP to port 25565 on the first IP.

I have searched for some Iptables commands to do this, but they seem to only deal with forwarding one port to another on the same IP.

As I stated, I am fairly new to Linux; so if I haven't provided enough information, I apologise. Any help given would be greatly appreciated.

---

### Post by tjetson on 2011-08-12
I have made some progress here:
```
iptables -t nat -A PREROUTING -p tcp -d <2nd IP> --dport 20 -j DNAT --to <1st IP>:22
iptables -t nat -A PREROUTING -p tcp -d <2nd IP> --dport 21 -j DNAT --to <1st IP>:25565
```

The 25565 is a port that a game runs on. When I connect to the game on the first IP, port 25565; the game runs fine. However, if I run the above code and then try to connect to the game on the second IP, port 21; I am immediately disconnected. What I think must be happening is that the port is forwarded in one direction but not the other, if that is possible (?).

By the way, I should add that the game is being told to only listen on IP1:25565; so that is not an issue here.

Again, any help is appreciated.

---

### Post by tjetson on 2011-08-16
Bump

---

### Post by Doug S on 2011-08-16
> What I think must be happening is that the port is forwarded in one direction but not the other, if that is possible (?).
Yes, that is possible, and from what little information is given even probable.
A path the other way needs to also be provided in your iptables rules. I am more used to defining similar things in iptables via interface names, so I can only provide some rough suggestion based on the rules you gave, and you can try and debug to get it right from there. Try something like:```
iptables -A FORWARD -s <1st IP> -m state --state ESTABLISHED,RELATED -j ACCEPT
```
While not the same as your issue, see also [http://ubuntuforums.org/showthread.php?t=1758922](http://ubuntuforums.org/showthread.php?t=1758922) , particularly post #8. 
If your troubles continue maybe give us more detail about your overall iptables rule set.

---

### Post by tjetson on 2011-08-24
Apologies for my (very) late reply; I have been rather busy. I can tell you now that no further help is required on this particular issue, as (long story short) the need for the forwarding of the ports is no more.

Thank you kindly for your assistance anyway.

---

