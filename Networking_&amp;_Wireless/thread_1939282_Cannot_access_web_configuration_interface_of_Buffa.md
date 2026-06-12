---
title: "Cannot access web configuration interface of Buffalo Airstation"
date: 2012-03-11
forum: Networking &amp; Wireless
---

### Post by Timokl on 2012-03-11
I have bought today a [Buffalo Airstation N450 Giga]("http://www.buffalotech.com/products/wireless/wireless-n-routers-access-points/airstation-highpower-n450-gigabit-wireless-router-wzr-hp-g450h/") as Wireless N Router. I set up the router using Windows (I have a dua-boot setup), and everything worked fine.

When I booted into Ubuntu, I could connect to the internet normally, but I cannot open the web-based admin UI. When I enter the address 192.168.1.100 (which works fine with Windows), I am asked for my admin password, the address changes to [http://192.168.1.100/cgi-bin/cgi?req=twz](http://192.168.1.100/cgi-bin/cgi?req=twz) - but then the connection times out everytime. I can use the web with other websites without problems, but the admin interface does not come up.

Anybody with an idea what could be the problem and how get access to the admin UI from Ubuntu?

All the best,
Timo

---

### Post by gordintoronto on 2012-03-11
What browser are you using? What version of Ubuntu? Have you installed the Restricted Extras?

---

### Post by Timokl on 2012-04-05
I use Ubuntu 11.10 and normally Firefox.

I now figured that I can access the config interface with Chromium.

Strangely, I can access the interface from Win XP with Firefox without any problems.

But ok ... seems I found a solution. Thanks a lot!

---

