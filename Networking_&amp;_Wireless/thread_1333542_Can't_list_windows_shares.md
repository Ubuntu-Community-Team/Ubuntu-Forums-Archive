---
title: "Can't list windows shares"
date: 2009-11-21
forum: Networking &amp; Wireless
---

### Post by Alexis Phoenix on 2009-11-21
Hello lovely people...

I have been trying to access the shared folders on the windows 7 pc from my ubuntu laptop.  I can find the pc, but can't list any folders.  I get the following error:```
alexis@laptop:~$ smbclient -L //HOMEPC/ -U alexis -N
Anonymous login successful
Domain=[WORKGROUP] OS=[Windows 7 Home Premium 7600] Server=[Windows 7 Home Premium 6.1]

	Sharename       Type      Comment
	---------       ----      -------
Error returning browse list: NT_STATUS_ACCESS_DENIED
Anonymous login successful
Domain=[WORKGROUP] OS=[Windows 7 Home Premium 7600] Server=[Windows 7 Home Premium 6.1]

	Server               Comment
	---------            -------
	HOMEPC               Desktop

	Workgroup            Master
	---------            -------
	HOME                 BTHOMEHUB
	WORKGROUP            HOMEPC

```I've tried looking on the internet for the error: NT_STATUS_ACCESS_DENIED, but all I can find is how it relates to shares on a samba server.  I don't want to share the files on my laptop so I don't have (and shouldn't need) to have it installed.

I don't know if the problem is being caused by the pc (though the files are accessible from another device, so I doubt it) or something on my laptop.  I've tried this with the generic kernel and my recent home-brew kernel.  I don't have any firewall rules set, so can rule that out.

Can anyone help?

TIA
Alexis

---

### Post by selfcontr0l on 2010-08-28
Did you ever solve this?  I have the same problem.

My Windows PC can access my samba share on my Linux PC but I cannot get the Linux PC to see my Windows share.

---

