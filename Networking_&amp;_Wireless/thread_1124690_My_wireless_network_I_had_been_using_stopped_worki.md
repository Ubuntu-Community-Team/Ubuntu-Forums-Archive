---
title: "My wireless network I had been using stopped working"
date: 2009-04-13
forum: Networking &amp; Wireless
---

### Post by aaronej on 2009-04-13
After my second installation of ubuntu on a flash drive (the first time I filled up the drive and couldn’t boot so I needed to start a new) all was hunky dory for a little while, then around when I was trying to install some plug-ins to mp3 support for rhythm box my wireless network I had been using stopped working.  Its not that I couldn’t connect, just that I nothing was getting through.  I tried using the networking tool to see whether I could get any information about the router or IP to no success.  Is there anyway to make sure that that is not something on my end to ease my fears it’s a remote problem?

---

### Post by scapegoat on 2009-04-13
I've run into a similar issue with a fresh install of 8.10 on a Acer laptop, after doing an install from a flash drive.

I've narrowed it down to WPA/WPA2 issues.  If I have security off or use WEP, I am able to connect without issue.  I have tried installing/re-installing the WPASupplicant with no success.

Once I find some blank cd's, I'm going to try formatting again - but I wouldn't expect it to fix anything (unless the flash drive install causes issues with this package?).

---

### Post by aaronej on 2009-04-13
How does one turn security off?

---

### Post by scapegoat on 2009-04-13
> **aaronej said:**
> How does one turn security off?

It's an option in your router, I'd suggest doing MAC address limiting so that it's still semi-secure (from the basic intruders) but not encrypted.

---

