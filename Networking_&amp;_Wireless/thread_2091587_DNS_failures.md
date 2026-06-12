---
title: "DNS failures"
date: 2012-12-05
forum: Networking &amp; Wireless
---

### Post by lisanels47 on 2012-12-05
I'm not sure who decided dnsmasq was a good idea to replace the normal DNS resolution on Ubuntu, but it fails all the time!

AGAIN today my BF's computer would not open his use-enco.com site he frequents.  He's running Ubuntu 12.04.1 like I am.  I could go to the site with no errors.  His failed.  

The difference is my computer has dnsmasq removed.  I removed it on his, and now it works great... 

Here's how you can easily remove dnsmasq and fix these types of issues:

First, comment out this line in /etc/NetworkManager/NetworkManager.conf

#dns=dnsmasq

Then use "apt-get remove resolvconf" to get rid of the resolver. Restart, and things are back to normal and working great.

---

### Post by jdthood on 2012-12-09
> **lisanels47 said:**
> Then use "apt-get remove resolvconf" to get rid of the resolver. Restart, and things are back to normal and working great.

Commenting out the "dns=dnsmasq" line was all you had to do in order to disable dnsmasq.

Removing resolvconf was not necessary and is not advisable since it is part of the base system and is assumed to be present on upgrade.

Without resolvconf you are either using a static /etc/resolv.conf which only works properly for systems in static network environments, or a dynamic /etc/resolv.conf written by NetworkManager directly. But, in the latter case, in the absence of resolvconf there is an increased risk of another tool also writing to /etc/resolv.conf and thus conflicting with NetworkManager.

---

