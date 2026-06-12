---
title: "Cannot use system-wide connections in jaunty"
date: 2009-06-28
forum: Networking &amp; Wireless
---

### Post by archivator on 2009-06-28
I am trying to set up a HTPC with XBMC as the media center. I started off by using Xubuntu Jaunty, installed xbmc, stripped the xubuntu a bit and was almost happy. I had networking at this point (naturally, since the nm-applet was running).

I then decided to scrap the whole Xfce business and use the Xsession that XBMC provides which basically starts XBMC instead of your WM. That way, I lost my wireless connection. The connection has been marked system-wide (appears in /etc/NetworkManager/system-connections) but looks like it's never activated without the nm-applet. 

Any help will be greatly appreciated.

[Follow-up] This is a suspend/resume issue. Once the system is woken up from S3, the network goes down *if the applet is not running*

[Follow-up] Fixed by using the madwifi file in /etc/pm/config.d/

---

