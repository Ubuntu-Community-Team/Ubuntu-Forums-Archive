---
title: "Share a drive/partitions on a network. How ?"
date: 2006-06-08
forum: Networking &amp; Wireless
---

### Post by SynapseR on 2006-06-08
Hi,

Can someone please explain how to share multiple NTFS drives (partitions) on a network that contains both windows and linux PC's.
The host computer has an Ubuntu Partition which it runs from, and multiple other   NTFS partitions which I want to share (R + W access) on the network.

--Thanks

---

### Post by DJiNN on 2006-06-08
[quote=SynapseR]Hi,

Can someone please explain how to share multiple NTFS drives (partitions) on a network that contains both windows and linux PC's.
The host computer has an Ubuntu Partition which it runs from, and multiple other   NTFS partitions which I want to share (R + W access) on the network.

--Thanks[/quote]

I'd be REALLY interested in this one as well, but i don't think you'll get an easy answer. I never have..... it's really hard work getting something akin to "Simple File Sharing" working on Linux......  I've tried it several times, with a mixture of machines (Both Ubuntu & XP) & it's never worked yet.... :)

DJiNN

---

### Post by DJiNN on 2006-06-09
[quote=SynapseR]Hi,

Can someone please explain how to share multiple NTFS drives (partitions) on a network that contains both windows and linux PC's.
The host computer has an Ubuntu Partition which it runs from, and multiple other   NTFS partitions which I want to share (R + W access) on the network.

--Thanks[/quote]

Well, once again i find myself well & truly eating my words, as i have just managed to get it working & now have access to my Ubuntu box from my Win Box etc... Which is exactly what i wanted.

I'm running Dapper, and all i did was go to System/Administration/Shared Folders & chose what folders i wanted to share & the settings etc. (Use the "smb" setting. 

Then open a terminal & type  "sudo smbpasswd -a user" (Where user is the name that you wish to use to access the machine - i used my login name on the Ubuntu box) & it'll ask you to chose a password..... do that, then try & access your Ubuntu box from your Winbox & it'll ask you for the Username (This is the Samba Username for Winshares) & the password, and there you go.... you should have access to your machines. 

My Dapper machine by the way, was already set up to access the Winbox.... Don't know why, but it just worked that way. :) 

Let me know how you get on & good luck.... 

DJiNN

---

### Post by dvarsam on 2006-06-09
Hello!

If you want an easy way to Network your 2 Ubuntu PCs, I have figured out how to do this with NFS & SSH...

Please read the article here: [http://ubuntuforums.org/showthread.php?t=186063](http://ubuntuforums.org/showthread.php?t=186063)

Be patient & read it up to the end...

Good Luck!

P.S.> I have NOT experimented yet with "samba"... (btw: I have _just_ managed the NFS...)

---

