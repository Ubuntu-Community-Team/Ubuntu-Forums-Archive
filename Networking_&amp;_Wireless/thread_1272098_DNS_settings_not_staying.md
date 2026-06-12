---
title: "DNS settings not staying"
date: 2009-09-21
forum: Networking &amp; Wireless
---

### Post by wrwarwick on 2009-09-21
I have followed the instructions here [http://ubuntuforums.org/showthread.php?t=191239](http://ubuntuforums.org/showthread.php?t=191239) but everytime I reboot I get the DHCP supplied settings from my router.

I am using Comcast and the DNS servers suck and really slow down my internet browsing. Is there anyway that I can stop having to manually edit /etc/resolv.conf?

---

### Post by Iowan on 2009-09-21
The procedure in the link usually works. I haven't used the "supersede" option, but the "prepend" option usually does the trick.

---

### Post by wrwarwick on 2009-09-21
It hasn't worked for me. There has to be some way to get these settings to change... if Windows can do it, Linux can do it better!

---

### Post by wrwarwick on 2009-09-21
For some reason the DNS information I had from when my machine was hard-wired to an ethernet network kept coming up when I was connected to wireless. I was able to go into the resolvconf settings and remove this information. Now looks like everything is working correctly.

Are the DNS settings the same for all network interfaces, ie eth0, eth1, etc...? If so this would explain the problem that I was having.

---

### Post by Iowan on 2009-09-21
I haven't used resolvconf  - it's not installed on any of my systems (though I found /etc/resolvconf directory.)  For what it's worth, I DID find [this]("http://ubuntuforums.org/showthread.php?t=971064") link.

---

