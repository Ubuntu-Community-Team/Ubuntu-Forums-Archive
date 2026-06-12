---
title: "wlan0: rx 25 DUPs in 76 Packets etc messages"
date: 2009-04-13
forum: Networking &amp; Wireless
---

### Post by nandemonai on 2009-04-13
Greetings,

I'm having an issue in Dapper on an old laptop with a:

```
0000:05:00.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface
```

PCMCIA card.

Things were smooth but the last couple of days I've noticed some odd behaviour. Namely:

```
[17180179.376000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[17180181.444000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[17180181.652000] wlan0: duplicate address detected!
```

When bringing the interface up manually.

Also, during my sessions (cli only) I'm bugged on occasion with messages like so:
```

[17181894.744000] wlan0: rx: 26 DUPs in 83 packets received in 10 secs
[17188259.084000] wlan0: rx: 14 DUPs in 66 packets received in 10 secs
[17190370.248000] wlan0: rx: 67 DUPs in 133 packets received in 10 secs
[17190381.700000] wlan0: rx: 14 DUPs in 49 packets received in 10 secs
[17191338.996000] wlan0: rx: 48 DUPs in 103 packets received in 10 secs
[17191353.732000] wlan0: rx: 31 DUPs in 80 packets received in 10 secs
[17191364.300000] wlan0: rx: 15 DUPs in 49 packets received in 10 secs
[17191908.508000] wlan0: rx: 13 DUPs in 20 packets received in 10 secs
[17194485.084000] wlan0: rx: 17 DUPs in 67 packets received in 10 secs
[17194496.944000] wlan0: rx: 63 DUPs in 126 packets received in 10 secs
[17194688.652000] wlan0: rx: 21 DUPs in 64 packets received in 10 secs
[17194701.540000] wlan0: rx: 27 DUPs in 73 packets received in 10 secs
[17194720.188000] wlan0: rx: 25 DUPs in 76 packets received in 10 secs
[17195325.184000] wlan0: rx: 70 DUPs in 144 packets received in 10 secs
```

All was well for a couple weeks but as I said the last few days it's been doing this. I'm not sure what to make of it. Are DUPs duplicate packets? ala packet collision? Or should I be worried from a security point of view.

I'm using WEP (no no I know) with a whitelist for mac addresses (Just the one interface).

/etc/network/interfaces file like so:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

iface wlan0 inet static
wireless-mode managed
wireless-essid XXXXXXXXXXXXX
wireless-key s:XXXXXXXXXXXXX
address XX.XX.XX.XX
netmask 255.255.255.0
gateway XX.XX.XX.XX
```

Details are blanked out ;)

I'd appreciate any help, it's an old card and it doesn't exactly run the best so if it's just packet collision or some such how would I go about suppressing the messages so they don't interrupt my cli session?

As a side note I'm using wifi channel 11 which I haven't had any isses with previously.

---

### Post by nandemonai on 2009-04-13
After doing a little reading it seems like there could be an issue with a duplicate IP address which is not possible my end because I know all the IPs in use on my network.

Would this indicate that perhaps someone is trying to spoof the mac address of this card in order to gain access to my wifi connection?

I've never once seen a connection to my router that wasn't me (I've been monitoring it all day) and it seems even after shutting down the system for an hour or two, rebooting and reconnecting the wifi connection I get the same messages instantly.

I find it hard to believe someone is sitting there all day waiting for me to connect and then injecting packets...

Surely there is another explanation?

---

### Post by nandemonai on 2009-04-18
Well after a long and painful update to Hardy the issue seems to have disappeared for the time being. Not too sure if it's coincidence yet or not though. Time will tell I guess.

Unfortunately even with ndiswrapper I can not get this card to use WPA so for the moment I'm just being careful about not leaving the AP open when I'm not using it.

---

