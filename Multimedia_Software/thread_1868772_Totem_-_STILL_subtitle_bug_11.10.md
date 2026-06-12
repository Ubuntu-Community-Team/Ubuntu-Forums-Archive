---
title: "Totem - STILL subtitle bug 11.10"
date: 2011-10-24
forum: Multimedia Software
---

### Post by cerda on 2011-10-24
So today updates to totem brought the version 3.0.1 back. Finally i can save a playlist again and the plugins seen to work fine except for the subtitle downloader. It's kinda working as i can search for a subtitle, it finds them fine but when you click to download here's the output

```
Traceback (most recent call last):
  File "/usr/lib/totem/plugins/opensubtitles/opensubtitles.py", line 570, in os_save_subtitles
    subFile  = fp.replace('', False)
  File "/usr/lib/python2.7/dist-packages/gi/types.py", line 43, in function
    return info.invoke(*args, **kwargs)
TypeError: replace() takes exactly 5 arguments (3 given)
```

And it hangs and no download gets done. Anyone with the same problem or who might know how to fix it ?? Thank you !!

---

### Post by cerda on 2011-10-25
Am I the only one out there using Totem :) ?? (bump)

---

### Post by psychok7 on 2011-10-30
> **cerda said:**
> Am I the only one out there using Totem :) ?? (bump)

got the same problem mate.. wish someone could help, by the way i upgraded to 11.10

---

### Post by mambro on 2011-11-06
[https://bugs.launchpad.net/ubuntu/+source/totem/+bug/886947](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/886947)

---

### Post by psychok7 on 2011-11-07
> **mambro said:**
> [https://bugs.launchpad.net/ubuntu/+source/totem/+bug/886947](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/886947)

the patch works

---

