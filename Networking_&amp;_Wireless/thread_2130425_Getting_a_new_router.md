---
title: "Getting a new router"
date: 2013-03-29
forum: Networking &amp; Wireless
---

### Post by hakermania on 2013-03-29
Hello there.

I am looking into buying a new router.

I am staying at a university building at the campus and I am being provided with a LAN internet connection (I do NOT have a phone and I am not aware of how the whole connection thingy is set up). I am not getting any local IP, I am directly connected to the outside world (I am not behind a router, something I trust to be kind of dangerous) and ifconfig confirms my sayings.

Now, I am planning into buying a router because I like the wireless connection (I have a laptop and a smartphone), but, I don't need a router with an entry for a phone line, as I don't have one. I am a total noob as to what to buy and if it will work, but, what I need is to "divide" my external IP to local IPs for my mobile phone and my laptop. So, it's basically a router with an entry for a LAN that can share it via wireless to multiple devices. Also, it would be nice to have a LAN exit as well, so as to plug my Raspberry Pi there.

What do I need to buy? Will a classical router do the job or there are some issues that I should be aware of?

Thanks for any answers.

---

### Post by hakermania on 2013-03-30
Boing!

---

### Post by ahallubuntu on 2013-03-30
~

---

### Post by kurt18947 on 2013-03-30
I'm no expert but it seems about any wireless router should do what you need. Typical 'consumer' routers have a WAN port where you'd plug your ethernet cable in and 4 lan ports plus wireless.  If you want to experiment with capabilities beyond basic, you could look for a router that will run one of the 3rd party firmwares like DD-WRT, OpenWRT, Tomato or similar.  In the U.S. it's pretty easy to find a Linksys WRT-54G router available used pretty cheap.  If a Linksys or other manufacturer's model will support your chosen 3rd party firmware(be careful, there are a lot of different models that look alike), you can get capabilities similar to professional grade routers pretty inexpensively.  For new, it seems like Netgear & Asus get pretty positive reviews.  I get the impression that Cisco buying Linksys didn't make Linksys better but my Linksys routers are pre-Cisco so I can't say about new.

---

### Post by hakermania on 2013-04-01
Thanks for your answers! I think I will go buy a regular router, but what about Ip Sharers? Will they do the job?

---

### Post by gordintoronto on 2013-04-01
I use a TP-Link WR642G which does exactly what you want. There are many, many similar routers, such as 
[http://www.newegg.ca/Product/Product.aspx?Item=N82E16833166064](http://www.newegg.ca/Product/Product.aspx?Item=N82E16833166064)

I'm not a shill for Newegg, but it's a good site for basic research.

---

### Post by hakermania on 2013-04-09
I got also a TP-Link router just now, and it seems that it has 1 ADSL port and 4 LAN ones.

The product you're pointing at doesn't have an ADSL port... If I connect my ethernet cable to any of these 4 ports, it just tries to connect to the corresponding "PC", but it isn't a "PC", it's where the internet connection comes from...

So, @ahallubuntu, @kurt18947, no, not every basic modem works with what I want. See attachment for what I got with a 30 euros TP-Link router... I guess I'll go change it :)

@gordintoronto Thanks for the suggestion, do you know the difference (in name) of modems that have an ADSL port and the ones that have an Ethernet port? How should I search/ask for them?

---

### Post by gordintoronto on 2013-04-09
A "router" has ethernet in and out. A "router plus modem" has a DSL (ADSL?) port in, and Ethernet ports out. Plus, either one might have wireless as well.

It appears that you got the second one, when you needed the first one.

---

