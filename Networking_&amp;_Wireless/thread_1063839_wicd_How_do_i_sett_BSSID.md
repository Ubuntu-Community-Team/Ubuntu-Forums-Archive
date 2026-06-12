---
title: "wicd: How do i sett BSSID?"
date: 2009-02-08
forum: Networking &amp; Wireless
---

### Post by perstromgren on 2009-02-08
I have switched to using wicd, and has to manually connect every time. Solutions for this talks about B/ESSID badly defined (with spaces if am correct), but I don't even know where the B/ESSID should be set! Do I need to create a wireless-settings.conf? The one I have, and haven't touched, is empty.

The man page says:

"Automatically Connecting to Networks
Wicd  uses  the  BSSID to recognize a particular network (and thus to decide whether it should automatically connect to it). " 

Where is this BSSID set?

The log repeats over and over again:

No wired connection present, attempting to autoconnect to wireless network
Unable to autoconnect, you'll have to manually connect

Any light on this is most welcome!

Per.

**Solution**

I was asking the wrong question...

My problem was that I did not know how to mark a network for automatic connection, as this does not seem to be documented. In the Wicd Mgr GUI, one should click the right arrow beside the network you want to connect autmatically, and click the check box that appears.

---

