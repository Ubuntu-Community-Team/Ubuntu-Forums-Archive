---
title: "Help! Latest update as broken my wireless (again)"
date: 2009-01-17
forum: Networking &amp; Wireless
---

### Post by simple.0 on 2009-01-17
I complete the updates about once a week so this is very recent.  A very recent update has broken my wireless (broadcom BCM4318 ).  Symptom is wireless light is on but no wireless networks are detected.

Checked:

Roaming is set in network tools.
ifconfig shows wlan0, wmaster0 but no packets sent or received
Attempt manual config has no effect
modprobe -l | grep bcm shows:

/lib/modules/2.6.24-23-generic/kernel/drivers/bluetooth/bcm203x.ko
/lib/modules/2.6.24-23-generic/kernel/drivers/net/wireless/bcm43xx/bcm43xx.ko
/lib/modules/2.6.24-23-generic/kernel/drivers/media/dvb/frontends/bcm3510.ko

Restricted hardware drivers shows BC43 driver enabled and in use

I struggled through the days of fiesty and gutsy and ndiswrapper and bfwcutter and was appreciative and thrilled when hardy did this automatically (although I had to circle round and install hardy from scratch as updating to hardy did not get the wireless working.)

This has happened on two previous updates to Hardy and I can usually mess around and get it working.  But this time I'm stumped.

Can anybody help?

Thanks
Simon

P.S. uname -r gives 2.6.24-23-generic

---

### Post by simple.0 on 2009-01-18
Hmmm fixed.  It seems that wpa_supplicant was not running.  I went into /etc/wpa_supplicant and ran ./ifupdown.sh and it all started working.

Curious thing is, it continued working over a reboot.

---

