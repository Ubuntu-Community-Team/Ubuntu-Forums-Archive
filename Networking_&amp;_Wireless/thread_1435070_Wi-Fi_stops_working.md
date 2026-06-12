---
title: "Wi-Fi stops working"
date: 2010-03-21
forum: Networking &amp; Wireless
---

### Post by aneganov on 2010-03-21
Hi all,

I experience strange problems with Wi-Fi on my laptop with Ubuntu 9.10: sometimes (about once per 2-3 days) Wi-Fi lost all networks - list of wireless networks in NM applet becomes empty.

"Restarting" wi-fi by pressing a button on laptop doesn't fix problem.
Restarting network-manager or networking doesn't help too.

Solution - restarting Ubuntu, which is definitely not an option.
Today I found one more solution, less stupid but still weird - manual modules reload:

rmmod iwlangn
rmmod iwlcore
rmmod mac80211

modprobe iwlangn
modprobe iwlcore
modprobe mac80211

1) Is there an utility which reloads modules?
2) Why this may happen?

Laptop: 
Acer Aspire 5930G

lspci: 
03:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100

---

### Post by seemore on 2010-03-22
I have the same problem with my Toshiba Lap top, wireless periodically drops out and I need to reboot.

Karmic 9.10


• Integrated Wi-Fi compliant wireless:
                ®
      o Atheros 802.11 b/g wireless-LAN

---

### Post by aneganov on 2010-03-26
Hi,

I've just experienced same fail again - wifi lost connection and couldn't reestablish conection. I looked into syslog and saw this:

