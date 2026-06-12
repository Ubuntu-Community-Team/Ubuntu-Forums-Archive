---
title: "3com card problem"
date: 2012-09-26
forum: Networking &amp; Wireless
---

### Post by SummerT on 2012-09-26
We are having problems accessing the internet.  Our wired access is listed as on , but firefox indicates server not found when trying to get on the internet.
 
Through some several entries of codes etc, we have come across another issue with the 3com card.  It appears it is on "half duplex" and needs to be "full duplex".
 
We've looked at some other threads and suggestions to fix this, but ethtools is usually the way people are suggesting to run.  However, we keep getting errors that ethtools is not available (either it isn't downloaded or whatever).  We can't get/download ethtools because we can't connect to the internet with that computer to download it.
 
Someone suggested we try the mii tool, in which we typed in sudo mii-tool eth0.
It came up as
 
```
 
eth0: 10Mbit, half duplex, link okay

```
 
Then someone said 
sudo mii tool v eth0 and it came up
 
```
 
eht0: 10Mbit, half duplex, link okay.
product info: vendor00: 10:5a, model 0 red 0, basic mode 10mbit, half duplex
basic status link okay.
Capabilities: 100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD
Advertising: 100baseTx-FD slow control..."    "    "

```
 
Then someone said to set capibilities to type in mii tools f 100basetx-FD eth0.  And then nothing happened.
 
And because we have been trying different suggestions for codees, we don't know if we turned off autonegotiation now.
 
What can we do?

---

### Post by Iowan on 2012-09-27
Half duplex would be standard for 10MB...
Can you can ping the router, other network machines, etc.?

---

### Post by SummerT on 2012-09-27
No, I can't.  I tried to connectu automatically dchp and could not get an established connection.
 
I don't know my IP address, so I ran an ifconfig -a and eth0 did not come up having an IP address. Not knowing what to do, I put the address that was in the auto lo loopback, whcih was of course 127.0.1.1.
 
Then not know what to do, I put that 127 number in manual in the network tools. And then I was able to get an established connection, but still not connected to the internet.  Of course i didn't know that this address is incorrect.  
 
So I still need advice to make this work.
Thanks

---

### Post by wildmanne39 on 2012-09-28
Thread closed. Please do not post duplicates, it dilutes community effort.

---

