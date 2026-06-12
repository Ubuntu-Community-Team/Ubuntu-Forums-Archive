---
title: "DC ++ active mode?"
date: 2010-07-30
forum: Networking &amp; Wireless
---

### Post by scania_gti on 2010-07-30
Try some DC++ clients - free dc, linuc dc, eiskalt dc, but no one work in active mode :(
Read hundred forums, but not find solution - i don't have "eth1", only "eth0". (My internet is DHCP, and all people have the same IP).
Open port from firewall, port is "LISTENING".
Where to search "active mode"? :D

---

### Post by marc.verwerft on 2010-07-30
I have never used DC++ but did some search using my dear friend GOOGLE :D

Start by reading [http://dcplusplus.sourceforge.net/webhelp/get_started.html](http://dcplusplus.sourceforge.net/webhelp/get_started.html) under the heading 'Setting up your connection' - first thing you need to figure out is what active mode is available to you.

> i don't have "eth1", only "eth0"

The name eth0 is formed by eth + number -> eth is for ethernet connection, the number is a sequencenumber for the cards/ports available on your PC. If you have 2 ports, you'll have eth0 and eth1, if you have eight ports, they'll be named eth0 to eth7.

> Open port from firewall, port is "LISTENING".
A port is listening means that it is ready to accept connections. E.g. when you have a webserver running on port 80, then that port will be in 'listening' mode for clients.

HTH

Marc

---

### Post by scania_gti on 2010-07-30
Thanks :)
eth0 - name of a ethernet card, not a port; only one card im my pc :) Any router or other devices, just cable and ethernet card :)
Firestarter wizard can open port, but must have eth0 and eth1, with same device wizard not work.
Strange, if port LISTEN is alllready OPEN, then where peoblem with active mode? :(

[URL="http://www.dslreports.com/faq/6517"]"In passive connection mode, DC++ will only make outbound connections to other  users"
" active mode on DC++ will make inbound and outbound connections  to other users"[/URL]

Problem with inbound connections?
And [online port check]("http://www.canyouseeme.org/") not seeing my "open ports" :D

Thanks for the links, i never see before that page, because in winxp i easily set active mode with few dc++ clients. In winxp i told to firewall to unblock program; in linux i'm still search, where is that option...

---

### Post by scania_gti on 2010-08-02
With network-config set static IP. Enable NAT.
With Firestarter open almost all connections and services.
Try lot ports number in eiskaltdc++ and...
and...
still pasive user :D
Second problem, or first problem - i now about ports NAT's and other similar stuff - i now allmost nothing :D
I believe, other "yesterday windows - tooday linux" users have similar problems :)
And similar favorites programs - DC++ :)
How to check what is wrong?

---

### Post by marc.verwerft on 2010-08-02
Setting a static IP will not solve your problem.

First of all figure out if you are directly connected to internet or not according to [http://dcplusplus.sourceforge.net/webhelp/get_started.html](http://dcplusplus.sourceforge.net/webhelp/get_started.html)- then follow the active mode setup FAQ : [http://dcplusplus.sourceforge.net/webhelp/faq_activemode.html](http://dcplusplus.sourceforge.net/webhelp/faq_activemode.html)

Some things you might not know about linux/Ubuntu:
- Ubuntu doesn't have a personal firewall activated by default
- ports under 1024 require special privileges - you need to be root to start a daemon that listens on those ports.
- NAT stands for 'network address translation' - basically only a router with 2 ethernet connections does this. One is connected to the home lan, the other to the internet. Read more on this on wikipedia: [http://en.wikipedia.org/wiki/Network_address_translation](http://en.wikipedia.org/wiki/Network_address_translation)
- since you could set up an active mode for windows, my guess is that you do not need to configure your router anymore. 

> I believe, other "yesterday windows - tooday linux" users have similar problems
And I believe that those who persevere with linux eventually will learn a lot more about computers, networks and protocols ;-)

Regards,

Marc.

---

### Post by scania_gti on 2010-08-02
Thank, marc.verwerft :)
Setting to static IP not work, as you say :)
and i read many many „how to set active mode“ or „firewall enabling“ :)
Maybe my internet provider block some services?
How to check/bench my internet connection/provider/services?
Maybe my sweet ubuntu work perfect, but evil provider kill my hope? :D

Step by step i learn about computers; steps too hard for my, but ubuntu still like more, than mswindows :D
windows - is like a 30-age car: fixing every day, but better, than walk :)

---

### Post by marc.verwerft on 2010-08-02
I started up synaptic (Ubuntu's package manager) selected linuxdcpp and installed it.

It immediately connected to a public hub and I could see that the active mode in the preferences tab was selected by default.

My computer is connected to the internet using a wireless router with no special settings. Maybe you can give it a try also?

Regards,

Marc.

---

### Post by scania_gti on 2010-08-02
Not too fast :)
Problem is hide, until you try find some files or get filelist ("browse files") from passive user.
Yes, all dc programs use "active" by default. If "active" not work - anyvay you get connected to hublist or hubs; or get filelist from active users; but real power of dc++ is in active mode, when you can download from all users.
With popular files - top pop music or films - no problem; but when try to find something old fashion or exactly what you want... ;)

Thanks, Mark, for advance :) I'm surprised - you install dc only for our talk?! :)

I think, maybe, when next time i'll pay for the net, i'll go in office and just ask provider computerhead :)
When you came with money, people is more lively :D

edit: i forget to add link to [online providers test]("http://www.measurementlab.net/measurement-lab-tools")  i try glasnost test, but nothing happened. With no results. :D

---

