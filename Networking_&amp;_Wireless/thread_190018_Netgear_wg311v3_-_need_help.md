---
title: "Netgear wg311v3 - need help"
date: 2006-06-05
forum: Networking &amp; Wireless
---

### Post by ness0216 on 2006-06-05
I've got ndiswrapper and the winxp drivers installed and ndiswrapper -l gives me driver present, hardware present. When I try to set up my essid and key however I can't get an IP address from the router. I'm using
sudo iwconfig wlan0 essid Dungeon enc open XXXXXXXXXXXX
iwconfig correctly identifies the essid as "Dungeon"
Then running sudo dhclient it will send IP requests but fails to get an IP.
It says I have 100% signal strength but I have no luck when I ping a server. This card used to work in the old verison of ubuntu and kubuntu; but for some reason 6.06 doesn't want to play nice. If anyone else has a wg311v3 working under dapper please lead me in the right direction. Thanks.

---

### Post by hackmeister on 2006-07-15
I just helped set this card up with a co-worker. We couldn't get an IP address until we passed the routers IP address via trace route. Once we did it worked flawlessly.

---

