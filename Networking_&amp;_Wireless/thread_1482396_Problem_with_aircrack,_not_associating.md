---
title: "Problem with aircrack, not associating"
date: 2010-05-13
forum: Networking &amp; Wireless
---

### Post by Diego Garcia Mendoza on 2010-05-13
Hi, I'm using ubuntu 10.04 and I'm trying to do some tests with aircrack. I've been doing this since Jaunty and worked fine.

But now when i unload and reload my module ath5k, something is starting a wlan interface in managed mode.

I stoped network-manager service but my problem persist... i can set my interface in monitor mode but can't associate to AP.

anyone knows what is my problem or how to stop that interface from being created automatically?

---

### Post by pytheas22 on 2010-05-13
You can't associate if the device is in monitor mode, can you?  What exactly are you trying to do?

For what it's worth, I have also had issues with aircrack on Ubuntu 10.04 where I can use airmon-ng to create a device in monitor mode and then start airodump successfully to sniff, but it doesn't actually pick up any packets at all.  I've found that killing network-manager and then rmmoding and reloading the ath5k driver solves the problem.

---

### Post by Diego Garcia Mendoza on 2010-05-13
That's exactly what i do.. but at load ath5k it creates that wlan0 interface in managed mode. It's ok, i create a monitor interface with airmon-ng.

But when i try to associate with aireplay -1 0... just never happens, that's my problem. On Jaunty and Karmic it just worked very nice.

---

### Post by pytheas22 on 2010-05-14
You could try recompiling your driver using an older version of the code from [http://linuxwireless.org/download/compat-wireless-2.6/](http://linuxwireless.org/download/compat-wireless-2.6/).  Maybe there have been changes introduced more recently to ath5k that cause the problems.

Also, I've found that association is not always necessary for many aircrack exercises, even though most of the tutorials say it is.  So depending on what you are doing, you could just skip that step and it may still work.

---

### Post by Diego Garcia Mendoza on 2010-05-18
Well, i updated my compat-wireless and now i can't set a channel...

It appears like a fixed channel problem... 

And if i go back to the previous driver just dont associate... it keeps
```
Sending Authentication Request (Open System) [ACK]
```

at backtrack linux it inject faster than ever... maybe i'll try to use that drivers... but i dunno if i have to patch them or what... i'll keep reading. Thanks for all your help!

---

### Post by Diego Garcia Mendoza on 2010-05-24
it's done... there's a new patch [http://patches.aircrack-ng.org/fix_ath5k_no_data_in_monitor_mode.patch](http://patches.aircrack-ng.org/fix_ath5k_no_data_in_monitor_mode.patch)

that works just fine with my ubuntu and a stable release compat-wireless-2.6.32.11

Thanks a lot!

---

