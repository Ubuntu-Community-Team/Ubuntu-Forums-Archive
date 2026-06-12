---
title: "Very bad problem with libreoffice"
date: 2020-10-08
forum: Multimedia Software
---

### Post by zohran on 2020-10-08
Hello, i use the last version of Libreoffice into Kubuntu, i have big problem, always when i save document and i leave libreoffice, when i open again it, all of my changes are losts. It's the first time i look this bug... I have updated to the last ppa libreoffice version, but same error. It's strange, because the thumbnails show me the changes, but when i open it, nothing....

---

### Post by CelticWarrior on 2020-10-08
Where are you saving it exactly? The reason I'm asking this is because it can have something to do with permissions and/or hibernation or something.

---

### Post by zohran on 2020-10-08
Just in my document ... i have already try to fix permission with chown, but this is not the problem ...

---

### Post by CelticWarrior on 2020-10-08
Maybe it is the problem... Users without a proper understanding of permissions tend to make things worse.

Have you been running graphical apps with 'sudo', by any chance?
And which version/release of Kubuntu and LibreOffice?

---

### Post by zohran on 2020-10-08
Hum lol, i just use kubuntu before change my laptop, but i'm not beginner, i'm gentoo user since many years ago. I never use sudo with graphical application ...

Kubuntu 20.04, and Libreoffice 7.0.2.2

---

### Post by The Cog on 2020-10-08
I don't understand why you think chown may help. Is the file owned by a different user or something?
Can you post the output of ***ls -l <filename>*** so we can see the permissions and ownership. 
Can you confirm that you are the owner?
Is it inside your home directory?
I'm guessing that there's something odd about the file or its location, not with LibreOffice itself.

---

### Post by SeijiSensei on 2020-10-08
Can you save a copy to /tmp, then close LibreOffice and reopen it again?  Every user has full permissions to /tmp.  If you can save it there, then it's likely a permissions problem with the actual location you are trying to use. (Don't reboot after saving the file as /tmp will be destroyed and created anew.)

---

### Post by zohran on 2020-10-09
[FONT=monospace][COLOR=#54ff54]**zohran@MSI-GS73VR-6RF**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~/Documents**[/COLOR][COLOR=#000000]$ ls -l CV.odt  [/COLOR]
-rw-rw-r-- 1 zohran zohran 13116385 oct.   8 19:06 CV.odt

I'm agree with you, i don't think it's permission problem ...
It's strange, my document just save 3 pictures, but all of rest disappear ...
[/FONT]

---

### Post by Hagar Delest on 2020-12-28
If you "save as" with another name, does it keep the changes?

---

### Post by TheFu on 2020-12-28
Need to see the directory permissions too. That would be the . file - **ls -al ~/Documents**
I'm assuming that is fine and would ask about the file system and SMART data for the storage being used.

Also, any chance that NFS or a snap version of libreoffice got loaded accidentally?  snaps don't work on NFS storage.  ZFS or BTRFS used?  

Can an empty file be created without libreoffice - **touch ~/Documents/foo** does that work?

Without more information, we are just throwing guesses at a brick wall.

---

