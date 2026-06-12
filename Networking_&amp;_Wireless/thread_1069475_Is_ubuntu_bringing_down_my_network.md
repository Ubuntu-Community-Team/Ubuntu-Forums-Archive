---
title: "Is ubuntu bringing down my network"
date: 2009-02-14
forum: Networking &amp; Wireless
---

### Post by whaledawg on 2009-02-14
So I've got an Airlink 101 wireless card and I have the windows drivers installed with ndis wrapper. I connect to a WRT54GL Linksys router with the original firmware.

It works fine most of the time, but every once in a while the wireless network seems to hose up and neither I, nor anyone else, can connect. But when I boot into windows it always seems to connect right away and tonight someone else who was trying to connect could as well. 

I know that reseting the router and cable modem also solve this problem, but since it's in a room that belongs to a roomate that isn't always an option.

By the way, when I say it hoses up on me in Ubuntu I mean I can only connect to the network 1 out of 3 times and when I do I can get outside(I try to ping google) for about 10 seconds and then I can no longer reach outside hosts.

---

### Post by cariboo on 2009-02-14
Have you tried restarting networking? Open an Applications-->Accessories-->Termianl and type:

```
sudo /etc/init.d/networking restart
```

I would also check to see that no one on the network is assigned the same ip address as the one you are using.

Jim

---

### Post by superprash2003 on 2009-02-14
are you using static ips or are you getting an ip via DHCP?

---

