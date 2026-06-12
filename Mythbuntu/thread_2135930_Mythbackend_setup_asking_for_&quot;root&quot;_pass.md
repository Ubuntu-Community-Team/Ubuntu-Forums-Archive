---
title: "Mythbackend setup asking for &quot;root&quot; password"
date: 2013-04-15
forum: Mythbuntu
---

### Post by dannyboy79 on 2013-04-15
I just ran into something weird. I first install Ubutnu minimal 12.04, then I installed mythbuntu-desktop. I could run mythbuntu-control-center just fine but when it came time to run the mythtv-backend setup command it  wanted to add my user to the mythtv group first and asked for the password of the current user which kept failing. I struggled with this message for a while and even tgm user within mythtv-ubuntu in IRC chat couldn't help. I thought to look within /var/log/auth.log and it showed the following error: 
```
pam_unix(su:auth): authentication failure; logname= uid=1000 euid=0 tty=/dev/pts/2 ruser=daniel rhost=  user=root
Apr 15 17:20:07 dell su[14361]: pam_authenticate: Authentication failure
Apr 15 17:20:07 dell su[14361]: FAILED su for root by daniel
Apr 15 17:20:07 dell su[14361]: - /dev/pts/2 daniel:root
Apr 15 17:20:13 dell su[14366]: pam_unix(su:auth): authentication failure; logname= uid=1000 euid=0 tty=/dev/pts/3 ruser=daniel rhost=  user=root
Apr 15 17:20:15 dell su[14366]: pam_authenticate: Authentication failure
Apr 15 17:20:15 dell su[14366]: FAILED su for root by daniel
Apr 15 17:20:15 dell su[14366]: - /dev/pts/3 daniel:root
Apr 15 17:20:20 dell su[14371]: pam_unix(su:auth): conversation failed
Apr 15 17:20:20 dell su[14371]: pam_unix(su:auth): auth could not identify password for [root]
Apr 15 17:20:20 dell su[14371]: pam_authenticate: Authentication failure
Apr 15 17:20:20 dell su[14371]: FAILED su for root by daniel
Apr 15 17:20:20 dell su[14371]: - /dev/pts/5 daniel:root

```
which made me realize that the dialog box was asking for a root password which there was none. Before I figured out what to do I manually added myself to the mythtv group within the users and groups section and logged out and back in and I was getting past the adding my user to the mythtv group error at least but it was asking to stop the mythbackend server and for a password again and it was still failing. So i thought to actually create a root password using ```
sudo passwd root
``` (i made it the same as my user, not sure of the security implications of this) and now it's working at least.

Not sure if this is a design of the mythbuntu-desktop scripts but I would think if the intention was to not have the root account enabled then why would the scripts ask for a root password. Also, I believe that mythbackend is run as root. Oh well, at least now it's working.

---

### Post by mail-lakepowellforest on 2013-09-02
Thank you. This had me stumped.

---

### Post by steeldriver on 2013-09-02
I missed the original thread but since you've bumped it, before resorting to setting password for root I'd suggest running

```
gksu-properties
```

and making sure the mode is set to 'sudo' not 'su'

---

### Post by tgm4883 on 2013-09-04
I missed this thread as well, but I'd like to reply to some of the content here.

> **dannyboy79 said:**
> I just ran into something weird. I first install Ubutnu minimal 12.04, then I installed mythbuntu-desktop. I could run mythbuntu-control-center just fine but when it came time to run the mythtv-backend setup command it  wanted to add my user to the mythtv group first and asked for the password of the current user which kept failing. I struggled with this message for a while and even tgm user within mythtv-ubuntu in IRC chat couldn't help. I thought to look within /var/log/auth.log and it showed the following error: 


I'm wondering if ubuntu-minimal does something weird here.

> **dannyboy79 said:**
> 
which made me realize that the dialog box was asking for a root password which there was none. Before I figured out what to do I manually added myself to the mythtv group within the users and groups section and logged out and back in and I was getting past the adding my user to the mythtv group error at least but it was asking to stop the mythbackend server and for a password again and it was still failing. So i thought to actually create a root password using ```
sudo passwd root
``` (i made it the same as my user, not sure of the security implications of this) and now it's working at least.


Please don't do this or recommend people add a root password. This isn't necessary.

> **dannyboy79 said:**
> 
Not sure if this is a design of the mythbuntu-desktop scripts but I would think if the intention was to not have the root account enabled then why would the scripts ask for a root password. Also, I believe that mythbackend is run as root. Oh well, at least now it's working.

The scripts are attempting to stop (and start) the backend process. In order to do that, it needs credentials from an admin user. Also, the backend is not run as root, it is run as the mythtv user.

---

