---
title: "Mount Windows user share folder at login"
date: 2010-09-29
forum: Networking &amp; Wireless
---

### Post by guimenez on 2010-09-29
i need to always mount the user share of my Windows server at Ubuntu login. 

Can anyone help me on this please? 

This is my server struture: 

Server 
|-Group1 
| |-user1 
| 
|-Group2 
|-user2 


i’ve found that i need to configure pam mount and i have this example: 

<volume user="user" fstype="smbfs" server="krueger" path="public" 
mountpoint="/home/user/krueger" > 

but i don’t know what to change relative to my server folder struture. 

thanks

many thanks

---

### Post by guimenez on 2010-09-30
please, any help here?

every time i login it doesn't happen nothing, nothing is mount and ubuntu doesn't give me any error



this is my pam.d configurations

----------------  /etc/pam.d/common-auth  ---------------
auth	[success=2 default=ignore]	pam_unix.so nullok_secure
auth	[success=1 default=ignore]	pam_lsass.so try_first_pass
auth	requisite			pam_deny.so
auth	required			pam_permit.so
auth	optional			pam_mount.so 
session	optional			pam_mount.so 


----------------  /etc/pam.d/common-session  -------------
session	[default=1]			pam_permit.so
session	requisite			pam_deny.so
session	required			pam_permit.so
session	required	pam_unix.so 
session	sufficient	pam_lsass.so 
session	optional	pam_mount.so 
session	optional	pam_ck_connector.so nox11


--------------- /etc/pam.d/login  ------------------------
auth       optional   pam_faildelay.so  delay=3000000
auth       required  pam_securetty.so
auth       requisite  pam_nologin.so
session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so close
session       required   pam_env.so readenv=1
session       required   pam_env.so readenv=1 envfile=/etc/default/locale
@include common-auth
auth       optional   pam_group.so
session    required   pam_limits.so
session    optional   pam_lastlog.so
session    optional   pam_motd.so
session    optional   pam_mail.so standard
@include common-account
@include common-session
@include common-password
session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so open
session   optional    pam_mount.so 
auth      optional    pam_mount.so try_first_pass


-----------------  /etc/security/pam_mount.conf.xml  ------------------
<volume
user="*"
server="servername.domain.local"
path="UserShares"
mountpoint="home"
fstype="cifs"
/>

<cifsmount>mount -t cifs //%(SERVER)/%(VOLUME)/%(USER) %(MNTPT)/%(USER) -o "user=%(USER),uid=%(USERUID),gid=%(USERGID)%(before=\",\" OPTIONS)"</cifsmount>

thanks

---

### Post by P4man on 2010-09-30
IM pretty sure your server isnt called "servername.domain.local" and the mountpoint where you try to mount it is not a valid path either. It should be something like '/home/*yourusername*/windows_share'.

Anyway, there is probably a much easier solution. In the main menu go to Places, then "Connect to server,..", select "Windows share" as service type. Fill out the appropriate fields (server is required, and you probably need to fill out the share name too). Then  check the "add bookmark" box and give it a sensible name..

---

### Post by guimenez on 2010-09-30
thanks for replying

my home path is /home/likewise-open/DOMAIN/user

and the user is always changing and i need to mount it automatically without specifying the username

my server name's: SERVER
my domain: DOMAIN.LOCAL

Inside the SERVER i have 2 folders group (GROUP1 and GROUP2) and inside them i have USER1 and USER2

please, can you help on what i need to change in this code:

<volume
user="*"
server="servername.domain.local"
path="UserShares"
mountpoint="home"
fstype="cifs"
/>

<cifsmount>mount -t cifs //%(SERVER)/%(VOLUME)/%(USER) %(MNTPT)/%(USER) -o "user=%(USER),uid=%(USERUID),gid=%(USERGID)%(befor e=\",\" OPTIONS)"</cifsmount>


many thanks once again

---

### Post by P4man on 2010-09-30
edit: Im misreading. Let me go over it again. Hang on.

---

### Post by guimenez on 2010-09-30
> **P4man said:**
> edit: Im misreading. Let me go over it again. Hang on.
thanks for your help.

i need this a lot, and after making this working, i will make a tutorial for everyone needing this

---

### Post by P4man on 2010-09-30
Im throwing the towel Im afraid. Cant get my head around cfis and too many conflicting resources. I hope someone else chimes in. 

