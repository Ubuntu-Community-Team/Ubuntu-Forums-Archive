---
title: "To obtain write access to a Windows machine?"
date: 2010-04-26
forum: Networking &amp; Wireless
---

### Post by BallisticBrian on 2010-04-26
Hi all
 
For some time now, I have been backing up a windows box (data files only) to a ubuntu machine using the following:
 
mount -t cifs -o user=xxx,password=xxx //windowsshare/ /mnt/
 
 
For the first time I needed to restore some files and found I did not have the correct rights to write to the windows machine.
 
I had already wasted a whole day trying to map the ubuntu machine from windows and failed so this is not an option.
 
I have tried adding write rights to several accounts on the windows machine, also tried adding write rights to "everyone", checked both the share permissions, as well as the folder permissions.
 
I read about chmod, and tried to use the command gksudo to do something but this fails with DISPLAY error. Tried several things to fix this which didn't work and I was just going off on a tangent.
 
In the end I used a CD ROM to copy the files from one machine to another.
 
So for next time I need to restore a file, how can I give myself rights to do so? Any help appreciated.

---

### Post by 98cwitr on 2010-04-26
is this a XP box or Vista/7?

Give 'everyone' 'full control' on the share on the windows side

---

### Post by BallisticBrian on 2010-04-26
It's XP Professional, and I've already tried giving Everyone full permissions.

---

### Post by 98cwitr on 2010-04-26
try

*sudo chmod a+x **mountedSambaShare***

---

### Post by BallisticBrian on 2010-04-26
Using the sudo command with anything after it gives me an input\output error. The gksudo command was also giving me ouput display errors today.

---

