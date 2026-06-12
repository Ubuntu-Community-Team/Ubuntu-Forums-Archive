---
title: "pppoe Jaunty Problem"
date: 2009-07-12
forum: Networking &amp; Wireless
---

### Post by _khAttAm_ on 2009-07-12
I am using Jaunty Jackalope (no upgrade, fresh install). I had removed network-manager and network-manager-gnome because it could not connect to my internet (back then, I had a different internet ppp dial up, pon did it for me). Now I need to connect using pppoe. I know it can be done with network-manager and reinstalled network-manager and network-manager-gnome.

Then, I created a connection by right clicking on the nm-applet and new DSL connection, but I get something like wired device not configured when I right click on the applet and try to connect.

I know this works coz it does work in my frens and also works for my card as it works with a USB portable install of Jaunty. So, I guess some configuration\update\something else caused this.

Currently, I am connecting to the internet using pon (dsl-provider)(I used pppoeconf to configure and it takes care of everything, almost) and have started it on startup. Also, I have shortcuts for start and hangup (also for gksu killall pppd.. sometimes need to use that too) in the panel and everything is perfect except I am unable to use OpenDNS.

To sum it up:
1. Can anybody help in specifying DNS for pppoeconf (pon)? What files will I need to edit. What do I put in there? How do I put it in?
2. Can anyone help me getting the network manager running? I have currently removed (purged) it since when I install it, I see some problems with pon too (Network is down or something like that).

Thank you for reading. Any comments are welcome. Please ask me questions (if needed) so that I can better explain it.

PS: I am a moderate Linux user and have been using Ubuntu for over a year now.

EDIT: I am using the amd64 version btw.
Linux 2.6.28-13-generic #45-Ubuntu x86_64 GNU/Linux

---

