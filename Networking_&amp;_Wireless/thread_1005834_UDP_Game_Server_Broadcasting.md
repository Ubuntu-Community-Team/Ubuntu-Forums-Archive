---
title: "UDP Game Server Broadcasting"
date: 2008-12-08
forum: Networking &amp; Wireless
---

### Post by Pixelmilitant on 2008-12-08
Hi all,

I've been putting together a ubuntu 8.10 server, built specifically for running a LAN party. it is used for maintaining network connectivity (DHCP, DNS), serving games (all sorts of games, I'll get to that later), and also routing traffic between interfaces.

The Network structure is as follows:


eth0 - 192.168.1.150 - 255.255.255.0
This plugs into the local LAN

eth1 - 10.0.0.150 - 255.0.0.0
This plugs into the pre-existing venue network, which has a router on 10.0.0.254.


The default gateway is set to 10.0.0.254.


I've configured my server to masquerade, using webmin and the 'Linux Firewall' interface. I've also limited outgoing traffic to ports and destinations related to Valve's Steam service, so that our users can authenticate to Steam and use their services, without having full reign of the internet. This is to ensure that we don't chew through our venue's data quota, and that inappropriate sites are available to our users.


Now, for the issue!

I've provided that information for a little context to my setup, but my main issue is that quite a few of my games aren't broadcasting to the local LAN. I can bring the console down and type 'open 192.168.1.150', but they will not show up in the browser.

I'm talking specifically about Call Of Duty 2, Painkiller, Soldat, and UT3, all of which i can connect to manually, but cannot see via 'advertisement'. Some of the causes I have considered include:

- Firewall. I've enabled the specific UDP (and TCP where required) ports. I've even allowed an 'All EVERYWHERE' rule on the firewall to rule that out (don't worry, LAN only).

- Game server-specific configuration. I've read up how to set the servers to advertise via LAN. 

- Local firewall. Maybe it was my PC. Disabling my firewall did not help, and besides, I can see a stack of internet games in each game browser.

- Local game. Possibly the in-game browser doesn't like something. I also use XFire, which has a LAN browser in it. They don't show up in there, whereas my other servers do.


So, I am thinking that the issue may lie in something to do with UDP broadcasting and possibly which IP address/network these UDP announce broadcasts are occurring on. My quake 3 arena server would not broadcast itself and show up in the quake 3 game browser if I bound it to a specific port and/or IP address, yet if I leave it to its own devices, it lists fine. A little bit annoying due to not being controllable, but at least they're available now.


Anyway, if anyone knows of anything related to this issue, I'd love to hear right away, as time is ticking away (the LAN is in less than 5 days away).


Regards,
PixMil

---

### Post by Pixelmilitant on 2008-12-08
I found it interesting here that another service (counterstrike) has the same issue with broadcasts.

[http://forums.srcds.com/viewtopic/5182](http://forums.srcds.com/viewtopic/5182)

The fix is to force the server to broadcast its presence via UDP.


I just wonder if something is stopping the server from sending UDP broadcasts to the 192.168.1.255 broadcast domain.

When I'm in front of my computer I'll run some tcpdump/netstat commands and see whats out there...

---

### Post by Pixelmilitant on 2008-12-08
Sorry to stack posts against myself like this, but:

[http://forums.soldat.pl/index.php?PHPSESSID=670b301be592ab6567295e056219cdcf&topic=31026.0](http://forums.soldat.pl/index.php?PHPSESSID=670b301be592ab6567295e056219cdcf&topic=31026.0)

According to the above post (10-11-08), the soldat game browser does not search LAN games anyway.


That rules that one out to attempt to troubleshoot!!

---

### Post by psusi on 2008-12-08
My guess would be that the game server is picking the wrong interface to broadcast on.  See if you can tell it which one to use.

---

### Post by Pixelmilitant on 2008-12-09
> **psusi said:**
> My guess would be that the game server is picking the wrong interface to broadcast on.  See if you can tell it which one to use.

Yeah, thats the impression I get, I'm just not sure how I tell a 3rd party game server to hook into a particular interface. Could it be possibly limiting LAN UDP advertisements to localhost/127.0.0.1 ?

I think i need to run wireshark on my windows client to see if anything UDP-shaped is coming from my server...


Thanks for the reply so far.

---

