---
title: "Network-manager can't connect to wireless"
date: 2006-06-23
forum: Networking &amp; Wireless
---

### Post by joeljkp on 2006-06-23
I have a laptop with a Dell Truemobile 1150 mPCI card that uses the native hermes/orinoco drivers. I'm using this to connect to a Linksys WRT54G router with 128-bit WEP. Yes, this card supports 128-bit WEP.

My problem is that I can connect manually using iwconfig, but network-manager always fails when pointed at the same AP, and when given the exact same WEP key (and telling it it's hex, not ascii or passphrase).

Here are the commands that bring it up successfully (I did this to connect now so that I could post):

```

sudo iwconfig eth1 essid a2 key xxxxxxxxxxxxxxxxxxxxxxxxxx open
sudo dhclient eth1

```

network-manager detects the AP, and pops up a dialog asking for the WEP. I tell it it's a hex key, paste it in, and tell it to use open authentication, but it always times out without connecting.

The relevant log from syslog is attached.

Thanks for the help!

---

