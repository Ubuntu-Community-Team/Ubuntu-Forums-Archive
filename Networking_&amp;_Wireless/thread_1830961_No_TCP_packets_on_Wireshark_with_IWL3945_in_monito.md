---
title: "No TCP packets on Wireshark with IWL3945 in monitor mode"
date: 2011-08-22
forum: Networking &amp; Wireless
---

### Post by Kernelingus on 2011-08-22
I'm running Lucid on a Dell Inspiron 1525, and I'm having some trouble getting Wireshark to capture properly with the iwl3945 module, which is supposed to support monitor mode and even injection.  (Which I'm not trying to do, I'm just trying to sniff.)

A distro upgrade or so ago, I switched to the new driver from the old ipw3945, which I'd replace with ipwraw anytime I wanted to put the card into promiscuous mode.  (It worked great.)

Now, with iwl3945, the card *seems* to go into monitor mode properly.  In fact, I can even use airmon-ng to create a pseudo-interface for monitoring while leaving the other one up for browsing.  But on it, I can't seem to monitor anything other than broadcast and management packets.  I can't see TCP packets of any sort.

I've googled around on this, and it seems like a few others have run into this difficulty without finding solutions.  Any ideas out there?

---

### Post by Kernelingus on 2011-08-22
...bump.  ^

---

### Post by lkjoel on 2011-08-23
Try following this HOWTO: [http://lkubuntu.wordpress.com/2011/07/18/upgrade-wireshark-to-1-6-0/](http://lkubuntu.wordpress.com/2011/07/18/upgrade-wireshark-to-1-6-0/)
It might simply be because Wireshark isn't at the latest version.

---

### Post by Kernelingus on 2011-08-26
Thanks for the suggestion.  I couldn't make the upgrade work from source, and the referenced PPA wasn't there anymore.  So I just did a distribution upgrade, which I'd been meaning to do anyway.

**Now I'm on Natty, with Wireshark 1.4.6**  Interface looks a little nicer, but problem persists!

Any other ideas?  (At this point, I'm tapped.)

---

### Post by Kernelingus on 2011-08-26
Another bit of info...

With the device in monitor mode I can run airodump-ng and *see* running counts of packets on the various interfaces around, channel hopping and all.  So I *know* the hardware's fine and the driver probably isn't the reason Wireshark can't see them...

(...but why can't it see them?!)

---

