---
title: "OpenDNS install failed connection lost"
date: 2012-03-17
forum: Networking &amp; Wireless
---

### Post by mdsikir on 2012-03-17
I tried to install OpenDNS on ubuntu so as to have internet filtering.
While following their setting on [https://store.opendns.com/get/home-free](https://store.opendns.com/get/home-free)
I had to click on "Edit Connections..." and then I changed accordingly.

The problem is that after reboot, nothing was working. The problem is
likely that whenever I set up the wireless connection I have to login.
Now the problem is that I cannot reverse the operation anymore. There is
no more "Edit connection ..." icon.
That was with Ubuntu 10.04

Thanks for any help

---

### Post by mdsikir on 2012-03-19
Ok, no answer. Let´s try something more specific.
The files```
/etc/resolv.conf
/etc/resolvconf/run/resolv.conf
```both have the mention that we should not edit them by hand since
changes would be overwritten. But on the other hand the file
```
/etc/resolvconf/run/interface/NetworkManager
```contains the DNS nameserver but my changes to it are overwritten, 
despite this file having no disclaimer about modification.

So, several questions:

[LIST=1]
[*]Where is the NetworkManager configuration saved? I did a grep 208.67.222.222 in the /etc directory and subdirectory and there is no other file containing it. In particular the file /etc/dbus-1/system.d/NetworkManager.conf does not contain this information.
[*]How can one edit the configuration once it has disappeared from the gnome panel? I was able to put the information by '"Edit connection..." but once it was broken there was no way back. How is that even possible?
[*]Is there any alternative to reinstalling ubuntu? Maybe reinstalling only selected debian packages.
[/LIST]
 Thanks for any help,


  Mathieu

---

