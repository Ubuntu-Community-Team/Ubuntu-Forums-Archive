---
title: "Windows 7 Networking"
date: 2011-01-16
forum: Networking &amp; Wireless
---

### Post by Rick Montes on 2011-01-16
Greetings Fellow Ubuntuers,

I had this probably a while back and solved it by removing Windows Live Assistant. I upgraded my Windows 7 64 bit computer as well as Ubuntu (The latest version, I believe it is 10).

I can see and access the Ubuntu files/folders from my Windows 7 machine but cant access Windows from Ubuntu.

I can see the computer(s) on the network from Ubuntu but I keep getting the "password" problem again. I don't have a password! 

Once again, can anyone help me solve this dilemma?

Thanks,

Rick

---

### Post by garvinrick4 on 2011-01-16
Ubuntu 10.04 or 10.10 will work out of box with Windows workgroup so it is in setting up
your Windows workgroup correctly in your Windows 7 the same for 32 or 64 bit makes no difference. 
I have same setup with 7 and vista and 9.10 on up to 11.04 and all work out of box. It is not in theory it is applied. 
Check out the Windows box.

---

### Post by Rick Montes on 2011-01-16
Thanks for the reply. I can access the Ubuntu computer through Windows. What do I need to do to allow the Ubuntu computer  to access Windows without the "password"?

---

### Post by garvinrick4 on 2011-01-16
It needs password and shared items in Windows.

---

### Post by Rick Montes on 2011-01-17
The files are shared already. I can see the Windows 7 computer from Ubuntu but cannot access the files/documents without a "password". I have no problems from the other networked Windows computer.

---

### Post by vidtek on 2011-01-17
> **Rick Montes said:**
> Greetings Fellow Ubuntuers,

I had this probably a while back and solved it by removing Windows Live Assistant. I upgraded my Windows 7 64 bit computer as well as Ubuntu (The latest version, I believe it is 10).

I can see and access the Ubuntu files/folders from my Windows 7 machine but cant access Windows from Ubuntu.

I can see the computer(s) on the network from Ubuntu but I keep getting the "password" problem again. I don't have a password! 

Once again, can anyone help me solve this dilemma?

Thanks,

Rick

Garvinrick is right, but it is better to go back to your w7 install and disable all homegroup stuff.  Linux and Samba work fine with XP type networking but have problems with homegroups.
w7 intoduced homegroups and promptly stuffed backward-capabilities with XP and Linux at a stroke.  Gotta love Microsoft

Tony.

---

### Post by Rick Montes on 2011-01-17
I disabled Home group and turned off all services and it still does not work. This is very frustrating. I can access the Ubuntu computer. Any other ideas out there?

---

### Post by Rick Montes on 2011-01-17
I figured it out. I did not have Windows Live Assistant but had Windows Movie Maker. This was the problem. I uninstalled it and now I have access to the Windows 7 files. Wow, I can't believe that this program would cause a network problem. Anyway, thanks for the replies. I hope this helps others.

Rick

---

### Post by Morbius1 on 2011-01-17
Looks like we'll have to add another one to the list:

Windows Live Essentials 2011
Windows Live ID Sign-in Assistant
Microsoft Games for Windows - LIVE
Microsoft Games for Windows - LIVE Redistributable
[COLOR=Blue]Windows Movie Maker[/COLOR]

Notice an ominous trend? Eventually the only way to communicate with a Win7 machine will be to uninstall all of it's applications. ;)

I thought samba released a spnego fix for this.

---

### Post by Rick Montes on 2011-01-17
LOL. I just can't seem to rid myself of Windows completely, yet. However, Ubuntu has been great and the more I use it the more I like it. How do I know if I have the latest version?

---

### Post by garvinrick4 on 2011-01-18
rick montes mark this as solved it is one that is a value to a lot of users with same. Nice you stuck with it until you got it solved. Welcome to Ubuntu like your persistence.

---

### Post by BearDrummer on 2011-02-02
> **Rick Montes said:**
> LOL. I just can't seem to rid myself of Windows completely, yet. However, Ubuntu has been great and the more I use it the more I like it. How do I know if I have the latest version?

The latest version is listed in drop box at [http://www.ubuntu.com/desktop/get-ubuntu/download]("http://www.ubuntu.com/desktop/get-ubuntu/download") ... which happens to be 10.10

---

