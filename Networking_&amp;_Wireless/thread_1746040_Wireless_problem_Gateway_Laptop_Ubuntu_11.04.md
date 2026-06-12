---
title: "Wireless problem Gateway Laptop Ubuntu 11.04"
date: 2011-05-01
forum: Networking &amp; Wireless
---

### Post by cinkoff11 on 2011-05-01
I have a gateway laptop that has been running Ubuntu 10.10 perfectly fine for a while with the wireless features working great, but I decided to update to Ubuntu 11.04. I completely got rid of 10.10 and installed Ubuntu 11.04, and now it wont show anything about wifi networks, and wont connect to any wireless networks. It works fine with an ethernet cable plugged in, that is how I am using the internet right now but I really need the wireless features. If anyone knows how to help me solve this problem, I would greatly appreciate some help. Thanks in advance.

---

### Post by mohdforever on 2011-05-01
in my opinion , 
you have to reinstall 11.04 from a USB or CD ... 
according to your post ... you upgraded your system.
so .. try to install 11.04 as a new release

---

### Post by cinkoff11 on 2011-05-01
I did not update my system, I decide I wanted to do a fresh install. I installed from an Ubuntu 11.04 installation cd, deleting my old filesystem.
-Thanks

---

### Post by waggotamp on 2011-05-02
We are having the same issue, 10:10 worked fine, now 11:04 no wifi. Any help would be appreciated.

Thank you

---

### Post by cinkoff11 on 2011-05-02
I fixed my problem! Here is how I did it. Install these drivers, [http://ie.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb](http://ie.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb)
For me, the first time I did this and then restarted it didn't work, but then I tried it again and turned off the computer. When I turned my laptop back on in an hour the wireless features worked!:P 
Hope this helps, good luck with your laptop.

-cinkoff11

---

### Post by waggotamp on 2011-05-02
Nothing was working for me, So I went to the Gateway drivers page, downloaded the Vistax64 drivers for the Realtec Wireless card that is in our Gateway MT6451.

I loaded it into the 'addition drivers' and now after a reboot the wifi is working again.

11.04 is looking very good. Thanks to everyone involved!

---

