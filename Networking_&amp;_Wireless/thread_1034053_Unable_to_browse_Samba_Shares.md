---
title: "Unable to browse Samba Shares"
date: 2009-01-07
forum: Networking &amp; Wireless
---

### Post by lakerssuperman on 2009-01-07
Hello.  I am currently running Ubuntu 8.10 64 bit.  I am unable to browse my network shares on any of my other Linux or Windows boxes through Nautilus, Dolphin, or Konqueror.  I am, however, able to browse the shares through Smb4k.  Also I can print to network printers and browse my DAAP shares.  I thought my problem was only related to Nautilus but now I have found it in both Dolphin and Konqueror.  I have checked my settings but don't seem to find anything wrong and the fact that Smb4k works only makes the problem more unclear.  Anyone else having these problems?  I have browsed the forums but haven't found anything about this problem.  Any help would be appreciated.

---

### Post by superprash2003 on 2009-01-08
try this way [http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html](http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html)

---

### Post by dmizer on 2009-01-08
If you must have network browsing, I'm afraid I don't have good answers for you. Some things you can try would be:

[LIST=1]
[*]Make sure all the computers belong to the same workgroup.
[*]Make sure you have a correctly configured winbind server on your Ubuntu machine.
[*]Make sure there are no firewalls interfering (Windows or Ubuntu).
[/LIST]
In Ubuntu, point number 1 will require a correctly configured Samba server (I currently do not know of any other way of doing this). Please take a look at the first link in my sig for the howto on this.

If access is your primary concern, I suggest mounting the shares rather than browsing. This gives you several advantages like better speed, and instant access. If you'd like to try mounting, please see the second link in my sig.

The second link in my sig also includes directions on how to correctly configure a winbind server.

Good luck.

---

