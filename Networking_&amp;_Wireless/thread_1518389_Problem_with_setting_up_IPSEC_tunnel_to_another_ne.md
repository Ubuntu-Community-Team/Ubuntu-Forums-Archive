---
title: "Problem with setting up IPSEC tunnel to another network"
date: 2010-06-26
forum: Networking &amp; Wireless
---

### Post by Radapompa on 2010-06-26
Hi
I've starting setting up an IPSEC tunnel too another network. What I'm trying to do is I have a Ubuntu 10.04 server which acts as a firewall and behind it, there is a network with Windows machines. From one of the Windows machines I'm supposed to connect too another network behind a firewall. I've tested installing a client on one of my Windows machines and it works. But now instead of opening up this tunnel with this client on all the machines, I want my Ubuntu firewall to establish the tunnel and then let the Windows machines go through the tunnel on the firewall.

What I've managed so far is too open the tunnel on the firewall (I think). I've installed OpenSwan for this and whenever I restart IPSEC I get the "IPsec SA established tunnel mode" in the Auth-log. The problem is now that I don't seem to be able too connect from any of my Windows macinhes too a server on the other network.

I know I've not done everything I'm supposed too do too make it work but I don't know what I'm supposed too do. Does the Windows machines need to connect to the firewall through a tunnel? Do I have to install and configure L2PTD so that a Windows machine can connect to the firewall? Am I supposed too just connect to one of the servers on the other network after I'm done with IPSEC? How is the firewall supposed too look like in iptables for this too work?

I hope you can help me with this and if there is something unclear on this, just ask ;)

//Radapompa

---

### Post by Radapompa on 2010-06-29
Have tested some more on the iptables, but with no results. Have tested forward the remote network to my internal and forward my internal to the remote network. Also have tested accept incomming connections from the remote gateway to esp, udp 500 and udp 4500 with no results.

Any idea at all where it could be wrong?

//Radapompa

---

### Post by Radapompa on 2010-06-30
Lots of thoughts and I need some help on these.

So what I have understood from this is that I need to make the Ubuntu firewall to act as a Ipsec client. To do this it needs to connect through the localnetwork behind it. So I was thinking of if I can make it go through eth1 which has an adress to the local network and then connect to the remote network? Remember, the firewall is connected directly on to the internet so it is the gateway for the other network.
Since I don't have a clue on how to do this, I really need some help on this. As I said in the first post. I've got now OpenSwan on the Ubuntu firewall, but it's not necessary that I need it if there exists something better. 

//Radapompa

---

