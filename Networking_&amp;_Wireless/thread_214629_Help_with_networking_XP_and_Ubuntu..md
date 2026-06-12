---
title: "Help with networking XP and Ubuntu."
date: 2006-07-12
forum: Networking &amp; Wireless
---

### Post by AceRimmer on 2006-07-12
Hi.  I have a network with a PC with WinXP SP2, a Dapper Drake machine, and a Coyote Linux based router that routes my DSL.  All the computers can see each other, but I cannot get the XP machine to find the folder I have set to share via SMB on the Dapper box.  It finds the machine "Dagon" in the WORKGROUP, but when I try to access it I get a prompt for a password and it doesn't accept my Ubuntu user passworld.  

For example, when I log into Linux my username is *foo*, and my password is *bar*, and the machine name is *Dagon*.  Everything works fine on the Linux end.  Places->Network Servers shows the Windows machine and I can access its shared folders.  But when I try to access *Dagon* from the XP box I get a prompt that shows username *Dagon\foo* and I type in the password *bar* and it rejects it.  Is there a different password for samba sharing or should it connect with my user info that I log into Ubuntu with?  Do I have to setup something on the Linux side to allow the Windows machine to access it? I setup shared folders under system->shared folders and everything seems to be ok.  

What am I missing?

---

### Post by SonicSteve on 2006-07-12
I know this isn't exactly helpful but... I have the exact same thing happening. My ubuntu box (really like the new version) can see and access my winxp pro box perfectly. However the windows prompts for a password and it seems that it's impassable. 
This kind of reminds me of the XP to win98 issue of IPC$ share problem. My hunch is that something in the smb.conf file is blocking access. 

Someone with experience please help us.
](*,) :-k

---

### Post by Tweek84 on 2006-07-13
By default samba does not use your user account passwords.

You'll need to use: smbpasswd to set the password for your user account. I believe the first time you have to use sudo, so

sudo smbpasswd <foo>

then you should be able to login from the XP machine.

---

### Post by AceRimmer on 2006-07-13
Thanks, I'll give that a try.

---

### Post by dasyar613 on 2006-07-13
Thanks Tweek84, I tried your suggestion, and it worked. Now, if I could only get ubuntu to get to the machine that has Vista beta installed.

---

### Post by Thenotsowyzewun on 2006-07-14
Cheers Tweek, you fixed my problem too (had the same one) :D.
Now I've just got to work out how to get ubuntu to see my windows shares...

---

