---
title: "Permission settings for /usr/share/mythtv"
date: 2012-01-06
forum: Mythbuntu
---

### Post by ubnewbie2 on 2012-01-06
I was having trouble downloading themes in theme chooser and found a suggested solution in a post on the web.  This was to do the following...

```
sudo chgrp -R mythtv /usr/share/mythtv
sudo chown -R mythtv /usr/share/mythtv
```

This however breaks mythweb, so I temporarily

```
sudo chmod -R 777 /usr/share/mythtv
```

Now I am wondering what is the best owner/group/permissions settings to use?

---

### Post by superm1 on 2012-01-10
Shouldn't the theme chooser be downloading themes into ~/.mythtv though?

---

### Post by ubnewbie2 on 2012-01-10
Maybe it does, but there is a second thing, after the download where it says it's transferring or copying it somewhere (don't remember the actual words).

I really don't know much about it, I just followed some instructions I found.

---

### Post by bergqvistjl on 2012-01-15
> **superm1 said:**
> Shouldn't the theme chooser be downloading themes into ~/.mythtv though?

the .mythtv directory is complicated because it appears Mythtv itself gets confused as to whether to use the /home/myuser/.mythtv directory, and the /home/mythtv/.mythtv directory. Some functions use the one for the mythtv user, yet others use the one for the current logged in user. It's stupid. I might try symlinking the two actually.

---

### Post by superm1 on 2012-01-15
Oh does the theme downloader do the downloading from the backend?  I could see that for sure complicating things then and permissions need to be fixed up somehow.

---

### Post by bergqvistjl on 2012-01-15
> **superm1 said:**
> Oh does the theme downloader do the downloading from the backend?  I could see that for sure complicating things then and permissions need to be fixed up somehow.

I'm not sure, although it downloads the .zip file to the /home/mythtv/.mythtv directory at first, which might cause problems if i'm running mythfrontend as my own user.

---

