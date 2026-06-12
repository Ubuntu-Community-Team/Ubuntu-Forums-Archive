---
title: "ssh via mobile 3G protocol"
date: 2011-10-06
forum: Networking &amp; Wireless
---

### Post by asm2545w on 2011-10-06
Hello,

I am having some troubles to connect via ssh from my iphone to my ubuntu desktop 10.04 via 3G protocol.

I have a laptop with Ubuntu Desktop 10.04 isntalled, with openssh-client and openssh-server installed.

I have another computer with Ubuntu Server 11.04 installed, with openssh-client and openssh-server installed too.

iPhone 3GS with MobileTerminal and ssh installed too.

All the connections work perfect, I mean, I can connect between these three devices with any trouble via wi-fi. The rare thing is that I can connect from my iPhone via 3G to the server, but not to the Desktop (if the iPhone is connected to the network via wi-fi every connection works ok), but not via 3G from the iPhone to the Desktop.

Any idea?

Thanks in advance

---

### Post by haqking on 2011-10-06
> **asm2545w said:**
> Hello,

I am having some troubles to connect via ssh from my iphone to my ubuntu desktop 10.04 via 3G protocol.

I have a laptop with Ubuntu Desktop 10.04 isntalled, with openssh-client and openssh-server installed.

I have another computer with Ubuntu Server 11.04 installed, with openssh-client and openssh-server installed too.

iPhone 3GS with MobileTerminal and ssh installed too.

All the connections work perfect, I mean, I can connect between these three devices with any trouble via wi-fi. The rare thing is that I can connect from my iPhone via 3G to the server, but not to the Desktop (if the iPhone is connected to the network via wi-fi every connection works ok), but not via 3G from the iPhone to the Desktop.

Any idea?

Thanks in advance

obvious question but i presume your router is set up correctly to port forward ssh 22 to your desktop ?

---

### Post by asm2545w on 2011-10-07
Yes, everything is working fine. Just, when I try to connect to the Desktop from the iPhone when this is using 3G protocol, it does not work. If the iPhone is connected to the network via wi-fi, I can connect to the Desktop from the iPhone.

Router and firewalls are set up correctly.

Another point is that I can connect from the iPhone to the Ubuntu Server via 3G, but not to the Ubuntu Desktop. Is this not rare?

---

### Post by haqking on 2011-10-07
> **asm2545w said:**
> Yes, everything is working fine. Just, when I try:

$ ssh user@desktop_ip

From the iPhone and this is connected via 3G.

your 3g connection is not on your wifi and so not on your network, so connects via the internet to your WAN IP which is your router.

Your desktop IP is not a public WAN IP so how is your phone going to connect to it ?

i suspect your dekstop IP is something like 192.168.x.x or similar which is a private class c address.

IM confused so your 3g can connect to your server by doing same thing ? is your server a static public IP or your router forwards WAN requests for port 22 to your server ?

---

### Post by asm2545w on 2011-10-07
My router has an static ip. Different things that I did without problem:

From iPhone connected via wi-fi:

$ ssh user@intranet_Desktop_ip
$ ssh user@intranet_Server_ip

From iPhone via 3G protocol

$ ssh user@static_router_ip   

In this case I set up the router forwards WAN requests for port 22 to the server.

The problem is when I set up the router forwards requests to the desktop and I use the iPhone via 3G the following command does not work:

$ ssh user@static_router_ip

Why? I don't know.

---

### Post by haqking on 2011-10-07
> **asm2545w said:**
> My router has an static ip. Different things that I did without problem:

From iPhone connected via wi-fi:

$ ssh user@intranet_Desktop_ip
$ ssh user@intranet_Server_ip

From iPhone via 3G protocol

$ ssh user@static_router_ip   

In this case I set up the router forwards WAN requests for port 22 to the server.

The problem is when I set up the router forwards requests to the desktop and I use the iPhone via 3G the following command does not work:

$ ssh user@static_router_ip

Why? I don't know.

ok that is clearer.

When you say doesnt work, what error do you get ?

remember thouth that your ssh client has a key stored now for that static IP, which is now establishing itself to a different server. so is it an authentication issue as that would make sense because the server has changed but the connection on your device remains the same if you see what i mean ?

---

### Post by asm2545w on 2011-10-07
This is the error:

$ ssh user@static_router_ip

ssh: connect to host static_router_ip port 22: Operation timed out

I copied the id_rsa.pub key from the iPhone to the authorized_keys file in the .ssh directory on both machines, the server and the desktop.

It is exactly the same configuration but in one machine I have a Ubuntu Server 11.04 and in the other Ubuntu Desktop 10.04.

---

### Post by haqking on 2011-10-07
> **asm2545w said:**
> This is the error:

$ ssh user@static_router_ip

ssh: connect to host static_router_ip port 22: Operation timed out

I copied the id_rsa.pub key from the iPhone to the authorized_keys file in the .ssh directory on both machines, the server and the desktop.

It is exactly the same configuration but in one machine I have a Ubuntu Server 11.04 and in the other Ubuntu Desktop 10.04.

mmm ok wierd.

Well to be honest i have no clue then? as i can ssh to my 10.10 desktop, i also have various VM's running servers and desktops and can ssh to all of them from my nexus android phone so no difference between the 10.04 and 11.04 thing.

I would be inclined short of not knowing whats wrong to remove the ssh client from my phone including config data and try again without ever connecting to the server, perhaps ? but that is a stretch as it connects to both locally.

can you ping your desktop machine from outside your LAN through your WAN ? firewall dependant of course ? i wam wondering whether it is SSH related or Desktop connectivity related if you know what i mean

---

### Post by asm2545w on 2011-10-07
Thanks a lot for your time haqking. I do not have time now, but I will do what you suggest later...

---

### Post by haqking on 2011-10-07
> **asm2545w said:**
> Thanks a lot for your time haqking. I do not have time now, but I will do what you suggest later...

no problem, sorry cant be of more help right now, perhaps someone else has a suggestion, maybe something obvious i am missing.

Try the connectivity thing out and also the clearing of ssh data on phone then we can go from there perhaps then.

cheers

---

### Post by SlugSlug on 2011-10-07
spose it possible your 3g provider is blocking port 22

---

### Post by haqking on 2011-10-07
> **SlugSlug said:**
> spose it possible your 3g provider is blocking port 22

you might want to read the thread before posting ;-)

he can connect to his server but not the desktop

---

### Post by jaimeap on 2012-02-10
Hello,

I am having exactly the same problem on 10.04. I can ping the machine through 3G but that is the full extent of the connectivity I can get. Incidentally, when I try the connection the other way round, from Desktop to phone, I have full access (one i put the password and all). Wondering if anyone has a moment to tackle this question again?

thanks,
JA

---

