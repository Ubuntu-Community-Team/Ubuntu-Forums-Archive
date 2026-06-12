---
title: "How does networking work with Ubuntu?"
date: 2009-05-22
forum: Networking &amp; Wireless
---

### Post by jbruced on 2009-05-22
Quickly,

3 computers

#1 jaunty
#2 ibex  (has fat32 external USB drive)
#3 ibex


on computer #2
reloaded #2 from scratch (8:10), all updates(stayed with 8.10 so as not to lose ati drivers)


on #2 right click folder on usb drive, opened everything
checked share
checked allow other people to write to folder
checked all guests

CHECKED EVERYTHING!!!! Used to work before reload.

Frustration, over 1 year with Ubuntu and still can't get it right.

Help me!!!!  

CAN NOT CONNECT!

---

### Post by Iowan on 2009-05-22
I presume this is a Samba share?

---

### Post by superprash2003 on 2009-05-23
are all pcs able to ping each other?

---

### Post by jbruced on 2009-05-24
> **Iowan said:**
> I presume this is a Samba share?

yes, works fine for internal hard drive shared folders

---

### Post by jbruced on 2009-05-24
> **superprash2003 said:**
> are all pcs able to ping each other?

yes, works fine for internal hard drive shared folders

---

### Post by roman_platonov on 2009-05-24
check rights access you usb device? by default restricted to logged user (not for samba)/ change access rights to access usb from samba (or samba user if suid)

---

### Post by jbruced on 2009-05-24
> **roman_platonov said:**
> check rights access you usb device? by default restricted to logged user (not for samba)/ change access rights to access usb from samba (or samba user if suid)


As stated, clicked everything to share on folder within the usb drive.


I don't understand how to do what you said?
:-|

---

### Post by Wiebelhaus on 2009-05-24
> **jbruced said:**
> Quickly,

3 computers

#1 jaunty
#2 ibex  (has fat32 external USB drive)
#3 ibex


on computer #2
reloaded #2 from scratch (8:10), all updates(stayed with 8.10 so as not to lose ati drivers)


on #2 right click folder on usb drive, opened everything
checked share
checked allow other people to write to folder
checked all guests

CHECKED EVERYTHING!!!! Used to work before reload.

Frustration, over 1 year with Ubuntu and still can't get it right.

Help me!!!!  

CAN NOT CONNECT!

I'm about to end your frustration mate!



First install samba:

```
sudo apt-get install samba
```

With samba installed on your system, now you need to edit the configuration file which is located at:


```
Sudo nautilus
```



> /etc/samba/smb.conf



Copy and paste this at the bottom with your information as needed: 
 

```
[global]

workgroup = [COLOR="Red"]YOUR_WORKGROUP_NAME[/COLOR]

netbios name = [COLOR="Red"]UBUNTU_SERVER - whatever you want just KEEP_STANDARD[/COLOR]

security = SHARE

auth methods = guest

domain master = No

wins support = Yes

[share1]

comment = mi home

path = /home/[COLOR="Red"]USERNAME IN LOWERCASE[/COLOR]

 

read only = No

guest ok = Yes

```
 

 

    * workgroup; Lets you specify the windows workgroup

    * netbios name; Lets you specify the name with your Linux PC will be seen by windows PCs

    * security; specifies the level of security, default is user, but if the users on the windows PCs are not the same as the ones on the Linux PC, you better use share instead

    * auth methods; Possible options include guest (anonymous access), sam (lookups in local list of accounts based on netbios name or domain name), winbind (relay authentication requests for remote users through winbindd), ntdomain (pre-winbindd method of authentication for remote domain users; deprecated in favour of winbind method), trustdomain (authenticate trusted users by contacting the remote DC directly from smbd; deprecated in favour of winbind method)

    * domain master; Lets you configure your PC as a domain master or not, in this case we prefer not, as our goal is only to share files

    * wins support; If you want or not to have wins enabled or not 

Now comes the shares section, the string you put between the [] will be how windows will sees the share, in this case share1

      path; You put here the path you may want to share

      read only; yes or no, depending if you want to permit other users to write on this directories.

      gest ok; It is a boolean field, and will permit or not guest users to access this resource

For simple file serving this is all that's needed.

---

