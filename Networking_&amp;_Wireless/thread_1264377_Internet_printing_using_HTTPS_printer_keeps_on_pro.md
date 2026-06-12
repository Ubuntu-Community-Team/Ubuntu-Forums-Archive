---
title: "Internet printing using HTTPS: printer keeps on processing but does not print"
date: 2009-09-12
forum: Networking &amp; Wireless
---

### Post by RudderDuck on 2009-09-12
Hi,

My university uses web print ([http://webprint.tudelft.nl/uk.htm](http://webprint.tudelft.nl/uk.htm)) which enables Internet printing using HTTPS. This works for XP, even from home (see manual for XP at [https://www.tudelft.nl/live/pagina.jsp?id=b3d1caf2-5f01-4e50-93a4-bc3d14e7f8c5&#9001;=en&binary=/doc/Use%20webprint%20with%20Windows%20XP.pdf]("https://www.tudelft.nl/live/pagina.jsp?id=b3d1caf2-5f01-4e50-93a4-bc3d14e7f8c5&lang=en&binary=/doc/Use%20webprint%20with%20Windows%20XP.pdf")). They also have a manual for Linux but this is written for pcs on the university domain. My computer is a netbook which is not registered on the university domain.

In short, I should be able to use the printers fom any location, as long as I have a working internet connection as I have tested this and works for XP. However, I cannot get this to work on Ubuntu Netbook Remix.

There is site that explains what to do ([https://wiki.ubuntu.com/NlTUDelft](https://wiki.ubuntu.com/NlTUDelft) in Dutch) although the instructions are meant for the more seasoned Ubuntu user. This site points to another site with detailed instructions on how to get internet printing with HTTPS to work: [http://www.cse.ust.hk/~lkmpoon/linux/ubuntu-hkust.html]("http://www.cse.ust.hk/%7Elkmpoon/linux/ubuntu-hkust.html"). 

I followed these instructions to the letter and although I can now successfully connect to the webprint printers it does not finish print jobs. It stays on "Processing - Waiting for job to complete", which never happens.

The output of CUPS, after setting the output level to debug is below.

Although it has some on "authentication data" I doubt that that is the problem as, unless I am mistaken, it is more related to the web interface of CUPS. The part where it requests my username (ruud) it is successful.

There is also a manual for MacOS ([http://studiolab.io.tudelft.nl/static/gems/mactudelft/Webprint.pdf](http://studiolab.io.tudelft.nl/static/gems/mactudelft/Webprint.pdf)) which I looked into but this did not differ much from what I did.

Hopefully one of you can give me some pointers on how to solve or diagnose the exact problem as I am rather stuck now as the debug output does not really show any problem.

(All manuals can be found at: [http://www.tudelft.nl/live/pagina.jsp?id=b3d1caf2-5f01-4e50-93a4-bc3d14e7f8c5&#9001;=en]("http://www.tudelft.nl/live/pagina.jsp?id=b3d1caf2-5f01-4e50-93a4-bc3d14e7f8c5&lang=en"))

Thanks!

```
D [12/Sep/2009:09:40:40 +0200] cupsdCloseClient: 42
D [12/Sep/2009:09:40:40 +0200] cupsdReadClient: 38 POST / HTTP/1.1
D [12/Sep/2009:09:40:40 +0200] cupsdAuthorize: No authentication data provided.
D [12/Sep/2009:09:40:40 +0200] CUPS-Get-Printers
D [12/Sep/2009:09:40:40 +0200] cupsdProcessIPPRequest: 38 status_code=0 (successful-ok)
D [12/Sep/2009:09:40:40 +0200] cupsdReadClient: 38 POST / HTTP/1.1
D [12/Sep/2009:09:40:40 +0200] cupsdAuthorize: No authentication data provided.
D [12/Sep/2009:09:40:40 +0200] CUPS-Get-Classes
D [12/Sep/2009:09:40:40 +0200] cupsdProcessIPPRequest: 38 status_code=0 (successful-ok)
D [12/Sep/2009:09:40:42 +0200] cupsdAcceptClient: 41 from localhost (Domain)
D [12/Sep/2009:09:40:42 +0200] cupsdReadClient: 41 POST / HTTP/1.1
D [12/Sep/2009:09:40:42 +0200] cupsdAuthorize: No authentication data provided.
D [12/Sep/2009:09:40:42 +0200] Create-Printer-Subscription /
D [12/Sep/2009:09:40:42 +0200] cupsdCreateSubscription(con=0xb90bcd40(41), uri="/")
D [12/Sep/2009:09:40:42 +0200] pullmethod="ippget"
D [12/Sep/2009:09:40:42 +0200] notify-lease-duration=86400
D [12/Sep/2009:09:40:42 +0200] notify-time-interval=0
D [12/Sep/2009:09:40:42 +0200] cupsdAddSubscription(mask=798f, dest=(nil)(), job=(nil)(0), uri="(null)")
D [12/Sep/2009:09:40:42 +0200] Added subscription 100 for server
I [12/Sep/2009:09:40:42 +0200] Saving subscriptions.conf...
D [12/Sep/2009:09:40:42 +0200] cupsdProcessIPPRequest: 41 status_code=0 (successful-ok)
D [12/Sep/2009:09:40:42 +0200] cupsdReadClient: 41 POST / HTTP/1.1
D [12/Sep/2009:09:40:42 +0200] cupsdAuthorize: No authentication data provided.
D [12/Sep/2009:09:40:42 +0200] CUPS-Get-Printers
D [12/Sep/2009:09:40:42 +0200] cupsdProcessIPPRequest: 41 status_code=0 (successful-ok)
D [12/Sep/2009:09:40:42 +0200] cupsdReadClient: 41 POST / HTTP/1.1
D [12/Sep/2009:09:40:42 +0200] cupsdAuthorize: No authentication data provided.
D [12/Sep/2009:09:40:42 +0200] CUPS-Get-Printers
D [12/Sep/2009:09:40:42 +0200] cupsdProcessIPPRequest: 41 status_code=0 (successful-ok)
D [12/Sep/2009:09:40:42 +0200] cupsdCloseClient: 41
D [12/Sep/2009:09:40:42 +0200] cupsdAcceptClient: 41 from localhost (Domain)
D [12/Sep/2009:09:40:42 +0200] cupsdReadClient: 41 POST / HTTP/1.1
D [12/Sep/2009:09:40:42 +0200] cupsdAuthorize: No authentication data provided.
D [12/Sep/2009:09:40:42 +0200] Get-Jobs ipp://localhost/printers/
D [12/Sep/2009:09:40:42 +0200] cupsdProcessIPPRequest: 41 status_code=0 (successful-ok)
D [12/Sep/2009:09:40:42 +0200] cupsdAcceptClient: 42 from localhost (Domain)
D [12/Sep/2009:09:40:42 +0200] cupsdReadClient: 42 POST / HTTP/1.1
D [12/Sep/2009:09:40:42 +0200] cupsdAuthorize: No authentication data provided.
D [12/Sep/2009:09:40:42 +0200] Get-Printer-Attributes ipp://ruud-netbook:631/printers/bleh
D [12/Sep/2009:09:40:42 +0200] cupsdProcessIPPRequest: 42 status_code=0 (successful-ok)
D [12/Sep/2009:09:40:42 +0200] cupsdCloseClient: 42
D [12/Sep/2009:09:40:42 +0200] cupsdCloseClient: 41
D [12/Sep/2009:09:40:42 +0200] cupsdAcceptClient: 41 from localhost (Domain)
D [12/Sep/2009:09:40:42 +0200] cupsdReadClient: 41 POST / HTTP/1.1
D [12/Sep/2009:09:40:42 +0200] cupsdAuthorize: No authentication data provided.
D [12/Sep/2009:09:40:42 +0200] Get-Jobs ipp://localhost/printers/
D [12/Sep/2009:09:40:42 +0200] cupsdProcessIPPRequest: 41 status_code=0 (successful-ok)
D [12/Sep/2009:09:40:42 +0200] cupsdCloseClient: 41
D [12/Sep/2009:09:40:43 +0200] cupsdAcceptClient: 41 from localhost (Domain)
D [12/Sep/2009:09:40:43 +0200] cupsdReadClient: 41 POST / HTTP/1.1
D [12/Sep/2009:09:40:43 +0200] cupsdAuthorize: No authentication data provided.
D [12/Sep/2009:09:40:43 +0200] Get-Notifications /
D [12/Sep/2009:09:40:43 +0200] cupsdIsAuthorized: requesting-user-name="ruud"
D [12/Sep/2009:09:40:43 +0200] cupsdProcessIPPRequest: 41 status_code=0 (successful-ok)
D [12/Sep/2009:09:40:43 +0200] cupsdCloseClient: 41
D [12/Sep/2009:09:40:49 +0200] cupsdAcceptClient: 41 from localhost (Domain)
D [12/Sep/2009:09:40:49 +0200] cupsdReadClient: 41 POST / HTTP/1.1
D [12/Sep/2009:09:40:49 +0200] cupsdAuthorize: No authentication data provided.
D [12/Sep/2009:09:40:49 +0200] Cancel-Subscription /
D [12/Sep/2009:09:40:49 +0200] cupsdIsAuthorized: requesting-user-name="ruud"
I [12/Sep/2009:09:40:49 +0200] Saving subscriptions.conf...
D [12/Sep/2009:09:40:49 +0200] cupsdProcessIPPRequest: 41 status_code=0 (successful-ok)
D [12/Sep/2009:09:40:49 +0200] cupsdCloseClient: 41
I [12/Sep/2009:09:41:11 +0200] Subscription 48 has expired...
I [12/Sep/2009:09:41:11 +0200] Saving subscriptions.conf...
D [12/Sep/2009:09:41:23 +0200] cupsdNetIFUpdate: "lo" = localhost:631
D [12/Sep/2009:09:41:23 +0200] cupsdNetIFUpdate: "wlan0" = 192.168.178.37:631
D [12/Sep/2009:09:41:23 +0200] cupsdNetIFUpdate: "lo" = localhost:631
D [12/Sep/2009:09:41:23 +0200] cupsdNetIFUpdate: "wlan0" = fe80::226:5eff:fe23:63f5%wlan0:631
D [12/Sep/2009:09:41:23 +0200] Report: clients=1
D [12/Sep/2009:09:41:23 +0200] Report: jobs=16
D [12/Sep/2009:09:41:23 +0200] Report: jobs-active=1
D [12/Sep/2009:09:41:23 +0200] Report: printers=6
D [12/Sep/2009:09:41:23 +0200] Report: printers-implicit=0
D [12/Sep/2009:09:41:23 +0200] Report: stringpool-string-count=2731
D [12/Sep/2009:09:41:23 +0200] Report: stringpool-alloc-bytes=11848
D [12/Sep/2009:09:41:23 +0200] Report: stringpool-total-bytes=54536
```

---

