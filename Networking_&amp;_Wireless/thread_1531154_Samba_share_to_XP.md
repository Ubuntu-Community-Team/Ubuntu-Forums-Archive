---
title: "Samba share to XP"
date: 2010-07-14
forum: Networking &amp; Wireless
---

### Post by Rubicon421 on 2010-07-14
I'm trying to set up Samba to share a few folders on a NTFS partition on my dual boot Win7/Mint 9 system. 

I have installed Samba and tried to share a folder from the properties menu in Nautilus but I get this:

'net usershare' returned error 255: net usershare add: cannot share path /media/Back_Up/MUSIC/MUSIC - Full Albums as we are restricted to only sharing directories we own.
    Ask the administrator to add the line "usershare owner only = false" 
    to the [global] section of the smb.conf to allow this.

If I try the same thing but as root, or opening the folder as administrator then I get:

'net usershare' returned error 255: net usershare add: cannot convert name "Everyone" to a SID. Invalid parameter.

I have the folder set up in Samba's server configuration settings as USER, with :allow access to everyone" and NO PASSWORDS

The Windows XP machine trying to access it does not have a password and only has one account.

---

### Post by Morbius1 on 2010-07-14
Something doesn't make sense about all this.
> 'net usershare' returned error 255: net usershare add: cannot share path  /media/Back_Up/MUSIC/MUSIC - Full Albums as we are restricted to only  sharing directories we own.You got that error because you attempted to use Samba Nautilus-share on a file you don't own. SO that leads to the question: How are you mounting /media/Back_Up. If you mounted it through Places then it would have mounted with you as owner so you shouldn't have gotten that error. That means you must have mounted it through fstab. Please post the output of this command:
```
cat /etc/fstab
```> I have the folder set up in Samba's server configuration settings as  USER, with :allow access to everyone" and NO PASSWORDS
This is Classic-share and is a completely different method. Please post the output of the following command so we can see how you are set up:
```
testparm -s
```

---

### Post by Rubicon421 on 2010-07-14
UUID=C4B03B26B03B1DFC /media/Back_Up ntfs-3g defaults 0 2
UUID=9CB8F7FFB8F7D5AC /media/Win7 ntfs-3g defaults 0 0
UUID=c4ad35ce-60ed-4b5b-ae2c-4d4542d2a725 / ext4 defaults 0 1
UUID=3a9ef491-a657-40dc-b37c-5e1c26fc7264 swap swap sw 0 0


Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[test]"
Processing section "[Movies]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    workgroup = TOOL
    server string = %h server (Samba, LinuxMint)
    encrypt passwords = No
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
    dns proxy = No
    usershare allow guests = Yes
    usershare owner only = No
    panic action = /usr/share/samba/panic-action %d

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No
    browsable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[test]
    path = /home/droid-pc/test
    valid users = droid-pc
    read only = No
    guest ok = Yes

[Movies]
    path = /media/Back_Up/Movies
    guest ok = Yes
droid-pc@droid-pc-desktop ~ $ 


I installed mountmanager so I think that is what is being used to automount the NTFS drive on startup. 

I added the "_" in the UUID line for "Back Up" on the drive name because I was getting an error during the start up. I can't remember the error exactly but it was something about being unable to mount, press s to skip or m for manual. After I added the underscore it started up fine.

---

### Post by Morbius1 on 2010-07-14
Well despite the fact that you used mountmanager this looks OK to me. Probably because you intervened and added the "_":
>          UUID=C4B03B26B03B1DFC /media/Back_Up ntfs-3g defaults 0 2That would have created a mount with owner = root and read / write access to everyone.

There is one obvious error in you smb.conf:
>      encrypt passwords = No That should be changed to Yes even though no explicit password are being passed.
So do a:
```
gksu gedit /etc/samba/smb.conf
``` and change the above to Yes. Then save the file, exit gedit, and restart samba:
```
sudo service smbd restart
```

---

### Post by capscrew on 2010-07-14
> I'm trying to set up Samba to share a few folders on a NTFS partition on my dual boot Win7/Mint 9 system. 

