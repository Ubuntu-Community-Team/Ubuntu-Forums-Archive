---
title: "[SOLVED] Network Manager Won't &amp;quot;Forget&amp;quot; Hidden SSID"
date: 2008-12-13
forum: Networking &amp; Wireless
---

### Post by rjantz on 2008-12-13
Hello,

I am running Ubuntu 8.10 and have a Network Manager problem.  The problem is that I installed a new router, which was (I believe) factory-configured to not broadcast the SSID, even though I later enabled broadcast.  Network Manager apparently detected the network when it was hidden, and now refuses to treat the SSID as "not hidden."  I want Network Manager to forget this setting and just see the network on boot and not require me to manually connect, but no matter what I do, it treats it as hidden.  FYI, I am using WEP security.

Does anyone know how to make Network Manager forget about a hidden SSID?  Would it be OK to remove it and re-install it?

Thanks.

---

### Post by The Cog on 2008-12-13
In synaptic, I think the option of "Complete Removal" also removes the applications configuration files, so doing that and reinstalling may well do the trick.

Alternatively, install wicd instead, which I think is rather more reliable and better behaved. [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by rjantz on 2008-12-15
I finally put the old router back in, and it everything works as it should now.  Apparently the new router was not broadcasting the SSID even though "broadcast" was checked.  I've never heard of anything like that, but how else to explain that the same Network Manager successfully sees the network with the old router, but acts as if it is hidden with the new router?

---

### Post by bab1 on 2008-12-15
This article should help you:
[http://www.arachnoid.com/linux/NetworkManager/index.html]("http://www.arachnoid.com/linux/NetworkManager/index.html")

---

