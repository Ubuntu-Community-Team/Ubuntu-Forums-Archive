---
title: "Server Timeout - While Browsing Network"
date: 2010-10-25
forum: Mythbuntu
---

### Post by b1acksun on 2010-10-25
**Server Timeout - While Samba Browsing** 			
 			 			 		   		 		 		Having allowed  Samba to be upgraded on all my networked machines, after rebooting the  machines to allow a clean Samba start, to my horror couldn't see any  machines or directories on my network.

The Mythbuntu box was partially affected it was able to get get files  from the Freenas NAS Box, trying to browse failed with the Server  Timeout Message.

Using smb://xxx.xxx.xxx.xxx in the url of Dolphin or firefox did allow  browsing; telling me that Samba was generally fine and that it was  likely to be a configuration issue.

Plenty of experiments with the /etc/samba/smb.conf - gave me the following apparent fix.

name resolve order = lmhosts bcast host


The default for samba is:
name resolve order = lmhosts wins hosts bcast

Hope this is useful.

---

