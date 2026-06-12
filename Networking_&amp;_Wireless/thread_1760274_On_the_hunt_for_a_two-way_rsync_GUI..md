---
title: "On the hunt for a two-way rsync GUI."
date: 2011-05-16
forum: Networking &amp; Wireless
---

### Post by Roasted on 2011-05-16
I'm trying to find a good solid rsync GUI that synchronizes in both directions. That way any changes made to the server get put on the desktop, and changes on the desktop get put on server. This is using CIFS, so I will also need it to access .gvfs to access the CIFS share and I also need it to exclude .gvfs within the GUI so it doesn't go through a continual loop, since I want to synchronize the home directory (and .gvfs is within the home directory).

This is for my parents and their backup, otherwise it'd be easy to just drop in a bin bash job on cron and call it a day. But I want something easy I can walk them through over the phone. Plus if the GUI does the job it might be a solution for some users at work.

Any thoughts?

---

### Post by Roasted on 2011-05-17
Some findings:

LuckyBackup:
I thought I'd like LuckyBackup a lot. It appears at first glance to be a solid GUI tool with a lot of features, such as a built in scheduler, etc. The downside is, I can't get Lucky to work right. It'll take my directories, but nothing inside of them. Well, that defeats the purpose. If I can figure this out, LuckyBackup might be the winner. Until then, no can do here.

Grsync:
Solid application. Very simple, very easy to use. The problem? No built in scheduler. I also can't find a two-way sync option, as I would like to utilize a two-way sync so if I do any work from my NAS it'll bounce up to my desktop when the program kicks in. So while it functions, it doesn't have the extra features that make it scream.

Really, if we could combine these two applications (Grsync's simple fact that it works and Lucky's scheduling and two-way sync features) we would have an extremely solid rsync GUI app.

Any input? I hope someone can chime in here and tell me where I'm messing up. :)

EDIT - I came across Deja Dup, which looks VERY simple to set up and even has entries to automatically mount CIFS shares if it's not already mounted. Holy awesome!

The only thing is, it compresses the data. I'm trying to find something that simply synchronizes the data over, so that way I can log into the NAS and see the raw data. So I can see the doc files, jpg files, mp3 files, etc. Not just one massive tarball of a backup.

Can Deja Dup be configured to do this, somehow?

---

### Post by Roasted on 2011-05-19
Up. There's gotta be one out there.

---

### Post by colin.p on 2011-05-19
I've used grsync, lucky and deja-dup. I prefer lucky. I (manually, don't do scheduled) back up my /home, music files and some recorded voice stuff, onto an external HD. I even made a second backup job, for one external drive to another one.
Everything backs up great, however, even though I have it set up to restore (if need be), I've never actually used it. 
If I were you, play around with lucky to make it work. Just an FYI, lucky will make a folder on the destination drive itself. You don't need to specify a destination folder, lucky makes one for you.

---

### Post by Dennis N on 2011-05-19
There is a package called **unison** that syncs both ways. You could look into that one and see if it meets your needs. I checked, and it is still in the Ubuntu repos (at least for 10.04).

---

### Post by Roasted on 2011-05-19
Unison doesn't support CIFS shares, so that one strikes out.

Lucky only transfers empty directories for me. No files. What gives?

---

### Post by ge00rg on 2011-06-27
Have you tried Free File Sync? [http://freefilesync.sourceforge.net/]("http://freefilesync.sourceforge.net/")
It's hard to tell if it's based on rsync but it works really well for me

---

### Post by Roasted on 2011-06-27
> **ge00rg said:**
> Have you tried Free File Sync? [http://freefilesync.sourceforge.net/]("http://freefilesync.sourceforge.net/")
It's hard to tell if it's based on rsync but it works really well for me

It looks real sweet, but it doesn't look like it supports auto mounting of CIFS shares. Likewise, it's also giving me a headache when I put in the path to my already-mounted CIFS share, saying no directory found, etc... I'm using the smb://server/share/ path...

---

### Post by ge00rg on 2011-06-28
> **Roasted said:**
> It looks real sweet, but it doesn't look like it supports auto mounting of CIFS shares. Likewise, it's also giving me a headache when I put in the path to my already-mounted CIFS share, saying no directory found, etc... I'm using the smb://server/share/ path...

I think you'd need to use the absolute path as it exists on your system, either in /media or /mnt

But you're right about auto-mounting a drive, you'd need to script something to do this, which would be pretty simple, FFS doesn't handle mounting.

---

### Post by gianca666 on 2011-09-27
Hi

I am using DirSyncPro (java based) and it works great for two-ways synch.Synchronizes files also from/to network drives. However is not based on rsync, but you might want to give it a try anyway! [http://www.dirsyncpro.org/](http://www.dirsyncpro.org/)

---

### Post by naught101 on 2012-02-16
Try Krusader. It's in the repos. In the tools menu, there's a "synchronise directories option. Kursader works over all common network protocols, and has a really nice, but highly configurable interface for dealing with syncing.

---

