---
title: "Trying to set up remote access to localhost"
date: 2008-12-25
forum: Networking &amp; Wireless
---

### Post by 2010student on 2008-12-25
Hi, I'm looking for a way to set up a server so that 2 other computers can access the [http://localhost/](http://localhost/) site on the server.

The server and one of the two clients run ubuntu, and the other client runs windows vista.  Is there an easy way to do this?  FYI my internet connection is time warner cable for home use.

---

### Post by cariboo on 2008-12-26
Have a look at [this]("http://tldp.org/HOWTO/NET3-4-HOWTO.html"), to help you set up your home network. To access your local web site alias the hostname of the server in /etc/hosts on each computer on your network. For windows:

> Windows NT/2000/XP/2003/Vista: %SystemRoot%\system32\drivers\etc\ is the default location, which may be changed. The actual directory is determined by the Registry key \HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters\DataBasePath.

This is basic networking, so use the howto to get familiar with networking, then you can do what you need without thinking about it.

Jim

---

