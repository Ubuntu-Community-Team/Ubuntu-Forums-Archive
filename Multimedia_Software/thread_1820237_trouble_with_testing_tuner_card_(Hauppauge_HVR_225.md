---
title: "trouble with testing tuner card (Hauppauge HVR 2250)"
date: 2011-08-07
forum: Multimedia Software
---

### Post by marlinbrandeaux on 2011-08-07
I'm trying to test my new tuner card (HVR-2250) on 11.04 as described in [http://parker1.co.uk/mythtv_dvb.php:](http://parker1.co.uk/mythtv_dvb.php:)

scarface@littlefriend:~$ scan /usr/share/dvb/dvb-t/uk-WinterHill | tee channels.conf
scanning /usr/share/dvb/dvb-t/uk-WinterHill
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:2284: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 2 No such file or directory

Indeed, dvb folder does not exist, and I'm not sure why.

I have:
-installed firmware as described at [http://www.steventoth.net/linux/hvr22xx/](http://www.steventoth.net/linux/hvr22xx/) readme file
-installed v4l-dvb as described at [http://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers](http://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers)

I can confirm that the tuner card works correctly on the same machine in MS Windows.

lspci returns
...
03:00.0 Multimedia controller: Philips Semiconductors SAA7164 (rev 81)

What's wrong here?  Why doesn't dvb folder exist?

---

### Post by marlinbrandeaux on 2011-08-07
Hmm

After poking around the 'net, I found:

$ wget [http://www.steventoth.net/linux/hvr22xx/firmwares/4019072/NXP7164-2010-03-10.1.fw](http://www.steventoth.net/linux/hvr22xx/firmwares/4019072/NXP7164-2010-03-10.1.fw)
$ cp NXP7164-2010-03-10.1.fw /lib/firmware
$ wget [http://www.steventoth.net/linux/hvr22xx/firmwares/4038864/v4l-saa7164-1.0.3-3.fw](http://www.steventoth.net/linux/hvr22xx/firmwares/4038864/v4l-saa7164-1.0.3-3.fw)
$ cp v4l-saa7164-1.0.3-3.fw /lib/firmware
$ rmmod saa7164
$ modprobe saa7164

which seems to have fixed the dvb problem...

---

### Post by marlinbrandeaux on 2011-08-07
The tuner is now working.  It's pretty choppy, but I think I can troubleshoot that.

---

