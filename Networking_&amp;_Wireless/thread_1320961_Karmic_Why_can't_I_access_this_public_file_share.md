---
title: "Karmic: Why can't I access this public file share"
date: 2009-11-09
forum: Networking &amp; Wireless
---

### Post by jstars on 2009-11-09
There is a public file share that I cannot connect to with my Ubuntu 9.10 netbook. This fileshare was accessible in WinXP (but I since upgraded to Ubuntu 9.10). On our local network the IP address is: 10.2.2.40

[LIST]
[*]I can ping 10.2.2.40 (so I know it is there).
[*]I can access it via [http://10.2.2.40](http://10.2.2.40) in Firefox (it brings up the fileshare's webpage). However when I click on the link to get to the folders it doesn't bring up the folder in Nautilius.
[/LIST]
I tried smb://10.2.2.40 in Nautilus and a error message comes up saying "Error: Cannot retrieve share list from server Please select another viewer and try again."

There is another fileshare on the network (10.2.2.20) that I can access in Nautilus using smb://10.2.2.20 just fine.

How do I troubleshoot this to find out why Ubuntu (samba) cannot get access to this troublesome fileshare?

---

### Post by jstars on 2009-11-10
Here is some more info about the fileshare I am trying to access:
```
XXXXX@XXX:~$ smbclient -L 10.2.2.40
Enter XXXXX's password: 
Domain=[FORTRESS] OS=[Windows Server 2008 R2 Standard 7600] Server=[Windows Server 2008 R2 Standard 6.1]

	Sharename       Type      Comment
	---------       ----      -------
Error returning browse list: NT_STATUS_NOT_SUPPORTED
session request to 10.2.2.40 failed (Called name not present)
session request to 10 failed (Called name not present)
session request to *SMBSERVER failed (Called name not present)
NetBIOS over TCP disabled -- no workgroup available

```

I suspect it is a problem using smbclient to access a Windows Server 2008 fileshare - if so how to I fix this on my end?

---

### Post by jstars on 2009-11-10
This may be a bug. See here: [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/472681]("https://bugs.launchpad.net/ubuntu/+source/samba/+bug/472681")
I will be downloading a proposed-update to smbclient.

---

### Post by jstars on 2009-11-10
I applied the proposed update. I still can't browse the share using just the IP address.  I tried specifying the IP and folder name and that works (e.g. smb://10.2.2.40/movies).

Unfortunately I am not sure whether the update did that or it was like that before. I guess that makes this is partially solved - still would liek to browse the share though.

---

