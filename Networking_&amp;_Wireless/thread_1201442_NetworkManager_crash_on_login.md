---
title: "NetworkManager crash on login"
date: 2009-07-01
forum: Networking &amp; Wireless
---

### Post by hardke01 on 2009-07-01
I have a problem that NetworkManager daemon crashes on login after the system has been rebooted. Its fine if the session is logged out and back in.

I get an IP address when logged in then the daemon crashes and the nm-applet reports that NetworkManager is not running (correct).

If Network is then started manually using "sudo NetworkManager" it continues to run fine for the remainder of the session until the system is rebooted again.

Using Jaunty 2.6.29-02062903-generic with nm-applet 0.7.0.100 and and NetworkManager 0.7.0.100.

---

