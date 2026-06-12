---
title: "encrypted password in samba credentials file"
date: 2010-04-20
forum: Networking &amp; Wireless
---

### Post by alecz20 on 2010-04-20
Hello

I remember that some time ago I found a guide on the Ubuntu website about adding samba shares to mount at boot via /etc/fstab.

The guide also mentioned using a credentials file to store the username and password.

However, the password was encrypted (in md5 I think) and it could not be read directly, but it still worked with fstab mount.

If I remember correctly, the file contents were similar to this:
```

useraname = user
password = --md5 *************

```
where ********** was replaced by the encoded password. All was done in terminal.

Recently I changed computers, and re-installed Ubuntu, but I forgot to save that file so I am not sure about the contents. 
I would like to know how to do this again, but I can't find the guide anymore.

Does anyone know how to do this?

Storing the password in plain text in file readable only by root is not acceptable because it can be read by someone mounting the drive from other operating system, and the share cannot be mounted/unmounted by regular users (which is possible with the md5 encrypted password).

---

### Post by Razor X on 2011-07-31
I hate to reopen an old topic, but this post was the only reference to an alternative to storing samba passwords in clear text on the client. I have the same question as alecz20. I can't imagine we are the only two people who share this concern.

Does anyone know a good way to authenticate *nix clients with a samba file sever without storing passwords in clear text on the client?

Thanks.

---

### Post by ionsquare on 2012-11-13
Still no answers? Anyone? I'd like to know this too...

---

### Post by alecz20 on 2012-11-13
My network topology has changed so I don't nee this that much anymore, but I would still like to have a solution.

So far I have also found this thread:
[http://ubuntuforums.org/showthread.php?t=1111986](http://ubuntuforums.org/showthread.php?t=1111986)

Essentially, you can use pam_mount to mount the remote filesystem right after the login.

> **albandy said:**
> Explanation of what is PAM:
[http://en.wikipedia.org/wiki/Pluggable_Authentication_Modules](http://en.wikipedia.org/wiki/Pluggable_Authentication_Modules)

how to make pam automount your shared resources:
first install pam_mount:
sudo apt-get install libpam-mount
then edit the file /etc/security/pam_mount.conf.xml
add something like this:

<volume fstype="smbfs" server="myserver.mydomain.org" path="shared_folder" mountpoint="/mnt/%(USER)/myremotehome" options="dmask=0700" />

finally add this to the file /etc/pam.d/gdm 
@include common-pammount 
(it should be added after the line which contents @include common-session)



in the file /etc/pam.d/common-pammount you can define how pam_mount should work, by default works ok, but you can modify some restrictions as setting it to required to don't allow login if can't mount the share or optional if you want to login anyway.

---

### Post by wildmanne39 on 2012-11-13
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

