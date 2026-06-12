---
title: "Cannot connect to Windows 7 shares from Ubuntu 10.10 (login loop)"
date: 2010-11-19
forum: Networking &amp; Wireless
---

### Post by krunalpatel on 2010-11-19
Okay before anybody asks me to search, i'll tell you that i've seen this issue addressed and have tried EVERYTHING that I have read. I still cannot connect to a Win7 PC in the house from my Ubuntu machine. I see the PC listed in >Network but when I click on it I receive the login auth window > in which I type in the proper credentials > and I get a loopback to the login window. It doesn't go past it. I've tried editing the smb.conf and editing settings on the win7 pc as well. Nothing i've tried is working. Please help.

---

### Post by peterpixel on 2010-12-01
I have the same problem, although I am running Lubuntu. 

I can see the workgroup, all the computers, but I simply cannot get past the login screen. 

Does anyone have any suggestion? I have already disable Windows Live Messenger on my Win 7 Machine.

---

### Post by krunalpatel on 2010-12-01
> **peterpixel said:**
> I have the same problem, although I am running Lubuntu. 

I can see the workgroup, all the computers, but I simply cannot get past the login screen. 

Does anyone have any suggestion? I have already disable Windows Live Messenger on my Win 7 Machine.

I have figured it out. Apparently you have to uninstall windows live sign in assistant from ur windows box. Also apply some local policy changes (you can google it and it's pretty simple). But do make sure you unisntall that windows live sign in assistant program (not sure of the exact name).

---

### Post by peterpixel on 2010-12-03
Thanks for the tip, however, uninstalling Live Essentials is not really an option. I rely a lot on Live Mesh and so far, other sharing solutions were less than satisfactory. I have disabled the Live Sign In Assistant process, but that, sadly, did not help.

Such a pity, I would love to access my shared media on my Win7 box.

---

### Post by krunalpatel on 2010-12-03
> **peterpixel said:**
> Thanks for the tip, however, uninstalling Live Essentials is not really an option. I rely a lot on Live Mesh and so far, other sharing solutions were less than satisfactory. I have disabled the Live Sign In Assistant process, but that, sadly, did not help.

Such a pity, I would love to access my shared media on my Win7 box.


I'm sorry but in order for it to work, you have to completely uninstall the sign in assistant program, or else it will not work. Not sure why that program causes this issue, but maybe you can search launchpad for this problem. Hopefully there is a fix for this problem (since it is common) in the near future.

---

