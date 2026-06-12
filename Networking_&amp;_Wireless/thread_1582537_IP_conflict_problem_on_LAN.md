---
title: "IP conflict problem on LAN"
date: 2010-09-26
forum: Networking &amp; Wireless
---

### Post by piyush.neo on 2010-09-26
i am connected to  LAN where i have to manually configure my IP settings. While using windows as soon as i try any IP which is already being used on LAN, "IP conflict message" is poped and if someone else try to use my ip i am not at all effected by it. But on Ubutntu, there is nothing as such, it keep on using the duplicate IP with very slow speed and never inform if there is ip conflict as a result i had to waste a lot of time on selecting an unused IP by surfing net for couple of minutes on each ip...
Plz suggest any simple  method for selecting  an unused IP..:confused:

---

### Post by elliotbeken on 2010-09-26
DHCP can be used or auto ip but it seems to simple or have i missed something out. ?

---

### Post by piyush.neo on 2010-09-26
> **elliotbeken said:**
> DHCP can be used or auto ip but it seems to simple or have i missed something out. ?
DHCP is not supported...i have to manully enter the IP.

---

### Post by SeijiSensei on 2010-09-26
Why can't you and the network administrator agree on a unique address for your computer that you can use all the time?  If you're going to have static IP assignments, then they should be just that -- static.  No one should have to guess an address and worry that it might conflict with another machine on the network.

---

### Post by Iowan on 2010-09-26
It would seem to be a network management nightmare to require each machine to choose it's own static IP. You could ping a potential IP to see if an owner responds. There are some ways (which I've forgotten) to see what subnet addresses are in use - but the real solution would be better address management.

---

### Post by RetchingRabbit on 2010-09-26
Another possibility might be to scan the network with nmap. 

Something like ```
nmap 192.168.1/24
```where 192.168.1.x is the local area network address.
You had best advise the "administrator" of your intentions so the poor unfortunate doesn't think he's being cracked....

---

### Post by piyush.neo on 2010-09-27
> **SeijiSensei said:**
> Why can't you and the network administrator agree on a unique address for your computer that you can use all the time?  If you're going to have static IP assignments, then they should be just that -- static.  No one should have to guess an address and worry that it might conflict with another machine on the network.

Well i am a student at college...No network manager has time for  solutions that change their networks (after all they are human..).....assign static IP is not practical at this point of time as *lowan *has already mentioned...
I am afraid if nmap is good enough to scan my subnet if i am not being assigned a valid IP...Even if i have a valid ip, nmap is slower than my *hit and trial* method.....Any more ideas.....

---

### Post by piyush.neo on 2010-10-07
Well finally for  me....Ettercap is working great...:)

---

