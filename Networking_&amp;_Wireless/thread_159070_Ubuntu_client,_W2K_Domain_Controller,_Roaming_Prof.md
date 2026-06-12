---
title: "Ubuntu client, W2K Domain Controller, Roaming Profiles?"
date: 2006-04-12
forum: Networking &amp; Wireless
---

### Post by Jabran Asghar on 2006-04-12
Hi everyone :) 

I got Breezy to authenticate user login through Active Directory on W2k domain controller. What I want do now is:

*How to Configure Breezy to store/load W2k domain user profile from Server (either from W2K DC, or another Linux server)? :-k 

*How to configure a common profile for new domain users? i.e. When a new W2K domain user logs into Linux box, s/he should be assigned a preconfigured profile (including application shortcuts, menus, etc.). I checked Sabayon already, but that creates profiles only locally on the Linux. 

As I know, generally NTFS is not writeable from Linux, is it possible to do so somehow? If not, then I have another Linux server on network that can be used to host user profiles.

Do I have to configure any startup script Breezy boxes to mount /home directory from server? If yes, what kind of script, and where it should be done?

Thanks for any thoughts.

Jabran

EDIT: Seems I posted the message under Hardware category :(. Dont know how to move to another category ](*,) . 

Anyway, I hope some one will answer the original question :)

---

### Post by peatcom on 2006-04-19
Sorry, but I have no answer, just a question: Where can I find information on how to set up ubuntu as a client to a Windows AD domain?

I appreciate any hint.

---

### Post by vinfred on 2006-04-20
see [http://us5.samba.org/samba/docs/man/Samba-HOWTO-Collection/](http://us5.samba.org/samba/docs/man/Samba-HOWTO-Collection/)

---

