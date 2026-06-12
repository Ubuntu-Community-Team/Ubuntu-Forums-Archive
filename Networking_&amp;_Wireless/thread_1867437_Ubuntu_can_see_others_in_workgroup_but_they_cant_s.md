---
title: "Ubuntu can see others in workgroup but they cant see it (and it cant either)"
date: 2011-10-22
forum: Networking &amp; Wireless
---

### Post by ThunderAeroi on 2011-10-22
As the title says, my new ubuntu install can not see itself in the workgroup but can see everyone else. They can not see it either.  I'm a total noob to Ubuntu so I don't know what information to ptovide you for help. Please help!

I've gone though as many tutorials as I can find looking for the solution but I can't seem to find it.

---

### Post by capscrew on 2011-10-23
> **ThunderAeroi said:**
> As the title says, my new ubuntu install can not see itself in the workgroup but can see everyone else. They can not see it either.  I'm a total noob to Ubuntu so I don't know what information to ptovide you for help. Please help!

I've gone though as many tutorials as I can find looking for the solution but I can't seem to find it.

The answer is in [**_[COLOR="Blue"]this[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1861985") thread.  Read the entire thread.

---

### Post by ThunderAeroi on 2011-10-23
> **capscrew said:**
> The answer is in [**_[COLOR="Blue"]this[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1861985") thread.  Read the entire thread.

Thanks, that solves the issue where the other computers can't see it, but they can't access the share now either.

in Windows 7, they can see the machine, they can see the shared folder, but when I click on the folder to open it, Windows 7 says that it can't find the folder. That it may be misspelled.  Its not.

In Ubuntu the share is only done via Samaba and not through the file manager share.

---

### Post by capscrew on 2011-10-23
> **ThunderAeroi said:**
> Thanks, that solves the issue where the other computers can't see it, but they can't access the share now either.
This sounds like a file and folder permissions problem.  Samba does not override the underlaying file system permissions.  Where are the shares located?  Can you show me what the file permissions are? > 

in Windows 7, they can see the machine, they can see the shared folder, but when I click on the folder to open it, Windows 7 says that it can't find the folder. That it may be misspelled.  Its not.

In Ubuntu the share is only done via Samaba and not through the file manager share.
Post the output of this terminal command ```
testparm -s
```

---

### Post by ThunderAeroi on 2011-10-23
> **capscrew said:**
> This sounds like a file and folder permissions problem.  Samba does not override the underlaying file system permissions.  Where are the shares located?  Can you show me what the file permissions are? 
Post the output of this terminal command ```
testparm -s
```

I am attempting to share a NTFS volume that is mounted by the system user (auto mount by root seems to only mess things up and I can't change permissions)*. Right now I am only trying to share one folder on the volume "iTunes".  The print out of testparm -s is below:

```
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Itunes]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    server string = MachineTwo
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    username map = /etc/samba/smbusers
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    name resolve order = bcast host
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[Itunes]
    comment = Music Library
    path = /media/Storage/Itunes
    valid users = sarahdahl
    read only = No

```

sarahdahl is the samba username for the main account on the computer with a windows username of MachineOneAdmin. 

*, I can't seem to change any permissions anyway as no mater what I change it to, it never stays and goes back to some default setting.

Currently, the Unbuntu machine (MachineTwo) can see itself, but not the windows machine (MachineOne).  The windows machines can see the ubuntu machine and itself but can not get past the "MachineTwo" name as I receive an error saying I don't have permission.  SO i've seen to taken a step back some.

---

### Post by ThunderAeroi on 2011-10-24
I think i got it to work, but I doubt it's pretty.

MachineOne can access the files from the share as can MachineTwo access the shares from MachineOne.

I've been toying around on settings so I can't say what really did it.  But both sides have read and write access.

---

### Post by ThunderAeroi on 2011-10-24
Also I know this isn't the right place but its related.

Is there anyway to force the automount of PySDM to place everything uder the ownership of a none root account?

Cause making it root makes it imposible to share and it seems like ubuntu refuses to allow a user other than the root to mount it.

---

### Post by capscrew on 2011-10-24
> **ThunderAeroi said:**
> Also I know this isn't the right place but its related.

Is there anyway to force the automount of PySDM to place everything uder the ownership of a none root account?

Cause making it root makes it imposible to share and it seems like ubuntu refuses to allow a user other than the root to mount it.

Why did you leave out the ```
netbios = <netbios_name> 
```directive?  I see you changed the *name resolve order* to allow broadcast of the netbios name, but you did not define the netbios name in the smb.conf file.

When you mount a NTFS share using */etc/fstab* you have to explicitly provide permissions for a specific user.  I never do it that way.  I use nautilus to mount the share.  About 1/2 of my shares are on windows hosts with NTFS.  All the permissions are set at the Windows host.  Did you set the share permissions so that all could access (everyone)?

I would not use PySDM at all.  PySDM just uses scripts to create the entries in the /etc/fstab file.  My impression is that PySDM dose not always work correctly. I directly edit edit the fstab configuration.

---

### Post by PayPaul on 2011-10-24
I have a similar problem. I've tried to set the share and permission properties in Nautilus to no avail. Every time I attempt to change them the permissions revert back to "None" or if I change the file access those properties revert back to their original non-accessible configuration. That is no user on a Windows machine on my network can access these shares on my machine created in Nautilus. What is causing this problem? See Screenshot below.

---

### Post by capscrew on 2011-10-24
> **PayPaul said:**
> I have a similar problem. I've tried to set the share and permission properties in Nautilus to no avail. Every time I attempt to change them the permissions revert back to "None" or if I change the file access those properties revert back to their original non-accessible configuration. That is no user on a Windows machine on my network can access these shares on my machine created in Nautilus. What is causing this problem? See Screenshot below.

My first guess (and it is a guess) is that you have not set the ***share permissions*** correctly when creating the share.  The share and its attributes can be seen with this command in the terminal (post the results)```
net usershare info --long
```

My hunch is that you can't change ***share attributes *** using *file attributes* in Nautilus.  These are two separate entities.

Maybe you can describe how you created this share; such as Right Click and then I...

---

### Post by PayPaul on 2011-10-25
> **capscrew said:**
> My first guess (and it is a guess) is that you have not set the ***share permissions*** correctly when creating the share.  The share and its attributes can be seen with this command in the terminal (post the results)```
net usershare info --long
```My hunch is that you can't change ***share attributes *** using *file attributes* in Nautilus.  These are two separate entities.

Maybe you can describe how you created this share; such as Right Click and then I...

Yes, I right clicked on a folder and clicked on Sharing Options. Then allowed guest access and allow others to create and delete files in that folder. 

Here is the result of the command you gave me above. It'll come in handy in future.

```
paulw@ubuntu:~$ net usershare info --long
[bad as me]
path=/media/Free Agent Files And Videos/Free Agent Files/Music/Tom Waits/Bad As Me
comment=
usershare_acl=Everyone:F,
guest_ok=y

[movies 1]
path=/media/Photos And Videos II/Movies 1
comment=
usershare_acl=Everyone:F,
guest_ok=y

paulw@ubuntu:~$ 
```

Everything in that seems like it should work for the users/machines on my network. However they nor myself can access files across the network.

---

### Post by Morbius1 on 2011-10-25
@capscrew:
> Why did you leave out the      Code:
     netbios = <netbios_name> 
directive?  I see you changed the *name resolve order* to allow broadcast of the netbios name, but you did not define the netbios name in the smb.conf file.If he added "netbios name = his existing hostname" tesparm will not show it because that's what it is by default. Easy enough to verify: run "testparm -sv" on an smb.conf without that line and you should see "netbios name = hostname"

@paypaul:
I'm guessing that "path=/media/Free Agent Files And Videos" points to an ntfs partition - most likely an external usb drive of some sort? If that's true then add the following line to the [global] section of /etc/samba/smb.conf
```
force user = morbius
```[COLOR=Blue]*Change morbius to whatever you login user name is for that box.*[/COLOR]
Then restart samba:
```
sudo service smbd restart
```

---

### Post by PayPaul on 2011-10-25
> **Morbius1 said:**
> 

@paypaul:
I'm guessing that "path=/media/Free Agent Files And Videos" points to an ntfs partition - most likely an external usb drive of some sort? If that's true then add the following line to the [global] section of /etc/samba/smb.conf
```
force user = morbius
```[COLOR=Blue]*Change morbius to whatever you login user name is for that box.*[/COLOR]
Then restart samba:
```
sudo service smbd restart
```

The problem is that the smb.conf file is in root and I don't have permissions for that section. That really isn't good. How do I edit this file or change permissions so I can edit it? There's no apparent way to do that in properties as the choices to change permissions are all grayed out!

---

### Post by Morbius1 on 2011-10-25
You personally don't have permissions or you don't know how in invoke it?

To edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```

---

### Post by capscrew on 2011-10-25
> **Morbius1 said:**
> @capscrew:
If he added "netbios name = his existing hostname" tesparm will not show it because that's what it is by default. Easy enough to verify: run "testparm -sv" on an smb.conf without that line and you should see "netbios name = hostname"

Not necessarily.  If nmbd can't determine what the hostname is then there won't be a netbios name.  I think the OP should explicitly provide the netbios name.  This will also cause nmbd to NOT look to DNS (hosts) for name resolution.

---

### Post by Morbius1 on 2011-10-25
It won't do any harm to add it but I wouldn't necessarily assume that he didn't add it because it's not showing up in testparm. Testparm will only show that line if it's different from what samba already had.

---

### Post by PayPaul on 2011-10-25
> **Morbius1 said:**
> You personally don't have permissions or you don't know how in invoke it?

To edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```


With that, everything else falls into place. Thanks.

---

