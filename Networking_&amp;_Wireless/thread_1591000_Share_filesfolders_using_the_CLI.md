---
title: "Share files/folders using the CLI"
date: 2010-10-08
forum: Networking &amp; Wireless
---

### Post by d1brian on 2010-10-08
Hi.

I want to share certain files/folders with other computers in the network. Now I know how to do this in two ways: using the GUI and modifying the *smb.conf* file, but the GUI may not be available (e.g. connecting to the server using SSH) and the *smb.conf* file takes a little bit of time to modify (and from what I have noticed by using the GUI, the *smf.conf* file does not get modified).

Is there a way to share files/folders using only the CLI and without the need of modifying files?

Thanks in advance.

---

### Post by luvshines on 2010-10-08
If I am not wrong, GUI uses the 'net usershare' CLI internally to create shares.

Maybe that is what you are looking for.
Though I haven't given it a try, but maybe you can explore it more.

PS: It may still require some bit of modifications in smb.conf but those shall be not major ones since nautilus is able to do it, you should too

If you find something useful, some links etc, do share them here :D

GOOD LUCK!!

---

### Post by d1brian on 2010-10-08
> **luvshines said:**
> GUI uses the 'net usershare' CLI internally to create shares.

that is what i was looking for, except it doesn't work very good because the share cannot be created for a specific user.

the syntax to add a share is: 
```
[FONT=Courier New]net usershare add sharename path [comment]  [acl] [guest_ok=[y|n]][/FONT]
```[FONT=Courier New] 
so the command to create a share that can be accesed only by someone that has an account on the server and not by guests is:

[/FONT]```
[FONT=Courier New]net usershare add myshare /mypath "" everyone:f  guest_ok=n[/FONT]
```[FONT=Courier New] 
The downside is that the share is created for every user that has an account on the server. I have tried the following command: [/FONT][FONT=Courier New]
[/FONT]```
[FONT=Courier New]
net usershare add myshare /mypath "" myuser:f  guest_ok=n[/FONT]
```but for some reason it does not allow me to access the share. 

Does anyone know how to make this work for specific users?
[FONT=Courier New] 
[/FONT]

---

### Post by luvshines on 2010-10-09
You can try these commands to see what it says for your user:
```
smbclient -L <server-ip> -U<username>%<password> # For listing the shares

smbclient //<server-ip>/<shared-path> -U<username>%<password> # For accessing them

```

---

### Post by luvshines on 2010-10-09
> **d1brian said:**
> [FONT=Courier New] 
The downside is that the share is created for every user that has an account on the server. I have tried the following command: [/FONT][FONT=Courier New]
[/FONT]```
[FONT=Courier New]
net usershare add myshare /mypath "" myuser:f  guest_ok=n[/FONT]
```but for some reason it does not allow me to access the share. 

Does anyone know how to make this work for specific users?
[FONT=Courier New] 
[/FONT]

I just noticed that you missed the DOMAIN(ie your machine name or netbios name) from username.
From the help:
```
<acl> is an optional share acl in the format "DOMAIN\name:X,DOMAIN\name:X,...."
name may be a domain user or group. **For local users use the local server name instead of "DOMAIN"**
```

I just made one using this and it is working fine:
```
net usershare add Docs /home/scoobydo/Documents "Be safe" Scoob-laptop\\scoobydo:f guest_ok=n
```

---

### Post by d1brian on 2010-10-09
> **luvshines said:**
> I just noticed that you missed the DOMAIN(ie  your machine name or netbios name) from username.
From the help:
```
<acl> is an optional share acl in the format  "DOMAIN\name:X,DOMAIN\name:X,...."
name may be a domain user or group. **For local users use the local  server name instead of "DOMAIN"**
```

it works now, thanks. the thing is that I never thought to also look through the help (i only looked in the manual :oops: - where this is not specified)

---

