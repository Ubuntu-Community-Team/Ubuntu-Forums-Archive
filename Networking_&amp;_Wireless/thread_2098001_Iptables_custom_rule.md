---
title: "Iptables custom rule"
date: 2012-12-25
forum: Networking &amp; Wireless
---

### Post by Tyden on 2012-12-25
Hi, i'm new on this forum but i want to ask you a specific thing :)
Imagine that i want to redirect all requests from host A to Host B with ALL protocols with a port expect only one protocol(with a single port associated on this protocol), does exists a rule that do this?
Thanks

---

### Post by chadk5utc on 2012-12-25
Yes this is possible with either routing or forwarding depending on what your doing? If you can offer a little more information what you want to do we maybe able to offer suggestions

---

### Post by Tyden on 2012-12-26
Thanks for the fast reply.
For example suppose that I have two Hosts A(1.1.1.1), B(2.2.2.2), a request come from A and i must accept and resolve this request.
Now i want that all requests are redirected to B for all protocols and all ports expect ICMP(that will work normally) for not to break the network diagnostic.
Thanks in advance.

---

### Post by agillator on 2012-12-26
In general you will need rules in in the PREROUTING chain of the nat table. Your development of the rules will probably be a series of iterations until you get it fine tuned to exactly what you want, so be careful you don't lock yourself out of any of the machines. In the extreme, rebooting a machine should clear anything you have done until you do something to make a rule load at boot time. Of course restarting iptables should do the same thing slightly less drastically. Once you know you are not going to lock yourself out of anything take a look at the rules.

Since ICMP packets are not to be forwarded, you are going to have to make a rule for each protocol to be forwarded. I assume you are NOT doing this as root, that would be a VERY, VERY BAD idea!

You will need to know the internet-facing interface name on the machine connected to the internet. That could be something like ppp0, wlan, etc. You can probably get this from ifconfig. You will also obviously need the ips of the source and destination machines. Once you have that info you can enter your rules on the machine facing the internet. Assuming you want ONLY all tcp and udp packets from machine A sent to B, packets from any other source on the internet to go as addressed, try the following.

sudo iptables -t nat -I PREROUTING -i <interface name> -p tcp -s <machine A ip> -j DNAT --to-destination <machine B ip>
sudo iptables -t nat -I PREROUTING -i <internace name> -p udp -s <machine A ip> -j DNAT --to-destination <machine B ip>

The manual page for iptables (man iptables), especially the TARGET section for DNAT will give you the details. NOTE: these rules will probably be lost when iptables is restarted. Note also that they are being inserted (-I) at the beginning of the chain. That may not be what you want. Again, the man page will help you put the rules where you want them. Once they work, to make them permanent you will need to put them in rc.local or some other location that is automatically loaded during the iptables start process.

---

### Post by Tyden on 2012-12-26
Ok, thank you for the complete and specific reply :D
You have clarify my ideas, i will try as soon as possible.

---

