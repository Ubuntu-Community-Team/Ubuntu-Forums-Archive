---
title: "Not use VPN for some sites"
date: 2010-10-06
forum: Networking &amp; Wireless
---

### Post by Ubu-freak on 2010-10-06
To get on some sites I need to use a VPN, but in order to get on the internet I need to login on one of my school's websites. If I use the VPN then an error will occur on my school's login website since I'll be using the VPN and not my original connection to connect to it. I was wondering how do I configure firefow so that it doesn't use the VPN to connect to pages that have a url of .*\.example\.edu.*

---

### Post by SeijiSensei on 2010-10-06
Type the command "route -n" in a Terminal and post it here in [noparse]```

```[/noparse] tags.

You'll need to add a static route to the school's network so it won't be routed through the VPN.  There isn't really a way to do this with hostnames, nor with changes to the browser.

You'll need to determine the IP address of the school's login website.

---

### Post by Ubu-freak on 2010-10-08
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
59.66.241.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
0.0.0.0         59.66.241.1     0.0.0.0         UG    0      0        0 eth0

```

---

### Post by SeijiSensei on 2010-10-08
Where's the VPN interface? I just see eth0.  Start the VPN connection, then post the routing table.

Do you know the IP of the login website?  Don't post it, but you will need to know it.

---

### Post by Ubu-freak on 2010-10-16
Sorry for the late reply, I've been busy lately.

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.31.255.1    0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
72.52.104.74    59.66.238.1     255.255.255.255 UGH   0      0        0 eth0
72.52.104.74    59.66.238.1     255.255.255.255 UGH   0      0        0 eth0
59.66.238.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0

```

---