I have installed Samba and tried to share a folder from the properties menu in Nautilus but I get this:


I just have to ask this question; Are you sharing this from one partition to another on ***a single system***?  By that I mean you are not sharing between to hosts.

If this is correct (and I have done it myself), I wonder why you feel you need to do that.  You can (and have) mounted the NTFS partition to the local Linux file system and you should be able to see it under "Computer" in Nautilus or do this in the CLI```
cd /media/Back_Up
```

All the files should be visible.  I believe if you mount it using your user name then you can read and write to the directory.

---

### Post by Rubicon421 on 2010-07-14
OK, well that worked perfectly, as far as getting rid of the error and sharing the folder. But it still doesn't show up in the network on the XP machine. 

The folder shows the little hand icon holding it now, showing that it is shared and I didn't get the error this time. 

I'm going to restart both machines in a minute and see if that helps now that the folder is shared.

---

### Post by Rubicon421 on 2010-07-14
> **capscrew said:**
> I just have to ask this question; Are you sharing this from one partition to another on ***a single system***?  By that I mean you are not sharing between to hosts.



No, I have a dual boot with Windows 7 and Mint 9. I am trying to share files from the NTFS partition of the dual boot machine with a second system that only has XP. They are both connected to a router and are networked when booted to Windows 7.

---

### Post by capscrew on 2010-07-14
> **Rubicon421 said:**
> No, I have a dual boot with Windows 7 and Mint 9. I am trying to share files from the NTFS partition of the dual boot machine with a second system that only has XP. They are both connected to a router and are networked when booted to Windows 7.

I wasn't sure.  I would follow @Morbius1's advice in these matters.  :D

---

### Post by Rubicon421 on 2010-07-14
Still not working after reboot of both machines. The Linux system doesn't show up in the network under workgroup computers, and the shared folders don't show up under the shared network folders.

---

### Post by Morbius1 on 2010-07-14
> The folder shows the little hand icon holding it now, showing that it is  shared and I didn't get the error this time. Uh-oh. You only get the little hand icon when you're using nautilus-share. There are two completely different methods of using samba to share files and your're using both. That means I need to see the output of more commands:
```
net usershare info
sudo net usershare info
```Is it only this share that's not showing up: /media/Back_Up/MUSIC/MUSIC - Full Albums

BTW, I hope you called that share something other than [COLOR=Blue]MUSIC - Full Albums[/COLOR]. I don't think it matters anymore if its 12 characters or less. I think that's prior to WinNT/2K but I don't remember about the spaces in share names. By habit I don't have spaces in anything in Linux.

---

### Post by Morbius1 on 2010-07-14
2 quick things to check.

Firewalls. Disable them. If you haven't touched the firewall on your linux systems you are OK. WinXP is another matter.

Linux machine name length. By default Samba will use the host name of the machine to represent itself on the network. But it has to be 15 characters or less. When you open a termainl the host name is what appears after the @ sign. Is it more than 15 characters?

[COLOR=Blue]EDIT[/COLOR]: Sorry to leave you in this state but I've been at this far too long today. capscrew know more than I do anyway.

---

### Post by Rubicon421 on 2010-07-14
> **Morbius1 said:**
> Uh-oh. You only get the little hand icon when you're using nautilus-share. There are two completely different methods of using samba to share files and your're using both. That means I need to see the output of more commands:
```
net usershare info
sudo net usershare info
```Is it only this share that's not showing up: /media/Back_Up/MUSIC/MUSIC - Full Albums

BTW, I hope you called that share something other than [COLOR=Blue]MUSIC - Full Albums[/COLOR]. I don't think it matters anymore if its 12 characters or less. I think that's prior to WinNT/2K but I don't remember about the spaces in share names. By habit I don't have spaces in anything in Linux.


Yes, it's the only share I have made so far. I just installed Mint 9 on this system. And I named the share "MUSIC".

---

### Post by Rubicon421 on 2010-07-14
> **Morbius1 said:**
> 2 quick things to check.

