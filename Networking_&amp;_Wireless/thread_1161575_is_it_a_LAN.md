---
title: "is it a LAN"
date: 2009-05-16
forum: Networking &amp; Wireless
---

### Post by dec7m2 on 2009-05-16
a LAN is a network with a centralized administation right but in a peer-to-peer network there is no central point of control or administration in the network. the why and how is peer to peer a LAN?

---

### Post by CyberMick on 2009-05-16
LAN == Local Area Network.
The name implies that the network is made up of geographically close nodes.
LAN can be either Peer to Peer or Client Server.
I.E. you can run something like Active Directory over your LAN and centrally administer access to files, printers etc.

Peer to Peer is where administration is not left to one central party and is usually seen in small workgroups. User accounts need to be administered on each individual machine.

WAN == Wide Area Network.
Usually used to link up LANs. I don't think I need to ellaborate on that one given the question asked.

Hope this helps a little.

---

### Post by dec7m2 on 2009-05-16
well i am in basic troubleshooting in my school 
this is what it says for what a LAN is(taken from the cisco website) 	

Local Area Network (LAN) refers to a group of interconnected devices that is under the same administrative control. In the past, LANs were considered to be small networks that existed in a single physical location. Àlthough LANs can be as small as a single local network installed in a home or small office, over time, the definition of LANs has evolved to include interconnected local networks consisting of many hundreds of devices, installed in multiple buildings and locations.

The important thing to remember is that all of the local networks within a LAN are under one administrative control group that governs the security and access control policies that are in force on the network. In this context, the word &#8220;Local&#8221; in Local Area Network refers to local consistent control rather than being physically close to each other. Devices in a LAN may be physically close, but it is not a requirement.  

and  for Peer to Peer

In a peer-to-peer network there are no dedicated servers or hierarchy among the computers. In this type of network, each device has equivalent capabilities and responsibilities. Individual users are responsible for their own resources and can decide which data and devices to share. Because individual users are responsible for the resources on their own computers, there is no central point of control or administration in the network.

Peer-to-peer networks work best in environments with ten or fewer computers. Because individual users are in control of their own computers, there is no need to hire a dedicated network administrator.

Peer-to-peer networks have several disadvantages:

    * There is no centralized network administration which makes it difficult to determine who controls resources on the network.
    * There is no centralized security. Each computer must use separate security measures for data protection.
    * The network becomes more complex and difficult to manage as the number of computers on the network increases.
    * There may be no centralized data storage. Separate data backups must be maintained. This responsibility falls on the individual users.

Peer-to-peer networks still exist inside larger networks today. Even on a large client network, users can still share resources directly with other users without using a network server. In your home, if you have more than one computer, you can set up a peer-to-peer network. You can share files with other computers, send messages between computers, and print documents to a shared printer.

i find that i don't understand why it falls under LAN

---

### Post by redmk2 on 2009-05-17
> **dec7m2 said:**
> ...
i find that i don't understand why it falls under LAN

You will find a bewildering amount of misnaming along with similar naming of unlike concepts and devices in Networking and System Administration in general

In this case one should try and understand what concept the Cisco website is trying to convey, and in what context it is being conveyed.

We Have LAN vs WAN.  We can agree; both are networks.  So the difference must be the type of network.  Local in this case means (as is stated) under one administration.  In this case the writer assumes you know ***what*** is to be administered in a network.

A network by ciscos's definition, I believe, is the infrastructure to **allow** the [COLOR="Blue"]interconnection[/COLOR] (but not the ([COLOR="Red"]***internetworking***[/COLOR] of hosts in a network.  By definition this does not include any control and administration of the hosts themselves.  That would be either domain wide or peer to peer administration of users, groups and individual software.  Either way cisco provides the services for the **proper operation of the network only**.

Some of these network services include a IP addressing scheme, dhcp, DNS, NAT'ing, a state full firewall, and routing.  These are all controlled  by a "network administrator" or organization.

With this idea established; the notion of whether they are domain controlled or peer to peer is not important as far as networking is concerned.

On last thought.  I used the term ([COLOR="Red"]***internetworking***[/COLOR] and did not define it.  Cisco considers ([COLOR="Red"]***internetworking***[/COLOR] to be the connection of separate LANS.  In a WAN situation we have the ([COLOR="Red"]***internetworking***[/COLOR] of LANs over telco controlled transit networks.

I hope this helps you.  If you need clarification or more info just ask.

---

