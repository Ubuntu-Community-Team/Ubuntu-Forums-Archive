---
title: "Connection sharing with a single network adapter"
date: 2009-01-24
forum: Networking &amp; Wireless
---

### Post by MisterM on 2009-01-24
Hi,

I intend to use an Ubuntu Desktop installation for my router. From what I've read, Firestarter is the way to go here, but in it's documentation it says I need two network adapters to set up connection sharing (i.e. NAT). Is this really necessary? Currently I'm using a Win2003 machine with RRAS to do my routing and it works perfectly, with just one network adapter. The router (win2003), the modem and all the other PCs are connected to the same switch, while RRAS does the routing.

So, my question is, do I really need another network adapter to set this up in Ubuntu?

---

### Post by cariboo on 2009-01-24
from computerperformance.co.uk

> The Routing side of RRAS

Windows 2000 or Server 2003 servers can act as a software router.  Naturally you need at least two network cards.  Check out the Routing by going to RRAS \ <Server Name> \IP Routing \General and then right click and add the Interface or Routing protocol that you need.

If your modem is connecting directly to the switch, then you aren't using RRAS properly.

---

### Post by MisterM on 2009-01-24
> **cariboo907 said:**
> If your modem is connecting directly to the switch, then you aren't using RRAS properly.

It may well be that I'm not using it "properly", but as I said before, it's working perfectly.

The Windows machine connects to the internet (via ADSL) as if the modem was connected directly. It then routes this connection to the local network. In RRAS, I actually see two connections - the internet connection and the local area connection. It's just that they share the same physical network adapter.

I've added the internet connection to RRAS manually, by selecting "New Demand-dial Interface". Is there a similar option in Firestarter?

---

### Post by MisterM on 2009-01-25
Has really no one ever done this with a single network adapter?

I will be able to try this myself, once I install Ubuntu, but I'd really like to find out beforehand, so that I know whether I have to go out and buy another network adapter.

---

### Post by bgerlich on 2009-01-25
If your modem doesn't have issues with connecting to your computer through a switch it shouldn't be a problem. Mind you I never came across this particular setup, but this is how I think you should approach it.

On your Linux machine you should have:
1. A virtual network interface to be used with internal network
2. A non authoritative DHCP server bound to the virtual interface
3. Turned on ip forwarding
4. IP Masquarade iptables rule.

Should work just fine.

---

### Post by MisterM on 2009-01-25
Thanks for your explanation, bgerlich. I take it this is possible then, and I don't need to buy another network adapter.

Would you be so kind as to provide a short explanation for each of your points? I understand the basics of routing, but am in no way an expert on it. In RRAS, all I had to do, was add both interfaces and specify which port goes to which internal machine (via NAT). :D

In particular, what is a non-authoritative DHCP server and why use one, as well as what is ip forwarding and masquerading.

Thanks!

---

### Post by bgerlich on 2009-01-25
Ip forwarding is a process of forwarding packets from one network to another.

DHCP server is a system daemon allowing dynamic network configuration - assigning IP addresses, telling clients which machine is a router, etc.

The non authoritative server means that the DHCP server will not correct clients asking for an address it is not configured to assign.

IP Masquerade is another name for NAT.


Basically all you have to do is follow any tutorial describing how to setup NAT in linux remembering that you will be using a virtual interface instead of a physical one.

Setting up a virtual interface is as simple as issuing one command: sudo ifconfig eth0:1 10.0.1.1 netmask 255.255.255.0 for example. This will setup an virtual interface with IP address 10.0.1.1 on physical interface eth0.

---

### Post by MisterM on 2009-01-25
Thank you very much. This is exactly what I needed.

One minor point though. I think the DHCP server should be authoritative, since I would like any newly connected PC to get an IP address automatically. (BTW, forgot to mention in my previous post that I am well aware what DHCP is, I just didn't know what "non-authoritative" means)

---

### Post by bgerlich on 2009-01-25
Both in non authoritative and authoritative modes your clients will get IP addresses automatically. The difference is that if a client asks for an address that the DHCP server can not issue, the server will just stay silent instead of correcting the client. I think the server should be in non-authoritative mode so that it wouldn't conflict with DHCP requests sent to your ISP's DHCP server.

---

### Post by MisterM on 2009-01-25
Ok, thank you for the clarification and thanks again for all your help.

---