Firewalls. Disable them. If you haven't touched the firewall on your linux systems you are OK. WinXP is another matter.

Linux machine name length. By default Samba will use the host name of the machine to represent itself on the network. But it has to be 15 characters or less. When you open a termainl the host name is what appears after the @ sign. Is it more than 15 characters?

[COLOR=Blue]EDIT[/COLOR]: Sorry to leave you in this state but I've been at this far too long today. capscrew know more than I do anyway.

Yes, it's 16 characters actually. Will it get truncated or just not work at all because it's over 15?

EDIT:
Added another share and still nothing. Here's the output:

[music - full albums]
path=/media/Back_Up/MUSIC/MUSIC - Full Albums
comment=
usershare_acl=Everyone:R,
guest_ok=y

[movies]
path=/media/Back_Up/Movies
comment=
usershare_acl=Everyone:R,
guest_ok=y


The second command had no output. No error either, just went right back to a new prompt with the $.

---

### Post by capscrew on 2010-07-14
> **Rubicon421 said:**
> Yes, it's 16 characters actually. Will it get truncated or just not work at all because it's over 15?
The short answer is:  I don't know. Samba converts the Linux host name to a NetBIOS name and adds a server type to it.  To see netbios name you should be able to use these two commands from the CLI:```
smbclient -L [Linux_hostname]
smbtree
```> 

EDIT:
Added another share and still nothing. Here's the output:

[music - full albums]
path=/media/Back_Up/MUSIC/MUSIC - Full Albums
comment=
usershare_acl=Everyone:R,
guest_ok=y

[movies]
path=/media/Back_Up/Movies
comment=
usershare_acl=Everyone:R,
guest_ok=y


The second command had no output. No error either, just went right back to a new prompt with the $.

Can you see them now?  Sometimes it takes awhile for the browse list to be updated.

---

### Post by Morbius1 on 2010-07-15
> Yes, it's 16 characters actually. Will it get truncated or just not work  at all because it's over 15?It's got to be 15 characters or less . The easiest way to do this for me was to use samba itself.
```
gksu gedit /etc/samba/smb.conf
```Add the following line to the [global] section of smb.conf:
```
netbios name = something-15-characters-or-less
```[COLOR=Blue]*No spaces or weird characters please*[/COLOR]

I don't mean to nag about this but you really should stop using Nautilus-share and Classic-share on the same target directories.
These are Nauilus-shares:
> [music - full albums]
path=/media/Back_Up/MUSIC/MUSIC - Full Albums
comment=
usershare_acl=Everyone:R,
guest_ok=y

[movies]
path=/media/Back_Up/Movies
comment=
usershare_acl=Everyone:R,
guest_ok=yThis is the Classic-share:
> [Movies]
    path = /media/Back_Up/Movies
    guest ok = Yes2 different samba methods. 2 different share definition locations. 2 different ways of enabling shares. Use one form or the other. Since the Nautilus-shares now outnumber the classic-shares, I would eliminate the Classic-share.

When you're done with all the changes restart samba:
```
sudo service smbd restart
```

---

### Post by Rubicon421 on 2010-07-15
OK, I renamed my netbios name to something shorter and disabled one of the types of shares. 

I see the difference you are talking about but which one is which from the GUI side of things? 
There's the method of adding a share through the folder properties, or you can use the Samba configuration settings. 

I unshared both folders from the properties of the folder and left the Samba settings the same. 

With the netbios name change, where in the global section should it go? Does it matter as long as it is on it's own line of text? I put on it's own line below the [Global] line.

[COLOR=Blue]EDIT[/COLOR]: By the way, after those changes, still not working. Restarted Samba, restarted the XP machine and still no shares showing up on XP's Network Places or Work Group Computers.

I have made several changes to the smb.conf file as well as the Samba Configuration settings since starting. Should I uninstall and reinstall it? Will that write a new smb.conf?

---

### Post by Morbius1 on 2010-07-15
> There's the method of adding a share through the folder propertiesThat's Nautilus-share
> or you can use the Samba configuration settingsThat's classic-share
>  I unshared both folders from the properties of the folder and left the  Samba settings the same. You deleted the Nautilus-shares and left the Classic shares. That's fine either one will work. Just to make sure though you should run a **net usershare info** and make sure it comes back blank. That will tell you if all the Nautilus-shares are gone.
> I have made several changes to the smb.conf file as well as the Samba  Configuration settings since starting. Should I uninstall and reinstall  it? Will that write a new smb.conf?     There's a way to reset just the smb.conf file itself but before we go down that route why not post your smb.conf file:
```
testparm -s
```

---

### Post by Rubicon421 on 2010-07-15
net usershare info returned nothing.

droid-pc@droid-pc-desktop ~ $ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[test]"
Processing section "[Movies]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    workgroup = TOOL
    netbios name = DROID-PC
    server string = %h server (Samba, LinuxMint)
    map to guest = Bad User
    obey pam restrictions = Yes
    guest account = droid-pc
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    username map = /etc/samba/smbusers
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    usershare owner only = No
    panic action = /usr/share/samba/panic-action %d
    guest ok = Yes

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No
    browsable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[test]
    path = /home/droid-pc/test
    valid users = droid-pc
    read only = No

[Movies]
    path = /media/Back_Up/Movies
droid-pc@droid-pc-desktop ~ $ 


The [Test] share is one from a tutorial I was trying. It didn't work either but I left the folder as something to keep testing on.

---

### Post by Morbius1 on 2010-07-15
You've got some circular logic going on in that smb.conf. While we stall for time until I can think though it could you do one more thing please? In WinXP open up **Command Prompt** and type the following command:

```
net view
```And post back any errors

[COLOR=Blue]EDIT: You've got a line:[/COLOR]
> valid users = droid-pc
Is droid-pc your local login user name or is it something you created just for networking?

---

### Post by Rubicon421 on 2010-07-15
Well, I don't know what finally did it but it's working! I ran the net view command in XP and it showed the LM9 Samba server so I decided to check it again and it's working fine. 

I have a few more things to check but it seems good. Thanks for all the help!

---

### Post by Rubicon421 on 2010-07-15
It's working great! Added another share and checked it from a third PC on the network and everything is working smoothly. 

Now to figure out if I can stream to my XBOX 360 and PS3, but that's another thread LOL!

---

### Post by joffe on 2011-03-15
> **Rubicon421 said:**
> Well, I don't know what finally did it but it's working! I ran the net view command in XP and it showed the LM9 Samba server so I decided to check it again and it's working fine. 

I have a few more things to check but it seems good. Thanks for all the help!

I would really like to know how you solved the file sharing problem. I also had my hostname set to something longer by the ubiquity installer and not until I changed it to a shorter one was I able to browse the share from OSX.

It looks to me your hostname "droid-pc-desktop" was given by the installer, am I right? Mine was johan-aspire-3820, a hostname consisting of 17 characters and thus rendering sharing completely useless... If you changed the hostname and think that was the problem, please have a look at this bug i just filed:

[[COLOR="Navy"]Bug #735072 in Ubuntu: “The hostname proposed by installer is too long file sharing to work correctly.”[/COLOR]]("https://bugs.launchpad.net/ubuntu/+bug/735072")

---

### Post by Rubicon421 on 2011-03-16
> **joffe said:**
> I would really like to know how you solved the file sharing problem. I also had my hostname set to something longer by the ubiquity installer and not until I changed it to a shorter one was I able to browse the share from OSX.

It looks to me your hostname "droid-pc-desktop" was given by the installer, am I right? Mine was johan-aspire-3820, a hostname consisting of 17 characters and thus rendering sharing completely useless... If you changed the hostname and think that was the problem, please have a look at this bug i just filed:

[[COLOR=Navy]Bug #735072 in Ubuntu: “The hostname proposed by installer is too long file sharing to work correctly.”[/COLOR]]("https://bugs.launchpad.net/ubuntu/+bug/735072")


I wish I could tell you but it's been a while and I have done a few reinstalls since then. Sorry I can't be of more help. Good luck!

---

