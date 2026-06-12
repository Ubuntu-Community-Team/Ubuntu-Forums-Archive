---
title: "Detect machines on LAN &amp; adjust Deluge limits"
date: 2011-12-14
forum: Networking &amp; Wireless
---

### Post by lebrun on 2011-12-14
Since I share my internet connection with other people I started using Deluge's bandwidth scheduler plugin to avoid hogging the connections (and avoid conflicts)

I set Deluge max to 60KBps, and on the evening hours it goes down to 40KBps.

But during the day, even this seemed wasteful if no one was home. Increasing the max (or setting it to unlimited) would make the connection useless for anyone working from home (and yes, sometimes that includes me)

So I made a small script to be run via cron say, every 5 minutes. It uses smbtree to count the number of Windows machines on the network, excluding the current host. When no other machine is found, deluge is set for a higher max download limit, and when other machines are detected, it reverts deluge to more modest settings.

Here is the code, which is also hosted at: [https://github.com/acarroz/autobw](https://github.com/acarroz/autobw)


```
#!/bin/bash

logfile=$(echo "$0.log" | sed "s/.sh//g")

maxdownspeed="90.0"
maxupspeed="30.0"

regdownspeed="60.0"
regupspeed="15.0"

wincount=$(smbtree -S -N -b | grep '\\\\' | grep -v "`hostname`" | wc -l)
currdownspeed=$(deluge-console "config max_download_speed" | sed 's/ max_download_speed: //g')
now=$(date +"%F %T")

if [ $wincount -gt 0 ]; then
if [ $currdownspeed != $regdownspeed ]; then
deluge-console "config --set max_download_speed $regdownspeed"
    deluge-console "config --set max_upload_speed $regupspeed"

    echo "$now *REG* $wincount hosts found" >> $logfile
  fi
else
if [ $currdownspeed != $maxdownspeed ]; then
deluge-console "config --set max_download_speed $maxdownspeed"
    deluge-console "config --set max_upload_speed $maxupspeed"

    echo "$now *MAX* $wincount hosts found" >> $logfile
  fi
fi
```


The script will only detect Windows (or Samba) hosts, but for my particular situation, I can live with that.

---

### Post by Cas07 on 2012-01-10
You should post this on the Deluge [forum]("http://forum.deluge-torrent.org/").

---

