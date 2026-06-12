---
title: "[SOLVED] Upgrade Ubuntu, no internet"
date: 2009-01-08
forum: Networking &amp; Wireless
---

### Post by afderrick on 2009-01-08
I just upgraded my ubuntu to the newest intrepid release.  My internet isn't working and I have no access to the network manager.  I have a network configuration app but even though it is properly setup as best I can tell, it still won't connect.  Any help?

---

### Post by Snogus on 2009-01-08
You may have lost drivers. Track them down and reinstall the latest versions just incase.
If you have no access to the network manager in all likelyhood you have a problem with your networking on your computer, no reason for it to be hardware (if internet was working before upgrade) so its software. Get the drivers (see Above)

---

### Post by cdtech on 2009-01-08
Why don't you have access to the NM?
Post the output of "ifconfig" and lets have a look see.

---

### Post by afderrick on 2009-01-08
under drivers it shows that I have the atheros drivers intalled now, for restricted drivers. Maybe if i disable it?

---

### Post by afderrick on 2009-01-08
I disabled the atheros driver under hardware drivers, rebooted, re-enabled in and rebooted again.  It's recognizing my network now, just having difficulty actually making the connection.

---

### Post by afderrick on 2009-01-08
That was weird, got it up and working.  Sorry for the bother, thanks for the help.

---

