---
title: "Unable to stay associated to a wifi access point"
date: 2010-04-11
forum: Networking &amp; Wireless
---

### Post by ldardini on 2010-04-11
Hello,
yesterday I discovered I can no more associate to my access point using wpa key. This happened not only to my laptop, but also to my laptop wife. We got the same error on the access point (running OpenWRT). These two laptops are completely updated to the latest deb archive and running karmic.

Apr 11 18:38:54 OpenWrt daemon.info hostapd: ath0: STA 00:13:ce:f2:d1:9e IEEE 802.11: associated
Apr 11 18:38:54 OpenWrt daemon.info hostapd: ath0: STA 00:13:ce:f2:d1:9e WPA: received EAPOL-Key 2/4 Pairwise with unexpected replay counter
Apr 11 18:38:57 OpenWrt daemon.info hostapd: ath0: STA 00:13:ce:f2:d1:9e IEEE 802.11: deauthenticated due to local deauth request
Apr 11 18:38:57 OpenWrt daemon.info hostapd: ath0: STA 00:13:ce:f2:d1:9e IEEE 802.11: disassociated
Apr 11 18:38:57 OpenWrt daemon.info hostapd: ath0: STA 00:13:ce:f2:d1:9e IEEE 802.11: associated
Apr 11 18:38:57 OpenWrt daemon.info hostapd: ath0: STA 00:13:ce:f2:d1:9e WPA: received EAPOL-Key 2/4 Pairwise with unexpected replay counter
Apr 11 18:39:00 OpenWrt daemon.info hostapd: ath0: STA 00:13:ce:f2:d1:9e IEEE 802.11: deauthenticated due to local deauth request
Apr 11 18:39:00 OpenWrt daemon.info hostapd: ath0: STA 00:13:ce:f2:d1:9e IEEE 802.11: disassociated
Apr 11 18:39:01 OpenWrt daemon.info hostapd: ath0: STA 00:13:ce:f2:d1:9e IEEE 802.11: associated
Apr 11 18:39:01 OpenWrt daemon.info hostapd: ath0: STA 00:13:ce:f2:d1:9e WPA: received EAPOL-Key 2/4 Pairwise with unexpected replay counter
Apr 11 18:39:04 OpenWrt daemon.info hostapd: ath0: STA 00:13:ce:f2:d1:9e IEEE 802.11: deauthenticated due to local deauth request
Apr 11 18:39:04 OpenWrt daemon.info hostapd: ath0: STA 00:13:ce:f2:d1:9e IEEE 802.11: disassociated
Apr 11 18:39:05 OpenWrt daemon.info hostapd: ath0: STA 00:13:ce:f2:d1:9e IEEE 802.11: associated
Apr 11 18:39:05 OpenWrt daemon.info hostapd: ath0: STA 00:13:ce:f2:d1:9e WPA: received EAPOL-Key 2/4 Pairwise with unexpected replay counter
Apr 11 18:39:08 OpenWrt daemon.info hostapd: ath0: STA 00:13:ce:f2:d1:9e IEEE 802.11: deauthenticated due to local deauth request
Apr 11 18:39:08 OpenWrt daemon.info hostapd: ath0: STA 00:13:ce:f2:d1:9e IEEE 802.11: disassociated
Apr 11 18:39:09 OpenWrt daemon.info hostapd: ath0: STA 00:13:ce:f2:d1:9e IEEE 802.11: associated

I tried with my son laptop he rarely used and it works. It was running Ubuntu-remix. This laptop was last updated two weeks ago.

I tried dual booting my laptop with Windows and it works.

I believe one of the latest update kicks in some incompatibility.

Leandro

---

