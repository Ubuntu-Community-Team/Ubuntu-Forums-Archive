---
title: "very difficult to monitor network"
date: 2011-07-06
forum: Networking &amp; Wireless
---

### Post by Sharft 6 on 2011-07-06
For the last couple of weeks I have been trying to figure out what application is uploading and downloading 0-2KB/s. So far I have figured out that the ip and ports are random and nothing else.

I have tried looking through a huge list of processors (sudo ps -a) and killing a bunch of them but the traffic usage hasn't died down at all.
e.g.
transmission-da
mythtv-backend
mythfrontend
mythfrontend.real
vsftpd
httpd
smbd
srcds

I have tried ntop but that doesn't work.

I have tried iftop but that doesn't give me anything useful.

I have tried nmmap but again that doesn't bring up anything useful.

I have tried wireshark and whois but all that shows is the traffic is comming from and going to random ip addresses and ports. The only consistency is that the protocol is UDP.

I have tried netstat but that doesn't bring up anything useful either.

Those are just the tools I remember using. I have used more but obviously didn't get anywhere with them.

Does anybody have anymore ideas?

OS: mythbuntu 10.04

---

### Post by Sharft 6 on 2011-07-06
:o I found one by looking at the local port in wireshark. So if I'm receiving the packet I would check destination port and if I'm sending the packet I would check source port. then I would use that port in the following command.

```

[COLOR="Red"]sudo netstat -pa | grep 51413[/COLOR]
tcp        0      0 *:51413                 *:*                     LISTEN      2118/transmission-d
tcp6       0      0 [::]:51413              [::]:*                  LISTEN      2118/transmission-d

```

Now that I've terminated transmission I still get a whole bunch of traffic and now wireshark says "Destination unreachable (Port unreachable)". Owell I guess all my peers will eventually figure out that I'm unreachable and stop trying.

---

