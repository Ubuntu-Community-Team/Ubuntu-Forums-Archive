---
title: "Problem with samba: can't mount the shared folders"
date: 2010-10-07
forum: Networking &amp; Wireless
---

### Post by reomachi on 2010-10-07
Guys,

I was trying to configure samba, but I'm having some difficult to share my folders.
My roommate can see the folders, but when he tries to mount it, the system says that it can't be done.
Here is the ```
:
#======================= Global Settings =======================
[global]
## Browsing/Identification ###
# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = CAVERNAS

# server string is the equivalent of the NT Description field
   server string = Samba Server

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
   wins support = yes

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
    dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
   name resolve order = lmhosts host wins bcast

#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m

# Cap the size of the individual log files (in KiB).
   max log size = 1000

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
   syslog = 0

# Do something sensible when Samba crashes: mail the admin a backtrace
   panic action = /usr/share/samba/panic-action %d

####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
    security = share

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
    encrypt passwords = no

############ Misc ############

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
    domain master = no
    local master = no
    preferred master = no
    hosts allow = ALL
    netbios name = reo

#======================= Share Definitions =======================
# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
   create mask = 0700

[Filmes]
        comment = Filmes
        path = /media/Data/Filmes
       available = yes
      browsable = yes
       writable = no
       public = yes
      printable = no

[Series]
        comment = Series
        path = /media/Data/Series
       available = yes
      browsable = yes
       writable = no
       public = yes
      printable = no
[Game Installs]
        comment = Installs
        path = /media/Data/Installs
       available = yes
      browsable = yes
       writable = no
       public = yes
      printable = no

[EFEI]
        comment = EFEI
        path = /media/Data/Backup/EFEI
       available = yes
      browsable = yes
       writable = no
       public = yes
      printable = no

[Musicas]
        comment = Musicas
        path = /media/Data/Backup/Musicas
       available = yes
      browsable = yes
       writable = no
       public = yes
      printable = no

[Programas]
        comment = Programas
        path = /media/Data/Backup/Programas
       available = yes
      browsable = yes
       writable = no
       public = yes
      printable = no

```If someone could help me please.
Thank you

---

