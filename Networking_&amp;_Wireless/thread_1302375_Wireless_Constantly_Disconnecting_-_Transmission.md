---
title: "Wireless Constantly Disconnecting - Transmission"
date: 2009-10-27
forum: Networking &amp; Wireless
---

### Post by megafan on 2009-10-27
Im really new to jaunty, only a couple days into the whole experience, having loads of fun customizing everything, but having a problem with my wireless staying connected. Seems my router (D-link DIR-625) thats connected to the home Windows based PC is periodically disconnecting me from the home network (about once a half hour or so) I also noticed that its prevalence is higher when im running Transmission Bittorent client. This is VERY annoying because I have yet to be able to download a full torrent without constant disconnections. I have the same IP address as before when i was running windows, using the same listening ports etc. 

Could this be a problem with the settings ive got on jaunty, or perhaps a problem with my router not trusting the new system etc? Any insight into the issue would be greatly appreciated!

---

### Post by Dark_Stang on 2009-10-27
Sounds like your router is going bad or may need an upgrade. Torrenting applications are notorious for opening up far more connections than the average home router or access point can handle. For example: The default configuration that came with my qBitorrent application opened up 500 connections. I turned it down to 20 and now it's fine.

If you are wanting to torrent constantly and not drop signals or slow down the rest of your network you will need to drop some more cash on a much nicer router. A low end Cisco or Sonicwall router ($200-$400) should do okay. But that's some big cash to spend to save a little money on movies.

---

### Post by megafan on 2009-10-27
Yeah that seemed like a likely candidate, but when I had windows several days ago, I was downloading files at incredible speeds, sometimes even 2mbps with no interruptions in the connections, even when I had my computer on for days! Now with jaunty im getting average speeds of around 20kb/s for about ten minutes before the router boots me off. 

Every other computer in the house running windows has no problems with torrent downloading, but jaunty seems to rub the router the wrong way or something... Im hoping there is a fix for this, because I cant warrant buying a new router and seeing if that helps when this is the only computer with a downloading issue.

Im going to try and tweak the amount of connections like you suggested and see if that will effect its longevity. Im wondering what else it could be because the router is booting me off, even when transmission isnt loaded, and there is very little strain on the bandwidth. 

Im really appreciating the community atmosphere to this OS BTW! I feel relatively free from the restraints of big corporate powers - at least on matters of software!

---

