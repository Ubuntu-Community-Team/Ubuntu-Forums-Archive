---
title: "Which config.xml file is used?"
date: 2012-11-10
forum: Mythbuntu
---

### Post by brianafischer on 2012-11-10
I am in the process of upgrading from 9.04 (0.25) to 12.10 (0.26) right now and have encountered the dreaded "ERROR 1046 (3D000) at line 22: No database selected".

I have read a lot of posts that the config.xml is the cause for this.  A search of my system for this returns:

```
/etc/mythtv/config.xml
~/.mythtv/config.xml
/home/mythtv/.mythtv/config.xml
/usr/share/mythtv/config.xml
/var/www/.mythtv/config.xml
```

Which one of these 5 files is actually used/what is the priority?  Can I remove any of these to simplify my setup?

---

### Post by nickrout on 2012-11-10
> **brianafischer said:**
> I am in the process of upgrading from 9.04 (0.25) to 12.10 (0.26) right now and have encountered the dreaded "ERROR 1046 (3D000) at line 22: No database selected".

I have read a lot of posts that the config.xml is the cause for this.  A search of my system for this returns:

```
/etc/mythtv/config.xml
~/.mythtv/config.xml
/home/mythtv/.mythtv/config.xml
/usr/share/mythtv/config.xml
/var/www/.mythtv/config.xml
```

Which one of these 5 files is actually used/what is the priority?  Can I remove any of these to simplify my setup?I think the one in your home directory followed by /etc.

To solve this get one that works and put it in /etc/mythtv. Then make all the others symlinks to /etc/mythtv/config.xml.

By the way, are you sure you want 12.10? 12.04 is LTS.

---

### Post by brianafischer on 2012-11-10
> **nickrout said:**
> I think the one in your home directory followed by /etc.

To solve this get one that works and put it in /etc/mythtv. Then make all the others symlinks to /etc/mythtv/config.xml.

Thanks for the prompt response!  I will follow your advice.


> By the way, are you sure you want 12.10? 12.04 is LTS.
Actually, I would prefer 12.04, but I accidentally upgraded to 12.10.  I don't know of any way to go back...

---

### Post by nickrout on 2012-11-10
> **brianafischer said:**
> Thanks for the prompt response!  I will follow your advice.



Actually, I would prefer 12.04, but I accidentally upgraded to 12.10.  I don't know of any way to go back...
Possibly only by starting from scratch, which is what I would tend to do anyway.

---

