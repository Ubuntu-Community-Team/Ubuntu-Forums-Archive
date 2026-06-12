---
title: "Accessing network - ubuntu/winxp"
date: 2006-05-11
forum: Networking &amp; Wireless
---

### Post by scaramouche on 2006-05-11
I have a dual boot computer with Ubuntu on the secondary drive and Win XP on the master.  This computer is on my network (wired) along with 3 other Win XP computers.  I can access the shared folders of the 3 windows units through Ubuntu, however I can't access Ubuntu from Windows.  I also can't access my master hard drive on the computer in question from the Ubuntu secondary drive.  Should I be able to?  Thank you.

---

### Post by jtibau on 2006-05-11
The file sharing protocol for mixed (win/*nix) networks is Samba (or SMB).
If you haven't already shared a couple of folders in your ubuntu machine, it is pretty simple, right click on the folder and find share folder. Select SMB from the protocol list...
What you need afterwards is to have a samba user. Open a terminal and type:
"sudo smbpasswd -a user" it will guide you through setting a user.
Afterwards you can use the IP on the ubuntu system to find the shares on that machine from another computer. It will ask you for a user and password.
If you need to do anything more specialized you should read a samba tutorial.

---

