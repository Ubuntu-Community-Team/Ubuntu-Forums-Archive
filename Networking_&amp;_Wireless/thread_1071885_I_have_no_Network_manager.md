---
title: "I have no Network manager"
date: 2009-02-16
forum: Networking &amp; Wireless
---

### Post by jarett on 2009-02-16
Ok so installed ubuntu studio 8.10 I believe it is and during installation it said cant find DHCP. So I skipped the step after trying again. But now I don't have Network Manager, so I can't get hooked up to the internet on ubuntu luckily I'm dual booting it with windows. So my first question is what the crap is a DHCP? Then my second question is how to I find it? And my third question is how can I install Network Manager since I don't have a connection in Ubuntu?

 thanks,
   Jarett

---

### Post by x33a on 2009-02-16
dhcp is a network protocol. it is used to automatically configure the network. if you are using a router, and you enable dhcp, you'll be assigned lan ip automatically.

[http://en.wikipedia.org/wiki/Dhcp](http://en.wikipedia.org/wiki/Dhcp)

to enable or disable, it you have to access your router

type [http://192.168.1.1](http://192.168.1.1) or [http://192.168.0.1](http://192.168.0.1) (depending upon the router)

if you can't access the net and want to install network manager,

1. open a terminal, alt+f2, type gnome-terminal.
2. type sudo pppoeconf in the terminal.
3. follow the instructions, if unsure stick to the defaults.
4. you should have the connection running in a few moments.

if you manage to connect to the net, then type in a terminal
```
sudo aptitude install network-manager
```this will install the network manager.

---

### Post by jarett on 2009-02-16
ok ill try it

---

### Post by jarett on 2009-02-16
ok so i tried it. but it wasnt searching for wireless and thats what i have...

---

### Post by x33a on 2009-02-17
you can find good instructions to set your wireless connection here:

[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

---

