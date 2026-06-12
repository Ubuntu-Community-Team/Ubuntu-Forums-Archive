---
title: "upnp / Port forwarding issue"
date: 2010-09-15
forum: Networking &amp; Wireless
---

### Post by Origin_Unknown on 2010-09-15
Morning All,
 
I've recently moved my media center pc from windows 7 to Ubuntu, now while on windows 7 i used the machine with XBMC and utorrent with upnp enabled on my router (Netgear WNR2000 v1) and also in the utorrent client for the port mapping. I was also able to connect to the machine from work via remote deskop (via Windows RDP, real/ultra vnc) using either a windows machine or via ubuntu that i have installed on a laptop (externally to my network). Utorrent also was able to talk to my router and ask for the ports it needed via uPnp or even by setting the port forwarding manually.
Since upgrading ( ;) ) to Ubuntu from windows 7 on my mediacenter pc I've not been able to connect via RDP / VNC using port forwarding from the outside world although I added ports 5900 and (i beleive) 3389 to the port forwarding section in my router and pointing it to the static ip on my mediacenter. I'm also not able to get the ports to forward for deluge / vuze at all, if i manaually set port forwarding up then nothing happens and deluge says it has no incomming connections and it also doesn't talk to my router to ask for ports via upnp. The same also holds true for the linux version of sopcast which will not connect to any streams. I can also replicate the same issue on a laptop that i use with ubuntu installed.
 
If i watch my upnp page on my router config then i can see that my windows clients (Brother & Mom's macine) both talk to the router and ask it for ports so i assume that the router is working as it should be but obviously the fault happens when my ubuntu )10.04.1) clients ask for any kind of ports.
 
by default is there any kind of firewall installed on ubuntu or anything i need to do to allow it to ask for upnp connections?

---

### Post by the_mouse on 2010-09-26
In the last couple of days I was having troubles with Ktorrent uploading: no upload traffic after some time (ports forwarded via UPnP).

Yesterday I installed uTorrent on my Kubuntu 10.04 via Wine 1.2 and after 5 minutes of upload I got error saying "Listen error: you should change the listen port". uTorrent's test for forwarded port gave "OK" as a result, though.

Even if I change to a random port I get the same error after some time.

Using KTorrent or uTorrent I checked my TP-LINK to see if there's a successful UPnP port forwarding and everithing looked OK: the router had a log of both programs and their ports as forwarded.


So, is there some issue with (K)Ubuntu 10.04 and UPnP?


edit: Just got the same error again from uTorrent without UPnP...
On the other side I tried configuring KTorrent without UPnP and forwarding the ports manually and everything worked ok... I really have no clue why I'm getting these errors....

---

