---
title: "NM-Applet is not showing up / No Wireless"
date: 2012-03-28
forum: Networking &amp; Wireless
---

### Post by Hellageddon on 2012-03-28
Alright, 

I am using an internal wifi-card which works on wlan0.
I uninstalled Wicd and installed the Network-Manager to manage VPN Connections, as there apparently no other way to do that.

My /etc/network/interfaces is configured like
```

auto lo
iface lo inet loopback

```

When I open the NM over Preferences it shows me only the eth0 connection and nothing else. No wireless connections either.

And also, that nm-applet isn't showing up in my panel.

So can anyone explain me how to solve this?

---

### Post by nothingspecial on 2012-03-29
*Thread moved to **Networking & Wireless**.*

---

### Post by Hellageddon on 2012-03-29
**Solved:**

clearing out /etc/network/interfaces to blank and adding a notification area to my panel made the applet showing up.

Also is it important to uninstall other network-managers (e.g. Wicd)

---

