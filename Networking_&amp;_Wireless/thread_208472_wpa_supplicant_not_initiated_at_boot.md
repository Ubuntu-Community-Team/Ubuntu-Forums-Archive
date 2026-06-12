---
title: "wpa_supplicant not initiated at boot?"
date: 2006-07-03
forum: Networking &amp; Wireless
---

### Post by quiz000 on 2006-07-03
In order to get my atheros-based pci-card to work, I need to do something like this:

ifdown ath0
wpa_supplicant -i ath0 -c /etc/wpa_supplicant/wpa_supplicant.conf -D madwifi -B -w
ifup ath0

Why?

My /etc/network/interfaces looks like this:

auto lo ath0
iface ath0 inet dhcp

I am not using Network-manager or Wifi-radar


Kim

---

### Post by Agent86 on 2006-07-03
[QUOTE=quiz000]In order to get my atheros-based pci-card to work, I need to do something like this:

ifdown ath0
wpa_supplicant -i ath0 -c /etc/wpa_supplicant/wpa_supplicant.conf -D madwifi -B -w
ifup ath0

Why?

My /etc/network/interfaces looks like this:

auto lo ath0
iface ath0 inet dhcp

I am not using Network-manager or Wifi-radar


Kim[/QUOTE]
Try editing /etc/network/interfaces so the end looks like:```
auto ath0
iface ath0 inet dhcp
wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf
```and rebooting. If that doesn't work, edit /etc/default/wpasupplicant so the only line not commented in it is ```
ENABLED=0
```It's OK if the file doesn't exist, just create a new file with only that line in it.

From what I understand, the wpa_supplicant daemon runs if the interface is if-up'd , but needs to get it's config either from a separate file, or directly in an /etc/network/interfaces stanza. The line we add points to your config file.

---

### Post by Agent86 on 2006-07-03
Oops, put these lines at the top of /etc/network/interfaces```
auto lo
iface lo inet loopback
```So the whole thing looks like```
auto lo
iface lo inet loopback

auto ath0
iface ath0 inet dhcp
wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf
```

---

### Post by StoneMan353 on 2006-07-03
I did this differently, I simply added this line to /etc/rc.local, before the "exit 0"

```
/sbin/wpa_supplicant -Bw -iath0 -Dmadwifi -c/etc/wpa_supplicant.conf
```

That starts the daemon at bootup before dhclient assigns the network address, so I found it was the only line that was required.

---

### Post by quiz000 on 2006-07-04
Thanks for the responses

agent86,

wpa_supplicant seems to be initiated at boot now, but with the wrong configuration. Where do I set this, now that I dont start the program manually anymore?


Kim

---

