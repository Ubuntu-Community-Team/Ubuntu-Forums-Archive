---
title: "planning on getting a AT&amp;T wifi plan, but don't know how to configure the modem"
date: 2009-04-08
forum: Networking &amp; Wireless
---

### Post by shiningkenmonster on 2009-04-08
planning on getting a AT&T wifi plan, but don't know how to configure the modem

hey, so i want to purchase an AT&T wifi plan. (supposedly its a dsl plan, but the Gateway modem converts the signals into wifi signals) I will probably get the 3.0 mbps plan.

AT&T will give me a CD that works on a Windows XP/Vista and a Mac OS X computer. The CD is suppose help me configure the modem for me.

I am running on Dell's custom Ubuntu 8.04. on a Dell mini 9 netbook. Supposedly this CD won't work because of the OS i am using (Ubuntu). Either way, I don't even have a CD-ROM/DVD-ROM drive.

The modem that I am getting from the website is a:
2Wire DSL Gateway Model 2701HG-B

[http://store.att.com/catalog/productdetails.asp?ProductId=1000-401047-000&CategoryId=catMRG&show=Features]("http://store.att.com/catalog/productdetails.asp?ProductId=1000-401047-000&CategoryId=catMRG&show=Features")

AT&T told me I am suppose to configure the Gateway modem myself. Because they don't support linux home users.

kind of ironic that AT&T made UNIX in the past, but they can't help their home users.

I tried to google it but i founded no answers. can someone help me?

---

### Post by chili555 on 2009-04-09
I don't have this exact model, but I have an AT&T wireless modem/router. I had no trouble connecting to it with a wired ethernet connection by opening a browser and entering [http://192.168.1.254](http://192.168.1.254). Your access IP may be different; check the manual.

All I needed to do was plug in the username and password, which AT&T will assign and tell you, and then tell the device to connect; that is, grab an IP address from the AT&T network.

I then set up encryption (WEP, WPA etc.), saved all settings and restarted the device. Everything works fine. In fact, I can't even imagine what the CD might do for me that I couldn't do faster and easier myself.

---

