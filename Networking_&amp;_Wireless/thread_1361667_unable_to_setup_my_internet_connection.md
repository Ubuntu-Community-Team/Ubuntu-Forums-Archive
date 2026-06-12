---
title: "unable to setup my internet connection"
date: 2009-12-22
forum: Networking &amp; Wireless
---

### Post by the nazgul on 2009-12-22
after installing ubuntu 9 yesterday, i was unable to setup the internet connection! 
i used to connect on windows using a broadband connection ( cable connection ) with a username and a password! 
so i guess the only equivalent type of connection on ubuntu is DSL
so after going to the DSL tab and Adding a new connection, ( added username and password, Mac address was left empty, MTU set to AUTO method, IPv4 setting set to automatic ) and put a tick next to the " connect automatically " ! 
but nthg happens! it keeps giving me on the top right of the screen an alert saying that i am now disconnected! i try to reconnect by pressing on the DSL i created, it loads for few sec and then nthg happens!
i tried pinging ubuntu.com , it said that add could not be found!
i went to the terminal, typed ifconfig and found " eth0" and "lo" active! both of them! 
 
now im on windows waiting for ur help!
if any info is required please tell me! thank u

---

### Post by thedukesd on 2009-12-22
Maybe this will help:

[http://blogs.gnome.org/happyaron/2009/11/27/getting-networkmanager-work-with-pppoe-connection-on-ubuntu-9-10/](http://blogs.gnome.org/happyaron/2009/11/27/getting-networkmanager-work-with-pppoe-connection-on-ubuntu-9-10/)

[http://www.khattam.info/2009/11/08/solved-dsl-pppoe-not-able-to-connect-in-ubuntu-9-10-karmic-koala/](http://www.khattam.info/2009/11/08/solved-dsl-pppoe-not-able-to-connect-in-ubuntu-9-10-karmic-koala/)

[http://www.ubuntugeek.com/how-to-setup-networkmanager-work-with-pppoe-connection-on-ubuntu-9-10-karmic.html]("http://www.ubuntugeek.com/how-to-setup-networkmanager-work-with-pppoe-connection-on-ubuntu-9-10-karmic.html")

[https://edge.launchpad.net/~network-manager/+archive/trunk](https://edge.launchpad.net/~network-manager/+archive/trunk)

From what I know there was a bug in the Ubuntu 9.10 regarding DSL/PPP/PPPOE .

---

