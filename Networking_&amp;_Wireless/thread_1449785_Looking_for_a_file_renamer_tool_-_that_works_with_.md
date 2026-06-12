---
title: "Looking for a file renamer tool - that works with SMB://"
date: 2010-04-08
forum: Networking &amp; Wireless
---

### Post by Andre-D on 2010-04-08
please help me find a mass rename tool that handles the virtual mounting that Nautilus/ubuntu does smb://server/share
most applications ignore these "mounted" folders ... and that sucks.. :)
- wish it was standard.

---

### Post by doas777 on 2010-04-08
you will probably have to mount the share to somwhere on the local drive (but not in ~/.gvfs).

check [this]("http://ubuntuforums.org/showthread.php?t=288534") thread and look at the first post, under the heading "Manual Mount" for details on how to do it.

---

### Post by Andre-D on 2010-04-08
yes, I know .. that sucks .gvfs is very convenient, but it needs to be supported by everybody..

---

### Post by doas777 on 2010-04-08
yeah, I really don't understand the .gvfs. The files are mounted there, but you can't touch them.... most annoying. others have said they can just click into it and manipulate it, but I am unable to do that on numerous boxes spanning 3 versions of ubuntu so...

---

### Post by Mountaineer on 2010-04-08
I don't know how welcome this answer will be, but if you know your regex you could use the command line perl rename program.

Use nautilus to browse to your share so it gets mounted in .gvfs.
Open up a gnome terminal and cd to where ever your files are through the .gvfs mount.
Use rename...

This will remove the .bak extension from all files having that extension in the current directory:
rename 's/\.bak$//' *.bak

Lets say you have a heap of images in a folder named like this:
DSC_1299.JPG, DSC_1300.JPG, DSC_1301.JPG, DSC_1302.JPG etc
And you wanted to rename them like "My Party 01.jpg" etc you could do something like this:
rename 's/DSC_1\d(\d\d)\.JPG$/My Party $1.jpg/' *.JPG

adding the argument -n will allow you to test run before you screw things up (regex's being a tricky thing ;))

As I said earlier, I know this isn't optimal if you are a CLI hater, but I'm pretty confident it'll work for you.

---

### Post by doas777 on 2010-04-08
just fyi, I was writting some python code a few weeks ago, that needed to access smb paths. I did a bit of research on it, and with the exception of a third party library, there was no means to access the smb without mounting it first. as a result I just ran the system commands to mount the share to a local temp folder. 

I have since realised that there is no such thing as a one-off way to connect to a share; it's always mounting it locally, the one-off tools and techniques just hide the mounting from us, much as any share in nautilus is invisibly mapped to a location in ~/.gvfs.

in the end, the part of my python script that actually did work was about a 3rd the size of the code that was required to make samba files available to it, which is why many apps do not specify a way to directly use samba shares. the app devs want to leave that up to the OS configuration to handle, rather than putting in code for each and every type of sharing protocol.


oh, and since i didn't get around to saying it, PyRenamer works pretty well, and there is an even better windows app called "Renamer" that runs well under wine.

---

### Post by Andre-D on 2010-04-08
> **Mountaineer said:**
> ....
Use nautilus to browse to your share so it gets mounted in .gvfs.

....is isn't optimal if you are a CLI hater, but I'm pretty confident it'll work for you.


hi , Thanks !   I did not knew gvfs mounted shares were CLI accessible, that was in fact one thing I missed !

I am not a CLI hater, but a CLI learner...  after too many wears in the business, I just recently switched completely to Linux.

---

### Post by Andre-D on 2010-04-09
may I ask for a little regex help ?

I did rename from high to low case like "Ep S01E01.avi" to "Ep s01e01.avi"
since the files are on a samba-share, it failed (same file exists).
So I renamed all to "-Ep s01e01"
the problem is that I cannot remove the "-" 

rename  's/-Ep s(\d\d)e(\d\d)\.avi$/Ep s$1e$2.avi/' *.avi -n

gives:
Unknown option: E
Unknown option: p
Unknown option:  
Unknown option: s
Unknown option: 0
Unknown option: 1

I have tried to read [http://www.regular-expressions.info/reference.html](http://www.regular-expressions.info/reference.html)
and do

rename  's/\-Ep s(\d\d)e(\d\d)\.avi$/Ep s$1e$2.avi/' *.avi -n
rename  's/[\-]Ep s(\d\d)e(\d\d)\.avi$/Ep s$1e$2.avi/' *.avi -n

but it's obvious that I do not completely understand the syntax..yet :)

---

