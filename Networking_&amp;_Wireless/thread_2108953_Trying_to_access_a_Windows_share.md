---
title: "Trying to access a Windows share"
date: 2013-01-26
forum: Networking &amp; Wireless
---

### Post by oygle on 2013-01-26
There are 2 computers, one is running XP pro with IP 192.168.1.100 , and the other is running Kubuntu 12.04, with IP 192.168.1.101

The networking share is working okay on Windows XP, I can see the workgroup from that computer, under explorer.

When I try to access the share with either nautilus or Dolphin, I get an error message. In nautilus, the message is

> Unable to mount location
Failed to retrieve share list from server


I notice in the router logs (both computers are connected to a router, which has the DNS side of things), the following, when I'm trying to use Nautilus to browse

my.ip.add.res:138 > my.ip.add.res:138

Does port 138 need to be 'open' for this to work ?

Nautilus does get the workgroup name from the Windows XP computer correctly.

I've read a fair bit on Samba and CIFS, and have no idea what I'm meant to install on that side of things ??   :confused:

Oygle

---

### Post by oygle on 2013-01-27
Can someone please advise on what I am meant to install, to be able to access a Windows share from Ubuntu.

---

### Post by oygle on 2013-01-27
I tried this command ..

```
nautilus smb://192.168.1.100
```

and can now browse the Windows share. It doesn't work by trying to use the Windows workgroup name, but works under Nautilus and Dolphin.

Also noticed the share is under ~/.gvfs/[COLOR="Blue"]sharename[/COLOR] on 192.168.1.100 , which means I can access it via other tools.

I didn't have to install smbfs , the only packages installed were from a 12.04 default installation, and those related to samba are

> 
samba-common
samba-common-bin
libwbclient0
smbclient
libsmbclient
kdenetwork-filesharing


Great to have the browsing on the Win computer, from Ubuntu. Thanks for your help.   :)

Oygle

---

