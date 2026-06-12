---
title: "Windows XP and Ubuntu 9.10 Network Sharing Problems"
date: 2009-11-24
forum: Networking &amp; Wireless
---

### Post by jdorenbush on 2009-11-24
I ran into this problem a few weeks ago where my Ubuntu desktop was able to view the Windows XP computer on my network, but not able to access the shared files, printer, etc. So essentially it's like Ubuntu knows it's there but it can't interact with it.

Somehow, I fixed it the first time -- I found a solution somewhere on the Internet. Problem now is that I can't remember how or where I found the solution.

If I remember correctly it was a fix that I did on my Ubuntu machine not the Windows computer. So the problems lies within Ubuntu.

Error message when trying to access a folder on the network: *You do not have the permissions necessary to view the contents of "Folder Name".*

- Both the Windows XP and Ubuntu 9.10 are current and up-to-date. 
- Sharing is activated on Windows XP.

---

### Post by Dookert on 2009-11-24
sounds like your having an identical problem to me. lemme know if you figure something out. Ive read all the standard posts on this forum of how its supposed to be fixex but none address my problem. Theres a netowork drive that I want to mount, ubuntu can see it but tells me that it can't mount the drive window share or something along those lines. Funny thing is i can access the public shared folder on my windows machine but none of the other hard drives on the PC

---

### Post by dmizer on 2009-11-24
With any file sharing problem, start by disabling firewalls. This is the most common problem with file sharing.

