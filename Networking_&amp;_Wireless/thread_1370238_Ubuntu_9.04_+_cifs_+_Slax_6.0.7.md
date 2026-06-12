---
title: "Ubuntu 9.04 + cifs + Slax 6.0.7"
date: 2010-01-02
forum: Networking &amp; Wireless
---

### Post by 10nitro on 2010-01-02
So, I'm sitting here on my laptop running Ubuntu 9.04 desktop, and I ssh to a Slax 6.0.7 box downstairs.  Then I realize that I still need access to local files on my desktop.

I pop open nautilus on my laptop, right-click on th directory I need, and select `Sharing Options'.  I check the first box (``Share this _f_older'', and name it `ipl'.  It pops open a box telling me I need to install a package, I do so, it tells me I need to restart the session; I log out and back in.

I add the line ```
/home/luke/Development/ipl *(rw,sync,no_subtree_check)
``` to /etc/exports, and run the command to update this.

So I get back in on the Slax box, and mount the share with the command ```
mount -t cifs -o 'user=luke' HP-dv6426us-u904:ipl ipl/
```.  This appears to work, but I soon discover that I do not have write access.

I see that the files are owned by UID 1000, I create a user with that ID, no luck.
I try the command ```
mount -t cifs -o 'user=luke' -o rw -o uid=0 HP-dv6426us-u904:ipl ipl
``` instead. Still no luck.

I see the ``Allow other people to write in this folder'' checkbox in the sharing dialog box in Ubuntu, however, it tells me that it will change file permissions, the current file permissions are relevant, I'd rather let the system know that I am the same user.

---

