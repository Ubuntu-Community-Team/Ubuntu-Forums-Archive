---
title: "Wireless troubles with Linksys WUSB54GC and Karmic"
date: 2010-04-26
forum: Networking &amp; Wireless
---

### Post by DaveAU on 2010-04-26
Hi,

I've got a Linksys WUSB54GC wireless adapter that worked flawlessly with Jaunty.

I'm using /etc/network/interfaces and wpa_supplicant since the original posts I read about getting WPA going with USB adaptors recommended against working with Network Manager (which my experience in the 20-30 minutes I tried stuff before I plugged my wired network in and found those posts).

Anyhow, from that point on I had no troubles.  A few weeks back I upgraded to Karmic.  Now the network randomly drops out, usually 2-3 times and hour and much more regularly if there's heavy or highly varying network load.

The output of iwconifg shows that the link has gone from associated to not-associated, and dmesg gives me
```
[29354.891300] wlan0: no probe response from AP 00:19:5b:99:97:b8 - disassociating
```

Relevant bit of /etc/network/interfaces:
```

auto wlan0
iface wlan0 inet dhcp
wireless-essid MYSSIDNAME
wireless-channel 6
wireless-mode managed
pre-up wpa_supplicant -B -D wext -i wlan0 -c /etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant
```

And /etc/wpa_supplicant.conf:
```
ctrl_interface=/var/run/wpa_supplicant

network={
        ssid="DavesPlace"
        proto=WPA
        key_mgmt=WPA-PSK
        psk=BIGPSKSTRING...
}
```

For good measure, uname -a gives:
```
Linux dantes 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 04:38:19 UTC 2010 x86_64 GNU/Linux
```

I'm not entirely sure, but my link level seems to be down a bit as well.

Does anyone know what's going on or what I should try to gather further information?

I've seen a few posts by people in similar situations, but the only people who seem to be getting anywhere are those affected by the Atheros troubles.

---

