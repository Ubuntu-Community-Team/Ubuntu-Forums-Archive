---
title: "can't open most websites except google,baidu"
date: 2009-10-15
forum: Networking &amp; Wireless
---

### Post by qywolala on 2009-10-15
hi there , i'm in china !
in xp,i connect to internet using broadband connection, so in ubuntu 9.04,sudo pppoeconf,

BUT i just can open google.cn,google.com,baidu.com .......
except bing.com ,yahoo.com,microsot.com, this forum and so on..........

i can ping  [www.bing.com,microsoft.com](www.bing.com,microsoft.com) ,and i'm the ip is correct , in other words , dns is not the problem ....

it's the same with  dnsmasq or without .....

i tried disabled ipv6,doesn't help !

any help appreciated !

thanks !

hardware config: thinkpad r60e
os: ubuntu jaunty 9.04
using pppoeconf

---

### Post by prshah on 2009-10-15
> **qywolala said:**
> 
BUT i just can open google.cn,google.com,baidu.com .......
except bing.com ,yahoo.com,microsot.com, this forum and so on..........


See [ Firefox/Epiphany/Lynx not loading certain websites]("http://ubuntuforums.org/showpost.php?p=4514356&postcount=12") for a possible solution.

Summary hint: Change the MTU (to 1492, or so)

---

### Post by qywolala on 2009-10-17
> **prshah said:**
> See [ Firefox/Epiphany/Lynx not loading certain websites]("http://ubuntuforums.org/showpost.php?p=4514356&postcount=12") for a possible solution.

Summary hint: Change the MTU (to 1492, or so)

thanks for reminding me!:):):):):):)

then i googled "MTU" ,then i change MTU of ppp0, and reboot .

haha, it works !

THANKS A LOT !

---

