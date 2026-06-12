---
title: "Different passwords for different shares?"
date: 2009-03-14
forum: Networking &amp; Wireless
---

### Post by ownaginatious on 2009-03-14
I was wondering if it's possible to set up the smb server so that each of my shares can have a different username and password. My brother keeps stealing my old school work, and I need to keep him out of mine while still giving access to his from my file server.

Does anyone know how to do this? I have been unable to find anything that specific about configuration.

Any help would be greatly appreciated,

Thanks!

---

### Post by mrsteveman1 on 2009-03-14
Doesn't samba obey file permissions? Keep your files in a folder that his user has no permissions for, chmod them to 700 or something. 

I think it is possible to do per share permissions but it's been a while since i messed with it.

---

### Post by capscrew on 2009-03-14
There are no **share** passwords.  You authenticate the user, not the share.  After the user is [COLOR="Green"]authenticated,[/COLOR] the underlying permissions [COLOR="Blue"]authorize[/COLOR] the use of the files.

You can use the "**valid user =**" directive in the share stanza to limit the users of the share.

---

### Post by ownaginatious on 2009-03-15
The problem is the drive I'm trying to share folders on is a permanent NTFS drive in the computer. Every time I try to change permissions, it automatically changes them all back to root. I have NTFS-3G, or whatever it's called, but I still can't get around it.

Any other options?

Thanks!

---

### Post by capscrew on 2009-03-15
> **ownaginatious said:**
> The problem is the drive I'm trying to share folders on is a permanent NTFS drive in the computer. Every time I try to change permissions, it automatically changes them all back to root. I have NTFS-3G, or whatever it's called, but I still can't get around it.

Any other options?

Thanks!

You might start here:
[http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/AccessControls.html]("http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/AccessControls.html")

---

### Post by mrsteveman1 on 2009-03-15
If this is a machine that's going to be a samba server you should really use a filesystem that directly supports permissions like ext3.

---

