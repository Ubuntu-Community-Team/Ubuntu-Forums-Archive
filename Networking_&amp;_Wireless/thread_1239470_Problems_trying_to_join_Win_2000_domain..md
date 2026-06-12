---
title: "Problems trying to join Win 2000 domain."
date: 2009-08-13
forum: Networking &amp; Wireless
---

### Post by darksoul7 on 2009-08-13
Hi guys.

I am having a bit of an issue trying to connect a Ubuntu 9.04 workstation to a Windows 2000 Server Active Directory domain. 

I have been following this HowTo:

but am getting this error - "Failed to join domain: failed to find DC for domain SURREY.COM" when using sudo net ads join -U admin

Is there anything I am missing? I have winbind and samba installed and configured. 

Any help would be appreciated.

Cheers!

Edit - if I use sudo net ads join -S WINNT -U admin%******
Failed to join domain: failed to lookup DC info for domain 'SURREY.COM' over rpc: The network name cannot be found

---

