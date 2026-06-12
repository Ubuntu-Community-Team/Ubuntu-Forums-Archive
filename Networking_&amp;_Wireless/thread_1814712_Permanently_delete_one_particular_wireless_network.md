---
title: "Permanently delete one particular wireless network"
date: 2011-07-30
forum: Networking &amp; Wireless
---

### Post by jonlemur on 2011-07-30
Hello, I'm wanting to permanently delete one particular wireless network.  I don't want to merely disable auto-connect, I want it to not even show up in my list of available networks.  Is there a way to do this?  I'd like to still be able to connect other wireless networks.

I'm using Ubuntu 11.04

Thanks

---

### Post by garvinrick4 on 2011-07-30
#You can edit connections in network manager with applet in upper right that you must have seen. Edit connections to wireless to highlight connection and hit edit and remove.
#If it is a routers SSID you do not want to see when it scans then it must be a router of yours. Type in your default gateway in URL and put in routers user name and password and make changes.

---

### Post by jonlemur on 2011-07-30
Thanks for the reply.  When I edit connections and delete it, it just reappears immediately.  It seems that there should be a config file somewhere that I can blacklist certain networks from appearing in nm-applet.

---

### Post by FuzzyFeat on 2011-08-14
I am having a problem similar to yours. I delete the connection and it pops up  again, and again, and again .. .  I posted the problem as a ghost connection, but have received no solution. Luck to us both.

---

### Post by walt.smith1960 on 2011-08-14
This is on Ubuntu 11.04 classic with Gnome 2 menus, not sure about Unity.  System -> Preferences -> Network Connections -> Wireless.  Select the network you want to delete  and "delete". That should make it go away permanently.

---

### Post by FuzzyFeat on 2011-11-22
> **walt.smith1960 said:**
> This is on Ubuntu 11.04 classic with Gnome 2 menus, not sure about Unity.  System -> Preferences -> Network Connections -> Wireless.  Select the network you want to delete  and "delete". That should make it go away permanently.

Yes it should, but it doesn't. That is the problem. It keeps reappearing.  sometimes right away, many times in a couple of days, one time over a week.

---

