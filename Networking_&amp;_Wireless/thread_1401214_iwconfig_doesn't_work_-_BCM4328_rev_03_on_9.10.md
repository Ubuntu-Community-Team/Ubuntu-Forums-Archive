---
title: "iwconfig doesn't work - BCM4328 rev 03 on 9.10"
date: 2010-02-07
forum: Networking &amp; Wireless
---

### Post by tetsu on 2010-02-07
Hi,

My wireless hardware is the BCM4328 rev 03, and I'm using Broadcom STA driver (wl)
on Ubuntu 9.10 (i686 2.6.31-17-generic).
I'd like to use this with WEP, but iwconfig doesn't work correctly.

"# iwlist eth1 scan ESSID" work correctly, but "# iwconfig eth1 essid ESSID key s:KEY open" doesn't work.
I checked the command result by "# iwconfig eth1", but ESSID didn't set.

Please, somebody advise me?
Thanks.
--
tetsu

---

### Post by chili555 on 2010-02-07
Manual configuration; that is, with iwconfig, doesn't work and play well with Network Manager. NM will only set the ESSID, etc. when it has successfully connected to an access point. Have you tried to click the NM icon and connect?

---

### Post by tetsu on 2010-02-07
Thank you for the reply.

At first, I used nm-connection-editor, and set-up ESSID, and WEP.
But it didn't work well, so, I manually used iwconfig.

I also tried iwconfig after stopping the NM by "# service network-manager stop",
but the result is the same.

I also noticed that lib80211_crypt_wep module hadn't loaded, and manually loaded.
(lib80211_crypt_tkip is loaded...)
--
tetsu

---

