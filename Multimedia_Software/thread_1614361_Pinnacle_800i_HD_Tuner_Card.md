---
title: "Pinnacle 800i HD Tuner Card"
date: 2010-11-05
forum: Multimedia Software
---

### Post by sdavy13 on 2010-11-05
Ladies and Gentlemen;

I am having trouble getting my new computer to recognize the aforementioned TV tuner card.  I'm using the newest version of Ubuntu - 10.10 - and installed it on this computer earlier this week.

I'm following the directions on the LinuxTV Wiki

[http://www.linuxtv.org/wiki/index.php/Pinnacle_PCTV_HD_Card_%28800i%29#Making_it_Work](http://www.linuxtv.org/wiki/index.php/Pinnacle_PCTV_HD_Card_%28800i%29#Making_it_Work)

but come up with this error...
> cp: cannot create regular file `/lib/firmware/dvb-fe-xc5000-1.1.fw': Permission denied
while trying to install the firmware.  I seem to be stuck at this point.  

I should warn y'all, this is my first computer NOT running some version of Windows.  I'm liking Ubuntu so far - it seems to be running better on this computer than Windows ever did, is doing nearly everything I ask it to (this week, at least).  I'm learning my way around this thing, but I'm still low down on the learning curve.

---

### Post by efflandt on 2010-11-05
Assuming you found the extract.sh script somewhere to extract the firmware, it looks like you are having trouble copying it to /lib/firmware which has do be done as root.  So you need to precede the cp command with sudo.  cd to your directory containing the firmware and then try:

**sudo cp dvb-fe-xc5000-1.1.fw /lib/firmware**

I have a different older Pinnacle USB digital tuner (800e I think), and so far I have not been able to get it to work other than successfully scanning for local digital channels with w-scan.  I have not tried it in 10.10 yet, but in 10.04 I could not get any of the tests with dvb-apps to work.

---

