---
title: "Wireless will not work in 11.04! only wired!"
date: 2011-04-30
forum: Networking &amp; Wireless
---

### Post by FrankieD93 on 2011-04-30
Hey guys, first post here :) Well here's my problem..
So I recently installed ubuntu 11.04 after trying 10.10 for a while and never had to deal with wireless seeing as I always had it hooked up. but Now I am running it on my new laptop which has a Ralink RT5390 802.11b/g/n WiFi Adapter, and I am truly stumped on how to get linux to recognize it. Do I have to install a driver?.. plus, my laptop has the on/off toggle switch assigned to an 'fn' key, so it easily toggles on/off in Windows, but not in ubuntu. Any Ideas on how to make this work?

---

### Post by teachop on 2011-04-30
If the problem relates to the keyboard on/off control, you could try this from Terminal:  sudo rfkill unblock wifi

---

