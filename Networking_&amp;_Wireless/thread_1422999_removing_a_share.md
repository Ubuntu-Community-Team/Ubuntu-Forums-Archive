---
title: "removing a share"
date: 2010-03-06
forum: Networking &amp; Wireless
---

### Post by Irti on 2010-03-06
hi i was trying to create a share in ubuntu...went to smb.conf and joined a workgroup but the name i gave for it was wrong..i fixed it later on..but the name of the workgroup won't go from the network..How can i delete the workgroup from the network????

---

### Post by Irti on 2010-03-06
anyone????

---

### Post by Irti on 2010-03-06
cmon...there must be someone who knows how to do this!!!!!!!!!!!!!!!!

---

### Post by Morbius1 on 2010-03-06
By "joined a network" I'm guessing you mean you specified a workgroup name in smb.conf? If you went back and corrected the name did you restart samba?

**sudo service samba restart**

---

### Post by Irti on 2010-03-07
yes..exactly i joined a workgroup (i.e i specified a name in smb.conf) but it was wrong.....so i just went back and corrected it and i restarted samba. I am guessing that when i specified a name in that file it created a workgroup....and i restarted samba after correcting it but still no luck. the workgroup is still there...

---

### Post by Irti on 2010-03-09
ok restarting samba didnt work...but restarting linux did!!!

---

