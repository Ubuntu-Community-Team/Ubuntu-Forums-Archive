---
title: "Can’t use TV tuner (nano 520e USB stick) with Kaffeine"
date: 2017-05-27
forum: Multimedia Software
---

### Post by py-ohayo on 2017-05-27
Hello,

First I've tried a simplest way: downloaded driver from here:
[http://www.hauppauge.de/pctv-faq/doku.php?id=en:linux:linux-pctv](http://www.hauppauge.de/pctv-faq/doku.php?id=en:linux:linux-pctv)
and then put it in /lib/firmware/ location.
After running lsusb, I see that my USB stick is recognized: the 1st line being like this:
Bus 002 Device 004: ID 2013:0251 PCTV Systems
Unfortunately, when I run Kaffeine, the device seems to be not recognized: in Configure Television/Device_1/Name there is following name - "DRXK DVB-C DVB-T", but not "PCTV Systems" as in lsubs output.
And in the field of TV standard there is DVB-C, but not DVB-T as it supposed to be.
Well, suspecting that driver that I picked from hauppauge.de is probably obsolete, I've tried another approach - download driver sources and build them, found here:
[https://help.ubuntu.com/community/DVB-T_(USB)](https://help.ubuntu.com/community/DVB-T_(USB))
Unfortunately it failed at the stage of $ ./build: build was aborted with errors (e.g. "recipe for target 'apply_patches' failed").
Any ideas ?
Thanks in advance.
Pavel.

---

### Post by deadflowr on 2017-05-27
> Unfortunately, when I run Kaffeine, the device seems to be not recognized: in Configure Television/Device_1/Name there is following name - "DRXK DVB-C DVB-T", but not "PCTV Systems" as in lsubs output.
"DRXX DVB-C DVB-T" is the proper frontend name for the device. So that output you see is correct.

Not clear, but did you try running a scan anyway? 
Even if it does only list dvb-c.

---

### Post by py-ohayo on 2017-05-28
According to the manual, found here
[https://ubuntu-mate.community/t/how-to-watch-digital-tv-with-kaffeine-or-me-tv-in-ubuntu/906](https://ubuntu-mate.community/t/how-to-watch-digital-tv-with-kaffeine-or-me-tv-in-ubuntu/906)
on the Pic.5, before running search channel, one must set "Autoscan" as a source.
But I didn't find this option in the "Source" drop-down list..
There are only names of "country providers" (if I properly understood notations).
Also in Standard Field (field just below "Reset" button, isn't named on Kaffeine interface), only standard DVB-C is shown.
Thanks.

---

