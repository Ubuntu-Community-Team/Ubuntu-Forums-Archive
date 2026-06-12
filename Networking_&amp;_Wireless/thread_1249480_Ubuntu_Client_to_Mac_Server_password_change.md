---
title: "Ubuntu Client to Mac Server password change"
date: 2009-08-25
forum: Networking &amp; Wireless
---

### Post by PsyMan2000 on 2009-08-25
Hi all,

After a few days of headscratching I have finally got my ubuntu client to authenticate against our Mac OSX leopard server and use the same home folders as our mac clients.

It did involve a quick install of fedora 11 on another machine so I could use the red hat ldap gui to create a working ldap.conf file and then installing webmin to create a working fstab file for mounting the home folders. Cheating? maybe but that bit is working now :D

However, I now seem to have one final hurdle before I use deploystudio to roll out this fine OS

If a user on the mac server has to change their password or is forced to change it on login, I can't seem to find a way of using ubuntu to do this in the same way as a mac client or windows client can.

Am I missing something obvious?

Any advice on this would be appreciated.

Regards

Simon

---

