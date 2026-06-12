---
title: "Networking disabled after comming out of sleep state"
date: 2009-01-27
forum: Networking &amp; Wireless
---

### Post by Pro_D on 2009-01-27
[edit]
The following appears to have been fixed with a recent update to the linix kernel (2.6.27-11, was using -7).
[/edit]

Searched around a bit and found no help.

Machine is an XPS 1530 with 8.10 Ubuntu recently installed.  All updates up to the time of this post installed.

When I come out of a sleep state (either sleep or hibernate) after coming back up the networkmanager applet right click claims network disabled.  Clicking to enable it does nothing but hang up the applet for a while.  Pretty much any network applications (ex firefox) that were opened or are opened after this point freeze up (grey window).

I tried /etc/init.d/network restart but this hangs the terminal.

I haven't tried pluging a wire into the system after this point but the wireless connection is no longer listed and the implication (from the applet) is that the wired network is also gone.

Possibly related:  If I turn off wireless (via the external physical switch on the laptop) and then later turn on wireless via that switch, the hardware is not recognized.  Wireless will not come back up.  This isn't nearly as important as getting a proper resume though and if it's not related it's not worth dealing with atm.

---

