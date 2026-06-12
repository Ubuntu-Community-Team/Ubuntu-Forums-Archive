---
title: "[SOLVED] 8.10 Diskless client + ability to update display drivers?"
date: 2008-12-20
forum: Mythbuntu
---

### Post by stiev3 on 2008-12-20
I've recently moved to 8.10 through a fresh install.  I'm noticing that any diskless clients I build now seemingly have no connection to the web.

Any attempts to update their drivers are met with errors that the package sources are unreachable.

Should I still be able to download packages etc... through each specific client, or is it by design that they're seemingly disconnected.

Could it be an issue with my iptables settings?  My configuration nearly mimics the basic one found here: [http://ubuntuforums.org/showthread.php?p=5887413](http://ubuntuforums.org/showthread.php?p=5887413) if that helps.

---

### Post by stiev3 on 2008-12-20
Found the solution in this post:
[http://www.uluga.ubuntuforums.org/showpost.php?p=6060607&postcount=5](http://www.uluga.ubuntuforums.org/showpost.php?p=6060607&postcount=5)

A setting to turn ipforwarding on wasn't sticking for some reason.

---

