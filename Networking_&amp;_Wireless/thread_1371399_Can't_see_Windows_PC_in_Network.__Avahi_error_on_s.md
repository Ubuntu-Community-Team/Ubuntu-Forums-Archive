---
title: "Can't see Windows PC in Network.  Avahi error on starup."
date: 2010-01-03
forum: Networking &amp; Wireless
---

### Post by cscomp3 on 2010-01-03
Ever since 9.10 I have had no connectivity to my windows network. My system runs just fine, just no windows connectivity with this error message at startup:

"Network service discovery disabled. Your current network has a .local domain, which is not recommended and incompatible with the Avahi network service discovery. The service has been disabled."

I have my Ubuntu PC on a wired connection to a wired/wireless router with DCHP and on a cable modem.

I have tried modifying smb.conf to a very simple version.  That lets my Windows XP PC see my Ubuntu machine but not the other way around.

ufw is turned off.  I have uninstalled Firestarter.  My windows PC firewall allows my IP range.

I tried most things in the following post:

[http://ubuntuforums.org/showthread.p...t=avahi+.local]("http://ubuntuforums.org/showthread.php?t=1169149&highlight=avahi+.local")

This helps some as I can at least mount my windows network, but all I see is my Ubuntu machine set up through Samba but not my windows PC.  I still see the error message at startup.

In my previous versions, Samba connected just fine in default form to my windows network on my router with DCHP.  I could see my entire network.  Not any more.  Just getting that pesky Avahi error message.  Any ideas?  Can anyone help me understand the difference between Samba and Avahi?

---

### Post by cscomp3 on 2012-01-15
I changed the router back to a cisco product and networking came back.  The dell version did not work.  I flashed the dell router with dd-wrt and it is now a bridging router.  My Ubuntu box now even works through the dell.

---

