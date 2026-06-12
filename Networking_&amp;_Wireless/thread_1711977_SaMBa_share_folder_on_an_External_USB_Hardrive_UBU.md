---
title: "SaMBa share folder on an External USB Hardrive UBUNTU 10.10"
date: 2011-03-22
forum: Networking &amp; Wireless
---

### Post by boobcat on 2011-03-22
Hello all!

I am doing my head in with this. Googling and the forums are not helping 100%.

I have a 1.0T External USB hard drive plugged into a PC running Ubuntu 10.10.

I wish to share a music folder on this drive to Windows users on my home network.

This is what I have done.

Installed SaMBa.

I am logged on as administrator.

-> Samba GUI via System/Administration/Samba

-> Preferences -> Basic - Changed Workgroup to 'mshome' (Same as other PC's)

-> Create Samba Share - Browsed to Music folder on External USB - 'Ticked' writable and visible.

-> Access tab - 'Allow access to everyone' checked.



Then:- 

-> Browsed to the music folder and right clicked - then selected properties.

-> Share - Ticked 'Share, Allow other users to create and delete file in this folder and also Guest Access'

-> Create share.

'Nautilus needs to add some permissions to your folder "Music" in order to share it' - clicked 'Add the Permissions automatically'

DONE.


NOW.....

Over to a Windows 7 computer on the network. 

->Computer -> Network -> 'DANS-DESKTOP'

I can see 'Music' folder shared and also 'Stylus Photo R230' shared.

Open 'Music' and I am getting - ' Windows cannot access \\DANS-DESKTOP\Music
 Error code 0x80070035. The network path was not found.'

Back onto 'DANS-DESKTOP' I can access files from the WINDOWS 7 computer.

Like I said - this is doing my head in. I have just come over from being a windows user for over 10 years. PC's were linked to share music, files and have the odd LAN game.

My missus is on my case because she can't access the music.  

HELP!!!

(Should have put this in networking.... SORRY)

---

### Post by boobcat on 2011-03-22
My drives name is 'External Store'


"\\DANS-DESKTOP\Music" just doesn't seem a right path....

I don't know but wouldn't:-

 dans-desktop/media/External Store/Music 

or something along the lines be closer???

Stumped  :neutral:

---

### Post by crispy_420 on 2011-03-22
Check out this post:

[http://ubuntuforums.org/showthread.php?p=10565296](http://ubuntuforums.org/showthread.php?p=10565296)

He was having issues with external drive and it worked out for him.

---

### Post by boobcat on 2011-03-22
Adding force user = dan

Did not work.

---

### Post by boobcat on 2011-03-22
MSHOME
    \\KAYDEE-PC              Kristy-Dees Lappy
    \\DANS-DESKTOP           Dans-desktop server (Samba, Ubuntu)
        \\DANS-DESKTOP\Stylus-Photo-R230    EPSON Stylus Photo R230
        \\DANS-DESKTOP\print$             Printer Drivers
        \\DANS-DESKTOP\Music              
        \\DANS-DESKTOP\IPC$               IPC Service (Dans-desktop server (Samba, Ubuntu))
dan@Dans-desktop:~$ net usershare info --long
[music]
path=/media/External Store/Music
comment=
usershare_acl=Everyone:F,
guest_ok=y

dan@Dans-desktop:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Music]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    workgroup = MSHOME
    server string = %h server (Samba, Ubuntu)
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
    valid users = dan, jaxen, nobody, sharnijay
    read only = No

[Music]
    path = /media/External Store/Music
    read only = No
    guest ok = Yes

---

### Post by Morbius1 on 2011-03-22
Couple of things:
> -> Samba GUI via System/Administration/SambaThat will generate a Samba Classic share in smb.conf
> -> Browsed to the music folder and right clicked - then selected properties.

-> Share - Ticked 'Share, Allow other users to create and delete file in this folder and also Guest Access'That will generate a Samba Usershare ( a.k.a. nautilus-share ) in /var/lib/samba/usershares.

It's best to use one method at a time and never use both methods on the same target. There are at least 3 HowTo's out on the web that actually tell you to use both but I think the authors took far too many drugs in the 70's. Since your share is guest accessible I would get rid of the Classic share - but that's up to you.
> Adding force user = dan

Did not work.     From the output of **testparm** you did not add it, you didn't save smb.conf, or it's added in the wrong place. I would put in in the global section of smb.conf, save the file, and restart samba:
```
sudo service smbd restart
```

---

### Post by boobcat on 2011-03-23
Morbius - Thank you - It works.

 "From the output of **testparm** you did not add it, you didn't save  smb.conf, or it's added in the wrong place. I would put in in the global  section of smb.conf, save the file, and restart samba:"


I did originally add and save it but it was not put in the global section. I added it to the very end and it did not work so I took it back out.


Once again -  Thank you .  :biggrin:

---

