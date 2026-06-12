---
title: "Accessing Network Drives"
date: 2006-06-26
forum: Networking &amp; Wireless
---

### Post by casperlingus on 2006-06-26
At work I'm trying to install MS Office 2003 using Crossover Office, but the people at work don't have CDs/DVDs, it's all network installation.  They gave me the network address, in Windows format:

\\frontier\software\MS\

They said the installation files are there.  I recognize you can just type that directly into a Windows task bar to get there, but it's not quite so straightforward in linux/Ubuntu

When I open the "Network Servers" dialog, I see a few machines (that appear to be there via Samba), but this machine isn't listed.  I tried going to the "Go->Locations" and typed that address with a variety of syntaxes, none of which worked.  Any ideas?

Casper...

---

### Post by scxtt on 2006-06-26
are you sure the boxes are in the same workgroup?

---

### Post by LKRaider on 2006-06-26
If you can't find the machine through the interface (maybe the machine is on another network), typing the machine IP should work, like for example this:
```
smb:///192.168.11.111
```
This should show you the samba/windows shares of that machine.

---

### Post by casperlingus on 2006-06-27
Looks like it was literally a matter of (pseudo-rebooting).  Oops, sorry to waste your time.

However, I do have a real question now.  I see the computer I need to access.  However, when I select it, it gives me the error:

*Sorry, couldn't display all the contents of "Windows Network: somenetwork".*

I *know* that I need to enter a username and password, but it's not giving me a chance to do so.  After talking to someone about it, he said I need to configure GNOME/Nautilus for network browsing so I can enter a username and password.

Does this sound familiar?  I know the username and password, but for my life I can't figure out how to get a dialog asking me for it.  Soooo frustrating...

Casper...

---

### Post by LKRaider on 2006-06-27
You can enter the name and password on the location bar, like this:
```
smb://user:password@servername/sharename/
```

Also, I found an useful post about [mounting Samba shares]("http://www.ubuntuforums.org/showpost.php?p=1087710&postcount=5") .

---

