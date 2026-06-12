---
title: "Need help setting up a shared folder"
date: 2009-05-18
forum: Networking &amp; Wireless
---

### Post by diablo75 on 2009-05-18
I'm doing a little work for someone by remote.  They have 3 PCs in their network, all in the same IP network address range.

So far I've only attempted to setup a share between two PCs (the third is not essential).

On the first PC, I created a folder in their home folder and called it networkshare.  I then right-clicked on it and went to sharing options.  Upon checking off the box to enable sharing, I was prompted to install some extra packages (I'm assuming Samba, right?).  I installed the packages, canceled the box out, and then restarted the system.  We then right-clicked on it again to setup sharing options and checked off all three boxes to allow sharing and read/write access to guests.  Pretty standard, really.

Now, on the second PC, when I right-clicked and hit sharing options, checked off the box to enable sharing, I was not prompted to install anything.  I proceeded to check all three boxes off like I did on the first one.  On this second PC, I would then click Places>Network and in there would be a "Windows Network" icon.  If I double-click on that I get an error message that says:  Unable to mount location
Failed to retrieve share list from server.

Nothing else but the Windows Network icon appears.

Both systems are running 9.04 which were upgraded from 8.10 and as far as I know have never had network sharing enabled before.

---

### Post by Wiebelhaus on 2009-05-18
First install samba

```
sudo apt-get install samba
```

With this you will have samba installed on your system, now you need to edit the configuration file which is located at:

/etc/samba/smb.conf
```

Sudo nautilus
``` then surf to that location and open the config file to edit.

A simple minimal configuration to allow share files from your Linux server.

 

```
[global]

workgroup = MSHOME - [COLOR="Red"]change to your workgroup[/COLOR]

netbios name = UBUNTU_SERVER [COLOR="Red"]name it whatever you want but remember to keep the standard ALL_CAPS[/COLOR]

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



For simple sharing that is all that is needed , cheers!

---

### Post by diablo75 on 2009-05-18
Hey that's one handy and super simple guide!  Thanks a ton!!

---

### Post by Wiebelhaus on 2009-05-18
> **diablo75 said:**
> Hey that's one handy and super simple guide!  Thanks a ton!!

No worries mate and if you have an issues just reply , cheers!.

---

