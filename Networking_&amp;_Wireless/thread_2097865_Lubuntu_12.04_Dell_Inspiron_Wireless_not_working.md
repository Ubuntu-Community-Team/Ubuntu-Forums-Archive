---
title: "Lubuntu 12.04 Dell Inspiron Wireless not working"
date: 2012-12-24
forum: Networking &amp; Wireless
---

### Post by shan2812 on 2012-12-24
Hi,

First time user of Lubuntu, trying to get it working my old Dell Inspiron 6000. Started with Ubuntu 12.04 which worked fine but too slow with my hardware, hence switched to Lubuntu 12.04 as advised on another thread of mine.

Now the speed looks quite good. Unfortunately I am unable to get the wireless working :-(

Any inputs would be of great help.

Merry Christmas

Cheers

---

### Post by NikTh on 2012-12-24
Hi , 
what is the problem exactly ? 

Please give the results of the commands below
```
lspci -nnk | grep -iA2 net
lsmod
rfkill list all
iwconfig
nmcli nm status
```_Please click on **"New Reply"** and put the results inside [CODE] tags to be easier to read._ [See here how]("http://i.stack.imgur.com/zADbK.png")

Thanks

---

### Post by Pjotr123 on 2012-12-24
You might try this roadmap:
[https://sites.google.com/site/easylinuxtipsproject/internet](https://sites.google.com/site/easylinuxtipsproject/internet)

---

### Post by shan2812 on 2012-12-25
iwconfig gave me the hint, and the roadmap solved it. 

The problem was wireless light was never on with Ubuntu/Lubuntu, 
So i gig not realize that.

Thanks a lot.

Cheers

---

### Post by NikTh on 2012-12-25
Hi ,
glad you solved it. 
Please mark the thread as [SOLVED] , see at my signature how. 

Thanks

---

