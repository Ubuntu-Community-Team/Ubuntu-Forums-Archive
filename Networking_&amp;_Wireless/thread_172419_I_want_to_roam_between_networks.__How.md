---
title: "I want to roam between networks.  How?"
date: 2006-05-08
forum: Networking &amp; Wireless
---

### Post by Kensey on 2006-05-08
I have fairly detailed networking desires, and I want Ubuntu to do everything for me :)

* When I start up my laptop with a wired interface marked to be activated and configured by DHCP in Network Manager, but no cable is actually plugged in, my laptop waits for DHCP to time out before it continues booting.  I want Ubuntu to be smart enough to recognize "hey, nothing's plugged in there, let's ignore it until something is."  As I understand it this is what ifplugd is for, but how does that interact with the existing tools (and see below about wireless issues)?

* When I start up in an area with unsecured wireless networks where none of the networks I usually use are visible, I get what looks like the same waiting-for-DHCP hang.  This appears to be because the wireless tools select and associate with an unsecured network, but wpa_supplicant doesn't know about it and causes issues -- if I run iwconfig I see an association, but `dhclient eth1' never gets a response, and configuring manually doesn't work either.  If I shut down wpa_supplicant and rerun dhclient or configure manually, everything works beautifully.  So, I want wpa_supplicant to recognize when it's got nothing to do and allow association to unsecured networks whether or not it explicitly knows about them.  Ideally it would allow me to manually choose an unsecured/unknown network to associate to via other tools even if it has already automatically associated to a network it knows about.  This seems to be a particularly thorny issue, and I've seen reference to a tool called waproamd that handled this intuitively but now appears to be abandoned.

* Sometimes Network Manager takes an inordinately long time to do simple things like bring an interface up.  I've seen it hang for as long as what seems like a full two minutes just trying to bring up a DHCP-configured, wired interface.  Once I actually brought it up and added it as default route manually while waiting on NM, and it worked until NM "finished", at which point I had to (as I recall) fix the routing table manually to get it to work again.  Is this a known issue, and if so does a simple fix exist?

---

