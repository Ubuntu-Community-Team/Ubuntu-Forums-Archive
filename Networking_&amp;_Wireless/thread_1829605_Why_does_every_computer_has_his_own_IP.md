---
title: "Why does every computer has his own IP?"
date: 2011-08-20
forum: Networking &amp; Wireless
---

### Post by stamatiou on 2011-08-20
Hey guys,
I am trying to learn networks lately but I have a question. Why does every computer has his own IP? When the packet arrives at the LAN it "finds its way" with the MAC Address doesn't it? So why does a Computer need a unique Ip?

---

### Post by walt.smith1960 on 2011-08-20
> **stamatiou said:**
> Hey guys,
I am trying to learn networks lately but I have a question. Why does every computer has his own IP? When the packet arrives at the LAN it "finds its way" with the MAC Address doesn't it? So why does a Computer need a unique Ip?

I'm no networking authority but I'm pretty sure MAC address has nothing to do with it.  When installing networked printers I.P. address is how I've designated printers.  MAC address can be used to include or exclude a particular adapter from a network but data is routed by I.P. address AFAIK.

---

### Post by Basher101 on 2011-08-20
the MAC adress is your physical "fingerprint" of your network card. The IP comes from your Modem (or router). This is needed for the DNS server to work, so a website called [www.google.com](www.google.com) is what you need to type into your browser, and not numbers like 241.123.457 or sth like this. The DNS "translates" the numbers to words.

---

### Post by dave01945 on 2011-08-20
i have recently been learning about networking there are some good free videos on this website

[http://www.learntcpip.com/](http://www.learntcpip.com/)

there abit old but they still apply

mac address is to do with discovering what ip the packets need to be sent to the videos are very helpful

---

### Post by papibe on 2011-08-20
Read this couple of pages:
[LIST]
[*][Why do we use IP address for routing/communication and not MAC address?]("http://answers.yahoo.com/question/index?qid=20110410175602AAVnwC0")
[*][If MAC address then why IP address?]("http://wiki.answers.com/Q/If_MAC_address_then_why_IP_address")
[/LIST]
Basically, MAC addresses are like Social Security Numbers (or any ID). That is, just a random number. IP addresses are hierarchical (most like phone numbers), and designed specifically for managing networks, subnetworks and routing.

Regards.

---

### Post by lisati on 2011-08-20
You might like to think of it this way: An IP address is a computer network's equivalent of a phone number, and a MAC address it the equivalent of the serial number printed on the bottom of the phone. The IP address identifies the connection, and the MAC address identifies a particular piece of hardware.

---

### Post by stamatiou on 2011-08-22
Thank you very much, but I hae read in a forum that for example if I want to send a packet to a computer in the same LAN I send it with the MAC Address (that's why we also use the ARP to have the IP to MAC Table). When do we use the IP and when the MAC?

---

### Post by stamatiou on 2011-08-22
Thank you very much, but I have read in a forum that for example if I want to send a packet to a computer in the same LAN I send it with the MAC Address (that's why we also use the ARP to have the IP to MAC Table). When do we use the IP and when the MAC?

---

### Post by haqking on 2011-08-22
> **stamatiou said:**
> Thank you very much, but I have read in a forum that for example if I want to send a packet to a computer in the same LAN I send it with the MAC Address (that's why we also use the ARP to have the IP to MAC Table). When do we use the IP and when the MAC?

You dont do it.  ARP does it transparently for you.

ARP is like DNS, it resolves the IP to MAC for you

This is from a post i made earlier in a different thread explaining MAC addresses:

MAC addresses are unique and they are a 48 bit (12 digit) unique address.

the first half of the address (24 bits) identifies the manufacturer.   The second half or (24 bits) is or should be unique to the device.

There in theory should never be a repeat, however a few years ago mass  production of cheap knocks off in China flooded the market with repeat  identifiers but it hasnt really been an issue.

The MAC is a hardware (burned) address and the IP is a logical one (dynamic)

IP is routable which is what we need in routed environments usch as the  Internet.  Once the packet reaches the LAN associated with the source IP  another protocol known as ARP takes over and resolves the IP to the MAC  address so it knows where to deliver the packet.

Using software it is also easy to change (spoof) your MAC address to  make packets appear to have come from another machine then they really  did, this is something you may need to do during WPA cracking for  example. However i will not discuss that here :wink:

---

### Post by Gwaro on 2011-08-22
> **haqking said:**
> You dont do it.  ARP does it transparently for you.

ARP is like DNS, it resolves the IP to MAC for you

This is from a post i made earlier in a different thread explaining MAC addresses:

MAC addresses are unique and they are a 48 bit (12 digit) unique address.

the first half of the address (24 bits) identifies the manufacturer.   The second half or (24 bits) is or should be unique to the device.

There in theory should never be a repeat, however a few years ago mass  production of cheap knocks off in China flooded the market with repeat  identifiers but it hasnt really been an issue.

The MAC is a hardware (burned) address and the IP is a logical one (dynamic)

IP is routable which is what we need in routed environments usch as the  Internet.  Once the packet reaches the LAN associated with the source IP  another protocol known as ARP takes over and resolves the IP to the MAC  address so it knows where to deliver the packet.

Using software it is also easy to change (spoof) your MAC address to  make packets appear to have come from another machine then they really  did, this is something you may need to do during WPA cracking for  example. However i will not discuss that here :wink:



I like your explanation.However,i would to add on that in MAC addresses are more helpful in a LAN(though IP addresses are needed for their translation) and IP addresses are helpful in routing of Packets outside the LAN:they help packets to reach their destined LANs

---

