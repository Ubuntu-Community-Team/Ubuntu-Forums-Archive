---
title: "Anyway to auto-unmount NFS server from client?"
date: 2009-06-21
forum: Networking &amp; Wireless
---

### Post by Bucky Ball on 2009-06-21
Hi all,

With the fantastic help of another forum member, I have recently set up an NFS network for the three computers we have running at home, using my Laptop as the server.

Now, this is all fine and working great except for one thing (and I am going to try FTP after my exams as it looks like it might fit my purpose better). When the laptop is switched off, my desktop running Xubuntu (the other two machines are running Ubuntu) can't open partitions anymore. When I go Places->File System (for instance but applies to anywhere), the cursor ball just keeps a spinning and finding nothing. No files. 

Restart machine, all is well again.

So, automatically mounts the remote partition on the Lappy, if Lappy is on, files are there, if off the folder is empty but all else works fine.

If I then switch the Lappy (server) off, desktop problem as outlined.

Any ideas how to unmount automatically on the desktop when the Lappy is switched off mid-session? Is there any way the desktop can detect this change and unmount accordingly?

Incidentally, I can open a terminal after the Lappy has been switched off and when I input:

sudo umount Lappy

... can't find Lappy (which is the mount point in /media directory in the desktop).

---

### Post by LeeU on 2009-06-23
I have just installed NFS (Hardy 8.04) and was wondering the same thing. I wasn't able to find too much on Google. I was also wondering what would happen if the client just shut down without unmounting.

---

### Post by Bucky Ball on 2009-06-24
Client shutting down seems to be fine here. Just server shutting down. The past couple of times I have switched the laptop (server) on, it has thrown a message:
```

exportfs: files has no inet address
```

I think it was inet or iinet. Just about to investigate that. This is with none of the other machines on so perhaps related. Just finished my last exam for the semester so now I can devote some unhindered, serious study time to solving a couple of niggling Ubuntu issues and learning something new along the way! haha. 

Will post with any further developments regarding our mutual issue.

---

