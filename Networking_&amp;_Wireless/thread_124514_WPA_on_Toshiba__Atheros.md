---
title: "WPA on Toshiba / Atheros"
date: 2006-02-01
forum: Networking &amp; Wireless
---

### Post by aseem_mal on 2006-02-01
Hi Toshiba Laptop owners. This may be a little OT, but its for any Toshiba owner using Ubuntu and Wireless internet.
I recently installed Ubuntu 5.10 on my Toshiba Satellite A75 with built in Atheros wifi. My wireless network works fine with no encryption. But if I enable encryption, WEP or WPA, it doesn't work.
I have tried all kinds of things, including wpa_supplicant. I followed all the steps, but Nothing is working. :confused: 
Any help from someone who has done this successfully will be a big help. I wonder isn't there a simple gui based utility, not terminal based, where I can simply enter my SSID and my pass-phrase, and be connected. Just like the Config Free of windows. I wish. :-k

---

### Post by Lambert on 2006-02-02
No gui that I know of for wpa but network-manager is getting close so it's on it's way.

[http://madwifi.org/wiki/UserDocs/802.11i](http://madwifi.org/wiki/UserDocs/802.11i)

You don't need to compile wpasupplicant as there is a version in the repos, but maybe the rest of the link will help you set up. There are also docs on the wiki, you can check the wifidocs link in my signature

If you use wep what kind of settings? I suggest an open key with hexadecimal format

Here is my /etc/network/interfaces file using wep with open/hex key

auto ath0
iface ath0 inet dhcp
wireless-essid xxx
wireless-key xxxxxxxxxx
wireless-mode managed

---

