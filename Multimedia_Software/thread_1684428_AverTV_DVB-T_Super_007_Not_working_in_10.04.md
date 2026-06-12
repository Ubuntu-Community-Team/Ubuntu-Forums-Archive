---
title: "AverTV DVB-T Super 007 Not working in 10.04"
date: 2011-02-09
forum: Multimedia Software
---

### Post by mric5180 on 2011-02-09
Hi, 

I have a MythTV box at home with an AverMedia AverTV DVB-T Super 007 tuner card in it. 

I was running Ubuntu 8.10 and it worked perfectly with no dramas. 

I then upgraded to Ubuntu 10.04 and the Tuner card does not work at all. 

I have tried running the cmd below but that didn't work:

```
sudo apt-get install linux-firmware-nonfree
```

Then i tried building the latest v4l-dvb drivers and that didn't work. 

So i'm wondering if anyone else has come across the same problem and what their fix was.

I've been googling for a day now and still nothing. So any help is much appreciated. 

Thanks

Matt

---

### Post by Blues- on 2011-02-09
This should get you going ...
[http://www.linuxtv.org/wiki/index.php/AVerMedia_AVerTV_DVB-T_Super_007](http://www.linuxtv.org/wiki/index.php/AVerMedia_AVerTV_DVB-T_Super_007)

---

### Post by mric5180 on 2011-02-09
Thanks for the reply but i gave up on my googling too soon. 

Turns out this is the fix (taken from [https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/486264):](https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/486264):)

> Workaround indicated in [https://bugs.launchpad.net/mythbuntu/+bug/556204](https://bugs.launchpad.net/mythbuntu/+bug/556204) resolved my issue. Modify /etc/init/mythtv-backend.conf as follows:

Replace line

start on (local-filesystems and net-device-up IFACE=lo)

with

start on (local-filesystems and net-device-up IFACE=lo and started udev-finish)

My mythtv is working now for several restarts. The only drawback is the boot is a bit longer.


Hopefully this helps anyone else with the same issue

Also i had this card working perfectly on Ubuntu 8.10. Now even after applying the fix above the card will not pick up channel 9, 90, and 99 (in Australia). Then after a while the card stopped working altogether. Not sure what happened to the driver between 8.10 and 10.04 but obviously something changed. No idea what the solution is. So i'm just going to get another card.

---

