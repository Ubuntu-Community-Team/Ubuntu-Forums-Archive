---
title: "Port forwarding problem"
date: 2010-05-16
forum: Networking &amp; Wireless
---

### Post by /tmp on 2010-05-16
Hello

It isn't just another question "How to access my PC from the Internet"

My problem is the following:
For example, I have Apache working on port 80. I use NAT on ADSL router and I forwarded port 80 to my PC. So Apache is accessible from the Internet. But I can't access it from my PC's IP-address: I just have no response from Apache (e.g. if my IP-address is 12.34.56.78, I can't access 12.34.56.78:80). Surely, I can use localhost or 127.0.0.1 or other local addresses instead of external one, but I need to access an external address for some reasons

I scanned localhost and 12.34.56.78 via Nmap and got following:
> 80/tcp  **open**  http
it is for localhost
> 80/tcp **filtered** http
and it is for 12.34.56.78. All forwarded ports will be filtered

I didn't have this problem using Windows. Now I use Ubuntu 10.04. ufw is disabled

How can I access forwarded ports via external IP?


Thank you.

---

### Post by Iowan on 2010-05-16
From inside the network, you *should* be able to use the server's internal address. From what I've read, routers generally block (as "spoofed") internal addresses trying to access the network on an external port.

---

