---
title: "dwa-150 frustration"
date: 2010-06-30
forum: Networking &amp; Wireless
---

### Post by gwpritch on 2010-06-30
I have just install LL 10.04 on my desktop which also has as its only network link a d-link dwa-150 usb adapter which had been driving me crazy trying to install.

I followed the instructions from chili555 here:
[http://ubuntuforums.org/showthread.php?p=8966294#post8966294](http://ubuntuforums.org/showthread.php?p=8966294#post8966294)

When I did the ```
sudo apt-get remove --purge ndiswrapper* 
```
it wanted to remove my kernel. So I skipped that and continued to creating the two files.

When I got to ```
sudo modprobe rt3070sta
```
I got the following:
```
FATAL: Module rt3070sta not found.
sh: cannot create /sys/bus/usb/drivers/rt2870/new_id:Directory nonexistent
FATAL: Error running install command for rt3070sta
```

Please help before I put this thing under the heel of my boot!

Thanks

---

### Post by David006 on 2010-08-06
I did solve this for 10.04 Lucid.

see:
[http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=9632897&postcount=15](http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=9632897&postcount=15)

---

