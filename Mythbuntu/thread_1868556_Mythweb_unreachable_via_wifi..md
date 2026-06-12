---
title: "Mythweb unreachable via wifi."
date: 2011-10-24
forum: Mythbuntu
---

### Post by PhilWig on 2011-10-24
I'm having problems connecting an Asus 1011PX netbook running windows 7 to Mythweb but only if I connect it via wifi.

My myth box is an FE+BE on an Asus M3N78-EM mobo.  The 'production' service (frozen updates for higher WAF) is 9.04 though I have identical symptoms with 11.04 with latest upgrades on the same hardware.

The other systems in the house (XP, Ubuntu, directly or wifi connected) all work fine.

The Netbook works if running  'Expressgate' (an Asus packaged system with Linux + Chrome) via wifi,or with Windows 7 + Firefox 7.0.1 or IE9 and a wired connection.

However, the same netbook and same software will not connect if wifi linked.   It will just 'stick' after password submission but all other addresses seem okay.  In particular, I can login to both my Thompson router and my ICY NAS on the house network.

The network consists of a 4 port ADSL wifi router.  The myth box is connected to it via 'ether over power', the others are plugged in directly or are wifi connected.

I thought that the Apache logs would be illuminating.  /var/log/apache2/access.log shows this for the netbook with wired connection:

> 
192.168.1.68 - - [24/Oct/2011:07:27:45 +0100] "GET /mythweb HTTP/1.1" 401 369 "-" "Mozilla/5.0 (Windows NT 6.1; rv:7.0.1) Gecko/20100101 Firefox/7.0.1"
192.168.1.68 - phil [24/Oct/2011:07:27:49 +0100] "GET /mythweb HTTP/1.1" 301 273 "-" "Mozilla/5.0 (Windows NT 6.1; rv:7.0.1) Gecko/20100101 Firefox/7.0.1"
192.168.1.68 - - [24/Oct/2011:07:27:49 +0100] "GET /mythweb/ HTTP/1.1" 200 2302 "-" "Mozilla/5.0 (Windows NT 6.1; rv:7.0.1) Gecko/20100101 Firefox/7.0.1"
192.168.1.68 - phil [24/Oct/2011:07:27:49 +0100] "GET /mythweb/js/prototype.js HTTP/1.1" 304 - "http://192.168.1.67/mythweb/" "Mozilla/5.0 (Windows NT 6.1; rv:7.0.1) Gecko/20100101 Firefox/7.0.1"
192.168.1.68 - phil [24/Oct/2011:07:27:49 +0100] "GET /mythweb/js/prototip/prototip.js HTTP/1.1" 304 - "http://192.168.1.67/mythweb/" "Mozilla/5.0 (Windows NT 6.1; rv:7.0.1) Gecko/20100101 Firefox/7.0.1"
192.168.1.68 - phil [24/Oct/2011:07:27:49 +0100] "GET /mythweb/js/prototip/prototip.css HTTP/1.1" 304 - "http://192.168.1.67/mythweb/" "Mozilla/5.0 (Windows NT 6.1; rv:7.0.1) Gecko/20100101 Firefox/7.0.1"
192.168.1.68 - phil [24/Oct/2011:07:27:49 +0100] "GET /mythweb/js/utils.js HTTP/1.1" 304 - "http://192.168.1.67/mythweb/" "Mozilla/5.0 (Windows NT 6.1; rv:7.0.1) Gecko/20100101 Firefox/7.0.1"
192.168.1.68 - phil [24/Oct/2011:07:27:49 +0100] "GET /mythweb/js/AC_OETags.js HTTP/1.1" 304 - "http://192.168.1.67/mythweb/" "Mozilla/5.0 (Windows NT 6.1; rv:7.0.1) Gecko/20100101 Firefox/7.0.1"
192.168.1.68 - phil [24/Oct/2011:07:27:49 +0100] "GET /mythweb/skins/default//style.css HTTP/1.1" 304 - "http://192.168.1.67/mythweb/" "Mozilla/5.0 (Windows NT 6.1; rv:7.0.1) Gecko/20100101 Firefox/7.0.1"
192.168.1.68 - phil [24/Oct/2011:07:27:49 +0100] "GET /mythweb/skins/default//header.css HTTP/1.1" 304 - "http://192.168.1.67/mythweb/" "Mozilla/5.0 (Windows NT 6.1; rv:7.0.1) Gecko/20100101 Firefox/7.0.1"
192.168.1.68 - phil [24/Oct/2011:07:27:49 +0100] "GET /mythweb/skins/default//menus.css HTTP/1.1" 304 - "http://192.168.1.67/mythweb/" "Mozilla/5.0 (Windows NT 6.1; rv:7.0.1) Gecko/20100101 Firefox/7.0.1"
192.168.1.68 - phil [24/Oct/2011:07:27:49 +0100] "GET /mythweb/skins/default//programming.css HTTP/1.1" 304 - "http://192.168.1.67/mythweb/" "Mozilla/5.0 (Windows NT 6.1; rv:7.0.1) Gecko/20100101 Firefox/7.0.1"
[... etc ...]


When wifi connected:
> 
192.168.1.70 - - [24/Oct/2011:07:24:14 +0100] "GET /mythweb HTTP/1.1" 401 369 "-" "Mozilla/5.0 (Windows NT 6.1; rv:7.0.1) Gecko/20100101 Firefox/7.0.1"
192.168.1.70 - phil [24/Oct/2011:07:24:34 +0100] "GET /mythweb HTTP/1.1" 301 273 "-" "Mozilla/5.0 (Windows NT 6.1; rv:7.0.1) Gecko/20100101 Firefox/7.0.1"
192.168.1.70 - - [24/Oct/2011:07:24:34 +0100] "GET /mythweb/ HTTP/1.1" 200 2301 "-" "Mozilla/5.0 (Windows NT 6.1; rv:7.0.1) Gecko/20100101 Firefox/7.0.1"

....  and no more.

The Apache error log is empty at that time, and the backend log seems quite innocuous:
> 
2011-10-24 07:24:34.677 MainServer::HandleAnnounce Monitor
2011-10-24 07:24:35.092 adding: myth as a client (events: 0)
2011-10-24 07:25:09.342 Reschedule requested for id -1.


Can anyone shed light on this oddity?  I seem to have exonerated every component and I just cannot find any details of Apache logs.

Phil

---

### Post by PhilWig on 2011-10-25
The problem is now fixed.  It was an MTU issue on the wifi interface on the netbook.  The clue came from:

[http://www.richard-slater.co.uk/archives/2009/10/23/change-your-mtu-under-vista-or-windows-7/](http://www.richard-slater.co.uk/archives/2009/10/23/change-your-mtu-under-vista-or-windows-7/)

Reducing MTU for the W7 wifi interface to 1400 fixed it.

Sorry this was off topic and thanks for reading it.

Phil

---

