---
title: "Cron Job to restart Wireless Adaptor"
date: 2009-03-20
forum: Networking &amp; Wireless
---

### Post by King DeaN on 2009-03-20
Hey Guise,

My wireless is EXTREMELY flakey so I've got a cron job setup to simply check if the wireless is working and if not then it will reset the adaptor and bring it back but it doesn't even work, ie if I take the adaptor down the cron job doesn't bring it back up (but if I run just run the script as root it works fine)

My wireless script looks something like this
```
#!/bin/bash

if ! `ping -c 1 -w 1 -q 138.77.122.1 </dev/null &>/dev/null` ; then
        echo resetting wireless
        ifdown ath0
        ifup ath0
        ip route add default via ath0 table WIFI
else
        echo wireless operational
fi
exit 0

```

My Crontab for root looks like this
```
7 9 * * * /etc/webmin/cron/tempdelete.pl
*/5 * * * * wirelesstest
*/5 * * * * touch /home/lollol.txt
*/5 * * * * ifup ath0

```

ifup ath0 is there because I was testing if my script was failing SOMEHOW (it works perfectly if I just run it as root)

My Cron log look like this:
```
Mar 20 16:11:57 melchior cron[1185]: (CRON) INFO (pidfile fd = 3)
Mar 20 16:11:57 melchior cron[1185]: (CRON) INFO (Skipping @reboot jobs -- not system startup)
Mar 20 16:15:01 melchior CRON[1261]: (root) CMD (ifup ath0)
Mar 20 16:15:01 melchior CRON[1264]: (root) CMD (touch /home/lollol.txt)
Mar 20 16:15:01 melchior CRON[1262]: (root) END (touch /home/lollol.txt)
Mar 20 16:15:01 melchior CRON[1267]: (root) CMD (wirelesstest)
Mar 20 16:17:01 melchior CRON[1321]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar 20 16:17:01 melchior CRON[1320]: (root) END (   cd / && run-parts --report /etc/cron.hourly)
Mar 20 16:20:01 melchior CRON[1397]: (root) CMD (ifup ath0)
Mar 20 16:20:01 melchior CRON[1399]: (root) CMD (touch /home/lollol.txt)
Mar 20 16:20:01 melchior CRON[1398]: (root) END (touch /home/lollol.txt)
Mar 20 16:20:01 melchior CRON[1403]: (root) CMD (wirelesstest)
```
And is just continues on and wirelesstest and ifup ath0 never "END" (I am unsure of what that implies)

Thank you for any assistance on getting this working

**Also I'm running rtorrent on this box as well, it never seems to so anything after the wireless has dropped is the best way to resume any torrents just to  add "/etc/init.d/rtorrent restart" into my wirelesstest script?

---

### Post by King DeaN on 2009-03-20
I added my script to /etc/crontab instead and it seems to work fine

---

