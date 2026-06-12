---
title: "Network between XP and Ubuntu with samba / passwd problem ?"
date: 2006-06-10
forum: Networking &amp; Wireless
---

### Post by andlinux on 2006-06-10
Hi

I have ubuntu on my laptop and on the desktop is windows xp home.
I want a network between those computers so I installed samba.
The computers are connected true a router, laptop is wireless and the desktop with a cable.

I already searched on this forum and found some stuff from samba, I tried several things but with no luck. When I open the xp shared map with nautilus then I can copy some files from the XP-pc to the ubuntu-laptop, but not all the files.
When I want to copy a file from ubuntu to XP that's not working at all.

I think that there a problem is with the passwd file and the account's.
I use admin as login name for the xp box and when I try to add that to the passwd file with this command: sudo smbpasswd -a admin

I get this: Failed to initialise SAM_ACCOUNT for user admin. Does this user exist in the UNIX password database ?
Failed to modify password entry for user admin

What can I do to solve this ?

---

### Post by fargoth on 2006-06-10
if you'd change the line 
```
security = user
```
to
```
security = share
```
you won't need to set a user account in the first place...

but if you insist on making a user account, you have to add a user by that name  to your system (i think, haven't tried that one, i just typed in my user's details on smbpasswd...)

---

### Post by andlinux on 2006-06-11
[QUOTE=fargoth]if you'd change the line 
```
security = user
```
to
```
security = share
```
you won't need to set a user account in the first place...

but if you insist on making a user account, you have to add a user by that name  to your system (i think, haven't tried that one, i just typed in my user's details on smbpasswd...)[/QUOTE]
Is it safe then ?

---

### Post by linuchsan on 2006-06-11
You can use smbmount for your windows share
smbmount //ip_windows_xp/share_name /some/mount/point -o username=admin
note:
You have to install smbfs first

---

### Post by andlinux on 2006-06-11
[QUOTE=linuchsan]You can use smbmount for your windows share
smbmount //ip_windows_xp/share_name /some/mount/point -o username=admin
note:
You have to install smbfs first[/QUOTE]
I changed it to "share" but I still cannot copy to my xp-box.

I already tried it with smbmount (I did it always with that) but it's the same result.

---

### Post by linuchsan on 2006-06-11
And what happens when you run smb://ip_windows_xp/sharename in Konqueror?

---

### Post by nikolokolus on 2006-06-11
[QUOTE=andlinux]I changed it to "share" but I still cannot copy to my xp-box.

I already tried it with smbmount (I did it always with that) but it's the same result.[/QUOTE]

You may not be having a linux or samba issue at all.  When you set up your shares under windows did you make them writeable by other users?

(I'm not on a windows machine, so bear with me).  Get on your windows box, open the file manager and go to the folder that you are sharing, right click on it and go to sharing and security, explore the tabs that pop up and there should be some tick marks to make the share writeable by other users, if this is already checked then you may need to reconfigure samba. . . but at least double check the settings on your windows box before you go the trouble of reconfiguring your smb.conf file.

---

### Post by Paradoxx on 2006-06-11
[QUOTE=fargoth]if you'd change the line 
```
security = user
```
to
```
security = share
```
you won't need to set a user account in the first place...

but if you insist on making a user account, you have to add a user by that name  to your system (i think, haven't tried that one, i just typed in my user's details on smbpasswd...)[/QUOTE]

I'm having the same problem. 

Files from windows -> ubuntu is fine
Files from ubuntu -> windows doesn't work... it asks for password, and i don't know what that is ?.

when you are talking about changing the secure lines to share... where is that ? 

ps. I'm bit of a newbie... so please be patient with me :)

---

### Post by andlinux on 2006-06-12
[QUOTE=nikolokolus]You may not be having a linux or samba issue at all.  When you set up your shares under windows did you make them writeable by other users?

(I'm not on a windows machine, so bear with me).  Get on your windows box, open the file manager and go to the folder that you are sharing, right click on it and go to sharing and security, explore the tabs that pop up and there should be some tick marks to make the share writeable by other users, if this is already checked then you may need to reconfigure samba. . . but at least double check the settings on your windows box before you go the trouble of reconfiguring your smb.conf file.[/QUOTE]
Ok, I changed that on the windows-box but I can try it later.

---

### Post by EmmEff on 2006-06-12
> Files from ubuntu -> windows doesn't work... it asks for password, and i don't know what that is ?.

You need to specify the username and password you use on the Windows side.

---

### Post by andlinux on 2006-06-13
Ok when I try to copy a file from windows to linux, some files I can copy but not all :s

---

### Post by Paradoxx on 2006-06-13
[QUOTE=EmmEff]You need to specify the username and password you use on the Windows side.[/QUOTE]

I've tried "sudo smbpasswd -a admin" but i just get the same errormassage discriped in first post... 

How can i set the password ?

---

