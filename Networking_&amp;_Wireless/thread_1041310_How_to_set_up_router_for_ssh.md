---
title: "How to set up router for ssh"
date: 2009-01-16
forum: Networking &amp; Wireless
---

### Post by walter_j on 2009-01-16
I'm trying to sert up a Dlink EBR2310 for ssh. I gave the ubuntu server a static ip, while all other pc's have dynamic ip's assigned by the router. I went into the router settings and added the ip address for the ubuntu server that I wanted to be redirected to, as well as a port. When I try ssh from a remote location with the IP address of the router, it eventually times out. The router is also set up with a static ip. It seesm that I connected with the router but am not being redirected. Any ideas what I could be doing wrong?

If the router dynamically assigns ip's, should the static ip be within the range of ip's ofr the router or outside?


Walter

---

### Post by stefangr1 on 2009-01-16
The fixed ip should be within the subnet of the router.

Did you check (with the command "ifconfig") whether your server has the assigned ip address?
If yes, can you ssh into the pc from your home network?

Then, in your router you should add an entry for port forwarding like:
outside ip: 0.0.0.0  port 22
inside ip: 192.168.#.#  port 22  (the ip should be the inside ip of your router)

---

### Post by Iowan on 2009-01-16
> **walter_j said:**
> If the router dynamically assigns ip's, should the static ip be within the range of ip's ofr the router or outside?
WalterStatic IP should be **outside** the router's DHCP range - otherwise the router might assign a machine the same address, causing a conflict. But... it must be within the router's subnet so it can play with the other kiddies on the block... uh, so to speak.

> When I try ssh from a remote location with the[COLOR="Red"] IP address of the router[/COLOR], it eventually times out. The router is also set up with a static ip.You're not talking about the router's internal address...

---

### Post by stefangr1 on 2009-01-17
But when you assign a fixed ip address in the router, it won't assign the same address again, right? So I think that's only a problem if you run your own dhcp server.

---

### Post by Iowan on 2009-01-17
If the router is assigning IP addresses it IS a DHCP server. As an example:
A router's internal port is assigned 192.168.0.1 with a netmask of 255.255.255.0, and it assigns addresses in the range 192.168.0.100 - 192.168.0.200
Addresses from 192.168.0.2 - 192.168.0.99 and 192.168.0.101 - 192.168.0.254 are in the same subnet and could be used for static addresses (or assigned static leases by the router - based on MAC addresses). A machine with static address of 192.168.0.150 is inside the DHCP range and could cause problems.

Most ISP's issue dynamic addresses to their clients (static addresses *might* be available for a fee).  This address gets assigned to the external port of the router - it is what you would see from [http://whatsmyipaddress.com/]("http://whatsmyipaddress.com/"). From outside the network (remote?), the router's internal address (192.168.0.1) is inaccessible.

---

### Post by walter_j on 2009-01-18
I changed the router range so that it included the static ip. Ifconfig shows the ubuntu server having a static ip. When i try to ssh into it, the connection times out. The router has a static ip assigned by the isp (we have a high speed radio connection). Sory it takes me awhile to test the settings. I have to drive 35 Km to the site. Should I be using the gateway address? Could I be using the wrong command format? I used:

 slogin [email]walter@204.xx.xx.xxx[/email] -p xx -v

(The ip address and port have been represented by x's)


Walter

---

### Post by Hobgoblin on 2009-01-18
> **walter_j said:**
> 

 slogin [email]walter@204.xx.xx.xxx[/email] -p xx -v


I would use ```
ssh xxx.xxx.xxx.xxx -p xx
```

slogon should work in place of ssh.

Can you ssh from within the network, using the internal fixed IP?

---

### Post by walter_j on 2009-01-18
> **Hobgoblin said:**
> I would use ```
ssh xxx.xxx.xxx.xxx -p xx
```

slogon should work in place of ssh.

Can you ssh from within the network, using the internal fixed IP?

I can ssh from other nets - but i haven't tried the one where it's currently at. I'll try that next. When I set up the server at home, the static ip was outside the router ip range, and was able to ssh it internally, but didn't try a remote connection.

I'll try ssh internally tomorrow, and I'll verify my ip address with whatsmyipaddress.com

If the connection times out, does it mean I connected to the router but not to the server?

---

### Post by walter_j on 2009-01-20
The router manual states the static ip must be outside the ip range, otherwise there may be conflicts.

What is the diff between TCP and UDP? Should I enter the same port in both?

Walter

---

### Post by walter_j on 2009-01-22
After working through the router configuration with the ISP support and with Dlink, neither one of them could get port forwarding to work with this router. Apparently I did set up the router correcetly, but it just doesn't work. My next option is to create a DMZ host on the router: I'm creating another thread since I got lots of questions about this too.

---

