---
title: "Isolating Samba Server from Wireless Clients"
date: 2010-05-19
forum: Networking &amp; Wireless
---

### Post by thabeat on 2010-05-19
Scenario: Enterprise with open space for Studying, conferences, classes, etc...

A server with Samba Shares and Internal Info (Private Info)

Just deployed an Open Wireless Network for guests or whoever.

The main idea was to locate every wireless client in a new subnet per AP. Meaning, the main net is 192.168.1.1, every AP connects by DHCP and has the subnet 192.168.*.* with DHCP to the clients.
Then I was going to use hosts deny / allow in smb.conf to deny access from wireless clients (different from .1.1)

It doesn't work...

So I tryed to play with the /etc/hosts.deny, it cuts the access on ssh, but not samba nor web access.

Any hints?

---

### Post by thabeat on 2010-05-21
Ok, now I'm totally lost

I was told the hosts.allow and hosts.deny files were deprecated and I should use /etc/security/access.conf instead.

But it doesn't work..., so I decided to create a firewall with iptables, such as:

iptables -A INPUT -s 192.168.X.1/24 -j DROP

for every subnet (X=10,20,30,40...)

And a shellscript to restore tables at boot.

With iptables --list I can see the tables there, but, right now, I'm in a laptop with wifi and IP 192.168.80.145 and just logged with ssh.

This should NOT happen, right?

---

### Post by redmk2 on 2010-05-21
> **thabeat said:**
> Scenario: Enterprise with open space for Studying, conferences, classes, etc...

A server with Samba Shares and Internal Info (Private Info)

Just deployed an Open Wireless Network for guests or whoever.

The main idea was to locate every wireless client in a new subnet per AP. Meaning, the main net is 192.168.1.1, every AP connects by DHCP and has the subnet 192.168.*.* with DHCP to the clients.
Then I was going to use hosts deny / allow in smb.conf to deny access from wireless clients (different from .1.1)

I'm can't give you a specific answer.  But maybe we can clear some things up and it will become clear.  My first thought is that *192.168.1.1* is not a network address.  It appears to be a IP address in a network.  We would need to know the subnet mask to know exactly where the boundaries are.  As an example: 
```
192.168.1.0/24 = network
192.168.1.1 = first address in the network [COLOR="Blue"]<-- boundry[/COLOR]
192.168.1.254 = last usable address in network <[COLOR="Blue"]-- boundry[/COLOR] 
192.168.1.255 = broadcast address of network

192.168.0.0/16 = network
192.168.0.1 = first address in network   [COLOR="Red"]<--boundry[/COLOR]
192.168.0.255 = 255th address in network
192.168.1.0 = 256th address in network
192.168.1.1 = 257th address in network
192.168.255.254 = last address in network [COLOR="red"]<-- Boundry[/COLOR]
192.168.255.255 = broadcast address of network 
```

The subnet mask will help in determining if you have set up the networks correctly.  > 

It doesn't work...

So I tryed to play with the /etc/hosts.deny, it cuts the access on ssh, but not samba nor web access.

Any hints?

...

Ok, now I'm totally lost

I was told the hosts.allow and hosts.deny files were deprecated and I should use /etc/security/access.conf instead.

But it doesn't work..., so I decided to create a firewall with iptables, such as```
:

iptables -A INPUT -s 192.168.X.1/24 -j DROP  [COLOR="Red"]<- do you only mean one address here?  
Or are you meaning to drop a whole subnet[/COLOR]
```

for every subnet (X=10,20,30,40...)

And a shellscript to restore tables at boot.

With iptables --list I can see the tables there, but, right now, I'm in a laptop with wifi and IP 192.168.80.145 and just logged with ssh.

This should NOT happen, right?

I have a feeling that the subnets are not properly set up.

---

### Post by BoneKracker on 2010-05-21
++

192.168.10.1  <---- IP address of a single node

192.168.10.0/24 <----- IP address of the subnet

iptables -A INPUT -s 192.168.10.0/24 -j DROP


Also, if you have all your wireless access points configured use dhcp to serve addresses in _a single range_ of addresses that is mutually exclusive with the range of addresses served to your wired clients, then you don't need a separate iptables rule for each wireless subnet (just one rule for all of them).

In other words, choose a network space for your wireless clients that:

a) is a logical subnet of your overall network space so you can refer to all the wireless space by a single network address/netmask (and so you can refer to all of your wired address space by a mutually exclusive network address/netmask).

b) you can decompose the wireless network space easily into the number of subnets you need (one for each wireless dhcp server, as you intend).

You'll probably need to use a subnet calculator to do that (lots of them online), but this will reduce the number of firewall rules, which increases the efficiency of your firewall.

---

### Post by redmk2 on 2010-05-21
@ BoneKracker, (Are you a D.C.?)

Yes indeed, the next idea was to present the notion of a **_contigious _** range of IP addresses for the AP's.  This allows (as you say) the admin to aggregate the subnets into one entry in the FW.

With that in mind, you could do this: A single network that contains 4 contiguously aligned /24 subnets _that can be expressed as one_. ```
192.168.4.0[COLOR="Red"] /22[/COLOR] = contains 4 /24 sub-networks.  
There are 1022 usable IP addresses in this range.
((256 * 4) - 2) if you consider it one network.

192.168.4.1   = starting IP address
192.168.7.254 = ending IP address

192.168.4.0 /24
192.168.5.0 /24
192.168.6.0 /24
192.168.7.0 /24


```

A nice calculator for this type of work is located [**_here_**]("http://www.mikero.com/misc/ipcalc/?start=192.168.4.0&end=192.168.7.255").

---

### Post by BoneKracker on 2010-05-21
> **redmk2 said:**
> @ BoneKracker, (Are you a D.C.?)
What's a D.C.?  (I guess that's a strong indication I could have simply said, "no".)

---

### Post by redmk2 on 2010-05-21
> **BoneKracker said:**
> What's a D.C.?  (I guess that's a strong indication I could have simply said, "no".)

Doctor of Chiropractic. A Bone Cracker

---

### Post by oldfred on 2010-05-21
I do not know networks, but ipcop looks interesting??

Red, green, orange, blue networks
[http://www.ipcop.org/1.4.0/en/install/html/decide-configuration.html](http://www.ipcop.org/1.4.0/en/install/html/decide-configuration.html)

---

### Post by BoneKracker on 2010-05-21
Check out shorewall too.

---

### Post by thabeat on 2010-05-26
Sorry, my fault, I was really trying 192.168.1.0/24

I've been thinking about the problem.... Is it possible the routers are NATING the packets and changing the source IP?

It's really weird...

---

