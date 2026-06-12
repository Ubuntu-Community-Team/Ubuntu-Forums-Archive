---
title: "[SOLVED] get the most of out your ipbloker"
date: 2008-10-07
forum: Multimedia Software
---

### Post by stinger30au on 2008-10-07
if our looking for a peer guardian type program for ubuntu use ipblock it uses java and runs well with a few tweaks


if you go here

[http://sourceforge.net/projects/iplist](http://sourceforge.net/projects/iplist)

click the download button and then find the version needed for your current ubuntu install and save it to your ramdrive or hdd

then double click the file you just d/l and a package manager will install it and if needed d/l any extras


once installed  i suggest you add a few extra ip black lists as the update function is not perfect and keeps missing stuff from the web site bluetack cos u need to be registered to get their files

but you can still get the files for free but from this web site instead

[http://iblocklist.com/lists.php](http://iblocklist.com/lists.php)

select lvel 1 2 or 3 or all 3 if you wish

save the .gz file and open up ipblock and click on lists add file and point it to the file you just d/l

simple!

---

### Post by Spitphire on 2008-10-19
I was thinking of writing a small script and adding to crontab - to insure they are always up-to-date.  Here's what i got so far..

```

#!/bin/bash

wget -O /home/am/.scripts/.iplists/bt_level1.gz http://list.iblocklist.com/?list=bt_level1
wget -O /home/am/.scripts/.iplists/bt_level2.gz http://list.iblocklist.com/?list=bt_level2
wget -O /home/am/.scripts/.iplists/bt_level3.gz http://list.iblocklist.com/?list=bt_level3


```

Question:

Is there a command to invoke to have ipblock update itself with the new files?  The location of the files would always be the same, ipblock just needs to 'refresh' it's blocking lists.  any idea how to do this?

Thanks,
Spit

---

### Post by uljanow on 2008-10-19
IPblock comes with a cron script **/etc/cron.daily/ipblock**. If you want to add another list, try the Import button. The filename must be the file that the URL returns. The file will be auto-updated.

To restart ipblock: "sudo ipblock -r" .

---

### Post by Spitphire on 2008-10-19
Cool, thanks.  I decided to stick with moblock; i like the way it runs and i don't need the gui.

---

