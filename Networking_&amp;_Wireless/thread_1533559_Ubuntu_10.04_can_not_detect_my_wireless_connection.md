---
title: "Ubuntu 10.04 can not detect my wireless connection."
date: 2010-07-18
forum: Networking &amp; Wireless
---

### Post by hoboy on 2010-07-18
Ubuntu 10.04 can not detect my wireless connection.
I don't know anything about this subject.
I am using :
Linux lucas05-desktop 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 07:54:58 UTC 2010 i686 GNU/Linux
lucas@lucas05-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=11 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

---

### Post by hoboy on 2010-07-18
ok.. The problem is solved.
Butttt I have no idea what I have done specifically to solve it.
1.I have activate NVIDIA hardware Drivers.
2.sudo apt-get install b43-fwcutter linux-backports-modules-wireless-lucid-generic
3. sudo apt-get install build-essential
so here you can see that I don't know what I am doing.
but the wireless is working fine.

---

### Post by wojox on 2010-07-18
```
sudo apt-get install b43-fwcutter linux-backports-modules-wireless-lucid-generic
```

That's the wireless driver there. So good job. :p

---

### Post by hoboy on 2010-07-18
> **wojox said:**
> ```
sudo apt-get install b43-fwcutter linux-backports-modules-wireless-lucid-generic
```

That's the wireless driver there. So good job. :p

OOOOOOOOOOOK. 
Then it is time for me to go to se Tour de france :)

---

