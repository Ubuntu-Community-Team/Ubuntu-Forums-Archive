---
title: "How to get internet in both the systems using lan !!??"
date: 2010-08-31
forum: Networking &amp; Wireless
---

### Post by chinmaya_n on 2010-08-31
HI

I dont know if my question is correct or not... but that is my way of understanding (it sounded different to me too !!)

Now my problem is...
My ISP registers MAC address when connected to Internet. So if connect another system with a switch, Internet will be accessible by only one system (which registers first). I want both systems to work at a time!
What should I do?? Are there different methods of connecting??
I searched google, but I could not frame a sentence to ask?!! :(
It would be happy if it is either a command based or UI based.

Can Someone help me plzz...:confused:

++: How can I restrict the bandwidth usage of the second system??

---

### Post by uberlinuxnerd on 2010-08-31
You need a NAT'ing Router... 

[https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)

EDIT: QoS to throttle bandwidth

---

### Post by chinmaya_n on 2010-08-31
> **uberlinuxnerd said:**
> You need a NAT'ing Router... 

EDIT: QoS to throttle bandwidth

Do I need to buy a router for sure??
It again costs me :(

Is nt there anyother idea??

---

### Post by uberlinuxnerd on 2010-08-31
> **chinmaya_n said:**
> Do I need to buy a router for sure??
It again costs me :(

Is nt there anyother idea??

We if you have two machines on a basic peer to peer network one machine can act as a router (gateway) to the Internet. The other machine would sit behind the routers IP (and therefore MAC address).

So it shouldn't cost you anything.. Now of course the gateway machine will have to be on for the machine behind it to access the Internet.

---

### Post by chinmaya_n on 2010-08-31
Hey, Is it enough with an external lan card???
I 've it already!! :)

---

### Post by uberlinuxnerd on 2010-08-31
> **chinmaya_n said:**
> Hey, Is it enough with an external lan card???
I 've it already!! :)

Correct, a bare min is two network cards!

---

### Post by prshah on 2010-08-31
> **chinmaya_n said:**
> Is it enough with an external lan card?

Yes, with two LAN cards, you can set up your existing machine to act as a gateway to the Internet for other machines on your LAN.

See [the community documentation]("https://help.ubuntu.com/community/Internet/ConnectionSharing#GUI%20Method%20via%20Network%20Manager%20%28Ubuntu%209.10%20and%20up%29") for how to set it up.

Please post back if you have any problems.

Note that it will be better if you have two internal LAN cards; and LAN cards are very cheap now. However, the external LAN (usb?) card will do as well.

And do remember as mentioned by uberlinuxnerd, you will need the gateway (Internet "server") machine to be active for the rest of the LAN machines to access the Internet.

---

### Post by sikander3786 on 2010-08-31
Yes you need to get 2 network cards in the PC that is going to act as a Server.

Setting up a gateway is not an easy task. Good if you manage it and if not, consider [Firestarter]("https://help.ubuntu.com/community/Firestarter"). It is far more easy and graphical than iptables.

For bandwidth usage restriction I have never found something easy in Linux. I use Squid but that will be far more advanced setup for a single client.

---

### Post by chinmaya_n on 2010-08-31
Hey... Thanks to all!!

I just connected my lan card & then other system using a cable.
And then changed IPv4 settings of **eth1**(lan) as "**Shared to other Computers**" in the Network Configurations.(where as eth0 is my original Inet connection).
When restarted it connected automatically :)

Thanx to all once again! :lol:

EDIT: How could I manage the bandwidth now?? QoS ??

---

### Post by chinmaya_n on 2010-09-10
How could I manage the bandwidth now??
Plz help me some one!!

---

