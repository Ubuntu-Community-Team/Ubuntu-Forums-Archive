---
title: "Cannot access samba shares located on external harddrive"
date: 2010-03-14
forum: Networking &amp; Wireless
---

### Post by alex_linux on 2010-03-14
HI 

I am attempting to create shares so that other windows/linux machines on local lan can have full access to them.


Here are the partitions that I am working with ([COLOR=Red]/dev/sdb1 is giving me trouble[/COLOR]):
/dev/sda6     ext4     5763616    216260   5254576   4% /home
/dev/sda7     ext4     2205780     68824   2024908   4% /space
/dev/sdb5     ext4    54293308    184136  51351216   1% /media/35c1819f-6a04-4994-a7cb-1a35ccbc8e40
[COLOR=Red]/dev/sdb1  fuseblk   921600820 408133696 513467124  45% /media/7273720939FEC4A8[/COLOR]


Here is a list of shares:

alex@adience:~$[COLOR=Red] smbclient -L adience[/COLOR]
Enter alex's password: 
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.4.0]

    Sharename       Type      Comment
    ---------       ----      -------
    print$          Disk      Printer Drivers
    IPC$            IPC       IPC Service (adience server (Samba, Ubuntu))
[COLOR=Red]    server_share    Disk      meant as temp location
    movies          Disk   [/COLOR]   
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.4.0]

    Server               Comment
    ---------            -------
    ADIENCE              adience server (Samba, Ubuntu)
    LAPTOP               

    Workgroup            Master
    ---------            -------
    WORKGROUP            ADIENCE



Currently in wondows I [COLOR=Red]can see but not open anything from /dev/sdb1[/COLOR]:

alex@adience:/media/7273720939FEC4A8$ ls -lrth
total 196K
drwx------ 1 alex alex 4.0K 2009-05-10 23:14 System Volume Information
drwx------ 1 alex alex 164K 2010-03-12 19:16 [COLOR=Red]movies[/COLOR]


However I have no problems accessing a share on /home:
drwxrwxrwx 2 alex sambashare 4096 2010-03-14 13:44 [COLOR=Red]server_share[/COLOR]



I have tried to change the group but the command is ignored:

[COLOR=Red]drwx------[/COLOR] 1 alex alex 164K 2010-03-12 19:16 server_movies
alex@adience:/media/7273720939FEC4A8$ [COLOR=Red]chown -v alex:sambashare server_movies[/COLOR]
changed ownership of `server_movies' to alex:sambashare
alex@adience:/media/7273720939FEC4A8$ ls -lrt
total 196
[COLOR=Red]drwx------[/COLOR] 1 alex alex 167936 2010-03-12 19:16 server_movies


Hope this makes sense. 
Please help me set this up properly.

Thanks in advance,
Alex

---

### Post by l4zy on 2010-03-15
Do you mount those share by using the account which you made int CIFS / SMB or your linux account ? 

Does the user which you're using belong to that group which should have access to those share.

---

### Post by Morbius1 on 2010-03-15
To answer this question correctly we really need more information.

What is the format of the external hard drive?
How are you mounting it?
What method are you using to share it: Nautilus-share or Classic-share?

Based solely on the output of your "ls" command I'm going to assume the following:

It's an NTFS formatted drive
It automounts when you plug it in
I'm also going to assume you're using Nautilus-share ( right click > Sharing Options )

When you plug in that usb device it mounts with you as owner and with read / write permissions to the owner only. When you share the device you tell samba to allow others to access it but nothing can over rule linux file permissions. By far the easiest way out of this is the following:

Open **Terminal**
Type **sudo gedit /etc/samba/smb.conf**

Add the following line to the[COLOR=Blue] [global][/COLOR] section of smb.conf:
```
force user = alex
```When a remote user accesses the share,  "force user" will create a mask making him appear to be you for that share and right now only you have access.

If I'm wrong about my assumptions let me know. If your using classic-shares you would need to put that force user option in another part of the file. If you encouner any problems please post he output of the following commnads:

**net usershare info**
**testparm -s**

---

### Post by alex_linux on 2010-03-15
14zy: yes the user belongs to the "sambashare" group
to setup I used pretty much everything out of the box.

Morbius1: you are right about almost everything, except I think that my ntfs external drive actually got mounted as root

What I did is I installed "psydm" modified owner/group to alex/sambashare and it permanently added my drive to /etc/fstab :
/dev/sdb1                                  /media/sdb1     ntfs         nls=iso8859-1,ro,umask=000,gid=sambashare,uid=alex  0  0


after a reboot everything started working, not sure if this is the right way to setup my server, but it will have to do for a home lan.

FYI for anyone that is using samba first time:
If you are trying to add a samba user make sure that the user exists first, before running: sudo smbpasswd -a USR_NAME
for me on ubuntu my current user got added to samba automatically...

Thanks for the help guys!

---

### Post by Morbius1 on 2010-03-16
I'm glad you got it working and I'm not suggesting for a moment that you change a thing, however.....

> [QUOTE] /dev/sdb1 /media/sdb1 ntfs nls=iso8859-1,[COLOR=Blue]ro[/COLOR],[COLOR=DarkGreen]umask=000[/COLOR],gid=sambashare,uid=alex 0 0[/QUOTE]It's for reasons like the above fstab line that I do not recommend anyone use psydm.

[COLOR=Blue]ro - mounts the partition as read only
[/COLOR][COLOR=DarkGreen]umask=000 enables everyone the ability to read and write to that partition.

[COLOR=Black]It appears to work for you so I can only conclude that [COLOR=DarkGreen]umask[/COLOR] takes precedence over [COLOR=Blue]ro[/COLOR].[/COLOR]
[/COLOR]

---

### Post by alex_linux on 2010-03-18
Thanks again for the help, I guess my goal was to be able to see the files.
I  will probably have to remove 'ro' because i cannot write to the shares. work in progress.

---

