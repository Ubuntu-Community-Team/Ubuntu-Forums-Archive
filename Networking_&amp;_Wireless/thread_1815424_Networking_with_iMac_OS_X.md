---
title: "Networking with iMac OS X"
date: 2011-07-31
forum: Networking &amp; Wireless
---

### Post by XMen67 on 2011-07-31
Hi Guys,

Need some advice. Just installed Ubuntu 11.04. Right click to File share a folder. Successfully installed the option (from USC). Set the Admin user acccount, password protected. Join the WORKGROUP. My Mac could see the "ubuntu" on the network. Click and could see the "Folder". However when click to display content message "System resource unavailable". I checked SAMBA was installed, etc.

Any ideas?

---

### Post by Morbius1 on 2011-07-31
Please post the output of the following commands so we can see how your shares are set up:
```
testparm -s
net usershare info --long
```

---

### Post by XMen67 on 2011-07-31
Hi here's my screen print.

testparm -s

Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    server string = %h server (Samba, Ubuntu)
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

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers
xadmin@ubuntu:~$ ^C


xadmin@ubuntu:~$ net usershare info --long
[vidz]
path=/media/SAM1TB-2/VIDZ
comment=
usershare_acl=Everyone:F,
guest_ok=n

[vidz2]
path=/media/SAM1TB-1/VIDZ2
comment=
usershare_acl=Everyone:F,
guest_ok=n

Thanks in advance

---

### Post by Morbius1 on 2011-07-31
Your shares require authentication to access so did you set up local accounts for the remote users and create samba passwords for them?

---

### Post by XMen67 on 2011-07-31
Hi Morbius. Yes I did create it. The odd thing is that I can mount my Mac and see the directories and access the files. But Ubu PC does not prompt me for the Mac id and pwd, so I can access only the public files but not the personal files. Vice versa from the Max I see Ubu, but it does not prompt for a id n pwd. I can't display the share dirs. Mac says "Operation cannot complete because dir can be found".

The other thing is that, when i do Places-->Network--> I see the Ubu PC volume and the Mac vol. too. When I try to mount the Ubu dirs, it says "Fail to Mount windows share". I tried to mount other local dirs, got them mounted but still the same, the Mac can't access those volumes.

Btw, where do you find the settings for the Samba? I use Personal File Sharing and the Users n Groups to do the settings.

Thanks.

---

### Post by Morbius1 on 2011-08-01
Let me answer the easy questions first:
> where do you find the settings for the Samba?/etc/samba/smb.conf

Smb.conf is the Samba configuration file but in addition to that you are using nautilus-share or usershares so the share definitions are in /var/lib/samba/usershares. Don't try to edit anything there however since the syntax has to be very exact.
> I use Personal File Sharing and the Users n Groups to do the settingsPersonal File Sharing = Apache + Avahi. It is not Samba. Whatever you do there will have no impact on Samba file sharing. And it's only capable of sharing the "Public" folder in your home directory.

Somewhere along the line you have to add the user to the samba database and the way you do that is like this:
```
sudo smbpasswd -a user-name
```As for the general "nobody seems to be asking the other for id and password" problem, I don't know at the moment. Yours is now the third post with this problem and to be honest I thought the first 2 posters were drunk because this just can't happen. Samba on 11.04 is a little flakey but not that flaky - I need to see if I can somehow duplicate your symptom.

As for the "dir not found" and "failed to mount" issue are you sure these partitions are mounted:
> /media/SAM1TB-1
/media/SAM1TB-2Are these temporary mounts that you mount through Nautilus because they are external usb drives or do you have these set up in fstab? They need to be mounted first before they can be seen across the network.

---

### Post by XMen67 on 2011-08-02
Thanks Morbius, for the detail replies. I'll use the clues to try to figure things out. I setup another Ubu machine in the office. Installed PFSharing, Samba and etc. Seems to work, as I can see the files in the dir from a Win7 PC. However, only external shared drives or usb folders, can't be accessed. Local drives are ok. Haven't tried on a Mac though. I think there is a twist somewhere to get the Mac to see it. Will try. Thanks for the your time. Will update you.

---

### Post by Morbius1 on 2011-08-02
> However, only external shared drives or usb folders, can't be accessed.And I'm guessing they are formatted in either NTFS or FAT32. The problem here is that they will mount locally with you as owner and permissions set to allow access only to you. The remote user is not you so there is no access. The fix in this case is to make the remote user appear to be you as far as your shares are concerned:

Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Add the following line to the [globa] section of smb.conf:
```
force user = xmen67
```[COLOR=Blue]*Change that to match your local login user name.*[/COLOR]

[COLOR=Black]Then restart samba:
[/COLOR]```
[COLOR=Black]sudo service smbd restart[/COLOR]
```[COLOR=Black]
[COLOR=Blue][I]Note: Every time you restart samba the network has a hissy fit so give it a few minutes ( yes minutes ) to settle down before testing access.

[/I][COLOR=Black]That might fix the MAC's inability to access the share as well since from the Mac's perspective it can see the share because you defined it but can't get access since the permissions are 700 so access to anyone other than you is not possible.[/COLOR][/COLOR][/COLOR]

---