### Post by Toz on 2010-10-07
What exactly is the error message? 
How is he trying to access the shares (what command/program/utility is he using? 
Did you create an account for him on your computer using smbpasswd?

[https://help.ubuntu.com/community/Samba?action=show&redirect=SettingUpSamba](https://help.ubuntu.com/community/Samba?action=show&redirect=SettingUpSamba)

/ToZ

---

### Post by xihad76 on 2010-10-08
if u get the error "Shared folders cant be mounted" or something like that, this is probably the folder permission issue. normally it happens when u share something from Fat32 or NTFS formatted disk drive as the user/group permission are set during the time of mounting. currently i m also facing the same issue. so looking forward if somebody can provide any solution. cheers

---

### Post by ibtkm on 2010-10-08
you can use samba by mc(midnight commander)
it has a samba that works very good :D

---

### Post by Morbius1 on 2010-10-08
I would make the following changes to your smb.conf:
Change this:
> encrypt passwords = [COLOR=Blue]no[/COLOR]To this:
> encrypt passwords = [COLOR=Blue]yes[/COLOR]From this:
> security = [COLOR=Blue]SHARE[/COLOR]To this:
> security = [COLOR=Blue]user[/COLOR]And add a line to your [global] section:
```
map to guest = Bad User
```Then restart samba:
```
sudo service smbd restart
```You've also got a few other strange entries in there:
> wins server = w.x.y.zIt's not pointing to anything. I suppose at worst it just slows everything down when you try to access a remote share. Unless you created a wins server on your network it won't do anything anyway.
> wins support = yesThis has turned your Linux box into a WINS server. In order to make that work you would have had to make a modification to the networking components of all the other machines on your network to point to the Linux machine to resolve names. I'm betting you didn't do that and as luck would have it that statement will just be ignored.

---

### Post by reomachi on 2010-10-08
> **Morbius1 said:**
> I would make the following changes to your smb.conf:
Change this:
To this:
From this:
To this:
And add a line to your [global] section:
```
map to guest = Bad User
```Then restart samba:
```
sudo service smbd restart
```You've also got a few other strange entries in there:
It's not pointing to anything. I suppose at worst it just slows everything down when you try to access a remote share. Unless you created a wins server on your network it won't do anything anyway.
This has turned your Linux box into a WINS server. In order to make that work you would have had to make a modification to the networking components of all the other machines on your network to point to the Linux machine to resolve names. I'm betting you didn't do that and as luck would have it that statement will just be ignored.


But by doing it, I'll need to create a guess account? Or anyone will be able to access my folders?

---

### Post by Morbius1 on 2010-10-08
> But by doing it, I'll need to create a guess account?Short answer is no.

You already have a guest account. What you don't see when you look at smb.conf are all those things that are in the default and one of them is:
> guest account = nobodyIf you do an:
```
id nobody
```You should get back this:
> uid=65534(nobody) gid=65534(nogroup) groups=65534(nogroup)So smb.conf is already set up to accommodate an anonymous remote user and you shouldn't have to make any modifications or create any users.

---

### Post by reomachi on 2010-10-13
Sorry 'bout the delay to reply this thread, I was traveling at does last days.

But anyway, I made the changes as Morbius1 suggested, here is the "new" code:
```

#======================= Global Settings =====================================
[global]

# workgroup = NT-Domain-Name or Workgroup-Name, eg: MIDEARTH
  workgroup = Cavernas

# server string is the equivalent of the NT Description field
  server string = Samba Server

# Security mode. Defines in which mode Samba will operate. Possible
# values are share, user, server, domain and ads. Most people will want
# user level security. See the Samba-HOWTO-Collection for details.
  security = user

# This option is important for security. It allows you to restrict
# connections to machines which are on your local network. The
# following example restricts access to two C class networks and
# the "loopback" interface. For more examples of the syntax see
# the smb.conf man page
  hosts allow = ALL

# Uncomment this if you want a guest account, you must add this to /etc/passwd
# otherwise the user "nobody" is used
  guest account = nobody

# this tells Samba to use a separate log file for each machine
# that connects
  log file = /usr/local/samba/var/log.%m

# Put a capping on the size of the log files (in Kb).
  max log size = 50

# Browser Control Options:
# set local master to no if you don't want Samba to become a master
# browser on your network. Otherwise the normal election rules apply
  local master = no

# Domain Master specifies Samba to be the Domain Master Browser. This
# allows Samba to collate browse lists between subnets. Don't use this
# if you already have a Windows NT domain controller doing this job
  domain master = no

# Preferred Master causes Samba to force a local browser election on startup
# and gives it a slightly higher chance of winning the election
  preferred master = no

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable it's WINS Server
; wins support = yes

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
; wins server = w.x.y.z

# WINS Proxy - Tells Samba to answer name resolution queries on
# behalf of a non WINS capable client, for this to work there must be
# at least one WINS Server on the network. The default is NO.
; wins proxy = yes

# DNS Proxy - tells Samba whether or not to try to resolve NetBIOS names
# via DNS nslookups. The default is NO.
  dns proxy = no

  encrypt passwords = yes
  name resolve order = lmhosts wins bcast host
  create mask = 0777
  map to guest = Bad User

#============================ Share Definitions ==============================
[myshare]
 comment = Data
 path = /media/Data/
   available = yes
   browsable = yes
   writable = no
   public = yes
   printable = no

```The error that my roomie is having to mount is this message:
> It was not possible to mount the location. Fail to mount the windows share.I don't know the message in English, cuz my roomie OS (Arch) is at Portuguese (Brasil), so I translated it.

---

### Post by johnnytm on 2010-10-13
Is ufw enabled? if so it blocks samba shares. ```
 sudo ufw status 
```
try disabling it if it says enabled ```
 sudo ufw disable 
```
if it mounts then u may need to add some rules to ufw in order to open the ports for samba

---

### Post by luvshines on 2010-10-13
> **reomachi said:**
> 

  encrypt passwords = yes
  name resolve order = lmhosts wins bcast host
  create mask = 0777
  map to guest = Bad User

#============================ Share Definitions ==============================
[myshare]
 comment = Data
 path = /media/Data/
   available = yes
   [COLOR="Blue"]browsable[/COLOR] = yes
   writable = no
   public = yes
   printable = no


Can this typo be an issue, the spellings of 'browseable' ??

Correct the spellings, restart the service ( sudo service smbd restart) and give it a shot

Also make sure that each directory starting from / upto Data is having atleast 755 permissions

[COLOR="Red"]Edit: Though when I try it on my system with wrong spellings, it still works[/COLOR]

---

### Post by reomachi on 2010-10-13
The response for

sudo ufw status

was Status: inactive

And I don't think its a misspelling problem, I checked it now, and I think is everything alright.

About the
> Also make sure that each directory starting from / upto Data is having atleast 755 permissions
How can I make sure of it?

---

### Post by luvshines on 2010-10-13
Yeah, for the spellings thing, I checked the man page, it allows both :)

For the permissions, you will have to check the directory permissions at each step:
```
ls -ld /
ls -ld /media
ls -ld /media/Data
```

Each one should have drwxr-xr-x as the permission for browsing.

---

### Post by reomachi on 2010-10-13
> **luvshines said:**
> Yeah, for the spellings thing, I checked the man page, it allows both :)

