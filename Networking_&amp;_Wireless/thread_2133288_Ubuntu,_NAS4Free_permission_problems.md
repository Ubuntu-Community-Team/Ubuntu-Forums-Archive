---
title: "Ubuntu, NAS4Free permission problems"
date: 2013-04-07
forum: Networking &amp; Wireless
---

### Post by RandyN on 2013-04-07
Greetings! I've recently setup a NAS4Free box with CIFS running. I've setup 2 shares on the NAS box:[B]

Public[/B] drwxrwxr-x (group set to group / owner set to root)
 **Randy **drwx------   (group set to wheel / owner set to Randy)

The NAS box has a group account for Public & a user account for Randy (also a member of the Public group).

Both my PC's have the same username/password and while My Windows 7 PC has full access my Ubuntu 12.1 PC can only  read and when I try to write I get a 'permission denied' error. This occurs on both shares.

Since the NAS box works fine on the Windows PC I wondering if I have a *nix issue going on. Any suggestions?

TIA,
Randy

---

### Post by tgalati4 on 2013-04-07
Perhaps set group to Randy as well, or add Randy to the wheel group.  Try both and see which works.

```
sudo useradd -g wheel Randy
```

Not sure what the freenas syntax is for changing group.  Probably *chown*.

Yes: (But you have to log in as root)

```
chown -R Randy:Randy directory
```

That should recursively flow down to all subdirectories and files under *directory*.  Do a test file first to see if you can see the share.

I'm running an older version of freenas:

freenas:/mnt/Freenas2/Johns_Stuff# uname -a
FreeBSD freenas.local 7.3-RELEASE-p3 FreeBSD 7.3-RELEASE-p3 #0: Tue Nov  2 22:42:55 CET 2010     [email]root@dev.freenas.org[/email]:/usr/obj/freenas/usr/src/sys/FREENAS-i386  i386

Nas4free may be different.

---

### Post by RandyN on 2013-04-08
Tried a couple of things. I'm new to the world of Linux so I've been using WinSCP from my Win7 PC to change ownership & permissions. 

I added the Randy acct to the wheel group as per your suggestion and also added permissions for the wheel group to that acct.

Randy drwxrwx--- Randy(owner)/wheel(group)

 Public drwxrwxr-x Randy(owner)/Public(group) I called Public "group" in the OP by mistake. Changed the owner to Randy from root.

Still not having any luck. 

I tried the chown you suggested and got an illegal group name error. The CLI still giving me a headache so for now I prefer to use WinSCP. 

Given that I have no problems reading/writing from my Win7 (and an XP PC) I'm still wondering if it's an issue from my Ubuntu PC. When I open a Terminal window it shows: randy@dellcore2 could the lowercase r in randy be the issue? I'm really at a loss and clutching at straws now hehe.

---

### Post by RandyN on 2013-04-09
I posted this question at the NAS4Free forums and received the following solution:

With Ubuntu connect to smb share using Nautilus - Connect to Server option using the Windows share option - (in this case you can connect as normal user).

I thought I would pass this along in case it helps someone else down the road.

---

