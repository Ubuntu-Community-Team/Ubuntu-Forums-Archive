---
title: "Samba Not Installed, But It Is!??"
date: 2012-09-08
forum: Networking &amp; Wireless
---

### Post by Akacheebe on 2012-09-08
Ubuntu 12.04 running Mate 1.4 desktop and was a clean install about 2 weeks ago.

This is a multiboot system with multiple hard drives that include various flavors of Windows.  Please note that I have 3 of these multiboot computers on my home network and I what to be able to access all windows/Ubuntu drives from and too all the other computers on my LAN for file transfer/sharing purposes.  

I had this working in v9.04 and v10.04 but not without problems back then.  I opted out of v11.04 etc because of the Unity desktop and went to Mint 11/12 but came back to Ubuntu 12.04 when I found out about Mate.

I've had problems getting drive sharing working between all these systems so I installed NTFS Configuration tool that automatically mounts these drives at boot up but when I right click on Properties then Permissions all I see is root and no options to share anything??  

So I went to System > Administration > Shared Folders and I got this notification??  

> [B]Sharing services are not installed

You need to install at least either Samba or NFS in order to share your folders.[/B] Problem is, Samba IS installed already??  So I uninstalled it then reinstalled and I still get the same message?

Please keep in mind here that I want to be able to not only read these other drives but write to them as well.  

Oh, and please try to make this as simple as possible as I'm not very good in Terminal mode.;)

Thanks

---

### Post by Akacheebe on 2012-09-13
5 days and 78 views and no one has any comments on this?  Come on ppl?

---

### Post by iponeverything on 2012-09-13
there is a smb client and a smb server - is the server installed?

---

### Post by Akacheebe on 2012-09-16
Yup, everything is installed but still get that message?  

Good news is that I can now get to all drives on the other computers, but don't ask me what I did to fix it cuz I don't have a clue.  Sort of good news, bad news.  

Anyway, file sharing is working and that's all that matters right now.

Thanks

---

