---
title: "permissions on files copied via nautilus-share"
date: 2010-01-09
forum: Networking &amp; Wireless
---

### Post by abovett on 2010-01-09
Hi

I have two user accounts on my Ubuntu machine - mine and my wifes. Using my account, I created a folder which I shared via nautilus-share so we could copy files to it from a Windows PC. I also used my username and password when connecting to the share from the Windows PC. I was able to copy the files OK, but found that when they arrived in the shared folder my wife could not modify them because they were owned by me and the permissions were 755 (i.e. rwxr-xr-x).

Is there a way via nautilus-share of sharing folders so that files we put in them are writeable by both of us? We are both members of each others groups so creating the files with permissions 775 would do. The umask is set to 002 in /etc/profile so that files we create locally have permissions 775 by default but this doesn't seem to take effect when using nautilus-share.

Thanks

Andy B

---

