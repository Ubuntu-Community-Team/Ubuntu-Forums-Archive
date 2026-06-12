---
title: "How do I access my shared folders from the internet?"
date: 2010-02-13
forum: Networking &amp; Wireless
---

### Post by jon.reeve on 2010-02-13
I'm looking to set up some kind of a server so my friends can access my music folder. I've managed to set it up so that users on my LAN can do this, but I can't figure out how to make this available on the internet. Is there an easy way to do this? I've been looking at instructions for how to set up an FTP server, but none of these tell me how to configure my router, or what IP address I will need to access the folder from the internet.

---

### Post by nhasian on 2010-02-13
[Port Forward.com]("http://portforward.com/") will help you out with your router.  for ftp you will want to forward port 21 to your computer, for sftp it is port 22.  You should look at sharing an NFS volume instead:

[http://ubuntuforums.org/showthread.php?t=310168](http://ubuntuforums.org/showthread.php?t=310168)

---

### Post by jon.reeve on 2010-02-14
I've got my music folder shared via the "sharing" tab in nautilus folder properties, and I have no trouble accessing it from another computer on my home network. What I want to do is to let my friends access this remotely. What's the easiest way to do this? I tried setting up an SSH server, and even managed to forward the ports, but it shares all my folders, and I only want to share one.

---

### Post by gordintoronto on 2010-02-14
FTP!  Try wu-ftpd from Synaptic.

---

### Post by lavinog on 2010-02-15
If you use ssh, you need to make a user with restricted access.  Don't give them administrative access.

FTP would likely yeild higher transfer rates.  Make sure that you make it so users cant modify or delete the files you share.

---

### Post by bapoumba on 2010-02-16
THreads merged.

---

### Post by jon.reeve on 2010-02-18
Ok, I tried accessing smb://my.ip.address from another computer, and it works within my home network but I can't get it to work outside. I think I forwarded the right port. Anyway I hear samba is not secure? 

If I could set up an ftp server easily, I would. Is there a graphical utility for that? I installed vsftpd but there doesn't seem to be an option for which folder(s) to share. I only want to share two folders, not the entire filesystem. I already have those two folders checked in Nautilus file sharing preferences, I just want to make that share available on the internet. 

I wish there were a step-by-step guide for file sharing for those of us who know nothing about ports, forwarding, servers, permissions, user groups, and the like.

---

