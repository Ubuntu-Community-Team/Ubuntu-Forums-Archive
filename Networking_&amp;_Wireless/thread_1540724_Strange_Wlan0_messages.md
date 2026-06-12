---
title: "Strange Wlan0 messages"
date: 2010-07-28
forum: Networking &amp; Wireless
---

### Post by Mduke on 2010-07-28
Hi, I'm really not sure if it's anything to be concerned about as when it comes to things like this I have practically no knowledge, but I can't say I've ever seen these messages before and I'm not sure if I should be concerned or if there are any problems.

Daemon log:
Jul 28 00:38:14 jack-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> disconnected
Jul 28 00:38:14 jack-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jul 28 00:38:14 jack-desktop wpa_supplicant[984]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Jul 28 00:38:14 jack-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Jul 28 00:38:16 jack-desktop wpa_supplicant[984]: Associated with zz:zz:zz:zz:zz
Jul 28 00:38:16 jack-desktop wpa_supplicant[984]: CTRL-EVENT-CONNECTED - Connection to zz:zz:zz:zz:zz:zz  completed (reauth) [id=0 id_str=]
Jul 28 00:38:16 jack-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> associated
Jul 28 00:38:16 jack-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> completed

Kern log:
Jul 28 00:38:14 jack-desktop kernel: [120928.792604] wlan0: deauthenticated (Reason: 7)
Jul 28 00:38:16 jack-desktop kernel: [120930.798786] wlan0: direct probe to AP zz:zz:zz:zz:zz:zz try 1
Jul 28 00:38:16 jack-desktop kernel: [120930.801042] wlan0 direct probe responded
Jul 28 00:38:16 jack-desktop kernel: [120930.801060] wlan0: authenticate with AP zz:zz:zz:zz:zz:zz
Jul 28 00:38:16 jack-desktop kernel: [120930.808711] wlan0: authenticated
Jul 28 00:38:16 jack-desktop kernel: [120930.808730] wlan0: associate with AP zz:zz:zz:zz:zz:zz
Jul 28 00:38:16 jack-desktop kernel: [120930.822980] wlan0: RX ReassocResp from zz:zz:zz:zz:zz:zz (capab=0x431 status=0 aid=1)

I'm fairly sure I've never seen these messages before today, there are a couple others pretty much just like that which are hours apart.

So is this some kind of driver problem or something else or something to not even be at all concerned about?

Had to add z's for the AP cause it wanted to make a ton of smilies.

---

### Post by lisati on 2010-07-28
> **Mduke said:**
> 
Had to add z's for the AP cause it wanted to make a ton of smilies.
Try the [noparse][noparse][/noparse] works a treat to avoid the smileys, and [noparse]```

```[/noparse] works a treat for the formatting.

---

