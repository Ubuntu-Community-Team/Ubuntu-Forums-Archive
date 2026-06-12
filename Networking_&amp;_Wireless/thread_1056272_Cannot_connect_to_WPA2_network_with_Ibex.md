---
title: "Cannot connect to WPA2 network with Ibex"
date: 2009-01-31
forum: Networking &amp; Wireless
---

### Post by ktneely on 2009-01-31
I have not been able to connect my Ubuntu 8.10 laptop to my home wireless network that is running WPA2 (with WPA failback) when running Ibex.  When I boot a Hardy 8.04 LiveCD, I can connect just fine, but Ibex does not work.  It asks for the passphrase, thinks a while, then rejects it asking again

The access point is a Juniper Networks Netscreen 5GT.

Here is what I have tested:

Thinkpad T43:
Ibex (installed): not working
Ibex (liveCD): not working
Hardy (liveCD): working

Thinkpad T42:
Ibex (upgrade from Hardy): not working
Hardy (liveCD): working.

any ideas how to get this working?  The Ibex installs work fine with other wireless networks (open, WEP, etc) but not my home WPA2 network.

---

### Post by Reiger on 2009-01-31
The problem is in the difference between PSK (Pre Shared Key) and Passphrase. Apparently, the network manager tool (and hence, the gnome/kde gui frontends you see in the systray) treat the former as if it were the latter -- which means they keep attempting to connect using rehash of the actual 'key', or so it did for me. For me, the easy solution was to ditch network manager and use a different one instead like [wicd]("http://wicd.sourceforge.net/").

---

### Post by ktneely on 2009-01-31
Amazing, thank you!  After installing wicd, I didn't even have to re-enter my passphrase.  It immediately connected using the (correct) one I had told the default network-manager.

---

