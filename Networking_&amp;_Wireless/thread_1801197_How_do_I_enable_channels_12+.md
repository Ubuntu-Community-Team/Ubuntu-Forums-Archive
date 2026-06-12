---
title: "How do I enable channels 12+?"
date: 2011-07-10
forum: Networking &amp; Wireless
---

### Post by vlhuynh on 2011-07-10
Hello all,

I've been looking around on Google for the last hour and have not been able to find a solution to my problem.

I have a North American laptop and am presently in Seoul, South Korea. Many of the WIFI spots are using channel 13 which I do not have access to with the basic Ubuntu 11.04 set up. 

The closest fix I could find was this:
[http://www.linuxquestions.org/questions/ubuntu-63/solved-intel-wifi-not-working-after-ubuntu-8-10-upgrade-689834/](http://www.linuxquestions.org/questions/ubuntu-63/solved-intel-wifi-not-working-after-ubuntu-8-10-upgrade-689834/)

But it seems like that won't work for 11.04. Is there anyway I can enable the additional channels?

Thanks!

---

### Post by flash63 on 2011-07-11
Hello,
if your WiFi-Device works with mac80211-subsytem you must use **iw**

[http://www.linuxwireless.org/en/users/Drivers](http://www.linuxwireless.org/en/users/Drivers)
[http://www.linuxwireless.org/en/users/Documentation/iw](http://www.linuxwireless.org/en/users/Documentation/iw)



```
sudo apt-get install --reinstall iw
```
Test it:
```
iw reg get
```

Now ty to swich the country-code an unload/load the driver for your Wifi-Device (unknown). 

```

sudo service network-manager stop
sudo iw reg set EU    # for example
sudo modprobe -rf $module
sudo modprobe $module
iwlist chan
iw reg get
sudo service network-manager start

```
($module must be replaced with the actual module name)

---

