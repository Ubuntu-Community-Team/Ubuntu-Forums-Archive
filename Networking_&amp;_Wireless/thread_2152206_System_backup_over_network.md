---
title: "System backup over network"
date: 2013-06-07
forum: Networking &amp; Wireless
---

### Post by Roobir on 2013-06-07
Hi gents

I was wondering if there are any applications that I can install on my linux machine that will allow me to clone a whole system in my LAN? The system is running Oracle Linux, which I use for tests. I would love to have an immediate backup of the whole system, which I can install again if something happens.

More details:Oracle Linux is installed on a Sun X3 with vSphere. 
I require another format incase the lab layout changes away from VM on the Sun X3 servers.

Any help will be appreciated!

Kind regards,
Roob

---

### Post by 2F4U on 2013-06-07
Am I right in assuming that Oracle Linux is installed in a VM? I don't know vSphere, but almost any VM manager I know allows you to clone or backup the VM. In VirtualBox, for example, a VM is basically a file in the filesystem, which can be copied/backed up as any other file (the VM should, of course, be stopped before attempting to copy it).
Software capable of creating a clone from an installed system are, for example:

[http://clonezilla.org/](http://clonezilla.org/)
[http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)

---

