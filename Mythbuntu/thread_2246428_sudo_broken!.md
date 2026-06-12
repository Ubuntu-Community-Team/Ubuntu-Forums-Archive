---
title: "sudo broken?!"
date: 2014-09-30
forum: Mythbuntu
---

### Post by Jason_Gauthier on 2014-09-30
I upgraded my backend and my frontend to 14.04.

Now, sudo is busted.  I didn't change the config, but maybe I should have?  Everytime I try to sudo, I get prompted for a password. I configured this to not prompt me for a password over 5 years ago!

Thoughts?

-------
/etc/sudoers
jgauthier       ALL=NOPASSWD: ALL

~$ sudo ls
[sudo] password for jgauthier:




Thanks!

---

### Post by Jason_Gauthier on 2014-09-30
ugh.  Of course. As soon as I post.  Apparently config changed somewhere and I had to move the entry to the end of the file.

---

