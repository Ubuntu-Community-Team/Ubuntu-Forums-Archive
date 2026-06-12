---
title: "Active Directory and Wireless"
date: 2010-02-24
forum: Networking &amp; Wireless
---

### Post by de Silentio on 2010-02-24
I am running the Ubuntu Netbook Remix and setting up our systems for Active Directory Domain Authentication. When I am hard wired in (ethernet), AD authentication works with no problems using the Likewise-Open software (installed through Ubuntu Software Center).
 
What I want to be able to do is have people authenticate with AD with only a wireless connection. Has anybody done this before?
 
Thanks

---

### Post by Bufke on 2010-03-26
Likewise Open documentation [http://www.likewise.com/resources/documentation_library/manuals/open/likewise-open-guide.html#UseWiredConnection](http://www.likewise.com/resources/documentation_library/manuals/open/likewise-open-guide.html#UseWiredConnection)

They say it's because network-manager does not consider the network up until a user logs in.  I've ran into this problem too.  Setting wireless as available for all users I would think would solve it (which I thought ment it connected at GDM), yet it does not.  Once I log in as a local user, I can then login as a domain user.  But this isn't acceptable for many situations.  

Does anyone know an elegant way to work around this?  I would hate to remove network manager and take care of networking manually.  I see no way to connect to wireless before gdm without killing network-manager since wpa_supplicant doesn't work with it.

ps killing network-manager and connecting manually does fix it.  See [http://ubuntuforums.org/showthread.php?t=666977](http://ubuntuforums.org/showthread.php?t=666977)

---

