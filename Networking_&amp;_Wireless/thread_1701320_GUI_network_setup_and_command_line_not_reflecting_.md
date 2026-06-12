---
title: "GUI network setup and command line not reflecting changes"
date: 2011-03-06
forum: Networking &amp; Wireless
---

### Post by wgregori on 2011-03-06
Hi,

I'm running Ubuntu 10.04 LTS, Lucid Lynx and I'm having problems implementing changes to interfaces.  

I have made changes to my interfaces via the GUI but when I open a terminal window and so a ifconfig I find that nothing has changed.  I've opened an editor and looked at etc/network/interfaces but changes made with the GUI never make it to the config file....

Does the networking GUI result in changes to the etc/network/interfaces file.

Confused... 

Thanks,
Wayne

---

### Post by chili555 on 2011-03-06
> Does the networking GUI result in changes to the etc/network/interfaces file.No.

The networking GUI (Network Manager) is part of the automated way of doing all the steps necessary to find networks and connect. /etc/network/interfaces is part of the manual way. They are two completely different systems.

---

