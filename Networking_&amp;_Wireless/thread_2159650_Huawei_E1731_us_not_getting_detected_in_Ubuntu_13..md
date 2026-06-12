---
title: "Huawei E1731 us not getting detected in Ubuntu 13.04"
date: 2013-07-03
forum: Networking &amp; Wireless
---

### Post by rengasami21 on 2013-07-03
Hi,

I have installued Ubuntu 13.04 on my Dell insperion 14 laptop. I have an airtel data card 3G with Huawei E1731 firmware. When I plugged that device into my system, Ubuntu is not even recognizing that device which I came to know by getting /media directory. I am not able to proceed further because of this. When I used Network manager and added an entry for airtel data card also its not connecting. Can somebody please help me here?

I am not able to use wvdial as I am not having any network access to install that in Ubuntu

Regards,
Rengasami R

---

### Post by sanderj on 2013-07-04
As usual:

Unplug the stick, type "lsusb"
Plug in the stick, type "lsusb", find the new line and post it here and Google it. And immediately type "dmesg | tail -20" and post the output here.

---

### Post by vakashoney on 2013-07-04
i thnik ubumtu is not supporting it....

---

