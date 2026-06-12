---
title: "Intel(R) PRO/Wireless 3945ABG/BG - disconnects, can't connect to hidden network, etc"
date: 2010-07-30
forum: Networking &amp; Wireless
---

### Post by 0xd3af on 2010-07-30
Hey,

I'm running Ubuntu 10.04 with kernel 2.6.32-24 on my Dell Inspiron 6400. Since I upgraded my Ubuntu from 9 -> 10.04 I noticed several problems with my wireless network connectivity.

I have hidden wireless network (WPA2-Personal PSK). In Network Manager I have added hidden wireless and checked that it should you this network even if not broadcasting.

So the problem is Ubuntu doesn't automatically connect to this network, I have to manually pick "Connect to the hidden wireless network" - then I takes for about 2-5 minutes to connects. Sometimes I have to repeat that operation 2-3 times to get connected.

Another problem is I randomly lost my connection. Example logs after getting disconnected:

```

[  590.636081] iwl3945 0000:0b:00.0: Error sending REPLY_SCAN_CMD: time out after 500ms.
[  591.136095] iwl3945 0000:0b:00.0: Error sending REPLY_RXON: time out after 500ms.
[  591.136106] iwl3945 0000:0b:00.0: Error setting new configuration (-110).
[  591.638507] iwl3945 0000:0b:00.0: Error sending REPLY_RXON: time out after 500ms.
[  591.638518] iwl3945 0000:0b:00.0: Error setting new configuration (-110).
[  592.136153] iwl3945 0000:0b:00.0: Error sending REPLY_TX_PWR_TABLE_CMD: time out after 500ms.
[  596.140055] iwl3945 0000:0b:00.0: Error sending REPLY_RXON: time out after 500ms.
[  596.140065] iwl3945 0000:0b:00.0: Error setting new configuration (-110).
[  596.642660] iwl3945 0000:0b:00.0: Error sending REPLY_SCAN_CMD: time out after 500ms.

```

Or

```

[  650.425431] wlan0: authenticated
[  650.425467] wlan0: associate with AP 00:1c:f0:ee:f9:31 (try 1)
[  650.429502] wlan0: RX AssocResp from 00:1c:f0:ee:f9:31 (capab=0x431 status=0 aid=3)
[  650.429509] wlan0: associated
[  660.452091] wlan0: deauthenticating from 00:1c:f0:ee:f9:31 by local choice (reason=3)
[  660.469978] wlan0: direct probe to AP 00:1c:f0:ee:f9:31 (try 1)
[  660.473400] wlan0: direct probe responded
[  660.473409] wlan0: authenticate with AP 00:1c:f0:ee:f9:31 (try 1)
[  660.475152] wlan0: authenticated
[  660.475186] wlan0: associate with AP 00:1c:f0:ee:f9:31 (try 1)
[  660.477887] wlan0: RX AssocResp from 00:1c:f0:ee:f9:31 (capab=0x431 status=0 aid=3)
[  660.477894] wlan0: associated
[ 1660.504055] No probe response from AP 00:1c:f0:ee:f9:31 after 500ms, disconnecting.

```

Or

```

[ 1687.512057] iwl3945 0000:0b:00.0: Error setting new configuration (-110).
[ 1687.512082] iwl3945 0000:0b:00.0: No space in command queue
[ 1687.512086] iwl3945 0000:0b:00.0: Restarting adapter due to queue full
[ 1687.512090] iwl3945 0000:0b:00.0: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28

```

Or

```

[ 5243.187729] CE: hpet increasing min_delta_ns to 50624 nsec
[ 5380.529459] CE: hpet increasing min_delta_ns to 75936 nsec
[ 6160.772000] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[ 6174.838991] CE: hpet increasing min_delta_ns to 113904 nsec

```

I'm running following modules:
```

# lsmod | grep iwl
iwl3945                70360  0 
iwlcore               110869  1 iwl3945
mac80211              209734  2 iwl3945,iwlcore
cfg80211              130639  3 iwl3945,iwlcore,mac80211
compat_firmware_class     7043  1 iwl3945

```

Weird thing is I lost my connection almost always when browsing WWW pages with Flash objects.

I have this flash player:
```

# dpkg -l | grep -i flash
ii  adobe-flashplugin                                  10.1.53.64-1lucid1                              Adobe Flash Player plugin version 10
rc  flashplugin-installer                              10.0.45.2ubuntu1                                Adobe Flash Player plugin installer

```

How can I fix my system to get automatically connection with hidden networks, and how about my unstable connectivity? I'm using the same AP with other computers, cellphones, pda's, ipod touch and have no issues.

BTW. My Ubuntu is upgraded and up-to-date.

---

### Post by beastrace91 on 2010-09-24
A friend of mine is having pretty much the exact same issue... (Same wifi card) Did you ever resolve the problem?

~Jeff

---

