---
title: "lftp problem when run from cron"
date: 2010-01-10
forum: Networking &amp; Wireless
---

### Post by vies on 2010-01-10
Hi,

I'm using lftp to sync some folders between my server and ofsite ftp server.

Everything works just fine when I manually execute lftp command, but when I try to run it as cron job, it generates tar.gz file on my home folder and eventually fills up the whole hard drive. Files also get synced online though. 

I'm buzzled, since running it manually works just fine. Below is commands I use.

crontab
```
0  2    * * *   vies    /usr/local/bin/online_backup >>/home/vies/backup_log

```

online_backup
```
echo "---------------Starting Online Backup----------------------"
date
echo "-----------------------------------------------------------"
echo ""
lftp -f /home/vies/lftp_script
echo ""
echo "--------------Online Backup Finished-----------------------"
date
echo "-----------------------------------------------------------"

```

lftp_script
```
open Vies.onlinestoragesolution.net
user Vies "*******"
mirror -R -e --parallel=10 --verbose=1 /myth/pictures /sync/pictures
exit

```

Any ideas what might be wrong here? For now I'm syncing manually, but I would like to make it automatic.

---

