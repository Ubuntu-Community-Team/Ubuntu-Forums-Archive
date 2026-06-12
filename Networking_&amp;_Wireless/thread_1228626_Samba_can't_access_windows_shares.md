---
title: "Samba can't access windows shares"
date: 2009-08-01
forum: Networking &amp; Wireless
---

### Post by dstrang on 2009-08-01
Ubuntu 904 install. I installed samba and set up Ubuntu shared folder and changed the samba.conf workgroup to my workgroup_name. My windows box can see the Ubuntu box and the shares and can access them...great! Now I want to see the Windows box from Ubuntu. Using Nautilus, I select the network place
and it list my network name and I can select that and it list the Ubuntu box and the Windows box. When I
select the windows box, I get the message dialog...

Unable to mount location
Failed to retrieve share list from server

Where do I go from here? I installed swat and winbind. BTW, when I try to select the Ubuntu network shares, it does the same thing.

Thanks,
Dave

---

### Post by lisati on 2009-08-01
Have you enabled file sharing on the Windows machine?

---

### Post by swerdna on 2009-08-01
sorry -- reconsidered

---

### Post by Iowan on 2009-08-01
[Here]("http://ubuntuforums.org/showthread.php?t=1169149") is a How-To that might be useful.  Also, have you [edited]("http://ubuntuforums.org/showpost.php?p=7075850&postcount=4") */etc/nsswitch.conf*?

---

