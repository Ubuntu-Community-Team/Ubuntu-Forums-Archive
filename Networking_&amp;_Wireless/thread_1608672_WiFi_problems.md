---
title: "WiFi problems"
date: 2010-10-29
forum: Networking &amp; Wireless
---

### Post by svsanchez on 2010-10-29
Hello,

I installed Ubuntu Desktop Edition 10.1 a couple of days ago on my netbook(PB dot m), and it's working quite well, but I don't really like gnome, so I've installed e17 and fluxbox. 

The WiFi works under gnome, but it doesn't work with e17 or fluxbox. I've installed wicd and wifi-radar and both work property whith gnome, but under e17 or fluxbox, can detect the WiFi conections but when I try to connect, don't get an IP.

Can anybody give me some help?

Thanks.

---

### Post by worldwithoutgurus on 2010-10-30
Completly uninstall Wicd and Wifi-Radar and sudo apt-get install connman indicator-network. Then configure the ConnMan gadget in E17 &#8211; ConnMan should work in Fluxbox as well.

[https://wiki.ubuntu.com/ConnMan/Installation](https://wiki.ubuntu.com/ConnMan/Installation)
(Indicator-Network is faster/simpler than Network-Manager in GNOME)

[http://dazibaldo.pagesperso-orange.fr/Files/Pictures/Connman-e17.png](http://dazibaldo.pagesperso-orange.fr/Files/Pictures/Connman-e17.png)

---

