---
title: "crontab and wget with terminal"
date: 2010-09-13
forum: Networking &amp; Wireless
---

### Post by ras123 on 2010-09-13
Hi,
I used the crontab to start wget and download the file with the following
> 
14 02 * * * wget -c --directory-prefix=/home/Downloads/wget --input-filefile=/home/Downloads/wget/download.txt

But it doesn't shows a terminal and so not able to get the current status and stop wget. So how can I start wget with a terminal using crontab?

---

### Post by goldenbarb on 2010-09-13
Enable logging and you'll get status.

```
wget ... 1>> /home/user/log.log 2>>&1
```

---

