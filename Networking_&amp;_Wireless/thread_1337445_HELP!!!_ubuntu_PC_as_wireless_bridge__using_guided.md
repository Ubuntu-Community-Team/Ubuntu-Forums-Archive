---
title: "HELP!!! ubuntu PC as wireless bridge  using guidedog"
date: 2009-11-25
forum: Networking &amp; Wireless
---

### Post by maxxerific on 2009-11-25
hey all
   well here's my goal: 

home router (wireless)  --> ubuntu PC (wireless NIC + wired NIC) --> laptop (wired) (OSX or win)

i'm using an alfa wifi card to establish a connection to the router. 
Network Manager handles that okay (can connect to the internet in ubuntu no problem)

My laptop is connected to the ubuntu PC via rj45

From what i've read i can use guidedog (already tried firestarter)
to turn the  ubuntu box into a gateway. 
so i installed guidedog amd turned on masqerading etc

The alfa card has a dynamic IP assigned by the router in class 192.168.2.x
I set the IP of the other NIC (wired ethernet) in the ubuntu machine to 
10.0.0.2 to avoid subnet conflicts. 

the laptop is set with IP 10.0.0.5
gateway, dns: 10.0.0.2 (same as ubuntu machine)

i can ping the ubuntu machine with the laptop. 
but so far NAT seems to be broken (i can't get through to the internet on the laptop). 
Thought at first maybe it was just a dns issue (as firefox spins forever looking for a particular sight). 
but the same happens whether i use domain names or IP numbers. 


is network manager conflicting in some way? 
does guidedog expect to be connected to the WAN directly. My (very very rudimentary) understanding of networking would suggest that forwarded packets from guidedog to the router should in turn be handled no problem from the router to the WAN. 

erk.
i spent some time trying to set this up by manually editing config files. so maybe i've broken something. 

ANY advice would be super welcome. I need to figure this out so i can go back outside and stop drinking so much coffee.

-maxx

---

### Post by maxxerific on 2009-11-25
maybe i should ad, when guidedog starts its service i get 

```
/etc/rc.guidedog: line 58: warning: setlocale: LC_ALL: cannot change locale (US)
postconf: fatal: open /etc/postfix/main.cf: No such file or directory
Ignoring unknown interface wlan1=wlan1.
iptables v1.4.4: 
The "nat" table is not intended for filtering, the use of DROP is therefore inhibited.

```wlan1 being the alfa card which is connecting to the router 



but it does successfully start the NTP server (whatever that is). 

in linux there are so many things which look like crucial errors its hard to know which ones to investigate
 
lovely ignorance.

---

### Post by maxxerific on 2009-12-04
solved(ish) 
   purged guidedog - went back to firestarter. 
   flushed my IP tables - reinstalled network manager (got rid of WICD, sadly) 
   not sure what exactly did the trick - but everyrthing is golden.

---

