---
title: "wiimote problem 2.6.28-13"
date: 2009-06-28
forum: Mythbuntu
---

### Post by jape42 on 2009-06-28
After accepting updates for my 9.04 64 bit mythbuntu I realized something was wrong with my wiimote/wminput.

It was spining out of control:

[ 1613.605296] input: Nintendo Wiimote as /devices/virtual/input/input15209
[ 1613.685316] input: Nintendo Wiimote as /devices/virtual/input/input15210
[ 1613.765358] input: Nintendo Wiimote as /devices/virtual/input/input15211
[ 1613.845520] input: Nintendo Wiimote as /devices/virtual/input/input15212
myth@vcr7:~$ cat /proc/version
Linux version 2.6.28-13-generic (buildd@yellow) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #44-Ubuntu SMP Tue Jun 2 07:55:09 UTC 2009


So I reverted back to 28.11 and things were back to normal:

root@vcr7:/usr/local/data/disk1/home-movies# cat /proc/version
Linux version 2.6.28-11-generic (buildd@crested) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009

hope this saves someone some grief.

regards,

jp

---

