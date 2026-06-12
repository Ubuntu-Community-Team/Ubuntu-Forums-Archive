---
title: "UEC broken with upgrade."
date: 2010-09-08
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by pnunn on 2010-09-08
Hi folks,

I just upgraded my UEC cloud to meerkat to try and use the eucalyptus 2.0 tools that are installed within it (as I couldn't find them in a 10.04 package).

The install appears to have gone OK, but now my cloud in broken..

I can't seem to register any clusters even though the logs seem to indicate that they are working OK and are being seen by the CC.

When I try and log into the front end on the CC I get an error:

"The call failed on the server; see server logs for details"

I've looked in the logs and can't really see anything that makes sense, however, when I do a 

euca-describe-clusters

I get..

Traceback (most recent call last):
  File "/usr/sbin/euca-describe-clusters", line 4, in <module>
    from euca_admin.clusters import Cluster
ImportError: No module named euca_admin.clusters

and other describe-* commands return similar problems.  This looks like an issue to me.. but I'm not sure where to start looking to try get tis going again.

Ta

Peter.

---

### Post by pnunn on 2010-09-08
OK.. got around the login issue by resetting my password on the interface, now logged in, but there are no "VM Types" on the configuration page, I'm assuming that this is because of the nodes not being registered correctly.

The odd thing is that when I do a

sudo euca_conf --no-rsync --discover-nodes

The two node controllers are discovered, but they are reported by IPV6 address rather that IPV4 as they were in UEC 1.6.  Is that causing the issues?

Ta
P.

---

### Post by cariboo on 2010-09-08
You might have better luck getting your question answered in the [Ubuntu Cloud]("http://ubuntuforums.org/forumdisplay.php?f=392") sub-forum, I think this is the first cloud question, we've seen this cycle.

---

### Post by pnunn on 2010-09-08
OK, thanks I'll do that.  It was all working before the upgrade.. grrr... oh well, guess that's what you get on the bleeding edge.

Peter.

---

