---
title: "Prevent access to other machines on local network"
date: 2011-06-30
forum: Networking &amp; Wireless
---

### Post by squaregoldfish on 2011-06-30
I've got an interesting network question for somebody.

I've got a network controlled by a Netgear router (192.168.1.1), which handles all the machines on my local network.

One of these machines is a server (192.168.1.5) which can be accessed from the outside world - the router forwards the necessary ports to that server.

I'd like to include SSH access on this server to allow some friends to use it when they need to. However, I don't want them to have access to any other machines on my network. So, how can I configure things so that my server (192.168.1.5) can't connect to any other machines on the 192.168.1.x network? (Obviously it still needs to talk to the router so it can see the outside world!)

What's the best way to set this up?

Steve.

---

### Post by sanderj on 2011-06-30
How about activating firewall functionality on that machine, and disallowing local access? There are GUI-tools to easily set it up.

---

### Post by squaregoldfish on 2011-07-01
I assume the gui is a layer on top of ufw? Since it's a server, I don't have X installed.

Steve.

---

### Post by sanderj on 2011-07-01
> **squaregoldfish said:**
> I assume the gui is a layer on top of ufw? Since it's a server, I don't have X installed.

Steve.

You can configure a firewall using vi, too ..

---

### Post by squaregoldfish on 2011-07-01
True, but vi doesn't have a 'disable local access' option ;)

I can (probably) figure it out really - I was just asking for the best approach. If I can set up the firewall on the server, that's good enough for me.

Steve.

---

### Post by Drenriza on 2011-07-01
> **squaregoldfish said:**
> I've got an interesting network question for somebody.
 
I've got a network controlled by a Netgear router (192.168.1.1), which handles all the machines on my local network.
 
One of these machines is a server (192.168.1.5) which can be accessed from the outside world - the router forwards the necessary ports to that server.
 
I'd like to include SSH access on this server to allow some friends to use it when they need to. However, I don't want them to have access to any other machines on my network. So, how can I configure things so that my server (192.168.1.5) can't connect to any other machines on the 192.168.1.x network? (Obviously it still needs to talk to the router so it can see the outside world!)
 
What's the best way to set this up?
 
Steve.
 
Now im a fan of Cisco so im going to say.
Get a decent router from ebay and do nat port overload.
```
ip nat inside source static tcp 192.168.1.5 22 interface (wan interface or public ip address)
```
 
This does so, when people try and connect to your public ip address, they get forwarded to 192.168.1.5 IF! they connect on port 22(ssh).

---

### Post by squaregoldfish on 2011-07-01
> This does so, when people try and connect to your public ip address, they get forwarded to 192.168.1.5 IF! they connect on port 22(ssh).

I've got that bit working with my router already.

It's preventing access from 192.168.1.5 to other machines on my network that I'm trying to work out.

Steve.

---

### Post by Drenriza on 2011-07-01
> **squaregoldfish said:**
> I've got that bit working with my router already.
 
It's preventing access from 192.168.1.5 to other machines on my network that I'm trying to work out.
 
Steve.
Then what is the issue now? Not sure i understand your scenario then

---

### Post by squaregoldfish on 2011-07-01
Having allowed external users to access 192.168.1.5 through SSH, they then have a chance to see what else is on my network from that machine, which I don't want them to do.

I therefore want to block all outgoing connections from 192.168.1.5 to any other machine on the 192.168.1.x network. But I still want access to the outside world from that machine (i.e. all other IP addresses).

So, 192.168.1.5 is allowed to initiate connections to any address EXCEPT 192.168.1.x.

Does this make things clearer?

Steve.

---

### Post by Drenriza on 2011-07-01
> **squaregoldfish said:**
> Having allowed external users to access 192.168.1.5 through SSH, they then have a chance to see what else is on my network from that machine, which I don't want them to do.
 
I therefore want to block all outgoing connections from 192.168.1.5 to any other machine on the 192.168.1.x network. But I still want access to the outside world from that machine (i.e. all other IP addresses).
 
So, 192.168.1.5 is allowed to initiate connections to any address EXCEPT 192.168.1.x.
 
Does this make things clearer?
 
Steve.
 
If you can make a access list on your router.
```
ip access-list extended
``` or ```
access-list (number)
``` is a standard access-list.
```
permit 192.168.1.5 (subnet mask) (public ip address) (subnet mask)
```
```
activate it under the interface on the inbound interface from server to router.
```
this will permit access to any other networks. If you need to do it directly on the server, i cant remember that right here right now but sure its possible. But i definitely perfer it at router level.

---

### Post by squaregoldfish on 2011-07-01
I'd prefer to do it on the router too, but unfortunately mine ain't that sophisticated.

The pointers you've given on the type of settings I need should be enough for me to do some more Googling and work out what to do on the server though. I'll try it out when I get home.

Thanks,
Steve.

---

### Post by Drenriza on 2011-07-01
> **squaregoldfish said:**
> I'd prefer to do it on the router too, but unfortunately mine ain't that sophisticated.
 
The pointers you've given on the type of settings I need should be enough for me to do some more Googling and work out what to do on the server though. I'll try it out when I get home.
 
Thanks,
Steve.
 
You can buy very good and very cheap cisco routers at ebay.com
try and take a look at the 1841 router for a home network.

---

### Post by SeijiSensei on 2011-07-01
You can add rules to the iptables OUTPUT chain like this:

```

iptables -A OUTPUT -d 192.168.1.1 -j ACCEPT
iptables -A OUTPUT -d 192.168.1.0/24 -j REJECT

```

Now the machine can send packets to the router but not to any other machine on the 192.168.1.0/24 network.

Obviously you can give your friends root access on the machine, or they could blow away these rules and browse the local network.

---

### Post by Drenriza on 2011-07-01
> **SeijiSensei said:**
> You can add rules to the iptables OUTPUT chain like this:

```

iptables -A OUTPUT -d 192.168.1.1 -j ACCEPT
iptables -A OUTPUT -d 192.168.1.0/24 -j REJECT

```

Now the machine can send packets to the router but not to any other machine on the 192.168.1.0/24 network.

Obviously you can give your friends root access on the machine, or they could blow away these rules and browse the local network.

i dont know **ALOT** about blocking networks from a server. But from my point of view it seams a bit miss placed to do as so :p since it's the router/switch in the network that regulate the traffic. But if it works, it works.

---

### Post by squaregoldfish on 2011-07-01
@SeijiSensei: That works perfectly! Thanks very much!

@Drenriza: As I said, I agree with you in principle. But since my router can't do it, and iptables is cheaper than a new router, that's fine with me. If and when I get a new router, I'll look to get an improved one with this kind of support.

Steve.

---

### Post by SeijiSensei on 2011-07-02
There's no "right" way to do things like this, but blocking at the router won't work in this case.  The OP wants to keep users on one machine in 192.168.1.0/24 from contacting other machines in the same network.  Remember that packets destined for machines in the same subnet are not passed through the router at all.  They're broadcast directly onto the network.  All the machines on the local network see all the traffic; the TCP/IP stack on each machine ignores all the packets without its own target address.

---

