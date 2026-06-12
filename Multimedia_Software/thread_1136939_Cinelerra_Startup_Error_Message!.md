---
title: "Cinelerra Startup Error Message!"
date: 2009-04-25
forum: Multimedia Software
---

### Post by Rytron on 2009-04-25
Hi.
In Cinelerra, when I start it up I get this error message(attached picture). Sometime Cinelerra crashs also. Is there a fix? Thanks.

---

### Post by GammaRay256 on 2009-04-26
> **Rytron said:**
> Hi.
In Cinelerra, when I start it up I get this error message(attached picture). Sometime Cinelerra crashs also. Is there a fix? Thanks.

Try this:

```
sudo gedit /etc/sysctl.conf
```

At the end of the file, write:

```
kernel/shmmax=0x7fffffff
```

Run:

```
sudo sysctl -p
```

Try running Cinlerra, if it still doesn't work, try rebooting first.

Source: [http://ubuntuforums.org/showthread.php?t=501633](http://ubuntuforums.org/showthread.php?t=501633)

---

### Post by Rytron on 2009-04-26
> **GammaRay256 said:**
> Try this:

```
sudo gedit /etc/sysctl.conf
```

At the end of the file, write:

```
kernel/shmmax=0x7fffffff
```

Run:

```
sudo sysctl -p
```

Try running Cinlerra, if it still doesn't work, try rebooting first.

Source: [http://ubuntuforums.org/showthread.php?t=501633](http://ubuntuforums.org/showthread.php?t=501633)

Thank you GammaRay256, I will try that. :P

---

### Post by Rytron on 2009-04-26
> **GammaRay256 said:**
> Try this:

```
sudo gedit /etc/sysctl.conf
```

At the end of the file, write:

```
kernel/shmmax=0x7fffffff
```

Run:

```
sudo sysctl -p
```

Try running Cinlerra, if it still doesn't work, try rebooting first.

Source: [http://ubuntuforums.org/showthread.php?t=501633](http://ubuntuforums.org/showthread.php?t=501633)

Thanks GammaRay256. Your solution worked perfectly. :)

---

