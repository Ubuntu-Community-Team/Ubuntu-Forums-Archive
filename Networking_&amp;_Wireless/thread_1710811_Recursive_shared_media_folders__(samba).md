---
title: "Recursive shared media folders  (samba)"
date: 2011-03-20
forum: Networking &amp; Wireless
---

### Post by XBMC old School on 2011-03-20
I currently have samba set up to share to XBMC. One of my shares contains many folders. But the permissions aren't given to access those folder only the container folder.

I can browse the folders recursively with a windows Laptop

How do i enable recursive permissions?

---

### Post by oracle2b on 2011-03-20
Recursive Permission Changes

To change the permissions of multiple files and directories with one command. Please note the warning in the chmod with sudo section and the Warning with Recursive chmod section. 

Recursive chmod with -R and sudo

To change all the permissions of each file and folder under a specified directory at once, use sudo chmod with -R 
> user@host:/home/user$ sudo chmod 777 -R /path/to/someDirectory

source is [https://help.ubuntu.com/community/FilePermissions#Recursive Permission Changes]("https://help.ubuntu.com/community/FilePermissions#Recursive Permission Changes")

---

### Post by Morbius1 on 2011-03-20
The only problem with a "chmod 777 -R" is that it doesn't discriminate between a file and a directory. A "7" will enable read, write, and execute.

An "execute" on a directory means to open it up to see what's inside. That what you want it to do. An execute on a file means .. well ... to execute. That's not what you want - at least not for every file.

On way around this is to use another method:
```
sudo chmod -R a+rwX /path/to/someDirectory                      
```The big "X" will cause all folders to have the execute bit "on" and all files that are not already marked executable to have the execute bit turned "off":
Folders: 777
Files: 666

But you said this was a samba share. Can you access all folders locally? There may be a samba way around this.

---

### Post by XBMC old School on 2011-03-21
> **Morbius1 said:**
> 

But you said this was a samba share. Can you access all folders locally? There may be a samba way around this.

Um, ya i can access the folders via a windows laptop (wireless) no problem. But I have an XBMC (ATV) media centre (via bridge) that is having issues accessing the sub-folders.

Side question, i want write ability for the windows laptop but i am blocked in ubuntu because i don't have ownership control. Is there a work-a-round to make all written files to be ownerless or full permissions?

Thanks for your time and experience.

Thanks Morbius

---

### Post by Morbius1 on 2011-03-21
I'm getting confused by your description of the environment.

I'm not even sure if the samba shares are on an Ubuntu box. If they are please post the output of the following commands so I can see how they are set up:
```
net usershare info --long
``````
testparm -s
```All of this could be simple enough to fix depending on how you are set up. For example, If you have a guest share set up on an ubuntu box and the local login user on that ubuntu box ( let's call him bob ) has read / write access to the folder ( and it's contents ) that's being shared then you can make it so all remote users have the same access by adding a line to smb.conf:
```
force user = bob
```Whatever bob has access to so does the remote user. When a remote user adds something to the share the ownership will be converted to bob.

Where to put that line in this example depends on what method of samba sharing you are using - there are two and the output of the two commands above will tell me that.

---

### Post by XBMC old School on 2011-03-21
XXXXXXX@XXXXXXX:~$ net usershare info --long
[xbmc movies (themoviedb)]
path=/home/parent/Videos/xbmc/XBMC Movies (ThemovieDB)
comment=
usershare_acl=Everyone:F,
guest_ok=y

info_fn: file /var/lib/samba/usershares/video is not a well formed usershare file.
info_fn: Error was Path is not a directory.
[share]
path=/media/Family Shares/House Shares
comment=
usershare_acl=Everyone:F,
guest_ok=n

[xbmc]
path=/home/parent/Videos/xbmc
comment=
usershare_acl=Everyone:F,
guest_ok=y

[xbmc television]
path=/home/parent/Videos/xbmc/XBMC Television
comment=
usershare_acl=Everyone:F,
guest_ok=y

[xbmc movies (imdb)]
path=/home/parent/Videos/xbmc/XBMC Movies (IMDB)
comment=
usershare_acl=Everyone:F,
guest_ok=y

XXXXXXX@XXXXXXX:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Share]"
Processing section "[xbmc]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    server string = %h server (Samba, Ubuntu)
    security = SHARE
    encrypt passwords = No
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
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

[Share]
    path = /media/Family Shares/House Shares
    read only = No
    guest ok = Yes

[xbmc]
    path = /home/parent/Videos/xbmc
    read only = No
    guest ok = Yes

