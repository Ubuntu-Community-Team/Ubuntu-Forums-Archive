---
title: "Network-manager reports no network adapters but my network is up"
date: 2006-07-04
forum: Networking &amp; Wireless
---

### Post by timrichardson on 2006-07-04
My wifi atheros interface is working (ath0) but the gnome network-manager applet says that there are no adapters. This is a shame because I want to use this interface to configure WPA. Currently I am using WEP, which can be configured in the System->Admin-> Network control panel.

Perhaps the network-manager daemon is not running? I thought that the network-manager daemon would be listed as a service in the Service control panel, but it is not. Obviously I am a newbie. I have read about "dbus" but it has not helped. Some ideas?

---

### Post by Adrian_b on 2006-07-04
I configured my Atheros interface using cli..
'iwconfig ath0 key open -WEPkey-'
'iwconfig ath0 essid -essidname-'
'dhclient'

---

### Post by timrichardson on 2006-07-04
Yeah, I am cool with that ... for WEP. But I am keen to use the nice GUI front end for WPA, which sounds like a PITA to do via the shell.

---

### Post by r1chard on 2006-07-04
Yep I'm stuck finding gnome-network-mangager after installing (using synaptic) it too... also the nm-applet (part of that package) is not available in the list of things I can add to a panel...

-Richard

---

### Post by timrichardson on 2006-07-06
I have it working. Network Manager applet worked for me after installing the package on the live DVD. It should be listed as a start up program under System->Preferences->Sessions
nm-applet should be there; Synaptic sets it up correctly so this is only to verify it.

I think it was not recognising that I had wireless network adapters because I fiddled with /etc/network/interfaces; I removed the wlan0 entry when I shouldn't have. A reinstall of ubuntu fixed it. There are probably smarter ways, but reinstallation is so fst.

---

