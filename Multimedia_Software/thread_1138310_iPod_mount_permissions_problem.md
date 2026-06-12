---
title: "iPod mount permissions problem"
date: 2009-04-26
forum: Multimedia Software
---

### Post by WildeBeest on 2009-04-26
I have a jail broken iPod touch which works in Hardy with gtkpod(sort of, can't write to it) and amarok.

I'm trying to get them to work in Jaunty. I can mount the iPod, but can only see and access it when I run nautilus, gtkpod, and amarok with sudo.

Where and what permission setting do I have to change?

---

### Post by WildeBeest on 2009-04-27
Bump up.

---

### Post by WildeBeest on 2009-04-28
anyone?

---

### Post by EndersJ on 2010-02-11
Don't know if you've solved this problem as it has been a few months but I also recently experienced this problem and got it working after some searching.
 
I run Koala and gtkpod V0.99.14 with an ipod classic (5th ed). When I plugged my ipod in, it mounted and was recognized by gtkpod just fine. It was assigned the path **_/dev/sdf2_**. However, when I tried to drag and drop songs to it (in gtkpod) I got a message about permission being denied. After some searching I found a site that gave the following helpful code (with ipod plugged in):
 
```
sudo chown root:[user name] /dev/sdf2
sudo chmod 0777 /dev/sdf2
```
 
The 1st line gives permission of "/dev/sdf2" to [user name]. The 2nd line changes the permission of "/dev/sdf2" to allow read write and execute control to *owner, group, *and *public*. After performing this I could drop songs on the ipod in gtkpod without trouble. Hope this helps anyone else experiencing this problem.
 
ipod touch support is new according to the gtkpod site.

---

