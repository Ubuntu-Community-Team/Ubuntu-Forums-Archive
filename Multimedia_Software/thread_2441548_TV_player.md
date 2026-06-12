---
title: "TV player"
date: 2020-04-24
forum: Multimedia Software
---

### Post by nighthawk772 on 2020-04-24
I'm using Ubuntu Studio as my primary OS for couple of months now while I put Windows to rest a while..
I've discovered many great apps for editing or simply playing videos and music and now Ubuntu is my everyday OS. One thing that I come across is that lacking support for dvb cards. 
Since I'm huge fan of satellite TV, I was really hoping that studio version of Ubuntu is far more compatible with live tv but turns that is not true, at least in my case.
I tried Kaffeine and it works but it's not what I've expected. Considering programs like ProgDVB or DVBdream that work on Windows but not such version to support linux is very disappointing. 
I do hope this will change soon and that we will have decent software to watch live tv. Looks like I have to boot up my Windows again :(

---

### Post by TheFu on 2020-04-24
Most linux TV solutions use a client/server architecture.  These are complex to setup, but crazy flexible.  i don't know anything about dvb cards.  Here, we use HDHR network tuners which are really well supported.  in fact, "Recording" a TV show is really just a wget/curl download for the amount of time that the program is broadcast.

There are 2 main systems for accessing compatible TV tuners.
* MythTV [https://www.mythtv.org/wiki/Installing_MythTV_on_Ubuntu](https://www.mythtv.org/wiki/Installing_MythTV_on_Ubuntu)
* TV HeadEnd + some client like Kodi [https://kodi.wiki/view/Tvheadend](https://kodi.wiki/view/Tvheadend)
Both have extensive documentation.  These can run on the same system or different parts can run on different systems on the network.

There is also **me-tv**, but that is more like a current broadcast TV player that happens to have recording too.  May be what you seek..  TV stuff is highly dependent on local schedule data.  Some parts of the world have easy, free, schedule data.  Then there's where i live where schedule data is not free beyond 3 hours in advance.  One thing 7MC provided was free schedule data ... until last January.

---

