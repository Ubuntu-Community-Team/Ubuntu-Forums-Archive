---
title: "Network bandwidth is consumed when I launch Transmittion"
date: 2012-01-05
forum: Networking &amp; Wireless
---

### Post by Ifaistos on 2012-01-05
Hello everyone and Happy New Year :-)

I am having the following problem with transmition.  After a few seconds or a couple of minutes it consumes my bandwidth.

EVEN WHEN it does not download or upload anything!!

When I try to look into anything else, even a simple page, it seems that my network is down.  As if it completely blocks the port and allows only itself to send or receive.

I don't use all my bandwidth, but even if I did, I would expect that when I used chrome or any other browser to see a page, that it would allow me to at least "sneak" through a request and display a page.  Instead it makes my computer act as if there is no connection at all.

Transmition though has no problem in sending and receiving...

Does anyone have any idea as to what I should do?

Thank you all in advance :-)

---

### Post by TenPlus1 on 2012-01-05
What helped me was changing the port number that Transmission uses (pick at random) and enabling the blocklist:

Click Edit -> Preferences -> Privacy, add the URL below and click Update.

[http://list.iblocklist.com/?list=bt_level1&fileformat=p2p&archiveformat=gz](http://list.iblocklist.com/?list=bt_level1&fileformat=p2p&archiveformat=gz)

also, changing max downloads to 2 helps also...

---

### Post by Ifaistos on 2012-01-05
Hello and thank you for your answer.

I clicked on "change port every time transmittion is started".
I also added the blocklist you suggested.

I couldn't find an option for max. downloads.  Do I have to do it manually?

The problem is that it didn't help :(
Even when I started transmittion and it hadn't started downloading/uploading my connection went down.

I couldn't even reply to this message.

Could there be smt else?

Thanks.

btw.... what is the block list for?  It has 220.000+ rules !!!

---

### Post by Ifaistos on 2012-01-06
bump... :-)

---

### Post by Grenage on 2012-01-06
Most home routers cannot handle many NAT requests - there is some processing overhead involved.  While you may not be transferring much data, you probably have a lot of active connections.

As a test, set your maximum active torrents to 1, then set maximum global connections (or per-torrent connections) to 20.  If that performs well, you can increase the connection count and see where it starts flailing.

In my experience, less is often more; 1 good peer could be as fast as 100.

---

### Post by Ifaistos on 2012-01-06
Thank you for your answer !
It does explain the behavior of the transmition.

I will definitely try that...
Is there a way to set max active torrents, or do I have to do it manually?

btw.. I've set 10 connections per torrent and 30 total...
I will tell you how it goes...

---

### Post by Ifaistos on 2012-01-07
It seems that this was the problem!
I guess I will have to limit that down according to what I want to do, and how much access I want to have to the internet.

One more question to Grenage (or anyone who knows) :  You mentioned that most home routers cannot handle many NAT requests.

Do you have in mind any affordable home routers that could fix this problem?

Thank you in advance.

---

