---
title: "Squeezecenter networking problems"
date: 2009-11-07
forum: Multimedia Software
---

### Post by clnanderson on 2009-11-07
So I've been trying to get squeezeboxserver/center up and running on my mediabox (9.04 xbmc, boxee--zotac atom n330 board), and have run into some sort of networking problem I think. I have the following machines on my network:

mbox (9.04)
desktop (9.10)
laptop (xp)
squeezeboom
squeezebox2

Fresh install of jaunty and squeezeboxserver on mbox. Tried 7.3.3 as well.

Server on mbox can't find the players, vice versa.
I can ping the players from mbox and other machines.
I can see them "acking" when they try to connect to squeezecenter on mbox in a network sniffer (wireshark)
Port 9000 shows as open on a nmap scan from desktop.
I can ssh into mbox from one machine (desktop) but not from the laptop.
I can view the web interface from one machine (desktop) but not from the laptop.
I can stream to desktop, but not from the laptop.
ufw is disabled.

I can't ping mbox from laptop, (times out) but I can ping the rest of the network from laptop. I can ping mbox from desktop.

Running squeezeboxserver on desktop, players connect to that with no problem and play fine.

In squeezecenter web interface (mbox) under "players" both desktop and a squeezboom show up when squeezeboxserver is running on desktop. So, squeezecenter on mbox can find squeezboxserver on desktop.

Changing ip of desktop doesn't change it's access (so no filter or something based on ip).

I've been posting over at slimserver.forums but so far to no avail, thought I'd see whether general ubuntu advice might be helpful.

[http://forums.slimdevices.com/showthread.php?t=70780](http://forums.slimdevices.com/showthread.php?t=70780)

Any help would be appreciated.

---

### Post by clnanderson on 2009-11-07
Interesting. I can get web access to mbox from the laptop if I use it's network name ('mbox'), and after doing that I could get access using the ip address!

When I ssh from the desktop it tells me that the last login was from desktop.wanaddress but when the last login was from the laptop it doesn't give the full address just the network name. Don't know whether that changes anything.

But, that didn't change anything for the players.

---

