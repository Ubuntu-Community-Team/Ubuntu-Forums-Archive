---
title: "ndiswrapper or madwifi"
date: 2009-10-14
forum: Networking &amp; Wireless
---

### Post by dvdljns on 2009-10-14
Something strange is going on. I am trying to set up wg311v3 wireless card. I tried on ubuntu 5.10,606,610,8.04,9.04. I got the same error. Couldn't copy /drivers/wg311v3.inf at /usr/sbin/ndiswrapper line 135. But it did install the driver.
ndiswrapper -l tells me I have wg311v3 but claims it is the wrong driver. doing lspci finds a 88w8335 chip. So google tells me me marvel makes drivers for that chipset. So downloading the marvel drivers for marvel 88w8335 and installing them with ndiswrapper is no problem. They install with no errors. But when I try to set up wlan I am told I need madwifi utils installed.
Anybody have a clue whats going on. I am working on ubuntu 7.04 with the ndiswrapper and ndis utils out of dapper. (could not find anything else that would install on 7.04) I need the mad wifi utils that is in dapper. The ones I down loaded are from hardy and depend on libc6 2.6, I have libc6 2.5 I all ready know from trying with ndiswrapper utils the conflicts with 2.6 and tzdata or unresolveable. To change tzdata I have to do a distro upgrade that puts me back to a distro that I can not get the drivers to work.

Any body have an answer to this.

---

