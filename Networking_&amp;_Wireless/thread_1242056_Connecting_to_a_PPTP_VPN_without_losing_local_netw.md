---
title: "Connecting to a PPTP VPN without losing local network capabilities...?"
date: 2009-08-16
forum: Networking &amp; Wireless
---

### Post by michwill on 2009-08-16
Hi All,

I'm having a bit of an issue with PPTP VPNs in Ubuntu Jaunty.  The following is my "uname" info:

	Linux corebox 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 19:49:51 UTC 2009 i686 GNU/Linux

Basically I have several servers behind a ZOOM ADSL router.  I currently have a web application on its own box.  This application is visible (via port forwarding) to the outside world.  However, it requires logging in to a remote machine (via VPN) in order to update it's data.  Problem is, whenever it connects to the VPN, it loses all sense of self on the local network.  I need to have my cake and eat it to.  I can't afford for the web application to be inaccessible while the VPN is connected.

I used info gathered from ([http://ubuntuforums.org/showthread.php?t=91249](http://ubuntuforums.org/showthread.php?t=91249)) in order to connect.

In Ubuntu's defense, the VPN works amazingly well, I simply wish I could be more selective about what traffic gets sent where.  Any ideas?

Best.

---