Here is the requested information. I have a desktop PC as per my signature, an XBMC media centre (Linux installed ATV) and a win7 laptop.

I apologize for the confusion. I would like to have all my "shares" on an extra HDD in my desktop. I have a /root SDD, a /home 2TB HDD, a extra 2TB ext4 spare HDD "shares". 

Ideally I would like to have an admin account managing and serving the shares whether my user accounts are logged in or not.

I have a fresh install and able to abandon it or modify it if it is easier.

Again thank you for you time and experience.

XBMC OS

---

### Post by Morbius1 on 2011-03-22
You've actually got a bit of a mess there - it's not your fault as this isn't explained very well anywhere. The are two methods of creating a samba share. 
Usershare ( a.k.a. Nautilus-share ):
> [share]
path=**[COLOR=Blue]/media/Family Shares/House Shares[/COLOR]**
comment=
usershare_acl=Everyone:F,
**[COLOR=Blue]guest_ok=n[/COLOR]**And Classic-Share:
> [Share]
    path = **[COLOR=Blue]/media/Family Shares/House Shares[/COLOR]**
    read only = No
    **[COLOR=Blue]guest ok = Yes[/COLOR]**As you can see you are using both methods at the same time and in this one example on the same target folder with different parameters. It's anybody's guess if Samba thinks this is a guest accessible share or not. I would get rid of one or the other.

From your post:
> **[COLOR=Teal]XXXXXXX[/COLOR]**@XXXXXXX:~$ net usershare info --longI am assuming that user = **[COLOR=Teal]XXXXXXX [/COLOR]**[COLOR=Teal][COLOR=Black]has access to all these folders[/COLOR][/COLOR][COLOR=Black] locally on the Ubuntu box. If so then add the following line to the [global] section of smb.conf:
[/COLOR]```
[COLOR=Black]force user = XXXXXXX[/COLOR]
```[COLOR=Black] [COLOR=Blue][I]Changing XXXXXXX to the actual login user name represented by XXXXXXX.

[/I][COLOR=Black]Then restart samba:
[/COLOR][/COLOR][/COLOR]```
[COLOR=Black]sudo service smbd restart[/COLOR]
```[COLOR=Black][COLOR=Blue][COLOR=Black]
[/COLOR][/COLOR][/COLOR][B][COLOR=Teal]
[/COLOR][/B]

---

### Post by XBMC old School on 2011-03-22
Thank you for the clarification! Your right, I have looked through the forum/google and haven't found explicit instructions and/or information about how samba functions/management/ecetera. For dummies is needed.

sudo chmod -R a+rwX /path/to/someDirectory
Has fixed my recursive permissions. 

XXXXXXXX is my admin account. I intend to have a dumbed down account for my son and would like to have the shares functioning for my media centre & laptop. Which Samba method is best for that?
How do i delete the other one?

Is there any explicit instructions on how to manage user & network permissions with samba? Preferably i would like to have -R for XXX, Laptop & XBMC. And read only for son and wifi users.

XMBC OS

Can't say thanks enough.

---

### Post by Morbius1 on 2011-03-22
Confused again.

This is what I'm reading:

You want Read / Write access for yourself when you log into the Ubuntu machine.
You want read / write access for remote clients on Laptop and XBMC.
You want read only access for son - not sure if son is remote or another local login user on the Ubuntu box.
You want read only access for wifi users - don't know where these folks are coming from.

If all of these folks are remote users then Usershare is not the way to go. It can set up a guest share or it can require authentication but it's one way or the other. You can't say ( easily ) that I want user1 to have read access and user2 to have write access using usershares.

I also don't know how XBMC connects to your share. If it's asked for a username and password can it respond? 

To remove either of the type of shares just redo the steps you used to create them. Userhsares - Nautilus, whatever you used to create the Classic shares - go back into it and delete the share.

---

### Post by XBMC old School on 2011-03-22
You want Read / Write access for yourself when you log into the Ubuntu machine.
You want read / write access for remote clients on Laptop and XBMC (XBMC can provide user&password).
You want read only access for son - local login user on the Ubuntu box.
You want read only access for wifi users - don't know where these folks are coming from.

I apologize if i'm frustrating you a bit. I just am not clear on what i can & can't do. Can these types of controls be managed by groups?

---

### Post by XBMC old School on 2011-03-23
Hey Morb,

Do you know of a good,clear and complete tutorial or guide on using users and groups to manage accesses? 

XMBC OS

---

