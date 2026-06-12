---
title: "Wireless connected, but no internet?"
date: 2009-12-22
forum: Networking &amp; Wireless
---

### Post by QwUo173Hy on 2009-12-22
I have a Broadcom Corporation BCM4312 802.11b/g wireless card on my (mothers) Dell laptop.

I can connect to the wireless router and even to the internet - but sometimes I can't. The browser just says 'resolving host' and eventually says it can't find the page or server.

Direct ethernet connection to the ISP router is fine.

(So my setup is LAPTOP -> Wireless router -> ISP router)

I thought it might be a DNS problem but no matter what settings I use I still can't get a page. I can get the wireless routers configuration page though. I'm connecting using WEP and I tried both WPA(TKIP) and WPA2(AES).

Can anyone tell me what to try next?

---

### Post by LowSky on 2009-12-22
If it works sometimes and sometimes doesn't I would think its the signal from the router, change the frequency channel. Most use 6 as default, If you have a bunch of neighbors using wifi, it can mess things up. Change the channel and it might be fixed.

or try this if you keep getting "resolving host" issues in Firefox

Delete the stored Cache under Advanced Tab in options

if that doesn't work  in the browser address bar type
[about:config]("about:config") click yes saying you will  be careful

find _Network.DNS.DisableIPv6_ change it to **True**

that should do it.

---

### Post by QwUo173Hy on 2009-12-22
First of all, thank you so much for such a detailed reply.

Since reading your message, I've changed the channel in case it might help the connection loss when it *is* working.

However, at the moment I'm still having problem #2 where I am connected to the router with  100% signal, but can't get a webpage.

I've tried using IP addresses in case it might be a DNS problem, but it seems it isn't as I still can't get a page. I've deleted the Firefox cache and I also changed the IPv6 disable setting to True.


Unfortunately, I still can't get online without connecting directly with the ethernet cable.

---

### Post by LowSky on 2009-12-22
System > Administration > Network tools
see attached image, you should have an option for wlan under Network Device.

If you dont see an IP address then you are not connecting

---

### Post by QwUo173Hy on 2009-12-25
Thanks LowSky - I just have options for: lo, eth0 and eth2.

But I have wireless working at present, so I'm confused!

---

### Post by Iowan on 2009-12-25
You can check **lshw -C network** (from a terminal) to see which interface is which hardware device - my laptop uses eth0 for ethernet, eth1 for wireless.

---

### Post by QwUo173Hy on 2009-12-25
I managed to get two more laptops to try out on the network - another Ubuntu and a Windows 7. The problem is the same on both and I'm certain that the problem is with the router now. I disconnected power for a few minutes and when I plugged it back in everyone got their connections back.

Interestingly, the Windows 7 wifi connection icon notified me that I had a connection, but no internet access. That's quite useful in this scenario.

Should I make a bug or blueprint out of this? Or just brainstorm it?

---

