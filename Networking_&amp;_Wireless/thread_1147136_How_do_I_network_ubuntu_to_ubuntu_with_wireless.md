---
title: "How do I network ubuntu to ubuntu with wireless"
date: 2009-05-03
forum: Networking &amp; Wireless
---

### Post by gleble on 2009-05-03
I have an Acer aspire 5735 and an Aspire One. Both run on Ubuntu. My wife and daughter have Windows machines which the Acers can network with. How can I network the Acers?

---

### Post by gleble on 2009-05-03
Now the Aspire 5735 has the Aspire one in its network but not vice versa
```
neil@neil-laptop:~$ smbclient -L BABY6
Enter neil's password: 
Anonymous login successful
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.2.3]

	Sharename       Type      Comment
	---------       ----      -------
	print$          Disk      Printer Drivers
	IPC$            IPC       IPC Service (baby6 server (Samba, Ubuntu))
	shared          Disk      
Anonymous login successful
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.2.3]

	Server               Comment
	---------            -------
	BABY6                baby6 server (Samba, Ubuntu)
	SAM-PC               

	Workgroup            Master
	---------            -------
	WORKGROUP            BABY6

neil@neil-laptop:~$ 
neil@neil-laptop:~$ smbclient -L NEIL-LAPTOP
Connection to NEIL-LAPTOP failed (Error NT_STATUS_CONNECTION_REFUSED)
neil@neil-laptop:~$ 


```
How can I make it work both ways?

---

### Post by drrob1 on 2009-05-03
I was having this problem also.  I have a support contract w/ Canonical so this is what they said, and it works.

Make sure winbind is installed (not winbind4)

as root, edit /etc/nsswitch.conf line that looks like this:
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4

and add "wins" so that it looks like this:
hosts:          files mdns4_minimal [NOTFOUND=return] wins dns mdns4

Canonical says that the order on this line is important.

Good Luck

---

### Post by gleble on 2009-05-03
Thanks but didn't help.It appears the problem is the permissions on /shared
When I change them they change back so I can't make it shared.This isn't the case on the Aspire One :confused:

---

