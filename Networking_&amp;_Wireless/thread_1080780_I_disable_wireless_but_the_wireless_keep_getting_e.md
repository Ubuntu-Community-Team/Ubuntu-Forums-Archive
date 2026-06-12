---
title: "I disable wireless but the wireless keep getting enable when restarting Ubuntu 8.10."
date: 2009-02-25
forum: Networking &amp; Wireless
---

### Post by TJX09 on 2009-02-25
I disabled wireless but the wireless connection keep getting enable when restarting Ubuntu 8.10. Want i want is for the wireless connection to be disable when turning on the computer. How do i do that?

---

### Post by Yashiro on 2009-02-25
Usually wireless connections require you to login/or enter a password to start up. So remove the password from your keyring?

Or find out the name of the driver module and unload it.

---

### Post by Eric Draven on 2009-02-26
> **TJX09 said:**
> I disabled wireless but the wireless connection keep getting enable when restarting Ubuntu 8.10. Want i want is for the wireless connection to be disable when turning on the computer. How do i do that?
I also want to start Ubuntu 8.10 with wifi disabled.  Can't claim to be an expert on this, but I speculate this must be another quirk with the Network Manager application.  As I'm typing this, Network Manager can't show any Connection Information on my ethernet interface but I'm obviously connected right now, it says "No valid active connections found".  Also, my static IP disappears on some boot ups due to Network Manager's meddling.  Would be good if there were an option to configure startup network settings for the wireless adapter thru Network Manager.

---

