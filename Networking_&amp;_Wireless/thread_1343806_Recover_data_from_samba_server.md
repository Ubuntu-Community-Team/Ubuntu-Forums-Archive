---
title: "Recover data from samba server"
date: 2009-12-02
forum: Networking &amp; Wireless
---

### Post by Jim_in_Germany on 2009-12-02
Hi,
I have a samba server running at work and am using it to back up several Windows computers. That works fine.
I also created one shared folder which all of the clients can access.
Despite my warnings to the contrary, one of the users decided to use this shared folder to store her work. Then she deleted it by mistake.
My question: would this file find its way into the trash anywhere?
On the Ubuntu box where the samba server is running there is one main user - "jim" (me).
I have looked in /home/jim/.local/share/Trash/files, but nothing there!
There are several other users on the machine, but I created their accounts for use with the samba server. In this sense they have never physically logged on.
I tried to check the same path for the user that deleted her files, but the folder ".local" doesn't exist in her home directory.
It's a complete long shot, but does anyone have an idea if the files are saveable or not? 
Thanks in advance.

---

