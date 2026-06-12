---
title: "Ubuntu 10.10 Won't connect using both 802.11n &amp; Security"
date: 2011-05-05
forum: Networking &amp; Wireless
---

### Post by grogling on 2011-05-05
I am having a rather strange problem getting Ubuntu to connect to my brand new Netcomm NP124 wireless access point.

What I have established is there is only a problem when I am trying to use 802.11n & security. If i switch on 802.11g (in only or mixed modes) it will connect at 54mbps perfectly irrelivent of what securty is enabled.

It will also connect perfectly in 'n' mode if security is switched off on the access point. It only appears to be the combination of the two that causes the problems.

The problem is, I put in the key to connect and it just sits there trying to connect and eventually comes back asking for the key again. I have also tried using Wicd instead of Network Manager with no more success.

Also of note, if I boot the machine into Windows, there is no such problem.

Access Point : Netcomm NP124
Netbook      : Asus EeePC T101MT
Ubuntu       : Desktop Edition 10.10
Kernel       : 2.6.35-24-generic x86_64
Wireless card: Atheros AR9285

If anybody can suggest anything that may be stopping this from working, it would be really appriciated.

---

### Post by grogling on 2011-05-05
Not quite solved, but I have a workaround.

The Access Point's default encryption is TKIP, as soon as I changed that to AES or TKIP/AES everything connected properly. Is there some reason for this, does Ubuntu not support TKIP is it indeed a bug?

Still doesn't explain why it all works using 802.11g. Also doesn't explain why WEP doesn't work either.

---

