---
title: "routing &amp; firewall on 2NIC LAN server"
date: 2009-05-21
forum: Networking &amp; Wireless
---

### Post by IThinker on 2009-05-21
I have a PC with KUBUNTU installed on it and with 2NIC's on it (two PCI network 100Mbit cards). I want to use it as a server packet router and firewall between two computers with windows installed on them, each of this computer being connected to one different card on the KUBUNTU server. The computers are connected to the network cards using a switch.
I tried to configure the server to route the packets from one IP address rank to another and with different masks, but I hadn't managed to do this. Instead I did the following:
1. I've set net.ipv4.ip_forward = 1 in sysctl.conf
2. I configured eth0 as follows:
ifconfig eth0 192.168.2.1 netmask 255.255.255.0 up
3. I configured eth1 as follows:
ifconfig eth1 192.168.1.2 netmask 255.255.255.0 up

After this I managed to ping say a computer with Windows with 192.168.1.5 from a computer connected to another card with the IP address 192.168.2.5.

(But initially I wanted to ping say a computer with the IP with 81.180.75.70(mask 255.255.255.192) from a computer with the IP of 192.168.2.5(mask 255.255.255.0) -> I didn't managed to do that)

NEXT, I want to configure the server to act as a firewall. Let say he will allow ping from one PC connected to the server to another one but not viceversa. At the same time I want that ping(or say packets) from the PCs will reach the server and viceversa. (So finally to deny ping from one PC to another, but another will be able to ping the one whose packets will be rejected).

I tried to do something like this:
iptables -A FORWARD -s 0/0 -i eth0 -d 192.168.1.5 -o eth1 -j REJECT

but this isn't working.
If I do this, on one PC ping will result in Request timed out, 
and on another will result in some specific reject message. If I 
remove this by typing iptables -F FORWARD, everything goes back 
to normal and ping is allowed.

WHAT'S THE PROBLEM? CAN SOMEONE EXPLAIN STEP BY STEP WHAT I NEED TO DO?
THANKS IN ADVANCE TO EVERYONE WHO'LL TRY TO HELP ME!

PLEASE DON'T ASK WHY I NEED THAT AND WHY THIS VERSION OF LINUX(UBUNTU)
BECAUSE THE TASK IS SUPPOSED TO BE RESOLVED WITH THIS CONFIGURATION
AND NO MORE!

---

### Post by wirelessmonkey on 2009-05-21
Question: are both 192.168.1.2 and 192.168.2.1 and/or 192.168.1.5 and 192.168.2.5 connected to the same switch?  I need a clearer description of your topology before I can help.

---

### Post by superprash2003 on 2009-05-22
is this the desktop version or the server version?? the 81.x.x.x ip , is connected to which interface?? the 192.168.1.x interface or the 192.168.2.x interface?

---

### Post by IThinker on 2009-05-22
wirelessmonkey, yes, same switch.
superprash2003, desktop, I get to the console by hitting CTRL+ALT+F1. 
"the 81.x.x.x ip , is connected to which interface??" -> what matters? is the same thing. If to say correctly, 81.x.x.x is on eth0 and 192.168.2.x is on eth1.

---

### Post by superprash2003 on 2009-05-22
you could use firestarter for this , it has a neat GUI which could help in the routing

---

### Post by IThinker on 2009-05-22
superprash2003, I'm not supposed to use GUI. I'm supposed to solve all of this by using the console line and commands like ipconfig, route and iptables.

---

### Post by wirelessmonkey on 2009-05-22
Whoa whoa whoa.... I won't be doing your homework for you.

---

### Post by IThinker on 2009-05-23
[wirelessmonkey]("http://ubuntuforums.org/member.php?u=174597"), so what's the point of you then? What's the point of this forum then? To find some selfish people like you? Satisfied to know something that someone not know?
The point is that I did it already, but I wanted to find a kind person that knows what he does and explain step-by-step what to do and how to do, and that someone else will find this topic and will learn from it, and would not spend like me a month to find how this ** thing works in Linux, especially ubuntu. I spent a month for that, and this was because of people like you, very selfish, that likes that someone know less than them.

How old are you? Because only a child will reply like you! And this wasn't a homework, because I'm not at school and even at college!

---

