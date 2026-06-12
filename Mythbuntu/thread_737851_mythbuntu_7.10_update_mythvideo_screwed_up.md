---
title: "mythbuntu 7.10 update mythvideo screwed up"
date: 2008-03-28
forum: Mythbuntu
---

### Post by dvb3eak on 2008-03-28
I have just applied "recomended" updates on my mythbuntu 7.10

now my myvideo does not work any more :-(

I see following in mythfrontend log file:
2008-03-27 21:20:31.746 Unable to initialize plugin 'mythvideo'.
2008-03-27 21:20:31.746 Unable to configure plugin 'mythvideo': not initialized
/usr/lib/mythtv/plugins/libmythvideo.so: undefined symbol: _ZN18ConfigurationGroup6byNameE7QString
2008-03-27 21:20:33.006 MythPlugin::init() dlerror: /usr/lib/mythtv/plugins/libmythvideo.so: undefined symbol: _ZN18ConfigurationGroup6byNameE7QString

Does anybody have such symptoms too ?
How to cure this ?

---

### Post by axelsvag on 2008-03-28
Have you tried any of the good advice about mythvideo here on the forum??

---

### Post by nasha on 2008-03-28
A simple forum search would have found you exactly what you need. There have been countless amounts of posts about this issue, if only people learnt to search....

Type:
```
sudo apt-get install mythvideo
```
In a terminal

---

### Post by sierramike on 2008-04-06
> **nasha said:**
> A simple forum search would have found you exactly what you need. There have been countless amounts of posts about this issue,** if only people learnt to search**....

Type:
```
sudo apt-get install mythvideo
```
In a terminal

If only you could be conprehensive, I've had the same problem and I've been googling for 2 days before I found this thread ...

Also, your solution isn't complete, as I had to do :
apt-get remove mythvideo
before, because it was installed, but wasn't working ...

---

