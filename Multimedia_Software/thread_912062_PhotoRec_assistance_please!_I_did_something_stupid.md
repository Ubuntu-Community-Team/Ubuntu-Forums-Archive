---
title: "PhotoRec assistance please! I did something stupid."
date: 2008-09-06
forum: Multimedia Software
---

### Post by MarkTBSc on 2008-09-06
In attempting to upgrade my system, I accidentally formatted a drive containing a lot of stuff of sentimental value. Mostly holiday photos and my email backup from Thunderbird. I'd very much like to recover as much as possible and PhotoRec looks like a good bet. However...

Apparently PhotoRec copies all recovered files back to the folder it's run from but I want it to save everything to a spare drive. I've got an 80gb drive with Windows and Linux dual booting on it, a 160gb NTFS formatted drive I'd like to recover from and a 500gb NTFS formatted drive I'd like to recover it all to.

So... Do I need to pipe it or something? I'm not a raw beginner here but I'm damn close to it.

Ummm... Help? Please?

---

### Post by Irihapeti on 2008-09-06
I've not actually used Photorec myself, but it looks as though all you need to do is cd to the directory you'll be recovering to.

You might find it useful to look at the Photorec wiki:
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

This article [http://www.linux.com/articles/56588](http://www.linux.com/articles/56588) describes someone's experience with using it.

I hope that gets you started. Maybe someone else who knows more about it than I do will be able to tell you more.

Irihapeti

---

### Post by aysiu on 2008-09-06
Photorec allows you to save to external media. It defaults to save in /home/ubuntu (if you're using a live CD), which would obviously fill up too quickly (especially if you're, again, using a live CD).

You can use the right arrow on **..** to go up a directory and then the right arrow on any directory to go into the directory.

Here are some detailed instructions:
[http://www.psychocats.net/ubuntucat/recovering-windows-files-with-a-ubuntu-cd-iii-deleted-files/](http://www.psychocats.net/ubuntucat/recovering-windows-files-with-a-ubuntu-cd-iii-deleted-files/)

The instructions are Windows-oriented, but it's pretty much the same deal for Ubuntu, except it'll probably be an Ext3 system instead of NTFS.

---

### Post by MarkTBSc on 2008-09-07
I'm deeply indebited to you guys. I'm running PC Inspector in Windows at the moment but as soon as that's done (another three days by the progress bar) I'll take a good look at PhotoRec, which I suspect is superior. 

Thank you again for the links and pointers.

---

