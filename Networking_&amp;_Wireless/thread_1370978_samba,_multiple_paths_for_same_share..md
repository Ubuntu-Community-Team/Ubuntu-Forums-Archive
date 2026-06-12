---
title: "samba, multiple paths for same share."
date: 2010-01-02
forum: Networking &amp; Wireless
---

### Post by bender1234 on 2010-01-02
Hey is there a way to make samba shares use multiple directories?

```
[series]
        comment = Serier
        path = /mnt/drive_d/movies/series
        writeable = no
        printable = no
        browsable = yes
        guest ok = yes

[series2]
        comment = Serier
        path = /mnt/drive_e/movies/series
        writeable = no
        printable = no
        browsable = yes
        guest ok = yes

```

Is there any way to merge these two shares two one share?

Also in the linux filesystem is it possible to "mount" several directories, so they appear to be in one dir? That is without having to make symbolic links to each element in the dir?

regards,
Bender

---

### Post by dmizer on 2010-01-02
> **bender1234 said:**
> Hey is there a way to make samba shares use multiple directories?

```
[series]
        comment = Serier
        path = /mnt/drive_d/movies/series
        writeable = no
        printable = no
        browsable = yes
        guest ok = yes

[series2]
        comment = Serier
        path = [COLOR="Red"]/mnt/drive_e/movies/series2[/COLOR]
        writeable = no
        printable = no
        browsable = yes
        guest ok = yes

```

Is there any way to merge these two shares two one share?

Also in the linux filesystem is it possible to "mount" several directories, so they appear to be in one dir? That is without having to make symbolic links to each element in the dir?

regards,
Bender

No. But if you organize your server's file system, you can get the same results.

On /mnt/drive_d/movies/ create a directory called "series" and add a directory for each series below that so you get something like this:

/mnt/drive_d/movies/series/series-name1/series1.avi
/mnt/drive_d/movies/series/series-name2/series2.avi
/mnt/drive_d/movies/series/series-name3/series3.avi

Then remove the second share definition and that's it. All you'll see on the remote systems is a share named "series" with a bunch of series listed inside.

---

