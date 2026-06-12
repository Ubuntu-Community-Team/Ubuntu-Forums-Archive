---
title: "Cameo/Excel WLG-2002 AP default IP?"
date: 2009-01-14
forum: Networking &amp; Wireless
---

### Post by VictorR on 2009-01-14
Recently bought cheap WLG-2002 Wireless Access Point without documentation, just to provide WiFi access to internet for Asus EEE-PC. Connected it to an ADSL router, pressed Reset and instantly got unsecured wireless network with SSID "default". But when I tried to open its Web-based configuration page, I realized I cannot find its IP. I thought it might be visible in:
1. ADSL router DHCP table
2. "ip address show" command
3. "arp -a" command
4. "nmap 192.168.0.0/16" command
5. IP scan utility, when connected to XP computer
but it did not appeared anywhere (the computers, connected wirelessly, are visible and can access both the Internet and LAN).

Does anybody know the trick how to get to its config interface?

Thanks in advance for any ideas.

---

### Post by chex_m8 on 2009-01-14
most routers use 192.168.0.1 or 192.168.1.1 ,something in this range.
if it's connected to your dsl modem it should be in the web config page of that router.
i guess you could connect with a wire once just to get an ip address and find out the default gateway.

---

### Post by VictorR on 2009-01-15
Thank you for your reply.
I hope someone has a manual for this Access Point and can tell me how to get access to its config page exactly.

I tried most of the IP addresses and ways to connect I found in the Internet, but nothing worked. There should be some trick with this particular AP.

---

### Post by VictorR on 2009-01-22
Finally got it. In hope that it could be useful for someone.
The default settings for Cameo/Excel WLG-2002 Wireless Access Point are:
IP : 192.168.1.100
username and password: empty (it does not asked for them).
The problem is that the above IP is invisible everywhere, it does not reply on ping, nor it shown in any commands, displaying presented devices in the network.
I could access the access point using Windows XP laptop, so I explain the main idea, how to do it.
1. configure your network card (in your computer) to assign the IP address manually, like this:
```
IP : 192.168.1.199
Mask: 255.255.255.0
```
2. connect the access point to your computer directly
3. turn AP on
4. open the browser and type
```
http://192.168.1.100
```
in the address line. Make sure Javascript is allowed for this address.
Then configure the access point as usually.

---

