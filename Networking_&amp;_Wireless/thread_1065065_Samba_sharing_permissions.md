---
title: "Samba sharing permissions"
date: 2009-02-09
forum: Networking &amp; Wireless
---

### Post by samba_man on 2009-02-09
Evening All!

Where I work (a college), we have a shared folder running off Samba on Ubuntu 8.04 sharing to 25 Windows XP clients all logged on as different users. The clients are connected to the server all as guests with full access, this has been the case for a couple of years now.

Today, some students decided that it would be helpfull to delete other students work, thankfully I am paranoid about backups and only an hours work was lost. This whole scenario happened again later today.

I know with NTFS we are able to set a special permission to allow everything but deletion of files to a certain user (say guest) but Linux working using UGO doesn't have these special permissions.

I've found a few things while racking my brain today including a 'fix' using chmod to only allow the owner to delete the file, this could work if the permissions of a newly created file where immediatly iherited from the parent to change the ownership to a different account.

Something else that has crossed my mind is installing an NTFS formatted HD into the server with the relevant NTFS permissions set, would these permissions then carry onto the client machines, or would Ubuntu's Samba take over?

Something I might look into is integration into the Win 2k3 domain to see if I will gain anything...

Sorry for the long first post!
I'd be grateful for your help.

---

### Post by dmizer on 2009-02-09
The problem with common shares is that everyone has equal access. You can't have everyone be equal, but not equal.

I would suggest giving each student their own space, and if collaboration is needed, make the share visible but read only to non-owner logins. See the first link in my sig for information on how to configure Samba for user based logins.

It's more work for you for initial setup, but less headache in the long run.

---

### Post by redmk2 on 2009-02-10
use sticky bit on the directory and files.  This means that only the owner and root can delete.  See below:
```
        
create mask = 3775
force create mode = 3775
directory mask = 3775

```

---

### Post by dmizer on 2009-02-10
> **redmk2 said:**
> use sticky bit on the directory and files.  This means that only the owner and root can delete.  See below:
```
        
create mask = 3775
force create mode = 3775
directory mask = 3775

```

I'm not sure I completely understand the recent "sticky bit" fad. It's certainly not a solution for Samba shares where none of the users have a local login. In Linux, the sticky bit ONLY works on the directory level, not the file level. So, in a Samba share environment, everyone has to have access to the common share, so everyone has sticky bit permission.

More information here: [http://en.wikipedia.org/wiki/Sticky_bit](http://en.wikipedia.org/wiki/Sticky_bit)

The proper way to handle this problem is to give individuals separate shares and only use the common share for file which everyone has a stake in preserving.

---

### Post by samba_man on 2009-02-11
Thanks for the replys :)

I appear to have fixed the problem now using a combination of the sticky bit and owner/group configuration.

I'm currently writing some notes on what I did for my personal future reference but will get around to making a generalised version for the benefit of others some point in the next few days ;-)

---

