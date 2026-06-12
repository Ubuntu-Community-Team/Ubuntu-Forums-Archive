---
title: "DHCP server with Web Management UI"
date: 2013-04-17
forum: Networking &amp; Wireless
---

### Post by Niquest on 2013-04-17
I have a box running Ubuntu Server 12.04 and the isc-dhcp-server package.  I need some sort of locally hosted web GUI interface to easily change settings, including adding/removing Static IP maps.

I would prefer nginx as the webserver for this if possible, but I have no problems with using a different one.
One caveat is that I need advanced control over the static maps, specifically, I need some of the static maps to use different gateways than the default one.  This is easily supported by editing the dhcpd.conf file, but I haven't been able to find a good webgui one that will do this.

I would, of course, prefer something with an ubuntu repository, but if I have to compile it myself, I'll do it, as long as it has the features.

Can anyone offer suggestions on a package?  My own search on this subject has come up dry.  I dug up something called Sauron, but it doesn't seem to have an ubuntu package.  Any help would be much appreciated.

---

### Post by hfdragon on 2013-11-21
Hi !

I saw this thread because I'm looking for the exact same thing... did you find what you were looking for ?

---

### Post by ejmarten on 2014-03-13
There's one on Source Forge.  

[http://phpdhcpadmin.sourceforge.net/](http://phpdhcpadmin.sourceforge.net/)

---

### Post by xicarusx on 2014-03-13
Give Webmin a look as well. [www.webmin.com](www.webmin.com)

---

