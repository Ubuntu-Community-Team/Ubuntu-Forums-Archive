---
title: "capture voip data for skype"
date: 2010-12-09
forum: Networking &amp; Wireless
---

### Post by h9uest on 2010-12-09
Hi all:

I'm using tcpdump and tcptrace to track all incoming and outgoing data packets through my network interfaces. But I fail to monitor the voip data for skype that way, although it works well with http port 80, for example. 

I want to track the ip address of the data packets for skype, i.e. know the ip address of the other one speaking at the other end of skype. How can I achieve this?

FYI, I've checked the port setting in my skype and I'm sure I'm listening on the right port. But nothing is showing up while I'm in connection with skype.

Thanks a lot.

---

### Post by puppywhacker on 2010-12-09
Skype uses P2P protocols to route packets. I don't think you will ever see the end-point you are connecting to. Rather it is distributed over a bunch of other (super) nodes. Skype uses a lot of secretive stuff

to see which connections you have there is no need to tcpdump, an netstat is enough.
```
netstat -tulpn | grep skype
```

---

### Post by h9uest on 2010-12-11
Thanks, dude.

---

