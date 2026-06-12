---
title: "Strange behaviour in Ubutnu vs Windows connecting to NAS over DDNS"
date: 2012-11-19
forum: Networking &amp; Wireless
---

### Post by ragr on 2012-11-19
Hi all,

Just to have it said;
I haven't been a big Linux user, but I'm trying to get there bit by bit.
I'm not a network expert but I like to fool around with it and learn as I go.
So please bare with me :)

The problem I've faced is a bit strange, I have a NAS server connected to a DDNS, I can access the NAS from my windows machine using the DDNS address but trying to do the same in Ubuntu 12.04 just times out.

The likely trigger for the problem is my router, a D-Link DIR 655. Reason for this suspicion is that I recently upgraded from D-Link DIR 635, in this version I could access the NAS using the DDNS address from the same Ubuntu machine I\m having trouble with now.

My network layout is straight forward:
WAN -> D-link DIR 655 -> QNAP 212 NAS

The D-link forwards a number of ports to the QNAP, e.g. webserver, ftp. These I can access using DDNS address from a windows machine but not my Ubuntu 12.04. (Though I can ping the DDNS address from Ubuntu)

If not using the DDNS address and instead using the internal LAN address, I can access the NAS without a problem.

My guess is that there probably is some difference in connection behavior between my windows and Ubuntu system that triggers connection refusal by the D-link when trying to connect using the  DDNS address.

I'm digging in the diff between D-link DIR-635 and DIR-655 to try what triggers the problem.

If you have any ideas or suggestions as to why this problem has turned up, or even better, how it can be tackled, I would be very thankful :)

---

