---
title: "Pptp"
date: 2011-01-10
forum: Networking &amp; Wireless
---

### Post by Colo2 on 2011-01-10
Hello

I set up PPTP server on my ubuntu machine.

When I try and connect to it, it says: port opened, checking user and pass, then this error:

[IMG]http://i52.tinypic.com/1z3mf7p.png[/IMG]

Does anyone know what I've done wrong in the configuration ?

Windows diagnose, says that the server wasn't accepting connections.

Thanks

---

### Post by Colo2 on 2011-01-10
Oops, picture added

---

### Post by PatchesTheCaveman on 2011-01-10
Windows is configured to connect to an IPsec VPN, not a PPTP one.  To reconfigure it to connect to a PPTP VPN, click on the Network icon in the taskbar and click *Network and Sharing Center*.  On the blue bar on the left, choose *Change adapter settings*.  Then, right-click on the VPN connection your created and click *Properties*.  Switch to the *Security* tab.  In the drop-down box labeled *Type of VPN*, choose **Point to Point Tunneling Protocol (PPTP)**.  Click *OK*.

If you continue to have trouble, check your firewall settings.  You can temporarily disable the firewall to eliminate it as a potential problem by running the following command on a terminal:
```
sudo ufw disable
```

Good luck!

---

