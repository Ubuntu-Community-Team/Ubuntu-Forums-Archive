---
title: "OpenSWAN IPSec L2TP VPN for Android 4.0"
date: 2012-03-20
forum: Networking &amp; Wireless
---

### Post by ThatOtherGuy435 on 2012-03-20
I built up an IPSec L2TP server based on the configuration found in another thread on this forum: [http://ubuntuforums.org/showthread.php?t=1645473](http://ubuntuforums.org/showthread.php?t=1645473)

All of my configuration files match that walkthrough except for the changed IP addresses.

However, there appears to be a bug in the Android implementation of IPSec in Ice Cream Sandwich related to sending non-standard packets. Specifically, it's outline in this Google Code bug report: [https://code.google.com/p/android/issues/detail?id=23124](https://code.google.com/p/android/issues/detail?id=23124)

In /var/log/auth.log I see the same types of log entries:
```

<server.hostname> pluto[30383]: "L2TP-PSK-noNAT" <cli.ent.ip.addr> #1: ignoring informational payload, type IPSEC_INITIAL_CONTACT
<server.hostname> pluto[30383]: "L2TP-PSK-noNAT" <cli.ent.ip.addr> #1: received and ignored informational message
<server.hostname> pluto[30383]: "L2TP-PSK-noNAT" <cli.ent.ip.addr> #1: byte 7 of ISAKMP NAT-OA Payload must be zero, but is not
<server.hostname> pluto[30383]: "L2TP-PSK-noNAT" <cli.ent.ip.addr> #1: malformed payload in packet
<server.hostname> pluto[30383]: "L2TP-PSK-noNAT" <cli.ent.ip.addr> #1: sending notification PAYLOAD_MALFORMED to <cli.ent.ip.addr>:4500
<server.hostname> pluto[30383]: "L2TP-PSK-noNAT" <cli.ent.ip.addr> #1: sending encrypted notification INVALID_MESSAGE_ID to <cli.ent.ip.addr>:4500
<server.hostname> pluto[30383]: "L2TP-PSK-noNAT" <cli.ent.ip.addr> #1: byte 7 of ISAKMP NAT-OA Payload must be zero, but is not

```
Since deity_of_choice only knows when a fix will trickle down from Google to my device (Asus Transformer TF101), does anyone know of a workaround? Putting pluto into a permissive mode where it won't automatically refuse if the reserved bits are set, or an alternative to OpenSWAN that doesn't use pluto for the IKE?

I have tried the configuration on OpenSWAN 2.6.28 (in the maverick ppa), 2.6.37 (from OpenSWAN directly), and 2.4.15 (from source), and all versions are having the same issue.

---

### Post by apotheos on 2012-06-29
I am having the exact same problem. Have you found anything yet?

---

### Post by ThatOtherGuy435 on 2012-07-06
I ended up giving up, rooting my tablet, and using OpenVPN - though that has stopped working since the 4.0.4 update, so I may have to revisit this.

The two workarounds I found are using raccoon instead of pluto/openswan ( [http://wiki.nikoforge.org/L2TP/IPSec_VPN_Setup_on_Centos_6_(64-bit)_for_use_with_Android_ICS_Clients](http://wiki.nikoforge.org/L2TP/IPSec_VPN_Setup_on_Centos_6_(64-bit)_for_use_with_Android_ICS_Clients) ).

The other is a patch for OpenSWAN, though you'd (obviously) have to build it from source:
[https://code.google.com/p/android/issues/detail?id=23124#c180](https://code.google.com/p/android/issues/detail?id=23124#c180)

---

