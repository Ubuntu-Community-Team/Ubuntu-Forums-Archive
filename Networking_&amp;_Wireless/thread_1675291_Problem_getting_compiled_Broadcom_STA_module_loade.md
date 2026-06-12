---
title: "Problem getting compiled Broadcom STA module loaded"
date: 2011-01-25
forum: Networking &amp; Wireless
---

### Post by Diskdoc on 2011-01-25
Hi!

I'm having trouble getting WPA-support working properly in Lucid, as per my [reported bug]("https://bugs.launchpad.net/ubuntu/+bug/707297"). Downloaded the Linux Broadcom STA driver source from [here]("http://www.broadcom.com/support/802.11/linux_sta.php") and tried to compile.

Compilation went ok, installed the module but when trying to load it I get:

[I]root@barbar9:~# modprobe wl
FATAL: Error inserting wl (/lib/modules/2.6.32-27-generic/kernel/drivers/net/wireless/wl.ko): Unknown symbol in module, or unknown parameter (see dmesg)[/I]

In dmesg I see this:

[I][  200.604438] lib80211: common routines for IEEE802.11 drivers
[  200.604453] lib80211_crypt: registered algorithm 'NULL'
[  200.618508] wl: disagrees about version of symbol lib80211_get_crypto_ops
[  200.618514] wl: Unknown symbol lib80211_get_crypto_ops
[/I]

Can anyone give me some help on this?

--- *later*

Nevermind..seems I've messed something up on this particular laptop that causes this problem.

---

