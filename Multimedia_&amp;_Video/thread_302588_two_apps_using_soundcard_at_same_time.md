---
title: "two apps using soundcard at same time"
date: 2006-11-18
forum: Multimedia &amp; Video
---

### Post by partriv on 2006-11-18
I have looked at the comprehensive sound problems guide, and it states that to get alsa to to be able to play sound through 2 apps (xmms and firefox, for me) at the same time, i must install alsa-oss

this is what i get

```
par@parnix:~$ sudo apt-get install alsa-oss
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package alsa-oss is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package alsa-oss has no installation candidate
par@parnix:~$ 
```

can someone please point me in the right direction as to why this is happening?  thanks!

---

### Post by 3rdalbum on 2006-11-19
Check that you've got all the repositories enabled, and then do a sudo apt-get update.

---

### Post by partriv on 2006-11-19
Ok, i uncommented some repositories and it worked!  i got alsa-oss installed, and it works, but ONLY WHEN i launch all my apps with aoss in front of it.

so if i want to play xmms and watch videos in firefox, i need to do
aoss xmms
aoss firefox 
(i just changed my launchers)

Is this right?  This seems kind of weird to have to do seperately for every app.  Is there no way to 'enable' this in general?

Thanks!

---

