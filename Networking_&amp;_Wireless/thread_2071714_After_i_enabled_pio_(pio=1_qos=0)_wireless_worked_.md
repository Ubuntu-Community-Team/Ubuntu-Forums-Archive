---
title: "After i enabled pio (pio=1 qos=0) wireless worked but my windows wireless stoped"
date: 2012-10-15
forum: Networking &amp; Wireless
---

### Post by JohnVinxtreme on 2012-10-15
hey guys...

Just put my bcm4312 in pio mode and it worked like a charm but my windows wireless just gave up on me .. it was working fine before  ... so i installed and reinstalled all the necessary wireless drivers but nothing .... Also i tried to bring back into pio=0 mode in ubuntu and restarted to check in windows  if may be it was staying in pio enabled mode but again nothing  .... cant see wireless networks :(
Please Help ....


Thanks In Advance :-)

---

### Post by chenxiaolong on 2012-10-15
> **JohnVinxtreme said:**
> hey guys...

Just put my bcm4312 in pio mode and it worked like a charm but my windows wireless just gave up on me .. it was working fine before  ... so i installed and reinstalled all the necessary wireless drivers but nothing .... Also i tried to bring back into pio=0 mode in ubuntu and restarted to check in windows  if may be it was staying in pio enabled mode but again nothing  .... cant see wireless networks :(
Please Help ....


Thanks In Advance :-)

Could you try removing the "/etc/modprobe.d/b43.conf" and then try changing to pio mode?

```
sudo rmmod b43
sudo modprobe b43 pio=0
```

---

### Post by JohnVinxtreme on 2012-10-16
> **chenxiaolong said:**
> Could you try removing the "/etc/modprobe.d/b43.conf" and then try changing to pio mode?

```
sudo rmmod b43
sudo modprobe b43 pio=0
```


Yeah had already tried that ... but now i tried with pio =0 qos=1 then ubuntu will not have wireless but windows will .. so i guess have to switch to pio=0 qos=1 when i logout of ubuntu and ill have it working ...!!!
Thanks ):P

---

### Post by nothingspecial on 2012-10-16
Question moved to it's own thread.

---

