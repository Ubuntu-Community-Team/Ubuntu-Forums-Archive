---
title: "Help? SMB Sharing Error: NT_STATUS_NOT_SUPPORTED"
date: 2010-05-01
forum: Networking &amp; Wireless
---

### Post by zabby on 2010-05-01
Hey all, I'm having a problem accessing a network share in windows 7 from Ubuntu 9.10.  I can access this share from a Vista computer on the network, but not from Ubuntu.  Windows 7 can also connect fine to my Ubuntu Samba shares.  I get the following error when trying to connect with SMBclient. Any ideas?  

```

smbclient -L KRONOS
Domain=[KRONOS] OS=[Windows 7 Ultimate 7600] Server=[Windows 7 Ultimate 6.1]

	Sharename       Type      Comment
	---------       ----      -------
Error returning browse list: NT_STATUS_NOT_SUPPORTED
Domain=[KRONOS] OS=[Windows 7 Ultimate 7600] Server=[Windows 7 Ultimate 6.1]

	Server               Comment
	---------            -------

	Workgroup            Master
	---------            -------

```

---

### Post by zabby on 2010-05-02
bump

---

