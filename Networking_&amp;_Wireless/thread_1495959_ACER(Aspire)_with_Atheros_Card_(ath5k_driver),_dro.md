---
title: "ACER(Aspire) with Atheros Card (ath5k driver), drops connection with High Bandwidth"
date: 2010-05-28
forum: Networking &amp; Wireless
---

### Post by hryanjones on 2010-05-28
**Machine & OS details:**
[LIST]
[*]Acer Aspire 1 ZG5
[*]AR5001 Wireless Network Adapter
[*]Driver=ath5k
[*]Ubuntu Netbook Remix 10.04 (upgraded from 9.10, no problem then)
[/LIST]

**The problem:**  On using a lot of bandwidth (e.g. transferring a large file over the local network, or downloading big files {>3MB} & perusing Google Maps, etc), my wireless connection drops & takes a minute or two to reconnect itself.  Trying to troubleshoot through the system log I found the first few messages after the drop are as follows:

May 28 13:16:47 jones-netbook kernel: [ 4780.588657] wlan0: deauthenticated from 00:14:6c:99:83:70 (Reason: 14)
May 28 13:16:47 jones-netbook wpa_supplicant[909]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
May 28 13:16:47 jones-netbook NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> disconnected
May 28 13:16:47 jones-netbook NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning

I've been unable to find any help from the interwebs on what Reason 14 means when wlan0 is deauthenticated from the MAC address of my Netgear router.

Any clues or leads would be super greatly appreciated.

Thanks,
Ryan

---

