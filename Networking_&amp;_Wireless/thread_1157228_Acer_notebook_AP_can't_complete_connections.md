---
title: "Acer notebook AP can't complete connections"
date: 2009-05-12
forum: Networking &amp; Wireless
---

### Post by Rhodri James on 2009-05-12
I've given up on trying to make the USB stick work as an AP, and have moved on to an Acer notebook running the madwifi drivers.  I've set it up [exactly specified by Robin]("http://blog.robin.smidsrod.no/index.php/2008/08/08/how_to_setup_an_atheros_based_access_poi") except that the machine is running 8.10 desktop version, and I am totally unclear as to how to stop the NetworkManager from interfering with things.  None the less, the AP appears on network lists once it reboots (usually after a couple of stuck beacons, but that error log doesn't recur).

Trying to connect to it from either a 9.04 desktop or a Windows box, however, fails.  The relevant portion of syslog looks like this:

May 12 18:41:11 indigo hostapd: ath0: STA 00:08:10:71:d6:7a IEEE 802.11: associated
May 12 18:41:11 indigo hostapd: ath0: STA 00:08:10:71:d6:7a WPA: event 1 notification
May 12 18:41:11 indigo hostapd: ath0: STA 00:08:10:71:d6:7a WPA: start authentication
May 12 18:41:11 indigo hostapd: ath0: STA 00:08:10:71:d6:7a IEEE 802.1X: unauthorizing port
May 12 18:41:11 indigo hostapd: ath0: STA 00:08:10:71:d6:7a WPA: sending 1/4 msg of 4-Way Handshake
May 12 18:41:11 indigo hostapd: ath0: STA 00:08:10:71:d6:7a WPA: received EAPOL-Key frame (2/4 Pairwise)
May 12 18:41:11 indigo hostapd: ath0: STA 00:08:10:71:d6:7a WPA: sending 3/4 msg of 4-Way Handshake
May 12 18:41:11 indigo hostapd: ath0: STA 00:08:10:71:d6:7a WPA: received EAPOL-Key frame (4/4 Pairwise)
May 12 18:41:11 indigo hostapd: ath0: STA 00:08:10:71:d6:7a IEEE 802.1X: authorizing port
May 12 18:41:11 indigo hostapd: ath0: STA 00:08:10:71:d6:7a WPA: pairwise key handshake completed (RSN)
May 12 18:41:56 indigo hostapd: ath0: STA 00:08:10:71:d6:7a IEEE 802.11: disassociated
May 12 18:41:56 indigo hostapd: ath0: STA 00:08:10:71:d6:7a WPA: event 2 notification
May 12 18:41:56 indigo hostapd: ath0: STA 00:08:10:71:d6:7a IEEE 802.1X: unauthorizing port
May 12 18:42:13 indigo hostapd: ath0: WPA rekeying GTK

As you can see, the pairwise key exchange seems to complete happily, but the group key handshake mentioned in the article doesn't happen.  I have no clue where to look next, so any advice would be much appreciated.

---

### Post by Rhodri James on 2009-05-13
To answer my own question, I seem to need to configure "wpa=1" instead of "wpa=3".  Neither 9.04 with mac80211 nor the Windows box I tried can handle RSN key exchange, and there was no graceful backoff.

Now I just need to configure my dhcpd properly...

---

