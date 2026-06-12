---
title: "PPTP client"
date: 2009-03-24
forum: Networking &amp; Wireless
---

### Post by CharlieNixon on 2009-03-24
I am unable to connect to a PPTP server on the Internet from my Ubuntu 8.10 pptp client. Here are the details:

I have these two packages installed: pptp-linux & network-manager-pptp.

I have configured the client with my info (server,username, password, etc) and it fails to connect. I know it's not a problem with the server or account because I can connect to that server using the same account from my iPhone and my laptop (Ubuntu 8.04). 

I think it's not a network problem because I have taken a traffic capture while attempting to connect and have confirmed traffic is flowing back and forth from my machine (in a NAT range) to the VPN server on the Internet. 

I suspect one of two things:

1) a network problem - I do not believe it is a network problem, as I said, I can see the traffic going back and forth from my computer to the public IP of the VPN server. But it is worth mentioning that the other systems that are able to connect are on a different network.

2) a VPN client application/configuration problem: I'm not as good at troubleshooting application problems, so I may have something completely wrong or missing. Also, the vpn manager on my laptop (which works) looks different then the one on my desktop (which doesn't work).

Any help?

*note - putting the problem machine on the known-good network is very difficult, though not impossible. I haven't done this yet, but I will if necessary.

---

### Post by CharlieNixon on 2009-03-25
bump?

---

### Post by CharlieNixon on 2009-04-10
the answer to this problem turned out to be both (1) and (2) from above. I had some unnecessary packages installed (which I have now removed) and it turns out that the firewall through which my traffic was egressing is not able to handle outbound GRE connections without a static 1-to-1 NAT on the internal IP address. 

It works fine now (when I go out a different firewall, that is).

---

