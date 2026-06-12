---
title: "AirRaid , Cannot locate ifconfig iwconfig and macchanger"
date: 2010-01-04
forum: Networking &amp; Wireless
---

### Post by FlapBags on 2010-01-04
Ok fellas Im trying to run air raid
 
And I need to know the location of threee things to get this running
 
FOUND - ifconfig
FOUND - iwconfig
NOT FOUND macchanger (perl file is calling for it inside /usr/local/bin/macchanger but it does not exist there)
 
Perl file was written for backtrack 2,  so I need to correct these directories.
 
 
I have no idea what the default directories are for these three tools and locate does not locate them.

---

### Post by chili555 on 2010-01-04
> locate does not locate them.Did you do:```
sudo updatedb
```and wait for the database to be rebuilt before you did 'locate'?

---

