---
title: "Ubuntu netbook to Ubuntu PC ICS Problem"
date: 2010-07-23
forum: Networking &amp; Wireless
---

### Post by bluebriant on 2010-07-23
I have managed to share my internet connection from my aspireone netbook (Ubuntu 9.10) to my PC running XP. This seems to work fine - after I unplug the lan connection and then reconnect. However, if I try to do the same with another Ubuntu PC(9.10), it just says "no connection".  I have checked all the settings on network manager like sharing etc and nothing seems to work. I have also tried a cross-over cable. Still no luck. I even downloaded firestarter - still no joy. What can be the problem?

My netbook is connected via wifi to my router. I know that the simplest solution is to buy a usb wifi for my PC, but this seems to be a waste and it doesn't suite me to do this.

---

### Post by Iowan on 2010-07-23
So, the wire is the shared port? 
The netboot remains able to connect - even if the client cant?
How does the client get IP address?
Can client ping netbook - or vice-versa?

---

### Post by bluebriant on 2010-07-24
[LIST]
[*]The Netbook connects to the Internet without problems
[*]The wired port is connected to the PC (LAN cable)
[*]The Netbook is connected to the router via WiFi and then to the Internet
[*]I think the client obtains the IP address automatically via Network Manager
[*]How do I ping the client if I can't see the IP of the client on my Netbook?
[/LIST]

---

### Post by Iowan on 2010-07-24
Check **ifconfig -a** on client to get IP information. The netbook wired connection and the PC will need addresses in the same subnet. 
[This]("https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless") wireless ICS might have sume useful information - but it's the wrong-way-around (wireless client to wired "server").

---

### Post by bluebriant on 2010-07-24
My system is now up and running. A bit mysterious, but I hooked up my LAN cable to my spare Netbook, made sure that eth0 was shared to other computers and now I am running

Network Manager really works! Thanks for the help.
:p

---

### Post by Iowan on 2010-07-24
Glad it works - if it STAYS fixed, you can use the Thread Tools to mark this one [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads"). :)

---

