---
title: "70Kbs copying files over lan. Was a lot higher yesterday"
date: 2009-03-05
forum: Networking &amp; Wireless
---

### Post by robmypro on 2009-03-05
Got a strange issue. I have 2 Ubuntu desktop pc's. The one sharing files runs samba on the folder i am dealing with. I copy a few files over to the shared folder and I am getting 70kbs.

I've rebooted both machines. No change. 

Any idea what would cause this?

---

### Post by robmypro on 2009-03-05
A bit more info. I just tried the same operation from a Vista machine and got 11MB/sec speed. So it seems to be related to just Ubuntu, and possibly with samba.

---

### Post by Huufarted on 2009-03-05
Wireless or wired?

---

### Post by Huufarted on 2009-03-05
Also for the love of all that is holy, don't use samba when you're transferring between 2 Linux PCs.  Use rsync, ftp/sftp, or nfs.

---

### Post by robmypro on 2009-03-06
> **Huufarted said:**
> Also for the love of all that is holy, don't use samba when you're transferring between 2 Linux PCs.  Use rsync, ftp/sftp, or nfs.

Thanks for the replies. There are wireless connections. The Windows PC is also wireless. Okay how do I use NFS or the others?

Yeah, I'm new!

---

### Post by robmypro on 2009-03-11
Anybody have any ideas on this? I am still having horrible performance on my LAN. I can download files from the Internet with far greater speed than I can copy from the PC next to me. 

I want to be able to use Nautilus to move/copy files. What is the best way to set this up? I still need samba, but it is Linux to Linux that is super slow. 

Help!

---

### Post by robmypro on 2009-03-11
A little more info...

I created a share on one Ubuntu PC. I created a new folder, and then selected Sharing Options from the shortcut menu. The good news is I can see the share. The bad news is the speed is horrible. Now this shared folder has nothing to do with the samba share I have. 

Is samba impacting the speed of all my shares, even when they are not listed in the samba app? I am really at a loss to figure this out.

Thanks gang!

---

### Post by robmypro on 2009-03-15
So nobody has any idea how to do this? Getting 35kbs today copying. XP Pro is looking better and better every day.

---

