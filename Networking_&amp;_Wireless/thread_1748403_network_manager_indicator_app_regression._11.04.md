---
title: "network manager indicator app regression. 11.04"
date: 2011-05-03
forum: Networking &amp; Wireless
---

### Post by credomane on 2011-05-03
In 10.04 and 10.10 I was able to split my wireless networks into groups. In 11.04 the groups still show up in the edit connection list but when I connect to one none of them are available.

My work network is split into a few vlans decided by your ip. This is to keep IP phone traffic and Camera traffic separate from everything else.

I discovered, by luck, in 10.04 that I could name my wireless connections similarly to turn them into a menu.
Naming my wireless connections like this:
[LIST]
[*]work - phones
[*]work - cameras
[*]work - static
[*]work - dhcp
[*]home - static
[*]home - dhcp
[/LIST]
Would turn into this in the network-manager app menu.
[LIST]
[*][signal_level/encryption ssid]  home >[LIST]
[*]dhcp
[*]static
[/LIST]
[*][signal_level/encryption ssid]  work >[LIST]
[*]cameras
[*]dhcp
[*]phones
[*]static
[/LIST]
[/LIST]

Now in 11.04 when I open the network-manager app menu All i see for wireless is
[signal_level/encryption ssid]
Which corresponds to the "auto [ssid]" wireless connection in the network-manager edit connections dialog. I've been able to work around the problem by editing the "auto [ssid]" connection to the network I need to be on but is it a hassle. Before it was literally all of 2 seconds to switch networks now I'm back to wasting 2-3 minutes manually swapping IP info.

Anyone know what is going on here?

---

