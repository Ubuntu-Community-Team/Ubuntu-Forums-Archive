---
title: "[SOLVED] Mythweb not working - just default apache"
date: 2007-11-14
forum: Mythbuntu
---

### Post by ubnewbie2 on 2007-11-14
On a newly installed mythbuntu box, mythweb is ticked in the control centre, and I added a username/password for it.

I then tried to surf to the box (or even using firefox on the box to localhost, and all I get is a directory list with the "apache2-default"  - when I click on this, it says "It worked!"

So, no mythweb?

---

### Post by napsilan on 2007-11-14
Add /mythweb to the end of the adress

Mythbuntu control center probably already set the permissions in apache such that mythweb is passworded, and won't show up in the directory list.

---

### Post by ubnewbie2 on 2007-11-14
> **napsilan said:**
> Add /mythweb to the end of the adress

Mythbuntu control center probably already set the permissions in apache such that mythweb is passworded, and won't show up in the directory list.


Thanks, that got it going - but now I am getting a Database access denied error when I log in

---

### Post by ubnewbie2 on 2007-11-14
ahh fixed it - found this thread  [http://ubuntuforums.org/showthread.php?t=590858&highlight=database+access+denied](http://ubuntuforums.org/showthread.php?t=590858&highlight=database+access+denied)

where someone said

"ok now I resolved the problem, the password in /etc/mythtv/mythweb-htaccess was not the same like in /etc/mythtv/mysql.txt and everytime I run dpkg-reconfigure mythweb the password will be replaced with a wrong one :-/"

by making mine the same, it now works

bug?

---

