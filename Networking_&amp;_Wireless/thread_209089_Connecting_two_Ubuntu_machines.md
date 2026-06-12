---
title: "Connecting two Ubuntu machines"
date: 2006-07-04
forum: Networking &amp; Wireless
---

### Post by kriding on 2006-07-04
I have taken the plunge and convinced/forced/manipulated (delete where appropriate) my other half to change to ubuntu.

I am running dapper at the moment and the other is still on Breezy (dapper discs have not yet arrived) but will be upgraded to dapper as soon as I can.

I have set the shares on both systems, using NFS as the protocol, and my router (Billion Powerline BIPAC-7560) and both machins have DHCP enabled.

My machine connects to the internet ok, but I cannot get my girlfriends computer can't, nor can either computer communicate with each other.

I am new to networking in Linux, so I don't know any of the commands and I can't find any information on the forum (I did a search, but it won't let me access anything after page 10 in the search results)

Any pointers/advice would be greatly appreciated...she's given me 3 months to convince here to keep Ubuntu, otherwise it's back to windows (98SE..NOT XP..i'll be damned with all this activation lark!!).

TIA

Kev

---

### Post by opus on 2006-07-04
Are you trying to connect using the name of the other computer or the ip address?  You probably don't have name resolution on your network, so you will need to use the IP Address.  Since you are using DHCP your IP addresses will change eventually.  You might be better off using static IP's, and adding an entry for the other computer in the /etc/hosts file.  

Also - are you running a firewall like Firestarter? If so, you will need to enable connections from other computers for NFS.

Aaron

---

### Post by kriding on 2006-07-04
Both systems are fresh installs, the only addition is the ATI driver. I had set the IP address on both systems and subnet mask aswell as the default gateway, which was set to my routers IP.

What do you mean by trying to connect with the ip address/name?

I'm using the network servers link under 'places'...what do i need to do, to connect to the other system?

---

### Post by mit on 2006-07-04
are you trying to connect without a hub i.e using a crossover cable or in a network ?

mit

---

### Post by kriding on 2006-07-04
I'm using a router which is connected to my machine and the net, the other machine is connected via powerline adapter

---

### Post by Randomskk on 2006-07-04
So what is your network setup?
I'm thinking something like this:
```

INTERNET
      |
router (192.168.0.1)
  |                   |
your pc         powerline
(192.168.0.2)        |
                    her pc
                  (192.168.0.3)

```
The IP addresses may not be exactly that, but something similar?

Anyway, try pinging the router from both computers:
(in a terminal:)
```

ping 192.168.0.1

```assuming 192.168.0.1 is the router IP, replace as needed

if both computers can talk to the router, try pinging the two computers, like so:
```

your machine:
ping 192.168.0.3

her machine:
ping 192.168.0.2

```
If that all works, the problem is with the file shares, if not, the problem is with the network.

---

### Post by kriding on 2006-07-05
Yes, that's how my setup is.

I've tried to ping the router and my machine from hers, but get a 'destination unreachable' message, and my machine to hers is the same. Obviously, my machine to the router works ok..I started pinging it last night and it was still going this morning:D

---

### Post by Iowan on 2006-07-05
Her machine is actually getting an IP address?

---

### Post by kriding on 2006-07-05
how do you mean?, If your asking if I assign one, then yes I do. If your asking if she gets it via DHCP then I don't know.

My router and machines have been assigned with IP addresses by me, aswell as a subnet mask.

I've set the gateway address to the IP of the router, is this correct?

The only other thing I can think of is that the powerline adapter is not being used by linux, but i can't understand that, as all it does is send the signal over the power cables to the router, so as long as the NIC is working (and by all appearences it is) then all should be fine

---

