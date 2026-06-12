---
title: "MYTHWEB error message"
date: 2008-08-17
forum: Mythbuntu
---

### Post by Steenhad on 2008-08-17
I get the following message when trying to access MythVideo from within MythWeb:

Error
Could not create a symlink to /var/lib/mythtv/videos:/mnt/NAS/Film, the local MythVideo directory for this hostname (tvserver). Please create a symlink to your MythVideo directory at data/video in order to use the video portions of MythWeb.

I believe it's a small thing but not sure what to do...

Thanks
Steen

---

### Post by murbanci on 2008-08-17
> **Steenhad said:**
> I get the following message when trying to access MythVideo from within MythWeb:

Error
Could not create a symlink to /var/lib/mythtv/videos:/mnt/NAS/Film, the local MythVideo directory for this hostname (tvserver). Please create a symlink to your MythVideo directory at data/video in order to use the video portions of MythWeb.

I believe it's a small thing but not sure what to do...

Thanks
Steen

The symlinks in mythweb arent pointing to the right folder.  Go to /var/www/mythweb/data and then create a new symlink

```
ln -s video your-video-directory
```

check this post for some more info: [http://ubuntuforums.org/showthread.php?t=854721&highlight=mythweb+symlink](http://ubuntuforums.org/showthread.php?t=854721&highlight=mythweb+symlink)

---

### Post by Steenhad on 2008-08-18
Mark,

Thanks. The information on the attached link solved the problem.

Cheers,
Steen

---

### Post by gfowler on 2008-08-18
> **murbanci said:**
> The symlinks in mythweb arent pointing to the right folder.  Go to /var/www/mythweb/data and then create a new symlink

```
ln -s video your-video-directory
```

check this post for some more info: [http://ubuntuforums.org/showthread.php?t=854721&highlight=mythweb+symlink](http://ubuntuforums.org/showthread.php?t=854721&highlight=mythweb+symlink)

Just a nit, wouldn't the code be:

 ```
 ln -s your-video-directory video 
```

Jerry

---

