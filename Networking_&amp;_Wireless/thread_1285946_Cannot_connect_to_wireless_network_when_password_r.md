---
title: "Cannot connect to wireless network when password required"
date: 2009-10-08
forum: Networking &amp; Wireless
---

### Post by edmund on 2009-10-08
Since upgrading to Jaunty 9.04, I am unable to connect to wireless networks which require a password.
Here are things which DO work:
- connecting to a wireless network using Windows XP
- connecting to a wireless network (with or without a password) in 8.10 before I upgraded
- connecting to an unsecured wireless network in 9.04 (i.e. when no password is required) 

I am using Broadcom and ndiswrapper.
I am using wicd, which shows the network, and has the correct passphrase in Advanced Settings, but always displays 'Not connected' after I click on 'Connect'.

Output from 'iwconfig', 'lshw -C Network', 'ndiswrapper -l' all look good to me, though I am no expert.
Any help would be so much appreciated,
Edmund

---

### Post by bahamut920 on 2009-10-08
I'm having a very similar problem.  I'm using ndiswrapper to use a Netgear WG311v3 PCI card on Ubuntu 9.04, and whenever I try to access a secured network, the connection manager simply doesn't do anything for a while, whereuopn it asks me again for the WPA passphrase.  After two or three repetitions, it gives up entirely.

---

### Post by edmund on 2009-11-22
Yes! At last!    How I fixed it:

Open wicd, then
Preferences / Advanced Settings
Change WPA Supplicant Driver from ndiswrapper to wext.

I had to click on "Connect" to the wifi network 3 times before it connected - the first 2 times it connected then immediately disconnected.

Maybe the WPA Supplicant Driver was wrongly set because the upgrade to 9.04 replaced ndiswrapper with a better driver, but didn't update this setting, but that's pure speculation.  Anyway, it now works!

---

