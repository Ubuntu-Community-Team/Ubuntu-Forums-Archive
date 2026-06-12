---
title: "tmpfs and Chromium with Youtube"
date: 2013-12-01
forum: Multimedia Software
---

### Post by istvan3 on 2013-12-01
Hi all!


Maybe you can help me? 

I started Chromium with 
```
chromium-browser %U --disk-cache-dir="/tmpfs"
```
and watch a 2 h long Youtube video

In fstab I have 

```
tmpfs    /dev/shm    tmpfs    defaults,nodev,nosuid,noexec    0    0
```

In Task Manager had a increase of used memory of about 300 MB (so looks normal),
--> but I cannot see this tmpfs  dev/shm with "df"

how can I also see the this tmpfs dev/shm" ?
or is it the /run/shm here? 
But it's very low, 5 MB for Youtube video?

```

iamuser@Shuttle:/$ df --block-size=M | grep tmpfs
tmpfs               277M    2M      276M   1% /run
tmpfs              1385M    5M     1380M   1% /run/shm


```


thxx

---

