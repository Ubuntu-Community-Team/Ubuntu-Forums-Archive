---
title: "No such file or directory? (ndiswrapper for wirless USB driver)"
date: 2010-08-24
forum: Networking &amp; Wireless
---

### Post by Sickness.10.4 on 2010-08-24
I am trying to use ndiswrapper for an .inf file located a /home/user/downloads

The full path would then be the file at the end correct?

/home/user/downloads/netr28u.inf

I keep getting the error that couldn't open /home.user/downloads/netr28u.inf: no such file at /usr/sbin/ndiswrapper-1.9 Line 219




Any clues to what i could be doing wrong?

---

### Post by tocado on 2010-08-24
try 

/home/user/Downloads/netr28u.inf

and remember linux is case sensitive where D is D and not d 

=)

---

### Post by gordintoronto on 2010-08-24
Also, /home is incorrect. Instead, use the tilde:
~/Downloads/netr28u.inf

---

### Post by chaanakya_chiraag on 2010-08-24
/home/user = ~ :D
~ is just a shortcut

---

### Post by Sickness.10.4 on 2010-08-24
Well, both of those work...  next problem!

Couldn't create /etc/ndiswrapper/netr28u.inf: Permission denied at /usr/sbin/ndiswrapper-1.9 Line194

Maybe I'm not cut out for Ubuntu, lol

I do have to say that other than the internet not working, thiss blows MS Windows out of the water!!

---

### Post by gordintoronto on 2010-08-24
For files which are NOT part of Home, you need to use sudo. For example, in accessories/Terminal, you can paste this command:

gksudo gedit /etc/ndiswrapper/netr28u.inf

(Use gksudo for GUI commands, just sudo for command-line stuff.)

---

### Post by Sickness.10.4 on 2010-08-25
> **gordintoronto said:**
> For files which are NOT part of Home, you need to use sudo. For example, in accessories/Terminal, you can paste this command:

gksudo gedit /etc/ndiswrapper/netr28u.inf

(Use gksudo for GUI commands, just sudo for command-line stuff.)

Gksudo gedit /etc/ndiswrapper/netr28u.inf brings up a blank text document while gksudo gedit ~/Downloads/netr28u.inf seem to 'run in the background' but only brings up the driver documentation...

---

