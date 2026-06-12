---
title: "[SOLVED] Server 8.04 LTS on PowerEdge 2600 hostname problem"
date: 2008-12-07
forum: Networking &amp; Wireless
---

### Post by cjleonard on 2008-12-07
I am currently in a dilemma when I tracert my Server box.

> C:\*>tracert <Internal Network IP>

Tracing route to adsl-10-1-2.mia.bellsouth.net [Internal Network IP]
over a maximum of 30 hops:

  1     6 ms     1 ms     2 ms  adsl-10-1-2.mia.bellsouth.net [Internal Network IP]

Trace complete.

Attempted

> /etc/hosts

127.0.0.1       localhost
127.0.1.1       <Server Name>.mia.bellsouth.net       <Server Name>

-and-

> /etc/hostname

<Server Name>

I named the box something different and yet I still see it as **"adsl-10-1-2.mia.bellsouth.net"** Another thing, I don't use BellSouth. They are a slow ISP, in my opinion.

Thank you in advance. FYI COMMAND LINE/NO GUI

---

### Post by jmoorse on 2008-12-08
1. Is your server eth interface on DHCP?  If so what is the provider of addressing?  I would check it is not auto-appending said suffix.

---

### Post by cjleonard on 2008-12-08
> **jmoorse said:**
> 1. Is your server eth interface on DHCP?  If so what is the provider of addressing?  I would check it is not auto-appending said suffix.

Yes. The server is set with DHCP, however the router is assigning the address based on Address Reservation. Configured /etc/network/interfaces with static address and still resolves the same.

I have a feeling it has something to do with my internal network, but should it not show the server host name instead of adsl-10-1-2.mia.bellsouth.net :confused:

Just traced the route to another address on my network and it came out with adsl-10-1-3.mia.bellsouth.net. What in the hell is going on here?

---

### Post by cjleonard on 2008-12-08
Turns out my router resolves to **"adsl-10-1-1.mia.bellsouth.net"**

Now im confused and will need to play some more with my network to make it work.

---

### Post by cjleonard on 2008-12-08
Turns out my router resolves to **"adsl-10-1-1.mia.bellsouth.net"**

Now im confused and will need to play some more with my network to make it work.

---

### Post by jmoorse on 2008-12-08
What internal address are you pinging?

---

### Post by cjleonard on 2008-12-08
The gateway for my router. I uset he range of 65.10.1.0/24 on my network and the gateway is 65.10.1.1 When I tracert the gateway of my router is responds with adsl-10-1-1.mia.bellsouth.net. I really don't understand why it would do that.

---

### Post by jmoorse on 2008-12-08
Because you are using public IPs (no NAT) you are receiving a reverse DNS lookup that corresponds to your ISP (or the IP block you ISP is subleasing).

This is because your default gateway is _their_ router 1.1 correct?

Where/what is your DHCP server?

Also, you may want to edit out your public IP block just to be safe :)

---

### Post by cjleonard on 2008-12-08
Yes, I run a home based router for my network which uses NAT for my internal networking. The router is setup for DHCP and assigns automatically, except for the servers I host.

What is this Public IP Block?

---

### Post by jmoorse on 2008-12-08
Public IP blocks are IPs that are globally accessible (e.g.: the ip for google.com, or ubuntuforums.org)

Common private addresses are in the ranges:
10.0.0.0 - 10.255.255.255
172.16.0.0 - 172.31.255.255
192.168.0.0 - 192.168.255.255

(see: [http://en.wikipedia.org/wiki/Private_network](http://en.wikipedia.org/wiki/Private_network) for more info)

If you set up your internal addressing to incorrectly be the 65.10.1.0/24 range it will `work`, but will break connectivity to that valid external network.  E.g.: if ubuntuforums.org resolved to 65.10.1.37 you would get a page cannot be displayed because it lives outside your network and your router thinks that it owns that range.

---

### Post by cjleonard on 2008-12-08
Jeff, thank you. I feel so stupid not relizing I was using an improper internal address. I will change this as soon as I get home tonight.

Can't believe it's been 3 years since I took a CCNA course, but never followed through with it and it's caught up with me. Im a senior in college now and was a senior in high school when I took that course.

Again thank you! If this is the problem, im going to laugh all night long at myself and bellsouth for having the address range 65.10.1.0/24

---

### Post by cjleonard on 2008-12-08
Well Jeff, I'm laughing about it.

> OrgName:    BellSouth.net Inc. 
OrgID:      BELL
Address:    575 Morosgo Drive
City:       Atlanta
StateProv:  GA
PostalCode: 30324
Country:    US

ReferralServer: rwhois://rwhois.eng.bellsouth.net:4321

NetRange:   65.0.0.0 - 65.15.255.255 
CIDR:       65.0.0.0/12 
NetName:    BELLSNET-BLK6
NetHandle:  NET-65-0-0-0-1
Parent:     NET-65-0-0-0-0
NetType:    Direct Allocation
NameServer: AUTH-DNS.ASM.BELLSOUTH.NET
**NameServer: AUTH-DNS.MIA.BELLSOUTH.NET**
NameServer: AUTH-DNS.MSY.BELLSOUTH.NET
Comment:    
Comment:    For Abuse Issues, email [email]abuse@bellsouth.net[/email]. NO ATTACHMENTS. Include IP
Comment:    address, time/date, message header, and attack logs.
Comment:    For Subpoena Request, email [email]ipoperations@bellsouth.net[/email] with "SUBPOENA" in
Comment:    the subject line. Law Enforcement Agencies ONLY, please.
RegDate:    2003-12-29
Updated:    2007-02-28

RAbuseHandle: ABUSE81-ARIN
RAbuseName:   Abuse Group 
RAbusePhone:  +1-404-499-5224
RAbuseEmail:  [email]abuse@bellsouth.net[/email] 

RTechHandle: JG726-ARIN
RTechName:   Geurin, Joe 
RTechPhone:  +1-404-499-5240
RTechEmail:  [email]ipoperations@bellsouth.net[/email] 

OrgAbuseHandle: ABUSE81-ARIN
OrgAbuseName:   Abuse Group 
OrgAbusePhone:  +1-404-499-5224
OrgAbuseEmail:  [email]abuse@bellsouth.net[/email]

OrgTechHandle: JG726-ARIN
OrgTechName:   Geurin, Joe 
OrgTechPhone:  +1-404-499-5240
OrgTechEmail:  [email]ipoperations@bellsouth.net[/email]



Notice the **bold** is where I am getting the DNS of mia.bellsouth.net :D

---

### Post by jmoorse on 2008-12-08
Haha, glad I could help.

And I have seen this problem a few times in the field.  In fact I think some time ago there was a SoHO router that was manufactured with internal addressing of 200.200.200.0/24 ....

---

