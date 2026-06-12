---
title: "trickle doesn't even work"
date: 2010-06-01
forum: Networking &amp; Wireless
---

### Post by fermulator on 2010-06-01
Does anyone have any problems with trickle?  This program used to work, but I have no data points to say when or on what version of Ubuntu.

_**My Goal:**_
 * Limit the download and upload rate of the "rdesktop" application.  I use rdesktop to work from home, but it likes to eat the upload pipe, and causes significant impact on other users of the Internet.

I tried to use it today as follows:
```
**trickle -s -d 10 -u 10 -t 0.01** rdesktop -u username -d domain -z -x -P -f -a 16 -g 100% -0 -T my_windows_pc
```

Any of the parameters after "rdesktop" are irrelevant to this question as they're particular to rdesktop.

Yet, even telling trickle to operate in standalone mode (-s), 10KB/s for both download and upload (-d 10 -u 10) and a smoothing time of 0.01 (tried 0.1 and 1 too..) ... the rates are still unaffected and rdesktop is allowed to eat any and all of the bandwidth it needs.

Anyone else had this problem?

My current setup:
 * Ubuntu Jaunty 9.04
 * $ uname -a
> Linux fermmy 2.6.28-18-server #60-Ubuntu SMP Fri Mar 12 05:41:54 UTC 2010 i686 GNU/Linux
 * trickle: version 1.07

---

### Post by xbyte1024 on 2010-06-23
I have the same problem.
ubuntu 9.04.
Any attempt to use trickle fails.
I am searching tc
[http://ubuntuforums.org/showthread.php?t=1353070](http://ubuntuforums.org/showthread.php?t=1353070)

but it is not that simble and flexible.
:(

---

### Post by Earnol on 2010-07-01
The same problem here. I use trickle in following context:
```

 sudo -u dcbot /usr/bin/screen -S microdc -d -m /usr/bin/nice -n 19 /usr/bin/trickle -s -u 5000 /usr/local/bin/microdc2 -c /home/data/storage/DCDownload/.microdc2/config

```The big idea is to limit microdc2 bandwidth to 5Mbyte per second. Unfortunately it idoes not work. MicroDC happily consume 11MB/s(100Mbit connection) with and without trickle. So trickle does not have any affect.

Relevant part from htop:

[IMG]http://gyazo.com/8ebdbec4660f38cbc88767a1f4a47eb6.png[/IMG]

May be there are any other application level traffic shaper?

---

