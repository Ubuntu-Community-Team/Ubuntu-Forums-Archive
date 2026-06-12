---
title: "Variable write access to a NAS mounted with CIFS"
date: 2009-06-21
forum: Networking &amp; Wireless
---

### Post by mageus on 2009-06-21
I have a Dlink DNS-323 mounted via cifs.  I can and can't write to it depending on the scenario.

From command line or Krusader, user account or root:
- can create/delete/rename files
- can't overwrite a file
   error on cp - cannot create regular file `<filename>': No such file or directory

From other programs I get variable write access.
- some can create/delete/rename files
- some can't do any write functions to a file
- none can overwrite a file

My permissions are set up
- NAS has me with full r/w access to drive
- The mount point has permissions 777
- All files on the NAS have a uid 502, gid 702 (my user is 1000)
- tried mounting cifs with option "uid=<myid>"


I'm thinking it has to do with the different uids, but then why would all write functions work except overwrite?


Ubuntu 9.04
DNS-323 fw 1.06

---

