---
title: "How can several PC's get online through one USB ADSL modem?"
date: 2009-11-05
forum: Networking &amp; Wireless
---

### Post by Ulysses_ on 2009-11-05
In windows it can be done with internet connection sharing. In debian lenny, what options are available to achieve the goal of providing internet access to all computers in the LAN if the only modem available has just a USB cable?

---

### Post by t0mppa on 2009-11-05
Not sure if Lenny uses Network Manager, but if it does it should be [as simple as on Windows]("http://jeremy.visser.name/2009/03/24/simple-internet-connection-sharing-with-networkmanager/").

Alternatively, you can set up [bridging]("https://help.ubuntu.com/community/BridgingNetworkInterfaces") through */etc/network/interfaces* file, in which case you'll have to configure all the relevant connections there and not use fancy GUIs for them. This should be the same on Ubuntu and Lenny, but if you really want specified Lenny help, try posting on Debian forums instead.

---

### Post by Ulysses_ on 2009-11-06
Thanks.  I'm a bit confused with terms, is NAT a special case of bridging?

---

### Post by t0mppa on 2009-11-06
You could say that, actually NAT is just a service that requires the bridging of two or more interfaces in order to work. Bridging basically just means forwarding packets from one interface to another, i.e., physically sharing the connection.

NAT on the other hand is short from Network Address Translation and works on a higher layer, letting one device "hide" lots of other devices that connect through it from the Internet by translating all the packets to seem as if they were coming to and going from it, instead of the group of devices connected to it.

You could think of it like having a group of French speakers discussing with a group of Chinese speakers and both groups having a translator who translates all the messages sent out into English and those coming in back to their native language, so to any outsider it would simply appear like an exchange of messages between two English speakers.

Common usage of NAT is one of the reasons why IPv4 hasn't run out of address space yet. On the other hand, it breaks down the original philosophy of end-to-end connectivity that the IP address scheme was designed for and thus makes things more complex and lowers performance.

---

