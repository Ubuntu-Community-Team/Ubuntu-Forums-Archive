---
title: "Question about LIRC + HVR-2250"
date: 2012-11-25
forum: Mythbuntu
---

### Post by lucgallant on 2012-11-25
Hi everyone,

I'm running Mythbuntu 12.04, kernel version 3.2.0-32, and I am trying to get the IRBlaster working on my Hauppauge HVR-2250. I installed LIRC from the Mythbuntu Software Center and I deduced that I need to load the lirc_zilog module.... I followed the instructions located here: 

[http://jaysdesktop.blogspot.ca/2012/06/configuring-lirc-for-hvr-1600-in-ubuntu.html](http://jaysdesktop.blogspot.ca/2012/06/configuring-lirc-for-hvr-1600-in-ubuntu.html)

As that post states, the lirc-modules-source package is not available for 12.04, so I took the lirc_zilog.ko from my staging directory (/lib/modules/3.2.0-32-generic/kernel/drivers/staging/media/lirc)  and placed it in here: 
/lib/modules/3.2.0-32-generic/kernel/drivers/staging/media/lirc/lirc_zilog.ko

When I try to modprobe lirc_zilog I get 
```
[ 1419.291447] lirc_zilog: disagrees about version of symbol lirc_register_driver
[ 1419.291458] lirc_zilog: Unknown symbol lirc_register_driver (err -22)
```


I'd like some help in resolving this conflict. 

I also tried doing what the post suggests and downloading the .deb file and extracting the lirc_zilog.ko file, but it has the same results.

I was using analog cable only but now that my provider is forcing everyone to use a STB, my getting this blaster working is essential in me being able to use my new MythTV setup. Any help anyone can provide would be greatly appreciated! I also posted this in IRC earlier but there weren't really any responses. Thanks.

---

