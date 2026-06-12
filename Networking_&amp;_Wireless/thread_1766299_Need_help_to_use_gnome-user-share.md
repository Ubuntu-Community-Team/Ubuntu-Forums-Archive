---
title: "Need help to use gnome-user-share"
date: 2011-05-24
forum: Networking &amp; Wireless
---

### Post by drunkfish on 2011-05-24
When try to share my files between two Ubuntu 11.04-x86_64 machines, I could find the shared icon under network folder in my home directory. But it is just an icon, when I click on it, there is an error message pop-up (the screen-shot attached)

Do you have any idea on this error?

---

### Post by Morbius1 on 2011-05-24
This is a long shot but you will get a similar error in Samba if the remote client used "Remember Forever" when applying the password to access the remote share.

If you go to "Personal File Sharing" and select "Never" to the "Require Password" option does the problem go away?

---

### Post by drunkfish on 2011-05-24
Thanks for response, Morbius1

It is the same message after I change to 'require password'.

---

### Post by Morbius1 on 2011-05-24
Bad news I'm afraid. I installed the requite packages to get this thing functional and have encountered the same problem.

There's a year old bug report that doesn't seem to be going anywhere that describes the problem: [https://bugs.launchpad.net/ubuntu/+source/gnome-user-share/+bug/582542](https://bugs.launchpad.net/ubuntu/+source/gnome-user-share/+bug/582542)

---

### Post by drunkfish on 2011-05-24
Ok, I acknowledge this is a bug of Natty build in function and hope it could be solved soon; thanks for your help.

---

