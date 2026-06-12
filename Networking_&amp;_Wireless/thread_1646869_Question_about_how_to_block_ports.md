---
title: "Question about how to block ports"
date: 2010-12-16
forum: Networking &amp; Wireless
---

### Post by justinmiller87 on 2010-12-16
I was following the directions over on the page [How to watch Hulu overseas without a proxy server]("http://supermariodiplomacy.wordpress.com/2010/07/10/how-to-watch-hulu-overseas-without-a-proxy-server/") and got to the section about blocking ports, which I need to block port 1935. I figured this would be easy, as the mac instructions are ```
sudo ipfw add 0 deny tcp from any to any 1935
sudo ipfw add 0 deny udp from any to any 1935
``` and the Windows instructions are practically a book in itself. Since this page was lacking instructions on how to do it in Ubuntu, and ipfw seemingly doesn't exist in Ubuntu, how do I block the ports?

Thanks.

---

### Post by spiky001 on 2010-12-16
By default all ports are closed in linux, you have to open then up

---

### Post by amauk on 2010-12-16
Are we talking in-bound or out-bound here?

For in-bound (stuff from outside coming to your machine), a port is not "open" unless 2 things are true
1) Your machine is accessible from the outside
2) You have a service on your machine listening to that port

Outbound traffic (stuff from your machine to the outside world) tends to be sent out from a random port number between 49152 & 65535

From the page you linked to, it's not really clear what they're telling you to block (in-bound, out-bound, or both)

It's also not clear whether they want to to "drop" or "reject" packets
Drop discards the packet silently without informing the sender
Reject discards the packet and informs the sender that it's been rejected

Anyway, as root:
```
iptables -A INPUT -p tcp --dport 1935 -j DROP
```will drop all TCP packets in-bound to your machine to port 1935

You may need several of these, depending on how many different combinations of packets you want to reject

- Changing "-A INPUT" to "-A OUTPUT" will alter the direction (input is in-bound packets, output is out-bound packets)
- Changing "-p tcp" to "-p udp" will alter the protocol of matched packets (TCP or UDP)
- Changing "-j DROP" to "-j REJECT" will alter how your machine responds to rejected packets

---

