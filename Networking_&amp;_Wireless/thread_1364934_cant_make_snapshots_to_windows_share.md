---
title: "cant make snapshots to windows share"
date: 2009-12-26
forum: Networking &amp; Wireless
---

### Post by yairsuari on 2009-12-26
i am trying to backup my ubuntu machine to a windows share mounted through fstab using rsnapshot.
but i have some permission problem i cant figure out.
i am able to touch files on the windows share as shawn on the following lines:

[B]yair@yair-laptop:~$ sudo touch /mnt/backup/hourly.5
[sudo] password for yair: 
[/B]

i am even able to remove folders in there:

[B]yair@yair-laptop:~$ sudo rm  -r /mnt/backup/hourly.5
[/B]

but when i am trying to run rsnapshot i am getting an error massage:

[B]yair@yair-laptop:~$ sudo rsnapshot hourly
echo 4883 > /var/run/rsnapshot.pid 
/bin/rm -rf /mnt/backup/hourly.5/ 
/bin/rm: cannot remove directory `/mnt/backup/hourly.5/localhost/home/yair/Documents/&#1513;&#1500;&#1504;&#1493;/My Music': Permission denied
/bin/rm: cannot remove directory `/mnt/backup/hourly.5/localhost/home/yair/Documents/&#1513;&#1500;&#1504;&#1493;/My Pictures': Permission denied
[/B]

it looks to me like a windows permission isue so i am running the following windows bat file each time i start the windows machine:

cacls E:\backup /e /g everyone:F
cacls C:\MyDocuments /e /g everyone:F

with no luck

has anyone got an idea?

---

### Post by impact on 2009-12-26
Looks to me that this "&#1513;&#1500;&#1504;&#1493;" might be the problem. 

Try renaming the folder or removing those characters and then run it again and see if it works.

---

