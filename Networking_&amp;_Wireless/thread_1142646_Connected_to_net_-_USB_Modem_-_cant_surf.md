---
title: "Connected to net - USB Modem - cant surf"
date: 2009-04-29
forum: Networking &amp; Wireless
---

### Post by darkworld on 2009-04-29
Hi

Orange 3G USB mobile Modem, detects device, did setup wizard connects fine, signal strenght shown and states connected etc

Ive just installed the latest Ubuntu, replacing fiesty with fresh install of latest Ubuntu on a dual boot machine - windows XP. The USB modem works ok etc.

Now my issue is, I open firefox and I cant get to any web pages, server not found etc. I used the setup wizard, it asked orange contract or paymonthly.... i pay monthly but its contract so I chose contract... I dont think this is the issue. The device appears to be connected to the service provider orange. Say connected etc.

What else to I have to do? Sorry not that great on this topic.

---

### Post by prshah on 2009-04-29
> **darkworld said:**
> 
Orange 3G USB mobile Modem, detects device, did setup wizard connects fine, signal strenght shown and states connected etc

 I open firefox and I cant get to any web pages, server not found etc.

a) You may not be getting DNS server IPs
b) You may need to enter a proxy server's IP.

To confirm (a); try this when connected```
 ping -c 3 www.google.com
``` It should fail, if your DNS servers are not setup.

If it fails, then try```
ping -c 3 208.67.219.230
```; if you get a reply, then the DNS servers are definitely your problem. In this case, you can manually add the DNS servers (in Windows XP, the "ipconfig /all" command will give you the DNS addresses) or you can use the OpenDNS servers (208.67.220.220 and 208.67.222.222). Check in your connection properties for entries for DNS servers.

As a further step, if this is your problem, can you post the /etc/resolv.conf file (after connecting?)

If this is not your problem, then you need to check if you need to specify a proxy address when using the Internet; possibly ask "Orange" techsupport.

---

### Post by darkworld on 2009-04-29
Thanks for that. It was the DNS for orange contract that was the problem. Orange where quiet helpful and got me some DNS IP's but I also found just switching to another connection orange pay monthly, put the correct server IP's in automatically.

The guy from orange also told me there are several different APN's and you will get different speeds from different ones. here are two to try if anybody on orange is interested. 

> consumerbroadband > internetvpn

---