If all firewalls on both machines have been disabled (and you're absolutely positive there are no firewalls enabled), and you still have problems then please see the 6th link in my sig.

---

### Post by jdorenbush on 2009-11-28
> **dmizer said:**
> With any file sharing problem, start by disabling firewalls. This is the most common problem with file sharing.

If all firewalls on both machines have been disabled (and you're absolutely positive there are no firewalls enabled), and you still have problems then please see the 6th link in my sig.

Turning firewall off didn't work.

I went to the 6th link in your sig. and performed those steps, which didn't resolve the problem either.

Problem 1: Determined it is MSHOME, which I changed in the steps of Problem 2. So Ubuntu is now using MSHOME.

Problem 2: Performed that, but when trying to restart Samba I got an error message:
```
sudo: /etc/init.d/samba: command not found
```

Problem 3: Performed that.

Problem 4: Check that. It doesn't look like I have a firewall.
```
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

---

### Post by Unanimated on 2009-11-28
In 9.10, everything (rather annoyingly) changed to a 'service.' Try this:

```
sudo service samba restart
```

---

### Post by jdorenbush on 2009-11-28
> **Unanimated said:**
> In 9.10, everything (rather annoyingly) changed to a 'service.' Try this:

```
sudo service samba restart
```


```
samba: unrecognized service
```

---

### Post by Iowan on 2009-11-28
[Old way]("http://ubuntuforums.org/showpost.php?p=8272485&postcount=5") *should* still work.

---

### Post by jdorenbush on 2009-11-28
> **Iowan said:**
> [Old way]("http://ubuntuforums.org/showpost.php?p=8272485&postcount=5") *should* still work.

```
sudo: /etc/init.d/samba: command not found
```

That's what I get when I use the restart command. Is it possible that Samba is installed incorrectly or not at all?

---

### Post by Iowan on 2009-11-28
Check via **ps -ef | grep mbd**.
Should see smbd and/or nmbd.

---

### Post by jdorenbush on 2009-11-28
> **Iowan said:**
> Check via **ps -ef | grep mbd**.
Should see smbd and/or nmbd.

```
jeff      4544  4523  0 16:13 pts/0    00:00:00 grep --color=auto [COLOR="Red"]mbd[/COLOR].
```

---

### Post by Iowan on 2009-11-28
Unless I messed up the command (certainly not impossible) that would suggest that Samba is not running.
You did install the server (and smbfs)?

---

### Post by jdorenbush on 2009-11-28
> **Iowan said:**
> Unless I messed up the command (certainly not impossible) that would suggest that Samba is not running.
You did install the server (and smbfs)?

Can you provide more detail on what exactly is to be installed so I can verify if I have the package installed?

Thanks

---

### Post by Iowan on 2009-11-28
In Synaptic (on my Jaunty laptop), the packages are **samba** and **smbfs** - dunno if the procedure has changed in Karmic.

---

### Post by jdorenbush on 2009-11-28
A search for "**smbfs**" produced the following results...
INSTALLED:
```
smbclient
```
NOT INSTALLED:
```
smbfs
pyneighborhood
samba
```

A search for "**samba**" produced a ton of results, so to keep the list short these are the only things that showed as installed.
INSTALLED:
```
samba-common
samba-common-bin
libwbclient0
python-smbc
winbind
smbclient
libsmbclient
```

---

### Post by Iowan on 2009-11-28
I just re-read your original post - and may be misleading you... 
 If you're trying to view shares (from Ubuntu) the server should be unnecessary.The Samba client should be installed by default. If you're trying to share files (from Ubuntu), then the server becomes necessary.

---

### Post by idontknow82 on 2009-11-28
I also have a problem accessing my windows xp shares from ubuntu.  It worked fine in 9.04!  Someone fixed something that wasn't broken,  and now it is broken.

---

### Post by Iowan on 2009-11-29
You've seen [this]("http://ubuntuforums.org/showthread.php?t=1169149") one?

---

### Post by dmizer on 2009-11-29
> **jdorenbush said:**
> 
NOT INSTALLED:
```
smbfs
pyneighborhood
samba
```

Perhaps it will help if you install smbfs.

---

### Post by jdorenbush on 2009-11-30
@Iowan Went through all those steps already. No luck.

@dmizer Installed smbfs and still no luck.

---

### Post by brad1138 on 2009-11-30
I am having the same problem, I have never had any problem on any of the previous versions of Ubuntu, Clicked on network and they pulled up my Windows network for sharing files and printing perfectly.

Now with 9.10  I click on Network icon, get the network window with a "windows network" icon, then when I click that I now (after above steps) get "WORKGROUP" and "MSHOME" but clicking on either I get "Unable to mount location - Failed to retrieve share list from server" I have tried all the above steps, as someone else said, they fixed something that wasn't broken, and now it broken.

---

### Post by ken0069 on 2009-12-23
Well, seems I'm not the only one beating my brains out trying to fix this!  Anyone got a fix that actually works?

Thanks,

Ken

---

### Post by jdorenbush on 2009-12-29
Just completely reinstalled Ubuntu from disc and still getting the same error. I am able to print through this networked computer but not browse the shared files...

/bump

---

### Post by Morbius1 on 2009-12-29
It's always best with network sharing issues to post the output of the following commands. If you're lucky it will produce error messages that someone has seen and resolved before.

Open **Terminal**
Type **smbtree**
Type **findsmb**

---

### Post by jdorenbush on 2009-12-29
> **Morbius1 said:**
> It's always best with network sharing issues to post the output of the following commands. If you're lucky it will produce error messages that someone has seen and resolved before.

Open **Terminal**
Type **smbtree**
Type **findsmb**

No errors, at least not that I saw.
**smbtree**
> MSHOME
\\XCOMPUTER Xcomputer's Computer
\\XCOMPUTER\C$             	Default share
\\XCOMPUTER\ADMIN$         	Remote Admin
\\XCOMPUTER\My Book (G)    	
\\XCOMPUTER\Printer3300    	HP Photosmart 3300 series
\\XCOMPUTER\G$             	Default share
\\XCOMPUTER\SharedDocs     	
\\XCOMPUTER\print$         	Printer Drivers
\\XCOMPUTER\IPC$           	Remote IPC

**findsmb**
> *=DMB
+=LMB
IP ADDR / NETBIOS NAME / WORKGROUP/OS/VERSION 
----------------------------------------------
192.168.1.101 / XCOMPUTER / +[XCOMPUTER] [Windows 5.1] [Windows 2000 LAN Manager]

---

### Post by Morbius1 on 2009-12-29
What happens when you do this:

Press **Alt+F2**
Type [B]nautilus smb://XCOMPUTER/SharedDocs

[/B]If nautilus opens to the remote share bookmark it. It will then appear under "Places" sort of like a "mapped drive" appears in Windows. This isn't a solution it's a work around.

---

### Post by jdorenbush on 2009-12-29
I can access root directories and see the folders contained within. However, when I try and move forward within the directory it won't allow me to.

Example of what I can access:
> //XCOMPUTER/My Book (G) 
//XCOMPUTER/SharedDocs

Example of what I can NOT access:
> //XCOMPUTER/My Book (G)/Files
//XCOMPUTER/SharedDocs/My Music

There is 1 folder though that I am able to access and I am not sure why.
> //XCOMPUTER/SharedDocs/Pinnacle

---

### Post by Morbius1 on 2009-12-29
It's is interesting that /XCOMPUTER/SharedDocs/Pinnacle is the only one of your examples that does not have a space in its path.

I don't have an answer at the moment.

---

### Post by jdorenbush on 2009-12-29
> **Morbius1 said:**
> It's is interesting that /XCOMPUTER/SharedDocs/Pinnacle is the only one of your examples that does not have a space in its path.

I don't have an answer at the moment.

I just tried opening up SharedDocs/microsoft and that didn't working :(

---

### Post by dmizer on 2009-12-29
You said you just reinstalled Ubuntu. You'll need to go through all the steps in the 6th link in my sig.

If you still cannot get connected to XP, then you probably have a problem on the XP side of things.

---

