---
title: "Windows domain file sharing"
date: 2008-12-05
forum: Networking &amp; Wireless
---

### Post by Ianvn on 2008-12-05
I hope somebody can help me with a few questions I have related to sharing between a windows domain and a ubuntu machine.

We currently run a Windows 2003 domain with a mixture of XP and Vista clients. I am trying to intoduce a Ubuntu 8.10 machine to the network to replace our current fileserver.

I have successfully joined the ubuntu box to my domain and I'm able to login with domain users on the Ubuntu box.

Now the questions:
* I am able to setup a share on the ubuntu box but when trying to access the share from a windows machine I get a prompt for a username and password. Can I setup the share to use "windows authentication" for the domain users?

* How do I go about sharing a folder on the Ubuntu box with specific rights for certain domain users. (ie. domain user1 only have write access to folder 1 and domain user2 can write to folder 1 and 2) 

* How can I give my windows domain admin account - root type rights on the ubuntu box.

Any help would be appreciated.

---

### Post by superprash2003 on 2008-12-05
you generally use samba to share files between windows and ubuntu

---

### Post by Iowan on 2008-12-05
[Here]("https://help.ubuntu.com/community/SettingUpSamba") is a help page for setting up Samba.  [This]("http://www.redhat.com/archives/k12osn/2008-August/msg00138.html") one has several lilnks for Samba and LDAP.

---

### Post by Ianvn on 2008-12-06
Thanks for the replies.

Seeing as its weekend I have setup a test windows domain and a ubuntu virtual pc. I'm busy going through the steps in the following example: [SettingUpSamba]("https://help.ubuntu.com/community/SettingUpSamba#Active%20Directory%20Integrated%20File%20Server")

The 'kinit' worked fine.
But as soon as I do the 'net ads join' I receive the following error:

```
user@ubuserver:~$ sudo net ads join -U administrator@DOMAINTEST.LOCAL
[2008/12/06 21:08:53,  0] param/loadparm.c:lp_do_parameter(7196)
  Ignoring unknown parameter "change notify timeout"
Enter administrator@DOMAINTEST.LOCAL's password:

[2008/12/06 21:08:59,  0] libads/kerberos.c:ads_kinit_password(356)
  kerberos_kinit_password administrator@DOMAINTEST.LOCAL@DOMAINTEST.LOCALfailed: Malformed representation of principal

Failed to join domain: failed to connect to AD: Malformed representation of principal
```

Any ideas what the problem can be - I don't seem to get a lot of results when searching for the error.

---

### Post by gregphil on 2008-12-06
I am not sure if this is related, but you should be aware of it:

Ubuntu GUI **browsing** of **authenticated** Windows shares has been broken since Hardy Heron was released.  See bug:
[Bug #207072 in gvfs (Ubuntu Hardy): “nautilus does not display samba shares for machines inside an ADS network.”]("https://bugs.launchpad.net/ubuntu/hardy/+source/gvfs/+bug/207072") 
The bug actually applies to ALL **authenticated** shares, not just ADS networks.  Note that unauthenticed (guest or anomymous access) are not effected.

This is the opposite sharing direction of what you are asking for (I think), you seem to want to browse Ubuntu shares from a Windows machine.  But your problem may be related, the bug mentioned is in the gnome library that authenticates the machine to machine connection.

Good Luck.

---

### Post by sir4taye on 2008-12-06
Thank you for pointing this out. It's the best I've seen for a home network.

---

