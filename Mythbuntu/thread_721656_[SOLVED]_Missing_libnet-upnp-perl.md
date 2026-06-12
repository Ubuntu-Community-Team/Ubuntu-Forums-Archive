---
title: "[SOLVED] Missing libnet-upnp-perl"
date: 2008-03-11
forum: Mythbuntu
---

### Post by gareththered on 2008-03-11
I just used Synaptics to update my Mythbuntu 7.10 box and it failed half way through uninstalling MythTV 0.20 and before installing 0.21!

Currently, it shows Synaptics attempting to uninstall mythtv-backend presumeably so that it can upgrade it to 0.21.  Unfortunately, if I choose to 'mark for upgrade' I get a dialog that states > Depends: libmyth-perl but it is not going to be installedIf I try and install libmyth-perl, I get another dialog that states> Depends: libnet-upnp-perl but it is not installableIf I search for libnet-upnp-perl it is easy to work out why it won't be installed - as it is not available!

I've searched the online repository and this library is available in 'Hardy' but not 'Gutsy'.

Has anyone seen this issue?  Even better, does anyone know how to resolve it?

---

### Post by Commander9000 on 2008-03-11
Here you will find the missing package
[https://launchpad.net/ubuntu/gutsy/i386/libnet-upnp-perl/1.2.1-0ubuntu2~gutsy1](https://launchpad.net/ubuntu/gutsy/i386/libnet-upnp-perl/1.2.1-0ubuntu2~gutsy1)
Install it and everything is fine :-)

---

### Post by gareththered on 2008-03-11
Perfect! I googled, but couldn't find!  Many thanks.

---

