---
title: "Prefer Wireless over Ethernet"
date: 2011-08-15
forum: Networking &amp; Wireless
---

### Post by TechSupportx86 on 2011-08-15
OK so i am trying to setup a simple VOIP/File server for my buddy. Now the problem is the only wired connection he have access to is 1.5Mbp/s DSL (Please note that is not megabyte). 

There is however a 20Mbp/s wireless connection at his house (The server will be in the guest house where i am, and the 20Mbp/s Cable in his parents house, which he is allowed to use). 

The problem i am having is i need to have LAN access on his Ethernet card (eth0) for SSH and WAN on his wireless card (wlan0). Whenever i turn on the ethernet card it overrides the wireless and doesn't use it, this isn't what i want. 

He wants to use the wireless for internet, and the ethernet for LAN. Is this possible?

---

### Post by TechSupportx86 on 2011-08-15
lol, nevermind i actually figured it out.

In case anyone is wondering, you simply go into "Edit connections" and edit the one for your wired connection. Go to IPv4 and near the bottom go to "Routes". There will be a radio button for "use this connection only for for resources on it's network"

---

