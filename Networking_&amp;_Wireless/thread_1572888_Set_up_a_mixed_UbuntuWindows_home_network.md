---
title: "Set up a mixed Ubuntu/Windows home network?"
date: 2010-09-11
forum: Networking &amp; Wireless
---

### Post by cisasteelersfan on 2010-09-11
I have 4 computers- 
[LIST]
[*]2 desktops running 10.04
[*]1 laptop running 10.04
[*]1 desktop with Windows XP.
[/LIST]
I have been googling now for a few hours. So far, I have Samba set up so that windows sees one of my ubuntu desktops. None of my other Ubuntu PCs can access the shared folder, only XP. Is there any way I can share a folder from one Ubuntu desktop, and be able to access it from all my other PCs (both ubuntu and WinXP)? Or is there a way I can share a folder on the Windows PC and be able to access it from all others? I'm pretty new at this.

Any suggestions are greatly appreciated.

---

### Post by hudsonl on 2010-09-11
> **cisasteelersfan said:**
> I have 4 computers- 
[LIST]
[*]2 desktops running 10.04
[*]1 laptop running 10.04
[*]1 desktop with Windows XP.
[/LIST]
I have been googling now for a few hours. So far, I have Samba set up so that windows sees one of my ubuntu desktops. None of my other Ubuntu PCs can access the shared folder, only XP. Is there any way I can share a folder from one Ubuntu desktop, and be able to access it from all my other PCs (both ubuntu and WinXP)? Or is there a way I can share a folder on the Windows PC and be able to access it from all others? I'm pretty new at this.

Any suggestions are greatly appreciated.

If you want to access Samba (Linux) or Windows shares from your other Linux clients ... try using the following mount command(s) ...

Let's say you share c:\temp as "**mytemp**" on the Windows PC and the PC name is "**myPC**" and I login to Windows as "**fred**" with a password of "**mypass**"

Then create a folder on your Linux box (this can be most anywhere you want ...)

> sudo mkdir /mnt/temp
> sudo mount -t cifs //**myPC**/**mytemp** /mnt/temp -o user=**fred**,password=**mypass**

Now you can look at the contents ...

>ls /mnt/temp

---

