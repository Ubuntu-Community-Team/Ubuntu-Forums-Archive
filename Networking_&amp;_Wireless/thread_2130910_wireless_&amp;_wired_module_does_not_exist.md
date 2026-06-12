---
title: "wireless &amp; wired module does not exist"
date: 2013-03-30
forum: Networking &amp; Wireless
---

### Post by wildmanne39 on 2013-03-30
Hi, I had to install a new kernel, so I installed 3.8rc7 anyway the wire and wireless modules did not build I imagine because I can not modprobe ath9k or the wired module.

I will have to switch to the new kernel to get the info you need.
Thanks

---

### Post by chili555 on 2013-03-30
Is this where you got the packages, or where? [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.8-rc7-raring/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.8-rc7-raring/)

Did you install linux-image, linux-headers and linux-headers-all? In other words, all three?

---

### Post by wildmanne39 on 2013-03-30
Yes to both questions.
Thanks

---

### Post by chili555 on 2013-03-30
Installing myself to check. Back in a few moments.

---

### Post by wildmanne39 on 2013-03-30
Thank you!!!

---

### Post by chili555 on 2013-03-30
Please also install linux-image-***extra*** and I believe you'll be all set. Rebooting to test.

---

### Post by wildmanne39 on 2013-03-30
That is what i was wondering as well.
I will have to put it on a flash drive and see if I can I can install it, I have never done that before but I think I can manage it.
Thanks

---

### Post by chili555 on 2013-03-30
You can install the deb from any other kernel and yes it solves it:> chili@Think410:~$ uname -r
3.8.0-030800rc7-generic
chili@Think410:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"GBR1"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 99:13:XX:62:8D:99   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=64/70  Signal level=-46 dBm  
```
sudo dpkg -i Desktop/linux-image-extra*.deb
```Please marked Solved. I need a few more!

---

### Post by wildmanne39 on 2013-03-30
It worked so easy!!!! I did not know I could do it from >  You can install the deb from any other kernel and yes it solves it:
That is great information to know.
Thanks my good friend!!!

---

