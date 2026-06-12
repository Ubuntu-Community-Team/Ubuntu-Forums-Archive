---
title: "DI-524 router"
date: 2011-07-25
forum: Networking &amp; Wireless
---

### Post by sokerjunky on 2011-07-25
PC- Emachine T3612
I've done the quick installation through 192.168.0.1 and it said the router is set up. The router is giving out wireless internet but no webpages will load. The WAN settings are set up by the PPPoE. while on the wan settings page i scrolled down all the way to the bottom where it says "Connection Status" and it says disconnected. I hit connect but it just keeps saying connecting but it never does. What do you guys think i should do. If you guys need more info just let me know
Thank you very much in advance. I've been at this for about 3 hours and im beginning to get aggravated haha

---

### Post by JC Cheloven on 2011-07-25
Let's check the whole procedure: you open a browser, type in the adress ```
http://192.168.0.1
``` and the web page living in your router do appear.

Your ISP (your internet company) gave you some parameters to setup the router. among them:
- Protocol. Something like PPPoE 8.35.
- PPP user name. Something like sokerjunky334@thecompanyname
- PPP password. Something like 1122

--> Did you set up all of this? Leaving something as "automatic" may result in a bad option choosen.

Then some other basics: 
- Did you turned on the DHCP server? This makes a difference when setting up the connection in ubuntu.
- Did you try (after configuration) to shutdown both the router and the pc, and restarting?

If the above is done, the last of the basics is:
- Open network manager, click "edit connections" abd see if the "Auto eth0" (or Auto eth1...) connection matches the expected parameters for your router. In particular pay attention to DNS server (your ISP should have give you one, something like 63.23.211.101). In fact it's worth to try disabling the DHCP server at the router, and manually setup the connection in the network manager (at ubuntu), dns included.

If the avobe basics don't solve it, and before starting with ifconfig etc, please try at a terminal:
```
ping 192.168.0.1
```and```
ping www.ubuntu.com
```
Hit CTRL-C to stop the ping command. Tell us that is says.

---

