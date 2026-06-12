---
title: "Can't access network shares on Linux machine"
date: 2013-08-01
forum: Networking &amp; Wireless
---

### Post by dwlamb on 2013-08-01
Recently, I acquired a new system and installed Linux.  This was to replace an existing Linux machine.  I installed Samba and configured it using the GUI Samba Server Configuration tool.  I rebooted the Linux machine after Samba set-up.  I can not access the shares on the Linux machine from a Windows PC.  I get a long dialog box indicating I don't have sufficient permissions, etc.  

I do not think it is a Windows issue for the Windows machine could access the Linux shares on the previous machine.  Is there a checklist someone can provide of what to verify?

---

### Post by GwL3eNC on 2013-08-01
Hi dwlmap,

i have never done something special. I use ubuntu with kubuntu on it. There in dolphin i right click the
folder i want to share and use the properties to give a user and a password. Also a guest login is
possible there. After that i connect (LAN) the second pc with windows on it. In the Networks window
i add a networkfolder using the LAN ip of my linux pc and the shares name.

Hope you can solve your problem.

---

### Post by dwlamb on 2013-08-11
Going through the steps again to set-up Samba. I realised the name of the system running Kubuntu was long. 
[LIST]
[*]I have shortened it to something 12 alphanumeric characters long, making the appropriate change to hosts and hostname files.
[*]I did some more research and set-up an smbuser list after setting an smbuser name under the same login id I use.  This step has not been necessary before.
[*]Taking the advice of GwL3eNC, I have also done the method of sharing directories under Properties through Dolphin, denying privileges to Everyone and  only granting full access to my Samba log-in id.
[/LIST]

Despite all this, Windows can see the PC and lists all the shared directories but it will not let me login.  I obtain the Windows log-in dialog.  Even though the old Ubuntu PC is no longer active within the domain, Windows keeps prompting with the old PC\username (i.e. \\<pc-name>\<username>).  [Forget it, Windows. Dammit]  I can change pc-name, of course.  But Windows will not accept the password as valid, looping back to the same dialog box.

---

### Post by dwlamb on 2013-08-11
this has been solved

---

