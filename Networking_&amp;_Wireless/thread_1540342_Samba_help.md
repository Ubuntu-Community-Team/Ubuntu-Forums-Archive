---
title: "Samba help"
date: 2010-07-27
forum: Networking &amp; Wireless
---

### Post by jadep on 2010-07-27
Hello,
I installed ubuntu on my laptop.  I am slightly above a newbie.  Call me an experienced Linux user.  Not much of a hacker.

I have an old computer running Mandrake that I use as a file server using Samba.  I also have webmin installed.  I can not mount the share on my laptop.

My desktop running Suse has never had a problem.  Same with some Apple laptops.  

I go to Places->connect to server...  When I enter the info, it comes up with the password box.  I enter the password.  It then puts up the password dialog box again.  There is an interesting symptom, when I get into webmin and check Samba connections for that share, it shows that a connection is generated each time I enter a password, but the user name and group are left blank.

Is there a way to trouble shoot this via terminal?  Again, my other computers have zero problem.  Thanks for your help.

---

### Post by jadep on 2010-07-29
I tried this on the terminal:
smbclient -L <windows-box> -U <username>

It prompted me for a password.  when I entered the password, here is the message I got:
Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled  tree connect failed: NT_STATUS_ACCESS_DENIED

I tried it again without giving a password, just hit return, and this is what I got:
Domain=[DECNET] OS=[Unix] Server=[Samba 3.0.6]

	Sharename       Type      Comment
	---------       ----      -------
	CORPORATE       Disk      corporate files
	print$          Disk      
	pdf-gen         Printer   PDF Generator (only valid users)
	IPC$            IPC       IPC Service (Samba Server 3.0.6)
	ADMIN$          IPC       IPC Service (Samba Server 3.0.6)
	DECNET_P1       Printer   HP 3320
Domain=[DECNET] OS=[Unix] Server=[Samba 3.0.6]

	Server               Comment
	---------            -------
	DECSERVER            Samba Server 3.0.6

	Workgroup            Master
	---------            -------
	DECNET               DECSERVER
	WORKGROUP            JAMES-LAPTOP

I then tried to mount the share CORPORATE, and it appeared to work.  But when I tried to CD to it, it said "access denied".  From my other computers I have to give it the password and it works fine.

---

### Post by jadep on 2010-07-29
security = user
client lanman auth = Yes

Seemed to do the trick.

---

