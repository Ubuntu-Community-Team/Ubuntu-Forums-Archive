---
title: "Connected to Network but not Internet"
date: 2012-02-07
forum: Networking &amp; Wireless
---

### Post by danikhani on 2012-02-07
Hello 
Ive recently installed ubuntu server on my pc but I can connect to the network (can ping my router) but i cant connect to internet (cant ping yahoo.com even cant ping the ip address from yahoo).In my resolv.conf there is no setting. 
also i have dhcp activitated on my router (internet modem ) and Ive set my mac address to give me a static ip. 
pls help :confused:
Danik

---

### Post by danikhani on 2012-02-07
so guys i found the solution somebody helped me on ubuntu irc channel :P
solution:
i had the problem that 2 dhcp servers were into network and they were messing with my ubuntu.
so i did
```
tcpdump -s 0 -n udp port 68
``` 
on one windows then i did ctrl+alt+f1 and did 
```
ps auxww | grep dhclient
```
and then killed the PID from dhclient
after that i went back to the first windows ctr+alt+f2
and watched the resault and i saw that actually 2 dhcp servers are giving me ips :P thx to that guy on irc :guitar:
hoped i helped you

---

