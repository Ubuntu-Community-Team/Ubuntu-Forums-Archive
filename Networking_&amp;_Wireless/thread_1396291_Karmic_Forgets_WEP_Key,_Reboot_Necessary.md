---
title: "Karmic Forgets WEP Key, Reboot Necessary"
date: 2010-02-01
forum: Networking &amp; Wireless
---

### Post by vgrisham on 2010-02-01
I'm running 64 bit Karmic Koala on a System76 Pangolin. My wireless card is an Intel Corporation PRO/Wireless 5300 AGN [Shiloh] Network Connection.

Several times per week, I'll be working along just fine wirelessly when suddenly, my wireless connection will drop. Network Manager will attempt to reconnect, but when it does, it has forgotten the WEP key. It prompts me for it, and I enter it, but it will not handshake. If I reboot, it connects back to my wireless access point immediately and needs no reminder of the WEP key.

I am certain that the wireless access point is not the problem. Jaunty never showed this issue, and when it happens on my computer, my wife's Macbook remains connected without issue.

Anyone else seeing this? Tips?

---

### Post by lynysys2 on 2010-02-02
Hi there, glad to have found this thread

I have an identical problem.

I have 64 bit Karmic, using a WEP key (not WPA), my Wifi NIC is:-
03:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100

One workaround that seems to work for me is to Right Click NetworkManager applet and uncheck "Enable Wireless", then check it again.

An alternative to a reboot but still very frustrating !!
I hope others can chime in on their experiences and any other possible workarounds or even a fix :)

--
Luke

---

