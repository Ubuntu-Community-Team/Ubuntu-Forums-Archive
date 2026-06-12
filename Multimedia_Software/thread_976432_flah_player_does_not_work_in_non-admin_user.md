---
title: "flah player does not work in non-admin user"
date: 2008-11-09
forum: Multimedia Software
---

### Post by jabadabuntu on 2008-11-09
Hi,

when I go online with a non-admin user an then go on youtube flashplayer doesn't work. When I try to install flashplayer I am asked for the admin password but it is not accepted. Flashplayer is already installed on the admin user. Does anybody know how to get flashplayer running on a non-admin user?

jabadabuntu

---

### Post by aysiu on 2008-11-09
How did you install Flash to begin with?

And what do you mean by "admin user"? Do you mean a user who can use Add/Remove and the System > Administration menu items? Or did you somehow activate the root account?

---

### Post by gandaran on 2008-11-09
maybe flash is installed only on one home user account, if flash is installed in root file system all users can use it, check that,
you can also fix this by just coping the flash plugin from one home user account to another

---

### Post by jabadabuntu on 2008-11-11
How do i check if the flash player is installed in root file system? I can't find any folder where there is something like flash player...

jabadabuntu

---

### Post by aysiu on 2008-11-11
How did you install Flash? What steps did you take?

---

### Post by psyke83 on 2008-11-11
> **jabadabuntu said:**
> Hi,

when I go online with a non-admin user an then go on youtube flashplayer doesn't work. When I try to install flashplayer I am asked for the admin password but it is not accepted. Flashplayer is already installed on the admin user. Does anybody know how to get flashplayer running on a non-admin user?

jabadabuntu

I suspect you misunderstand the way administrative privileges work (especially compared to pre-Vista Windows versions).

In Windows XP and prior, creating a new user will give you administrative privileges by default - but there is no distinction between privileged and unprivileged (user vs superuser). On a standard XP installation, if you launch Firefox and browse the internet, then your Firefox process will be running with administrator privileges.

If you create a user in Ubuntu with the "Administrator" profile, it's not equivalent to a Windows Administrator account - by default you will still run as an ordinary user for most tasks. Firefox will not run with administrator privileges, for example.

If you wish to perform an administrative task (such as installing new packages) you will need to elevate to superuser status using sudo (via the terminal), or automatic GUI prompts - this requires the user to enter their password.

Windows Vista replicates this behaviour with the new UAC (User Account Control) prompts.

So in other words: your account should be set as an Administrator.

---

### Post by jabadabuntu on 2008-11-12
:confused: ok it's like this:

as i installed ubuntu, i created 2 user accounts, say user1 and user2. user1 is able to install packages and stuff like this so i guess user1 has administrative privileges (does it mean this is the root account?). user2 has not such rights. i installed the flash player with user1 since user2 is not able to install anything.

@aysiu: i guess i installed the flash player by downloading the appropriate file from adobe.com. sorry, it's been a while since i've done this, i can't remember all steps i took...

@psyke83: i dont't think that it is necessary to be logged in as an administrator just to get flash player to run

---

### Post by gandaran on 2008-11-12
jabadabuntu
post the output of **locate libflash** this shows where flash is installed

---

### Post by psyke83 on 2008-11-12
> **jabadabuntu said:**
> 
@aysiu: i guess i installed the flash player by downloading the appropriate file from adobe.com. sorry, it's been a while since i've done this, i can't remember all steps i took...

Ok, that's your problem. If you installed flash player manually, then the plugin got installed into the ~/home/user1/mozilla/plugins folder. Other users (including user2) cannot access this file.

```
$ sudo updatedb
$ locate libflashplayer.so

```

Delete all instances of the "libflashplayer.so" file you find. 

Finally:
```
$ sudo apt-get install flashplugin-nonfree
```

This will make the plugin available to all users.

---

### Post by jabadabuntu on 2008-11-12
yeah! it works! i did the steps posted by psyke83 and after a restart worked everything fine...

thanks a lot

---

### Post by wandalalakers on 2008-11-16
I'm using 8.04 32 bit.  Thx.

I still can't get the flash player to work for a non-admin user.
I did the following:
sudo updatedb
locate libflashplayer.so

result:
/usr/lib/flashplugin-nonfree/libflashplayer.so

I'm an admin user and I'm able to go to adobe.com and see the animamtion on the front page.
I login as a non-admin user and that user doesn't see any flash animation when going to adobe.com on the front page.

I'm going to create a second user just to see what happens.

---

