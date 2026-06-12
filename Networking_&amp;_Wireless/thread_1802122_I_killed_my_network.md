---
title: "I killed my network"
date: 2011-07-11
forum: Networking &amp; Wireless
---

### Post by hdyess on 2011-07-11
I'm running Ubuntu 11.04. Got this message while reinstalling Wine *"The following PAM profiles cannot be used together: Likewise Open, Winbind NT/Active Directory authentication Please select a different set of modules to enable."* While trying to resolve the issue error I removed some networking components that shutdown access to my local windows network. I can still get the internet without issue. Also using terminal service client or Virtualbox XP install I can access the local windows network. So, what do I need to put back to regain access to my windows network resources through my Ubuntu desktop?

---

### Post by hdyess on 2011-07-11
Okay, I fixed it myself by adding the gvfs backend add-on to my userspace virtual file system server. Now I back to where I started.... talking to myself :-)

---

