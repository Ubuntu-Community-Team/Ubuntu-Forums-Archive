---
title: "cannot tune dvb-t card in 9.10"
date: 2009-11-02
forum: Multimedia Software
---

### Post by Zanzibar on 2009-11-02
Don't know if anyone else has had this problem since installing Karmic. 

I was unable to tune dvb-t channels using either kaffeine or me-tv. With Me-Tv the card (Avermedia super 007) or (philips TDA10046H as registered in Me-TV) is recognised but when attempting to tune the error message "failed ot lock channel" would appear.

Looking at my system log showed> Nov  2 19:16:45 family-htpc kernel: [ 1505.620015] tda1004x: setting up plls for 48MHz sampling clock
Nov  2 19:16:47 family-htpc kernel: [ 1508.050026] tda1004x: timeout waiting for DSP ready
Nov  2 19:16:48 family-htpc kernel: [ 1508.150026] tda1004x: found firmware revision 0 -- invalid
Nov  2 19:16:48 family-htpc kernel: [ 1508.150033] tda1004x: trying to boot from eeprom
Nov  2 19:16:50 family-htpc kernel: [ 1510.520032] tda1004x: timeout waiting for DSP ready
Nov  2 19:16:50 family-htpc kernel: [ 1510.620028] tda1004x: found firmware revision 0 -- invalid
Nov  2 19:16:50 family-htpc kernel: [ 1510.620033] tda1004x: waiting for firmware upload...
Nov  2 19:16:50 family-htpc kernel: [ 1510.620043] saa7134 0000:03:07.0: firmware: requesting dvb-fe-tda10046.fw
and in user.log
> Nov  2 18:48:50 family-htpc firmware.sh[5028]: Cannot find  firmware file 'dvb-fe-tda10046.fw'
Nov  2 18:48:50 family-htpc firmware.sh[5034]: Cannot find  firmware file 'dvb-fe-tda10045.fw'
Nov  2 18:52:01 family-htpc firmware.sh[1377]: Cannot find  firmware file 'dvb-fe-tda10046.fw'
Nov  2 18:52:01 family-htpc firmware.sh[1383]: Cannot find  firmware file 'dvb-fe-tda10045.fw'

Looking in /lib/firmware the dvb-fe-tda10046.fw was missing.

By installing the linux-firmware-nonfree package, the missing firmware was installed. New users should write the following code in a terminal or search in synaptic packet manager found in System>Administration>Synaptic

```
sudo apt-get install linux-firmware-nonfree
```

The problem has been solved for me. Hope this helps others.

---

### Post by epek on 2009-11-02
Please mark it "solved",then ;-)

---

### Post by kem on 2009-11-09
Thank you Zanzibar! Installing the linux-firmware-nonfree package is better than my attempts to install firmware manually into /lib/firmware.

However, I am still getting "tda1004x: timeout waiting for DSP ready". I am solving it in this thread [http://ubuntuforums.org/showthread.php?p=8281808](http://ubuntuforums.org/showthread.php?p=8281808)

---

### Post by sbad on 2009-11-28
Thanks for the solution, I ran across your post while searching for issues in /var/log/messages after upgrading from Mythbuntu 9.04 to 9.10.  The messages file read "Cannot find firmware file... "...  about once per second since the upgrade... resulting in intermittent lockups at first, then choppy video, then remote (lirc) lockup, keyboard lockup, mouse freezing on the desktop.  The package install was just what the doctor ordered.  I'm only writing this up in case anyone else comes across this and wonders why their system is so unresponsive.  If you're having issues with your upgrade... check your logs!

---

