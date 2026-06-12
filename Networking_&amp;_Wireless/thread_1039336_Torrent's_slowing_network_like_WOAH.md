---
title: "Torrent's slowing network like WOAH"
date: 2009-01-14
forum: Networking &amp; Wireless
---

### Post by tErbo b00st on 2009-01-14
This is my first post as I have figured out every other issue on my own thanks to these forums and google (started using ubuntu a couple months ago).

I'm wirelessly (problem persists even when hardwired) connected to my Dlink DI-524 router with my Intel 3956/a/g/b.  I have my router set to only broadcast in g.  Internet speeds are really fast when a torrent program is not running.

As soon as I load up a torrent program (tried default transmission, as well as utorrent through wine) all internet speeds drop drastically.  And it is not because I'm using all my bandwidth as total download speed (upload similar)will be somewhere between 30-70 kbps, sometimes spiking to around 200 for a brief minute.  Which is a problem in itself.  My torrent speeds will not get very high.  I'm using upnp port forwarding and both utorrent and transmission report back that the port is open.

Anyone connected to my router, either wireless or wired, have overall really crappy internet speeds as well.

Please help.  Thanks in advance.  I'm loving ubuntu so far and have basically given up on windows...but this is the only problem that is keeping me 100% satisfied with ubuntu.

---

### Post by tErbo b00st on 2009-01-15
i hate bumping threads....but i need someone's help

---

### Post by blackened on 2009-01-15
It's more likely that your upload speeds are the culprit. If you bog down the upload bandwidth, then other client programs (e.g. Firefox, email clients, etc.) can't make requests. Limit upload to 10-15K and it should help.

---

