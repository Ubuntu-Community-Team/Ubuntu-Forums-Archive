---
title: "Synchronize Ubuntu folder to Windows"
date: 2011-04-24
forum: Networking &amp; Wireless
---

### Post by paulvp on 2011-04-24
Hello All,

OK, I've searched and searched but can't find an answer to my question.  I have a Ubuntu machine and a Windows 7 machine on my home LAN.  I want to synchronize the contents of a folder on my Ubuntu machine to a folder on the Windows 7 machine.  From what I can tell, my best (only?) option is to use rsync.  I do not want this to be automatic.  I'm OK with the various switches required by rsync but I don't know how to point it at the Windows 7 machine.

Lets say the computers are as follows:
Ubuntu Machine:
User name = abc
Computer name = linbox
Folder (to be sync'ed) = copyme (in my Home folder)

Windows 7 Machine:
User name = abc
Computer name = Win7
Folder = copyme (on the C: drive.  ie C:\copyme)  Note that this folder already exists and is shared.  I am able to mount and browse this folder from my Ubuntu machine.

What I need is a specific example of the command required to sync the Ubuntu folder to the Windows folder.  I believe it will start something like this:

rsync  -va --delete /home/abc/copyme/

Then what??
(Yes I've read the rsync manual - it doesn't help)
Note 1. I want to perform the sync from the Ubuntu machine.
Note 2. I don't want to use use a cloud-based solution. ie Dropbox

Thanks,
Paul vP

---

### Post by joberly on 2011-04-24
You need the source and destination directory.

> rsync -va --delete /home/abc/copyme/ /mounted/windows/share

Will copy your files from /home/abc/copyme to the windows share, while deleting files in the windows share that do not exist in /home/abc/copyme.

---

### Post by paulvp on 2011-04-25
OK, thanks for the reply.  Are you saying that's *exactly* what I need to type or do I need to substitute something for the "/mounted/windows/share" part of it?

I've tried using exactly what you've suggested but nothing seems to happen.  No error messages or anything.

Thanks,
Paul vP

---

### Post by joberly on 2011-04-25
No, that's not the exact syntax. You say that you can mount your windows share in a previous post. Where are you mounting it? (Where are you accessing it?)

---

### Post by paulvp on 2011-04-26
I mount the windows shared folder by doing this:

Places > Network > Windows Network > WORKGROUP > Win7 

then right click on the folder, left click on "Mount".

I now have an icon on my Ubuntu Desktop which I can double click to open and browse within.

Thanks again for your help.
Paul vP

---

### Post by joberly on 2011-04-26
When you mount a drive that way, it mounts to /media/UUID (where UUID is the seriously long hardware identifier for that drive).

So, with what I wrote, /mounted/windows/share would essentially be /media/UUID. Are you familiar with the command line?

Simply do an ls /media to see what the folder name is for the drive in question, and change it appropriately for your rsync command.

---

### Post by paulvp on 2011-04-26
OK, I've checked that out and there is a /media/UUID folder on this machine but it appears to be the Windows 7 partition that is on this computer (I'm dual booting Ubuntu and Win7 on this machine).

I can't see anything for the shared folder that is on the other Windows 7 machine.

Regards,
Paul vP

---

