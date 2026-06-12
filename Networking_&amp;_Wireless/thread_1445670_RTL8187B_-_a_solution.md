---
title: "RTL8187B - a solution?"
date: 2010-04-02
forum: Networking &amp; Wireless
---

### Post by microfi on 2010-04-02
Hi folks!

I've successfully managed to connect to my WEP-protected wireless network through RTL8187L Linux driver from Realtek's website! I had no success doing this through ndiswrapper or through Ubuntu embedded drivers. I made no modifications to the downloaded driver (only changed entries at *Makefile*, *wlan0up* and *wlan0down* from RTL8187L to RTL8187B, but I don't think it's necessary) and installed as if I had a RTL8187L card.

[[ Download from RTL8187L Driver Page ]]("http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8187L")

I've just downloaded a 130MB update from Ubuntu's repositories flawlessly. Hope you are well-succeeded installing this!

Filipe.

---

