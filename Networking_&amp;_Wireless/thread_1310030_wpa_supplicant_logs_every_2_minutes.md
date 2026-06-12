---
title: "wpa_supplicant logs every 2 minutes"
date: 2009-11-01
forum: Networking &amp; Wireless
---

### Post by edantes on 2009-11-01
I just installed 9.10 from scratch in a system using a wifi adaptor Atheros AR5001X+ (AR2414 chipset). Ubuntu 9.10 automatically assigns to it the ath5k driver. With 9.04 this combination was problematic resulting in frequent crashes solved when I switched to the madwifi driver. Madwifi is not available with 9.10.

I had one unexplained crash in the 48 hours I've been running 9.10. Examining the syslog, I noticed a message from wpa_supplicant every 2 minutes. Other than that one crash, the system seems to be running fine.

Is the wpa_supplicant insistence a problem in itself? A bug?
Should I go back  to madwifi? (I noticed instructions on how to install it in this area of the forum)

Here is a sample from syslog:

-----
Nov 1 12:48:37 ggv-desktop wpa_supplicant[1387]: CTRL-EVENT-SCAN-RESULTS
Nov 1 12:50:36 ggv-desktop wpa_supplicant[1387]: CTRL-EVENT-SCAN-RESULTS
Nov 1 12:52:36 ggv-desktop wpa_supplicant[1387]: CTRL-EVENT-SCAN-RESULTS
Nov 1 12:54:36 ggv-desktop wpa_supplicant[1387]: CTRL-EVENT-SCAN-RESULTS
Nov 1 12:56:36 ggv-desktop wpa_supplicant[1387]: CTRL-EVENT-SCAN-RESULTS
Nov 1 12:58:36 ggv-desktop wpa_supplicant[1387]: CTRL-EVENT-SCAN-RESULTS
Nov 1 13:00:36 ggv-desktop wpa_supplicant[1387]: CTRL-EVENT-SCAN-RESULTS
Nov 1 13:02:37 ggv-desktop wpa_supplicant[1387]: CTRL-EVENT-SCAN-RESULTS
Nov 1 13:04:36 ggv-desktop wpa_supplicant[1387]: CTRL-EVENT-SCAN-RESULTS

---

### Post by kevdog on 2009-11-01
I think the wpa_supplicant is scanning for APs.  Im not sure how to disable this feature if running network manager (although Im sure its possible), however I do know a way to disable this feature if connecting manually with a "custom" wpa_supplicant.conf file.

---

### Post by edantes on 2009-11-01
Thanks for your reply. I am still unsure if this behavior is by design.  Is it necessary to scan for access-points this often or flood the log file.

---

### Post by kevdog on 2009-11-01
What log are you looking in?

---

### Post by edantes on 2009-11-01
Rain or shine, even if system is left unattended,  wpa_supplicant enters every 2 minutes a single line at /var/log/syslog.  Like this example:

> Nov  2 00:23:12 ggv-desktop wpa_supplicant[1307]: CTRL-EVENT-SCAN-RESULTS 

---

### Post by mr19 on 2009-11-03
I'm seeing the same thing.  Side effect seems to be my network cxn freezing for 5 secs or so every time it happens.   Rather annoying.

---

### Post by mr19 on 2009-11-03
Not sure when this freezing started, don't remember it the other day, but it sure is a pain to work in 2 minute chunks, then stop for 10 secs.

---

### Post by Tritonio on 2009-11-08
I have the same "problem" but it doesn't seem to block my connection when it happens. It just floods my syslog.

I also get these messages in syslog if they are related:
```
Nov  8 16:06:53 Sonia wpa_supplicant[1499]: CTRL-EVENT-SCAN-RESULTS 
Nov  8 16:08:53 Sonia wpa_supplicant[1499]: CTRL-EVENT-SCAN-RESULTS 
Nov  8 16:10:53 Sonia wpa_supplicant[1499]: CTRL-EVENT-SCAN-RESULTS 
Nov  8 16:12:53 Sonia wpa_supplicant[1499]: CTRL-EVENT-SCAN-RESULTS 
Nov  8 16:14:53 Sonia wpa_supplicant[1499]: CTRL-EVENT-SCAN-RESULTS 
Nov  8 16:16:23 Sonia kernel: [69925.749746] iwlagn 0000:06:00.0: Microcode SW error detected.  Restarting 0x82000000.
Nov  8 16:16:23 Sonia kernel: [69925.990100] Registered led device: iwl-phy0::radio
Nov  8 16:16:23 Sonia kernel: [69925.990124] Registered led device: iwl-phy0::assoc
Nov  8 16:16:23 Sonia kernel: [69925.990146] Registered led device: iwl-phy0::RX
Nov  8 16:16:23 Sonia kernel: [69925.990166] Registered led device: iwl-phy0::TX
Nov  8 16:16:35 Sonia wpa_supplicant[1499]: WPA: Group rekeying completed with 00:14:bf:99:89:ed [GTK=TKIP]
Nov  8 16:16:35 Sonia NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> group handshake
Nov  8 16:16:35 Sonia NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Nov  8 16:16:55 Sonia wpa_supplicant[1499]: CTRL-EVENT-SCAN-RESULTS 
Nov  8 16:17:02 Sonia CRON[29253]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov  8 16:17:06 Sonia wpa_supplicant[1499]: WPA: Group rekeying completed with 00:14:bf:99:89:ed [GTK=TKIP]
Nov  8 16:17:06 Sonia NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> group handshake
Nov  8 16:17:06 Sonia NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Nov  8 16:17:45 Sonia wpa_supplicant[1499]: WPA: Group rekeying completed with 00:14:bf:99:89:ed [GTK=TKIP]
Nov  8 16:17:45 Sonia NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> group handshake
Nov  8 16:17:45 Sonia NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Nov  8 16:18:53 Sonia wpa_supplicant[1499]: CTRL-EVENT-SCAN-RESULTS 
Nov  8 16:20:00 Sonia wpa_supplicant[1499]: WPA: Group rekeying completed with 00:14:bf:99:89:ed [GTK=TKIP]
Nov  8 16:20:00 Sonia NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> group handshake
Nov  8 16:20:00 Sonia NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Nov  8 16:20:54 Sonia wpa_supplicant[1499]: CTRL-EVENT-SCAN-RESULTS 
Nov  8 16:22:53 Sonia wpa_supplicant[1499]: CTRL-EVENT-SCAN-RESULTS 
```

---

### Post by brian183 on 2009-11-15
I have this same issue where wpa_supplicant does a scan every 2 minutes and my network does freeze for a good solid 5 seconds.  For the most part this doesn't really mess with my day to day work load on my network.  When I attempt to watch streaming video/audio it does.  Nothing is more annoying to me then trying to watch a stream when every two minutes it freezes up and I have to wait a few seconds to continue watching.

So for when I am watching streams I make sure I'm on my LAN and not wireless.  I'd really appreciate a fix for this though.

-brian

---

