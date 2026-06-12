---
title: "cannot install realplayer under edge"
date: 2007-01-22
forum: Multimedia &amp; Video
---

### Post by cccc on 2007-01-22
hi

I cannot install realplayer under edgy:```

root@ubuntu:/home/ubuntu# apt-cache search realplay
kmplayer-konq-plugins - KMPlayer plugin for KHTML/Konqueror
root@ubuntu:/home/ubuntu# apt-cache search realplayer
kmplayer-konq-plugins - KMPlayer plugin for KHTML/Konqueror

```

and add to /etc/apt/sources.list the following line:```

# Canonical Commercial packages
deb http://archive.canonical.com/ubuntu edgy-commercial main
```
it doesn't help.

knows someone what's wrong ?

---

### Post by mandrakethepenguin on 2007-01-22
The version of Opera in the Canonical Commercial repos is incompatible/untested on Edgy and is only available on Dapper.  However, I have installed Realplayer via the Dapper repo and I can ensure that it runs flawlessly.

---

