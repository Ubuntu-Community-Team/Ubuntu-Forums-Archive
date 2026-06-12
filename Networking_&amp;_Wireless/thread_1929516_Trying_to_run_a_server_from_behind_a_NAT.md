---
title: "Trying to run a server from behind a NAT"
date: 2012-02-22
forum: Networking &amp; Wireless
---

### Post by h.r. on 2012-02-22
Hey everyone, I've hit a wall and could use some advice.

I'm trying to run an http server from behind a NAT. I thought it would be as simple as poking a hole in the NAT by forwarding traffic addressed to port 80 to my IP address on the LAN.

But it doesn't work. The server is accessible inside the LAN without a problem. But for some reason when I make a request to my public IP, it can't make it through. But I do know it is making it past the NAT because when I close port 80 on my router, the request fails immediately. When I open it, it tries for a long time.

I ran a traceroute, and got a 30-hop sequence of * * *s. That doesn't mean anything to me.

Any ideas of things I should check?

---

### Post by roelforg on 2012-02-22
Tell us which http-server you use.
Also, make sure you've got a static ip.

My Ubuntu servers run fine behind my NAT and are perfectly accessible, so i think your NAT isn't working the way is should.

Wait!!!
Have you tried to use a mobile phone with wireless turned off?
My NAT prevents me from connecting to my public ip from the inside, maybe yours does so too.

---

### Post by h.r. on 2012-02-22
Wow, excellent suggestion, that was the problem. I tried from outside the LAN and it works fine. Thanks!

---

### Post by roelforg on 2012-02-22
> **h.r. said:**
> Wow, excellent suggestion, that was the problem. I tried from outside the LAN and it works fine. Thanks!
You're welcome.

---

