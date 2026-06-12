---
title: "Lost remote after upgrade from 8.10 to 9.4"
date: 2009-10-28
forum: Mythbuntu
---

### Post by kyfehr on 2009-10-28
I have a harmony remote that has been working for about a year and a half no problems. I upgraded from 7.10 through 8.10 without issues. I saved copies of the /etc/lirc/ files and the custom file I created for the remote based on a sony reciver remote. However, after I did the upgrade from 8.10 .21-fixes to 9.4 .22 I can not get the remote to work anymore. 

I placed the files back into their original places. and in the MCC I seleced the custom again - however, selecting custom didn't let me select the custom file to use - so I placed the include in the config file just like the backup file had it.

I also am unable to get irw to report anything back, but the reciever does show activity. 

Help would be very much appreciated because I am at an impass. If you need to see my files I can post them, just let me know.

Kyle

---

### Post by kyfehr on 2009-10-29
update: found the problem. Everytime I restart the computer the lircd.conf file defaults back to the unaltered one. I have to go in and add the include again and restart lirc

---

