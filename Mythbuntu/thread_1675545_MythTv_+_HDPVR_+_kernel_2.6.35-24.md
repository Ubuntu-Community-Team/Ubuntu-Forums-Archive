---
title: "MythTv + HDPVR + kernel 2.6.35-24"
date: 2011-01-25
forum: Mythbuntu
---

### Post by drumz on 2011-01-25
Pardon me for posting this, but I'm hoping that this may help someone else with the same problem at some point....

After updating to the latest patches, my HDPVR stopped working - it was being properly detected ('tail -f /var/log/messages') but after a few seconds the amber light on the face of the HDPVR would turn on.  If I rebooted and used the previous kernel (2.6.35-22) it worked fine.

After reading several posts, I discovered that the firmware version on my HDPVR was slightly out of date - version 0x12 but others were posting there's had 0x15.

After rebooting a laptop into Windows, downloading the latest drivers from Hauppauge's website, plugging the HDPVR into my laptop and installing the latest drivers it automatically updated the firmware on my HDPVR.

Reconnected the HDPVR onto my Mythbuntu backend, rebooted to switch to the newer kernel and all is well.

lsusb shows my hardware as the '4901' version:

```
Bus 002 Device 005: ID 2040:4901 Hauppauge 
```

Grep'ing through /var/log/messages for 'hdpvr' now shows it has firmware 0x15:

```
Jan 25 17:04:35  kernel: [   56.040468] hdpvr 2-3:1.0: untested firmware version 0x15, the driver might not work
```

It's safe to ignore the 'the driver might not work part', I've seen that for several years now and it works fine.

---