```
Mar 26 14:45:33 fantomas-laptop wpa_supplicant[1115]: CTRL-EVENT-SCAN-RESULTS 
Mar 26 14:45:33 fantomas-laptop kernel: [45187.788180] iwlagn 0000:03:00.0: No space for Tx
Mar 26 14:45:33 fantomas-laptop kernel: [45187.788185] iwlagn 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
Mar 26 14:45:33 fantomas-laptop kernel: [45187.788188] iwlagn 0000:03:00.0: Error setting new RXON (-28)
Mar 26 14:45:33 fantomas-laptop kernel: [45187.788207] iwlagn 0000:03:00.0: No space for Tx
Mar 26 14:45:33 fantomas-laptop kernel: [45187.788209] iwlagn 0000:03:00.0: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
Mar 26 14:45:33 fantomas-laptop kernel: [45187.788224] iwlagn 0000:03:00.0: No space for Tx
Mar 26 14:45:33 fantomas-laptop kernel: [45187.788226] iwlagn 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
Mar 26 14:45:33 fantomas-laptop kernel: [45187.788228] iwlagn 0000:03:00.0: Error setting new RXON (-28)
Mar 26 14:45:33 fantomas-laptop kernel: [45187.788231] iwlagn 0000:03:00.0: No space for Tx
Mar 26 14:45:33 fantomas-laptop kernel: [45187.788233] iwlagn 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
Mar 26 14:45:33 fantomas-laptop kernel: [45187.788235] iwlagn 0000:03:00.0: Error setting new RXON (-28)
Mar 26 14:45:33 fantomas-laptop kernel: [45187.788242] iwlagn 0000:03:00.0: No space for Tx
Mar 26 14:45:33 fantomas-laptop kernel: [45187.788244] iwlagn 0000:03:00.0: Error sending REPLY_TX_POWER_DBM_CMD: enqueue_hcmd failed: -28
Mar 26 14:45:33 fantomas-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Mar 26 14:45:38 fantomas-laptop wpa_supplicant[1115]: CTRL-EVENT-SCAN-RESULTS 
Mar 26 14:45:38 fantomas-laptop kernel: [45192.793050] iwlagn 0000:03:00.0: No space for Tx
Mar 26 14:45:38 fantomas-laptop kernel: [45192.793054] iwlagn 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
Mar 26 14:45:38 fantomas-laptop kernel: [45192.793057] iwlagn 0000:03:00.0: Error setting new RXON (-28)
Mar 26 14:45:38 fantomas-laptop kernel: [45192.793078] iwlagn 0000:03:00.0: No space for Tx
Mar 26 14:45:38 fantomas-laptop kernel: [45192.793081] iwlagn 0000:03:00.0: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
Mar 26 14:45:38 fantomas-laptop kernel: [45192.793095] iwlagn 0000:03:00.0: No space for Tx
Mar 26 14:45:38 fantomas-laptop kernel: [45192.793097] iwlagn 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
Mar 26 14:45:38 fantomas-laptop kernel: [45192.793099] iwlagn 0000:03:00.0: Error setting new RXON (-28)
Mar 26 14:45:38 fantomas-laptop kernel: [45192.793102] iwlagn 0000:03:00.0: No space for Tx
Mar 26 14:45:38 fantomas-laptop kernel: [45192.793105] iwlagn 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
Mar 26 14:45:38 fantomas-laptop kernel: [45192.793107] iwlagn 0000:03:00.0: Error setting new RXON (-28)
Mar 26 14:45:38 fantomas-laptop kernel: [45192.793112] iwlagn 0000:03:00.0: No space for Tx
Mar 26 14:45:38 fantomas-laptop kernel: [45192.793115] iwlagn 0000:03:00.0: Error sending REPLY_TX_POWER_DBM_CMD: enqueue_hcmd failed: -28
Mar 26 14:45:43 fantomas-laptop wpa_supplicant[1115]: CTRL-EVENT-SCAN-RESULTS 
Mar 26 14:45:43 fantomas-laptop kernel: [45197.801052] iwlagn 0000:03:00.0: No space for Tx
Mar 26 14:45:43 fantomas-laptop kernel: [45197.801058] iwlagn 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
Mar 26 14:45:43 fantomas-laptop kernel: [45197.801061] iwlagn 0000:03:00.0: Error setting new RXON (-28)
Mar 26 14:45:43 fantomas-laptop kernel: [45197.801082] iwlagn 0000:03:00.0: No space for Tx
Mar 26 14:45:43 fantomas-laptop kernel: [45197.801085] iwlagn 0000:03:00.0: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
Mar 26 14:45:43 fantomas-laptop kernel: [45197.801101] iwlagn 0000:03:00.0: No space for Tx
Mar 26 14:45:43 fantomas-laptop kernel: [45197.801103] iwlagn 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
Mar 26 14:45:43 fantomas-laptop kernel: [45197.801105] iwlagn 0000:03:00.0: Error setting new RXON (-28)
Mar 26 14:45:43 fantomas-laptop kernel: [45197.801108] iwlagn 0000:03:00.0: No space for Tx
Mar 26 14:45:43 fantomas-laptop kernel: [45197.801110] iwlagn 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
Mar 26 14:45:43 fantomas-laptop kernel: [45197.801113] iwlagn 0000:03:00.0: Error setting new RXON (-28)
Mar 26 14:45:43 fantomas-laptop kernel: [45197.801118] iwlagn 0000:03:00.0: No space for Tx
Mar 26 14:45:43 fantomas-laptop kernel: [45197.801121] iwlagn 0000:03:00.0: Error sending REPLY_TX_POWER_DBM_CMD: enqueue_hcmd failed: -28
etc...

```

The essential part of messages I believe are these three:
iwlagn: No space for Tx
iwlagn: Error sending REPLY_RXON: enqueue_hcmd failed: -28
iwlagn: Error setting new RXON (-28)

I rmmod/modprobe'ed iwlagn module and it started to work. Conclusion - iwlagn is buggy.

---

### Post by tedrampart on 2010-03-27
yea I'm also seeing something similar, haven't checked the logs though, but I will next time it happens.

I find mine seems to mostly happen after a suspend/resume, but has happened inadvertantly if I recall correctly.. same thing applies, reloading the iwlagn module and restarting networking service gets me back up and running without a reboot.

it was working well til the latest kernel updates.

---