For the permissions, you will have to check the directory permissions at each step:
```
ls -ld /
ls -ld /media
ls -ld /media/Data
```Each one should have drwxr-xr-x as the permission for browsing.

I did it, and the answers I got was:
```
drwxr-xr-x 22 root root 4096 2010-10-06 13:42 /
drwxr-xr-x 3 root root 4096 2010-10-12 09:56 /media
drwx------ 1 reo reo 4096 2010-10-11 22:01 /media/Data
```

---

### Post by Morbius1 on 2010-10-13
> drwx------ 1 reo reo 4096 2010-10-11 22:01 /media/DataWhere we go from here depends on your answer to the following questions:

Is /media/Data pointing to an internal or an external drive?

How is /media/Data formatted? NTFS, FAT32, Ext3, ext4, ... ?

If it's a ext3 partition then a simple chmod should fix it. If it's an external NTFS USB drive then I would recommend a "force user = reo" placed in the share definition. Actually a "force user" would work in any case but .....

---

### Post by reomachi on 2010-10-13
It's an internal driver, NFTS.

---

### Post by Morbius1 on 2010-10-13
The easiest way our of this since it's just a guest share is to add a line to your share definition:

From this:
> [myshare]
 comment = Data
 path = /media/Data/
   available = yes
   browsable = yes
   writable = no
   public = yes
   printable = noTo this:
> [myshare]
 comment = Data
 path = /media/Data/
   available = yes
   browsable = yes
   writable = no
[COLOR=Blue]   force user = reo[/COLOR]
   public = yes
   printable = noThen restart samba:
```
sudo service smbd restart
```force user will act as a mask and convert your remote user to you as far as that share is concerned. Note that although it will appear to be you the remote user is still under the constraints of the other parameters in the share definition. So , for example, "writable = no" will still prevent the remote user from writing to the share.

---

### Post by luvshines on 2010-10-13
@ Morbius1

I totally forgot about external HDD and NTFS thing, glad you asked :D

Have one question, when it's 'force user' then the owner of files created by remote users will also be 'force user' ?? Does only filesystem type make difference or external/internal will also affect this?

---

### Post by reomachi on 2010-10-13
It works now =)
Thank you so much!

---

### Post by luvshines on 2010-10-13
Aah!! I was again looking back thru the posts and then saw that you edited it to say it does work. CLEVER !! 8)

Gr8 to hear that it works :D

**Please mark it SOLVED**

---

