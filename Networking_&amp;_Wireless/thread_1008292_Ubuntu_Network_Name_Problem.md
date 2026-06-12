---
title: "Ubuntu Network Name Problem"
date: 2008-12-11
forum: Networking &amp; Wireless
---

### Post by MaloKorrigan on 2008-12-11
Hi everyone,

Here's my problem in a nutshell:

1st Computer: Windows XP Professional (SP3)
2nd Computer: Ubuntu 8.10 (with all updates installed)
3rd Laptop: Windows XP Professional (SP3)

Each computer has a static IP address and unique computer name.

I've managed to install XAMPP successfully on each computer, the real problem is when I type the name of the Ubuntu computer, "mike" into the address bar, [http://mike/](http://mike/) it won't visit the XAMPP homepage unless I enter the IP address of the Ubuntu computer into the address bar of my browser, [http://192.168.0.2](http://192.168.0.2)

I can type in the name of the Windows computer and laptop into the address bar to load the XAMPP homepage, [http://adam/](http://adam/) but it won't work for the Ubuntu computer.

Is there anything I can do to make this work like the Windows computers?

Thanks in advance. :)

---

### Post by Iowan on 2008-12-11
Name resolution in a Windows environment seems to be a recurring problem.  Sometimes Winbind helps.  I'll see if I can at least find some similar links.
One thing to check - /etc/hosts file has line:```
127.0.1.1. <hostname>
```

---

### Post by MaloKorrigan on 2008-12-12
Thanks for the help Iowan, I've checked the /etc/hosts file and this is what it lists

127.0.0.1 localhost
127.0.1.1 ben



Because I'm thinking of installing a Linux computer at work with LAMPP installed, we have a Windows 2003 acting as out DNS server, can I add a name to that DNS to redirect to that computers IP address?

---

