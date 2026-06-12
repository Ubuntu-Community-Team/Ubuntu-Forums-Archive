---
title: "Bittorrent Killing Ability to Browse the Web"
date: 2011-02-19
forum: Networking &amp; Wireless
---

### Post by drlego on 2011-02-19
OK I just started having this problem a few hours ago and I'm officially surrendering because I ran out of ideas. Here's the run down:

When I load qBittorrent and start downloading, I am unable to browse any web pages in Firefox (Stays @ Connecting to ABC.com.........). At first, I thought this could be some kind of shenanegans from my ISP. However, I cannot even access my own router from Firefox while a torrent is downloading. I can ping my router, and ping other websites, but I cannot browse them in Firefox. When I close qBittorrent, Firefox regains the ability to access and render content.

This is very strange and I have no idea how to go about solving this problem -- let alone why this problem even rose up in the first place.:confused:

Has anyone else encountered this problem? Any guidance would be greatly appreciated.

(ulimit = unlimited)
(ports all forwarded properly)

---

### Post by kerry_s on 2011-02-19
throttle it, sounds like it's using all the bandwidth.

for example: i have 3mb internet, i set mine to 150, so i can browse, watch vids, etc...

if you don't need to watch vids go 75% of your connection speed.

---

### Post by SeijiSensei on 2011-02-19
BT creates lots of connections between your client and all the peers.  Many consumer routers don't have enough memory to maintain all those connections.  So even if you limit your bandwidth, you may still find your router falls over when using BT.  

The solution is to limit the number of *connections* as well bandwidth.

---

### Post by drlego on 2011-03-03
Thanks for the input folks,

I have tried multiple times. It seems like I can get it to be stable at 10 connections per torrent -- but this is far too low to be realistic. When I was running windows I was able to achieve 80+ connections per torrent.

Anything that uses Bittorrent is killing my ability to use the internet -- for example, the Blizzard download client. 

I've spent a week trying to fix this issue and still nothing. I suspect there is some kind of strange thing that I need to tweak in ubuntu to get this to work properly but I have no idea where to start.

Thanks for your help,
Drlego

---

### Post by coolbrook on 2011-03-03
Limit your upstream to 5% of its capable speed.

---

