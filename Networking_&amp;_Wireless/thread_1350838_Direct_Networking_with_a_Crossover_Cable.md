---
title: "Direct Networking with a Crossover Cable"
date: 2009-12-09
forum: Networking &amp; Wireless
---

### Post by leftfootleashed on 2009-12-09
I may be repeating something someone else has written here, but I couldn't find it so I thought I'd post my solution in case anyone else has the same problem:

Basically my music collection is too large to transfer practically over a wireless connection, so I got hold of a crossover cable.
At first I couldn't figure out how to use this to transfer files but this is what I did:

1. In System > Preferences > Network Connections, under the Wired tab, select the wired connection (e.g. eth0) and click Edit.

2. Under the IPv4 tab, change Method to Link-Local Only. Apply and close Network Connections.

3. Repeat 1 and 2 on the other computer.

3. On either computer, use Places > Connect to a Server to set up connection. I used SSH (as far as I can see you only need the openssh-client package, not the -server package). Under server, enter the IP address of the computer you want to connect to - to find it run
```
ifconfig 
```
in a terminal on that computer - the IP address is shown in the eth0 section after "inet addr:". Enter the username you want to log in to on the computer you are connecting to. The root of the filesystem on the other computer should open in Nautilus.

Hope this helps someone. Feel free to correct me if I've made any mistakes.

---

### Post by Mr. Matt on 2010-01-27
Yes! Thank you! This was so simple and much easier to follow than the other instructions I found.

---

