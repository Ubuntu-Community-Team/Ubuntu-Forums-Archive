---
title: "Using samba to browse Windows share"
date: 2012-11-11
forum: Networking &amp; Wireless
---

### Post by Annorax on 2012-11-11
Hello all,

I have Kubuntu 12.10 and Windows XP. On Windows I have my entire hard drive shared as "C$". Using smb4k, I am able to mount and browse most of the Windows machine. However, there are some folders (my user's documents folder, Program Files, etc...) which I am able to browse to but are blank. I am assuming this is because of some user authentication. I have set the default user and password properly but despite this, the folders are still blank.

Does anyone have any ideas?

---

### Post by gerowen on 2012-11-12
Have you tried browsing the C$ share with the file browser to see if maybe it's smb4k having issues with authentication?  Try pointing a file browser to smb://WINDOWSMACHINE/C$ and see if it prompts you for username and password and functions properly.  Just a random idea.  Also make sure the username and password you provide are that of an account with administrative privileges, because even if you're only browsing to your user profiles, C$ is an administrative share., so it requires more elevated rights than if you browsed to a folder you shared yourself.

---

