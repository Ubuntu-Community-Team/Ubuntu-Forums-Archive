---
title: "knetworkmanager in 10.10 - hidden ssid?"
date: 2010-12-29
forum: Networking &amp; Wireless
---

### Post by Kiesel on 2010-12-29
Hi,
im trying to connect to an ap with a hidden ssid, but i failed up till now. I can input the credentials and the network name, but i cant find any method to persuade knetworkmanager to start connecting.
Im not the admin so i cannot change the ssid to visible and i would like to stay with knetworkmanager.
So is this yet possible, or do i need to file a bug report?
Greetz, Kiesel

---

### Post by clb92 on 2011-02-10
I have the same problem...

Found this thread. Don't know if it'll help...

[http://kubuntuforums.net/forums/index.php?topic=3110265.0](http://kubuntuforums.net/forums/index.php?topic=3110265.0)

---

### Post by jarl on 2012-08-15
I had the same problem.

I found a workaround on this post:
[http://forums.opensuse.org/english/get-technical-help-here/wireless/452093-hidden-ssid-wifi-11-3-kde-networkmanager.html#post2272375](http://forums.opensuse.org/english/get-technical-help-here/wireless/452093-hidden-ssid-wifi-11-3-kde-networkmanager.html#post2272375)

So if your hidden SSID is "MyHiddenWLAN" you can trigger knetworkmanager to show it by doing this in the console:

[FONT="Courier New"][SIZE="4"]sudo iwlist wlan0 scanning essid MyHiddenWLAN[/SIZE][/FONT]

I hope this helps.

It is definitely a bug in knetworkmanager.

---

