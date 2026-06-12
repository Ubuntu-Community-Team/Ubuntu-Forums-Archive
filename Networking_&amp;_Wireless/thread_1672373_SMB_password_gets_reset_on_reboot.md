---
title: "SMB password gets reset on reboot"
date: 2011-01-20
forum: Networking &amp; Wireless
---

### Post by rage_311 on 2011-01-20
Hey,

Hopefully somebody can shed some light on this issue.

I'm using Ubuntu server 10.04 32-bit and I have smbd installed.  Somehow, four users were added to smbpasswd in the first place -- not really sure how that happened.  That's not the problem, just some information.  I really only need to use one user, this user is one of the users that were already added to smbpasswd when I looked at it (via pdbedit -w -L).  This user name is also a user in the passwd file, but I want a different password for samba.  Somehow, after I change it, the password for that user gets reset after a reboot.  It doesn't get reset to the passwd password that's set for that user -- I'm not sure what it gets set to, but it's different than what I just changed it to before the reboot.  This makes it so that I can no longer access my protected shares.  I even added ```
unix password sync = no
``` in the [global] section of the smb.conf file just to make sure.  Does anybody have any idea what's going on?  I've looked around for info/solutions with no luck.  Thanks in advance for any help!

---

### Post by rage_311 on 2011-01-21
Any help?  I'm stumped here.

Maybe I should add that I migrated my setup from a 32-bit Desktop version of Ubuntu 10.04 and that was working just fine... same samba configs, unix passwd file, etc.  Any ideas of something else I could try?

---

### Post by Morbius1 on 2011-01-22
You are not alone. What appears to be happening is that the samba password for userX is being reset to the local server login password for userX at each boot. I can't access the remote share from a client using the smbpasswd but I can using the server login password for userX.

You've got two options:

[1] Don't create a server login password for userX or create a new user for userX strictly for samba uses. For example if my server username = morbius and I want to access the server from a remote machine I would create a new user called morbiusadmin that has no local server login password:
```
sudo useradd -s /bin/true morbiusadmin
```Then create a samba password:
```
sudo smbpasswd -a morbiusadmin
```Without a local login password database to sync with the samba password will not change.

[2] Remove a package that previous versions of Ubuntu didn't have. The process I used was as follows:

Remove the package:
```
sudo apt-get remove libpam-smbpass
```Reset the samba password back to what is should be:
```
sudo smbpasswd -a morbius
```Reboot

[COLOR=Blue]*There's probably some service that needs to be restarted for this to take affect eliminating the need to reboot but I can't find it. Restarting smbd doesn't appear to be enough so I just rebooted.*
[/COLOR] 
The libpam-smbpass package and it's affect can be found in the bug report on this issue: [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/566560](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/566560)

Apparently it's not considered a bug but a feature and is working as designed. When I calm down a little bit and am not as angry I will try to think of a single situation where this would be a desired "feature".

---

### Post by rage_311 on 2011-01-22
Thanks for the detailed reply!  I'm going to give option #2 a go tonight and see if that does it.  It's definitely a "feature" that I am not a fan of...



[EDIT] That worked perfectly!  All is working once again.  Thanks.

---

