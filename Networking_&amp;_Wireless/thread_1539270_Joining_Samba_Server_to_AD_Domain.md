---
title: "Joining Samba Server to AD Domain"
date: 2010-07-26
forum: Networking &amp; Wireless
---

### Post by Audiosears on 2010-07-26
Folks,

Need a bit of guidance with changing over our Samba server such that authentication is handled through Active Directory rather than locally.  We have been using the Samba server in workgroup mode, which was OK with XP and previous Windows clients, but Vista+ utilizes NTLM and other newer handshaking techniques, and I have been unable to correct some of the major/minor annoyances resulting (see [http://ubuntuforums.org/showthread.php?t=1527521]("http://ubuntuforums.org/showthread.php?t=1527521")).

Found [this]("http://www.builderau.com.au/blogs/codemonkeybusiness/viewblogpost.htm?p=339270746") guide (see post 71):

> you could simply use the default Vista settings and do the following:

On the *nix box (or ssh onto it) run

vi /etc/samba/smb.conf

then edit the smb.conf file to include the next lines in the GLOBAL section. Make sure the actual domain name (realm) is in UPPER CASE (i.e realm = MYDOMAIN.LOCAL)

[global]
idmap gid = 10000-20000
netbios name = yourmachinename
idmap uid = 10000-20000
workgroup = YOURWORKGROUP (yourdomain short name)
os level = 20
security = ADS
encrypt passwords = yes
winbind trusted domains only = yes
realm = YOURDOMAIN.INT
winbind enum users = no

Now on the *nix box entre :
/etc/init.d/smb restart
/etc/init.d/nmb restart -(if not restarted by smb)
/etc/init.d/winbind restart

net join -U administrator -S FQDN_of_Server

when requested entre the password and your samba will be a domain memeber.

Sounds good, but the usernames are totally different on Samba as they are on AD.  Does this mean I will have to remap all my users on the Samba server to match AD?

i.e. currently user 'bob' on Samba might be 'RJericho' on AD.  Does this mean I then have to kill the 'bob' account in Samba and migrate files/etc to 'RJericho'?  This would also mean changing folder permissions here and there from 'bob' to 'RJericho'.

Might there be an easier method of converting usernames rather than doing it manually?  I want to avoid having to effectively take down the Samba server (by joining it to AD) and then manually updating each user, causing inaccessibility until each user is updated..

Currently running Samba 3.4.7 on Ubuntu 10.04 server.

---

### Post by Audiosears on 2010-08-03
[Bump]

Anyone had any experience with joining Ubuntu 10.04 to an AD domain that has been running under workgroup mode for some time?

I already found enough information on joining itself, but I'd like to find the best way to do this with the least downtime for network shares as possible.

AFAIK, I will have to redo all the usernames on the Samba side so they match usernames defined by AD (current legacy usernames in Samba are totally different).  Rather than do that one at a time, might there be a better way to batch-convert current usernames to a new username set?  Is there a defined process for something like this?

Any help much appreciated...

Regards,

Erik

---

