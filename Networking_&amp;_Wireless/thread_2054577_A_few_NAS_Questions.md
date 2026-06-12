---
title: "A few NAS Questions"
date: 2012-09-07
forum: Networking &amp; Wireless
---

### Post by marshall1001 on 2012-09-07
I have a few NAS-related questions that I can't seem to get answers for via Google. Any help would be greatly appreciated.

Firstly, I have an Android tablet and I'm not too big on moving things round via USB as it's a bit slow. I've spotted "Droid NAS" on the Play Store, and it's apparently the best thing since sliced bread if you're a Mac user; however when I try to access the server through Nautilus it refuses to mount. Is there an alternative app for Android that will work similarly and allow access for Ubuntu? Or is there any workaround you know of to make Droid NAS and Ubuntu play nice that would be swell also.

Secondly, I'm planning on buying a NAS enclosure soon and was wondering if any of you could recommend one. It'll need to house two hdds, and again be accessible through Ubuntu. I'm cautious mainly because I've seen a few which come bundled with software to set them up/use them appropriately and I don't want to have to jump through too many hoops. Ideally I'd like to plug it in, have it appear in Nautilus and then play with it as if it were a regular external hdd.

Thanks to anyone who takes the time to reply.

---

### Post by mdo2 on 2013-08-15
> **marshall1001 said:**
> I have a few NAS-related questions that I can't seem to get answers for via Google. Any help would be greatly appreciated.

Firstly, I have an Android tablet and I'm not too big on moving things round via USB as it's a bit slow. I've spotted "Droid NAS" on the Play Store, and it's apparently the best thing since sliced bread if you're a Mac user; however when I try to access the server through Nautilus it refuses to mount. Is there an alternative app for Android that will work similarly and allow access for Ubuntu? Or is there any workaround you know of to make Droid NAS and Ubuntu play nice that would be swell also.

Secondly, I'm planning on buying a NAS enclosure soon and was wondering if any of you could recommend one. It'll need to house two hdds, and again be accessible through Ubuntu. I'm cautious mainly because I've seen a few which come bundled with software to set them up/use them appropriately and I don't want to have to jump through too many hoops. Ideally I'd like to plug it in, have it appear in Nautilus and then play with it as if it were a regular external hdd.

Thanks to anyone who takes the time to reply.

Hi, you may have since figured this out, but I've just successfully mounted my Android SD card over wifi using the instructions posted here:

[http://hisham.hm/2013/05/05/mounting-the-sd-card-from-your-android-device-on-linux-over-wifi/](http://hisham.hm/2013/05/05/mounting-the-sd-card-from-your-android-device-on-linux-over-wifi/)

After installing and running Droid NAS, the command I used to mount the "Camera" share (which is the share I was interested in) was:

sudo mount.cifs -o port=7777 //192.168.0.3/Camera <mountpoint>

Hope this is helpful for someone!

---

