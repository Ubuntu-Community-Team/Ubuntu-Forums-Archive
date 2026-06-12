---
title: "No sound on Ubuntu ( I messed it up)"
date: 2009-08-16
forum: Multimedia Software
---

### Post by withoutn on 2009-08-16
Hello, 
For a while ive been struggling with a rather old issue of 'having to use external speakers on ubuntu laptops'. 

I was trying to fix it yesterday by going through various solutions at
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/269027](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/269027)

i eventually installed alsa-driver-linuxant_1.0.18.0_all.deb and now my ubuntu sound doesn't work. 

When the computer boots, i get the following message (everytime the pc boots, it lasts about a minute): 

```
Building modules for the 2.6.28-14-generic kernel, please wait... done.
ERROR: Build failed. Please review the build log at /var/run/alsa-driver.11076.log.
Original kernel modules will be used.
```

and alsa doesn't get started. 

When i try to start it manually i get this very same error. 


Here is my log file: [http://pastebin.com/m6ead7715](http://pastebin.com/m6ead7715)

Perhaps i need to reinstall alsa. Please help on alsa issue and how to remove the building modules thing at the start up. Thank you

---