Let me just toss you this thread:
[http://ubuntuforums.org/showthread.php?t=1040514](http://ubuntuforums.org/showthread.php?t=1040514)

I know its a different approach, using fstab, but the info about mounting it verbose to see what happens and perhaps the fact mount.cifs requires 'username' rather than 'user' might apply. I honestly dont know.

My GUI approach should still work though. If this is for 2 rather than 200 users.

---

### Post by guimenez on 2010-09-30
the main problem of fstab its that i need to make credentials to all users and i have more then 100 users :(

i'm lost now

thanks

---

### Post by guimenez on 2010-10-04
i'm using now this commands in pam_mount.conf.xml

<volume fstype="cifs" server="SERVER" path="Group1/%(DOMAIN_USER)"

but always fail to mount

please, can someone help me?

thanks

---

### Post by guimenez on 2010-10-04
I've finally found the solution!!!

the main problem was the server name, i need to put the IP and now it works flawless

---

### Post by pwebster25 on 2010-11-14
guimenez-
Did you get this to work so that various users could get their windows shares mounted?  It looked like you were successful, based on your last post.  If so, what version are you using?

What worked for you?

Your original posted included code for 3 or 4 different pam config files.  Did you need all of these or just the last one?  

I am also using likewise-open (6.0) on 10.10 and want to do something similar for a group of students using various machines and each with their own windows share, which is named based on their username.

Looks like your domain setup is similar to my own.

Thanks
Paul

---

### Post by guimenez on 2010-11-15
> **pwebster25 said:**
> guimenez-
Did you get this to work so that various users could get their windows shares mounted?  It looked like you were successful, based on your last post.  If so, what version are you using?

What worked for you?

Your original posted included code for 3 or 4 different pam config files.  Did you need all of these or just the last one?  

I am also using likewise-open (6.0) on 10.10 and want to do something similar for a group of students using various machines and each with their own windows share, which is named based on their username.

Looks like your domain setup is similar to my own.

Thanks
Paul

Its very simple :D

1- install libpam-mount
2 - install smbfs
3 - add this line in your etc/security/pam_mount.conf.xml

<volume user="*" fstype="smbfs" server="your server ip" path="Group1/%(DOMAIN_USER)" mountpoint="~/%(DOMAIN_USER)" options="iocharset=utf8,file_mode=0700,dir_mode=0700" />


you only need to change in the above lines the server ip and name of the shared group

it only that :D

---

### Post by pwebster25 on 2010-11-15
Thanks-
I'll give it a try and report back.
Paul

---

### Post by pwebster25 on 2010-11-15
Any idea what happens when the network share is unavailable?  For example, if the server is down or if the user is logging in from home instead of inside the domain?

---

### Post by guimenez on 2010-11-16
it will startup normally but without the mounted share. You will not have the shared folder icon in your desktop and will not receive any kind of error :D

cumps

guimenez

---

### Post by jauntymeerkat on 2010-12-01
> **pwebster25 said:**
> Any idea what happens when the network share is unavailable?  For example, if the server is down or if the user is logging in from home instead of inside the domain?

Did you get this to work, because I am running the exact same set up as u. 10.10 and likewise open 6.0.
I have been looking for this solution for weeks.;)

---

### Post by jauntymeerkat on 2010-12-01
> **pwebster25 said:**
> Any idea what happens when the network share is unavailable?  For example, if the server is down or if the user is logging in from home instead of inside the domain?

> **guimenez said:**
> Its very simple :D

1- install libpam-mount
2 - install smbfs
3 - add this line in your etc/security/pam_mount.conf.xml

<volume user="*" fstype="smbfs" server="your server ip" path="Group1/%(DOMAIN_USER)" mountpoint="~/%(DOMAIN_USER)" options="iocharset=utf8,file_mode=0700,dir_mode=0700" />


you only need to change in the above lines the server ip and name of the shared group

it only that :D

I am assuming I need to make sure my pam.d config files have to be set up as yours are on the previous page?
Thanks for any help!

---

### Post by pwebster25 on 2010-12-03
> **guimenez said:**
> Its very simple :D

1- install libpam-mount
2 - install smbfs
3 - add this line in your etc/security/pam_mount.conf.xml

<volume user="*" fstype="smbfs" server="your server ip" path="Group1/%(DOMAIN_USER)" mountpoint="~/%(DOMAIN_USER)" options="iocharset=utf8,file_mode=0700,dir_mode=0700" />


you only need to change in the above lines the server ip and name of the shared group

it only that :D

[LIST=1]
[*]I installed Likewise Open 6 (from their website, not from the repositories, as there is a comment about an glitch in the version in the repositories.
[*]I did 1, 2, and 3 above.
[*]I added a folder called WindowsFolder to /etc/skel, so that it would be placed in each new users home folder.
[*]I added the following to my /etc/security/pam_mount.conf.xml
[*]-I added it just above the closing line: </pam_mount>
[/LIST]

```
<volume user="*" fstype="smbfs" server="IPAddress" path="staff-files/%(DOMAIN_USER)" mountpoint="/home/local/DOMAINNAME/%DOMAIN_USER/WindowsFolder" options="iocharset=utf8,file_mode=0700,dir_mode=07 00" />
```

I ended up getting the WindowsFolder showing up for each user from /etc/skel but nothing mounted in it and no disk drive.

I changed my code  in each of the other pam_mount files, per post #2 in this thread and then I changed my code in the /etc/security/pam_mount.conf.xml file to the following:
```
<volume user="*" fstype="cifs" server="IPAddress" path="staff-files/%(USER)" mountpoint="/home/local/DOMAINNAME/%(USER)/WindowsFolder" options="iocharset=utf8,file_mode=0700,dir_mode=07 00" />
```

It did then mount a drive in the folder and on my desktop.  However, it won't let me open it.  It tells me I don't have permission.  It also won't let me unmount the drive, saying I don't have access to fstab.  I wonder if I need to do something related to group permissions or if I need to change something in the sudoers file.

I think I am so close.  Any ideas?

---

### Post by enboig on 2011-12-27
I have exactly the same problem [#18]. Did you solve this?

---

### Post by pwebster25 on 2011-12-27
Sorry. I gave up and moved to something else. I think out must be possible, as I can do it manually in nautilus.

---

### Post by enboig on 2012-05-15
I found my problem, my shared folder permissions were "rw-rwx---"; I changed them to 770 and everything worked.

---

