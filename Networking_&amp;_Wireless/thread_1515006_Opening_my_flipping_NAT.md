---
title: "Opening my flipping NAT"
date: 2010-06-21
forum: Networking &amp; Wireless
---

### Post by Windows Nerd on 2010-06-21
Hey all,

I have an Xbox. It works great and has worked fine to connect to XBOX Live. Since I got a new router/modem thing (Its a combination one: Gigaset SE567), my NAT has been set to strict (it was Open NAT a while ago before with the old router). I want it to be set to OPEN NAT, so that I can play with a couple of my buddies. 

So, I logged into the router (set at IP adress 198.162.1.254) and set the DMZ settings to allow the IP adress 192.168.1.50. I then went into the Xbox and set it's settings (it is connected by wired, by the way) as:

IP Addr: 192.168.1.50
Subnet Mask: 255.255.255.0
Gateway: 192.168.1.254
DNS server: 192.168.1.254

I went and tested the connection. It worked, it could connect fine to Xbox with manual settings. Except that the NAT was still flipping STRICT!

I tried restarting my modem (Unplugging it, wait 30 sec, plugging it back in), enabling the UPnP, all with no avail.

Any help? I would really like to play with ALL my buddies!

Scott

After some extensive Googling, some people have said that port-fowarding was how you solve it. I went into my router, and fowarded the following ports to the Xbox's now static IP:

80 TCP
53 TCP
3074 TCP
53 UDP
88 UDP
3074 UDP

These are the ports many guides 'round the net said to open. It didn't help. 

Well, still no views yet... :(.

---

### Post by Windows Nerd on 2010-06-21
I solved it - I enabled UPnP on a broader setting, thread closed.

---

