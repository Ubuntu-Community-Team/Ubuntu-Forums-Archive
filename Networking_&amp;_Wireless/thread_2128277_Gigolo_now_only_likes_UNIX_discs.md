---
title: "Gigolo now only likes UNIX discs"
date: 2013-03-22
forum: Networking &amp; Wireless
---

### Post by dave0109 on 2013-03-22
I have a bunch of bookmarks in Gigolo for accessing Samba shares on PVRs etc.  I don't need to do this very often, and it's been a while.  This week, I get an error in Gigolo:-

> Connecting to "smb://user@host/share/" failed.
Location is not mountable


If I go to Help -> Supported Protocols, it lists "Unix Device (file)" and that's it.  Somewhere down the line gigolo seems to have lost the ability to handle other protocols.

If I use 'smbtree -b' then I get a list of the configured workgroups, and it shows the PVR share that I'm trying to get to.  So as far as I can tell from that, the Samba client is working.

A few weeks ago, I was trying to MTP working to my phone, and I did install a different (newer) version of the mtp tools stuff, though I have subsequently backed out of that.  It's the only change that I've made recently, but I can't think what's missing for Gigolo to do samba (or SSH for that matter).

---

### Post by dave0109 on 2013-03-23
Fixed it.  For reference, I had not rolled back all the GVFS packages correctly, so I did a ppa-purge, then had to re-install gvfs-backend which then lets Gigolo use multiple protocols.

(I don't see how to mark this thread as resolved. It used to be in thread tools, but isn't there now.)

---

### Post by Toz on 2013-03-23
Thanks for posting back the resolution. 

The "marking threads as solved" plugin is not currently enabled. Please follow the workaround instructions [here]("http://ubuntuforums.org/showthread.php?t=2121377&p=12536730&viewfull=1#post12536730") to mark this thread as solved.

---

