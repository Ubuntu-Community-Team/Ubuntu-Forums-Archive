---
title: "How do I use server as a router and traffic monitor"
date: 2012-09-20
forum: Networking &amp; Wireless
---

### Post by cackles on 2012-09-20
I just need some help to get going here (until I ask again). I want to pass all my traffic from a switch through my server to a) control it and b) monitor it.

Why? A ten year old that I either have to ban from the net or help because she is her own worst enemy :P

I dont want DHCP but I do want (NEED!) to be able to monitor visited addresses and ban her MAC from sites and such.

I did have a plan for this day coming, but that was like 10 years ago and its well out of date.

---

### Post by Rokel on 2012-09-20
Do you really need it to be completely physically between the client and internet? Like an IP router?

It is a lot easier to setup normal networking for this server like it is another laptop in the house (preferably with fixed IP) and setup your daughters laptop to use that ip address as a HTTP proxy. 

As proxy software there is of course squid with tons of logging and config possibilities, I don't now about frontends and nice graphical monitor for this one but there should be plenty.

You could delete DNS servers and default gateway from her machine. Or make set the server as default gateway just for her.

If you are more thinking in a fully physically seperated and controlled network it becomes quite advanced networking (iptables (to block and do NAT), 2 network cards, routing etc.), use  wireshark for monitoring and make sure this server is powerful and fast to do this.

May I also remind you this is a very hard battle on the technical level, those kids learn each other to use webbased proxies or go to chat sites you would not recognize as dangerous.

Twitter, facebook, yahoo, gmail/chat is encrypted (SSL/HTTPS) you don't want to go into SSL re-encryption setups. Black or whitelisting is hopeless with all websites now using each others api's. 

Maybe you should indeed monitor, but also talk to her about fake profiles, pretenders, bullying, blackmailing, webcam recording, money stuff, adult stuff, malicious software, downloading, uploading, sharing personal data, posting here whereabouts, twittering about being on holiday or new expensive items(attracting burglars), the internet being an eternal archive and so on.

---

### Post by Rokel on 2012-09-20
Another idea: 

Instead of a proxy server or IP router give her a (VNC) remote desktop to the server, so you can tightly control what programs she runs and installs and you can see (or record/snapshot frequently) all desktop activity. 

It also prevents you from reading complex traffic data back in to context like how long did she spend on school stuff and nicely ignoring chat messages or pages in the background that are refreshing and causing a lot of traffic data.

---

### Post by cackles on 2012-10-04
Thanks, I'll have a look at the tools and stuff you suggested.

I have a Ubuntu server ATM, Im going to be upgrading it to a dual Xeon with 32GB RAM in the future, probably around Christmas.

I became bored with modding and OCing years ago so what Im going to do is build a new gaming machine after Christmas and put my secondary and tertiary machines as well as the server into a rackmount. Shoulda done it years ago TBH.

The server will have 2 onboard 1GB NIC and I will add another two 2 x 1GB NICs giving it 6 x 1GB ports and add my two wireless N routers that also have 4 ports (giving me three a piece in this case) and one will go downstairs and one to the first floor. I will also probably add one into my shed too when its built, since it will really be my lab.

That will leave only three empty ports in total. Just for fun I have a 5 port 1GB switch too just in case.

Complicated shouldnt be an issue, I just need to know what Im looking for. The idea is to get all the kids machines (I have three, oldest is ten) running through it.

---

