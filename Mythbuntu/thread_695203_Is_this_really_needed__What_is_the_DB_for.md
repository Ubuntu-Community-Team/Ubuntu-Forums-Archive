---
title: "Is this really needed?  What is the DB for?"
date: 2008-02-12
forum: Mythbuntu
---

### Post by volkswagner on 2008-02-12
I new setting up a multi machine environment would be a challenge.  Two months later I am still pecking away.  Good for me writers strike allowed for no missed programs for the Mrs.  :)

I am trying to access my music from a slave BE/FE machine.  I can access all my music on the master machine which also runs a FE.  All sub folders in var/lib/mythtv on master machine are listed SMB shared folders.

Why is recordings the only folder correctly functioning in the database as shared throughout the system?

Do I really need to perform the steps mentioned here?  Or should it just work?

[http://ubuntuforums.org/showthread.php?t=680494&highlight=share+music]("http://ubuntuforums.org/showthread.php?t=680494&highlight=share+music")

It seems to me a STICKY should be in place for general post install steps not listed as part of the install instructions.

ie:Proper steps to change of Mysql password for user mythtv, doing it via myth does nothing.  Just this one item could possibly have reduced numerous posts.

Done ranting  :mad:

---

### Post by tgm4883 on 2008-02-16
recordings are the only thing that are transfered over the mythtv backend protocol.  You need to share the music, pictures, movie directories with something like NFS or CIFS

---

### Post by volkswagner on 2008-02-16
Thanks for the information.  I will add the shares to remote frontend.

---

