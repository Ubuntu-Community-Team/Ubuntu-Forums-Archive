---
title: "Unablle to find Upnp Backend"
date: 2009-05-30
forum: Mythbuntu
---

### Post by bcudda on 2009-05-30
I had an issue with a fresh install of Mythbuntu 9.04 as my server. My 2 front ends found the back end the first time > I saved back end details and everything seemed to work until I shut the front ends down and updated the back end server. 
After that the front ends complained they couldn't find upnp backed server. I found a similar problem referenced in [http://ubuntuforums.org/showthread.php?t=1061276]("http://ubuntuforums.org/showthread.php?t=1061276")
After i edited /etc/mythtv/mysql.txt 
Line #6 from #DBHostPing=no to #DBHostPing=yes
everything seems to work fine.
This file also gave me the random password to the mysql database
Line #9 DBPassword= 
which can be used if you do not want upnp enabled to manually set things up.

Maybe this will help someone else

---

