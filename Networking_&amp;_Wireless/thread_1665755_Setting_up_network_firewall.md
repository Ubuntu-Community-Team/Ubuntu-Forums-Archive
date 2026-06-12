---
title: "Setting up network firewall"
date: 2011-01-12
forum: Networking &amp; Wireless
---

### Post by joesquire on 2011-01-12
Hello
I'm new to all this Linux stuff.
I was wondering if I could set up a firewall on my linux machine?
The idea I have is to connect my router wired to the linux machine and then from the linux machine to my main computer, and obviously routing the internet connection through the linux box as a firewall.
I use a Netgear DG834G router and im with AOL
Thanks for any help in advance

---

### Post by sj1410 on 2011-01-13
you can do a lot with linux, firewall, proxy, content filter, traffic shaping, vpn, network management and lots more. just google it and do it yourself, or if you can spend some go for a ready solution like this

[http://www.pisces.net.in/p/effortless-linux-based-firewall.html](http://www.pisces.net.in/p/effortless-linux-based-firewall.html)

---

### Post by joesquire on 2011-01-13
Hi thanks for your reply.
I have tried a search on google but i never seem to be able to find the exact information that i want, all of it seems like just setting up a normal firewall just for that one preticular computer and well if thats all it is then i dont need that?
Could anyone point me in the right direction?

---

### Post by sj1410 on 2011-01-13
> **joesquire said:**
> Hi thanks for your reply.
I have tried a search on google but i never seem to be able to find the exact information that i want, all of it seems like just setting up a normal firewall just for that one preticular computer and well if thats all it is then i dont need that?
Could anyone point me in the right direction?

Just for one computer you definitely don't need that. but why do you want to divert traffic thru a linux firewall for just one computer.

---

### Post by joesquire on 2011-01-13
well it was just the plan at the moment just to learn it all properly and then i would extend it to obviously more computers and so on

---

### Post by sj1410 on 2011-01-13
> **joesquire said:**
> well it was just the plan at the moment just to learn it all properly and then i would extend it to obviously more computers and so on

than you can proceed, 

you configure iptables for firewalling or use the firewall script at

 [http://rocky.eld.leidenuniv.nl/joomla/](http://rocky.eld.leidenuniv.nl/joomla/)


theres lot more to do, configure squid for proxy, etc...

---

### Post by joesquire on 2011-01-13
dont supose you know of a place where i can find a list of stuff that need doing? haha sorry for being a pain

---

### Post by ripat on 2011-01-13
If you want your Linux box to act as a real firewall to protect your LAN, you will first need to install a second NIC. I wouldn't recommend to use it for anything else like mail, web or file server. If one of these servers is compromised (root escalation), your firewall is as good as dead.

The learning curve to master a firewall using iptables might be of the steep type if you are new to Linux. They are a number of solutions like Shorewall, Firestarter or SmoothWall. But if you decide to go the hard way, you will be rewarded 1000 times as you will be able to do virtually anything you like with the utilities like *iptables*,* ip* and *tc*.

---

### Post by joesquire on 2011-01-13
hello thanks for your reply
i wasnt planning on using it for any other kind of server, just the firewall.
i think i might go the easier way fpr now because ive had a quick look at the other and looks complicated but i might look into it again in the future and learn it all once ive l;earnt more about linux =)

---

### Post by airtonix on 2011-01-13
Easiest way is to use the already installed utility called "UFW" : 

```

~$ sudo ufw status
Status: active

To                         Action      From
--                         ------      ----
Anywhere on eth12          ALLOW       Anywhere
Anywhere on wlan0          DENY        5353
Anywhere on wlan0          DENY        631

Anywhere                   DENY OUT    135,139/udp on wlan0
Anywhere                   DENY OUT    135,139/tcp on wlan0
Anywhere                   DENY OUT    445 on wlan0

```


eth12 is my local lan and wlan0 is the rest of the house.

the above rules : 

1. allow everything from inside the lan to get out, except for 
 1a. avahi announcements (i don't want housemates finding out about these services or hostnames)
 1b. cups printing...

2. deny any samba traffic to escape my local lan (it' likes to announce alot of stuff)

If i wanted to allow access to port 80 (usually for the apache2 webserver) for traffic coming in via the wifi card : 

```

sudo ufw allow in on wlan0 to any port 80

```

to have ufw handle the Network Address Translation you first need to satisfy two things : 

1. that your lan side (your computer to linux box) addresses are not the same network as the wan side (linux box to router).

2. that you make use of /etc/before.rules as mentioned here : [https://www.nowhere.dk/articles/tip_nat_with_ubuntus_ufw_firewall](https://www.nowhere.dk/articles/tip_nat_with_ubuntus_ufw_firewall)

---

### Post by sj1410 on 2011-01-13
> **joesquire said:**
> dont supose you know of a place where i can find a list of stuff that need doing? haha sorry for being a pain

no matter you are not a pain, even if you are expecting a step by step spoon feeding for learning linux this is not the right forum.

---

