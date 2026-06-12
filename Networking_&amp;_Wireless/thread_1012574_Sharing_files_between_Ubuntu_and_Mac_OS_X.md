---
title: "Sharing files between Ubuntu and Mac OS X"
date: 2008-12-16
forum: Networking &amp; Wireless
---

### Post by Goombie on 2008-12-16
Ok, here's what I want to do:
Share a folder with some business files (on my computer, running Ubuntu Hardy) with my sister's Macbook running MAC OS X Leopard. I want her to be able to read/write the files from her computer, and save the changes to my computer over the network. Both computers are on the same wireless network.
I've read a bunch of different guides, but I have little experience with Samba, and I haven't been able to make anything work yet. I've gotten as far as her being able to see the files, but only opening them as read only which isn't enough. Any help would be appreciated! :popcorn:
Also, I want to share a USB printer connected to my computer over the network so she can use it from her Mac, but that's a low priority right now. :)

---

### Post by nixscripter on 2008-12-16
For the file sharing, I would suggest NFS instead of Samba. A guide can be found here: [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

The Mac should be able to detect it once you have it set up.

As for the printer, I would suggest sharing it over CUPS. This would allow the Mac to add an IPP printer. Instructions for Debian (which might also work for Ubuntu) are here: [http://forums.debian.net/viewtopic.php?t=10438](http://forums.debian.net/viewtopic.php?t=10438)

Hope this helps.

---

### Post by Goombie on 2009-01-01
Yeah, those should help me. Thanks! :D
If I understand what you said correctly, I just need to set up the NFS server on my Ubuntu box, and then the Mac will detect my shared files?

If I have any problems, I'll post them here and plead for help some more. :)

---

### Post by Goombie on 2009-01-01
Sorry for double-posting, but I'm still running into trouble. Basically, I've tried NFS and gotten an error (the directory I'm sharing doesn't support NFS export), and I haven't been able to get it working with Samba, either. So I'm back to square one. 
Normally I'm a bit of a geek, but I just feel like an idiot whenever it comes to setting up networking like this, since I don't know much (hardly anything) about it. Help! :(

---

### Post by corrosion on 2009-01-04
You should only use NFS in your LAN and only if you consider that your LAN is secure.
Apart from that, the question here is that NFS uses the UNIX id of your user to let or not to let to read/write files. If your uid in Mac OS X is not the same uid in the server, it will not let you to mount the NFS.
I read somewhere to avoid this by setting some flags to the NFS server but it just didn't work for me.
Other chance you have, maybe more simpler, is to use the SMB protocol (the windows share directory and files service). But I simply don't like to use SMB between 2 diferent unixes, it is like... odd to say the least.
You have AppleTalk too, as an option.

Anyway I am looking forward to find something to be able to share NFS between machines independent of the UID.

Sorry for my English, I am not a native speaker.

Regards,

---

### Post by nixscripter on 2009-01-17
There is a way to make this work: user squashing.

Let's say your mac has user ID 501 (I think OS X sartes IDs from 500), and your UNIX user ID is 1001 (Linux starts from 1000). If you mount with normal options, everything will be owned by 501, so it won't work.

The solution is to squash all user IDs to 1001. In /etc/exports:

```
/home/myuser    client.ip.addr.here(rw,all_squash,anonuid=1001)
```

Then your user on Linux should have full access.

---

