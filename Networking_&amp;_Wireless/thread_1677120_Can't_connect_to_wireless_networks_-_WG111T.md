---
title: "Can't connect to wireless networks - WG111T"
date: 2011-01-28
forum: Networking &amp; Wireless
---

### Post by Raiden616 on 2011-01-28
HI All,

Just started using ubuntu yesterday and been working on trying to get my wifi sorted; driving me up the wall, any help would be really appreciated.

I have a NETGEAR WG111T, and am well aware that that particular brand seems to be infamous when it comes to ubuntu. Well, I managed to install the windows drivers for it using ndiswrapper and most recently installed wicd and disabled the default network manager in hopes that might help.

**Currently the situation is this**: I can see all the networks, but cannot connect to them. If I try and connect without any custom settings it just hangs on "Obtaining IP address" and then dies. If I set it up with a static IP address then it instead hangs on the line "Verifying access point connection".

Worth noting, a post on another forum said to comment out the line "self.verify_association(wiface)" in the wicd networking file. If I do that, then instead of hanging on "Verifying access point connection", it goes straight to "Done Connecting", but then says "disconnected" straight away.

Any ideas anyone? Thank you so much in advance.

---

