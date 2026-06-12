---
title: "Splitting traffic over interfaces by port"
date: 2010-07-28
forum: Networking &amp; Wireless
---

### Post by lukelambert on 2010-07-28
I have two internet connections in my apartment and two NICs in my Ubuntu box.

connection1: I pay for from a cable company
connection2: Provided by my apartment complex
eth0: connected to connection1
eth1: connected to connection2

I have a lot of traffic over a certain port (say, port 1234) that I would like routed over eth1 (my apartment's service), and all other traffic routed over eth0 (my service). 1234 should be the only open port on eth1, as I have file sharing and other services intended only for my local network enabled. And no traffic on 1234 should go through eth0 as it slows down my connection greatly.

eth0/connection1: all ports but 1234
eth1/connection2: only 1234

Can anyone tell me how to configure Ubuntu so that traffic on a specific port is routed to a specific interface? I think this has something to do with iptables.

---

### Post by Iowan on 2010-07-28
You might also check [UFW]("https://help.ubuntu.com/community/UFW").

---

