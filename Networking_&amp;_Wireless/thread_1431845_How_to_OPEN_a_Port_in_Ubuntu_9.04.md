---
title: "How to OPEN a Port in Ubuntu 9.04"
date: 2010-03-17
forum: Networking &amp; Wireless
---

### Post by Habboblob on 2010-03-17
[CENTER]**[SIZE="6"][COLOR="Red"]Hello there Ubuntu Users.[/COLOR][/SIZE]**
[[SIZE="4"] Whatever I have tried to do, I cannot seem to open any port on Ubuntu.

Now let me give you some details[/SIZE]
[SIZE="4"][COLOR="Red"]Ubuntu Version: 9.04[/COLOR]
[COLOR="Orange"]Network Connection: Wired[/COLOR]
[COLOR="RoyalBlue"]Router: LINKSYS WRT54G[/COLOR]
[COLOR="Lime"]Port I want open: 4900[/COLOR][/SIZE]

[SIZE="5"]Please give me step by step guidelines so that if I encounter this problem again, I will be able to resolve it without calling for help.

Also, let me explain why I want to open a port, firstly, I want to open a port in Ubuntu, and then use this open port in Ubuntu for a Virtual Pc (in _VirtualBox OSE_) that I am running, which has a OS of _Windows XP_. Because in the virtual box I have a remote management program, which requires my _IP Address and an open port._
Thank for your time[/SIZE]



[/CENTER]
Habboblob

---

### Post by aeiah on 2010-03-17
using iptables. what port do you need to open? are you sure it isnt a router firewall issue?

---

### Post by Habboblob on 2010-03-17
I went to open port 4900
I have a Linksys WRT54G Router.

---

### Post by Habboblob on 2010-03-17
old

---

### Post by c0nfusedami on 2010-03-17
I could be mistaken but I thought a router handled opening ports and port forwarding.

---

### Post by Iowan on 2010-03-17
Ubuntu will open ports as it needs - especially if it has a service running there - but you won't necessarily see them from [http://www.yougetsignal.com/tools/open-ports/](http://www.yougetsignal.com/tools/open-ports/) - since it sees only your router's ports. As **c0nfusedami** mentioned, if you want the site to see that port as open, you'll need to configure your router (too).

---

### Post by Habboblob on 2010-03-17
Well then how do I open up a port, so then I can use that port for my Virtualbox OSE?

---

### Post by Jeff Anthony on 2010-03-17
You'd probably have to ask on the [linksys forums]("http://forums.linksysbycisco.com/"), it's a router (hardware) issue, not an Ubuntu issue. You configure a router the same exact way no matter what OS you use, usually via browsing the router's IP address with Firefox. Good luck!

---

