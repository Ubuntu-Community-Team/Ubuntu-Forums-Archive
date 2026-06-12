---
title: "DNS Packets to custom port"
date: 2012-08-10
forum: Networking &amp; Wireless
---

### Post by nmvictor on 2012-08-10
I'm looking to redirect DNS UDP packets on port 53 to a local port where my application is listening. I am targeting the packets from the DNS servers, in response to DNS queries made from my host or other hosts on the network. My main goal is to have a full DNS packet with the Question and Answer section, so I can parse it to test my application.

I have been working with the command below, but it gets me the packets with a Question section only, the Answers, Authority e.t.c sections are empty.

Here is the command I have been using:
```
sudo iptables -t nat -A OUTPUT -p udp --dport domain -j REDIRECT --to-destination 127.0.0.1:9872
```

How do I get the packets as described above, Please advice how I can adjust the above command or propose a new one.

Thanks for your help.

---

