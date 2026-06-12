---
title: "Network-manager WPA connection problem"
date: 2010-10-14
forum: Networking &amp; Wireless
---

### Post by ario on 2010-10-14
Hi,
I want to connect two Ubuntu 10.04 computers wireless in Ad-Hoc mode.
**I can not connect them using WPA2 encryption mode.**
I can only connect using WEP or None encryption modes. This is the test result:
**Using WEP or None encryption modes:**
[INDENT]First computer will establish ad-hoc connection and waits for the other computer.
Second computer will detect connection and starts to connect to it. It will generate a connection with a name like "Auto connectionname". It will try to connect but fails! Until I edit the connection and enter the encription mode and passphrase and manual IP addresses and then reconnect it. **It will then connect and both computers can ping each other.**
[/INDENT]
**Using WPA2 personal mode:**
[INDENT]
Same as WEP or None encryption modes. But after manually setting encryption mode and IP addresses **It will fail again and establishes a new ad-hoc connection with different Cell-ID** and waits for the other computer to join it.
If I select the new established connection on the first computer to connect to it, first computer will fail to connect and will establish yet another connection itself with a new Cell ID. And this can continue in an endless loop.
[/INDENT]
Some times when I delete all connections in both computer again and again and establish new connections, they may eventually got connected; but it's only once and I can not reconnect them later.
Any Idea how to solve this problem? I need to connect them secure using WPA2 mode.
Should I report this as a bug?
Any response will be appreciated guys.

---

### Post by ario on 2010-10-15
I still cant get WPA to work. BUMP!

---

### Post by MartyBuntu on 2010-10-15
I highly doubt your network adapter supports WPA mode over Ad-Hoc.
Frankly, I'm surprised it even supports WEP. Most Linux/Windows ICS setups don't allow for encryption over Ad-Hoc (for most adapters that I have seen).

---

### Post by ario on 2010-10-15
> **MartyBuntu said:**
> I highly doubt your network adapter supports WPA mode over Ad-Hoc.
Frankly, I'm surprised it even supports WEP. Most Linux/Windows ICS setups don't allow for encryption over Ad-Hoc (for most adapters that I have seen).

Well, actually I'm using DWA-125 D-Link Wireless adapter. I created a topic to bring up networking based on this adapter and on 10.04. The topic went until I prepared the driver installation successfully, created a really working Ad-Hoc WEP encrypted network (Which I tested several times), but didn't figured out how to connect in WPA mode.
Chili555 then suggested me to create a new topic and find a solution in network-manager part.
So the problem still exists:
WEP, NONE modes working like a charm.
WPA, don't even think of it!
Any Idea?

---

### Post by MartyBuntu on 2010-10-16
> **ario said:**
> 
Any Idea?


Use a better networking scheme than ICS.

Cheap switch or router.

---

### Post by ario on 2010-10-16
> **MartyBuntu said:**
> Use a better networking scheme than ICS.

Cheap switch or router.

Thanks for the response. But, what is ICS? I googled that but didn't find anything relevant.
On the other hand, if you mean buying a router and use the Infrastructure mode, then it is different. I bought my current adapter for about 50$ here, but will not buy an 80$ DSL modem with built-in router until I determined that I cannot establish a safe WPA connection with this dangle. Because then all I can do with that 50$ dangle is to drop it right into the trash can!:D
Any Idea how to establish an Ad-Hoc WPA2 network using network-manager and the DWA-125 adapter?
Thank you guys:)

---

### Post by MartyBuntu on 2010-10-16
> **ario said:**
> Thanks for the response. But, what is ICS?

Internet Connection Sharing.

> **ario said:**
> ...but will not buy an 80$ DSL modem with built-in router until I determined that I cannot establish a safe WPA connection with this dangle.

A decent wireless router can be found for less than $20. The value you put on your time is of course, entirely up to you. 

> **ario said:**
> 
Any Idea how to establish an Ad-Hoc WPA2 network using network-manager and the DWA-125 adapter?


You can't. TKIP encryption only works on infrastructure mode, not Ad-Hoc.
It's hard-coded into any wireless adapter you'll find on the shelves.

---

### Post by ario on 2010-10-17
> You can't. TKIP encryption only works on infrastructure mode, not Ad-Hoc.
It's hard-coded into any wireless adapter you'll find on the shelves.

Thank you Marty. But what about this: I read in wikipedia that TKIP is used by WPA1 but WPA2 uses AES instead?

---

### Post by ario on 2010-11-01
Bump!

---

### Post by ario on 2010-11-09
Bump!

---

### Post by ario on 2010-11-16
Guys, I still cannot connect Ad-Hoc in WPA mode using dwa-125! Say something! Bumpity Bump!

---

### Post by ario on 2010-11-23
Maybe in future linux systems can do such a thing. But for now it is impossible!

---

### Post by cybergnome on 2010-11-23
You should be aware that some wireless adapters (I have no idea about yours) can be configured as access points.  I have one that will operate as both a station and an access point at the same time.  That might help you with the encryption issue, but you'll still have to deal with packet routing, if you're going to share you internet connection.  A cheap router, as suggested, is a better choice, IMO.

---

