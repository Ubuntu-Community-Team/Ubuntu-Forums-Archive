---
title: "How often does mythbuntu sync the time to the internet?"
date: 2009-11-21
forum: Mythbuntu
---

### Post by jodajen2 on 2009-11-21
Is there a way to have it sync more often?

---

### Post by ian dobson on 2009-11-22
Hi,

Have a look here [https://help.ubuntu.com/7.04/server/C/NTP.html](https://help.ubuntu.com/7.04/server/C/NTP.html)

Maybe rather than sticking the script in a daily cron job you can get it running every hour with crontab -e as user root:-

```
# m        h     dom  mon    dow     command
  30       *       *   *     *       Command to run
```

This will run the command at exactly 30 minutes passed the hour every hour.

Regards
Ian Dobson

---

### Post by movieman on 2009-11-22
NTP should be maintaining sync automatically. I presume it's installed by default because my system is running it.

---

