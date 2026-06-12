---
title: "wpa_supplicant is being REALLY slow to connect"
date: 2009-02-01
forum: Networking &amp; Wireless
---

### Post by thinking2loud on 2009-02-01
Hello, I've had this persistent problem ever since I upgraded from Vista to Ubuntu.  Unfortunately, this is one of those that Windows has handled better....

I have 2 wireless networks in the house.  One of them is unsecured.  Ubuntu always connects to it on the first try.  The other one has WPA.  I have always had trouble with it...and now I tracked it down (...sort of...).  wpa_supplicant stays in the wpa_state=GROUP_HANDSHAKE for a really, really, really long time.  It will complete...eventually...or at least it does for the times where I give it enough patience.  After that, the DHCP gets around to configuring it, and then everything works fine and stays that way.  I watched it with wpa_cli; an example:
```
laptop:~$ sudo wpa_cli
wpa_cli v0.5.8

Selected interface 'wlan0'

Interactive mode

> sta<2>Associated with 00:14:bf:af:b2:19
tus
bssid=00:14:bf:af:b2:19
ssid=yost
id=0
pairwise_cipher=TKIP
group_cipher=TKIP
key_mgmt=WPA-PSK
wpa_state=GROUP_HANDSHAKE
ip_address=192.168.1.102
> <2>Associated with 00:14:bf:af:b2:19
<2>Associated with 00:14:bf:af:b2:19
<2>Associated with 00:14:bf:af:b2:19
                                       [...snip...]
<2>Associated with 00:14:bf:af:b2:19
<2>Associated with 00:14:bf:af:b2:19
<2>Associated with 00:14:bf:af:b2:19
status
bssid=00:14:bf:af:b2:19
ssid=yost
id=0
pairwise_cipher=TKIP
group_cipher=TKIP
key_mgmt=WPA-PSK
wpa_state=GROUP_HANDSHAKE
> <2>Associated with 00:14:bf:af:b2:19
p<2>Associated with 00:14:bf:af:b2:19
<2>Associated with 00:14:bf:af:b2:19
                                       [...snip...]
<2>Associated with 00:14:bf:af:b2:19
<2>Associated with 00:14:bf:af:b2:19
<2>WPA: Key negotiation completed with 00:14:bf:af:b2:19 [PTK=TKIP GTK=TKIP]
<2>CTRL-EVENT-CONNECTED - Connection to 00:14:bf:af:b2:19 completed (auth) [id=0 id_str=]

```

That one completed more rapidly than usual.  When I set the router (Linksys WRT54GSV4) to unsecured it connects right away.  This is a Dell E1505 with Broadcom 4311.

Clues, anyone?

---

### Post by thinking2loud on 2009-02-01
I sort-of solved it by getting rid of nm-applet and using manual configuration.  It connects.  Eventually.  I have to listen to the kids and wife complain they can't get on the internet.  But after a few games of minesweeper it works.

---

