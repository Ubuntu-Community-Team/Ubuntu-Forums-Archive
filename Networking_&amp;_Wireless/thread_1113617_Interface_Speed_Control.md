---
title: "Interface Speed Control"
date: 2009-04-01
forum: Networking &amp; Wireless
---

### Post by zeekgenateer on 2009-04-01
Hey let me tell you about my problem.

I have two computers a windows and an ubuntu.  The windows is my gaming/everyday rig and my ubuntu is a webserver, media center and fileserver.  I have a web gui for torrents (torrentflux) that I like to use, however, it's really frustrating to manually stop and start all torrents through the web gui if I want to play online.  I'd like to have something that I can use that changes the max up/down of eth0, and preferably can be run in a script.  I've looked at QoS, but I have not found a very good guide.

If anyone knows a guide for QoS or a program that would be able to do the above that would be helpful.

---

### Post by freonchill on 2009-04-01
do you have a router?

its typically easier to have the router decide the QoS rather than the individual machine.

---

### Post by zeekgenateer on 2009-04-01
I do but the router in question is crappy.  Was thinking about getting a better one, but can't find a cheap one that works with open firmware or comes with QoS.

---

### Post by freonchill on 2009-04-01
whats cheap to you?

you can find dd-wrt/openwrt/tomato supported G routers for < $ 30
you can find dd-wrt/openwrt/tomato supported N routers for < $100

---

### Post by Cheesehead on 2009-04-01
Deluge has such a control. It is wonderful - my family online doesn't notice lag due to torrents at all. Control by-torrent and for the whole bundle-of-torrents. And the bundle controls are a right-click in the notification area. Very convenient.

---

### Post by freonchill on 2009-04-01
> **Cheesehead said:**
> Deluge has such a control. It is wonderful - my family online doesn't notice lag due to torrents at all. Control by-torrent and for the whole bundle-of-torrents. And the bundle controls are a right-click in the notification area. Very convenient.

true, but that doesnt help him for his media server, web server, and file server.

---

### Post by zeekgenateer on 2009-04-01
The torrent software is website based run with php and python (bitTornado), so no I would need another program to control based on port.

That is good money, but finding it in local stores can be a doozy. (Rather not pay shipping and saving up for laptop)

---

### Post by freonchill on 2009-04-01
craigslist can be your friend

i have found several wrt54g v1-4 on there for $10-30
(sometimes you have to haggle people down)
most of the time you have to email them and ask b/c most people post "linksys G router" and thats it.

---

