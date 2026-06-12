---
title: "Command Line Access To Networked WD MyBookLive Drive"
date: 2012-06-14
forum: Networking &amp; Wireless
---

### Post by wdelv on 2012-06-14
I successfully installed a 2TB WD MyBookLive drive connected to my home's router.  I can access the drive's file system using the GUI tool, **files**, under the **Network** left menu option or through the browser using the URL, **mybooklive/UI/** which brings up WD's dashboard.  However, I would like to access this drive using the terminal (command line) prompt for scripts, etc.
Where do I find this using the terminal?

---

### Post by sanderj on 2012-06-15
Easy first step:

With a GUI go the drive. Then open a terminal, and type "mount". You should see the drive mapped and mounted onto /mnt/.... From the command line you can access that drive.

---

### Post by wdelv on 2012-07-13
**[SIZE="3"]Solved (kinda):[/SIZE]**
After navigating to ***Network->Browse Network*** link on left pane of **files** GUI application, the ***MyBookLive/Public*** folder becomes mounted under ~/.gvfs.
I just need a way to accomplish this mount from the script instead of manually navigating with **files**.

---

### Post by bab1 on 2012-07-13
> **wdelv said:**
> **[SIZE="3"]Solved (kinda):[/SIZE]**
After navigating to ***Network->Browse Network*** link on left pane of **files** GUI application, the ***MyBookLive/Public*** folder becomes mounted under ~/.gvfs.
I just need a way to accomplish this mount from the script instead of manually navigating with **files**.

Is this SMB or NFS that you are trying to mount?  The ~/.gvfs location is where Nautilus mounts SMB for sure.  You do not need to mount it there if you don't want to.  You could mount it at ~/mnt or ~/nas or ~/data or outside your home directory as in /data or /mnt.  In other words its its up to your situation.  How many folks will be using the NAS on your network?  What OS's are you using on the network?

---

